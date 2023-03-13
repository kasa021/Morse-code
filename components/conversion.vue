<template>
  <div class="input-body">
    <div class="input-text">
      <p class="sentense">平仮名かアルファベットを入力して</p>
      <textarea type="text" placeholder="文字を入力してください" class="input-box" id="textarea1"></textarea>
      <button @click="convert()">変換</button>
    </div>
    <div class="out-text">
      <p class="sentense">変換された信号がでるよ</p>
      <textarea type="text" placeholder="モールス信号に変換されます" class="out-box" id="textarea2"></textarea>
    </div>
  </div>
</template>

<script setup lang="ts">
const morseCodeMap = new Map<string, string>();
morseCodeMap.set('A', '.-');
morseCodeMap.set('B', '-...');
morseCodeMap.set('C', '-.-.');
morseCodeMap.set('D', '-..');
morseCodeMap.set('E', '.');
morseCodeMap.set('F', '..-.');
morseCodeMap.set('G', '--.');
morseCodeMap.set('H', '....');
morseCodeMap.set('I', '..');
morseCodeMap.set('J', '.---');
morseCodeMap.set('K', '-.-');
morseCodeMap.set('L', '.-..');
morseCodeMap.set('M', '--');
morseCodeMap.set('N', '-.');
morseCodeMap.set('O', '---');
morseCodeMap.set('P', '.--.');
morseCodeMap.set('Q', '--.-');
morseCodeMap.set('R', '.-.');
morseCodeMap.set('S', '...');
morseCodeMap.set('T', '-');
morseCodeMap.set('U', '..-');
morseCodeMap.set('V', '...-');
morseCodeMap.set('W', '.--');
morseCodeMap.set('X', '-..-');
morseCodeMap.set('Y', '-.--');
morseCodeMap.set('Z', '--..');
morseCodeMap.set('a', '.-');
morseCodeMap.set('b', '-...');
morseCodeMap.set('c', '-.-.');
morseCodeMap.set('d', '-..');
morseCodeMap.set('e', '.');
morseCodeMap.set('f', '..-.');
morseCodeMap.set('g', '--.');
morseCodeMap.set('h', '....');
morseCodeMap.set('i', '..');
morseCodeMap.set('j', '.---');
morseCodeMap.set('k', '-.-');
morseCodeMap.set('l', '.-..');
morseCodeMap.set('m', '--');
morseCodeMap.set('n', '-.');
morseCodeMap.set('o', '---');
morseCodeMap.set('p', '.--.');
morseCodeMap.set('q', '--.-');
morseCodeMap.set('r', '.-.');
morseCodeMap.set('s', '...');
morseCodeMap.set('t', '-');
morseCodeMap.set('u', '..-');
morseCodeMap.set('v', '...-');
morseCodeMap.set('w', '.--');
morseCodeMap.set('x', '-..-');
morseCodeMap.set('y', '-.--');
morseCodeMap.set('z', '--..');
morseCodeMap.set('あ', '--.--');
morseCodeMap.set('い', '.-');
morseCodeMap.set('う', '..-');
morseCodeMap.set('え', '-.---');
morseCodeMap.set('お', '.-...');
morseCodeMap.set('か', '.-..');
morseCodeMap.set('き', '-.-..');
morseCodeMap.set('く', '...-');
morseCodeMap.set('け', '-.--');
morseCodeMap.set('こ', '----');
morseCodeMap.set('さ', '-.-.-');
morseCodeMap.set('し', '--.-.');
morseCodeMap.set('す', '---.-');
morseCodeMap.set('せ', '.---.');
morseCodeMap.set('そ', '---.');
morseCodeMap.set('た', '-.');
morseCodeMap.set('ち', '..-.');
morseCodeMap.set('つ', '.--.');
morseCodeMap.set('て', '.-.--');
morseCodeMap.set('と', '..-..');
morseCodeMap.set('な', '.-.');
morseCodeMap.set('に', '-.-.');
morseCodeMap.set('ぬ', '....');
morseCodeMap.set('ね', '--.-');
morseCodeMap.set('の', '..--');
morseCodeMap.set('は', '-...');
morseCodeMap.set('ひ', '--..-');
morseCodeMap.set('ふ', '--..');
morseCodeMap.set('へ', '.');
morseCodeMap.set('ほ', '-..');
morseCodeMap.set('ま', '-..-');
morseCodeMap.set('み', '..-.-');
morseCodeMap.set('む', '-');
morseCodeMap.set('め', '-...-');
morseCodeMap.set('も', '-..-.');
morseCodeMap.set('や', '.--');
morseCodeMap.set('ゆ', '-..--');
morseCodeMap.set('よ', '--');
morseCodeMap.set('ら', '...');
morseCodeMap.set('り', '--.');
morseCodeMap.set('る', '-.--.');
morseCodeMap.set('れ', '---');
morseCodeMap.set('ろ', '.-.-');
morseCodeMap.set('わ', '-.-');
morseCodeMap.set('を', '.---');
morseCodeMap.set('ん', '.-.-.');
morseCodeMap.set('゛', '..');
morseCodeMap.set('゜', '..--.');
morseCodeMap.set('.', '.-.-.-');
morseCodeMap.set(',', '--..--');
morseCodeMap.set('が', '.-.. ..');
morseCodeMap.set('ぎ', '-.-.. ..');
morseCodeMap.set('ぐ', '...- ..');
morseCodeMap.set('げ', '-.-- ..');
morseCodeMap.set('ご', '---- ..');
morseCodeMap.set('ざ', '-.-.- ..');
morseCodeMap.set('じ', '--.-. ..');
morseCodeMap.set('ず', '---.- ..');
morseCodeMap.set('ぜ', '.---. ..');
morseCodeMap.set('ぞ', '---. ..');
morseCodeMap.set('だ', '-. ..');
morseCodeMap.set('ぢ', '..-. ..');
morseCodeMap.set('づ', '.--. ..');
morseCodeMap.set('で', '.-.-- ..');
morseCodeMap.set('ど', '..-.. ..');
morseCodeMap.set('ば', '-... ..');
morseCodeMap.set('び', '--..-. ..');
morseCodeMap.set('ぶ', '--.. ..');
morseCodeMap.set('べ', '. ..');
morseCodeMap.set('ぼ', '-.. ..');
morseCodeMap.set('ぱ', '-... ..--.');
morseCodeMap.set('ぴ', '--..-. ..--.');
morseCodeMap.set('ぷ', '--.. ..--.');
morseCodeMap.set('ぺ', '. ..--.');
morseCodeMap.set('ぽ', '-.. ..--.');


