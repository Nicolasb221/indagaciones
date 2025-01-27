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
          <fa @click="almacenarDatos" :icon="['fas', 'circle-right']" size="2xl" style="cursor: pointer;color: #ffffff;"/>
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
              <div class="container-siglas">
                <p class = siglas>{{ datosAlmacenados.archivoLinkedin}}</p>
                <fa @click="copiarLinkedin" :icon="['far', 'copy']" size="xs" style="cursor: pointer;color: #ffffff;" />
              </div>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Pep">PEP</button>
              <div class="container-siglas">
                <p class = siglas>{{ datosAlmacenados.archivoPEP}}</p>
                <fa @click="copiarPep" :icon="['far', 'copy']" size="xs" style="cursor: pointer;color: #ffffff;" />
              </div>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Informa">Informa</button>
              <div class="container-siglas">
                <p class = siglas>{{ datosAlmacenados.archivoInforma}}</p>
                <fa @click="copiarInforma" :icon="['far', 'copy']" size="xs" style="cursor: pointer;color: #ffffff;" />
              </div>
            </div>
          </div>
          <div class="container-bot">
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Corrupcion">Corrupción</button>
              <div class="container-siglas">
                <p class = siglas>{{ datosAlmacenados.archivoCorrupcion}}</p>
                <fa @click="copiarCorrupcion" :icon="['far', 'copy']" size="xs" style="cursor: pointer;color: #ffffff;" />
              </div>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Narcotrafico">Narcotráfico</button>
              <div class="container-siglas">
                <p class = siglas>{{ datosAlmacenados.archivoNarcotrafico}}</p>
                <fa @click="copiarNarcotrafico" :icon="['far', 'copy']" size="xs" style="cursor: pointer;color: #ffffff;" />
              </div>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Lavado">Lavado de</button>
              <div class="container-siglas">
                <p class = siglas>{{ datosAlmacenados.archivoLavado}}</p>
                <fa @click="copiarLavado" :icon="['far', 'copy']" size="xs" style="cursor: pointer;color: #ffffff;" />
              </div>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Fraude">Fraude</button>
              <div class="container-siglas">
                <p class = siglas>{{ datosAlmacenados.archivoFraude}}</p>
                <fa @click="copiarFraude" :icon="['far', 'copy']" size="xs" style="cursor: pointer;color: #ffffff;" />
              </div>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Facesearch">Facesearch</button>
              <div class="container-siglas">
                <p class = siglas>{{ datosAlmacenados.archivoFace}}</p>
                <fa @click="copiarFace" :icon="['far', 'copy']" size="xs" style="cursor: pointer;color: #ffffff;" />
              </div>
            </div>
   
          </div>
          <div class="container-bot">
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Facebook">Facebook</button>
              <div class="container-siglas">
                <p class = siglas>{{ datosAlmacenados.archivoFacebook}}</p>
                <fa @click="copiarFacebook" :icon="['far', 'copy']" size="xs" style="cursor: pointer;color: #ffffff;" />
              </div>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Instagram">Instagram</button>
              <div class="container-siglas">
                <p class = siglas>{{ datosAlmacenados.archivoInstagram}}</p>
                <fa @click="copiarInstagram" :icon="['far', 'copy']" size="xs" style="cursor: pointer;color: #ffffff;" />
              </div>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="TikTok">TikTok</button>
              <div class="container-siglas">
                <p class = siglas>{{ datosAlmacenados.archivoTiktok}}</p>
                <fa @click="copiarTiktok" :icon="['far', 'copy']" size="xs" style="cursor: pointer;color: #ffffff;" />
              </div>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Pinterest">Pinterest</button>
              <div class="container-siglas">
                <p class = siglas>{{ datosAlmacenados.archivoPinterest}}</p>
                <fa @click="copiarPinterest" :icon="['far', 'copy']" size="xs" style="cursor: pointer;color: #ffffff;" />
              </div>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Twitter">X</button>
              <div class="container-siglas">
                <p class = siglas>{{ datosAlmacenados.archivoX}}</p>
                <fa @click="copiarX" :icon="['far', 'copy']" size="xs" style="cursor: pointer;color: #ffffff;" />
              </div>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Youtube">Youtube</button>
              <div class="container-siglas">
                <p class = siglas>{{ datosAlmacenados.archivoYoutube}}</p>
                <fa @click="copiarYoutube" :icon="['far', 'copy']" size="xs" style="cursor: pointer;color: #ffffff;" />
              </div>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Socialsearch">Social search</button>
              <div class="container-siglas">
                <p class = siglas>{{ datosAlmacenados.archivoSs}}</p>
                <fa @click="copiarSs" :icon="['far', 'copy']" size="xs" style="cursor: pointer;color: #ffffff;" />
              </div>
            </div>

          </div>
          <div class="container-bot">
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Truora">Truora</button>
              <div class="container-siglas">
                <p class = siglas>{{ datosAlmacenados.archivoTruora}}</p>
                <fa @click="copiarTruora" :icon="['far', 'copy']" size="xs" style="cursor: pointer;color: #ffffff;" />
              </div>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Ramajudicial">Rama judicial</button>
              <div class="container-siglas">
                <p class = siglas>{{ datosAlmacenados.archivoRj}}</p>
                <fa @click="copiarRj" :icon="['far', 'copy']" size="xs" style="cursor: pointer;color: #ffffff;" />
              </div>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Offshoreleaks">Offshoreleaks</button>
              <div class="container-siglas">
                <p class = siglas>{{ datosAlmacenados.archivoOff}}</p>
                <fa @click="copiarOff" :icon="['far', 'copy']" size="xs" style="cursor: pointer;color: #ffffff;" />
              </div>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Wc">Wc</button>
              <div class="container-siglas">
                <p class = siglas>{{ datosAlmacenados.archivoWc}}</p>
                <fa @click="copiarWc" :icon="['far', 'copy']" size="xs" style="cursor: pointer;color: #ffffff;" />
              </div>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Contaduria">Contaduría</button>
              <div class="container-siglas">
                <p class = siglas>{{ datosAlmacenados.archivoContaduria}}</p>
                <fa @click="copiarContaduria" :icon="['far', 'copy']" size="xs" style="cursor: pointer;color: #ffffff;" />
              </div>
            </div>
            <div class="container-bot-b">
              <button class="botonbusqueda" @click="Contaduria">Contaduría</button>
              <div class="container-siglas">
                <p class = siglas>{{ datosAlmacenados.archivoContaduria}}</p>
                <fa @click="copiarContaduria" :icon="['far', 'copy']" size="xs" style="cursor: pointer;color: #ffffff;" />
              </div>
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
        nombre: '', // Variable reactiva para almacenar el valor del input
        apellido:'', 
        datosAlmacenados: null, // Para almacenar los datos cuando se envíen
        formularioVisible: true,
        iniciales: '',
      };
    },
    methods: {

      almacenarDatos() {
        // Obtener el texto del label
        const textoLabel = 'Ingresa tu nombre:';

        const conca = `${this.nombre} ${this.apellidos}`;
        this.iniciales = this.obtenerIniciales(conca);

        // Almacenar los datos
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


        };

        this.formularioVisible = false;

        
        // Limpiar el campo de texto
        this.nombre = '';
        this.apellidos = '';
        this.documento = '';
      },
      copy(texto) {
        navigator.clipboard.writeText(texto)
      },

      copiarLinkedin(archivoTemp) {
        if (archivoTemp) {
          const texto = this.datosAlmacenados.archivoTemp;
          this.copy(texto);
        }
      },
      copiarPep() {
        if (this.datosAlmacenados && this.datosAlmacenados.archivoPEP) {
          const texto = this.datosAlmacenados.archivoPEP;
          this.copy(texto);
        }
      },
      copiarInforma() {
        if (this.datosAlmacenados && this.datosAlmacenados.archivoInforma) {
          const texto = this.datosAlmacenados.archivoInforma;
          this.copy(texto);
        }
      },
      copiarCorrupcion() {
        if (this.datosAlmacenados && this.datosAlmacenados.archivoCorrupcion) {
          const texto = this.datosAlmacenados.archivoCorrupcion;
          this.copy(texto);
        }
      },
      copiarNarcotrafico() {
        if (this.datosAlmacenados && this.datosAlmacenados.archivoNarcotrafico) {
          const texto = this.datosAlmacenados.archivoNarcotrafico;
          this.copy(texto);
        }
      },
      copiarLavado() {
        if (this.datosAlmacenados && this.datosAlmacenados.archivoLavado) {
          const texto = this.datosAlmacenados.archivoLavado;
          this.copy(texto);
        }
      },
      copiarFraude() {
        if (this.datosAlmacenados && this.datosAlmacenados.archivoFraude) {
          const texto = this.datosAlmacenados.archivoFraude;
          this.copy(texto);
        }
      },
      copiarFace() {
        if (this.datosAlmacenados && this.datosAlmacenados.archivoFace) {
          const texto = this.datosAlmacenados.archivoFace;
          this.copy(texto);
        }
      },
      copiarFacebook() {
        if (this.datosAlmacenados && this.datosAlmacenados.archivoFacebook) {
          const texto = this.datosAlmacenados.archivoFacebook;
          this.copy(texto);
        }
      },
      copiarInstagram() {
        if (this.datosAlmacenados && this.datosAlmacenados.archivoInstagram) {
          const texto = this.datosAlmacenados.archivoInstagram;
          this.copy(texto);
        }
      },
      copiarTiktok() {
        if (this.datosAlmacenados && this.datosAlmacenados.archivoTiktok) {
          const texto = this.datosAlmacenados.archivoTiktok;
          this.copy(texto);
        }
      },
      copiarPinterest() {
        if (this.datosAlmacenados && this.datosAlmacenados.archivoPinterest) {
          const texto = this.datosAlmacenados.archivoPinterest;
          this.copy(texto);
        }
      },
      copiarX() {
        if (this.datosAlmacenados && this.datosAlmacenados.archivoX) {
          const texto = this.datosAlmacenados.archivoX;
          this.copy(texto);
        }
      },
      copiarYoutube() {
        if (this.datosAlmacenados && this.datosAlmacenados.archivoYoutube) {
          const texto = this.datosAlmacenados.archivoYoutube;
          this.copy(texto);
        }
      },
      copiarSs() {
        if (this.datosAlmacenados && this.datosAlmacenados.archivoSs) {
          const texto = this.datosAlmacenados.archivoSs;
          this.copy(texto);
        }
      },
      copiarTruora() {
        if (this.datosAlmacenados && this.datosAlmacenados.archivoTruora) {
          const texto = this.datosAlmacenados.archivoTruora;
          this.copy(texto);
        }
      },
      copiarRj() {
        if (this.datosAlmacenados && this.datosAlmacenados.archivoRj) {
          const texto = this.datosAlmacenados.archivoRj;
          this.copy(texto);
        }
      },
      copiarOff() {
        if (this.datosAlmacenados && this.datosAlmacenados.archivoOff) {
          const texto = this.datosAlmacenados.archivoOff;
          this.copy(texto);
        }
      },
      copiarWc() {
        if (this.datosAlmacenados && this.datosAlmacenados.archivoWc) {
          const texto = this.datosAlmacenados.archivoWc;
          this.copy(texto);
        }
      },
      copiarContaduria() {
        if (this.datosAlmacenados && this.datosAlmacenados.archivoContaduria) {
          const texto = this.datosAlmacenados.archivoContaduria;
          this.copy(texto);
        }
      },

      obtenerIniciales(cadena){
        return cadena
          .split(' ')
          .map(palabra => palabra.charAt(0).toUpperCase())
          .join('');

      },

      Linkedin() {
        const archivoLinkedin = this.datosAlmacenados.archivoLinkedin;
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Linkedin`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.copiarLinkedin(archivoLinkedin)
        window.open(urlBusqueda, '_blank');
      },
      Pep() {
      const consulta = `${this.datosAlmacenados.documentoId}`;
      const urlBusqueda = `https://www.funcionpublica.gov.co/fdci/consultaCiudadana/consultaPEP?tipoRegistro=0&numeroDocumento=${encodeURIComponent(consulta)}&primerNombre=&segundoNombre=&primerApellido=&segundoApellido=&entidad=&dpto=&mun=&find=Buscar#resultadosBusqueda`;
      window.open(urlBusqueda, '_blank');
      },
      Informa() {
      const urlBusqueda = `https://www.informacolombia.com/InformaIntWeb/Main/id_sess/00081623158000034624480000041879/idioma/01/activa/2/id_tmp/974.0/prod/VINCULACIONES_RESULTADO_CONTEO/prod_desde/BUSCADOR_VINCULACIONES`;
      window.open(urlBusqueda, '_blank');
      },  
      Corrupcion() {
      const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Corrupción`;
      const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
      window.open(urlBusqueda, '_blank');
      },
      Narcotrafico() {
      const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Narcotráfico`;
      const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
      window.open(urlBusqueda, '_blank');
      },
      Lavado() {
      const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Lavado de`;
      const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
      window.open(urlBusqueda, '_blank');
      },
      Fraude() {
      const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Fraude`;
      const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
      window.open(urlBusqueda, '_blank');
      },
      Facesearch() {
      const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA}`;
      const urlBusqueda = `https://www.google.com/search?hl=es&tbm=isch&q=${encodeURIComponent(consulta)}`;
      window.open(urlBusqueda, '_blank');
      },
      Facebook() {
      const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Facebook`;
      const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
      window.open(urlBusqueda, '_blank');
      },   
      Instagram() {
      const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Instagram`;
      const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
      window.open(urlBusqueda, '_blank');
      },   
      TikTok() {
      const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + TikTok`;
      const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
      window.open(urlBusqueda, '_blank');
      },   
      Pinterest() {
      const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Pinterest`;
      const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
      window.open(urlBusqueda, '_blank');
      },   
      Twitter() {
      const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + X`;
      const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
      window.open(urlBusqueda, '_blank');
      },  
      Youtube() {
      const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Youtube`;
      const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
      window.open(urlBusqueda, '_blank');
      }, 
      Socialsearch() {
      const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.apellidosSS}`;
      const urlBusqueda = `https://www.social-searcher.com/social-buzz/?q5=${encodeURIComponent(consulta)}`;
      window.open(urlBusqueda, '_blank');
      },    
      Truora() {
      const urlBusqueda = `https://checks.truora.com/#/dashboard/check/custom`;
      window.open(urlBusqueda, '_blank');
      },    
      Ramajudicial() {
      const urlBusqueda = `https://consultaprocesos.ramajudicial.gov.co/Procesos/NombreRazonSocial`;
      window.open(urlBusqueda, '_blank');
      }, 
      Offshoreleaks() {
      const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Offshoreleaks`;
      const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
      window.open(urlBusqueda, '_blank');
      }, 
      Wc() {
      const urlBusqueda = `https://members.worldcompliance.com/SignIn.aspx`;
      window.open(urlBusqueda, '_blank');
      },
      Contaduria() {
      const urlBusqueda = `https://eris.contaduria.gov.co/BDME/#`;
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
  .titulo{font-size: 50px;text-align: center;color:#ffffff;}
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
    color: white;
    font-family: 'Bubbler One', sans-serif;
    font-size: 15px;
    padding: 10px;
    border: none;
    border-radius: 10px;
    outline: 2px solid white;
    background-color: transparent;
    transition: outline-color 500ms;
    margin: 20px;

  }
  .input-container-input::placeholder{
    color:#ffffff;
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
    color: #ffffff;
    font-size: 25px;

  }
  .container-datos-i{
    display:flex;
    flex-direction: column;
    margin: 20px;
  }
  .titulo2{font-size: 50px;text-align: center;color:#ffffff;margin:10px;}

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
  .container-siglas{
    display: flex;
    align-items: center;
    height: 20px;
  }
  .siglas{font-size:15px; margin: 20px;margin-left: 0;}
  .container-bot-b{
    display: flex;
    justify-content: flex-start;

  }

  .botonbusqueda{
    width: 30%;
    margin-right: 20%;
    height: 20px;
  }
  </style>