<template>
    <div class="box-container">
      <form v-if="formularioVisible" @submit.prevent="almacenarDatos" class="container-formulario">
        <label for="nombre" class="titulo">Indagacion Terceros</label>
        <div class="container-inputs">
          <input type="text" class="input-container-input" id="nombre" v-model="nombre" placeholder="Ingrese el nombre" required>
          <input type="text" class="input-container-input" id="apellidos" v-model="apellidos" placeholder="Ingrese el apellido">
          <input type="number" class="input-container-input" id="documento" v-model="documento" placeholder="Cédula de ciudadanía">

        </div>
        <div class="boton-cargar">
          <fa @click="almacenarDatos" :icon="['fas', 'circle-right']" size="2xl" style="cursor: pointer;color: var(--color-azul-kp);"/>
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
            <div class="container-clases"><div class="container-icon"><fa :icon="['fas', 'eye']" style="color: var(--color-azul-kp);" /></div><div class="titulo-clase">IDENTIFICACIÓN</div></div>
            
            <div class="container-bot-b" @click="Linkedin">
              <div class="container-icon"><fa :icon="['fab', 'linkedin']" style="color: var(--color-azul-kp);" /></div>
              <div class="botonbusqueda" >Linkedin</div>
              <fa :icon="['fas', 'circle-check']" style="color: var(--color-azul-kp);" v-show="datosAlmacenados.flagCheckout[0]" />
            </div>
            <div class="container-bot-b" @click="Pep">
              <div class="container-icon"><fa :icon="['fas', 'bullhorn']" style="color: var(--color-azul-kp);" /></div>
              <div class="botonbusqueda">PEP</div>
              <fa :icon="['fas', 'circle-check']" style="color: var(--color-azul-kp);" v-show="datosAlmacenados.flagCheckout[1]"/>
            </div>
            <div class="container-bot-b" @click="Informa">
              <div class="container-icon"><fa :icon="['fas', 'users-between-lines']" style="color: var(--color-azul-kp);" /></div>
              <div class="botonbusqueda">Informa</div>
              <fa :icon="['fas', 'circle-check']" style="color: var(--color-azul-kp);" v-show="datosAlmacenados.flagCheckout[2]"/>
            </div>
          </div>
          <div class="container-bot">
            <div class="container-bot-b" @click="Corrupcion">
              <div class="container-icon"><fa :icon="['fas', 'comments-dollar']" style="color: var(--color-azul-kp);" /></div>
              <div class="botonbusqueda">Corrupción</div>
              <fa :icon="['fas', 'circle-check']" style="color: var(--color-azul-kp);" v-show="datosAlmacenados.flagCheckout[3]"/>
            </div>
            <div class="container-bot-b" @click="Narcotrafico">
              <div class="container-icon"><fa :icon="['fas', 'person-rifle']" style="color: var(--color-azul-kp);" /></div>
              <div class="botonbusqueda">Narcotráfico</div>
              <fa :icon="['fas', 'circle-check']" style="color: var(--color-azul-kp);" v-show="datosAlmacenados.flagCheckout[4]"/>
            </div>
            <div class="container-bot-b" @click="Lavado">
              <div class="container-icon"><fa :icon="['fas', 'sack-dollar']" style="color: var(--color-azul-kp);" /></div>
              <div class="botonbusqueda">Lavado de</div>
              <fa :icon="['fas', 'circle-check']" style="color: var(--color-azul-kp);" v-show="datosAlmacenados.flagCheckout[5]"/>
            </div>
            <div class="container-bot-b">
              <div class="container-icon"><fa :icon="['fas', 'magnifying-glass-dollar']" style="color: var(--color-azul-kp);" /></div>
              <div class="botonbusqueda" @click="Fraude">Fraude</div>
              <fa :icon="['fas', 'circle-check']" style="color: var(--color-azul-kp);" v-show="datosAlmacenados.flagCheckout[6]"/>
            </div>
            <div class="container-bot-b" @click="Facesearch">
              <div class="container-icon"><fa :icon="['fas', 'user-secret']" style="color: var(--color-azul-kp);" /></div>
              <div class="botonbusqueda">Facesearch</div>
              <fa :icon="['fas', 'circle-check']" style="color: var(--color-azul-kp);" v-show="datosAlmacenados.flagCheckout[7]"/>
            </div>
          </div>
          <div class="container-bot">
            <div class="container-bot-b" @click="Facebook">
              <div class="container-icon"><fa :icon="['fab', 'square-facebook']" style="color: var(--color-azul-kp);" /></div>
              <div class="botonbusqueda">Facebook</div>
              <fa :icon="['fas', 'circle-check']" style="color: var(--color-azul-kp);" v-show="datosAlmacenados.flagCheckout[8]"/>
            </div>
            <div class="container-bot-b" @click="Instagram">
              <div class="container-icon"><fa :icon="['fab', 'square-instagram']" style="color: var(--color-azul-kp);" /></div>
              <div class="botonbusqueda">Instagram</div>
              <fa :icon="['fas', 'circle-check']" style="color: var(--color-azul-kp);" v-show="datosAlmacenados.flagCheckout[9]"/>
            </div>
            <div class="container-bot-b" @click="TikTok">
              <div class="container-icon"><fa :icon="['fab', 'tiktok']" style="color: var(--color-azul-kp);" /></div>
              <div class="botonbusqueda">TikTok</div>
              <fa :icon="['fas', 'circle-check']" style="color: var(--color-azul-kp);" v-show="datosAlmacenados.flagCheckout[10]"/>
            </div>
            <div class="container-bot-b" @click="Pinterest">
              <div class="container-icon"><fa :icon="['fab', 'pinterest']" style="color: var(--color-azul-kp);" /></div>
              <div class="botonbusqueda">Pinterest</div>
              <fa :icon="['fas', 'circle-check']" style="color: var(--color-azul-kp);" v-show="datosAlmacenados.flagCheckout[11]"/>
            </div>
            <div class="container-bot-b" @click="Twitter">
              <div class="container-icon"><fa :icon="['fab', 'square-x-twitter']" style="color: var(--color-azul-kp);" /></div>
              <div class="botonbusqueda">X</div>
              <fa :icon="['fas', 'circle-check']" style="color: var(--color-azul-kp);" v-show="datosAlmacenados.flagCheckout[12]"/>
            </div>
            <div class="container-bot-b" @click="Youtube">
              <div class="container-icon"><fa :icon="['fab', 'square-youtube']" style="color: var(--color-azul-kp);" /></div>
              <div class="botonbusqueda">Youtube</div>
              <fa :icon="['fas', 'circle-check']" style="color: var(--color-azul-kp);" v-show="datosAlmacenados.flagCheckout[13]"/>
            </div>
            <div class="container-bot-b" @click="Socialsearch">
              <div class="container-icon"><fa :icon="['fas', 'users']" style="color: var(--color-azul-kp);" /></div>
              <div class="botonbusqueda">Social search</div>
              <fa :icon="['fas', 'circle-check']" style="color: var(--color-azul-kp);" v-show="datosAlmacenados.flagCheckout[14]"/>
            </div>
          </div>
          <div class="container-bot">
            <div class="container-bot-b" @click="Truora">
              <div class="container-icon"><fa :icon="['far', 'folder-open']" style="color: var(--color-azul-kp);" /></div>
              <div class="botonbusqueda">Truora</div>
              <fa :icon="['fas', 'circle-check']" style="color: var(--color-azul-kp);" v-show="datosAlmacenados.flagCheckout[15]"/>
            </div>
            <div class="container-bot-b" @click="Ramajudicial">
              <div class="container-icon"><fa :icon="['fas', 'gavel']" style="color: var(--color-azul-kp);" /></div>
              <div class="botonbusqueda">Rama judicial</div>
              <fa :icon="['fas', 'circle-check']" style="color: var(--color-azul-kp);" v-show="datosAlmacenados.flagCheckout[16]"/>
            </div>
            <div class="container-bot-b" @click="Offshoreleaks">
              <div class="container-icon"><fa :icon="['fas', 'magnifying-glass']" style="color: var(--color-azul-kp);" /></div>
              <div class="botonbusqueda">Offshoreleaks</div>
              <fa :icon="['fas', 'circle-check']" style="color: var(--color-azul-kp);" v-show="datosAlmacenados.flagCheckout[17]"/>
            </div>
            <div class="container-bot-b" @click="Wc">
              <div class="container-icon"><fa :icon="['fas', 'handcuffs']" style="color: var(--color-azul-kp);" /></div>
              <div class="botonbusqueda">Wc</div>
              <fa :icon="['fas', 'circle-check']" style="color: var(--color-azul-kp);" v-show="datosAlmacenados.flagCheckout[18]"/>
            </div>
            <div class="container-bot-b" @click="Contaduria">
              <div class="container-icon"><fa :icon="['fas', 'money-bill-transfer']" style="color: var(--color-azul-kp);" /></div>
              <div class="botonbusqueda">Contaduría</div>
              <fa :icon="['fas', 'circle-check']" style="color: var(--color-azul-kp);" v-show="datosAlmacenados.flagCheckout[19]"/>
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
          flagCheckout: [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0],
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
        this.datosAlmacenados.flagCheckout[0] = 1;
        window.open(urlBusqueda, '_blank');
      },
      Pep() {
        const consulta = `${this.datosAlmacenados.documentoId}`;
        const urlBusqueda = `https://www.funcionpublica.gov.co/fdci/consultaCiudadana/consultaPEP?tipoRegistro=0&numeroDocumento=${encodeURIComponent(consulta)}&primerNombre=&segundoNombre=&primerApellido=&segundoApellido=&entidad=&dpto=&mun=&find=Buscar#resultadosBusqueda`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoPEP;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        this.datosAlmacenados.flagCheckout[1] = 1;
        window.open(urlBusqueda, '_blank');
      },
      Informa() {
        const urlBusqueda = `https://www.informacolombia.com/InformaIntWeb/Main/id_sess/00081623158000034624480000041879/idioma/01/activa/2/id_tmp/974.0/prod/VINCULACIONES_RESULTADO_CONTEO/prod_desde/BUSCADOR_VINCULACIONES`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoInforma;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        this.datosAlmacenados.flagCheckout[2] = 1;
        window.open(urlBusqueda, '_blank');
      },  
      Corrupcion() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Corrupción`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoCorrupcion;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        this.datosAlmacenados.flagCheckout[3] = 1;
        window.open(urlBusqueda, '_blank');
      },
      Narcotrafico() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Narcotráfico`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoNarcotrafico;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        this.datosAlmacenados.flagCheckout[4] = 1;
        window.open(urlBusqueda, '_blank');
      },
      Lavado() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Lavado de`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoLavado;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        this.datosAlmacenados.flagCheckout[5] = 1;
        window.open(urlBusqueda, '_blank');
      },
      Fraude() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Fraude`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoFraude;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        this.datosAlmacenados.flagCheckout[6] = 1;
        window.open(urlBusqueda, '_blank');
      },
      Facesearch() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA}`;
        const urlBusqueda = `https://www.google.com/search?hl=es&tbm=isch&q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoFace;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        this.datosAlmacenados.flagCheckout[7] = 1;
        window.open(urlBusqueda, '_blank');
      },
      Facebook() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Facebook`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoFacebook;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        this.datosAlmacenados.flagCheckout[8] = 1;
        window.open(urlBusqueda, '_blank');
      },   
      Instagram() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Instagram`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoInstagram;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        this.datosAlmacenados.flagCheckout[9] = 1;
        window.open(urlBusqueda, '_blank');
      },   
      TikTok() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + TikTok`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoTiktok;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        this.datosAlmacenados.flagCheckout[10] = 1;
        window.open(urlBusqueda, '_blank');
      },   
      Pinterest() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Pinterest`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoPinterest;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        this.datosAlmacenados.flagCheckout[11] = 1;
        window.open(urlBusqueda, '_blank');
      },   
      Twitter() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + X`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoX;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        this.datosAlmacenados.flagCheckout[12] = 1;
        window.open(urlBusqueda, '_blank');
      },  
      Youtube() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Youtube`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoYoutube;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        this.datosAlmacenados.flagCheckout[13] = 1;
        window.open(urlBusqueda, '_blank');
      },
      Socialsearch() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.apellidosSS}`;
        const urlBusqueda = `https://www.social-searcher.com/social-buzz/?q5=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoSs;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        this.datosAlmacenados.flagCheckout[14] = 1;
        window.open(urlBusqueda, '_blank');
      },    
      Truora() {
        const urlBusqueda = `https://checks.truora.com/#/dashboard/check/custom`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoTruora;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        this.datosAlmacenados.flagCheckout[15] = 1;
        window.open(urlBusqueda, '_blank');
      },    
      Ramajudicial() {
        const urlBusqueda = `https://consultaprocesos.ramajudicial.gov.co/Procesos/NombreRazonSocial`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoRj;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        this.datosAlmacenados.flagCheckout[16] = 1;
        window.open(urlBusqueda, '_blank');
      }, 
      Offshoreleaks() {
        const consulta = `${this.datosAlmacenados.valorN} ${this.datosAlmacenados.valorA} + Offshoreleaks`;
        const urlBusqueda = `https://www.google.com/search?q=${encodeURIComponent(consulta)}`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoOff;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        this.datosAlmacenados.flagCheckout[17] = 1;
        window.open(urlBusqueda, '_blank');
      }, 
      Wc() {
        const urlBusqueda = `https://members.worldcompliance.com/SignIn.aspx`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoWc;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        this.datosAlmacenados.flagCheckout[18] = 1;
        window.open(urlBusqueda, '_blank');
      },
      Contaduria() {
        const urlBusqueda = `https://eris.contaduria.gov.co/BDME/#`;
        this.datosAlmacenados.archivoTemp = this.datosAlmacenados.archivoContaduria;
        this.copyPaste(this.datosAlmacenados.archivoTemp);
        this.datosAlmacenados.flagCheckout[19] = 1;
        window.open(urlBusqueda, '_blank');
      } 
      
    }
  };
  </script>
  <style scoped>

  .box-container {
    width: 90%;
    height: 90%;
    display: flex;
    position: absolute;
    justify-content: space-evenly;
    justify-items: center;
    align-items: center;
    border-radius: 8px;
  }
  input[type="number"]::-webkit-outer-spin-button, input[type="number"]::-webkit-inner-spin-button {-webkit-appearance: none;}
  
  .container-formulario{
    height: 320px;
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    padding: 10px;
    border-radius: 15px;
    border: 8px solid var(--color-azul-morado);
    background: linear-gradient(135deg, var(--color-gradiente-inicio), var(--color-gradiente-fin));
    backdrop-filter: blur(10px);
    box-shadow: 0 10px 20px var(--color-azul-morado);
    background-color: #DBDBDB;

  }
  .titulo{font-size: 40px;text-align: center;color:var(--color-azul-kp);}
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
    color: var(--color-morado-claro2);
    font-family: 'Bubbler One', sans-serif;
    font-size: 15px;
    padding: 8px;
    border: none;
    border-radius: 10px;
    outline: none;
    border-bottom: 2px solid var(--color-morado-claro2);
    background: linear-gradient(0deg, var(--color-morado-clarot), var(--color-gradiente-fin2));
    margin: 10px;
    margin-top: 0px;
    transition: border-bottom-color 1s ease-in;
  }
  .input-container-input:focus{
    background: linear-gradient(0deg, var(--color-morado-clarot), var(--color-gradiente-fin));
    border-bottom: 2px solid var(--color-azul-kp);
    transition: border-bottom-color 1s ease-out;
  }
  .input-container-input::placeholder{
    color:var(--color-azul-kp);
    opacity: .7;
  }
  .boton-cargar{
    height: 50%;
    display: flex;
    flex-direction: column;
    align-items: center;
    max-height: 32px;
  }
  .b-botoncargar{width: 10%;}

  .container-datos{
    display: flex ;
    max-width: 1200px;
    width: 90%;
    font-family: 'Bubbler One', sans-serif;
    flex-direction: column;
    color: var(--color-azul-kp);
    font-size: 25px;

  }
  .container-datos-i{
    display:flex;
    max-width: 1200px;
    flex-direction: column;
    margin: 20px;
    padding: 20px;
    border-radius: 15px;
    border: 8px solid var(--color-azul-morado);
    background: linear-gradient(135deg, var(--color-gradiente-inicio), var(--color-gradiente-fin));
    backdrop-filter: blur(10px);
    box-shadow: 0 10px 20px var(--color-azul-morado);
    background-color: #DBDBDB;
  }
  .titulo2{font-size: 50px;font-family: 'Anton', sans-serif;text-align: start;color:var(--color-azul-kp);margin:0px;}

  .parrafo{margin: 0;padding: 0;}

  .container-buttons{
    display:flex;
    max-width: 1200px;
    flex-flow: row wrap;
    margin: 20px;
    padding: 10px;
    border-radius: 15px;
    border: 8px solid var(--color-azul-morado);
    background: linear-gradient(135deg, var(--color-gradiente-inicio), var(--color-gradiente-fin));
    backdrop-filter: blur(10px);
    box-shadow: 0 10px 20px var(--color-azul-morado);
    background-color: #DBDBDB;
    justify-content: space-evenly;
  }
  .container-bot{
    display: inline-flex;
    flex-direction: column;
    margin: 5px;
    padding: 5px;
  }
  .container-bot-b{
    display: flex;
    justify-content: flex-start;
    align-items: center;    
    cursor:pointer;
    min-width: 135px;
    height: 30px;
  }

  .container-clases{
    display: flex;
    justify-content: space-around;
    align-items: center;
    height: 35px;
    width: 150px;
    margin-bottom: 10px;
    border-bottom: 1px solid var( --color-azul-claro);
    box-shadow: 0 4px 6px #ffffffa9;
    border-radius: 30px;
  }
  .titulo-clase{
    font-size: 16px;
    font-family: 'Anton', sans-serif;
    color: var(--color-azul-kp);
  }
  .botonbusqueda{
    display: flex;
    padding: 0px;
    min-width: 95px;
    justify-content: center;
    color:var(--color-azul-kp);
    background-color: transparent;
    border: none;
    font-size: 14px;
    font-family: 'Bubbler One', sans-serif;
    transition: color .3s ease-in, font-weight .3s ease-in, font-size .3s ease-in;
  }
  .container-icon{
    display: flex;
    justify-content: center;
    align-items: center;
    height: 30px;
    width: 30px;
  }
  .botonbusqueda:hover{
    color: var(--color-azul-morado);
    transition: color .3s ease-out, font-weight .3s ease-out, font-size .3s ease-out;
    font-weight: bold;
    font-size: 16px;
  }
  </style>