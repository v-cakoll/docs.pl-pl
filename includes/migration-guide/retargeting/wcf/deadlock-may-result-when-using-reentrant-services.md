---
ms.openlocfilehash: add7b803c413f8d9ba913d5dcc1a21bbd0c5bd48
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758359"
---
### <a name="deadlock-may-result-when-using-reentrant-services"></a>Zakleszczenia mogą wystąpić podczas korzystania z usług współużytkowane

|   |   |
|---|---|
|Szczegóły|Zakleszczenie może spowodować współużytkowane usługi, który ogranicza możliwość użycia wystąpień usługi na jeden wątek jednocześnie. Usługi podatne na ten problem będzie występował będzie mieć następujące <xref:System.ServiceModel.ServiceBehaviorAttribute> w ich kodzie:<pre><code class="lang-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]&#13;&#10;</code></pre>|
|Sugestia|Aby rozwiązać ten problem, należy wykonać następujące:<ul><li>Ustaw tryb współbieżności usługi <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> lub &lt;System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType&gt;. Na przykład:</li></ul><pre><code class="lang-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single)]&#13;&#10;</code></pre><ul><li>Zainstaluj najnowszą aktualizację programu .NET Framework 4.6.2 lub Uaktualnij do nowszej wersji programu .NET Framework. Powoduje to wyłączenie przepływ <xref:System.Threading.ExecutionContext> w <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>. To zachowanie jest konfigurowalne; jest to równoważne do dodawania następującego ustawienia app do pliku konfiguracji:</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>Wartość <code>Switch.System.ServiceModel.DisableOperationContextAsyncFlow</code> nigdy nie powinna być równa <code>false</code> współużytkowane usług.|
|Zakres|Mały|
|Wersja|4.6.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType></li></ul>|
