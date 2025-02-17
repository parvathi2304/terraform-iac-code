# terraform/main.tf
provider "docker" {}

resource "docker_image" "flask_app_image" {
  name = "flask-app-image"
  build {
    context = "./"
  }
}

resource "docker_container" "flask_app_container" {
  name  = "flask-app-container"
  image = docker_image.flask_app_image.latest
  ports {
    internal = 5000
    external = 5000
  }
}
