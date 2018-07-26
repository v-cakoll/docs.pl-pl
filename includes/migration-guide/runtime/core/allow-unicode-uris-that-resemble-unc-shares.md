### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>Zezwalaj na Unicode na identyfikatory URI, które przypominają udziały UNC

|   |   |
|---|---|
|Szczegóły|W <xref:System.Uri?displayProperty=fullName>, tworząc plik identyfikatorem URI zawierającym zarówno UNC nazwa udziału i już nie spowoduje znaki Unicode w identyfikatorze URI przy użyciu nieprawidłowy stan wewnętrzny. Spowoduje to zmianę działania tylko wtedy, gdy wszystkie następujące elementy są spełnione:<ul><li>Identyfikator URI ma schemat <code>file:</code> i następuje cztery lub więcej ukośników.</li><li>Nazwa hosta rozpoczyna się od znaku podkreślenia ani innych niezarezerwowane symboli.</li><li>Identyfikator URI zawiera znaki Unicode.</li></ul>|
|Sugestia|Aplikacje Praca z identyfikatorów URI spójnie zawierający Unicode mogą mieć wielkiego użyte to zachowanie zabrania odwołania się z udziałami UNC. Te aplikacje powinny używać <xref:System.Uri.IsUnc> zamiast tego.|
|Zakres|Krawędź|
|Wersja|4.7.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

