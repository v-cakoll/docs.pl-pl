---
title: 'Jak: Kompresować i wyodrębniać pliki'
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
ms.openlocfilehash: 5aa25e265ed6ffb613e9916414c6f2335a4aaf57
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159380"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="34f91-102">Jak: Kompresować i wyodrębniać pliki</span><span class="sxs-lookup"><span data-stu-id="34f91-102">How to: Compress and extract files</span></span>

<span data-ttu-id="34f91-103">Obszar <xref:System.IO.Compression> nazw zawiera następujące typy kompresji i dekompresji plików i strumieni.</span><span class="sxs-lookup"><span data-stu-id="34f91-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="34f91-104">Za pomocą tych typów można również odczytywać i modyfikować zawartość skompresowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="34f91-104">You can also use these types to read and modify the contents of a compressed file.</span></span>

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="34f91-105">W poniższych przykładach przedstawiono niektóre operacje, które można wykonać z skompresowanymi plikami.</span><span class="sxs-lookup"><span data-stu-id="34f91-105">The following examples show some of the operations you can perform with compressed files.</span></span>

## <a name="example-1-create-and-extract-a-zip-file"></a><span data-ttu-id="34f91-106">Przykład 1: Tworzenie i wyodrębnianie pliku zip</span><span class="sxs-lookup"><span data-stu-id="34f91-106">Example 1: Create and extract a .zip file</span></span>

<span data-ttu-id="34f91-107">W poniższym przykładzie pokazano, jak utworzyć i wyodrębnić skompresowany plik *zip* przy użyciu <xref:System.IO.Compression.ZipFile> klasy.</span><span class="sxs-lookup"><span data-stu-id="34f91-107">The following example shows how to create and extract a compressed *.zip* file by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="34f91-108">Przykład kompresuje zawartość folderu do nowego pliku *zip,* a następnie wyodrębnia zip do nowego folderu.</span><span class="sxs-lookup"><span data-stu-id="34f91-108">The example compresses the contents of a folder into a new *.zip* file, and then extracts the zip to a new folder.</span></span>

<span data-ttu-id="34f91-109">Aby uruchomić przykład, utwórz folder *startowy* w folderze programu i wypełnij go plikami do zip.</span><span class="sxs-lookup"><span data-stu-id="34f91-109">To run the sample, create a *start* folder in your program folder and populate it with files to zip.</span></span>

<span data-ttu-id="34f91-110">Jeśli pojawi się błąd kompilacji "Nazwa "ZipFile" nie istnieje w bieżącym `System.IO.Compression.FileSystem` kontekście," dodaj odwołanie do zestawu do projektu.</span><span class="sxs-lookup"><span data-stu-id="34f91-110">If you get the build error "The name 'ZipFile' does not exist in the current context," add a reference to the `System.IO.Compression.FileSystem` assembly to your project.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a><span data-ttu-id="34f91-111">Przykład 2: Wyodrębnianie określonych rozszerzeń plików</span><span class="sxs-lookup"><span data-stu-id="34f91-111">Example 2: Extract specific file extensions</span></span>

<span data-ttu-id="34f91-112">Następny przykład iteforuje zawartość istniejącego pliku *zip* i wyodrębnia pliki, które mają rozszerzenie *txt.*</span><span class="sxs-lookup"><span data-stu-id="34f91-112">The next example iterates through the contents of an existing *.zip* file and extracts files that have a *.txt* extension.</span></span> <span data-ttu-id="34f91-113">Używa klasy, <xref:System.IO.Compression.ZipArchive> aby uzyskać dostęp <xref:System.IO.Compression.ZipArchiveEntry> do zip i klasy do kontroli poszczególnych wpisów.</span><span class="sxs-lookup"><span data-stu-id="34f91-113">It uses the <xref:System.IO.Compression.ZipArchive> class to access the zip, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries.</span></span> <span data-ttu-id="34f91-114">Metoda <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> rozszerzenia dla <xref:System.IO.Compression.ZipArchiveEntry> obiektu jest <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> dostępna w klasie.</span><span class="sxs-lookup"><span data-stu-id="34f91-114">The extension method <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> for the <xref:System.IO.Compression.ZipArchiveEntry> object is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span>

