---
ms.openlocfilehash: ac929a8b3e9a7d56122f5699c51819ad483d1f5e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235611"
---
### <a name="binaryformatter-can-fail-to-find-type-from-loadfrom-context"></a>Elementu można nie można odnaleźć typu z LoadFrom — kontekst

|   |   |
|---|---|
|Szczegóły|Począwszy od .NET Framework 4.5, szereg <xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> zmiany mogą spowodować różnice w deserializacji, korzystając z <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> do deserializacji typów, które został załadowany w LoadFrom — kontekst. Zmiany te są ze względu na nowe sposoby <xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> ładowana typu, co powoduje, że inne zachowanie podczas <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> próbuje wykonać deserializacji do tego typu później. Domyślnego integratora serializacji nie będą automatycznie przeszukiwać LoadFrom — kontekst, chociaż może mający doświadczenie w niektórych sytuacjach, w oparciu o stare zachowanie elementu XmlSerializer. Z powodu zmian, gdy typ jest ładowany z zestawu, który został załadowany w innym kontekście <xref:System.IO.FileNotFoundException?displayProperty=name> może zostać wygenerowany.|
|Sugestia|Jeśli ten wyjątek jest widoczny, <code>Binder</code> właściwość <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> można ustawić niestandardowego integratora, który zawiera poprawnego typu.<pre><code class="lang-csharp">var formatter = new BinaryFormatter { Binder = new TypeFinderBinder() }&#13;&#10;</code></pre>A następnie niestandardowego integratora:<pre><code class="lang-csharp">public class TypeFinderBinder : SerializationBinder&#13;&#10;{&#13;&#10;private static readonly string s_assemblyName = Assembly.GetExecutingAssembly().FullName;&#13;&#10;&#13;&#10;public override Type BindToType(string assemblyName, string typeName)&#13;&#10;{&#13;&#10;return Type.GetType(String.Format(CultureInfo.InvariantCulture, &quot;{0}, {1}&quot;, typeName, s_assemblyName));&#13;&#10;}&#13;&#10;}&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|
