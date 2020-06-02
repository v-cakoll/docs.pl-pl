---
title: 'Instrukcje: kompresowanie i wyodrębnianie plików'
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
ms.openlocfilehash: 28f9a0baa73f58b0a5c7f93a4b0b3ece3b87c3a5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288566"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="4c70a-102">Instrukcje: kompresowanie i wyodrębnianie plików</span><span class="sxs-lookup"><span data-stu-id="4c70a-102">How to: Compress and extract files</span></span>

<span data-ttu-id="4c70a-103"><xref:System.IO.Compression>Przestrzeń nazw zawiera następujące typy do kompresowania i dekompresowania plików i strumieni.</span><span class="sxs-lookup"><span data-stu-id="4c70a-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="4c70a-104">Możesz również użyć tych typów do odczytu i modyfikacji zawartości skompresowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="4c70a-104">You can also use these types to read and modify the contents of a compressed file.</span></span>

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="4c70a-105">W poniższych przykładach przedstawiono niektóre operacje, które można wykonywać przy użyciu skompresowanych plików.</span><span class="sxs-lookup"><span data-stu-id="4c70a-105">The following examples show some of the operations you can perform with compressed files.</span></span> <span data-ttu-id="4c70a-106">Te przykłady wymagają dodania następujących pakietów NuGet do projektu:</span><span class="sxs-lookup"><span data-stu-id="4c70a-106">These examples require the following NuGet packages to be added to your project:</span></span>