<span data-ttu-id="34f91-115">Aby uruchomić próbkę, umieść plik *zip* o nazwie *result.zip* w folderze programu.</span><span class="sxs-lookup"><span data-stu-id="34f91-115">To run the sample, place a *.zip* file called *result.zip* in your program folder.</span></span> <span data-ttu-id="34f91-116">Po wyświetleniu monitu podaj nazwę folderu, do który chcesz wyodrębnić.</span><span class="sxs-lookup"><span data-stu-id="34f91-116">When prompted, provide a folder name to extract to.</span></span>

<span data-ttu-id="34f91-117">Jeśli pojawi się błąd kompilacji "Nazwa "ZipFile" nie istnieje w bieżącym `System.IO.Compression.FileSystem` kontekście," dodaj odwołanie do zestawu do projektu.</span><span class="sxs-lookup"><span data-stu-id="34f91-117">If you get the build error "The name 'ZipFile' does not exist in the current context," add a reference to the `System.IO.Compression.FileSystem` assembly to your project.</span></span>

<span data-ttu-id="34f91-118">Jeśli pojawi się błąd "Typ "ZipArchive" jest zdefiniowany w zestawie, do `System.IO.Compression` którego nie odwołuje się", dodaj odwołanie do zestawu do projektu.</span><span class="sxs-lookup"><span data-stu-id="34f91-118">If you get the error "The type 'ZipArchive' is defined in an assembly that is not referenced," add a reference to the `System.IO.Compression` assembly to your project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34f91-119">Podczas rozpakowywania plików należy szukać złośliwych ścieżek plików, które mogą wydostać się z katalogu, do którego rozpakujesz.</span><span class="sxs-lookup"><span data-stu-id="34f91-119">When unzipping files, you must look for malicious file paths, which can escape out of the directory you unzip into.</span></span> <span data-ttu-id="34f91-120">Jest to nazywane atakiem przechodzenia ścieżki.</span><span class="sxs-lookup"><span data-stu-id="34f91-120">This is known as a path traversal attack.</span></span> <span data-ttu-id="34f91-121">W poniższym przykładzie pokazano, jak sprawdzić, czy nie ma złośliwych ścieżek plików i zapewnia bezpieczny sposób rozpakowywania.</span><span class="sxs-lookup"><span data-stu-id="34f91-121">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a><span data-ttu-id="34f91-122">Przykład 3: Dodawanie pliku do istniejącego zamka błyskawicznego</span><span class="sxs-lookup"><span data-stu-id="34f91-122">Example 3: Add a file to an existing zip</span></span>

<span data-ttu-id="34f91-123">W poniższym <xref:System.IO.Compression.ZipArchive> przykładzie użyto klasy, aby uzyskać dostęp do istniejącego pliku *zip* i dodaje plik do niego.</span><span class="sxs-lookup"><span data-stu-id="34f91-123">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing *.zip* file, and adds a file to it.</span></span> <span data-ttu-id="34f91-124">Nowy plik zostanie skompresowany po dodaniu go do istniejącego zip.</span><span class="sxs-lookup"><span data-stu-id="34f91-124">The new file gets compressed when you add it to the existing zip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a><span data-ttu-id="34f91-125">Przykład 4: Kompresowanie i dekompresowanie plików .gz</span><span class="sxs-lookup"><span data-stu-id="34f91-125">Example 4: Compress and decompress .gz files</span></span>

<span data-ttu-id="34f91-126">Można również użyć <xref:System.IO.Compression.GZipStream> <xref:System.IO.Compression.DeflateStream> i klas do kompresji i dekompresji danych.</span><span class="sxs-lookup"><span data-stu-id="34f91-126">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="34f91-127">Używają tego samego algorytmu kompresji.</span><span class="sxs-lookup"><span data-stu-id="34f91-127">They use the same compression algorithm.</span></span> <span data-ttu-id="34f91-128">Można dekompresować <xref:System.IO.Compression.GZipStream> obiekty zapisane w pliku *gz* przy użyciu wielu typowych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="34f91-128">You can decompress <xref:System.IO.Compression.GZipStream> objects that are written to a *.gz* file by using many common tools.</span></span> <span data-ttu-id="34f91-129">W poniższym przykładzie pokazano, jak kompresować i <xref:System.IO.Compression.GZipStream> dekompresować katalog plików przy użyciu klasy:</span><span class="sxs-lookup"><span data-stu-id="34f91-129">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="34f91-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34f91-130">See also</span></span>

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [<span data-ttu-id="34f91-131">Plik i strumień we/wy</span><span class="sxs-lookup"><span data-stu-id="34f91-131">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
