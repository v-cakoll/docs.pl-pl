---
ms.openlocfilehash: d25c14f93da5fe8acf06269554fed30ddc6bc95d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614754"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a>Element OperationContext. Current może zwracać wartość null, gdy jest wywoływana w klauzuli using

#### <a name="details"></a>Szczegóły

<xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>może zwracać `null` i <xref:System.NullReferenceException> może wynikać, jeśli spełnione są wszystkie z następujących warunków:

- Pobierasz wartość <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> właściwości w metodzie, która zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> .
- Tworzysz wystąpienie <xref:System.ServiceModel.OperationContextScope> obiektu w `using` klauzuli.
- Pobierasz wartość <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> właściwości w `using statement` . Przykład:

```csharp
using (new OperationContextScope(OperationContext.Current))
{
    // OperationContext.Current is null.
    OperationContext context = OperationContext.Current;

    // ...
}
```

#### <a name="suggestion"></a>Sugestia

Aby rozwiązać ten problem, można wykonać następujące czynności:

- Zmodyfikuj swój kod w następujący sposób, aby utworzyć wystąpienie nowego obiektu niebędącego `null` <xref:System.ServiceModel.OperationContext.Current%2A> :

    ```csharp
    OperationContext ocx = OperationContext.Current;
    using (new OperationContextScope(OperationContext.Current))
    {
        OperationContext.Current = new OperationContext(ocx.Channel);

        // ...
    }
    ```

- Zainstaluj najnowszą aktualizację do .NET Framework 4.6.2 lub Uaktualnij do nowszej wersji .NET Framework. Spowoduje to wyłączenie przepływu <xref:System.Threading.ExecutionContext> w programie <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> i przywrócenie zachowania aplikacji WCF w .NET Framework 4.6.1 i wcześniejszych wersjach. To zachowanie można skonfigurować. jest to równoznaczne z dodaniem do pliku konfiguracji następującego ustawienia aplikacji:

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
    </appSettings>
    ```

    Jeśli ta zmiana jest niepożądana, a aplikacja zależy od kontekstu wykonywania przepływających między kontekstami operacji, można włączyć jej przepływ w następujący sposób:

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="false" />
    </appSettings>
    ```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.6.2       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>
