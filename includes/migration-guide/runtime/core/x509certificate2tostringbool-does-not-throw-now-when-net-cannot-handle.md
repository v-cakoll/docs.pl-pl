### <a name="x509certificate2tostringbool-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>X509Certificate2.toString(bool) nie zgłasza teraz po .NET nie można obsłużyć certyfikatu

|   |   |
|---|---|
|Szczegóły|Wcześniej, tej metody spowoduje zgłoszenie Jeśli <code>true</code> została przekazana dla parametru verbose i zostały zainstalowane certyfikaty, które nie były obsługiwane przez program .NET Framework. Teraz metoda powiedzie się i zwraca nieprawidłowy ciąg, który pomija niedostępny części certyfikat.|
|Sugestia|Każdy kod w zależności od <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)> powinny być aktualizowane oczekiwać, że zwrócony ciąg mogą wyłączyć niektóre dane certyfikatu (na przykład klucz publiczny, klucz prywatny i rozszerzenia) w niektórych przypadkach, w których interfejsu API będzie mieć wcześniej zgłoszony.|
|Zakres|Krawędź|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|

