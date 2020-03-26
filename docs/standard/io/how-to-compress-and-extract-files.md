---
title: 'Jak: Kompresowanie i wyodrębnianie plików'
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
ms.openlocfilehash: 10f990401830bc5f77176f4e586f15f7dd75ff14
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248020"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="b536d-102">Jak: Kompresowanie i wyodrębnianie plików</span><span class="sxs-lookup"><span data-stu-id="b536d-102">How to: Compress and extract files</span></span>

<span data-ttu-id="b536d-103">Obszar <xref:System.IO.Compression> nazw zawiera następujące typy kompresji i dekompresji plików i strumieni.</span><span class="sxs-lookup"><span data-stu-id="b536d-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="b536d-104">Za pomocą tych typów można również odczytać i zmodyfikować zawartość skompresowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="b536d-104">You can also use these types to read and modify the contents of a compressed file.</span></span>

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="b536d-105">Poniższe przykłady pokazują niektóre operacje, które można wykonać za pomocą skompresowanych plików.</span><span class="sxs-lookup"><span data-stu-id="b536d-105">The following examples show some of the operations you can perform with compressed files.</span></span> <span data-ttu-id="b536d-106">Te przykłady wymagają następujących pakietów NuGet, które mają zostać dodane do projektu:</span><span class="sxs-lookup"><span data-stu-id="b536d-106">These examples require the following NuGet packages to be added to your project:</span></span>

