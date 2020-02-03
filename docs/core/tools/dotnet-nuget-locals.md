---
title: polecenie locale dla pakietów NuGet dotnet
description: Polecenie locale polecenia NuGet programu dotnet czyści lub wyświetla listę lokalnych zasobów NuGet, takich jak pamięć podręczna żądań HTTP, tymczasowa pamięć podręczna lub folder pakietów globalnych dla całego komputera.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: b57c127650555e412af08df6656fb62d75c8ed7c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734083"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="9000a-103">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="9000a-103">dotnet nuget locals</span></span>

<span data-ttu-id="9000a-104">**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 1. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="9000a-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="9000a-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="9000a-105">Name</span></span>

<span data-ttu-id="9000a-106">`dotnet nuget locals` — czyści lub wyświetla lokalne zasoby NuGet.</span><span class="sxs-lookup"><span data-stu-id="9000a-106">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9000a-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="9000a-107">Synopsis</span></span>

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="9000a-108">Opis</span><span class="sxs-lookup"><span data-stu-id="9000a-108">Description</span></span>

<span data-ttu-id="9000a-109">Polecenie `dotnet nuget locals` czyści lub wyświetla listę lokalnych zasobów NuGet w pamięci podręcznej żądania HTTP, tymczasowej pamięci podręcznej lub na całej maszynie.</span><span class="sxs-lookup"><span data-stu-id="9000a-109">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="9000a-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9000a-110">Arguments</span></span>

* **`CACHE_LOCATION`**

  <span data-ttu-id="9000a-111">Lokalizacja pamięci podręcznej do wyświetlenia lub wyczyszczenia.</span><span class="sxs-lookup"><span data-stu-id="9000a-111">The cache location to list or clear.</span></span> <span data-ttu-id="9000a-112">Akceptuje jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="9000a-112">It accepts one of the following values:</span></span>

  * <span data-ttu-id="9000a-113">`all` — wskazuje, że określona operacja jest stosowana do wszystkich typów pamięci podręcznej: pamięć podręczna żądań HTTP, pamięć podręczna pakietów globalnych i tymczasowa pamięć podręczna.</span><span class="sxs-lookup"><span data-stu-id="9000a-113">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
  * <span data-ttu-id="9000a-114">`http-cache` — wskazuje, że określona operacja jest stosowana tylko do pamięci podręcznej żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="9000a-114">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="9000a-115">Nie ma to wpływu na inne lokalizacje pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="9000a-115">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="9000a-116">`global-packages` — wskazuje, że określona operacja jest stosowana tylko do globalnej pamięci podręcznej pakietów.</span><span class="sxs-lookup"><span data-stu-id="9000a-116">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="9000a-117">Nie ma to wpływu na inne lokalizacje pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="9000a-117">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="9000a-118">`temp` — wskazuje, że określona operacja jest stosowana tylko do tymczasowej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="9000a-118">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="9000a-119">Nie ma to wpływu na inne lokalizacje pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="9000a-119">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="9000a-120">Opcje</span><span class="sxs-lookup"><span data-stu-id="9000a-120">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="9000a-121">Wymusza uruchomienie aplikacji przy użyciu niezmiennej, opartej na języku angielskim kultury.</span><span class="sxs-lookup"><span data-stu-id="9000a-121">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="9000a-122">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="9000a-122">Prints out a short help for the command.</span></span>

* **`-c|--clear`**

  <span data-ttu-id="9000a-123">Opcja Clear wykonuje operację czyszczenia dla określonego typu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="9000a-123">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="9000a-124">Zawartość katalogów pamięci podręcznej jest usuwana rekursywnie.</span><span class="sxs-lookup"><span data-stu-id="9000a-124">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="9000a-125">Wykonywany użytkownik/grupa musi mieć uprawnienia do plików w katalogach pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="9000a-125">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="9000a-126">W przeciwnym razie zostanie wyświetlony komunikat o błędzie wskazujący pliki/foldery, które nie zostały wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="9000a-126">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

* **`-l|--list`**

  <span data-ttu-id="9000a-127">Opcja Lista służy do wyświetlania lokalizacji określonego typu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="9000a-127">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="9000a-128">Przykłady</span><span class="sxs-lookup"><span data-stu-id="9000a-128">Examples</span></span>

* <span data-ttu-id="9000a-129">Wyświetla ścieżki wszystkich lokalnych katalogów pamięci podręcznej (Katalog pamięci podręcznej http, Katalog pamięci podręcznej pakietów globalnych i tymczasowy katalog pamięci podręcznej):</span><span class="sxs-lookup"><span data-stu-id="9000a-129">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals all –l
  ```

* <span data-ttu-id="9000a-130">Wyświetla ścieżkę dla lokalnego katalogu pamięci podręcznej http:</span><span class="sxs-lookup"><span data-stu-id="9000a-130">Displays the path for the local http-cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals http-cache --list
  ```

* <span data-ttu-id="9000a-131">Czyści wszystkie pliki z katalogów lokalnej pamięci podręcznej (Katalog pamięci podręcznej http, Katalog pamięci podręcznej pakietów globalnych i tymczasowy katalog pamięci podręcznej):</span><span class="sxs-lookup"><span data-stu-id="9000a-131">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals all --clear
  ```

* <span data-ttu-id="9000a-132">Czyści wszystkie pliki w lokalnym katalogu globalnym pakietów pamięci podręcznej:</span><span class="sxs-lookup"><span data-stu-id="9000a-132">Clears all files in local global-packages cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals global-packages -c
  ```

* <span data-ttu-id="9000a-133">Czyści wszystkie pliki w lokalnym katalogu tymczasowej pamięci podręcznej:</span><span class="sxs-lookup"><span data-stu-id="9000a-133">Clears all files in local temporary cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals temp -c
  ```

## <a name="troubleshooting"></a><span data-ttu-id="9000a-134">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="9000a-134">Troubleshooting</span></span>

<span data-ttu-id="9000a-135">Informacje o typowych problemach i błędach przy użyciu polecenia `dotnet nuget locals` można znaleźć w temacie [Zarządzanie pamięcią podręczną NuGet](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="9000a-135">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>
