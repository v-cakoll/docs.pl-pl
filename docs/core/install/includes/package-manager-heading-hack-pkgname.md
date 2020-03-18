---
ms.openlocfilehash: 51b3c1b3e3d61b23a0511ca807afef0269ac9ee4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77465978"
---

<span data-ttu-id="298cb-101">Pakiety dodane do kanałów menedżera pakietów są nazwane `{product}-{type}-{version}`w formacie hackable: .</span><span class="sxs-lookup"><span data-stu-id="298cb-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="298cb-102">**Produktu**</span><span class="sxs-lookup"><span data-stu-id="298cb-102">**product**</span></span>\
<span data-ttu-id="298cb-103">Typ produktu .NET do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="298cb-103">The type of .NET product to install.</span></span> <span data-ttu-id="298cb-104">Prawidłowe opcje to:</span><span class="sxs-lookup"><span data-stu-id="298cb-104">Valid options are:</span></span>

  - <span data-ttu-id="298cb-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="298cb-105">dotnet</span></span>
  - <span data-ttu-id="298cb-106">aspnetcore (polski)</span><span class="sxs-lookup"><span data-stu-id="298cb-106">aspnetcore</span></span>

- <span data-ttu-id="298cb-107">**Typu**</span><span class="sxs-lookup"><span data-stu-id="298cb-107">**type**</span></span>\
<span data-ttu-id="298cb-108">Wybiera zestaw SDK lub czas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="298cb-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="298cb-109">Prawidłowe opcje to:</span><span class="sxs-lookup"><span data-stu-id="298cb-109">Valid options are:</span></span>

  - <span data-ttu-id="298cb-110">sdk</span><span class="sxs-lookup"><span data-stu-id="298cb-110">sdk</span></span>
  - <span data-ttu-id="298cb-111">środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="298cb-111">runtime</span></span>

- <span data-ttu-id="298cb-112">**Wersja**</span><span class="sxs-lookup"><span data-stu-id="298cb-112">**version**</span></span>\
<span data-ttu-id="298cb-113">Wersja sdk lub czas wykonywania do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="298cb-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="298cb-114">W tym artykule zawsze zostaną opublikowane instrukcje dotyczące najnowszej obsługiwanej wersji.</span><span class="sxs-lookup"><span data-stu-id="298cb-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="298cb-115">Prawidłowe opcje to dowolna wydana wersja, taka jak:</span><span class="sxs-lookup"><span data-stu-id="298cb-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="298cb-116">3.1</span><span class="sxs-lookup"><span data-stu-id="298cb-116">3.1</span></span>
  - <span data-ttu-id="298cb-117">3.0</span><span class="sxs-lookup"><span data-stu-id="298cb-117">3.0</span></span>
  - <span data-ttu-id="298cb-118">2.1</span><span class="sxs-lookup"><span data-stu-id="298cb-118">2.1</span></span>

  <span data-ttu-id="298cb-119">Możliwe, że zestaw SDK/runtime, który próbujesz pobrać, nie jest dostępny dla twojej dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="298cb-119">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="298cb-120">Aby uzyskać listę obsługiwanych dystrybucji, zobacz [zależności i wymagania programu .NET Core](../dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="298cb-120">For a list of supported distributions, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>

### <a name="examples"></a><span data-ttu-id="298cb-121">Przykłady</span><span class="sxs-lookup"><span data-stu-id="298cb-121">Examples</span></span>

- <span data-ttu-id="298cb-122">Zainstaluj ASP.NET core 3.1:`aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="298cb-122">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="298cb-123">Zainstaluj czas uruchomieniowy .NET Core 2.1:`dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="298cb-123">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="298cb-124">Zainstaluj zestaw SDK .NET Core 3.0:`dotnet-sdk-3.0`</span><span class="sxs-lookup"><span data-stu-id="298cb-124">Install the .NET Core 3.0 SDK: `dotnet-sdk-3.0`</span></span>

### <a name="package-missing"></a><span data-ttu-id="298cb-125">Brakuje pakietu</span><span class="sxs-lookup"><span data-stu-id="298cb-125">Package missing</span></span>

<span data-ttu-id="298cb-126">Jeśli kombinacja wersji pakietu nie działa, nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="298cb-126">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="298cb-127">Na przykład nie ma ASP.NET Core SDK, składniki sdk są dołączone do .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="298cb-127">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="298cb-128">Wartość `aspnetcore-sdk-2.2` jest niepoprawna `dotnet-sdk-2.2`i powinna być .</span><span class="sxs-lookup"><span data-stu-id="298cb-128">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="298cb-129">Aby uzyskać listę dystrybucji systemu Linux obsługiwanych przez program .NET Core, zobacz [zależności i wymagania programu .NET Core](../dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="298cb-129">For a list of Linux distributions supported by .NET Core, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>
