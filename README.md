# three.js

three.js est une bibliothèque JavaScript qui va nous permettre de faire de la 3D. 

## sources :
 - Le site officiel : [https://threejs.org/](https://threejs.org/).
 - Le code source : [se trouve sur github](https://github.com/mrdoob/three.js/).
 - Des exemples : [github](https://github.com/mrdoob/three.js/tree/dev/examples) , [site officiel].

## Pour l'utiliser : 
- Vous avez besoin d'importer la bibliothèque. Copiez le contenu de [ce lien](https://threejs.org/build/three.min.js) dans un fichier three.min.js que vous aurez crée. 

- Inclure la librairie avant la fermeture du body dans votre HTML :
      
      <script src="js/three.min.js"></script>    
  ou 
  
      <script src="http://mrdoob.github.com/three.js/build/three.min.js"></script> (le lien en ligne)

- Faire notre script après la librairie qu'on vient de copier :

         <script type="text/javascript">
         <!-- C'est ici que nous utiliserons Three.js -->
         </script>
      </body>
      </html>
      
- Nous allons initialiser notre scène avec le code suivant :

        var renderer, scene, camera, mesh;

        init();
        animate();

        function init(){
            // on initialise le moteur de rendu
            renderer = new THREE.WebGLRenderer();

            // si WebGL ne fonctionne pas sur votre navigateur vous pouvez utiliser le moteur de rendu Canvas à la place
            // renderer = new THREE.CanvasRenderer();
            renderer.setSize( window.innerWidth, window.innerHeight );
            document.getElementById('container').appendChild(renderer.domElement);

            // on initialise la scène
            scene = new THREE.Scene();

            // on initialise la camera que l’on place ensuite sur la scène
            camera = new THREE.PerspectiveCamera(50, window.innerWidth / window.innerHeight, 1, 10000 );
            camera.position.set(0, 0, 1000);
            scene.add(camera);

            // on créé un  cube au quel on définie un matériau puis on l’ajoute à la scène 
            var geometry = new THREE.CubeGeometry( 200, 200, 200 );
            var material = new THREE.MeshBasicMaterial( { color: 0xff0000, wireframe: true } );
            mesh = new THREE.Mesh( geometry, material );
            scene.add( mesh );
        }

        function animate(){ // Faire tourner la forme
            // on appel la fonction animate() récursivement à chaque frame
            requestAnimationFrame( animate );
            // on fait tourner le cube sur ses axes x et y
            mesh.rotation.x += 0.01;
            mesh.rotation.y += 0.02;
            // on effectue le rendu de la scène
            renderer.render( scene, camera );
        }
