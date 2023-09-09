要跑起 3D 渲染，场景最起码的要求就是场景、相机和渲染器三者的处理。

```TypeScript
// 示例：一个立方体旋转

// 创建场景对象
const scene = new THREE.Scene();
// 创建摄像头
const camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );
// 创建渲染器
const renderer = new THREE.WebGLRenderer();
renderer.setSize( window.innerWidth, window.innerHeight );
document.body.appendChild( renderer.domElement );

// 用BoxGeometry实例一个立方体，参数上表示长宽高三要素
const geometry = new THREE.BoxGeometry(1, 1, 1)
// MeshBasicMaterial用于表示材质
const material = new THREE.MeshBasicMaterial({ color: 0x00ff00 })
// Mesh（网格）网格包含一个几何体以及作用在此几何体上的材质，我们可以直接将网格对象放入到我们的场景中，并让它在场景中自由移动。
const cube = new THREE.Mesh(geometry, material)
// 在坐标轴（0，0，0）位置放置
scene.add(cube)

function animate() {
	// requestAnimationFrame最重要的一点或许就是当用户切换到其它的标签页时，它会暂停
	// 因此不会浪费用户宝贵的处理器资源，也不会损耗电池的使用寿命。
	requestAnimationFrame(animate)
	// 动画循环，改变物体旋转角度
	cube.rotation.x += 0.01
	cube.rotation.y += 0.01
	renderer.render(scene, camera)
}
animate()
```