- [<span data-ttu-id="4c70a-107">System. IO. Compression</span><span class="sxs-lookup"><span data-stu-id="4c70a-107">System.IO.Compression</span></span>](https://www.nuget.org/packages/System.IO.Compression)
- [<span data-ttu-id="4c70a-108">System. IO. Compression. ZipFile</span><span class="sxs-lookup"><span data-stu-id="4c70a-108">System.IO.Compression.ZipFile</span></span>](https://www.nuget.org/packages/System.IO.Compression.ZipFile)

<span data-ttu-id="4c70a-109">Jeśli używasz .NET Framework, Dodaj odwołania do tych dwóch bibliotek do projektu:</span><span class="sxs-lookup"><span data-stu-id="4c70a-109">If you're using .NET Framework, add references to these two libraries to your project:</span></span>

- `System.IO.Compression`
- `System.IO.Compression.FileSystem`

## <a name="example-1-create-and-extract-a-zip-file"></a><span data-ttu-id="4c70a-110">Przykład 1: Tworzenie i Wyodrębnianie pliku zip</span><span class="sxs-lookup"><span data-stu-id="4c70a-110">Example 1: Create and extract a .zip file</span></span>

<span data-ttu-id="4c70a-111">Poniższy przykład pokazuje, jak utworzyć i wyodrębnić skompresowany plik *zip* przy użyciu <xref:System.IO.Compression.ZipFile> klasy.</span><span class="sxs-lookup"><span data-stu-id="4c70a-111">The following example shows how to create and extract a compressed *.zip* file by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="4c70a-112">Przykład kompresuje zawartość folderu do nowego pliku *zip* , a następnie wyodrębnia plik zip do nowego folderu.</span><span class="sxs-lookup"><span data-stu-id="4c70a-112">The example compresses the contents of a folder into a new *.zip* file, and then extracts the zip to a new folder.</span></span>

<span data-ttu-id="4c70a-113">Aby uruchomić przykład, należy utworzyć folder *startowy* w folderze programu i wypełnić go plikami do pliku zip.</span><span class="sxs-lookup"><span data-stu-id="4c70a-113">To run the sample, create a *start* folder in your program folder and populate it with files to zip.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a><span data-ttu-id="4c70a-114">Przykład 2: Wyodrębnienie określonych rozszerzeń plików</span><span class="sxs-lookup"><span data-stu-id="4c70a-114">Example 2: Extract specific file extensions</span></span>

<span data-ttu-id="4c70a-115">Następny przykład wykonuje iterację zawartości istniejącego pliku *. zip* i wyodrębnia pliki z rozszerzeniem *. txt* .</span><span class="sxs-lookup"><span data-stu-id="4c70a-115">The next example iterates through the contents of an existing *.zip* file and extracts files that have a *.txt* extension.</span></span> <span data-ttu-id="4c70a-116">Używa <xref:System.IO.Compression.ZipArchive> klasy w celu uzyskania dostępu do pliku zip oraz <xref:System.IO.Compression.ZipArchiveEntry> klasy do inspekcji poszczególnych wpisów.</span><span class="sxs-lookup"><span data-stu-id="4c70a-116">It uses the <xref:System.IO.Compression.ZipArchive> class to access the zip, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries.</span></span> <span data-ttu-id="4c70a-117">Metoda rozszerzenia <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> dla <xref:System.IO.Compression.ZipArchiveEntry> obiektu jest dostępna w <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> klasie.</span><span class="sxs-lookup"><span data-stu-id="4c70a-117">The extension method <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> for the <xref:System.IO.Compression.ZipArchiveEntry> object is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span>

<span data-ttu-id="4c70a-118">Aby uruchomić przykład, Umieść plik *zip* o nazwie *Result. zip* w folderze programu.</span><span class="sxs-lookup"><span data-stu-id="4c70a-118">To run the sample, place a *.zip* file called *result.zip* in your program folder.</span></span> <span data-ttu-id="4c70a-119">Po wyświetleniu monitu podaj nazwę folderu do wyodrębnienia.</span><span class="sxs-lookup"><span data-stu-id="4c70a-119">When prompted, provide a folder name to extract to.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4c70a-120">Podczas rozpakowywania plików należy wyszukać złośliwe ścieżki plików, które mogą wyjść z katalogu, w którym się znajdujesz.</span><span class="sxs-lookup"><span data-stu-id="4c70a-120">When unzipping files, you must look for malicious file paths, which can escape out of the directory you unzip into.</span></span> <span data-ttu-id="4c70a-121">Jest to tzw. atak przechodzenia do lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="4c70a-121">This is known as a path traversal attack.</span></span> <span data-ttu-id="4c70a-122">W poniższym przykładzie pokazano, jak wyszukiwać złośliwe ścieżki plików i zapewniać bezpieczną metodę rozpakowania.</span><span class="sxs-lookup"><span data-stu-id="4c70a-122">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a><span data-ttu-id="4c70a-123">Przykład 3: Dodaj plik do istniejącego pliku zip</span><span class="sxs-lookup"><span data-stu-id="4c70a-123">Example 3: Add a file to an existing zip</span></span>

<span data-ttu-id="4c70a-124">Poniższy przykład używa <xref:System.IO.Compression.ZipArchive> klasy, aby uzyskać dostęp do istniejącego pliku *. zip* i dodaje do niego plik.</span><span class="sxs-lookup"><span data-stu-id="4c70a-124">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing *.zip* file, and adds a file to it.</span></span> <span data-ttu-id="4c70a-125">Nowy plik zostanie skompresowany po dodaniu go do istniejącego pliku zip.</span><span class="sxs-lookup"><span data-stu-id="4c70a-125">The new file gets compressed when you add it to the existing zip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a><span data-ttu-id="4c70a-126">Przykład 4: kompresowanie i dekompresowanie plików. gz</span><span class="sxs-lookup"><span data-stu-id="4c70a-126">Example 4: Compress and decompress .gz files</span></span>

<span data-ttu-id="4c70a-127">Można również użyć <xref:System.IO.Compression.GZipStream> <xref:System.IO.Compression.DeflateStream> klas i do kompresowania i dekompresowania danych.</span><span class="sxs-lookup"><span data-stu-id="4c70a-127">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="4c70a-128">Korzystają one z tego samego algorytmu kompresji.</span><span class="sxs-lookup"><span data-stu-id="4c70a-128">They use the same compression algorithm.</span></span> <span data-ttu-id="4c70a-129">Można dekompresowanie <xref:System.IO.Compression.GZipStream> obiektów, które są zapisywane w pliku *. gz* za pomocą wielu popularnych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="4c70a-129">You can decompress <xref:System.IO.Compression.GZipStream> objects that are written to a *.gz* file by using many common tools.</span></span> <span data-ttu-id="4c70a-130">Poniższy przykład przedstawia sposób kompresowania i dekompresowania katalogu plików przy użyciu <xref:System.IO.Compression.GZipStream> klasy:</span><span class="sxs-lookup"><span data-stu-id="4c70a-130">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="4c70a-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c70a-131">See also</span></span>

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [<span data-ttu-id="4c70a-132">We/wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="4c70a-132">File and stream I/O</span></span>](index.md)
