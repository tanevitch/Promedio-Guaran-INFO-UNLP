# Promedio-Guaran-INFO-UNLP
Este es un script JS para saber tu promedio en guaraní dado que lo eliminaron en la última actualización y es muy útil saberlo para diversos trámites. 

# Uso 
1) Abren su cuenta de guaraní, van a Reportes>Historia Académica>Historia completa
   ![image](https://github.com/tanevitch/Promedio-Guaran-INFO-UNLP/assets/66225963/7caa219b-b82e-4396-a3fa-98169ab0fd7a)

3) Se abren una consola en el navegador (shortcut f12)
4) Copian esto en la consola:

```
var spanAprobados = Array.from(document.getElementsByClassName("Aprobado"));

var notasExamenes = spanAprobados.map(node => {

    var nota = node.childNodes[1].nodeValue;
    var match = nota.match(/\b(?:[1-9]|10)\b/);

    return match ? parseInt(match[0]) : null;
}).filter(node => node != null);

const sum = notasExamenes.reduce((a, b) => a + b, 0);
const avg = (sum*1.0 / notasExamenes.length) || 0;
console.log(avg)
```
5) Ahí tienen su promedio. Saludos

# Disclaimer 
Quien esté registrado como ChromeDEV y quiera mejorar esta herramienta convirtiéndola en una extensión, es más que bienvenido a contribuir
