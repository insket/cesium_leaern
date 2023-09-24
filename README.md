### geojson
  - GeoJSON是一种对各种地理数据结构进行编码的JSON数据格式。GeoJSON支持点线面等多种几何图形。type表示要素类型，coordinates表示坐标数据，坐标通常是WGS-84。
  - turf  https://turfjs.fenxianglu.cn/

### topojson
- TopoJSON 是 GeoJSON 按拓扑学编码后的扩展形式，是由 D3 的作者 Mike Bostock 制定的。相比 GeoJSON 直接使用 Polygon、Point 之类的几何体来表示图形的方法，TopoJSON 中的每一个几何体都是通过将共享边（被称为arcs）整合后组成的。TopoJSON 拓扑表示共享一个称为弧的位置序列的一个或多个几何。
TopoJSON 作为 GeoJSON 的扩展，支持多种几何类型：Point，LineString，Polygon，MultiPoint，MultiLineString，MultiPolygon 和 GeometryCollection。 TopoJSON 中的几何可能包含其他属性，以对非几何数据进行编码。Mapshaper和arcgis都采用过这种拓扑格式。TopoJSON消除了冗余，共享的弧段仅存储一次，允许将相关的几何有效地存储在同一文件中。例如，内蒙古自治区和辽宁省之间的共享边界仅存储一次，而不是在两个省都重复。


### kml
- KML全称：Keyhole Markup Language，是基于XML（eXtensible Markup Language,可扩展标记语言）语法标准的一种标记语言（markup language），采用标记结构，含有嵌套的元素和属性。由Google（谷歌（页面存档备份，存于互联网档案馆））旗下的Keyhole公司发展并维护，用来表达地理标记。根据KML语言编写的文件则为KML文件，格式同样采用的XML文件格式，应用于Google地球相关软件中（Google Earth，Google Map, Google Maps for mobile...），用于显示地理数据（包括点、线、面、多边形，多面体以及模型...）。而现在很多GIS相关企业也追随Google开始采用此种格式进行地理数据的交换。
- kmz 是 kml 的压缩格式

### czml
● CZML是JSON的子集，这意味着一个有效的CZML文档也是一个有效的JSON文档。具体来说，CZML文档包含一个JSON数组，其中数组中的每个对象字面量元素都是一个CZML Packet。CZML包描述场景中单个对象的图形属性，例如单个飞机。
● 这种数据格式，使得Cesium具备实现动态数据的能力。
● CZML包含点、线、地标、模型等一些图形元素，并指明了这些元素如何随时间而变化。