- [<span data-ttu-id="b536d-107">System.IO.Kompresja</span><span class="sxs-lookup"><span data-stu-id="b536d-107">System.IO.Compression</span></span>](https://www.nuget.org/packages/System.IO.Compression)
- [<span data-ttu-id="b536d-108">Plik System.IO.Compression.ZipFile</span><span class="sxs-lookup"><span data-stu-id="b536d-108">System.IO.Compression.ZipFile</span></span>](https://www.nuget.org/packages/System.IO.Compression.ZipFile)

<span data-ttu-id="b536d-109">Jeśli używasz programu .NET Framework, dodaj odwołania do tych dwóch bibliotek do projektu:</span><span class="sxs-lookup"><span data-stu-id="b536d-109">If you're using .NET Framework, add references to these two libraries to your project:</span></span>

- `System.IO.Compression`
- `System.IO.Compression.FileSystem`

## <a name="example-1-create-and-extract-a-zip-file"></a><span data-ttu-id="b536d-110">Przykład 1: Tworzenie i wyodrębnianie pliku zip</span><span class="sxs-lookup"><span data-stu-id="b536d-110">Example 1: Create and extract a .zip file</span></span>

<span data-ttu-id="b536d-111">W poniższym przykładzie pokazano, jak utworzyć i wyodrębnić skompresowany plik *zip* przy użyciu <xref:System.IO.Compression.ZipFile> klasy.</span><span class="sxs-lookup"><span data-stu-id="b536d-111">The following example shows how to create and extract a compressed *.zip* file by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="b536d-112">W przykładzie zawartość folderu jest kompresowany do nowego pliku *zip,* a następnie wyodrębnia go do nowego folderu.</span><span class="sxs-lookup"><span data-stu-id="b536d-112">The example compresses the contents of a folder into a new *.zip* file, and then extracts the zip to a new folder.</span></span>

<span data-ttu-id="b536d-113">Aby uruchomić przykład, utwórz folder *startowy* w folderze programu i wypełnij go plikami do zip.</span><span class="sxs-lookup"><span data-stu-id="b536d-113">To run the sample, create a *start* folder in your program folder and populate it with files to zip.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a><span data-ttu-id="b536d-114">Przykład 2: Wyodrębnianie określonych rozszerzeń plików</span><span class="sxs-lookup"><span data-stu-id="b536d-114">Example 2: Extract specific file extensions</span></span>

<span data-ttu-id="b536d-115">Następny przykład iteruje zawartość istniejącego pliku *zip* i wyodrębnia pliki, które mają rozszerzenie *txt.*</span><span class="sxs-lookup"><span data-stu-id="b536d-115">The next example iterates through the contents of an existing *.zip* file and extracts files that have a *.txt* extension.</span></span> <span data-ttu-id="b536d-116">Używa klasy, <xref:System.IO.Compression.ZipArchive> aby uzyskać dostęp do <xref:System.IO.Compression.ZipArchiveEntry> zip i klasy do kontroli poszczególnych wpisów.</span><span class="sxs-lookup"><span data-stu-id="b536d-116">It uses the <xref:System.IO.Compression.ZipArchive> class to access the zip, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries.</span></span> <span data-ttu-id="b536d-117">Metoda <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> rozszerzenia obiektu <xref:System.IO.Compression.ZipArchiveEntry> jest dostępna <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> w klasie.</span><span class="sxs-lookup"><span data-stu-id="b536d-117">The extension method <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> for the <xref:System.IO.Compression.ZipArchiveEntry> object is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span>

<span data-ttu-id="b536d-118">Aby uruchomić próbkę, umieść plik *zip* o nazwie *result.zip* w folderze programu.</span><span class="sxs-lookup"><span data-stu-id="b536d-118">To run the sample, place a *.zip* file called *result.zip* in your program folder.</span></span> <span data-ttu-id="b536d-119">Po wyświetleniu monitu podaj nazwę folderu, do którym chcesz wyodrębnić.</span><span class="sxs-lookup"><span data-stu-id="b536d-119">When prompted, provide a folder name to extract to.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b536d-120">Podczas rozpakowywania plików należy szukać złośliwych ścieżek plików, które mogą wydostać się z katalogu, do którego się rozpakujesz.</span><span class="sxs-lookup"><span data-stu-id="b536d-120">When unzipping files, you must look for malicious file paths, which can escape out of the directory you unzip into.</span></span> <span data-ttu-id="b536d-121">Jest to znane jako atak przechodzenia ścieżki.</span><span class="sxs-lookup"><span data-stu-id="b536d-121">This is known as a path traversal attack.</span></span> <span data-ttu-id="b536d-122">W poniższym przykładzie pokazano, jak sprawdzić, czy złośliwe ścieżki plików i zapewnia bezpieczny sposób rozpakowania.</span><span class="sxs-lookup"><span data-stu-id="b536d-122">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a><span data-ttu-id="b536d-123">Przykład 3: Dodawanie pliku do istniejącego kodu błyskawicznego</span><span class="sxs-lookup"><span data-stu-id="b536d-123">Example 3: Add a file to an existing zip</span></span>

<span data-ttu-id="b536d-124">Poniższy przykład używa <xref:System.IO.Compression.ZipArchive> klasy, aby uzyskać dostęp do istniejącego pliku *zip* i dodaje do niego plik.</span><span class="sxs-lookup"><span data-stu-id="b536d-124">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing *.zip* file, and adds a file to it.</span></span> <span data-ttu-id="b536d-125">Nowy plik zostanie skompresowany po dodaniu go do istniejącego kodu błyskawicznego.</span><span class="sxs-lookup"><span data-stu-id="b536d-125">The new file gets compressed when you add it to the existing zip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a><span data-ttu-id="b536d-126">Przykład 4: Kompresowanie i dekompresja plików gz</span><span class="sxs-lookup"><span data-stu-id="b536d-126">Example 4: Compress and decompress .gz files</span></span>

<span data-ttu-id="b536d-127">Można również użyć <xref:System.IO.Compression.GZipStream> <xref:System.IO.Compression.DeflateStream> i klas do kompresji i dekompresji danych.</span><span class="sxs-lookup"><span data-stu-id="b536d-127">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="b536d-128">Używają tego samego algorytmu kompresji.</span><span class="sxs-lookup"><span data-stu-id="b536d-128">They use the same compression algorithm.</span></span> <span data-ttu-id="b536d-129">Można dekompresować <xref:System.IO.Compression.GZipStream> obiekty zapisywane w pliku *gz* przy użyciu wielu typowych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="b536d-129">You can decompress <xref:System.IO.Compression.GZipStream> objects that are written to a *.gz* file by using many common tools.</span></span> <span data-ttu-id="b536d-130">W poniższym przykładzie pokazano, jak skompresować i <xref:System.IO.Compression.GZipStream> dekompresować katalog plików przy użyciu klasy:</span><span class="sxs-lookup"><span data-stu-id="b536d-130">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="b536d-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b536d-131">See also</span></span>

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [<span data-ttu-id="b536d-132">We/wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="b536d-132">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
