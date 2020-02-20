---
ms.openlocfilehash: 51b3c1b3e3d61b23a0511ca807afef0269ac9ee4
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77465978"
---

<span data-ttu-id="a527f-101">Pakiety dodane do kanałów informacyjnych Menedżera pakietów są nazywane w formacie włamywania: `{product}-{type}-{version}`.</span><span class="sxs-lookup"><span data-stu-id="a527f-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="a527f-102">\ **produktu**</span><span class="sxs-lookup"><span data-stu-id="a527f-102">**product**\</span></span>
<span data-ttu-id="a527f-103">Typ produktu .NET do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="a527f-103">The type of .NET product to install.</span></span> <span data-ttu-id="a527f-104">Prawidłowe opcje to:</span><span class="sxs-lookup"><span data-stu-id="a527f-104">Valid options are:</span></span>

  - <span data-ttu-id="a527f-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="a527f-105">dotnet</span></span>
  - <span data-ttu-id="a527f-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="a527f-106">aspnetcore</span></span>

- <span data-ttu-id="a527f-107">**typ**</span><span class="sxs-lookup"><span data-stu-id="a527f-107">**type**</span></span>\
<span data-ttu-id="a527f-108">Wybiera zestaw SDK lub środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="a527f-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="a527f-109">Prawidłowe opcje to:</span><span class="sxs-lookup"><span data-stu-id="a527f-109">Valid options are:</span></span>

  - <span data-ttu-id="a527f-110">sdk</span><span class="sxs-lookup"><span data-stu-id="a527f-110">sdk</span></span>
  - <span data-ttu-id="a527f-111">środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a527f-111">runtime</span></span>

- <span data-ttu-id="a527f-112">\ **wersji**</span><span class="sxs-lookup"><span data-stu-id="a527f-112">**version**\</span></span>
<span data-ttu-id="a527f-113">Wersja zestawu SDK lub środowiska uruchomieniowego do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="a527f-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="a527f-114">Ten artykuł będzie zawsze zawierać instrukcje dotyczące najnowszej obsługiwanej wersji.</span><span class="sxs-lookup"><span data-stu-id="a527f-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="a527f-115">Prawidłowe opcje to wszystkie wydane wersje, takie jak:</span><span class="sxs-lookup"><span data-stu-id="a527f-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="a527f-116">3.1</span><span class="sxs-lookup"><span data-stu-id="a527f-116">3.1</span></span>
  - <span data-ttu-id="a527f-117">3.0</span><span class="sxs-lookup"><span data-stu-id="a527f-117">3.0</span></span>
  - <span data-ttu-id="a527f-118">2.1</span><span class="sxs-lookup"><span data-stu-id="a527f-118">2.1</span></span>

  <span data-ttu-id="a527f-119">Możliwe, że zestaw SDK/środowisko uruchomieniowe, które próbujesz pobrać, nie jest dostępny dla dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="a527f-119">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="a527f-120">Aby zapoznać się z listą obsługiwanych dystrybucji, zobacz temat [zależności i wymagania dotyczące platformy .NET Core](../dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="a527f-120">For a list of supported distributions, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>

### <a name="examples"></a><span data-ttu-id="a527f-121">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a527f-121">Examples</span></span>

- <span data-ttu-id="a527f-122">Zainstaluj środowisko uruchomieniowe ASP.NET Core 3,1: `aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="a527f-122">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="a527f-123">Zainstaluj środowisko uruchomieniowe programu .NET Core 2,1: `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="a527f-123">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="a527f-124">Zainstaluj zestaw SDK platformy .NET Core 3,0: `dotnet-sdk-3.0`</span><span class="sxs-lookup"><span data-stu-id="a527f-124">Install the .NET Core 3.0 SDK: `dotnet-sdk-3.0`</span></span>

### <a name="package-missing"></a><span data-ttu-id="a527f-125">Brak pakietu</span><span class="sxs-lookup"><span data-stu-id="a527f-125">Package missing</span></span>

<span data-ttu-id="a527f-126">Jeśli kombinacja pakiet-wersja nie działa, jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="a527f-126">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="a527f-127">Na przykład nie istnieje zestaw ASP.NET Core SDK, składniki zestawu SDK są dołączone do zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="a527f-127">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="a527f-128">Wartość `aspnetcore-sdk-2.2` jest niepoprawna i powinna być `dotnet-sdk-2.2`.</span><span class="sxs-lookup"><span data-stu-id="a527f-128">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="a527f-129">Aby uzyskać listę dystrybucji systemu Linux obsługiwanych przez platformę .NET Core, zobacz [zależności i wymagania dotyczące platformy .NET Core](../dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="a527f-129">For a list of Linux distributions supported by .NET Core, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>
