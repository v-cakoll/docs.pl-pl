### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>TargetFrameworkName dla domyślnej domeny aplikacji nie jest już domyślnie wartość null, jeśli nie ustawiona

|   |   |
|---|---|
|Szczegóły|<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> Został wcześniej wartości null w domyślnej domenie aplikacji, o ile nie została jawnie ustawiona. Począwszy od 4.6, <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> właściwości domyślnej domeny aplikacji będzie miał wartość domyślna pochodzi od TargetFrameworkAttribute (jeśli istnieje). Domeny aplikacji inne niż domyślne będą w dalszym ciągu dziedziczą ich <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> z domyślnej domeny aplikacji (co nie będzie domyślna wartość null w wersji 4.6) Jeśli nie zostanie jawnie zastąpiona.|
|Sugestia|Kod powinien zostać zaktualizowany w celu zależy od <xref:System.AppDomainSetup.TargetFrameworkName> przyjęto wartość domyślną wartość null. Jeśli wymagana jest, że ta właściwość w dalszym ciągu ma wartość null, można ją jawnie ustawić tej wartości.|
|Zakres|Krawędź|
|Wersja|4.6|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|

