---
title: polecenie lokalne nuget DotNet
description: Polecenie lokalne nuget dotnet usuwa lub wyświetla ich listę zasobów lokalnych NuGet, takie jak pamięć podręczna żądań http, tymczasowej pamięci podręcznej lub folder komputera globalnymi pakietami.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 6436bbaee7ae50f4b225c32b2245c737b0d359c3
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539269"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="04174-103">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="04174-103">dotnet nuget locals</span></span>

<span data-ttu-id="04174-104">**Ten temat dotyczy: ✓** platformy .NET Core SDK w wersji 1.x i nowszymi wersjami</span><span class="sxs-lookup"><span data-stu-id="04174-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="04174-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="04174-105">Name</span></span>

<span data-ttu-id="04174-106">`dotnet nuget locals` -Usuwa lub wyświetla ich listę zasobów lokalnych NuGet.</span><span class="sxs-lookup"><span data-stu-id="04174-106">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="04174-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="04174-107">Synopsis</span></span>

```
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="04174-108">Opis</span><span class="sxs-lookup"><span data-stu-id="04174-108">Description</span></span>

<span data-ttu-id="04174-109">`dotnet nuget locals` Polecenie usuwa lub wyświetla ich listę zasobów lokalnych NuGet w pamięci podręcznej żądania http, tymczasowej pamięci podręcznej lub folder globalnymi pakietami dla komputera.</span><span class="sxs-lookup"><span data-stu-id="04174-109">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="04174-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="04174-110">Arguments</span></span>

* **`CACHE_LOCATION`**

  <span data-ttu-id="04174-111">Lokalizacja pamięci podręcznej, aby wyświetlić listę lub usuń zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="04174-111">The cache location to list or clear.</span></span> <span data-ttu-id="04174-112">Akceptuje ona jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="04174-112">It accepts one of the following values:</span></span>

  * <span data-ttu-id="04174-113">`all` — Wskazuje, że określona operacja jest stosowana do wszystkich typów pamięci podręcznej: pamięć podręczna żądań http, pamięci podręcznej globalnymi pakietami i tymczasowej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="04174-113">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
  * <span data-ttu-id="04174-114">`http-cache` — Wskazuje, że określona operacja jest stosowane tylko do pamięci podręcznej żądania http.</span><span class="sxs-lookup"><span data-stu-id="04174-114">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="04174-115">Nie ma wpływu na innych lokalizacji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="04174-115">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="04174-116">`global-packages` — Wskazuje, że określona operacja jest stosowane tylko do pamięci podręcznej globalnymi pakietami.</span><span class="sxs-lookup"><span data-stu-id="04174-116">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="04174-117">Nie ma wpływu na innych lokalizacji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="04174-117">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="04174-118">`temp` — Wskazuje, że określona operacja jest stosowane tylko do tymczasowej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="04174-118">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="04174-119">Nie ma wpływu na innych lokalizacji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="04174-119">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="04174-120">Opcje</span><span class="sxs-lookup"><span data-stu-id="04174-120">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="04174-121">Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.</span><span class="sxs-lookup"><span data-stu-id="04174-121">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="04174-122">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="04174-122">Prints out a short help for the command.</span></span>

* **`-c|--clear`**

  <span data-ttu-id="04174-123">Usuń zaznaczenie opcji wykonuje wyczyść operacji na typie określonym w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="04174-123">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="04174-124">Zawartość pamięci podręcznej katalogów są rekursywnie usunięte.</span><span class="sxs-lookup"><span data-stu-id="04174-124">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="04174-125">Wykonywanie użytkownika/grupy musi mieć uprawnienia do plików w katalogach pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="04174-125">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="04174-126">W przeciwnym razie zostanie wyświetlony błąd wskazujący plików/folderów, które nie zostały wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="04174-126">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

* **`-l|--list`**

  <span data-ttu-id="04174-127">Opcja listy jest używana do wyświetlania lokalizacji, typu określonego w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="04174-127">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="04174-128">Przykłady</span><span class="sxs-lookup"><span data-stu-id="04174-128">Examples</span></span>

* <span data-ttu-id="04174-129">Wyświetla ścieżki wszystkich katalogów lokalnej pamięci podręcznej (katalog pamięci podręcznej http, katalog pamięci podręcznej globalnymi pakietami i katalog tymczasowy pamięci podręcznej):</span><span class="sxs-lookup"><span data-stu-id="04174-129">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```console
  dotnet nuget locals –l all
  ```

* <span data-ttu-id="04174-130">Wyświetla ścieżkę do katalogu lokalnej pamięci podręcznej http:</span><span class="sxs-lookup"><span data-stu-id="04174-130">Displays the path for the local http-cache directory:</span></span>

  ```console
  dotnet nuget locals --list http-cache
  ```

* <span data-ttu-id="04174-131">Czyści wszystkie pliki ze wszystkich katalogów lokalnej pamięci podręcznej (katalog pamięci podręcznej http, katalog pamięci podręcznej globalnymi pakietami i katalog tymczasowy pamięci podręcznej):</span><span class="sxs-lookup"><span data-stu-id="04174-131">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```console
  dotnet nuget locals --clear all
  ```

* <span data-ttu-id="04174-132">Czyści wszystkie pliki w katalogu pamięci podręcznej lokalnej globalnymi pakietami:</span><span class="sxs-lookup"><span data-stu-id="04174-132">Clears all files in local global-packages cache directory:</span></span>

  ```console
  dotnet nuget locals -c global-packages
  ```

* <span data-ttu-id="04174-133">Czyści wszystkie pliki w katalogu lokalnym tymczasowa pamięć podręczna:</span><span class="sxs-lookup"><span data-stu-id="04174-133">Clears all files in local temporary cache directory:</span></span>

  ```console
  dotnet nuget locals -c temp
  ```

## <a name="troubleshooting"></a><span data-ttu-id="04174-134">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="04174-134">Troubleshooting</span></span>

<span data-ttu-id="04174-135">Instrukcje dotyczące często występujących problemów i błędów podczas korzystania z `dotnet nuget locals` polecenia, zobacz [zarządzania pamięcią podręczną programu NuGet](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="04174-135">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>
