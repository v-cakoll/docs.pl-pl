---
title: 'Porady: kompresowanie i wyodrębnianie plików'
ms.date: 06/06/2018
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
ms.openlocfilehash: f045f2137d65a66ac025c81e58e66c96bcaca031
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827127"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="f2b44-102">Porady: kompresowanie i wyodrębnianie plików</span><span class="sxs-lookup"><span data-stu-id="f2b44-102">How to: Compress and extract files</span></span>

<span data-ttu-id="f2b44-103"><xref:System.IO.Compression> Przestrzeń nazw zawiera następujące typy kompresji i dekompresji plików i strumieni.</span><span class="sxs-lookup"><span data-stu-id="f2b44-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="f2b44-104">Można również używać tych typów może odczytywać i modyfikować zawartość skompresowanego pliku:</span><span class="sxs-lookup"><span data-stu-id="f2b44-104">You can also use these types to read and modify the contents of a compressed file:</span></span>

- <xref:System.IO.Compression.ZipFile>

- <xref:System.IO.Compression.ZipArchive>

- <xref:System.IO.Compression.ZipArchiveEntry>

- <xref:System.IO.Compression.DeflateStream>

- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="f2b44-105">W poniższych przykładach pokazano niektóre funkcje, które można wykonać podczas pracy z skompresowane pliki.</span><span class="sxs-lookup"><span data-stu-id="f2b44-105">The following examples show some of the functions you can perform when working with compressed files.</span></span>

## <a name="example-1---create-and-extract-a-zip-file"></a><span data-ttu-id="f2b44-106">Przykład 1 — Tworzenie i Wyodrębnij plik zip</span><span class="sxs-lookup"><span data-stu-id="f2b44-106">Example 1 - Create and extract a .zip file</span></span>

<span data-ttu-id="f2b44-107">Poniższy przykład przedstawia sposób tworzenia i Wyodrębnij skompresowany plik z rozszerzeniem .zip przy użyciu <xref:System.IO.Compression.ZipFile> klasy.</span><span class="sxs-lookup"><span data-stu-id="f2b44-107">The following example shows how to create and extract a compressed file that has a .zip file name extension by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="f2b44-108">Kompresuje zawartość folderu do nowego pliku zip, a następnie wyodrębnia zawartość do nowego folderu.</span><span class="sxs-lookup"><span data-stu-id="f2b44-108">It compresses the contents of a folder into a new .zip file and then extracts that content to a new folder.</span></span> <span data-ttu-id="f2b44-109">Aby użyć <xref:System.IO.Compression.ZipFile> klasy, należy wskazać `System.IO.Compression.FileSystem` zestawu w projekcie.</span><span class="sxs-lookup"><span data-stu-id="f2b44-109">To use the <xref:System.IO.Compression.ZipFile> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2---extract-specific-file-extensions"></a><span data-ttu-id="f2b44-110">Przykład 2 - Extract określonych rozszerzeń plików</span><span class="sxs-lookup"><span data-stu-id="f2b44-110">Example 2 - Extract specific file extensions</span></span>

<span data-ttu-id="f2b44-111">Kolejnym przykładzie pokazano, jak do iteracji zawartość istniejący plik zip i Wyodrębnij pliki z rozszerzeniem txt.</span><span class="sxs-lookup"><span data-stu-id="f2b44-111">The next example shows how to iterate through the contents of an existing .zip file and extract files that have a .txt extension.</span></span> <span data-ttu-id="f2b44-112">Używa <xref:System.IO.Compression.ZipArchive> klasę, aby uzyskać dostęp do istniejącego pliku .zip i <xref:System.IO.Compression.ZipArchiveEntry> klasy do zbadania poszczególne pozycje w skompresowany plik.</span><span class="sxs-lookup"><span data-stu-id="f2b44-112">It uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries in the compressed file.</span></span> <span data-ttu-id="f2b44-113">Używa metody rozszerzenia (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) dla <xref:System.IO.Compression.ZipArchiveEntry> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f2b44-113">It uses an extension method (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) for the <xref:System.IO.Compression.ZipArchiveEntry> object.</span></span> <span data-ttu-id="f2b44-114">Metody rozszerzenia jest dostępna w <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="f2b44-114">The extension method is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="f2b44-115">Aby użyć <xref:System.IO.Compression.ZipFileExtensions> klasy, należy wskazać `System.IO.Compression.FileSystem` zestawu w projekcie.</span><span class="sxs-lookup"><span data-stu-id="f2b44-115">To use the <xref:System.IO.Compression.ZipFileExtensions> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f2b44-116">Gdy rozpakować pliki, możesz wyszukiwać ścieżki złośliwych plików, które można wprowadzić limit katalogu miejscu Rozpakuj do.</span><span class="sxs-lookup"><span data-stu-id="f2b44-116">When unzipping files, you must look for malicious file paths which can escape out of the directory where you want to unzip into.</span></span> <span data-ttu-id="f2b44-117">Jest to nazywane atak przechodzenie ścieżki.</span><span class="sxs-lookup"><span data-stu-id="f2b44-117">This is known as a path traversal attack.</span></span>

