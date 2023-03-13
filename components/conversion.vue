<template>
  <div class="input-body">
    <div class="input-text">
      <p class="sentense">平仮名かアルファベットを入力して</p>
      <textarea type="text" placeholder="文字を入力してください" class="input-box">
        </textarea>
    </div>
    <div class="out-text">
      <p class="sentense">変換された信号がでるよ</p>
      <textarea type="text" placeholder="モールス信号に変換されます" class="out-box">
        </textarea>
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
morseCodeMap.set('あ', '.-');
morseCodeMap.set('い', '..');
morseCodeMap.set('う', '..-');
morseCodeMap.set('え', '.');
morseCodeMap.set('お', '---');
morseCodeMap.set('か', '-.-');
morseCodeMap.set('き', '-.-.');
morseCodeMap.set('く', '--.-');
morseCodeMap.set('け', '-.--');
morseCodeMap.set('こ', '--.');
morseCodeMap.set('さ', '.-..');
morseCodeMap.set('し', '...');
morseCodeMap.set('す', '...-');
morseCodeMap.set('せ', '--..');
morseCodeMap.set('そ', '-..-');
morseCodeMap.set('た', '-..');
morseCodeMap.set('ち', '-.--.');
morseCodeMap.set('つ', '-...');
morseCodeMap.set('て', '-');
morseCodeMap.set('と', '..-.');
morseCodeMap.set('な', '.');
morseCodeMap.set('に', '.--');
morseCodeMap.set('ぬ', '-.--');
morseCodeMap.set('ね', '-..-');
morseCodeMap.set('の', '-.');
morseCodeMap.set('は', '....');
morseCodeMap.set('ひ', '.---');
morseCodeMap.set('ふ', '..-.');
morseCodeMap.set('へ', '-.-..');
morseCodeMap.set('ほ', '.--.');
morseCodeMap.set('ま', '-.-');
morseCodeMap.set('み', '--');
morseCodeMap.set('む', '---.');
morseCodeMap.set('め', '--.-');
morseCodeMap.set('も', '....-');
morseCodeMap.set('や', '-.-');
morseCodeMap.set('ゆ', '.--.-');
morseCodeMap.set('よ', '-..');
morseCodeMap.set('ら', '.-.');
morseCodeMap.set('り', '...');
morseCodeMap.set('る', '.-..-');
morseCodeMap.set('れ', '-.-.');
morseCodeMap.set('ろ', '...');
morseCodeMap.set('わ', '.--');
morseCodeMap.set('を', '.-.-');
morseCodeMap.set('ん', '--.--');
morseCodeMap.set('゛', '.-..-.');
morseCodeMap.set('゜', '.-.-.-');
morseCodeMap.set('.', '.-.-.-');
morseCodeMap.set(',', '--..--');
morseCodeMap.set('。', '.-.-.-');
morseCodeMap.set('、', '--..--');
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