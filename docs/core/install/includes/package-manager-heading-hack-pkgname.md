---
ms.openlocfilehash: 7a55641b3673dc4d8d9b328f0de99b7247ca51d4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450885"
---

<span data-ttu-id="6ab62-101">Pakiety dodane do kanałów informacyjnych Menedżera pakietów są nazywane w formacie włamywania: `{product}-{type}-{version}`.</span><span class="sxs-lookup"><span data-stu-id="6ab62-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="6ab62-102">\ **produktu**</span><span class="sxs-lookup"><span data-stu-id="6ab62-102">**product**\</span></span>
<span data-ttu-id="6ab62-103">Typ produktu .NET do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="6ab62-103">The type of .NET product to install.</span></span> <span data-ttu-id="6ab62-104">Prawidłowe opcje to:</span><span class="sxs-lookup"><span data-stu-id="6ab62-104">Valid options are:</span></span>

  - <span data-ttu-id="6ab62-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="6ab62-105">dotnet</span></span>
  - <span data-ttu-id="6ab62-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="6ab62-106">aspnetcore</span></span>

- <span data-ttu-id="6ab62-107">**typ**</span><span class="sxs-lookup"><span data-stu-id="6ab62-107">**type**</span></span>\
<span data-ttu-id="6ab62-108">Wybiera zestaw SDK lub środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="6ab62-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="6ab62-109">Prawidłowe opcje to:</span><span class="sxs-lookup"><span data-stu-id="6ab62-109">Valid options are:</span></span>

  - <span data-ttu-id="6ab62-110">sdk</span><span class="sxs-lookup"><span data-stu-id="6ab62-110">sdk</span></span>
  - <span data-ttu-id="6ab62-111">środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="6ab62-111">runtime</span></span>

- <span data-ttu-id="6ab62-112">\ **wersji**</span><span class="sxs-lookup"><span data-stu-id="6ab62-112">**version**\</span></span>
<span data-ttu-id="6ab62-113">Wersja zestawu SDK lub środowiska uruchomieniowego do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="6ab62-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="6ab62-114">Ten artykuł będzie zawsze zawierać instrukcje dotyczące najnowszej obsługiwanej wersji.</span><span class="sxs-lookup"><span data-stu-id="6ab62-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="6ab62-115">Prawidłowe opcje to wszystkie wydane wersje, takie jak:</span><span class="sxs-lookup"><span data-stu-id="6ab62-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="6ab62-116">3.0</span><span class="sxs-lookup"><span data-stu-id="6ab62-116">3.0</span></span>
  - <span data-ttu-id="6ab62-117">2.2</span><span class="sxs-lookup"><span data-stu-id="6ab62-117">2.2</span></span>
  - <span data-ttu-id="6ab62-118">2.1</span><span class="sxs-lookup"><span data-stu-id="6ab62-118">2.1</span></span>

### <a name="examples"></a><span data-ttu-id="6ab62-119">Przykłady</span><span class="sxs-lookup"><span data-stu-id="6ab62-119">Examples</span></span>

- <span data-ttu-id="6ab62-120">Zainstaluj zestaw SDK platformy .NET Core 2,2: `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="6ab62-120">Install the .NET Core 2.2 SDK: `dotnet-sdk-2.2`</span></span>
- <span data-ttu-id="6ab62-121">Zainstaluj środowisko uruchomieniowe ASP.NET Core 3,0: `aspnetcore-runtime-3.0`</span><span class="sxs-lookup"><span data-stu-id="6ab62-121">Install the ASP.NET Core 3.0 runtime: `aspnetcore-runtime-3.0`</span></span>
- <span data-ttu-id="6ab62-122">Zainstaluj środowisko uruchomieniowe programu .NET Core 2,1: `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="6ab62-122">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>

### <a name="troubleshoot"></a><span data-ttu-id="6ab62-123">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="6ab62-123">Troubleshoot</span></span>

<span data-ttu-id="6ab62-124">Jeśli kombinacja pakietów nie działa, jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="6ab62-124">If the package combination doesn't work, it's not available.</span></span> <span data-ttu-id="6ab62-125">Na przykład nie istnieje zestaw ASP.NET Core SDK, składniki zestawu SDK są dołączone do zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="6ab62-125">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="6ab62-126">Wartość `aspnetcore-sdk-2.2` jest niepoprawna i powinna być `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="6ab62-126">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`</span></span>
