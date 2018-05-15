---
title: polecenie - .NET Core interfejsu wiersza polecenia delete DotNet nuget
description: Polecenie dotnet-nuget-delete Usuwa lub unlists pakietu z serwera.
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: 639ade54bfed5eb2de89bdb3b7f451393b4be187
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="3b2f0-103">Usuń nuget DotNet</span><span class="sxs-lookup"><span data-stu-id="3b2f0-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="3b2f0-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3b2f0-104">Name</span></span>

<span data-ttu-id="3b2f0-105">`dotnet nuget delete` — Usuwa lub unlists pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="3b2f0-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3b2f0-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="3b2f0-106">Synopsis</span></span>

`dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="3b2f0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3b2f0-107">Description</span></span>

<span data-ttu-id="3b2f0-108">`dotnet nuget delete` Polecenie usuwa lub unlists pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="3b2f0-108">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="3b2f0-109">Aby uzyskać [nuget.org](https://www.nuget.org/), akcja jest unlist pakietu.</span><span class="sxs-lookup"><span data-stu-id="3b2f0-109">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="3b2f0-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3b2f0-110">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="3b2f0-111">Pakiet do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="3b2f0-111">Package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="3b2f0-112">Wersja pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="3b2f0-112">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="3b2f0-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="3b2f0-113">Options</span></span>

`-h|--help`

<span data-ttu-id="3b2f0-114">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="3b2f0-114">Prints out a short help for the command.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="3b2f0-115">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="3b2f0-115">Specifies the server URL.</span></span> <span data-ttu-id="3b2f0-116">Obsługiwane adresy URL to nuget.org `http://www.nuget.org`, `http://www.nuget.org/api/v3`, i `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="3b2f0-116">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="3b2f0-117">Dla prywatnych źródeł danych, zastąp nazwą hosta (na przykład `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="3b2f0-117">For private feeds, substitute the host name (for example, `%hostname%/api/v3`).</span></span>

`--non-interactive`

<span data-ttu-id="3b2f0-118">Nie monituj o dane wejściowe użytkownika lub potwierdzeń.</span><span class="sxs-lookup"><span data-stu-id="3b2f0-118">Doesn't prompt for user input or confirmations.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="3b2f0-119">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="3b2f0-119">The API key for the server.</span></span>

`--force-english-output`

<span data-ttu-id="3b2f0-120">Wiersza polecenia wymusza dane wyjściowe w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="3b2f0-120">Forces command-line output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="3b2f0-121">Przykłady</span><span class="sxs-lookup"><span data-stu-id="3b2f0-121">Examples</span></span>

<span data-ttu-id="3b2f0-122">Usuwa pakiet w wersji 1.0 dla `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="3b2f0-122">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0` 

<span data-ttu-id="3b2f0-123">Usuwa pakiet w wersji 1.0 dla `Microsoft.AspNetCore.Mvc`, nie monitowanie użytkownika o poświadczenia lub innych danych wejściowych:</span><span class="sxs-lookup"><span data-stu-id="3b2f0-123">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`