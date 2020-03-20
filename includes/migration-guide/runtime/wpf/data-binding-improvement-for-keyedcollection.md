---
ms.openlocfilehash: 8aae403e3f23d3bfc755140b2ac29d757f10f753
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74451470"
---
### <a name="data-binding-improvement-for-keyedcollection"></a>Poprawa wiązania danych dla KeyedCollection

|   |   |
|---|---|
|Szczegóły|Naprawiono <xref:System.Windows.Data.Binding> nieprawidłowe użycie indeksatora IList, gdy obiekt źródłowy deklaruje niestandardowy indeksator&lt;z tym samym&gt;podpisem (na przykład KeyedCollection int,TItem ).|
|Sugestia|Aby aplikacja przeznaczona dla starszej wersji korzystała z tej zmiany, musi działać w programie .NET Framework 4.8 lub nowszym, <code>&lt;runtime&gt;</code> a następnie musi wyrazić zgodę <code>false</code>na zmianę, dodając następujący [przełącznik AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) do sekcji pliku konfiguracyjnego aplikacji i ustawiając go na:<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Duży|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|
