---
ms.openlocfilehash: ef3e4f9f8145677732b9d2e66d416be277697f55
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920634"
---

<span data-ttu-id="0ca7c-101">Pakiety dodane do kanałów informacyjnych Menedżera pakietów są nazywane w formacie włamywania: `{product}-{type}-{version}`.</span><span class="sxs-lookup"><span data-stu-id="0ca7c-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="0ca7c-102">\ **produktu**</span><span class="sxs-lookup"><span data-stu-id="0ca7c-102">**product**\</span></span>
<span data-ttu-id="0ca7c-103">Typ produktu .NET do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="0ca7c-103">The type of .NET product to install.</span></span> <span data-ttu-id="0ca7c-104">Prawidłowe opcje to:</span><span class="sxs-lookup"><span data-stu-id="0ca7c-104">Valid options are:</span></span>

  - <span data-ttu-id="0ca7c-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="0ca7c-105">dotnet</span></span>
  - <span data-ttu-id="0ca7c-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="0ca7c-106">aspnetcore</span></span>

- <span data-ttu-id="0ca7c-107">**typ**</span><span class="sxs-lookup"><span data-stu-id="0ca7c-107">**type**</span></span>\
<span data-ttu-id="0ca7c-108">Wybiera zestaw SDK lub środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="0ca7c-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="0ca7c-109">Prawidłowe opcje to:</span><span class="sxs-lookup"><span data-stu-id="0ca7c-109">Valid options are:</span></span>

  - <span data-ttu-id="0ca7c-110">sdk</span><span class="sxs-lookup"><span data-stu-id="0ca7c-110">sdk</span></span>
  - <span data-ttu-id="0ca7c-111">środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="0ca7c-111">runtime</span></span>

- <span data-ttu-id="0ca7c-112">\ **wersji**</span><span class="sxs-lookup"><span data-stu-id="0ca7c-112">**version**\</span></span>
<span data-ttu-id="0ca7c-113">Wersja zestawu SDK lub środowiska uruchomieniowego do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="0ca7c-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="0ca7c-114">Ten artykuł będzie zawsze zawierać instrukcje dotyczące najnowszej obsługiwanej wersji.</span><span class="sxs-lookup"><span data-stu-id="0ca7c-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="0ca7c-115">Prawidłowe opcje to wszystkie wydane wersje, takie jak:</span><span class="sxs-lookup"><span data-stu-id="0ca7c-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="0ca7c-116">3.0</span><span class="sxs-lookup"><span data-stu-id="0ca7c-116">3.0</span></span>
  - <span data-ttu-id="0ca7c-117">2.2</span><span class="sxs-lookup"><span data-stu-id="0ca7c-117">2.2</span></span>
  - <span data-ttu-id="0ca7c-118">2.1</span><span class="sxs-lookup"><span data-stu-id="0ca7c-118">2.1</span></span>

### <a name="examples"></a><span data-ttu-id="0ca7c-119">Przykłady</span><span class="sxs-lookup"><span data-stu-id="0ca7c-119">Examples</span></span>

- <span data-ttu-id="0ca7c-120">Zainstaluj zestaw SDK platformy .NET Core 2,2: `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="0ca7c-120">Install the .NET Core 2.2 SDK: `dotnet-sdk-2.2`</span></span>
- <span data-ttu-id="0ca7c-121">Zainstaluj środowisko uruchomieniowe ASP.NET Core 3,1: `aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="0ca7c-121">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="0ca7c-122">Zainstaluj środowisko uruchomieniowe programu .NET Core 2,1: `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="0ca7c-122">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>

### <a name="package-missing"></a><span data-ttu-id="0ca7c-123">Brak pakietu</span><span class="sxs-lookup"><span data-stu-id="0ca7c-123">Package missing</span></span>

<span data-ttu-id="0ca7c-124">Jeśli kombinacja pakiet-wersja nie działa, jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="0ca7c-124">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="0ca7c-125">Na przykład nie istnieje zestaw ASP.NET Core SDK, składniki zestawu SDK są dołączone do zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="0ca7c-125">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="0ca7c-126">Wartość `aspnetcore-sdk-2.2` jest niepoprawna i powinna być `dotnet-sdk-2.2`.</span><span class="sxs-lookup"><span data-stu-id="0ca7c-126">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span>
