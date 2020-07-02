---
ms.openlocfilehash: d25c14f93da5fe8acf06269554fed30ddc6bc95d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614754"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a><span data-ttu-id="51d18-101">Element OperationContext. Current może zwracać wartość null, gdy jest wywoływana w klauzuli using</span><span class="sxs-lookup"><span data-stu-id="51d18-101">OperationContext.Current may return null when called in a using clause</span></span>

#### <a name="details"></a><span data-ttu-id="51d18-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="51d18-102">Details</span></span>

<span data-ttu-id="51d18-103"><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>może zwracać `null` i <xref:System.NullReferenceException> może wynikać, jeśli spełnione są wszystkie z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="51d18-103"><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> may return `null` and a <xref:System.NullReferenceException> may result if all of the following conditions are true:</span></span>

- <span data-ttu-id="51d18-104">Pobierasz wartość <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> właściwości w metodzie, która zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="51d18-104">You retrieve the value of the <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> property in a method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>
- <span data-ttu-id="51d18-105">Tworzysz wystąpienie <xref:System.ServiceModel.OperationContextScope> obiektu w `using` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="51d18-105">You instantiate the <xref:System.ServiceModel.OperationContextScope> object in a `using` clause.</span></span>
- <span data-ttu-id="51d18-106">Pobierasz wartość <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> właściwości w `using statement` .</span><span class="sxs-lookup"><span data-stu-id="51d18-106">You retrieve the value of the <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> property within the `using statement`.</span></span> <span data-ttu-id="51d18-107">Przykład:</span><span class="sxs-lookup"><span data-stu-id="51d18-107">For example:</span></span>

```csharp
using (new OperationContextScope(OperationContext.Current))
{
    // OperationContext.Current is null.
    OperationContext context = OperationContext.Current;

    // ...
}
```

#### <a name="suggestion"></a><span data-ttu-id="51d18-108">Sugestia</span><span class="sxs-lookup"><span data-stu-id="51d18-108">Suggestion</span></span>

<span data-ttu-id="51d18-109">Aby rozwiązać ten problem, można wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="51d18-109">To address this issue, you can do the following:</span></span>

- <span data-ttu-id="51d18-110">Zmodyfikuj swój kod w następujący sposób, aby utworzyć wystąpienie nowego obiektu niebędącego `null` <xref:System.ServiceModel.OperationContext.Current%2A> :</span><span class="sxs-lookup"><span data-stu-id="51d18-110">Modify your code as follows to instantiate a new non- `null` <xref:System.ServiceModel.OperationContext.Current%2A> object:</span></span>

    ```csharp
    OperationContext ocx = OperationContext.Current;
    using (new OperationContextScope(OperationContext.Current))
    {
        OperationContext.Current = new OperationContext(ocx.Channel);

        // ...
    }
    ```

- <span data-ttu-id="51d18-111">Zainstaluj najnowszą aktualizację do .NET Framework 4.6.2 lub Uaktualnij do nowszej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="51d18-111">Install the latest update to the .NET Framework 4.6.2, or upgrade to a later version of the .NET Framework.</span></span> <span data-ttu-id="51d18-112">Spowoduje to wyłączenie przepływu <xref:System.Threading.ExecutionContext> w programie <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> i przywrócenie zachowania aplikacji WCF w .NET Framework 4.6.1 i wcześniejszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="51d18-112">This disables the flow of the <xref:System.Threading.ExecutionContext> in <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> and restores the behavior of WCF applications in the .NET Framework 4.6.1 and earlier versions.</span></span> <span data-ttu-id="51d18-113">To zachowanie można skonfigurować. jest to równoznaczne z dodaniem do pliku konfiguracji następującego ustawienia aplikacji:</span><span class="sxs-lookup"><span data-stu-id="51d18-113">This behavior is configurable; it is equivalent to adding the following app setting to your configuration file:</span></span>

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
    </appSettings>
    ```

    <span data-ttu-id="51d18-114">Jeśli ta zmiana jest niepożądana, a aplikacja zależy od kontekstu wykonywania przepływających między kontekstami operacji, można włączyć jej przepływ w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="51d18-114">If this change is undesirable and your application depends on execution context flowing between operation contexts, you can enable its flow as follows:</span></span>

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="false" />
    </appSettings>
    ```

| <span data-ttu-id="51d18-115">Nazwa</span><span class="sxs-lookup"><span data-stu-id="51d18-115">Name</span></span>    | <span data-ttu-id="51d18-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="51d18-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="51d18-117">Zakres</span><span class="sxs-lookup"><span data-stu-id="51d18-117">Scope</span></span>   | <span data-ttu-id="51d18-118">Brzeg</span><span class="sxs-lookup"><span data-stu-id="51d18-118">Edge</span></span>        |
| <span data-ttu-id="51d18-119">Wersja</span><span class="sxs-lookup"><span data-stu-id="51d18-119">Version</span></span> | <span data-ttu-id="51d18-120">4.6.2</span><span class="sxs-lookup"><span data-stu-id="51d18-120">4.6.2</span></span>       |
| <span data-ttu-id="51d18-121">Typ</span><span class="sxs-lookup"><span data-stu-id="51d18-121">Type</span></span>    | <span data-ttu-id="51d18-122">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="51d18-122">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="51d18-123">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="51d18-123">Affected APIs</span></span>

- <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>
