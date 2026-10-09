# 宝安区创业路“一轴三心” · 场地体块模型

基于真实底图的交互式三维场地模型（MapLibre GL JS），研究范围为“2022年国际咨询研究范围”（约 13.4 km²），并叠加城市更新重点片区范围。

## 使用
- 在线：发布到 GitHub Pages 后直接打开 `index.html`。
- 本地：在本目录运行 `python3 -m http.server`，浏览器访问 `http://localhost:8000`；或直接双击 `index_standalone.html`（数据与程序已内嵌，底图瓦片仍需联网）。
- 默认底图：高德卫星（GCJ-02）+ 底图灰度淡化。
- 底图可切换：高德矢量 / 高德卫星（GCJ-02，自动纠偏）、Esri 卫星 / Esri 浅灰 / OSM（WGS84）、无底图。
- 图层：山体资源（尖岗山 / 大井山 / 孖松山 / 塘岭山 / 官龙山 / 鸡公山及周边山体，绿色半透明）、水渠（新圳河，青色）、打石路（黄色高亮 +「打石路」标注）、标注（山峰名/新圳河/雪花科创城/留仙洞/西丽枢纽/打石路；编辑 `data/labels.geojson` 即可改）。
- 点击建筑可查看高度、高度来源、底面来源等属性。

## 文件
- `index.html`、`assets/`（MapLibre GL JS 5.24，本地化）、`data/`（建筑、范围线、道路、mountains、canal、labels GeoJSON，WGS84；高德底图时自动转 GCJ-02）
- `downloads/`：`massing.3dm` / `massing.obj` / `massing.glb`（EPSG:32650 UTM 50N，局部原点 E=181200、N=2499600，单位 m，Z 向上；glb 按规范为 Y 向上），`footprints.geojson`（含高度与来源字段），`boundary.geojson`

## 数据与精度说明
- 建筑底面：OpenStreetMap（© OSM 贡献者，ODbL）＋ 3D-GloBFP（Che et al., 2024，ESSD）补充。
- 建筑高度：优先使用 OSM `height` / `building:levels` 标注（约占研究范围内建筑的 4%），其余为估算（邻近同型标注建筑、3D-GloBFP 2020 估算、CMAB 估算或类型默认值），字段 `src` 标明来源。机器学习估算普遍**低估超高层**，仅供方案研究参考。
- 范围线：由竞赛文件“图二：基地范围”配准，并贴合 OSM 道路中心线；误差约数十米，以官方矢量范围为准。
