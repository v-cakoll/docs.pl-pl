---
title: polecenie usunięcia NuGet narzędzia dotnet
description: Polecenie dotnet-NuGet-DELETE Usuwa pakiet z serwera lub go wystawia.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 0950f03c0986bde17ae3e2e7170d402ea8222853
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733123"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="12fcf-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="12fcf-103">dotnet nuget delete</span></span>

<span data-ttu-id="12fcf-104">**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 1. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="12fcf-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="12fcf-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="12fcf-105">Name</span></span>

<span data-ttu-id="12fcf-106">`dotnet nuget delete` — usuwa pakiet z serwera lub go wystawia.</span><span class="sxs-lookup"><span data-stu-id="12fcf-106">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="12fcf-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="12fcf-107">Synopsis</span></span>

```dotnetcli
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a><span data-ttu-id="12fcf-108">Opis</span><span class="sxs-lookup"><span data-stu-id="12fcf-108">Description</span></span>

<span data-ttu-id="12fcf-109">Polecenie `dotnet nuget delete` usuwa pakiet z serwera lub go wystawia.</span><span class="sxs-lookup"><span data-stu-id="12fcf-109">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="12fcf-110">W przypadku [NuGet.org](https://www.nuget.org/)akcja ma na celu odlistowanie pakietu.</span><span class="sxs-lookup"><span data-stu-id="12fcf-110">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="12fcf-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="12fcf-111">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="12fcf-112">Nazwa/identyfikator pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="12fcf-112">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="12fcf-113">Wersja pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="12fcf-113">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="12fcf-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="12fcf-114">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="12fcf-115">Wymusza uruchomienie aplikacji przy użyciu niezmiennej, opartej na języku angielskim kultury.</span><span class="sxs-lookup"><span data-stu-id="12fcf-115">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="12fcf-116">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="12fcf-116">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="12fcf-117">Umożliwia zablokowanie polecenia i wymaga ręcznej akcji dla operacji takich jak uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="12fcf-117">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="12fcf-118">Opcja dostępna od wersji .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="12fcf-118">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="12fcf-119">Klucz interfejsu API dla serwera programu.</span><span class="sxs-lookup"><span data-stu-id="12fcf-119">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="12fcf-120">Nie dołącza "API/v2/Package" do źródłowego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="12fcf-120">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="12fcf-121">Opcja dostępna od wersji .NET Core 2,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="12fcf-121">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="12fcf-122">Nie monituje o dane wejściowe lub potwierdzone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="12fcf-122">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="12fcf-123">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="12fcf-123">Specifies the server URL.</span></span> <span data-ttu-id="12fcf-124">Obsługiwane adresy URL dla nuget.org obejmują `https://www.nuget.org`, `https://www.nuget.org/api/v3`i `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="12fcf-124">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="12fcf-125">W przypadku źródeł prywatnych Zastąp wartość Nazwa hosta (na przykład `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="12fcf-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

## <a name="examples"></a><span data-ttu-id="12fcf-126">Przykłady</span><span class="sxs-lookup"><span data-stu-id="12fcf-126">Examples</span></span>

* <span data-ttu-id="12fcf-127">Usuwa wersję 1,0 pakietu `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="12fcf-127">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="12fcf-128">Usuwa wersję 1,0 pakietu `Microsoft.AspNetCore.Mvc`, bez monitowania użytkownika o poświadczenia lub inne dane wejściowe:</span><span class="sxs-lookup"><span data-stu-id="12fcf-128">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
