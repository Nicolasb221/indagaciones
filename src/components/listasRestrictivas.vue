<template>

    <div class="box-container">
      <form v-if="formularioVisible" @submit.prevent="almacenarDatos" class="container-formulario">
        <label for="nombre" class="titulo">Indagacion Terceros</label><br>
        <div class="container-inputs">
          <input type="text" class="input-container-input" id="nombre" v-model="nombre" placeholder="Ingrese el nombre" required>
          <input type="text" class="input-container-input" id="apellidos" v-model="apellidos" placeholder="Ingrese el apellido">
          <input type="number" class="input-container-input" id="documento" v-model="documento" placeholder="Cédula de ciudadanía">

        </div>
        <br><br>
        <div class="boton-cargar">
          <fa @click="almacenarDatos" :icon="['fas', 'circle-right']" size="2xl" style="cursor: pointer;color: #483698;"/>
        </div>
      </form>
      <div class="container-datos" v-if="datosAlmacenados">
        <div class="container-datos-i">
          <h3 class="titulo2">Tercero</h3>

          <p class="parrafo"><strong>Nombres:</strong> {{ datosAlmacenados.valorN}}</p>
          <p class="parrafo"><strong>Apellidos:</strong> {{ datosAlmacenados.apellidosSS}}</p>
          <p class="parrafo"><strong>Cédula de ciudadanía:</strong> {{ datosAlmacenados.documentoId}}</p>
        </div>
        <div class="container-buttons">
          <div class="container-bot">
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Linkedin">Linkedin</button>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Pep">PEP</button>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Informa">Informa</button>
            </div>
          </div>
          <div class="container-bot">
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Corrupcion">Corrupción</button>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Narcotrafico">Narcotráfico</button>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Lavado()">Lavado de</button>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Fraude">Fraude</button>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Facesearch">Facesearch</button>
            </div>
          </div>
          <div class="container-bot">
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Facebook">Facebook</button>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Instagram">Instagram</button>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="TikTok">TikTok</button>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Pinterest">Pinterest</button>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Twitter">X</button>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Youtube">Youtube</button>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Socialsearch">Social search</button>
            </div>
          </div>
          <div class="container-bot">
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Truora">Truora</button>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Ramajudicial">Rama judicial</button>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Offshoreleaks">Offshoreleaks</button>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Wc">Wc</button>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Contaduria">Contaduría</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "listasRestrictivas",
    data() {
      return {
        nombre: '',
        apellido:'', 
        datosAlmacenados: null,
        formularioVisible: true,
        iniciales: '',
      };
    },
    methods: {
      almacenarDatos() {
        const textoLabel = 'Ingresa tu nombre:';
        const conca = `${this.nombre} ${this.apellidos}`;
        this.iniciales = this.obtenerIniciales(conca);
        this.datosAlmacenados = {
          label: textoLabel,
          valorN: this.nombre,
          valorA: `"${this.apellidos}"`,
          apellidosSS: this.apellidos,
          documentoId: this.documento,
          archivoLinkedin: `${this.iniciales} - Linkedin`,
          archivoPEP: `${this.iniciales} - PEP`,
          archivoInforma: `${this.iniciales} - Vinculaciones`,
          archivoCorrupcion: `${this.iniciales} - Google - Corrupción`,
          archivoNarcotrafico: `${this.iniciales} - Google - Narcotráfico`,
          archivoLavado: `${this.iniciales} - Google - Lavado de`,
          archivoFraude: `${this.iniciales} - Google - Fraude`,
          archivoFace: `${this.iniciales} - Google - Facesearch`,
          archivoFacebook: `${this.iniciales} - Google - Facebook`,
          archivoInstagram: `${this.iniciales} - Google - Instagram`,
          archivoTiktok: `${this.iniciales} - Google - Tiktok`,
          archivoPinterest: `${this.iniciales} - Google - Pinterest`,
          archivoX: `${this.iniciales} - Google - X`,
          archivoYoutube: `${this.iniciales} - Google - Youtube`,
          archivoSs: `${this.iniciales} - Social Search`,
          archivoTruora: `${this.iniciales} - Truora`,
          archivoRj: `${this.iniciales} - Rama Judicial`,
          archivoOff: `${this.iniciales} - Google - Offshoreleaks`,
          archivoWc: `${this.iniciales} - WC`,
          archivoContaduria: `${this.iniciales} - Contaduría`,
          archivoTemp: '',
        };
        this.formularioVisible = false;
        this.nombre = '';
        this.apellidos = '';
        this.documento = '';
      },
      copyPaste(archivoTemp) {
        if (archivoTemp) {
          const texto = this.datosAlmacenados.archivoTemp;
          navigator.clipboard.writeText(texto)
        }
      },
      obtenerIniciales(cadena){
        return cadena
          .split(' ')
          .map(palabra => palabra.charAt(0).toUpperCase())
          .join('');

      },
      Linkedin() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Linkedin`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoLinkedin;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        window.open(urlBusqueda, '_blank');
      },
      Pep() {
        const consulta = `${this.datosAlmacenados.documentoId}`;
        const urlBusqueda = `https://www.funcionpublica.gov.co/fdci/consultaCiudadana/consultaPEP?tipoRegistro=0&numeroDocumento=${encodeURIComponent(consulta)}&primerNombre=&segundoNombre=&primerApellido=&segundoApellido=&entidad=&dpto=&mun=&find=Buscar#resultadosBusqueda`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoPEP;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        window.open(urlBusqueda, '_blank');
      },
      Informa() {
        const urlBusqueda = `https://www.informacolombia.com/InformaIntWeb/Main/id_sess/00081623158000034624480000041879/idioma/01/activa/2/id_tmp/974.0/prod/VINCULACIONES_RESULTADO_CONTEO/prod_desde/BUSCADOR_VINCULACIONES`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoInforma;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        window.open(urlBusqueda, '_blank');
      },  
      Corrupcion() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Corrupción`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoCorrupcion;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        window.open(urlBusqueda, '_blank');
      },
      Narcotrafico() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Narcotráfico`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoNarcotrafico;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        window.open(urlBusqueda, '_blank');
      },
      Lavado() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Lavado de`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoLavado;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        window.open(urlBusqueda, '_blank');
      },
      Fraude() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Fraude`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoFraude;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        window.open(urlBusqueda, '_blank');
      },
      Facesearch() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA}`;
        const urlBusqueda = `https://www.google.com/search?hl=es&tbm=isch&q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoFace;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        window.open(urlBusqueda, '_blank');
      },
      Facebook() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Facebook`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoFacebook;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        window.open(urlBusqueda, '_blank');
      },   
      Instagram() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Instagram`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoInstagram;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        window.open(urlBusqueda, '_blank');
      },   
      TikTok() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + TikTok`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoTiktok;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        window.open(urlBusqueda, '_blank');
      },   
      Pinterest() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Pinterest`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoPinterest;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        window.open(urlBusqueda, '_blank');
      },   
      Twitter() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + X`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoX;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        window.open(urlBusqueda, '_blank');
      },  
      Youtube() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Youtube`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoYoutube;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        window.open(urlBusqueda, '_blank');
      },
      Socialsearch() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.apellidosSS}`;
        const urlBusqueda = `https://www.social-searcher.com/social-buzz/?q5=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoSs;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        window.open(urlBusqueda, '_blank');
      },    
      Truora() {
        const urlBusqueda = `https://checks.truora.com/#/dashboard/check/custom`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoTruora;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        window.open(urlBusqueda, '_blank');
      },    
      Ramajudicial() {
        const urlBusqueda = `https://consultaprocesos.ramajudicial.gov.co/Procesos/NombreRazonSocial`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoRj;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        window.open(urlBusqueda, '_blank');
      }, 
      Offshoreleaks() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Offshoreleaks`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoOff;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        window.open(urlBusqueda, '_blank');
      }, 
      Wc() {
        const urlBusqueda = `https://members.worldcompliance.com/SignIn.aspx`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoWc;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        window.open(urlBusqueda, '_blank');
      },
      Contaduria() {
        const urlBusqueda = `https://eris.contaduria.gov.co/BDME/#`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoContaduria;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        window.open(urlBusqueda, '_blank');
      } 
      
    }
  };
  </script>
  <style scoped>
  .box-container {
    width: 70%;
    height: 70%;
    display: flex;
    position: absolute;
    justify-content: space-evenly;
    justify-items: center;
    align-items: center;
    border-radius: 8px;
  }
  input[type="number"]::-webkit-outer-spin-button, input[type="number"]::-webkit-inner-spin-button {-webkit-appearance: none;}
  
  .container-formulario{
    height: 80%;
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
  }
  .titulo{font-size: 50px;text-align: center;color:#483698;}
  .container-inputs{
    position: relative;
    width: 100%;
    display: flex;
    flex-grow: 2;
    flex-direction: column;
    justify-content: space-evenly;
    
  }
  .input-container-input{
    display: flex;
    flex-grow: wrap;
    color: #483698;
    font-family: 'Bubbler One', sans-serif;
    font-size: 15px;
    padding: 10px;
    border: none;
    border-radius: 10px;
    outline: 2px solid #483698;
    background-color: transparent;
    transition: outline-color 500ms;
    margin: 20px;

  }
  .input-container-input::placeholder{
    color:#483698;
    opacity: .7;
  }
  .boton-cargar{
    height: 50%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .b-botoncargar{width: 10%;}

  .container-datos{
    display: flex ;
    width: 80%;
    font-family: 'Bubbler One', sans-serif;
    flex-direction: column;
    color: #483698;
    font-size: 25px;

  }
  .container-datos-i{
    display:flex;
    flex-direction: column;
    margin: 20px;
  }
  .titulo2{font-size: 50px;text-align: center;color:#483698;margin:10px;}

  .parrafo{margin: 0;padding: 0;}

  .container-buttons{
    display:flex;
    flex-direction: column;
    flex-wrap: wrap;
    max-width: 100%;
  }
  .container-bot{
    display: flex;
    flex-direction: column;
    margin: 10px;
  }
  .container-bot-b{
    display: flex;
    justify-content: center;

  }
  .botonbusqueda{
    width: 50%;
    height: 20px;
    color: #483698;
    background-color: transparent;
    border: none;

  }
  </style>