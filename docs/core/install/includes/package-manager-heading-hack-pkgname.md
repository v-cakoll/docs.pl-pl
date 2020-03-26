---
ms.openlocfilehash: 4340ed7444681b4601dea50c93926b0ee0c07eec
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134109"
---

<span data-ttu-id="145b9-101">Pakiety dodane do kanałów menedżera pakietów są `{product}-{type}-{version}`nazwane w formacie hackable: .</span><span class="sxs-lookup"><span data-stu-id="145b9-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="145b9-102">**Produktu**</span><span class="sxs-lookup"><span data-stu-id="145b9-102">**product**</span></span>\
<span data-ttu-id="145b9-103">Typ produktu .NET do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="145b9-103">The type of .NET product to install.</span></span> <span data-ttu-id="145b9-104">Prawidłowe opcje to:</span><span class="sxs-lookup"><span data-stu-id="145b9-104">Valid options are:</span></span>

  - <span data-ttu-id="145b9-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="145b9-105">dotnet</span></span>
  - <span data-ttu-id="145b9-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="145b9-106">aspnetcore</span></span>

- <span data-ttu-id="145b9-107">**Typu**</span><span class="sxs-lookup"><span data-stu-id="145b9-107">**type**</span></span>\
<span data-ttu-id="145b9-108">Wybiera SDK lub środowisko wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="145b9-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="145b9-109">Prawidłowe opcje to:</span><span class="sxs-lookup"><span data-stu-id="145b9-109">Valid options are:</span></span>

  - <span data-ttu-id="145b9-110">sdk</span><span class="sxs-lookup"><span data-stu-id="145b9-110">sdk</span></span>
  - <span data-ttu-id="145b9-111">środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="145b9-111">runtime</span></span>

- <span data-ttu-id="145b9-112">**Wersja**</span><span class="sxs-lookup"><span data-stu-id="145b9-112">**version**</span></span>\
<span data-ttu-id="145b9-113">Wersja pakietu SDK lub środowiska wykonawczego do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="145b9-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="145b9-114">W tym artykule zawsze będzie instrukcje dotyczące najnowszej obsługiwanej wersji.</span><span class="sxs-lookup"><span data-stu-id="145b9-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="145b9-115">Prawidłowe opcje to każda wydana wersja, taka jak:</span><span class="sxs-lookup"><span data-stu-id="145b9-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="145b9-116">3.1</span><span class="sxs-lookup"><span data-stu-id="145b9-116">3.1</span></span>
  - <span data-ttu-id="145b9-117">3.0</span><span class="sxs-lookup"><span data-stu-id="145b9-117">3.0</span></span>
  - <span data-ttu-id="145b9-118">2.1</span><span class="sxs-lookup"><span data-stu-id="145b9-118">2.1</span></span>

  <span data-ttu-id="145b9-119">Jest możliwe, że SDK/runtime próbujesz pobrać nie jest dostępny dla twojej dystrybucji Linuksa.</span><span class="sxs-lookup"><span data-stu-id="145b9-119">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="145b9-120">Aby uzyskać listę obsługiwanych dystrybucji, zobacz [.NET Core zależności i wymagania](../dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="145b9-120">For a list of supported distributions, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>

### <a name="examples"></a><span data-ttu-id="145b9-121">Przykłady</span><span class="sxs-lookup"><span data-stu-id="145b9-121">Examples</span></span>

- <span data-ttu-id="145b9-122">Zainstaluj środowisko wykonawcze ASP.NET Core 3.1:`aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="145b9-122">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="145b9-123">Zainstaluj środowisko uruchomieniowe .NET Core 2.1:`dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="145b9-123">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="145b9-124">Zainstaluj pakiet .NET Core 3.1 SDK:`dotnet-sdk-3.1`</span><span class="sxs-lookup"><span data-stu-id="145b9-124">Install the .NET Core 3.1 SDK: `dotnet-sdk-3.1`</span></span>

### <a name="package-missing"></a><span data-ttu-id="145b9-125">Brak pakietu</span><span class="sxs-lookup"><span data-stu-id="145b9-125">Package missing</span></span>

<span data-ttu-id="145b9-126">Jeśli kombinacja wersji pakietu nie działa, nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="145b9-126">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="145b9-127">Na przykład nie ma ASP.NET core SDK, składniki SDK są dołączone do .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="145b9-127">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="145b9-128">Wartość `aspnetcore-sdk-2.2` jest niepoprawna `dotnet-sdk-2.2`i powinna być .</span><span class="sxs-lookup"><span data-stu-id="145b9-128">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="145b9-129">Aby uzyskać listę dystrybucji systemu Linux obsługiwanych przez program .NET Core, zobacz [.NET Core zależności i wymagania](../dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="145b9-129">For a list of Linux distributions supported by .NET Core, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>
