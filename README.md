# WorkShop Deepfake
## Déroulement du WorkShop

Ce WS qui se présente sous forme de "tuto" est créé spécifiquement pour faire du deepfake en LIVE et pas faire du faceswap parfait sur des vidéos mais si cela vous intéresse venez me poser des questions.

- Installer les logiciels et les scripts pour entrainer un modèle
- Créer un dataset
- Nettoyer un dataset 
- Entrainer un modèle
- Exporter un modèle
- Utiliser un modèle (sur Teams/Discord/Twitch)

## Requirement

DirectX12 (Carte graphique compatible)
(Recommandé RTX 2070+ / Radeon RX 5700 XT+ )
CPU Moderne (Ryzen 7 5k+/intel I7 9k+)
4GB RAM, 32GB+ place
Windows 10
(Si vous êtes sur linux et que vous n'avez pas Windows installez un VM ou débrouillez vous.)

## Installation

Téléchargez deepfacelive et DeepFaceLab AVEC EN FONCTION DE VOTRE MATERIEL !!!
(Exemple : Si vous avez une RTX 2070 vous prenez 'DeepFaceLab_NVIDIA_up_to_RTX2080Ti...')

Lancez les 2 .exe pour extraire les fichiers dans votre dossier :
![](Install.png)

Vous devriez avoir un truc qui ressemble à ça :
![](Directory.png)

## 1. Le Data Set  

Tout d'abord allez dans le dossier DeepFaceLab_XXXXXXXX\workspace et supprimez les fichier vidéo data_src et data_dst.

Cherchez ensuite une vidéo ou on voit le plus possible la tête de la personne que vous souhaitez,
l'objectif par la suite sera de découper toutes les frames ou on vera son visage pour entrainer notre modèle.

Téléchargez la vidéo en MP4 (HD si possible mieux la qualité est mieux votre data set sera) et déposez la à la place des vidéo que vous avez supprimé (DeepFaceLab_XXXXXXXX\workspace), renommez la en "data_src".

Revenez aux .bat et lancez le "2) extract images from video data_src".
On vous demande le nombre de FPS pressez "Entrée" si vous avez de la place sur votre PC ou tapez 10.
Ensuite même principe, pour une meilleure qualité choisissez "png" mais si vous n'avez pas de place jpg.
En fonction de la taille de votre vidéo cela va prendre plus ou moins de temps.

Quand le programme à fini de découper toute les frames vous devez maintenant extraire uniquement les têtes, pour cela executez le "4) data_src faceset extract".
Une série d'option vont apparaître :
- GPU/CPU :  Si vous voulez allez plus vite prenez le GPU (ceux sans carte graphique beh CPU).
- Face Type F/WF/Head : Prenez WF c'est ce qui fontionnera le plus pour ce qu'on veut faire.
- Max number of faces from image : Si vous avez qu'une personne dans votre vidéo laissez 0 sinon si vous voulez moins d'image (vous allez devoir en supprimer beaucoup vous verrez) mettez 1 ou 2.
- Image size : Pour une qualité 720p mettez 768 ou moins, 1080p 1024 et 4K 2048 (tout est proportionel..)
- Jpeg quality : Mettez 100 ça ne change pas grand choses de mettre plus bas
- Write debug images to aligned_debug : Laissez "n" c'est pas utile pour notre application


| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Development

Want to contribute? Great!

Dillinger uses Gulp + Webpack for fast developing.
Make a change in your file and instantaneously see your updates!

Open your favorite Terminal and run these commands.

First Tab:

```sh
node app
```

Second Tab:

```sh
gulp watch
```

(optional) Third:

```sh
karma test
```

#### Building for source

For production release:

```sh
gulp build --prod
```

Generating pre-built zip archives for distribution:

```sh
gulp build dist --prod
```

## Docker

Dillinger is very easy to install and deploy in a Docker container.

By default, the Docker will expose port 8080, so change this within the
Dockerfile if necessary. When ready, simply use the Dockerfile to
build the image.

```sh
cd dillinger
docker build -t <youruser>/dillinger:${package.json.version} .
```

This will create the dillinger image and pull in the necessary dependencies.
Be sure to swap out `${package.json.version}` with the actual
version of Dillinger.

Once done, run the Docker image and map the port to whatever you wish on
your host. In this example, we simply map port 8000 of the host to
port 8080 of the Docker (or whatever port was exposed in the Dockerfile):

```sh
docker run -d -p 8000:8080 --restart=always --cap-add=SYS_ADMIN --name=dillinger <youruser>/dillinger:${package.json.version}
```

> Note: `--capt-add=SYS-ADMIN` is required for PDF rendering.

Verify the deployment by navigating to your server address in
your preferred browser.

```sh
127.0.0.1:8000
```

## License

MIT

**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>

   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>
