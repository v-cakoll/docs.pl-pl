---
ms.openlocfilehash: 483902ff2ec54d58bfb00dd8ee7fd78868f70ab4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620358"
---
### <a name="binaryformatter-can-fail-to-find-type-from-loadfrom-context"></a>BinaryFormatter może nie można znaleźć typu z kontekstu LoadFrom

#### <a name="details"></a>Szczegóły

W przypadku .NET Framework 4,5 wiele <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> zmian może spowodować różnice w deserializacji podczas korzystania z programu w <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> celu deserializacji typów, które zostały załadowane w kontekście LoadFrom. Te zmiany są spowodowane nowymi sposobami, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> teraz ładuje typ, który powoduje inne zachowanie podczas <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> próby deserializacji do tego typu w późniejszym czasie. Domyślny spinacz serializacji nie przeszukuje automatycznie kontekstu LoadFrom, chociaż może pracował w pewnych okolicznościach w oparciu o stare zachowanie elementu XmlSerializer. Ze względu na zmiany, gdy typ jest ładowany z zestawu załadowanego w innym kontekście, <xref:System.IO.FileNotFoundException?displayProperty=fullName> może zostać zgłoszony.

#### <a name="suggestion"></a>Sugestia

Jeśli ten wyjątek jest widoczny, <code>Binder</code> Właściwość <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> można ustawić na niestandardowy spinacz, który będzie znajdować poprawny typ.<pre><code class="lang-csharp">var formatter = new BinaryFormatter { Binder = new TypeFinderBinder() }&#13;&#10;</code></pre>A następnie niestandardowy spinacz:<pre><code class="lang-csharp">public class TypeFinderBinder : SerializationBinder&#13;&#10;{&#13;&#10;private static readonly string s_assemblyName = Assembly.GetExecutingAssembly().FullName;&#13;&#10;&#13;&#10;public override Type BindToType(string assemblyName, string typeName)&#13;&#10;{&#13;&#10;return Type.GetType(String.Format(CultureInfo.InvariantCulture, &quot;{0}, {1}&quot;, typeName, s_assemblyName));&#13;&#10;}&#13;&#10;}&#13;&#10;</code></pre>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|
