---
title: polecenie dotnet nuget delete
description: Polecenie dotnet-nuget-delete usuwa lub usuwa pakiet z serwera.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 0950f03c0986bde17ae3e2e7170d402ea8222853
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733123"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="45a78-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="45a78-103">dotnet nuget delete</span></span>

<span data-ttu-id="45a78-104">**Ten artykuł dotyczy:** ✔️ .NET Core 1.x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="45a78-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="45a78-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="45a78-105">Name</span></span>

<span data-ttu-id="45a78-106">`dotnet nuget delete`- Usuwa lub usuwa pakiet z serwera.</span><span class="sxs-lookup"><span data-stu-id="45a78-106">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="45a78-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="45a78-107">Synopsis</span></span>

```dotnetcli
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a><span data-ttu-id="45a78-108">Opis</span><span class="sxs-lookup"><span data-stu-id="45a78-108">Description</span></span>

<span data-ttu-id="45a78-109">Polecenie `dotnet nuget delete` usuwa lub usuwa listę pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="45a78-109">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="45a78-110">W [przypadku nuget.org](https://www.nuget.org/)akcja polega na wykreślania pakietu z listy.</span><span class="sxs-lookup"><span data-stu-id="45a78-110">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="45a78-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="45a78-111">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="45a78-112">Nazwa/identyfikator pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="45a78-112">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="45a78-113">Wersja pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="45a78-113">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="45a78-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="45a78-114">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="45a78-115">Wymusza uruchamianie aplikacji przy użyciu niezmiennej kultury opartej na języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="45a78-115">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="45a78-116">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="45a78-116">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="45a78-117">Umożliwia blokowanie polecenia i wymaga ręcznego działania dla operacji, takich jak uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="45a78-117">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="45a78-118">Opcja dostępna od sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="45a78-118">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="45a78-119">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="45a78-119">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="45a78-120">Nie dołącza "api/v2/package" do źródłowego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="45a78-120">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="45a78-121">Opcja dostępna od sdk .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="45a78-121">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="45a78-122">Nie monituje o wprowadzenie danych przez użytkownika ani potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="45a78-122">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="45a78-123">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="45a78-123">Specifies the server URL.</span></span> <span data-ttu-id="45a78-124">Obsługiwane adresy URL dla `https://www.nuget.org` `https://www.nuget.org/api/v3`nuget.org `https://www.nuget.org/api/v2/package`obejmują , i .</span><span class="sxs-lookup"><span data-stu-id="45a78-124">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="45a78-125">W przypadku prywatnych źródeł danych należy zastąpić `%hostname%/api/v3`nazwę hosta (na przykład).</span><span class="sxs-lookup"><span data-stu-id="45a78-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

## <a name="examples"></a><span data-ttu-id="45a78-126">Przykłady</span><span class="sxs-lookup"><span data-stu-id="45a78-126">Examples</span></span>

* <span data-ttu-id="45a78-127">Usuwa wersję 1.0 `Microsoft.AspNetCore.Mvc`pakietu:</span><span class="sxs-lookup"><span data-stu-id="45a78-127">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="45a78-128">Usuwa wersję 1.0 `Microsoft.AspNetCore.Mvc`pakietu, nie monitując użytkownika o poświadczenia lub inne dane wejściowe:</span><span class="sxs-lookup"><span data-stu-id="45a78-128">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
