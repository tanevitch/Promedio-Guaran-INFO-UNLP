# Promedio-Guaraní-INFO-UNLP
Este es un script JS para saber tu promedio en guaraní dado que lo eliminaron en la última actualización y es muy útil saberlo para diversos trámites. Además, muestra la cantidad de materias aprobadas

# Uso 
1) Abren su cuenta de guaraní, van a Reportes>Historia Académica>Historia completa
   ![image](https://github.com/tanevitch/Promedio-Guaran-INFO-UNLP/assets/66225963/7caa219b-b82e-4396-a3fa-98169ab0fd7a)

3) Se abren una consola en el navegador (shortcut f12)
4) Copian esto en la consola:

```
    var spanAprobados = Array.from(document.getElementsByClassName("Aprobado"));
    var spanDesaprobados = Array.from(document.getElementsByClassName("Reprobado"));
    var spanNotas= spanAprobados.concat(spanDesaprobados)

    function calcularPromedio(spans) {
        var spans = spanNotas.map(node => {
            var nota = node.childNodes[1].nodeValue;
            var match = nota.match(/(?<=\s|^)([1-9]|10)(?=\s|$)/);
            return match ? parseInt(match[0]) : null;
        }).filter(node => node != null);
        
        var sum = spans.reduce((a, b) => a + b, 0);
        var promedio = (sum*1.0 / spans.length) || 0;
        return {promedio: promedio, materias: spans.length}
    }

    const { promedio, materias }= calcularPromedio(spanNotas);
    console.log("Promedio con aplazos: " + promedio)
    console.log("Promedio sin aplazos: " + calcularPromedio(spanAprobados).promedio)
    console.log("Cantidad de materias aprobadas: "+materias)
```
5) Ahí tienen su promedio con y sin aplazos. Saludos

# Disclaimer 
Quien esté registrado como ChromeDEV y quiera mejorar esta herramienta convirtiéndola en una extensión, es más que bienvenido a contribuir
