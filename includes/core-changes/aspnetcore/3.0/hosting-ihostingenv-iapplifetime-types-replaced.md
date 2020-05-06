---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394332"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a><span data-ttu-id="587b4-101">Hosting: typy IHostingEnvironment i IApplicationLifetime oznaczone jako przestarzałe i zastąpione</span><span class="sxs-lookup"><span data-stu-id="587b4-101">Hosting: IHostingEnvironment and IApplicationLifetime types marked obsolete and replaced</span></span>

<span data-ttu-id="587b4-102">Wprowadzono nowe typy do zastępowania istniejących `IHostingEnvironment` i `IApplicationLifetime` typów.</span><span class="sxs-lookup"><span data-stu-id="587b4-102">New types have been introduced to replace existing `IHostingEnvironment` and `IApplicationLifetime` types.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="587b4-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="587b4-103">Version introduced</span></span>

<span data-ttu-id="587b4-104">3.0</span><span class="sxs-lookup"><span data-stu-id="587b4-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="587b4-105">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="587b4-105">Old behavior</span></span>

<span data-ttu-id="587b4-106">`IHostingEnvironment` Istnieją dwa różne `IApplicationLifetime` i typy z `Microsoft.Extensions.Hosting` i. `Microsoft.AspNetCore.Hosting`</span><span class="sxs-lookup"><span data-stu-id="587b4-106">There were two different `IHostingEnvironment` and `IApplicationLifetime` types from `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="587b4-107">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="587b4-107">New behavior</span></span>

<span data-ttu-id="587b4-108">Stare typy zostały oznaczone jako przestarzałe i zastąpione nowymi typami.</span><span class="sxs-lookup"><span data-stu-id="587b4-108">The old types have been marked as obsolete and replaced with new types.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="587b4-109">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="587b4-109">Reason for change</span></span>

<span data-ttu-id="587b4-110">Kiedy `Microsoft.Extensions.Hosting` został wprowadzony w ASP.NET Core 2,1, niektóre typy takie `IHostingEnvironment` jak `IApplicationLifetime` i zostały skopiowane z `Microsoft.AspNetCore.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="587b4-110">When `Microsoft.Extensions.Hosting` was introduced in ASP.NET Core 2.1, some types like `IHostingEnvironment` and `IApplicationLifetime` were copied from `Microsoft.AspNetCore.Hosting`.</span></span> <span data-ttu-id="587b4-111">Niektóre zmiany w ASP.NET Core 3,0 powodują, `Microsoft.Extensions.Hosting` że aplikacje zawierają zarówno `Microsoft.AspNetCore.Hosting` przestrzeń nazw, jak i.</span><span class="sxs-lookup"><span data-stu-id="587b4-111">Some ASP.NET Core 3.0 changes cause apps to include both the `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting` namespaces.</span></span> <span data-ttu-id="587b4-112">Każde użycie tych zduplikowanych typów powoduje błąd kompilatora "niejednoznaczne odwołanie", gdy następuje odwołanie do obu przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="587b4-112">Any use of those duplicate types causes an "ambiguous reference" compiler error when both namespaces are referenced.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="587b4-113">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="587b4-113">Recommended action</span></span>

<span data-ttu-id="587b4-114">Zamieniono wszystkie użycia starych typów na nowo wprowadzone typy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="587b4-114">Replaced any usages of the old types with the newly introduced types as below:</span></span>

<span data-ttu-id="587b4-115">**Przestarzałe typy (ostrzeżenie):**</span><span class="sxs-lookup"><span data-stu-id="587b4-115">**Obsolete types (warning):**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>

<span data-ttu-id="587b4-116">**Nowe typy:**</span><span class="sxs-lookup"><span data-stu-id="587b4-116">**New types:**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment?displayProperty=nameWithType>
- `Microsoft.AspNetCore.Hosting.IWebHostEnvironment : IHostEnvironment`
- <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.Environments?displayProperty=nameWithType>

<span data-ttu-id="587b4-117">Nowe `IHostEnvironment` `IsDevelopment` i `IsProduction` rozszerzenie metody znajdują się w `Microsoft.Extensions.Hosting` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="587b4-117">The new `IHostEnvironment` `IsDevelopment` and `IsProduction` extension methods are in the `Microsoft.Extensions.Hosting` namespace.</span></span> <span data-ttu-id="587b4-118">Ta przestrzeń nazw może być konieczna do dodania do projektu.</span><span class="sxs-lookup"><span data-stu-id="587b4-118">That namespace may need to be added to your project.</span></span>

#### <a name="category"></a><span data-ttu-id="587b4-119">Kategoria</span><span class="sxs-lookup"><span data-stu-id="587b4-119">Category</span></span>

<span data-ttu-id="587b4-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="587b4-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="587b4-121">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="587b4-121">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.EnvironmentName`
- `T:Microsoft.AspNetCore.Hosting.IApplicationLifetime`
- `T:Microsoft.AspNetCore.Hosting.IHostingEnvironment`
- `T:Microsoft.Extensions.Hosting.EnvironmentName`
- `T:Microsoft.Extensions.Hosting.IApplicationLifetime`
- `T:Microsoft.Extensions.Hosting.IHostingEnvironment`

-->
