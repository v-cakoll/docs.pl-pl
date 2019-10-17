---
ms.openlocfilehash: 16b9fde49f513643a37f65f3e926a34fc991c55a
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393928"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a><span data-ttu-id="aea26-101">Hosting: ObjectPoolProvider usunięte z zależności WebHostBuilder</span><span class="sxs-lookup"><span data-stu-id="aea26-101">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>

<span data-ttu-id="aea26-102">W ramach wprowadzania ASP.NET Core więcej opłat za odtwarzanie, `ObjectPoolProvider` został usunięty z głównego zestawu zależności.</span><span class="sxs-lookup"><span data-stu-id="aea26-102">As part of making ASP.NET Core more pay for play, the `ObjectPoolProvider` was removed from the main set of dependencies.</span></span> <span data-ttu-id="aea26-103">Określone składniki polegające na `ObjectPoolProvider` teraz dodają go.</span><span class="sxs-lookup"><span data-stu-id="aea26-103">Specific components relying on `ObjectPoolProvider` now add it themselves.</span></span>

<span data-ttu-id="aea26-104">W przypadku dyskusji zobacz [ASPNET/AspNetCore # 5944](https://github.com/aspnet/AspNetCore/issues/5944).</span><span class="sxs-lookup"><span data-stu-id="aea26-104">For discussion, see [aspnet/AspNetCore#5944](https://github.com/aspnet/AspNetCore/issues/5944).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="aea26-105">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="aea26-105">Version introduced</span></span>

<span data-ttu-id="aea26-106">3.0</span><span class="sxs-lookup"><span data-stu-id="aea26-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="aea26-107">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="aea26-107">Old behavior</span></span>

<span data-ttu-id="aea26-108">`WebHostBuilder` domyślnie zapewnia `ObjectPoolProvider` w kontenerze DI.</span><span class="sxs-lookup"><span data-stu-id="aea26-108">`WebHostBuilder` provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="aea26-109">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="aea26-109">New behavior</span></span>

<span data-ttu-id="aea26-110">`WebHostBuilder` nie zapewnia już domyślnie `ObjectPoolProvider` w kontenerze DI.</span><span class="sxs-lookup"><span data-stu-id="aea26-110">`WebHostBuilder` no longer provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="aea26-111">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="aea26-111">Reason for change</span></span>

<span data-ttu-id="aea26-112">Ta zmiana została wprowadzona, aby ASP.NET Core więcej opłat za odtwarzanie.</span><span class="sxs-lookup"><span data-stu-id="aea26-112">This change was made to make ASP.NET Core more pay for play.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="aea26-113">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="aea26-113">Recommended action</span></span>

<span data-ttu-id="aea26-114">Jeśli składnik wymaga `ObjectPoolProvider`, należy go dodać do zależności za pośrednictwem `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="aea26-114">If your component requires `ObjectPoolProvider`, it needs to be added to your dependencies via the `IServiceCollection`.</span></span>

#### <a name="category"></a><span data-ttu-id="aea26-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="aea26-115">Category</span></span>

<span data-ttu-id="aea26-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="aea26-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="aea26-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="aea26-117">Affected APIs</span></span>

<span data-ttu-id="aea26-118">Brak</span><span class="sxs-lookup"><span data-stu-id="aea26-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
