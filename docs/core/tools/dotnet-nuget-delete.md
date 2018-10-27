---
title: DotNet nuget Usuwanie polecenia — interfejs wiersza polecenia platformy .NET Core
description: Polecenia dotnet-nuget-delete Usuwa lub unlists pakietu z serwera.
author: karann-msft
ms.author: mairaw
ms.date: 06/01/2018
ms.openlocfilehash: f4aa027a465c4adea1de13853063d03e8e295411
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180884"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="5b12b-103">Usuń nuget DotNet</span><span class="sxs-lookup"><span data-stu-id="5b12b-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="5b12b-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="5b12b-104">Name</span></span>

<span data-ttu-id="5b12b-105">`dotnet nuget delete` -Usuwa lub unlists pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="5b12b-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5b12b-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="5b12b-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5b12b-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="5b12b-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5b12b-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5b12b-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5b12b-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5b12b-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="5b12b-110">Opis</span><span class="sxs-lookup"><span data-stu-id="5b12b-110">Description</span></span>

<span data-ttu-id="5b12b-111">`dotnet nuget delete` Polecenie usuwa lub unlists pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="5b12b-111">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="5b12b-112">Aby uzyskać [nuget.org](https://www.nuget.org/), akcja jest wyrejestrowanie pakietu.</span><span class="sxs-lookup"><span data-stu-id="5b12b-112">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="5b12b-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5b12b-113">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="5b12b-114">Nazwa/identyfikator pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="5b12b-114">Name/ID of the package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="5b12b-115">Wersja pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="5b12b-115">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="5b12b-116">Opcje</span><span class="sxs-lookup"><span data-stu-id="5b12b-116">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5b12b-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="5b12b-117">.NET Core 2.1</span></span>](#tab/netcore21)

`--force-english-output`

 <span data-ttu-id="5b12b-118">Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.</span><span class="sxs-lookup"><span data-stu-id="5b12b-118">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="5b12b-119">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="5b12b-119">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="5b12b-120">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="5b12b-120">The API key for the server.</span></span>

<span data-ttu-id="5b12b-121">`--no-service-endpoint` Nie dołącza "interfejsu api w wersji 2/pakiet" adres URL źródła.</span><span class="sxs-lookup"><span data-stu-id="5b12b-121">`--no-service-endpoint` Doesn't append "api/v2/package" to the source URL.</span></span>

`--non-interactive`

<span data-ttu-id="5b12b-122">Nie monit o podanie danych wejściowych użytkownika lub potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="5b12b-122">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="5b12b-123">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="5b12b-123">Specifies the server URL.</span></span> <span data-ttu-id="5b12b-124">Obsługiwane adresów URL dla dołączania nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, i `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="5b12b-124">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="5b12b-125">Dla prywatnych źródeł danych, zastąp nazwę hosta (na przykład `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="5b12b-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5b12b-126">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5b12b-126">.NET Core 2.0</span></span>](#tab/netcore20)

`--force-english-output`

 <span data-ttu-id="5b12b-127">Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.</span><span class="sxs-lookup"><span data-stu-id="5b12b-127">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="5b12b-128">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="5b12b-128">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="5b12b-129">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="5b12b-129">The API key for the server.</span></span>

`--non-interactive`

<span data-ttu-id="5b12b-130">Nie monit o podanie danych wejściowych użytkownika lub potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="5b12b-130">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="5b12b-131">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="5b12b-131">Specifies the server URL.</span></span> <span data-ttu-id="5b12b-132">Obsługiwane adresów URL dla dołączania nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, i `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="5b12b-132">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="5b12b-133">Dla prywatnych źródeł danych, zastąp nazwę hosta (na przykład `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="5b12b-133">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5b12b-134">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5b12b-134">.NET Core 1.x</span></span>](#tab/netcore1x)

`--force-english-output`

 <span data-ttu-id="5b12b-135">Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.</span><span class="sxs-lookup"><span data-stu-id="5b12b-135">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="5b12b-136">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="5b12b-136">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="5b12b-137">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="5b12b-137">The API key for the server.</span></span>

`--non-interactive`

<span data-ttu-id="5b12b-138">Nie monit o podanie danych wejściowych użytkownika lub potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="5b12b-138">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="5b12b-139">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="5b12b-139">Specifies the server URL.</span></span> <span data-ttu-id="5b12b-140">Obsługiwane adresów URL dla dołączania nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, i `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="5b12b-140">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="5b12b-141">Dla prywatnych źródeł danych, zastąp nazwę hosta (na przykład `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="5b12b-141">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

---

## <a name="examples"></a><span data-ttu-id="5b12b-142">Przykłady</span><span class="sxs-lookup"><span data-stu-id="5b12b-142">Examples</span></span>

<span data-ttu-id="5b12b-143">Usuwa pakiet w wersji 1.0 dla `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="5b12b-143">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0`

<span data-ttu-id="5b12b-144">Usuwa pakiet w wersji 1.0 dla `Microsoft.AspNetCore.Mvc`, nie monitowania użytkownika o poświadczenia lub inne dane wejściowe:</span><span class="sxs-lookup"><span data-stu-id="5b12b-144">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`
