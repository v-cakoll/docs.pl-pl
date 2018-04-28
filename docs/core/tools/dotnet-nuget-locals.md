---
title: polecenie zmiennych lokalnych nuget DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie zmiennych lokalnych nuget dotnet czyści lub wyświetla ich listę zasobów lokalnych NuGet np. pamięci podręcznej żądania http, tymczasowego pamięci podręcznej lub folderu packages globalne dla komputera.
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 1dfa50ff0971a82b3f6aafd86492fd57d8cf6a82
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="899ea-103">Zmienne lokalne nuget DotNet</span><span class="sxs-lookup"><span data-stu-id="899ea-103">dotnet nuget locals</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="899ea-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="899ea-104">Name</span></span>

<span data-ttu-id="899ea-105">`dotnet nuget locals` — Usuwa lub wyświetla ich listę zasobów lokalnych NuGet.</span><span class="sxs-lookup"><span data-stu-id="899ea-105">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="899ea-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="899ea-106">Synopsis</span></span>

`dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="899ea-107">Opis</span><span class="sxs-lookup"><span data-stu-id="899ea-107">Description</span></span>

<span data-ttu-id="899ea-108">`dotnet nuget locals` Polecenie czyści lub wyświetla ich listę zasobów lokalnych NuGet w pamięci podręcznej żądania http, tymczasowego pamięci podręcznej lub folderu packages globalne dla komputera.</span><span class="sxs-lookup"><span data-stu-id="899ea-108">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="899ea-109">Argumenty</span><span class="sxs-lookup"><span data-stu-id="899ea-109">Arguments</span></span>

`CACHE_LOCATION`

<span data-ttu-id="899ea-110">Jedna z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="899ea-110">One of the following values:</span></span>

* <span data-ttu-id="899ea-111">`all` — Wskazuje, że określona operacja jest stosowane do wszystkich typów pamięci podręcznej: pamięci podręcznej żądania http, pakiety globalnej pamięci podręcznej i tymczasowego pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="899ea-111">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
* <span data-ttu-id="899ea-112">`http-cache` — Wskazuje, że określona operacja jest stosowane tylko do pamięci podręcznej żądania http.</span><span class="sxs-lookup"><span data-stu-id="899ea-112">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="899ea-113">Nie dotyczy innych lokalizacji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="899ea-113">The other cache locations are not affected.</span></span>
* <span data-ttu-id="899ea-114">`global-packages` — Wskazuje, że określona operacja jest stosowane tylko do pakietów globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="899ea-114">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="899ea-115">Nie dotyczy innych lokalizacji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="899ea-115">The other cache locations are not affected.</span></span>
* <span data-ttu-id="899ea-116">`temp` — Wskazuje, że określona operacja jest stosowane tylko do tymczasowego pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="899ea-116">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="899ea-117">Nie dotyczy innych lokalizacji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="899ea-117">The other cache locations are not affected.</span></span>

## <a name="options"></a><span data-ttu-id="899ea-118">Opcje</span><span class="sxs-lookup"><span data-stu-id="899ea-118">Options</span></span>

`-h|--help`

<span data-ttu-id="899ea-119">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="899ea-119">Prints out a short help for the command.</span></span>

`-c|--clear`

<span data-ttu-id="899ea-120">Usuń zaznaczenie opcji wykonuje operację wyczyść na typ określony w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="899ea-120">The clear option performs a clear operation on the specified cache type.</span></span> <span data-ttu-id="899ea-121">Zawartość pamięci podręcznej katalogów jest rekursywnie usunięte.</span><span class="sxs-lookup"><span data-stu-id="899ea-121">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="899ea-122">Wykonywanie użytkownika/grupy musi mieć uprawnienia do plików w katalogach pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="899ea-122">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="899ea-123">W przeciwnym razie zostanie wyświetlony błąd wskazujący plików/folderów, które nie zostały wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="899ea-123">If not, an error is displayed indicating the files/folders which were not cleared.</span></span>

`-l|--list`

<span data-ttu-id="899ea-124">Opcja lista służy do wyświetlania lokalizacji pamięci podręcznej określonego typu.</span><span class="sxs-lookup"><span data-stu-id="899ea-124">The list option is used to display the location of the specified cache type.</span></span> 

`--force-english-output`

<span data-ttu-id="899ea-125">Wiersza polecenia wymusza dane wyjściowe w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="899ea-125">Forces command-line output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="899ea-126">Przykłady</span><span class="sxs-lookup"><span data-stu-id="899ea-126">Examples</span></span>

<span data-ttu-id="899ea-127">Wyświetla ścieżki wszystkich katalogów lokalnej pamięci podręcznej (katalog pamięci podręcznej http pakiety globalny katalog pamięci podręcznej i katalog tymczasowy pamięci podręcznej):</span><span class="sxs-lookup"><span data-stu-id="899ea-127">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals –l all`

<span data-ttu-id="899ea-128">Wyświetla ścieżkę dla katalogu lokalnej pamięci podręcznej http:</span><span class="sxs-lookup"><span data-stu-id="899ea-128">Displays the path for the local http-cache directory:</span></span>

`dotnet nuget locals --list http-cache`

<span data-ttu-id="899ea-129">Czyści wszystkie pliki ze wszystkich katalogów lokalnej pamięci podręcznej (katalog pamięci podręcznej http pakiety globalny katalog pamięci podręcznej i katalog tymczasowy pamięci podręcznej):</span><span class="sxs-lookup"><span data-stu-id="899ea-129">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals --clear all`

<span data-ttu-id="899ea-130">Czyści wszystkie pliki w katalogu pamięci podręcznej lokalnego globalnego pakiety:</span><span class="sxs-lookup"><span data-stu-id="899ea-130">Clears all files in local global-packages cache directory:</span></span>

`dotnet nuget locals -c global-packages`

<span data-ttu-id="899ea-131">Czyści wszystkie pliki w lokalnej pamięci podręcznej tymczasowego katalogu:</span><span class="sxs-lookup"><span data-stu-id="899ea-131">Clears all files in local temporary cache directory:</span></span>

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a><span data-ttu-id="899ea-132">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="899ea-132">Troubleshooting</span></span>

<span data-ttu-id="899ea-133">Aby uzyskać informacje dotyczące typowych problemów i błędów podczas korzystania z `dotnet nuget locals` polecenia, zobacz [Zarządzanie pamięci podręcznej NuGet](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="899ea-133">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>