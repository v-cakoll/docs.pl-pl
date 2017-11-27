---
title: polecenie - .NET Core interfejsu wiersza polecenia delete DotNet nuget
description: Polecenie dotnet-nuget-delete Usuwa lub unlists pakietu z serwera.
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 65fe52f07ed823b4f7518c5b1f2da1f7a61b0371
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="f9ef1-103">Usuń nuget DotNet</span><span class="sxs-lookup"><span data-stu-id="f9ef1-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="f9ef1-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f9ef1-104">Name</span></span>

<span data-ttu-id="f9ef1-105">`dotnet nuget delete`— Usuwa lub unlists pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="f9ef1-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f9ef1-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="f9ef1-106">Synopsis</span></span>

`dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="f9ef1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f9ef1-107">Description</span></span>

<span data-ttu-id="f9ef1-108">`dotnet nuget delete` Polecenie usuwa lub unlists pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="f9ef1-108">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="f9ef1-109">Aby uzyskać [nuget.org](https://www.nuget.org/), akcja jest unlist pakietu.</span><span class="sxs-lookup"><span data-stu-id="f9ef1-109">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="f9ef1-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f9ef1-110">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="f9ef1-111">Pakiet do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="f9ef1-111">Package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="f9ef1-112">Wersja pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="f9ef1-112">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="f9ef1-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="f9ef1-113">Options</span></span>

`-h|--help`

<span data-ttu-id="f9ef1-114">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="f9ef1-114">Prints out a short help for the command.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="f9ef1-115">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="f9ef1-115">Specifies the server URL.</span></span> <span data-ttu-id="f9ef1-116">Obsługiwane adresy URL to nuget.org `http://www.nuget.org`, `http://www.nuget.org/api/v3`, i `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="f9ef1-116">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="f9ef1-117">Dla prywatnych źródeł danych, zastąp nazwą hosta (na przykład `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="f9ef1-117">For private feeds, substitute the host name (for example, `%hostname%/api/v3`).</span></span>

`--non-interactive`

<span data-ttu-id="f9ef1-118">Nie monituj o dane wejściowe użytkownika lub potwierdzeń.</span><span class="sxs-lookup"><span data-stu-id="f9ef1-118">Doesn't prompt for user input or confirmations.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="f9ef1-119">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="f9ef1-119">The API key for the server.</span></span>

`--force-english-output`

<span data-ttu-id="f9ef1-120">Wiersza polecenia wymusza dane wyjściowe w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="f9ef1-120">Forces command-line output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="f9ef1-121">Przykłady</span><span class="sxs-lookup"><span data-stu-id="f9ef1-121">Examples</span></span>

<span data-ttu-id="f9ef1-122">Usuwa pakiet w wersji 1.0 dla `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="f9ef1-122">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0` 

<span data-ttu-id="f9ef1-123">Usuwa pakiet w wersji 1.0 dla `Microsoft.AspNetCore.Mvc`, nie monitowanie użytkownika o poświadczenia lub innych danych wejściowych:</span><span class="sxs-lookup"><span data-stu-id="f9ef1-123">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`