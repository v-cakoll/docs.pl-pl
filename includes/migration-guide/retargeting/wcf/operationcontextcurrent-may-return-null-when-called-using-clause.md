---
ms.openlocfilehash: e08b78b49cab88d4435d75b04bd446b413a61340
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59234963"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a>Właściwości OperationContext.Current może zwracać wartość null, gdy zostanie wywołana w za pomocą klauzuli

|   |   |
|---|---|
|Szczegóły|<xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> może zwracać <code>null</code> i <xref:System.NullReferenceException> może spowodować, jeśli spełnione są wszystkie następujące warunki:<ul><li>Pobieranie wartości <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> właściwość w metodę, która zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>.</li><li>Można utworzyć wystąpienia <xref:System.ServiceModel.OperationContextScope> obiektu <code>using</code> klauzuli.</li><li>Pobieranie wartości <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> właściwość w ramach <code>using statement</code>. Na przykład:</li></ul><pre><code class="lang-csharp">using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext context = OperationContext.Current;      // OperationContext.Current is null.&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre>|
|Sugestia|Aby rozwiązać ten problem, należy wykonać następujące:<ul><li>Zmodyfikuj kod w następujący sposób, aby utworzyć inną niż<code>null</code> <xref:System.ServiceModel.OperationContext.Current%2A> obiektu:</li></ul><pre><code class="lang-csharp">OperationContext ocx = OperationContext.Current;&#13;&#10;using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext.Current = new OperationContext(ocx.Channel);&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre><ul><li>Zainstaluj najnowszą aktualizację programu .NET Framework 4.6.2 lub Uaktualnij do nowszej wersji programu .NET Framework. Powoduje to wyłączenie przepływ <xref:System.Threading.ExecutionContext> w <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> i przywrócenie zachowania aplikacji WCF w programie .NET Framework 4.6.1 i wcześniejszych wersjach. To zachowanie jest konfigurowalne; jest to równoważne do dodawania następującego ustawienia app do pliku konfiguracji:</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>Jeśli aplikacja zależy od kontekstu wykonywania odbywającym się między kontekstami operacja ta zmiana jest niepożądany, należy włączyć przepływ w następujący sposób:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;false&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.6.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType></li></ul>|
