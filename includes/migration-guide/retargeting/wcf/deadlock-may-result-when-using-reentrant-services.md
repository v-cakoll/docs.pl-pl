---
ms.openlocfilehash: dd7d3e445772e4b5ec148576ccd1374d56e251bd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614783"
---
### <a name="deadlock-may-result-when-using-reentrant-services"></a>Zakleszczenie może wynikać z używania usług współużytkowanych

#### <a name="details"></a>Szczegóły

Zakleszczenie może skutkować usługą współużytkowaną, która ogranicza wystąpienia usługi do jednego wątku wykonywania w danym momencie. Usługi podatne na wystąpienie tego problemu będą miały następujące <xref:System.ServiceModel.ServiceBehaviorAttribute> kody:

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

#### <a name="suggestion"></a>Sugestia

Aby rozwiązać ten problem, można wykonać następujące czynności:

- Ustaw tryb współbieżności usługi do <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> lub &lt; System. ServiceModel. concurrency. Multiple? DisplayProperty = nameWithType &gt; . Przykład:

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

- Zainstaluj najnowszą aktualizację do .NET Framework 4.6.2 lub Uaktualnij do nowszej wersji .NET Framework. Spowoduje to wyłączenie przepływu <xref:System.Threading.ExecutionContext> w programie <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> . To zachowanie można skonfigurować. jest to równoznaczne z dodaniem do pliku konfiguracji następującego ustawienia aplikacji:

```xml
<appSettings>
  <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
</appSettings>
```

Wartość `Switch.System.ServiceModel.DisableOperationContextAsyncFlow` nie powinna być nigdy ustawiona na `false` dla usług współużytkowanych.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.6.2       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType>
