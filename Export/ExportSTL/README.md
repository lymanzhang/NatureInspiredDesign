## 设计输出：如何将造型输出为stl格式
### how to export design output into STL files

![image](https://github.com/lymanzhang/NatureInspiredDesign/blob/master/Export/ExportSTL/images/export%20STL.PNG)

### 首先，定义一个Triangle class

```java
public class Triangle {
  PVector a;
  PVector b;
  PVector c;
  PVector n;
  
  public Triangle( PVector a, PVector b, PVector c, PVector n ) {
    this.a = a;
    this.b = b;
    this.c = c;
    this.n = n;
  }
}
```

### 其次，定义一个TriangleSoup class

```java
import java.io.FileOutputStream;
import java.nio.ByteBuffer;
import java.nio.ByteOrder;
import java.util.Arrays;
import java.io.FileOutputStream;
import java.io.IOException;
import java.util.List;

public class TriangleSoup {  
  List<Triangle> triangles = new ArrayList<Triangle>();
  float scale = 1;

  void scale( float scale ) {
    this.scale = scale;
  }

  void add( PVector a, PVector b, PVector c, PVector n ) {
    triangles.add( new Triangle( a, b, c, n ));
  }

  void save( String filename ) {
    try {
      byte[] header = new byte[80];
      byte[] count = new byte[4];
      byte[] tri = new byte[50];

      FileOutputStream out = new FileOutputStream( filename );  
      ByteBuffer buffer = ByteBuffer.allocate( 80 );
      buffer.order( ByteOrder.LITTLE_ENDIAN );

      Arrays.fill(header, 0, 80, (byte)0);
      out.write( header, 0, 80 );
      buffer.putInt( triangles.size());
      buffer.rewind();
      buffer.get( count, 0, 4 );
      out.write( count, 0, 4 ); 


      for ( int i=0; i<triangles.size(); i++) {
        buffer.rewind();
        buffer.putFloat( triangles.get(i).n.x * scale);
        buffer.putFloat( triangles.get(i).n.z * scale);
        buffer.putFloat( triangles.get(i).n.y * scale);

        buffer.putFloat( triangles.get(i).a.x * scale);
        buffer.putFloat( triangles.get(i).a.z * scale);
        buffer.putFloat( triangles.get(i).a.y * scale);

        buffer.putFloat( triangles.get(i).b.x * scale);
        buffer.putFloat( triangles.get(i).b.z * scale);
        buffer.putFloat( triangles.get(i).b.y * scale);

        buffer.putFloat( triangles.get(i).c.x * scale);      
        buffer.putFloat( triangles.get(i).c.z * scale);
        buffer.putFloat( triangles.get(i).c.y * scale); 

        buffer.putShort( (short)0 );
        buffer.rewind();
        buffer.get( tri, 0, 50 );
        out.write( tri, 0, 50 );
      }

      out.flush();
      out.close();
    } 
    catch ( IOException ioe ) {
      ioe.printStackTrace();
    }
  }
}

```

### 定义一个export函数

```java
void export() {
  selectOutput( "Export to STL", "exportCallback" );
}
```

### 定义一个exportCallback函数

```java
void exportCallback(File exportFile) {
  if ( exportFile != null ) {
    String filename = exportFile.getAbsolutePath();
    TriangleSoup export = new TriangleSoup();
    export.scale(1);
    exportOuter( export );
    export.save(filename);
  }
}
```

### 定义一个exportOuter函数，实现造型中所有三角形数据添加到输出的stream中，完成输出为stl。

```java
void exportOuter( TriangleSoup export) {
  for (int i = 0; i < layer-1; i ++) {
    for (int j = 0; j < layerSection-1; j ++) { 
      PVector p1 = new PVector(vertexPoint[i][j].x, vertexPoint[i][j].y);
      PVector p2 = new PVector(vertexPoint[i+1][j].x, vertexPoint[i+1][j].y);
      PVector p3 = new PVector(vertexPoint[i][j+1].x, vertexPoint[i][j+1].y);
      PVector p4 = new PVector(vertexPoint[i+1][j+1].x, vertexPoint[i+1][j+1].y);

      PVector n1 = new PVector( -(p1.x+p2.x+p3.x)/3, 0, -(p1.y+p2.y+p3.y)/3);
      n1.normalize(); 
      PVector n2 = new PVector( -(p2.x+p3.x+p4.x)/3, 0, -(p2.y+p3.y+p4.y)/3);
      n2.normalize();
      export.add( p1, p2, p3, n1 );
      export.add( p3, p2, p4, n2 );
    }
  }
}
```

![image](https://github.com/lymanzhang/NatureInspiredDesign/blob/master/Export/ExportSTL/images/export%20STL2.PNG)

```java

```
