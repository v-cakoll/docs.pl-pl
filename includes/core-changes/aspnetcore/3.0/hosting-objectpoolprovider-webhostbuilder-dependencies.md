---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901616"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a><span data-ttu-id="e92d3-101">Hosting: ObjectPoolProvider usunięte z zależności WebHostBuilder</span><span class="sxs-lookup"><span data-stu-id="e92d3-101">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>

<span data-ttu-id="e92d3-102">W ramach wprowadzania ASP.NET Core więcej opłat za odtwarzanie, `ObjectPoolProvider` została usunięta z głównego zestawu zależności.</span><span class="sxs-lookup"><span data-stu-id="e92d3-102">As part of making ASP.NET Core more pay for play, the `ObjectPoolProvider` was removed from the main set of dependencies.</span></span> <span data-ttu-id="e92d3-103">Zależne składniki są teraz `ObjectPoolProvider` dodawane do siebie.</span><span class="sxs-lookup"><span data-stu-id="e92d3-103">Specific components relying on `ObjectPoolProvider` now add it themselves.</span></span>

<span data-ttu-id="e92d3-104">Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 5944](https://github.com/dotnet/aspnetcore/issues/5944).</span><span class="sxs-lookup"><span data-stu-id="e92d3-104">For discussion, see [dotnet/aspnetcore#5944](https://github.com/dotnet/aspnetcore/issues/5944).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e92d3-105">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e92d3-105">Version introduced</span></span>

<span data-ttu-id="e92d3-106">3.0</span><span class="sxs-lookup"><span data-stu-id="e92d3-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e92d3-107">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="e92d3-107">Old behavior</span></span>

<span data-ttu-id="e92d3-108">`WebHostBuilder`Domyślnie `ObjectPoolProvider` jest dostępna w kontenerze di.</span><span class="sxs-lookup"><span data-stu-id="e92d3-108">`WebHostBuilder` provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e92d3-109">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="e92d3-109">New behavior</span></span>

<span data-ttu-id="e92d3-110">`WebHostBuilder`nie zapewnia `ObjectPoolProvider` już domyślnego ustawienia w kontenerze di.</span><span class="sxs-lookup"><span data-stu-id="e92d3-110">`WebHostBuilder` no longer provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e92d3-111">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="e92d3-111">Reason for change</span></span>

<span data-ttu-id="e92d3-112">Ta zmiana została wprowadzona, aby ASP.NET Core więcej opłat za odtwarzanie.</span><span class="sxs-lookup"><span data-stu-id="e92d3-112">This change was made to make ASP.NET Core more pay for play.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e92d3-113">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="e92d3-113">Recommended action</span></span>

<span data-ttu-id="e92d3-114">Jeśli dany składnik wymaga `ObjectPoolProvider`programu, należy go dodać do swoich zależności za pośrednictwem `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="e92d3-114">If your component requires `ObjectPoolProvider`, it needs to be added to your dependencies via the `IServiceCollection`.</span></span>

#### <a name="category"></a><span data-ttu-id="e92d3-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="e92d3-115">Category</span></span>

<span data-ttu-id="e92d3-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e92d3-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e92d3-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="e92d3-117">Affected APIs</span></span>

<span data-ttu-id="e92d3-118">Brak</span><span class="sxs-lookup"><span data-stu-id="e92d3-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
