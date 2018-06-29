### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Obsługuje specjalne notacji względny identyfikator URI, gdy występuje Unicode

|   |   |
|---|---|
|Szczegóły|<xref:System.Uri> nie zgłosi <xref:System.NullReferenceException> podczas wywoływania metody <xref:System.Uri.TryCreate%2A> na niektórych względne identyfikatory URI zawierający Unicode.The reprodukowania najprostszym <xref:System.NullReferenceException> się dwie instrukcje równoważne poniżej:<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre>Aby odtworzyć <xref:System.NullReferenceException>, następujące elementy muszą być spełnione:<ul><li>Identyfikator URI musi być określona jako względną za dołączanie go przy użyciu "http:", a nie po jej wraz z opcją "/ /".</li><li>Identyfikator URI musi zawierać symboli bezwarunkowe lub procent zakodowane w formacie Unicode.</li></ul>|
|Sugestia|Zamiast tego należy określić użytkowników w zależności od tego zachowania, aby uniemożliwić względne identyfikatory URI <xref:System.UriKind.Absolute?displayProperty=nameWithType> podczas tworzenia identyfikatora URI.|
|Zakres|Krawędź|
|Wersja|4.7.2|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|

