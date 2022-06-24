# Rails 7 дээр Bootstrap 5 -аар шууд эхлүүлэх арга

* 1-р алхам
rails new myApp --css bootstrap
or
rails new myApp -c bootstrap

* 2-р алхам
Хэрэв консолоо сайн харвал package.json дээр ямар өөрчлөлт нэмэх хэрэгтэйг харуулсан байгаа. Тэр зааврын дагуу дараах мөрийг package.json дээр нэмнэ.
  "scripts": { 
    "build:css": "sass ./app/assets/stylesheets/application.bootstrap.scss:./app/assets/builds/application.css --no-source-map --load-path=node_modules",
    "build": "esbuild app/javascript/*.* --bundle --sourcemap --outdir=app/assets/builds --public-path=assets"
  }

  өөрөөр хэлбэл ийм болно.
{
  "name": "app",
  "private": "true",
  "scripts": { 
    "build:css": "sass ./app/assets/stylesheets/application.bootstrap.scss:./app/assets/builds/application.css --no-source-map --load-path=node_modules",
    "build": "esbuild app/javascript/*.* --bundle --sourcemap --outdir=app/assets/builds --public-path=assets"
  },
  "dependencies": {
    "@hotwired/stimulus": "^3.0.1",
    "@hotwired/turbo-rails": "^7.1.3",
    "@popperjs/core": "^2.11.5",
    "bootstrap": "^5.1.3",
    "bootstrap-icons": "^1.8.3",
    "esbuild": "^0.14.47",
    "sass": "^1.53.0"
  }
}

* package.json дээрх өөрчлөлтийг apply хийх
CSS build хийх
yarn build:css --watch 

JS build хийх
yarn build

* 3-р алхам
rails g controller pages home

in routes.rb

root to: "pages#home"
add bootstrap element to 
<button class="btn btn-success">Seico</button>

* SERVER ажиллуулах
./bin/dev
гэж ажиллуулж болно.

