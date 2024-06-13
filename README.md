const readline = require('readline');

const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});

rl.question('Horas: ', (H) => {
  rl.question('Minutos: ', (M) => {
    rl.question('Segundos: ', (S) => {
      rl.question('Tempo de adiamento em segundos: ', (T) => {
        // Converter tempo original para segundos
        let totalSeconds = parseInt(H) * 3600 + parseInt(M) * 60 + parseInt(S);
        
        // Adicionar tempo de adiamento
        totalSeconds += parseInt(T);
        
        // Calcular novo tempo
        let new_H = Math.floor(totalSeconds / 3600);
        totalSeconds %= 3600;
        let new_M = Math.floor(totalSeconds / 60);
        let new_S = totalSeconds % 60;
        
        // Ajustar horas se necessário
        if (new_H >= 24) {
          new_H %= 24;
        }
        
        // Imprimir resultado
        console.log(new_H);
        console.log(new_M);
        console.log(new_S);
        
        rl.close();
      });
    });
  });
});
