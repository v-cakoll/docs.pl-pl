### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>Zezwalaj na Unicode w identyfikatory URI, które przypominają udziały UNC

|   |   |
|---|---|
|Szczegóły|W <xref:System.Uri?displayProperty=fullName>, tworząc plik identyfikator URI zawierający zarówno UNC nazwa udziału i już nie spowoduje znaki Unicode w identyfikatorze URI z nieprawidłowy stan wewnętrzny. Spowoduje to zmianę działania tylko wtedy, gdy wszystkie następujące właściwości są spełnione:<ul><li>Identyfikator URI ma schemat <code>file:</code> i następuje cztery lub więcej ukośników.</li><li>Nazwa hosta rozpoczyna się od znaku podkreślenia ani innych niezastrzeżonych symbolu.</li><li>Identyfikator URI zawiera znaki Unicode.</li></ul>|
|Sugestia|Praca z identyfikatorów URI spójnie zawierający Unicode aplikacji można powrotne użyto tego zachowania do odrzucenia odwołania do udziały UNC. Te aplikacje powinny używać <xref:System.Uri.IsUnc> zamiast tego.|
|Zakres|Krawędź|
|Wersja|4.7.2|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

