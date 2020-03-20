---
ms.openlocfilehash: e08b78b49cab88d4435d75b04bd446b413a61340
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859257"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a>OperationContext.Current może zwracać wartość null po wywołaniu w using klauzuli

|   |   |
|---|---|
|Szczegóły|<xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>może <code>null</code> powrócić <xref:System.NullReferenceException> i może spowodować, jeśli wszystkie z następujących warunków są spełnione:<ul><li>Można pobrać wartość <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> właściwości w metodzie, <xref:System.Threading.Tasks.Task> która <xref:System.Threading.Tasks.Task%601>zwraca lub .</li><li>Tworzenie wystąpienia <xref:System.ServiceModel.OperationContextScope> obiektu w <code>using</code> klauzuli.</li><li>Można pobrać wartość <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> właściwości w <code>using statement</code>. Przykład:</li></ul><pre><code class="lang-csharp">using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext context = OperationContext.Current;      // OperationContext.Current is null.&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre>|
|Sugestia|Aby rozwiązać ten problem, można wykonać następujące czynności:<ul><li>Zmodyfikuj kod w następujący<code>null</code> <xref:System.ServiceModel.OperationContext.Current%2A> sposób, aby utworzyć wystąpienie nowego obiektu niebędącego obiektem:</li></ul><pre><code class="lang-csharp">OperationContext ocx = OperationContext.Current;&#13;&#10;using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext.Current = new OperationContext(ocx.Channel);&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre><ul><li>Zainstaluj najnowszą aktualizację do programu .NET Framework 4.6.2 lub uaktualnij do nowszej wersji programu .NET Framework. Spowoduje to wyłączenie przepływu <xref:System.Threading.ExecutionContext> <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> w i przywraca zachowanie aplikacji WCF w .NET Framework 4.6.1 i wcześniejszych wersjach. To zachowanie jest konfigurowalne; jest to równoznaczne z dodaniem do pliku konfiguracji następujących ustawień aplikacji:</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>Jeśli ta zmiana jest niepożądana, a aplikacja zależy od kontekstu wykonania przepływającego między kontekstami operacji, można włączyć jej przepływ w następujący sposób:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;false&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Zakres|Brzeg|
|Wersja|4.6.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType></li></ul>|
