---
ms.openlocfilehash: 78faa5f4008b41bac75c94ce09a58c8227e5b485
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614670"
---
### <a name="currentculture-and-currentuiculture-flow-across-tasks"></a><span data-ttu-id="af71b-101">Przepływy CurrentCulture i CurrentUICulture między zadaniami</span><span class="sxs-lookup"><span data-stu-id="af71b-101">CurrentCulture and CurrentUICulture flow across tasks</span></span>

#### <a name="details"></a><span data-ttu-id="af71b-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="af71b-102">Details</span></span>

<span data-ttu-id="af71b-103">Począwszy od .NET Framework 4,6 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> i <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> są przechowywane w wątku <xref:System.Threading.ExecutionContext?displayProperty=fullName> , który przepływa przez operacje asynchroniczne. Oznacza to, że zmiany w <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> lub <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> zostaną odzwierciedlone w zadaniach, które są później uruchamiane asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="af71b-103">Beginning in the .NET Framework 4.6, <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> are stored in the thread's <xref:System.Threading.ExecutionContext?displayProperty=fullName>, which flows across asynchronous operations.This means that changes to <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> will be reflected in tasks which are later run asynchronously.</span></span> <span data-ttu-id="af71b-104">Różni się to od zachowania poprzednich wersji .NET Framework (które zostałyby zresetowane <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> i <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> we wszystkich zadaniach asynchronicznych).</span><span class="sxs-lookup"><span data-stu-id="af71b-104">This is different from the behavior of previous .NET Framework versions (which would reset <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> in all asynchronous tasks).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="af71b-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="af71b-105">Suggestion</span></span>

<span data-ttu-id="af71b-106">Aplikacje, których dotyczy ta zmiana, mogą obejść je przez jawne ustawienie żądanej <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> lub <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> pierwszej operacji w zadaniu asynchronicznym.</span><span class="sxs-lookup"><span data-stu-id="af71b-106">Apps affected by this change may work around it by explicitly setting the desired <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> as the first operation in an async Task.</span></span> <span data-ttu-id="af71b-107">Alternatywnie, stare zachowanie (nieprzepływności <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> ) może być włączane przez ustawienie następującego przełącznika zgodności:</span><span class="sxs-lookup"><span data-stu-id="af71b-107">Alternatively, the old behavior (of not flowing <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName>) may be opted into by setting the following compatibility switch:</span></span>

```csharp
AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true);
```

<span data-ttu-id="af71b-108">Ten problem został rozwiązany przez WPF w .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="af71b-108">This issue has been fixed by WPF in .NET Framework 4.6.2.</span></span> <span data-ttu-id="af71b-109">Został również ustalony w programie .NET Frameworks 4,6, 4.6.1 do [KB 3139549](https://support.microsoft.com/kb/3139549).</span><span class="sxs-lookup"><span data-stu-id="af71b-109">It has also been fixed in .NET Frameworks 4.6, 4.6.1 through [KB 3139549](https://support.microsoft.com/kb/3139549).</span></span> <span data-ttu-id="af71b-110">Aplikacje ukierunkowane na .NET Framework 4,6 lub nowsze automatycznie otrzymają odpowiednie zachowanie w aplikacjach WPF — <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> ) byłyby zachowywane między operacjami dyspozytora.</span><span class="sxs-lookup"><span data-stu-id="af71b-110">Applications targeting .NET Framework 4.6 or later will automatically get the right behavior in WPF applications - <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName>) would be preserved across Dispatcher operations.</span></span>

| <span data-ttu-id="af71b-111">Nazwa</span><span class="sxs-lookup"><span data-stu-id="af71b-111">Name</span></span>    | <span data-ttu-id="af71b-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="af71b-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="af71b-113">Zakres</span><span class="sxs-lookup"><span data-stu-id="af71b-113">Scope</span></span>   | <span data-ttu-id="af71b-114">Mały</span><span class="sxs-lookup"><span data-stu-id="af71b-114">Minor</span></span>       |
| <span data-ttu-id="af71b-115">Wersja</span><span class="sxs-lookup"><span data-stu-id="af71b-115">Version</span></span> | <span data-ttu-id="af71b-116">4.6</span><span class="sxs-lookup"><span data-stu-id="af71b-116">4.6</span></span>         |
| <span data-ttu-id="af71b-117">Typ</span><span class="sxs-lookup"><span data-stu-id="af71b-117">Type</span></span>    | <span data-ttu-id="af71b-118">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="af71b-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="af71b-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="af71b-119">Affected APIs</span></span>

- <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType>
- <xref:System.Threading.Thread.CurrentCulture?displayProperty=nameWithType>
- <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=nameWithType>
- <xref:System.Threading.Thread.CurrentUICulture?displayProperty=nameWithType>
