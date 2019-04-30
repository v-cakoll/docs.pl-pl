---
title: 'Instrukcje: Kompresowanie i wyodrębnianie plików'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a4ea4c32f5b73b283a5982f16e55a4d078171c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61752037"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="8dbf3-102">Instrukcje: Kompresowanie i wyodrębnianie plików</span><span class="sxs-lookup"><span data-stu-id="8dbf3-102">How to: Compress and extract files</span></span>

<span data-ttu-id="8dbf3-103"><xref:System.IO.Compression> Przestrzeń nazw zawiera następujące typy do kompresowania i dekompresowania plików i strumieni.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="8dbf3-104">Można również użyć tych typów może odczytywać i modyfikować zawartość skompresowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-104">You can also use these types to read and modify the contents of a compressed file.</span></span>

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="8dbf3-105">W poniższych przykładach pokazano niektóre operacje, które można wykonywać za pomocą skompresowanych plików.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-105">The following examples show some of the operations you can perform with compressed files.</span></span>

## <a name="example-1-create-and-extract-a-zip-file"></a><span data-ttu-id="8dbf3-106">Przykład 1: Tworzenie i Wyodrębnij plik zip</span><span class="sxs-lookup"><span data-stu-id="8dbf3-106">Example 1: Create and extract a .zip file</span></span>

<span data-ttu-id="8dbf3-107">Poniższy przykład pokazuje, jak utworzyć i Wyodrębnij skompresowane *zip* plików przy użyciu <xref:System.IO.Compression.ZipFile> klasy.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-107">The following example shows how to create and extract a compressed *.zip* file by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="8dbf3-108">Przykład kompresuje zawartość folderu do nowego *zip* pliku, a następnie wyodrębnia pliku zip do nowego folderu.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-108">The example compresses the contents of a folder into a new *.zip* file, and then extracts the zip to a new folder.</span></span> 

<span data-ttu-id="8dbf3-109">Aby uruchomić przykład, utworzyć *start* folderu w folderze program i wypełnić ją plikami zip.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-109">To run the sample, create a *start* folder in your program folder and populate it with files to zip.</span></span> 

<span data-ttu-id="8dbf3-110">Jeśli wystąpi błąd kompilacji "Name"ZipFile"nie istnieje w bieżącym kontekście", Dodaj odwołanie do `System.IO.Compression.FileSystem` zestawu do projektu.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-110">If you get the build error "The name 'ZipFile' does not exist in the current context," add a reference to the `System.IO.Compression.FileSystem` assembly to your project.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a><span data-ttu-id="8dbf3-111">Przykład 2: Wyodrębnianie określonych rozszerzeń plików</span><span class="sxs-lookup"><span data-stu-id="8dbf3-111">Example 2: Extract specific file extensions</span></span>

<span data-ttu-id="8dbf3-112">Następny przykład wykonuje iterację przez zawartość do istniejącego *zip* plików i wyodrębnienie plików, które mają *.txt* rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-112">The next example iterates through the contents of an existing *.zip* file and extracts files that have a *.txt* extension.</span></span> <span data-ttu-id="8dbf3-113">Używa ona <xref:System.IO.Compression.ZipArchive> klasy w celu dostępu do pliku zip, a <xref:System.IO.Compression.ZipArchiveEntry> klasy, aby sprawdzić poszczególne wpisy.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-113">It uses the <xref:System.IO.Compression.ZipArchive> class to access the zip, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries.</span></span> <span data-ttu-id="8dbf3-114">Metoda rozszerzenia <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> dla <xref:System.IO.Compression.ZipArchiveEntry> obiekt jest dostępny w <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-114">The extension method <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> for the <xref:System.IO.Compression.ZipArchiveEntry> object is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span> 

<span data-ttu-id="8dbf3-115">Aby uruchomić przykład, umieść *zip* pliku o nazwie *result.zip* w folderze program.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-115">To run the sample, place a *.zip* file called *result.zip* in your program folder.</span></span> <span data-ttu-id="8dbf3-116">Po wyświetleniu monitu podaj nazwę folderu, aby wyodrębnić.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-116">When prompted, provide a folder name to extract to.</span></span> 

<span data-ttu-id="8dbf3-117">Jeśli wystąpi błąd kompilacji "Name"ZipFile"nie istnieje w bieżącym kontekście", Dodaj odwołanie do `System.IO.Compression.FileSystem` zestawu do projektu.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-117">If you get the build error "The name 'ZipFile' does not exist in the current context," add a reference to the `System.IO.Compression.FileSystem` assembly to your project.</span></span>

<span data-ttu-id="8dbf3-118">Jeśli zostanie wyświetlony błąd "Type"Obiekt ZipArchive"jest zdefiniowany w zestawie, który nie odwołuje się" Dodaj odwołanie do `System.IO.Compression` zestawu do projektu.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-118">If you get the error "The type 'ZipArchive' is defined in an assembly that is not referenced," add a reference to the `System.IO.Compression` assembly to your project.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="8dbf3-119">Podczas rozpakowywania plików, możesz wyszukiwać ścieżki złośliwych plików, które można udosłownić spoza katalogu w którym Rozpakuj do.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-119">When unzipping files, you must look for malicious file paths, which can escape out of the directory you unzip into.</span></span> <span data-ttu-id="8dbf3-120">Jest to znane jako atak przechodzenia przez ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-120">This is known as a path traversal attack.</span></span> <span data-ttu-id="8dbf3-121">Poniższy przykład pokazuje, jak sprawdzić, czy ścieżki złośliwych plików i zapewnia bezpieczny sposób Rozpakuj go.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-121">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a><span data-ttu-id="8dbf3-122">Przykład 3: Dodaj plik do istniejącego pliku zip</span><span class="sxs-lookup"><span data-stu-id="8dbf3-122">Example 3: Add a file to an existing zip</span></span>

<span data-ttu-id="8dbf3-123">W poniższym przykładzie użyto <xref:System.IO.Compression.ZipArchive> klasy w celu uzyskania dostępu do istniejącego *zip* pliku i dodaje plik do niego.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-123">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing *.zip* file, and adds a file to it.</span></span> <span data-ttu-id="8dbf3-124">Nowy plik pobiera skompresowany, gdy zostanie on dodany do istniejącego pliku zip.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-124">The new file gets compressed when you add it to the existing zip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a><span data-ttu-id="8dbf3-125">Przykład 4: Kompresję i dekompresję plików .gz</span><span class="sxs-lookup"><span data-stu-id="8dbf3-125">Example 4: Compress and decompress .gz files</span></span>

<span data-ttu-id="8dbf3-126">Można również użyć <xref:System.IO.Compression.GZipStream> i <xref:System.IO.Compression.DeflateStream> klasy do kompresji i dekompresji danych.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-126">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="8dbf3-127">Używają tego samego algorytmu kompresji.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-127">They use the same compression algorithm.</span></span> <span data-ttu-id="8dbf3-128">Można zdekompresować <xref:System.IO.Compression.GZipStream> obiektów, które są zapisywane w *.gz* plików przy użyciu wielu popularnych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="8dbf3-128">You can decompress <xref:System.IO.Compression.GZipStream> objects that are written to a *.gz* file by using many common tools.</span></span> <span data-ttu-id="8dbf3-129">Poniższy przykład pokazuje, jak kompresję i dekompresję katalog plików za pomocą <xref:System.IO.Compression.GZipStream> klasy:</span><span class="sxs-lookup"><span data-stu-id="8dbf3-129">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="8dbf3-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8dbf3-130">See also</span></span>

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [<span data-ttu-id="8dbf3-131">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="8dbf3-131">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