const convert = () => {
  const inputText = document.getElementById('textarea1') as HTMLTextAreaElement;
  // console.log(inputText.value);
  const outText = (text: string) => {
    let outText = '';
    for (let i = 0; i < text.length; i++) {
      const char = text.charAt(i);
      if (morseCodeMap.has(char)) {
        outText += morseCodeMap.get(char);
        outText+= ' ';
      } else {
        outText += char;
      }
    }
    return outText;
  };


  console.log(outText(inputText.value));
  // console.log(morseCodeMap.get('あ'));
  
  //textarea2に出力
  const textarea2 = document.getElementById('textarea2') as HTMLTextAreaElement;
  textarea2.value = outText(inputText.value);


};



</script>

<style scoped>
.sentense {
  font-size: 1.5rem;
}

.input-box {
  width: 300px;
  height: 200px;
}

.out-box {
  width: 300px;
  height: 200px;
}

.out-text {
  text-align: center;
  font-size: 2rem;
  font-weight: bold;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 50vw;
}

.input-text {
  text-align: center;
  font-size: 2rem;
  font-weight: bold;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 50vw;
}

.input-body {
  align-items: center;
  display: flex;
  padding: 0;
  width: 100vw;
  height: 50vh;
  justify-content: center;
  margin: 0;
}
</style>