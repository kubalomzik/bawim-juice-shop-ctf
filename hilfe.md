RG9uJ3Qgc2hvdyB0aGlzIHRvIG15IG1vdGhlciwgaXQncyBvbmx5IEdvb2dsZSBUcmFuc2xhdGU=

</br>

1. Öffnen Sie http://localhost:3000/#/search und laden Sie die Seite mit F5 neu, während Sie die Registerkarte Netzwerk in den DevTools Ihres Browsers beobachten.

2. Erkennen Sie die GET-Anforderung http://localhost:3000/rest/products/search?q=, die die Produktdaten zurückgibt.

3. Das Senden von SQL-Payloads über das Suchfeld in der Navigationsleiste bringt Ihnen nichts, da es nur Filter auf den gesamten Datensatz anwendet, der mit einem einzelnen Aufruf beim Laden der Seite abgerufen wurde.

4. In Anbetracht dessen wäre der Parameter q= auf dem Endpunkt http://localhost:3000/rest/products/search nicht einmal erforderlich, sondern könnte ein Überbleibsel einer anderen Implementierung der Suchfunktion sein. Testen Sie diese Theorie, indem Sie http://localhost:3000/rest/products/search?q=orange einreichen.

5. Einreichen '; als q über http://localhost:3000/rest/products/search?q=';

6. Sie erhalten eine Fehlerseite mit einem SQLITE_ERROR: Syntaxfehler, der darauf hinweist, dass SQL Injection tatsächlich möglich ist.

7. Sie befinden sich nun im Bereich Blind SQL Injection, wo der Versuch, gültige Abfragen zu erstellen, eine Frage von Geduld, Aufmerksamkeit und etwas Glück ist.

8. Das Variieren der Nutzlast in '-- für q führt zu einem SQLITE_ERROR: unvollständige Eingabe. Dieser Fehler tritt aufgrund von zwei (jetzt unausgeglichenen) Klammern in der Abfrage auf.

9. Die Verwendung von '))-- für q behebt die Syntax und ruft erfolgreich alle Produkte ab, einschließlich des (logischerweise gelöschten) Weihnachtsangebots. Notieren Sie sich die ID (10).

10. Gehen Sie zu http://localhost:3000/#/login und melden Sie sich als beliebiger Benutzer an.

11. Legen Sie alle regelmäßig verfügbaren Produkte in Ihren Warenkorb, um spätere Probleme beim Bezahlvorgang zu vermeiden. Merken Sie sich Ihren BasketId-Wert in der Nutzlast der Anfrage (beim Anzeigen der Registerkarte „Netzwerk“) oder finden Sie dieselben Informationen in der Gebotsvariablen im Sitzungsspeicher Ihres Browsers (auf der Registerkarte „Anwendung“).

12. Erstellen und senden Sie eine POST-Anfrage an http://localhost:3000/api/BasketItems mit:

        {"BasketId": "", "ProductId": 10, "quantity": 1} als Text
        application/json als Content-Type

13. Gehen Sie zu http://localhost:3000/#/basket, um zu überprüfen, ob sich die "Christmas Super-Surprise-Box (2014 Edition)" im Warenkorb befindet.

14. Klicken Sie auf der Seite „Ihr Warenkorb“ auf „Zur Kasse“, um die Aufgabe zu lösen.

