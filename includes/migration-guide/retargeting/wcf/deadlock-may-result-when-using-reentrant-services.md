---
ms.openlocfilehash: 2f960942bda54505690cbac3151ef74ec0ab5ebb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235513"
---
### <a name="deadlock-may-result-when-using-reentrant-services"></a>Zakleszczenie może spowodować korzystanie z usług reentrant

|   |   |
|---|---|
|Szczegóły|Zakleszczenie może spowodować ponowne enturant usługi, która ogranicza wystąpienia usługi do jednego wątku wykonywania w czasie. Usługi podatne na ten problem będą <xref:System.ServiceModel.ServiceBehaviorAttribute> miały następujące elementy w kodzie:<pre><code class="lang-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]&#13;&#10;</code></pre>|
|Sugestia|Aby rozwiązać ten problem, można wykonać następujące czynności:<ul><li>Ustaw tryb współbieżności usługi <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> na &lt;System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType&gt;. Przykład:</li></ul><pre><code class="lang-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single)]&#13;&#10;</code></pre><ul><li>Zainstaluj najnowszą aktualizację do programu .NET Framework 4.6.2 lub uaktualnij do nowszej wersji programu .NET Framework. Spowoduje to wyłączenie przepływu <xref:System.Threading.ExecutionContext> <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>w . To zachowanie jest konfigurowalne; jest to równoznaczne z dodaniem do pliku konfiguracji następujących ustawień aplikacji:</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>Wartość nigdy <code>Switch.System.ServiceModel.DisableOperationContextAsyncFlow</code> nie powinna <code>false</code> być ustawiona na usługi Rentrant.|
|Zakres|Mały|
|Wersja|4.6.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType></li></ul>|
