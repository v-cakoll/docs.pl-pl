---
title: polecenie locale dla pakietów NuGet dotnet
description: Polecenie locale polecenia NuGet programu dotnet czyści lub wyświetla listę lokalnych zasobów NuGet, takich jak pamięć podręczna żądań HTTP, tymczasowa pamięć podręczna lub folder pakietów globalnych dla całego komputera.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 3fdd7d946b08b4c18cfaeb65013de259b927a7fa
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503683"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="03d16-103">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="03d16-103">dotnet nuget locals</span></span>

<span data-ttu-id="03d16-104">**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="03d16-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="03d16-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="03d16-105">Name</span></span>

<span data-ttu-id="03d16-106">`dotnet nuget locals` — czyści lub wyświetla lokalne zasoby NuGet.</span><span class="sxs-lookup"><span data-stu-id="03d16-106">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="03d16-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="03d16-107">Synopsis</span></span>

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="03d16-108">Opis</span><span class="sxs-lookup"><span data-stu-id="03d16-108">Description</span></span>

<span data-ttu-id="03d16-109">Polecenie `dotnet nuget locals` czyści lub wyświetla listę lokalnych zasobów NuGet w pamięci podręcznej żądania HTTP, tymczasowej pamięci podręcznej lub na całej maszynie.</span><span class="sxs-lookup"><span data-stu-id="03d16-109">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="03d16-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="03d16-110">Arguments</span></span>

- **`CACHE_LOCATION`**

  <span data-ttu-id="03d16-111">Lokalizacja pamięci podręcznej do wyświetlenia lub wyczyszczenia.</span><span class="sxs-lookup"><span data-stu-id="03d16-111">The cache location to list or clear.</span></span> <span data-ttu-id="03d16-112">Akceptuje jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="03d16-112">It accepts one of the following values:</span></span>

  * <span data-ttu-id="03d16-113">`all` — wskazuje, że określona operacja jest stosowana do wszystkich typów pamięci podręcznej: pamięć podręczna żądań HTTP, pamięć podręczna pakietów globalnych i tymczasowa pamięć podręczna.</span><span class="sxs-lookup"><span data-stu-id="03d16-113">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
  * <span data-ttu-id="03d16-114">`http-cache` — wskazuje, że określona operacja jest stosowana tylko do pamięci podręcznej żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="03d16-114">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="03d16-115">Nie ma to wpływu na inne lokalizacje pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="03d16-115">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="03d16-116">`global-packages` — wskazuje, że określona operacja jest stosowana tylko do globalnej pamięci podręcznej pakietów.</span><span class="sxs-lookup"><span data-stu-id="03d16-116">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="03d16-117">Nie ma to wpływu na inne lokalizacje pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="03d16-117">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="03d16-118">`temp` — wskazuje, że określona operacja jest stosowana tylko do tymczasowej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="03d16-118">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="03d16-119">Nie ma to wpływu na inne lokalizacje pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="03d16-119">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="03d16-120">Opcje</span><span class="sxs-lookup"><span data-stu-id="03d16-120">Options</span></span>

- **`--force-english-output`**

  <span data-ttu-id="03d16-121">Wymusza uruchomienie aplikacji przy użyciu niezmiennej, opartej na języku angielskim kultury.</span><span class="sxs-lookup"><span data-stu-id="03d16-121">Forces the application to run using an invariant, English-based culture.</span></span>

- **`-h|--help`**

  <span data-ttu-id="03d16-122">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="03d16-122">Prints out a short help for the command.</span></span>

- **`-c|--clear`**

  <span data-ttu-id="03d16-123">Opcja Clear wykonuje operację czyszczenia dla określonego typu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="03d16-123">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="03d16-124">Zawartość katalogów pamięci podręcznej jest usuwana rekursywnie.</span><span class="sxs-lookup"><span data-stu-id="03d16-124">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="03d16-125">Wykonywany użytkownik/grupa musi mieć uprawnienia do plików w katalogach pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="03d16-125">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="03d16-126">W przeciwnym razie zostanie wyświetlony komunikat o błędzie wskazujący pliki/foldery, które nie zostały wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="03d16-126">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

- **`-l|--list`**

  <span data-ttu-id="03d16-127">Opcja Lista służy do wyświetlania lokalizacji określonego typu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="03d16-127">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="03d16-128">Przykłady</span><span class="sxs-lookup"><span data-stu-id="03d16-128">Examples</span></span>

- <span data-ttu-id="03d16-129">Wyświetla ścieżki wszystkich lokalnych katalogów pamięci podręcznej (Katalog pamięci podręcznej http, Katalog pamięci podręcznej pakietów globalnych i tymczasowy katalog pamięci podręcznej):</span><span class="sxs-lookup"><span data-stu-id="03d16-129">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals all –l
  ```

- <span data-ttu-id="03d16-130">Wyświetla ścieżkę dla lokalnego katalogu pamięci podręcznej http:</span><span class="sxs-lookup"><span data-stu-id="03d16-130">Displays the path for the local http-cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals http-cache --list
  ```

- <span data-ttu-id="03d16-131">Czyści wszystkie pliki z katalogów lokalnej pamięci podręcznej (Katalog pamięci podręcznej http, Katalog pamięci podręcznej pakietów globalnych i tymczasowy katalog pamięci podręcznej):</span><span class="sxs-lookup"><span data-stu-id="03d16-131">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals all --clear
  ```

- <span data-ttu-id="03d16-132">Czyści wszystkie pliki w lokalnym katalogu globalnym pakietów pamięci podręcznej:</span><span class="sxs-lookup"><span data-stu-id="03d16-132">Clears all files in local global-packages cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals global-packages -c
  ```

- <span data-ttu-id="03d16-133">Czyści wszystkie pliki w lokalnym katalogu tymczasowej pamięci podręcznej:</span><span class="sxs-lookup"><span data-stu-id="03d16-133">Clears all files in local temporary cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals temp -c
  ```

## <a name="troubleshooting"></a><span data-ttu-id="03d16-134">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="03d16-134">Troubleshooting</span></span>

<span data-ttu-id="03d16-135">Informacje o typowych problemach i błędach przy użyciu polecenia `dotnet nuget locals` można znaleźć w temacie [Zarządzanie pamięcią podręczną NuGet](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="03d16-135">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>
