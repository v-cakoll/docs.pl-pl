---
title: polecenie - .NET Core interfejsu wiersza polecenia delete DotNet nuget
description: Polecenie dotnet-nuget-delete Usuwa lub unlists pakietu z serwera.
author: karann-msft
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: a56ddaba72f8e1a76db810231e64993c657e908e
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34697245"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="5fc9e-103">Usuń nuget DotNet</span><span class="sxs-lookup"><span data-stu-id="5fc9e-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="5fc9e-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="5fc9e-104">Name</span></span>

<span data-ttu-id="5fc9e-105">`dotnet nuget delete` — Usuwa lub unlists pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5fc9e-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="5fc9e-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5fc9e-107">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="5fc9e-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5fc9e-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5fc9e-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5fc9e-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5fc9e-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="5fc9e-110">Opis</span><span class="sxs-lookup"><span data-stu-id="5fc9e-110">Description</span></span>

<span data-ttu-id="5fc9e-111">`dotnet nuget delete` Polecenie usuwa lub unlists pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-111">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="5fc9e-112">Aby uzyskać [nuget.org](https://www.nuget.org/), akcja jest unlist pakietu.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-112">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="5fc9e-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5fc9e-113">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="5fc9e-114">Nazwa/identyfikator pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-114">Name/ID of the package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="5fc9e-115">Wersja pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-115">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="5fc9e-116">Opcje</span><span class="sxs-lookup"><span data-stu-id="5fc9e-116">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5fc9e-117">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="5fc9e-117">.NET Core 2.1</span></span>](#tab/netcore21)

`--force-english-output`

 <span data-ttu-id="5fc9e-118">Wymusza aplikacji do uruchamiania przy użyciu opartego na język angielski, niezmienna kultura.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-118">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="5fc9e-119">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-119">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="5fc9e-120">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-120">The API key for the server.</span></span>

<span data-ttu-id="5fc9e-121">` --no-service-endpoint` Nie dołącza "interfejsu api w wersji 2/packages" adres URL źródła.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-121">` --no-service-endpoint` Doesn't append "api/v2/packages" to the source URL.</span></span>

`--non-interactive`

<span data-ttu-id="5fc9e-122">Nie monituj o dane wejściowe użytkownika lub potwierdzeń.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-122">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="5fc9e-123">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-123">Specifies the server URL.</span></span> <span data-ttu-id="5fc9e-124">Obsługiwane adresy URL to nuget.org `http://www.nuget.org`, `http://www.nuget.org/api/v3`, i `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-124">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="5fc9e-125">Dla prywatnych źródeł danych, zastąp nazwą hosta (na przykład `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="5fc9e-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5fc9e-126">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5fc9e-126">.NET Core 2.0</span></span>](#tab/netcore20)

`--force-english-output`

 <span data-ttu-id="5fc9e-127">Wymusza aplikacji do uruchamiania przy użyciu opartego na język angielski, niezmienna kultura.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-127">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="5fc9e-128">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-128">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="5fc9e-129">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-129">The API key for the server.</span></span>

`--non-interactive`

<span data-ttu-id="5fc9e-130">Nie monituj o dane wejściowe użytkownika lub potwierdzeń.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-130">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="5fc9e-131">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-131">Specifies the server URL.</span></span> <span data-ttu-id="5fc9e-132">Obsługiwane adresy URL to nuget.org `http://www.nuget.org`, `http://www.nuget.org/api/v3`, i `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-132">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="5fc9e-133">Dla prywatnych źródeł danych, zastąp nazwą hosta (na przykład `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="5fc9e-133">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5fc9e-134">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5fc9e-134">.NET Core 1.x</span></span>](#tab/netcore1x)

`--force-english-output`

 <span data-ttu-id="5fc9e-135">Wymusza aplikacji do uruchamiania przy użyciu opartego na język angielski, niezmienna kultura.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-135">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="5fc9e-136">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-136">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="5fc9e-137">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-137">The API key for the server.</span></span>

`--non-interactive`

<span data-ttu-id="5fc9e-138">Nie monituj o dane wejściowe użytkownika lub potwierdzeń.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-138">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="5fc9e-139">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-139">Specifies the server URL.</span></span> <span data-ttu-id="5fc9e-140">Obsługiwane adresy URL to nuget.org `http://www.nuget.org`, `http://www.nuget.org/api/v3`, i `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-140">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="5fc9e-141">Dla prywatnych źródeł danych, zastąp nazwą hosta (na przykład `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="5fc9e-141">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

---

## <a name="examples"></a><span data-ttu-id="5fc9e-142">Przykłady</span><span class="sxs-lookup"><span data-stu-id="5fc9e-142">Examples</span></span>

<span data-ttu-id="5fc9e-143">Usuwa pakiet w wersji 1.0 dla `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="5fc9e-143">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0`

<span data-ttu-id="5fc9e-144">Usuwa pakiet w wersji 1.0 dla `Microsoft.AspNetCore.Mvc`, nie monitowanie użytkownika o poświadczenia lub innych danych wejściowych:</span><span class="sxs-lookup"><span data-stu-id="5fc9e-144">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`