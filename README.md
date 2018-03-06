# three.js

three.js est une bibliothèque JavaScript qui va nous permettre de faire de la 3D. 

## sources :
 - Le site officiel : [https://threejs.org/](https://threejs.org/).
 - Le code source : [se trouve sur github](https://github.com/mrdoob/three.js/).
 - Des exemples : [github](https://github.com/mrdoob/three.js/tree/dev/examples) , [site officiel](https://threejs.org/examples/).

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

       function init() {

       // on initialise la camera que l’on place ensuite sur la scène
       camera = new THREE.PerspectiveCamera( 70, window.innerWidth / window.innerHeight, 0.01, 10 );
       camera.position.z = 1;
       // on initialise la scène
       scene = new THREE.Scene();

       // on créé un  cube auquel on défini un matériau puis on l’ajoute à la scène 
       geometry = new THREE.BoxGeometry( 0.2, 0.2, 0.2 );
       material = new THREE.MeshNormalMaterial();

       mesh = new THREE.Mesh( geometry, material );
       scene.add( mesh );

       // on initialise le moteur de rendu
       renderer = new THREE.WebGLRenderer( { antialias: true } );
       renderer.setSize( window.innerWidth, window.innerHeight );
       document.body.appendChild( renderer.domElement ); // on le place dans le body
       //   document.getElementById('container').appendChild(renderer.domElement); (si on place dans une div container)
       }

       function animate() { // Faire tourner la forme
       // on appel la fonction animate() récursivement à chaque frame
       requestAnimationFrame( animate );
       // on fait tourner le cube sur ses axes x et y
       mesh.rotation.x += 0.01;
       mesh.rotation.y += 0.02;
       // on effectue le rendu de la scène
       renderer.render( scene, camera );
       }
       
Résultat : 
