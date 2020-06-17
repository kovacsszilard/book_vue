<template>
    <div>   <!-- Felső navbar -->
          <nav class="navbar navbar-expand navbar-dark bg-dark">
        <a class="navbar-brand" href="#">KÖNVYTÁR</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarsExample02" aria-controls="navbarsExample02" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
      
        <div class="collapse navbar-collapse" id="navbarsExample02">
          <ul class="navbar-nav mr-auto">
            <li class="nav-item active">
              <a class="nav-link" href="#">Könyvek <span class="sr-only">(current)</span></a>
            </li>
            <li class="nav-item active">
                <a class="nav-link" href="#">Tagok <span class="sr-only">(current)</span></a>
              </li>
              <li class="nav-item active">
                <a class="nav-link" href="#">Kölcsönzés <span class="sr-only">(current)</span></a>
              </li>

              <li class="nav-item active">
                <a class="nav-link" href="#">Rólunk <span class="sr-only">(current)</span></a>
              </li>

              <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle" href="#" id="dropdown03" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">Linkek</a>
                <div class="dropdown-menu" aria-labelledby="dropdown03">
                  <a class="dropdown-item" href="https:/www.kindgirls.com">Kindgirls</a>
                  <a class="dropdown-item" href="#">Könyvtár a faszbukon</a>
                  <a class="dropdown-item" href="#">Something else here</a>
                </div>
              </li>
            
          </ul>
          <form class="form-inline my-2 my-md-0">
            <input class="form-control" type="text" placeholder="Keresés az oldalon">
          </form>
        </div>
      </nav>
    </div>
</template>

<!-- ami kell -->
<script>   
export default {
    name: "Header"}
</script>
<style scoped>
</style>