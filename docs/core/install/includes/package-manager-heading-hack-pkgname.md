---
ms.openlocfilehash: 7723892a33bf7dd8e475b2f696db5d9ab287e182
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602993"
---

<span data-ttu-id="545dd-101">Pakiety dodane do źródeł Menedżera pakietów są nazywane w formacie włamywania: `{product}-{type}-{version}` .</span><span class="sxs-lookup"><span data-stu-id="545dd-101">The packages added to package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="545dd-102">**iloczyn**</span><span class="sxs-lookup"><span data-stu-id="545dd-102">**product**</span></span>\
<span data-ttu-id="545dd-103">Typ produktu .NET do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="545dd-103">The type of .NET product to install.</span></span> <span data-ttu-id="545dd-104">Prawidłowe opcje to:</span><span class="sxs-lookup"><span data-stu-id="545dd-104">Valid options are:</span></span>

  - <span data-ttu-id="545dd-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="545dd-105">dotnet</span></span>
  - <span data-ttu-id="545dd-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="545dd-106">aspnetcore</span></span>

- <span data-ttu-id="545dd-107">**Wprowadź**</span><span class="sxs-lookup"><span data-stu-id="545dd-107">**type**</span></span>\
<span data-ttu-id="545dd-108">Wybiera zestaw SDK lub środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="545dd-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="545dd-109">Prawidłowe opcje to:</span><span class="sxs-lookup"><span data-stu-id="545dd-109">Valid options are:</span></span>

  - <span data-ttu-id="545dd-110">sdk</span><span class="sxs-lookup"><span data-stu-id="545dd-110">sdk</span></span>
  - <span data-ttu-id="545dd-111">środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="545dd-111">runtime</span></span>

- <span data-ttu-id="545dd-112">**Wersja**</span><span class="sxs-lookup"><span data-stu-id="545dd-112">**version**</span></span>\
<span data-ttu-id="545dd-113">Wersja zestawu SDK lub środowiska uruchomieniowego do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="545dd-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="545dd-114">Ten artykuł będzie zawsze zawierać instrukcje dotyczące najnowszej obsługiwanej wersji.</span><span class="sxs-lookup"><span data-stu-id="545dd-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="545dd-115">Prawidłowe opcje to wszystkie wydane wersje, takie jak:</span><span class="sxs-lookup"><span data-stu-id="545dd-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="545dd-116">3,1</span><span class="sxs-lookup"><span data-stu-id="545dd-116">3.1</span></span>
  - <span data-ttu-id="545dd-117">3.0</span><span class="sxs-lookup"><span data-stu-id="545dd-117">3.0</span></span>
  - <span data-ttu-id="545dd-118">2.1</span><span class="sxs-lookup"><span data-stu-id="545dd-118">2.1</span></span>

  <span data-ttu-id="545dd-119">Możliwe, że zestaw SDK/środowisko uruchomieniowe, które próbujesz pobrać, nie jest dostępny dla dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="545dd-119">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="545dd-120">Aby zapoznać się z listą obsługiwanych dystrybucji, zobacz temat [zależności i wymagania dotyczące platformy .NET Core](../linux.md).</span><span class="sxs-lookup"><span data-stu-id="545dd-120">For a list of supported distributions, see [.NET Core dependencies and requirements](../linux.md).</span></span>

### <a name="examples"></a><span data-ttu-id="545dd-121">Przykłady</span><span class="sxs-lookup"><span data-stu-id="545dd-121">Examples</span></span>

- <span data-ttu-id="545dd-122">Zainstaluj środowisko uruchomieniowe ASP.NET Core 3,1:`aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="545dd-122">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="545dd-123">Zainstaluj środowisko uruchomieniowe programu .NET Core 2,1:`dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="545dd-123">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="545dd-124">Zainstaluj zestaw SDK platformy .NET Core 3,1:`dotnet-sdk-3.1`</span><span class="sxs-lookup"><span data-stu-id="545dd-124">Install the .NET Core 3.1 SDK: `dotnet-sdk-3.1`</span></span>

### <a name="package-missing"></a><span data-ttu-id="545dd-125">Brak pakietu</span><span class="sxs-lookup"><span data-stu-id="545dd-125">Package missing</span></span>

<span data-ttu-id="545dd-126">Jeśli kombinacja pakiet-wersja nie działa, jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="545dd-126">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="545dd-127">Na przykład nie istnieje zestaw ASP.NET Core SDK, składniki zestawu SDK są dołączone do zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="545dd-127">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="545dd-128">Wartość `aspnetcore-sdk-2.2` jest niepoprawna i powinna być `dotnet-sdk-2.2` .</span><span class="sxs-lookup"><span data-stu-id="545dd-128">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="545dd-129">Aby uzyskać listę dystrybucji systemu Linux obsługiwanych przez platformę .NET Core, zobacz [zależności i wymagania dotyczące platformy .NET Core](../linux.md).</span><span class="sxs-lookup"><span data-stu-id="545dd-129">For a list of Linux distributions supported by .NET Core, see [.NET Core dependencies and requirements](../linux.md).</span></span>
