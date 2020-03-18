---
title: dotnet nuget locals polecenie
description: Polecenie dotnet nuget locals czyści lub wyświetla lokalne zasoby NuGet, takie jak pamięć podręczna żądań http, tymczasowa pamięć podręczna lub folder pakietów globalnych dla całego komputera.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 3fdd7d946b08b4c18cfaeb65013de259b927a7fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503683"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="cb3c6-103">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="cb3c6-103">dotnet nuget locals</span></span>

<span data-ttu-id="cb3c6-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="cb3c6-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="cb3c6-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cb3c6-105">Name</span></span>

<span data-ttu-id="cb3c6-106">`dotnet nuget locals`- Czyści lub wyświetla lokalne zasoby NuGet.</span><span class="sxs-lookup"><span data-stu-id="cb3c6-106">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cb3c6-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="cb3c6-107">Synopsis</span></span>

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="cb3c6-108">Opis</span><span class="sxs-lookup"><span data-stu-id="cb3c6-108">Description</span></span>

<span data-ttu-id="cb3c6-109">Polecenie `dotnet nuget locals` czyści lub wyświetla lokalne zasoby NuGet w pamięci podręcznej żądań http, tymczasowej pamięci podręcznej lub folderze pakietów globalnych dla całego komputera.</span><span class="sxs-lookup"><span data-stu-id="cb3c6-109">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="cb3c6-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cb3c6-110">Arguments</span></span>

- **`CACHE_LOCATION`**

  <span data-ttu-id="cb3c6-111">Lokalizacja pamięci podręcznej do listy lub wyczyścić.</span><span class="sxs-lookup"><span data-stu-id="cb3c6-111">The cache location to list or clear.</span></span> <span data-ttu-id="cb3c6-112">Akceptuje jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="cb3c6-112">It accepts one of the following values:</span></span>

  * <span data-ttu-id="cb3c6-113">`all`- Wskazuje, że określona operacja jest stosowana do wszystkich typów pamięci podręcznej: pamięci podręcznej żądań http, pamięci podręcznej pakietów globalnych i tymczasowej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="cb3c6-113">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
  * <span data-ttu-id="cb3c6-114">`http-cache`- Wskazuje, że określona operacja jest stosowana tylko do pamięci podręcznej żądań http.</span><span class="sxs-lookup"><span data-stu-id="cb3c6-114">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="cb3c6-115">Nie ma to wpływu na inne lokalizacje pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="cb3c6-115">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="cb3c6-116">`global-packages`- Wskazuje, że określona operacja jest stosowana tylko do pamięci podręcznej pakietów globalnych.</span><span class="sxs-lookup"><span data-stu-id="cb3c6-116">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="cb3c6-117">Nie ma to wpływu na inne lokalizacje pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="cb3c6-117">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="cb3c6-118">`temp`- Wskazuje, że określona operacja jest stosowana tylko do tymczasowej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="cb3c6-118">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="cb3c6-119">Nie ma to wpływu na inne lokalizacje pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="cb3c6-119">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="cb3c6-120">Opcje</span><span class="sxs-lookup"><span data-stu-id="cb3c6-120">Options</span></span>

- **`--force-english-output`**

  <span data-ttu-id="cb3c6-121">Wymusza uruchamianie aplikacji przy użyciu niezmiennej kultury opartej na języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="cb3c6-121">Forces the application to run using an invariant, English-based culture.</span></span>

- **`-h|--help`**

  <span data-ttu-id="cb3c6-122">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="cb3c6-122">Prints out a short help for the command.</span></span>

- **`-c|--clear`**

  <span data-ttu-id="cb3c6-123">Opcja wyczyść wykonuje wyczyść operację na określonym typie pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="cb3c6-123">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="cb3c6-124">Zawartość katalogów pamięci podręcznej są usuwane cyklicznie.</span><span class="sxs-lookup"><span data-stu-id="cb3c6-124">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="cb3c6-125">Wykonujący użytkownik/grupa musi mieć uprawnienia do plików w katalogach pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="cb3c6-125">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="cb3c6-126">Jeśli nie, zostanie wyświetlony błąd wskazujący pliki/foldery, które nie zostały wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="cb3c6-126">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

- **`-l|--list`**

  <span data-ttu-id="cb3c6-127">Opcja listy służy do wyświetlania lokalizacji określonego typu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="cb3c6-127">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="cb3c6-128">Przykłady</span><span class="sxs-lookup"><span data-stu-id="cb3c6-128">Examples</span></span>

- <span data-ttu-id="cb3c6-129">Wyświetla ścieżki wszystkich lokalnych katalogów pamięci podręcznej (katalog pamięci podręcznej http-cache, katalog pamięci podręcznej pakietów globalnych i katalog pamięci podręcznej tymczasowej):</span><span class="sxs-lookup"><span data-stu-id="cb3c6-129">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals all –l
  ```

- <span data-ttu-id="cb3c6-130">Wyświetla ścieżkę dla lokalnego katalogu http-cache:</span><span class="sxs-lookup"><span data-stu-id="cb3c6-130">Displays the path for the local http-cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals http-cache --list
  ```

- <span data-ttu-id="cb3c6-131">Czyści wszystkie pliki ze wszystkich katalogów lokalnej pamięci podręcznej (katalog pamięci podręcznej http-cache, katalog pamięci podręcznej pakietów globalnych i katalog pamięci podręcznej tymczasowej):</span><span class="sxs-lookup"><span data-stu-id="cb3c6-131">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals all --clear
  ```

- <span data-ttu-id="cb3c6-132">Czyści wszystkie pliki w katalogu pamięci podręcznej lokalnych pakietów globalnych:</span><span class="sxs-lookup"><span data-stu-id="cb3c6-132">Clears all files in local global-packages cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals global-packages -c
  ```

- <span data-ttu-id="cb3c6-133">Czyści wszystkie pliki w lokalnym katalogu tymczasowej pamięci podręcznej:</span><span class="sxs-lookup"><span data-stu-id="cb3c6-133">Clears all files in local temporary cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals temp -c
  ```

## <a name="troubleshooting"></a><span data-ttu-id="cb3c6-134">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="cb3c6-134">Troubleshooting</span></span>

<span data-ttu-id="cb3c6-135">Aby uzyskać informacje na temat `dotnet nuget locals` typowych problemów i błędów podczas korzystania z polecenia, zobacz [Zarządzanie pamięcią podręczną NuGet](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="cb3c6-135">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>
