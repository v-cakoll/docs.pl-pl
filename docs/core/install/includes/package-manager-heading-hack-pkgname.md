---
ms.openlocfilehash: 47e8e15a64236d8ade2febb1add81fa4e5c030d9
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116149"
---

<span data-ttu-id="c1760-101">Pakiety dodane do kanałów informacyjnych Menedżera pakietów są nazywane w formacie włamywania: `{product}-{type}-{version}`.</span><span class="sxs-lookup"><span data-stu-id="c1760-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="c1760-102">\ **produktu**</span><span class="sxs-lookup"><span data-stu-id="c1760-102">**product**\</span></span>
<span data-ttu-id="c1760-103">Typ produktu .NET do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="c1760-103">The type of .NET product to install.</span></span> <span data-ttu-id="c1760-104">Prawidłowe opcje to:</span><span class="sxs-lookup"><span data-stu-id="c1760-104">Valid options are:</span></span>

  - <span data-ttu-id="c1760-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="c1760-105">dotnet</span></span>
  - <span data-ttu-id="c1760-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="c1760-106">aspnetcore</span></span>

- <span data-ttu-id="c1760-107">**typ**</span><span class="sxs-lookup"><span data-stu-id="c1760-107">**type**</span></span>\
<span data-ttu-id="c1760-108">Wybiera zestaw SDK lub środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="c1760-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="c1760-109">Prawidłowe opcje to:</span><span class="sxs-lookup"><span data-stu-id="c1760-109">Valid options are:</span></span>

  - <span data-ttu-id="c1760-110">sdk</span><span class="sxs-lookup"><span data-stu-id="c1760-110">sdk</span></span>
  - <span data-ttu-id="c1760-111">środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="c1760-111">runtime</span></span>

- <span data-ttu-id="c1760-112">\ **wersji**</span><span class="sxs-lookup"><span data-stu-id="c1760-112">**version**\</span></span>
<span data-ttu-id="c1760-113">Wersja zestawu SDK lub środowiska uruchomieniowego do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="c1760-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="c1760-114">Ten artykuł będzie zawsze zawierać instrukcje dotyczące najnowszej obsługiwanej wersji.</span><span class="sxs-lookup"><span data-stu-id="c1760-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="c1760-115">Prawidłowe opcje to wszystkie wydane wersje, takie jak:</span><span class="sxs-lookup"><span data-stu-id="c1760-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="c1760-116">3.0</span><span class="sxs-lookup"><span data-stu-id="c1760-116">3.0</span></span>
  - <span data-ttu-id="c1760-117">2.2</span><span class="sxs-lookup"><span data-stu-id="c1760-117">2.2</span></span>
  - <span data-ttu-id="c1760-118">2.1</span><span class="sxs-lookup"><span data-stu-id="c1760-118">2.1</span></span>

### <a name="examples"></a><span data-ttu-id="c1760-119">Przykłady</span><span class="sxs-lookup"><span data-stu-id="c1760-119">Examples</span></span>

- <span data-ttu-id="c1760-120">Zainstaluj zestaw SDK platformy .NET Core 2,2: `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="c1760-120">Install the .NET Core 2.2 SDK: `dotnet-sdk-2.2`</span></span>
- <span data-ttu-id="c1760-121">Zainstaluj środowisko uruchomieniowe ASP.NET Core 3,1: `aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="c1760-121">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="c1760-122">Zainstaluj środowisko uruchomieniowe programu .NET Core 2,1: `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="c1760-122">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>

### <a name="troubleshoot"></a><span data-ttu-id="c1760-123">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="c1760-123">Troubleshoot</span></span>

<span data-ttu-id="c1760-124">Jeśli kombinacja pakietów nie działa, jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="c1760-124">If the package combination doesn't work, it's not available.</span></span> <span data-ttu-id="c1760-125">Na przykład nie istnieje zestaw ASP.NET Core SDK, składniki zestawu SDK są dołączone do zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="c1760-125">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="c1760-126">Wartość `aspnetcore-sdk-2.2` jest niepoprawna i powinna być `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="c1760-126">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`</span></span>
