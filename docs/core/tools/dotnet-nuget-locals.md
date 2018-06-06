---
title: polecenie zmiennych lokalnych nuget DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie zmiennych lokalnych nuget dotnet czyści lub wyświetla ich listę zasobów lokalnych NuGet np. pamięci podręcznej żądania http, tymczasowego pamięci podręcznej lub folderu packages globalne dla komputera.
author: karann-msft
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 799acb92d6ab7439e15c23c9f0b7b572c966adda
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696874"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="2e2ef-103">Zmienne lokalne nuget DotNet</span><span class="sxs-lookup"><span data-stu-id="2e2ef-103">dotnet nuget locals</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="2e2ef-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="2e2ef-104">Name</span></span>

<span data-ttu-id="2e2ef-105">`dotnet nuget locals` — Usuwa lub wyświetla ich listę zasobów lokalnych NuGet.</span><span class="sxs-lookup"><span data-stu-id="2e2ef-105">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2e2ef-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="2e2ef-106">Synopsis</span></span>

```
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="2e2ef-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2e2ef-107">Description</span></span>

<span data-ttu-id="2e2ef-108">`dotnet nuget locals` Polecenie czyści lub wyświetla ich listę zasobów lokalnych NuGet w pamięci podręcznej żądania http, tymczasowego pamięci podręcznej lub folderu packages globalne dla komputera.</span><span class="sxs-lookup"><span data-stu-id="2e2ef-108">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="2e2ef-109">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2e2ef-109">Arguments</span></span>

`CACHE_LOCATION`

<span data-ttu-id="2e2ef-110">Lokalizacja pamięci podręcznej listy lub wyczyścić.</span><span class="sxs-lookup"><span data-stu-id="2e2ef-110">The cache location to list or clear.</span></span> <span data-ttu-id="2e2ef-111">Przyjmuje jeden z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="2e2ef-111">It accepts one of the following values:</span></span>

* <span data-ttu-id="2e2ef-112">`all` — Wskazuje, że określona operacja jest stosowane do wszystkich typów pamięci podręcznej: pamięci podręcznej żądania http, pakiety globalnej pamięci podręcznej i tymczasowego pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="2e2ef-112">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
* <span data-ttu-id="2e2ef-113">`http-cache` — Wskazuje, że określona operacja jest stosowane tylko do pamięci podręcznej żądania http.</span><span class="sxs-lookup"><span data-stu-id="2e2ef-113">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="2e2ef-114">Nie ma wpływu na innych lokalizacji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="2e2ef-114">The other cache locations aren't affected.</span></span>
* <span data-ttu-id="2e2ef-115">`global-packages` — Wskazuje, że określona operacja jest stosowane tylko do pakietów globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="2e2ef-115">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="2e2ef-116">Nie ma wpływu na innych lokalizacji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="2e2ef-116">The other cache locations aren't affected.</span></span>
* <span data-ttu-id="2e2ef-117">`temp` — Wskazuje, że określona operacja jest stosowane tylko do tymczasowego pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="2e2ef-117">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="2e2ef-118">Nie ma wpływu na innych lokalizacji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="2e2ef-118">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="2e2ef-119">Opcje</span><span class="sxs-lookup"><span data-stu-id="2e2ef-119">Options</span></span>

`--force-english-output`

<span data-ttu-id="2e2ef-120">Wymusza aplikacji do uruchamiania przy użyciu opartego na język angielski, niezmienna kultura.</span><span class="sxs-lookup"><span data-stu-id="2e2ef-120">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="2e2ef-121">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="2e2ef-121">Prints out a short help for the command.</span></span>

`-c|--clear`

<span data-ttu-id="2e2ef-122">Usuń zaznaczenie opcji wykonuje operację wyczyść na typ określony w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="2e2ef-122">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="2e2ef-123">Zawartość pamięci podręcznej katalogów jest rekursywnie usunięte.</span><span class="sxs-lookup"><span data-stu-id="2e2ef-123">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="2e2ef-124">Wykonywanie użytkownika/grupy musi mieć uprawnienia do plików w katalogach pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="2e2ef-124">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="2e2ef-125">W przeciwnym razie zostanie wyświetlony błąd wskazujący plików/folderów, które nie zostały wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="2e2ef-125">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

`-l|--list`

<span data-ttu-id="2e2ef-126">Opcja lista służy do wyświetlania lokalizacji pamięci podręcznej określonego typu.</span><span class="sxs-lookup"><span data-stu-id="2e2ef-126">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="2e2ef-127">Przykłady</span><span class="sxs-lookup"><span data-stu-id="2e2ef-127">Examples</span></span>

<span data-ttu-id="2e2ef-128">Wyświetla ścieżki wszystkich katalogów lokalnej pamięci podręcznej (katalog pamięci podręcznej http pakiety globalny katalog pamięci podręcznej i katalog tymczasowy pamięci podręcznej):</span><span class="sxs-lookup"><span data-stu-id="2e2ef-128">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals –l all`

<span data-ttu-id="2e2ef-129">Wyświetla ścieżkę dla katalogu lokalnej pamięci podręcznej http:</span><span class="sxs-lookup"><span data-stu-id="2e2ef-129">Displays the path for the local http-cache directory:</span></span>

`dotnet nuget locals --list http-cache`

<span data-ttu-id="2e2ef-130">Czyści wszystkie pliki ze wszystkich katalogów lokalnej pamięci podręcznej (katalog pamięci podręcznej http pakiety globalny katalog pamięci podręcznej i katalog tymczasowy pamięci podręcznej):</span><span class="sxs-lookup"><span data-stu-id="2e2ef-130">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals --clear all`

<span data-ttu-id="2e2ef-131">Czyści wszystkie pliki w katalogu pamięci podręcznej lokalnego globalnego pakiety:</span><span class="sxs-lookup"><span data-stu-id="2e2ef-131">Clears all files in local global-packages cache directory:</span></span>

`dotnet nuget locals -c global-packages`

<span data-ttu-id="2e2ef-132">Czyści wszystkie pliki w lokalnej pamięci podręcznej tymczasowego katalogu:</span><span class="sxs-lookup"><span data-stu-id="2e2ef-132">Clears all files in local temporary cache directory:</span></span>

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a><span data-ttu-id="2e2ef-133">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="2e2ef-133">Troubleshooting</span></span>

<span data-ttu-id="2e2ef-134">Aby uzyskać informacje dotyczące typowych problemów i błędów podczas korzystania z `dotnet nuget locals` polecenia, zobacz [Zarządzanie pamięci podręcznej NuGet](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="2e2ef-134">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>