---
title: polecenie Usuń nuget DotNet
description: Polecenia dotnet-nuget-delete Usuwa lub unlists pakietu z serwera.
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: 827d295d7a52b6c9c82adbcf3d25281bd1cc98fd
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168315"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="35602-103">Usuń nuget DotNet</span><span class="sxs-lookup"><span data-stu-id="35602-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="35602-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="35602-104">Name</span></span>

<span data-ttu-id="35602-105">`dotnet nuget delete` -Usuwa lub unlists pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="35602-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="35602-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="35602-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="35602-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="35602-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="35602-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="35602-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="35602-109">Opis</span><span class="sxs-lookup"><span data-stu-id="35602-109">Description</span></span>

<span data-ttu-id="35602-110">`dotnet nuget delete` Polecenie usuwa lub unlists pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="35602-110">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="35602-111">Aby uzyskać [nuget.org](https://www.nuget.org/), akcja jest wyrejestrowanie pakietu.</span><span class="sxs-lookup"><span data-stu-id="35602-111">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="35602-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="35602-112">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="35602-113">Nazwa/identyfikator pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="35602-113">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="35602-114">Wersja pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="35602-114">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="35602-115">Opcje</span><span class="sxs-lookup"><span data-stu-id="35602-115">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="35602-116">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="35602-116">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`--force-english-output`**

  <span data-ttu-id="35602-117">Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.</span><span class="sxs-lookup"><span data-stu-id="35602-117">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="35602-118">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="35602-118">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="35602-119">Umożliwia polecenie, aby zablokować i wymaga ręcznej akcji dla operacji, takich jak uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="35602-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="35602-120">Opcja dostępna od zestawu SDK programu .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="35602-120">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="35602-121">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="35602-121">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="35602-122">Nie dołącza "interfejsu api w wersji 2/pakiet" adres URL źródła.</span><span class="sxs-lookup"><span data-stu-id="35602-122">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="35602-123">Opcja dostępna od zestawu SDK programu .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="35602-123">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="35602-124">Nie monit o podanie danych wejściowych użytkownika lub potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="35602-124">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="35602-125">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="35602-125">Specifies the server URL.</span></span> <span data-ttu-id="35602-126">Obsługiwane adresów URL dla dołączania nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, i `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="35602-126">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="35602-127">Dla prywatnych źródeł danych, zastąp nazwę hosta (na przykład `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="35602-127">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="35602-128">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="35602-128">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`--force-english-output`**

  <span data-ttu-id="35602-129">Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.</span><span class="sxs-lookup"><span data-stu-id="35602-129">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="35602-130">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="35602-130">Prints out a short help for the command.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="35602-131">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="35602-131">The API key for the server.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="35602-132">Nie monit o podanie danych wejściowych użytkownika lub potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="35602-132">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="35602-133">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="35602-133">Specifies the server URL.</span></span> <span data-ttu-id="35602-134">Obsługiwane adresów URL dla dołączania nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, i `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="35602-134">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="35602-135">Dla prywatnych źródeł danych, zastąp nazwę hosta (na przykład `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="35602-135">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

---

## <a name="examples"></a><span data-ttu-id="35602-136">Przykłady</span><span class="sxs-lookup"><span data-stu-id="35602-136">Examples</span></span>

* <span data-ttu-id="35602-137">Usuwa pakiet w wersji 1.0 dla `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="35602-137">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="35602-138">Usuwa pakiet w wersji 1.0 dla `Microsoft.AspNetCore.Mvc`, nie monitowania użytkownika o poświadczenia lub inne dane wejściowe:</span><span class="sxs-lookup"><span data-stu-id="35602-138">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```