<span data-ttu-id="f2b44-118">W poniższym przykładzie pokazano, jak i sprawdź, czy ścieżki złośliwych plików i zapewnia bezpieczny sposób, aby rozpakować:</span><span class="sxs-lookup"><span data-stu-id="f2b44-118">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip:</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3---add-a-new-file-to-an-existing-zip-file"></a><span data-ttu-id="f2b44-119">Przykład 3 - Dodaj nowy plik do istniejącego pliku zip</span><span class="sxs-lookup"><span data-stu-id="f2b44-119">Example 3 - Add a new file to an existing .zip file</span></span>

<span data-ttu-id="f2b44-120">W poniższym przykładzie użyto <xref:System.IO.Compression.ZipArchive> klasy dostęp do istniejącego pliku zip, a następnie dodaje nowy plik do skompresowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="f2b44-120">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and adds a new file to the compressed file.</span></span> <span data-ttu-id="f2b44-121">Nowy plik pobiera skompresowane po dodaniu go do istniejącego pliku zip.</span><span class="sxs-lookup"><span data-stu-id="f2b44-121">The new file gets compressed when you add it to the existing .zip file.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4---compress-and-decompress-a-directory-of-gz-files"></a><span data-ttu-id="f2b44-122">Przykład 4 - kompresji i dekompresji katalogu plików .gz</span><span class="sxs-lookup"><span data-stu-id="f2b44-122">Example 4 - Compress and decompress a directory of .gz files</span></span>

<span data-ttu-id="f2b44-123">Można również użyć <xref:System.IO.Compression.GZipStream> i <xref:System.IO.Compression.DeflateStream> klasy do kompresji i dekompresji danych.</span><span class="sxs-lookup"><span data-stu-id="f2b44-123">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="f2b44-124">Używają tego samego algorytmu kompresji.</span><span class="sxs-lookup"><span data-stu-id="f2b44-124">They use the same compression algorithm.</span></span> <span data-ttu-id="f2b44-125">Skompresowane <xref:System.IO.Compression.GZipStream> obiektów, które są zapisywane do pliku, który ma rozszerzenie .gz można zdekompresować za pomocą wielu typowych narzędzi oprócz metody udostępniane przez <xref:System.IO.Compression.GZipStream>.</span><span class="sxs-lookup"><span data-stu-id="f2b44-125">Compressed <xref:System.IO.Compression.GZipStream> objects that are written to a file that has an extension of .gz can be decompressed by using many common tools in addition to the methods provided by <xref:System.IO.Compression.GZipStream>.</span></span> <span data-ttu-id="f2b44-126">Poniższy przykład przedstawia sposób kompresji i dekompresji katalog plików przy użyciu <xref:System.IO.Compression.GZipStream> klasy:</span><span class="sxs-lookup"><span data-stu-id="f2b44-126">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="f2b44-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2b44-127">See also</span></span>

<xref:System.IO.Compression.ZipArchive>  
<xref:System.IO.Compression.ZipFile>  
<xref:System.IO.Compression.ZipArchiveEntry>  
<xref:System.IO.Compression.DeflateStream>  
<xref:System.IO.Compression.GZipStream>  
[<span data-ttu-id="f2b44-128">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="f2b44-128">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
