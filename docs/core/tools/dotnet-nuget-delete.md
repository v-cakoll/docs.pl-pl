---
title: polecenie Usuń nuget DotNet
description: Polecenia dotnet-nuget-delete Usuwa lub unlists pakietu z serwera.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 0b2ba64b70bae5e06f213457e30fedeca26a9819
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539250"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="f92ed-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="f92ed-103">dotnet nuget delete</span></span>

<span data-ttu-id="f92ed-104">**Ten temat dotyczy: ✓** platformy .NET Core SDK w wersji 1.x i nowszymi wersjami</span><span class="sxs-lookup"><span data-stu-id="f92ed-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="f92ed-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f92ed-105">Name</span></span>

<span data-ttu-id="f92ed-106">`dotnet nuget delete` -Usuwa lub unlists pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="f92ed-106">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f92ed-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="f92ed-107">Synopsis</span></span>

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a><span data-ttu-id="f92ed-108">Opis</span><span class="sxs-lookup"><span data-stu-id="f92ed-108">Description</span></span>

<span data-ttu-id="f92ed-109">`dotnet nuget delete` Polecenie usuwa lub unlists pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="f92ed-109">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="f92ed-110">Aby uzyskać [nuget.org](https://www.nuget.org/), akcja jest wyrejestrowanie pakietu.</span><span class="sxs-lookup"><span data-stu-id="f92ed-110">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="f92ed-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f92ed-111">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="f92ed-112">Nazwa/identyfikator pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="f92ed-112">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="f92ed-113">Wersja pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="f92ed-113">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="f92ed-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="f92ed-114">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="f92ed-115">Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.</span><span class="sxs-lookup"><span data-stu-id="f92ed-115">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="f92ed-116">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="f92ed-116">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="f92ed-117">Umożliwia polecenie, aby zablokować i wymaga ręcznej akcji dla operacji, takich jak uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="f92ed-117">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="f92ed-118">Opcja dostępna od zestawu SDK programu .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="f92ed-118">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="f92ed-119">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="f92ed-119">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="f92ed-120">Nie dołącza "interfejsu api w wersji 2/pakiet" adres URL źródła.</span><span class="sxs-lookup"><span data-stu-id="f92ed-120">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="f92ed-121">Opcja dostępna od zestawu SDK programu .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="f92ed-121">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="f92ed-122">Nie monit o podanie danych wejściowych użytkownika lub potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="f92ed-122">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="f92ed-123">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="f92ed-123">Specifies the server URL.</span></span> <span data-ttu-id="f92ed-124">Obsługiwane adresów URL dla dołączania nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, i `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="f92ed-124">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="f92ed-125">Dla prywatnych źródeł danych, zastąp nazwę hosta (na przykład `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="f92ed-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

## <a name="examples"></a><span data-ttu-id="f92ed-126">Przykłady</span><span class="sxs-lookup"><span data-stu-id="f92ed-126">Examples</span></span>

* <span data-ttu-id="f92ed-127">Usuwa pakiet w wersji 1.0 dla `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="f92ed-127">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="f92ed-128">Usuwa pakiet w wersji 1.0 dla `Microsoft.AspNetCore.Mvc`, nie monitowania użytkownika o poświadczenia lub inne dane wejściowe:</span><span class="sxs-lookup"><span data-stu-id="f92ed-128">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
