## Threejs

### 설명

- Light: 빛의 양
- Scene: 장면/무대
- Camera: 카메라
- Field of View: 시야각 (카메라)
- Geometry: 모양
- Material: 재질
- Geometry + Material = Mesh( 재질)

# 과정

- 캔버스내부에 만들기 시작한다
- 캔버스내부에 renderer를 통해서 모양을 제작한다

```javascript
const renderer = new THREE.WebGLRenderer({
  canvas,
  antialias: true,
});
renderer.setSize(window.innerWidth, window.innerHeight);
```

- 그안에 Scene을 만들어서 무대를 넣어준다.

```javascript
// Scene
const scene = new THREE.Scene();
```

- Camera의 위치를 조정해준다

```javascript
// Perspective Camera(원근 카메라)
const camera = new THREE.PerspectiveCamera(
  75, // 시야각(field of view)
  window.innerWidth / window.innerHeight, // 종횡비(aspect)
  0.1, // near
  1000 // far
);
camera.position.x = 1; // 카메라 x축
camera.position.y = 2; // 카메라 y축
camera.position.z = 5; // 카메라 z축
scene.add(camera); // 무대에 카메라 삽입
```

- 메시를 만들어서 무대에 삽입한다

```javascript
// Mesh
const geometry = new THREE.BoxGeometry(1, 1, 1);
const material = new THREE.MeshBasicMaterial({
  // color: 0xff0000
  // color: '#ff0000'
  color: "blue",
});
const mesh = new THREE.Mesh(geometry, material);
scene.add(mesh);
```

- 최종적으로 렌더러를 통해서 무대와 카메라를 넣는다

```javascript
// 그리기
renderer.render(scene, camera);
```

- 디바이스 별로 픽셀 크기가 다를 때는 아래 사용

```javascript
renderer.setPixelRatio(window.devicePixelRatio > 1 ? 2 : 1);
```
