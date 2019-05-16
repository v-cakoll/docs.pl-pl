---
title: polecenie lokalne nuget DotNet
description: Polecenie lokalne nuget dotnet usuwa lub wyświetla ich listę zasobów lokalnych NuGet, takie jak pamięć podręczna żądań http, tymczasowej pamięci podręcznej lub folder komputera globalnymi pakietami.
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: 0a9fd7876aa4d1907eb37e6bac54295d938d36d3
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632424"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="d7bc0-103">Zmienne lokalne nuget DotNet</span><span class="sxs-lookup"><span data-stu-id="d7bc0-103">dotnet nuget locals</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d7bc0-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="d7bc0-104">Name</span></span>

<span data-ttu-id="d7bc0-105">`dotnet nuget locals` -Usuwa lub wyświetla ich listę zasobów lokalnych NuGet.</span><span class="sxs-lookup"><span data-stu-id="d7bc0-105">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d7bc0-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="d7bc0-106">Synopsis</span></span>

```
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="d7bc0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d7bc0-107">Description</span></span>

<span data-ttu-id="d7bc0-108">`dotnet nuget locals` Polecenie usuwa lub wyświetla ich listę zasobów lokalnych NuGet w pamięci podręcznej żądania http, tymczasowej pamięci podręcznej lub folder globalnymi pakietami dla komputera.</span><span class="sxs-lookup"><span data-stu-id="d7bc0-108">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="d7bc0-109">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d7bc0-109">Arguments</span></span>

* **`CACHE_LOCATION`**

  <span data-ttu-id="d7bc0-110">Lokalizacja pamięci podręcznej, aby wyświetlić listę lub usuń zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="d7bc0-110">The cache location to list or clear.</span></span> <span data-ttu-id="d7bc0-111">Akceptuje ona jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="d7bc0-111">It accepts one of the following values:</span></span>

  * <span data-ttu-id="d7bc0-112">`all` — Wskazuje, że określona operacja jest stosowana do wszystkich typów pamięci podręcznej: pamięć podręczna żądań http, pamięci podręcznej globalnymi pakietami i tymczasowej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d7bc0-112">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
  * <span data-ttu-id="d7bc0-113">`http-cache` — Wskazuje, że określona operacja jest stosowane tylko do pamięci podręcznej żądania http.</span><span class="sxs-lookup"><span data-stu-id="d7bc0-113">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="d7bc0-114">Nie ma wpływu na innych lokalizacji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d7bc0-114">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="d7bc0-115">`global-packages` — Wskazuje, że określona operacja jest stosowane tylko do pamięci podręcznej globalnymi pakietami.</span><span class="sxs-lookup"><span data-stu-id="d7bc0-115">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="d7bc0-116">Nie ma wpływu na innych lokalizacji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d7bc0-116">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="d7bc0-117">`temp` — Wskazuje, że określona operacja jest stosowane tylko do tymczasowej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d7bc0-117">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="d7bc0-118">Nie ma wpływu na innych lokalizacji pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d7bc0-118">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="d7bc0-119">Opcje</span><span class="sxs-lookup"><span data-stu-id="d7bc0-119">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="d7bc0-120">Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.</span><span class="sxs-lookup"><span data-stu-id="d7bc0-120">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="d7bc0-121">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="d7bc0-121">Prints out a short help for the command.</span></span>

* **`-c|--clear`**

  <span data-ttu-id="d7bc0-122">Usuń zaznaczenie opcji wykonuje wyczyść operacji na typie określonym w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d7bc0-122">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="d7bc0-123">Zawartość pamięci podręcznej katalogów są rekursywnie usunięte.</span><span class="sxs-lookup"><span data-stu-id="d7bc0-123">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="d7bc0-124">Wykonywanie użytkownika/grupy musi mieć uprawnienia do plików w katalogach pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d7bc0-124">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="d7bc0-125">W przeciwnym razie zostanie wyświetlony błąd wskazujący plików/folderów, które nie zostały wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="d7bc0-125">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

* **`-l|--list`**

  <span data-ttu-id="d7bc0-126">Opcja listy jest używana do wyświetlania lokalizacji, typu określonego w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d7bc0-126">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="d7bc0-127">Przykłady</span><span class="sxs-lookup"><span data-stu-id="d7bc0-127">Examples</span></span>

* <span data-ttu-id="d7bc0-128">Wyświetla ścieżki wszystkich katalogów lokalnej pamięci podręcznej (katalog pamięci podręcznej http, katalog pamięci podręcznej globalnymi pakietami i katalog tymczasowy pamięci podręcznej):</span><span class="sxs-lookup"><span data-stu-id="d7bc0-128">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```console
  dotnet nuget locals –l all
  ```

* <span data-ttu-id="d7bc0-129">Wyświetla ścieżkę do katalogu lokalnej pamięci podręcznej http:</span><span class="sxs-lookup"><span data-stu-id="d7bc0-129">Displays the path for the local http-cache directory:</span></span>

  ```console
  dotnet nuget locals --list http-cache
  ```

* <span data-ttu-id="d7bc0-130">Czyści wszystkie pliki ze wszystkich katalogów lokalnej pamięci podręcznej (katalog pamięci podręcznej http, katalog pamięci podręcznej globalnymi pakietami i katalog tymczasowy pamięci podręcznej):</span><span class="sxs-lookup"><span data-stu-id="d7bc0-130">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```console
  dotnet nuget locals --clear all
  ```

* <span data-ttu-id="d7bc0-131">Czyści wszystkie pliki w katalogu pamięci podręcznej lokalnej globalnymi pakietami:</span><span class="sxs-lookup"><span data-stu-id="d7bc0-131">Clears all files in local global-packages cache directory:</span></span>

  ```console
  dotnet nuget locals -c global-packages
  ```

* <span data-ttu-id="d7bc0-132">Czyści wszystkie pliki w katalogu lokalnym tymczasowa pamięć podręczna:</span><span class="sxs-lookup"><span data-stu-id="d7bc0-132">Clears all files in local temporary cache directory:</span></span>

  ```console
  dotnet nuget locals -c temp
  ```

## <a name="troubleshooting"></a><span data-ttu-id="d7bc0-133">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="d7bc0-133">Troubleshooting</span></span>

<span data-ttu-id="d7bc0-134">Instrukcje dotyczące często występujących problemów i błędów podczas korzystania z `dotnet nuget locals` polecenia, zobacz [zarządzania pamięcią podręczną programu NuGet](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="d7bc0-134">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>
