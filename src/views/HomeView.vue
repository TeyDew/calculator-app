<template>
  <div class="home">
    <div class="circle"></div>
    <nav class="settings">
      <ul>
        <li>
          <span>Thème</span>
          <input class="tgl tgl-flat" id="cb1" type="checkbox" v-model="darkTheme"/>
          <label class="tgl-btn" for="cb1"></label>
        </li>
        <li>
          <span>Transparence</span>
          <input class="tgl tgl-flat" id="cb2" type="checkbox" v-model="transparent" checked/>
          <label class="tgl-btn" for="cb2"></label>
        </li>
      </ul>
    </nav>
    <div class="calculator" :class="calculatorClasses">
      <div class="top-section">
        <span class="operation">{{ expression }}</span>
        <h1 :style="{ fontSize: resultFontSize }">{{ result }}</h1>
      </div>
      <div class="button-section">
        <div class="row rowMin">
          <button class="minH bgWhite" @click="buttonClick('2.71828')">
            <svg width="10" height="12" viewBox="0 0 10 12" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M9.86001 5.52304C9.86001 5.85904 9.83602 6.15304 9.78802 6.40504H2.15601C2.19201 7.42504 2.47401 8.18104 3.00201 8.67304C3.53001 9.16504 4.18402 9.41104 4.96402 9.41104C5.64802 9.41104 6.22402 9.23704 6.69202 8.88904C7.17202 8.54104 7.46602 8.07904 7.57402 7.50304H9.77002C9.63802 8.19904 9.36201 8.81704 8.94202 9.35704C8.52202 9.89704 7.97602 10.323 7.30402 10.635C6.63202 10.935 5.88202 11.085 5.05402 11.085C4.09402 11.085 3.24201 10.881 2.49801 10.473C1.76602 10.065 1.19001 9.47704 0.770015 8.70904C0.350015 7.94104 0.140015 7.03504 0.140015 5.99104C0.140015 4.95904 0.350015 4.05904 0.770015 3.29104C1.19001 2.52304 1.76602 1.93504 2.49801 1.52704C3.24201 1.11904 4.09402 0.915039 5.05402 0.915039C6.02602 0.915039 6.87201 1.11904 7.59202 1.52704C8.32402 1.92304 8.88202 2.47504 9.26602 3.18304C9.66201 3.87904 9.86001 4.65904 9.86001 5.52304ZM7.79002 5.46904C7.81402 4.82104 7.70002 4.28104 7.44802 3.84904C7.20801 3.40504 6.87201 3.08104 6.44002 2.87704C6.02001 2.66104 5.55801 2.55304 5.05402 2.55304C4.25002 2.55304 3.57801 2.79904 3.03801 3.29104C2.49801 3.78304 2.20401 4.50904 2.15601 5.46904H7.79002Z"/>
            </svg>
          </button>
          <button class="minH bgWhite" @click="buttonClick('3,14159')">
            <svg width="12" height="12" viewBox="0 0 12 12" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M5.335 0.234366C2.54357 0.296866 1.68966 0.529678 1.16976 1.3703C1.01258 1.62499 0.897723 1.89374 0.59999 2.71093C0.48664 3.0203 0.353642 3.37655 0.30528 3.50155L0.2146 3.73124L0.330972 3.74062C0.394448 3.74687 0.489663 3.75468 0.544071 3.75937L0.642307 3.76874L0.720897 3.6453C0.763214 3.57812 0.858428 3.41718 0.930972 3.28905C1.10478 2.97655 1.21813 2.81874 1.38437 2.64687C1.7078 2.31405 2.10679 2.12343 2.65994 2.03749C2.8549 2.00624 3.37933 1.99843 3.66347 2.02187L3.8282 2.03437L3.81762 2.34218C3.76473 3.96874 3.56221 5.27812 3.1874 6.42812C3.0544 6.84062 2.935 7.13593 2.74306 7.53905C2.48311 8.08437 2.25188 8.46718 1.78488 9.12499C1.38286 9.69218 1.27102 9.88124 1.19243 10.1172C1.14256 10.2672 1.14256 10.5844 1.19092 10.7734C1.23173 10.9312 1.33903 11.1516 1.43727 11.2781C1.69269 11.6078 2.15364 11.8094 2.55112 11.7641C2.75515 11.7406 2.90478 11.6984 3.06347 11.6172C3.37631 11.4578 3.58941 11.2125 3.78588 10.7891C4.07455 10.1672 4.2544 9.29374 4.42669 7.67968C4.50226 6.98124 4.54911 6.45312 4.7607 3.8828C4.80301 3.37499 4.85591 2.74999 4.87858 2.49218L4.91939 2.02343L6.19344 2.01874C7.20603 2.01562 7.46598 2.01874 7.46598 2.03437C7.46598 2.0453 7.45541 2.20155 7.44331 2.3828C7.39042 3.16405 7.35415 3.58749 7.23173 4.89062C7.03374 6.98749 6.98085 7.66562 6.93702 8.66405C6.90226 9.47343 6.93097 9.82343 7.06699 10.25C7.32392 11.0531 7.90427 11.5734 8.70528 11.7219C8.93954 11.7641 9.38689 11.7672 9.59697 11.7281C10.2227 11.6109 10.738 11.2328 11.14 10.5953C11.3274 10.3 11.5043 9.89062 11.6146 9.4953C11.7143 9.1453 11.7884 8.69374 11.7884 8.4453V8.34374H11.5693H11.3501V8.41093C11.3501 8.52812 11.3048 8.76718 11.2489 8.94218C11.0735 9.49218 10.6957 9.7953 10.1184 9.84999C9.88563 9.87187 9.53802 9.79687 9.36271 9.68437C8.98639 9.4453 8.78689 9.01562 8.6947 8.24999C8.67656 8.09218 8.67052 7.90937 8.66901 7.52343C8.66901 6.85468 8.68563 6.59374 8.8413 4.92187C8.96825 3.5578 9.00301 3.07343 9.02115 2.42499L9.03022 2.06093L10.4101 2.06249L11.7884 2.06405V1.34687C11.7884 0.953116 11.7839 0.545303 11.7793 0.442178L11.7688 0.254678L11.2761 0.243741C10.469 0.228116 5.94709 0.220303 5.335 0.234366Z"/>
            </svg>
          </button>
          <button class="minH bgWhite" @click="buttonClick('%')">%</button>
          <button class="minH bgWhite" @click="buttonClick('deg')">
            <svg width="34" height="20" viewBox="0 0 34 20" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M4.71613 4.18603C5.61613 4.18603 6.38413 4.40803 7.02013 4.85203C7.65613 5.29603 8.10013 5.88403 8.35213 6.61603V0.910034H10.4221V14.23H8.35213V11.926C8.10013 12.658 7.65613 13.246 7.02013 13.69C6.38413 14.134 5.61613 14.356 4.71613 14.356C3.85213 14.356 3.07813 14.152 2.39413 13.744C1.72213 13.336 1.19413 12.748 0.810131 11.98C0.426131 11.212 0.234131 10.306 0.234131 9.26203C0.234131 8.23003 0.426131 7.33003 0.810131 6.56203C1.19413 5.79403 1.72213 5.20603 2.39413 4.79803C3.07813 4.39003 3.85213 4.18603 4.71613 4.18603ZM5.34613 5.98603C4.43413 5.98603 3.70213 6.28003 3.15013 6.86803C2.61013 7.44403 2.34013 8.24203 2.34013 9.26203C2.34013 10.282 2.61013 11.086 3.15013 11.674C3.70213 12.25 4.43413 12.538 5.34613 12.538C5.92213 12.538 6.43813 12.406 6.89413 12.142C7.35013 11.866 7.71013 11.482 7.97413 10.99C8.23813 10.498 8.37013 9.92203 8.37013 9.26203C8.37013 8.61403 8.23813 8.04403 7.97413 7.55203C7.71013 7.04803 7.35013 6.66403 6.89413 6.40003C6.43813 6.12403 5.92213 5.98603 5.34613 5.98603Z"/>
              <path d="M22.1006 8.79403C22.1006 9.13003 22.0766 9.42403 22.0286 9.67603H14.3966C14.4326 10.696 14.7146 11.452 15.2426 11.944C15.7706 12.436 16.4246 12.682 17.2046 12.682C17.8886 12.682 18.4646 12.508 18.9326 12.16C19.4126 11.812 19.7066 11.35 19.8146 10.774H22.0106C21.8786 11.47 21.6026 12.088 21.1826 12.628C20.7626 13.168 20.2166 13.594 19.5446 13.906C18.8726 14.206 18.1226 14.356 17.2946 14.356C16.3346 14.356 15.4826 14.152 14.7386 13.744C14.0066 13.336 13.4306 12.748 13.0106 11.98C12.5906 11.212 12.3806 10.306 12.3806 9.26203C12.3806 8.23003 12.5906 7.33003 13.0106 6.56203C13.4306 5.79403 14.0066 5.20603 14.7386 4.79803C15.4826 4.39003 16.3346 4.18603 17.2946 4.18603C18.2666 4.18603 19.1126 4.39003 19.8326 4.79803C20.5646 5.19403 21.1226 5.74603 21.5066 6.45403C21.9026 7.15003 22.1006 7.93003 22.1006 8.79403ZM20.0306 8.74003C20.0546 8.09203 19.9406 7.55203 19.6886 7.12003C19.4486 6.67603 19.1126 6.35203 18.6806 6.14803C18.2606 5.93203 17.7986 5.82403 17.2946 5.82403C16.4906 5.82403 15.8186 6.07003 15.2786 6.56203C14.7386 7.05403 14.4446 7.78003 14.3966 8.74003H20.0306Z"/>
              <path d="M28.0599 4.18603C28.9599 4.18603 29.7279 4.40803 30.3639 4.85203C30.9999 5.29603 31.4499 5.88403 31.7139 6.61603V4.31203H33.7659V14.338C33.7659 15.262 33.5739 16.078 33.1899 16.786C32.8179 17.506 32.2779 18.07 31.5699 18.478C30.8619 18.886 30.0219 19.09 29.0499 19.09C27.6579 19.09 26.5299 18.76 25.6659 18.1C24.8139 17.44 24.2799 16.546 24.0639 15.418H26.0979C26.2659 16.006 26.5899 16.462 27.0699 16.786C27.5499 17.122 28.1619 17.29 28.9059 17.29C29.7219 17.29 30.3939 17.038 30.9219 16.534C31.4499 16.03 31.7139 15.298 31.7139 14.338V11.926C31.4499 12.658 30.9999 13.246 30.3639 13.69C29.7279 14.134 28.9599 14.356 28.0599 14.356C27.1959 14.356 26.4219 14.152 25.7379 13.744C25.0659 13.336 24.5379 12.748 24.1539 11.98C23.7699 11.212 23.5779 10.306 23.5779 9.26203C23.5779 8.23003 23.7699 7.33003 24.1539 6.56203C24.5379 5.79403 25.0659 5.20603 25.7379 4.79803C26.4219 4.39003 27.1959 4.18603 28.0599 4.18603ZM28.6899 5.98603C27.7779 5.98603 27.0459 6.28003 26.4939 6.86803C25.9539 7.44403 25.6839 8.24203 25.6839 9.26203C25.6839 10.282 25.9539 11.086 26.4939 11.674C27.0459 12.25 27.7779 12.538 28.6899 12.538C29.2659 12.538 29.7819 12.406 30.2379 12.142C30.6939 11.866 31.0539 11.482 31.3179 10.99C31.5819 10.498 31.7139 9.92203 31.7139 9.26203C31.7139 8.61403 31.5819 8.04403 31.3179 7.55203C31.0539 7.04803 30.6939 6.66403 30.2379 6.40003C29.7819 6.12403 29.2659 5.98603 28.6899 5.98603Z"/>
            </svg>
          </button>
        </div>
        <div class="row">
          <button class="grey bgWhite" @click="buttonClick('Ac')">Ac</button>
          <button class="grey" @click="buttonClick('back')">
            <svg width="22" height="18" viewBox="0 0 22 18" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M6.53505 1.11994e-08H21.0001C21.2653 1.11994e-08 21.5196 0.105357 21.7072 0.292893C21.8947 0.48043 22.0001 0.734784 22.0001 1V17C22.0001 17.2652 21.8947 17.5196 21.7072 17.7071C21.5196 17.8946 21.2653 18 21.0001 18H6.53505C6.37046 18 6.20841 17.9594 6.06327 17.8818C5.91813 17.8042 5.7944 17.6919 5.70305 17.555L0.370054 9.555C0.260415 9.39067 0.201904 9.19755 0.201904 9C0.201904 8.80245 0.260415 8.60933 0.370054 8.445L5.70305 0.445C5.7944 0.308084 5.91813 0.195832 6.06327 0.118205C6.20841 0.0405779 6.37046 -2.46193e-05 6.53505 1.11994e-08ZM7.07005 2L2.40405 9L7.07005 16H20.0001V2H7.07005ZM13.0001 7.586L15.8281 4.757L17.2431 6.172L14.4141 9L17.2431 11.828L15.8281 13.243L13.0001 10.414L10.1721 13.243L8.75705 11.828L11.5861 9L8.75705 6.172L10.1721 4.757L13.0001 7.586Z"/>
            </svg>
          </button>
          <button class="sign" @click="buttonClick('/')">
            <svg width="12" height="27" viewBox="0 0 12 27" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M9.73769 0C10.8584 0 11.6564 1.08866 11.319 2.1574L3.84367 25.8409C3.62588 26.5309 2.98586 27 2.26231 27V27C1.1416 27 0.34362 25.9113 0.680953 24.8426L8.15633 1.15912C8.37412 0.469129 9.01414 0 9.73769 0V0Z"/>
            </svg>
          </button>
          <button class="sign" @click="buttonClick('*')">
            <svg width="12" height="12" viewBox="0 0 12 12" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M9.39967 2.7094C10.0074 2.24161 10.8938 2.41616 11.2713 3.0837L11.3055 3.14428C11.6697 3.78831 11.3686 4.60613 10.6748 4.86305C9.6281 5.25062 9.62776 6.73457 10.6769 7.11543C11.3708 7.36732 11.6742 8.18052 11.3149 8.82535L11.2436 8.95329C10.8666 9.62988 9.97289 9.80705 9.36631 9.32543C8.47322 8.61631 7.1779 9.39723 7.3487 10.5247C7.46527 11.2942 6.87153 12 6.09327 12H6.06106C5.28235 12 4.68307 11.3114 4.78931 10.54C4.94766 9.39017 3.6194 8.63594 2.71502 9.36342C2.09909 9.85887 1.18593 9.68466 0.795666 8.99724L0.697047 8.82353C0.331402 8.17948 0.63629 7.35841 1.3302 7.09957C2.36765 6.7126 2.38148 5.23786 1.34247 4.85509C0.654373 4.60159 0.355465 3.79335 0.713041 3.15314L0.758625 3.07153C1.13697 2.39413 2.02801 2.20965 2.64422 2.68113L2.68768 2.71439C3.61652 3.42508 4.9388 2.6462 4.77142 1.48871C4.65797 0.704129 5.27227 0 6.06501 0C6.855 0 7.46426 0.71245 7.34594 1.49352C7.17329 2.63316 8.48631 3.4125 9.39967 2.7094Z"/>
            </svg>
          </button>
        </div>
        <div class="row">
          <button class="border" @click="buttonClick('7')">7</button>
          <button class="border" @click="buttonClick('8')">8</button>
          <button class="border" @click="buttonClick('9')">9</button>
          <button class="sign" @click="buttonClick('-')">-</button>
        </div>
        <div class="row">
          <button class="border" @click="buttonClick('4')">4</button>
          <button class="border" @click="buttonClick('5')">5</button>
          <button class="border" @click="buttonClick('6')">6</button>
          <button class="dblH sign" @click="buttonClick('+')">+</button>
        </div>
        <div class="row">
          <button class="border" @click="buttonClick('1')">1</button>
          <button class="border" @click="buttonClick('2')">2</button>
          <button class="border" @click="buttonClick('3')">3</button>
          <p></p>
        </div>
        <div class="row">
          <button class="dblW border" id="btn0" @click="buttonClick('0')">0</button>
          <button @click="buttonClick('.')">.</button>
          <button class="dblH btnBottom" id="btnEgal" @click="buttonClick('=')">=</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'HomeView',
  data () {
    return {
      transparent: true,
      darkTheme: false,
      resultFontSize: '',
      result: '',
      expression: ''
    }
  },
  computed: {
    calculatorClasses() {
      return {
        dark: this.darkTheme,
        opaque: !this.transparent
      };
    }
  },
  methods: {
    buttonClick(value) {
      switch (value) {
        case '=':
          this.calculate();
          break;
        case 'Ac':
          this.clearExpression();
          break;
        case 'back':
          this.removeLastCharacter();
          break;
        default:
          this.addToExpression(value);
          break;
      }
    },
    calculate() {
      const maxLength = 15;
      let result = eval(this.expression).toString();

      if (result.length > maxLength) {
        result = result.slice(0, maxLength);
      }

      this.result = result.replace(/(\d)(?=(\d{3})+$)/g, '$1 ');

      const baseFontSize = 48;
      const fontSizeStep = 2;

      const resultLength = this.result.length;
      let reducedFontSize = baseFontSize;

      if (resultLength > 9) {
        const extraCharacters = resultLength - 9;
        reducedFontSize -= extraCharacters * fontSizeStep;
      }

      if (reducedFontSize >= 24) {
        this.resultFontSize = `${reducedFontSize}px`;
      } else {
        this.resultFontSize = '24px';
      }

      if (!['+', '-', '*', '/'].includes(this.expression.slice(-1))) {
        this.expression = this.result;
      }
      this.previousResult = this.result;
      this.currentOperator = null;
    },
    clearExpression() {
      this.expression = '';
      this.result = '';
      this.previousResult = null;
      this.currentOperator = null;
    },
    removeLastCharacter() {
      this.expression = this.expression.slice(0, -1);
    },
    addToExpression(value) {
      const lastChar = this.expression.slice(-1);

      if (value === '.' && lastChar.includes('.')) {
        return;
      }

      if (['+', '-', '*', '/'].includes(value)) {
        if (this.currentOperator === null) {
          if (this.expression === '') {
            return;
          }
          this.expression += ' ' + value + ' ';
          this.currentOperator = value;
        } else {
          this.calculate();
          this.expression += ' ' + value + ' ';
          this.currentOperator = value;
        }
      } else {
        this.expression += value;
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.home {
  width: 100vw;
  height: 100vh;
  background: #DAF0FF;
  color: #424242;
  position: relative;
  font-family: 'Poppins-Regular';
  .circle {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    height: 700px;
    width: 700px;
    border-radius: 50%;
    background: #109DFF;
  }
  .settings {
    position: fixed;
    display: flex;
    flex-direction: column;
    height: 100%;
    width: 300px;
    padding: 50px;
    ul {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 50px;
      li {
        width: 100%;
        list-style: none;
        display: flex;
        justify-content: flex-end;
        align-items: center;
        gap: 20px;
        .tgl {
          display: none;
          &,
          &:after,
          &:before,
          & *,
          & *:after,
          & *:before,
          & + .tgl-btn {
            box-sizing: border-box;
            &::selection {
              background: none;
            }
          }
          
          + .tgl-btn {
            outline: 0;
            display: block;
            width: 4em;
            height: 2em;
            position: relative;
            cursor: pointer;
            user-select: none;
            &:after,
            &:before {
              position: relative;
              display: block;
              content: "";
              width: 50%;
              height: 100%;
            }
            
            &:after {
              left: 0;
            }
            
            &:before {
              display: none;
            }
          }
          
          &:checked + .tgl-btn:after {
            left: 50%;
          }
        }
        .tgl-flat {
          + .tgl-btn {
            padding: 2px;
            transition: all .2s ease;
            background: #ffffff;
            border: 2px solid #aeddff;
            border-radius: 2em;
            &:after {
              transition: all .2s ease;
              background: #aeddff;
              content: "";
              border-radius: 1em;
            }
          }
          
          &:checked + .tgl-btn {
            border: 2px solid #109DFF;
            &:after {
              left: 50%;
              background: #109DFF;
            }
          }
        }
      }
    }
  }
  .calculator {
    position: relative;
    overflow: hidden;
    width: 375px;
    height: 812px;
    background: linear-gradient(133deg, #F7F8FB 0%, rgba(247, 248, 251, 0.1) 100%);
    backdrop-filter: blur(51px);
    top: 50%;
    left: 45%;
    transform: translate(-50%, -50%);
    border-radius: 39px;
    transition: all .2s ease-in-out;
    box-shadow: 100px 60px 50px 0px rgba(0, 50, 84, 0.55);
    display: flex;
    flex-direction: column;
    padding: 33px;
    &.dark {
      background: linear-gradient(223deg, #17181ae0 0%, #17181ab9 100%);
      .top-section {
        h1 {
          color: white;
        }
      }
      .button-section {
        .row {
          button {
            border: none!important;
            background: #303136;
            color: rgba(41, 168, 255, 1);
            transition: all .1s ease-in-out;
            &:hover {
              filter: brightness(120%);
            }
            &.minH {
              background: #303136;
              color: rgb(41, 168, 255);
              svg {
                path {
                  fill: rgba(41, 168, 255, 1);
                }
              }
            }
            &#btn0 {
              color: rgba(41, 168, 255, 1);
            }
            &#btnEgal {
              background: #1991FF;
              box-shadow: none;
              color: rgba(178, 218, 255, 1);
            }
            &.sign {
              background: #005DB2;
              box-shadow: none;
              color: rgba(51, 157, 255, 1);
              svg {
                path {
                  fill: rgba(51, 157, 255, 1);
                }
              }
            }
            &.grey {
              background: #616161;
              color: rgba(165, 165, 165, 1);
              svg {
                path {
                  fill: rgba(165, 165, 165, 1);
                }
              }
            }
          }
        }
      }
      &.opaque {
        background: linear-gradient(223deg, #17181A 0%, #17181a 100%);
        .button-section {
          .row {
            button {
              border: none!important;
              background: #303136;
              color: rgba(41, 168, 255, 1);
              &.minH {
                border-radius: 24px;
                background: #303136;
                color: rgb(41, 168, 255);
                svg {
                  path {
                    fill: rgba(41, 168, 255, 1);
                  }
                }
              }
              &#btn0 {
                color: rgba(41, 168, 255, 1);
              }
              &#btnEgal {
                background: #1991FF;
                box-shadow: none;
                color: rgba(178, 218, 255, 1);
              }
              &.sign {
                background: #005DB2;
                box-shadow: none;
                color: rgba(51, 157, 255, 1);
                svg {
                  path {
                    fill: rgba(51, 157, 255, 1);
                  }
                }
              }
              &.grey {
                background: #616161;
                color: rgba(165, 165, 165, 1);
                svg {
                  path {
                    fill: rgba(165, 165, 165, 1);
                  }
                }
              }
            }
          }
        }
      }
    }
    &.opaque {
      background: #F7F8FB;
      .button-section {
        .row {
          button {
            background: linear-gradient(132deg, rgba(255, 255, 255, 0.60) 0%, rgba(255, 255, 255, 0.40) 100%);
            color: rgba(56, 185, 255, 1);
            border: 1px solid white!important;
            &.grey {
              color: rgba(133, 133, 133, 1);
              background-color: #fff;
              svg {
                path {
                  fill: rgba(133, 133, 133, 1);
                }
              }
            }
            &#btnEgal {
              border: none!important;
            }
            &.sign {
              background-color: rgba(173, 226, 255, 1);
              border: none!important;
              color: rgba(16, 157, 255, 1);
              svg {
                path {
                  fill: rgba(16, 157, 255, 1);
                }
              }
            }
            &.minH {
              background: #FFF;
              color: #7CC9FF;
              svg {
                path {
                  fill: rgba(124, 201, 255, 1);
                }
              }
            }
            &#btn0 {
              color: rgba(16, 157, 255, 1);
            }
          }
        }
      }
    }
    .top-section {
      width: 100%;
      height: 40%;
      display: flex;
      flex-direction: column;
      justify-content: flex-end;
      align-items: flex-end;
      padding-bottom: 80px;
      .operation {
        color: #818181;
        font-size: 24px;
        .sign-operation {
          color: rgb(16, 157, 255);
        }
      }
      h1 {
        color: #424242;
      }
    }
    .button-section {
      width: 100%;
      height: 60%;
      display: grid;
      grid-template-columns: repeat(1, 1fr);
      grid-gap: 10px;
      .row {
        display: flex;
        justify-content: space-between;
        gap: 10px;
        height: 60px;
        width: 309px;
        &.rowMin {
          height: 40px;
        }
        button {
          padding: 10px;
          font-size: 20px;
          border: 1px solid rgb(231, 245, 255);
          width: 62px;
          height: 60px;
          padding: 6px 4px;
          border-radius: 16px;
          background: linear-gradient(132deg, rgba(255, 255, 255, 0.0) 0%, rgba(255, 255, 255, 0.0) 100%);
          backdrop-filter: blur(6px);
          cursor: pointer;
          color: #ffffff;
          font-size: 32px;
          display: flex;
          justify-content: center;
          align-items: center;
          transition: all .1s ease-in-out;
          &:hover {
            filter: brightness(110%);
          }
          svg {
            path {
              fill: #a3d0f5;
            }
          }
          &.minH {
            border-radius: 24px;
            height: 40px;
            color: #FFF;
            font-size: 19px;
            svg {
              path {
                fill: #ffffff;
              }
            }
          }
          &.bgWhite {
            background: linear-gradient(132deg, rgba(255, 255, 255, 0.0) 0%, rgba(255, 255, 255, 0.0) 100%);
          }
          &.dblH {
            height: 96px;
            &.btnBottom {
              align-self: flex-end;
            }
          }
          &.dblW {
            width: 144px;
          }
          &.border {
            border: 1px solid rgb(231, 245, 255);
          }
          &.grey {
            color: #a3d0f5;
          }
          &.sign {
            border-radius: 12px;
            background: linear-gradient(226deg, #ADD8FF 0%, rgba(173, 216, 255, 0.28) 100%);
            box-shadow: 0px 0px 9px 0px rgba(255, 255, 255, 0.43) inset;
            border: 1px solid rgb(231, 245, 255);
            color: hsl(205, 98%, 64%);
            svg {
              path {
                fill: #62ABE7;
              }
            }
          }
          &#btn0 {
            color: #ffffff;
          }
          &#btnEgal {
            border-radius: 12px;
            border: none;
            color: #B2DAFF;
            background: #19ACFF;
            box-shadow: -9px 13px 23px 0px rgba(0, 163, 255, 0.65), -3px 4px 11px 0px #B0DFFF inset;
          }
        }
        p {
          width: 62px;
        }
      }
    }
  }
}
</style>
