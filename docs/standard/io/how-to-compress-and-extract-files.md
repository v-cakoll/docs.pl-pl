---
title: "Porady: kompresowanie i wyodrębnianie plików"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 22a95ce18b602d4e329499c5d36557213e08a8b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="91caf-102">Porady: kompresowanie i wyodrębnianie plików</span><span class="sxs-lookup"><span data-stu-id="91caf-102">How to: Compress and Extract Files</span></span>
<span data-ttu-id="91caf-103"><xref:System.IO.Compression> Przestrzeń nazw zawiera następujące typy kompresji i dekompresji plików i strumieni.</span><span class="sxs-lookup"><span data-stu-id="91caf-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="91caf-104">Można również używać tych typów może odczytywać i modyfikować zawartość skompresowanego pliku:</span><span class="sxs-lookup"><span data-stu-id="91caf-104">You can also use these types to read and modify the contents of a compressed file:</span></span>  
  
-   <xref:System.IO.Compression.ZipFile>  
  
-   <xref:System.IO.Compression.ZipArchive>  
  
-   <xref:System.IO.Compression.ZipArchiveEntry>  
  
-   <xref:System.IO.Compression.DeflateStream>  
  
-   <xref:System.IO.Compression.GZipStream>  
  
 <span data-ttu-id="91caf-105">W poniższych przykładach pokazano niektóre funkcje, które można wykonać podczas pracy z skompresowane pliki.</span><span class="sxs-lookup"><span data-stu-id="91caf-105">The following examples show some of the functions you can perform when working with compressed files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91caf-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="91caf-106">Example</span></span>  
 <span data-ttu-id="91caf-107">W tym przykładzie pokazano, jak utworzyć i Wyodrębnij skompresowany plik z rozszerzeniem .zip przy użyciu <xref:System.IO.Compression.ZipFile> klasy.</span><span class="sxs-lookup"><span data-stu-id="91caf-107">This example shows how to create and extract a compressed file that has a .zip file name extension by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="91caf-108">Kompresuje zawartość folderu do nowego pliku zip, a następnie wyodrębnia zawartość do nowego folderu.</span><span class="sxs-lookup"><span data-stu-id="91caf-108">It compresses the contents of a folder into a new .zip file and then extracts that content to a new folder.</span></span> <span data-ttu-id="91caf-109">Aby użyć <xref:System.IO.Compression.ZipFile> klasy, należy wskazać `System.IO.Compression.FileSystem` zestawu w projekcie.</span><span class="sxs-lookup"><span data-stu-id="91caf-109">To use the <xref:System.IO.Compression.ZipFile> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="91caf-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="91caf-110">Example</span></span>  
 <span data-ttu-id="91caf-111">Kolejnym przykładzie pokazano, jak do iteracji zawartość istniejący plik zip i Wyodrębnij pliki z rozszerzeniem txt.</span><span class="sxs-lookup"><span data-stu-id="91caf-111">The next example shows how to iterate through the contents of an existing .zip file and extract files that have a .txt extension.</span></span> <span data-ttu-id="91caf-112">Używa <xref:System.IO.Compression.ZipArchive> klasę, aby uzyskać dostęp do istniejącego pliku .zip i <xref:System.IO.Compression.ZipArchiveEntry> klasy do zbadania poszczególne pozycje w skompresowany plik.</span><span class="sxs-lookup"><span data-stu-id="91caf-112">It uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries in the compressed file.</span></span> <span data-ttu-id="91caf-113">Używa metody rozszerzenia (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) dla <xref:System.IO.Compression.ZipArchiveEntry> obiektu.</span><span class="sxs-lookup"><span data-stu-id="91caf-113">It uses an extension method (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) for the <xref:System.IO.Compression.ZipArchiveEntry> object.</span></span> <span data-ttu-id="91caf-114">Metody rozszerzenia jest dostępna w <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="91caf-114">The extension method is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="91caf-115">Aby użyć <xref:System.IO.Compression.ZipFileExtensions> klasy, należy wskazać `System.IO.Compression.FileSystem` zestawu w projekcie.</span><span class="sxs-lookup"><span data-stu-id="91caf-115">To use the <xref:System.IO.Compression.ZipFileExtensions> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="91caf-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="91caf-116">Example</span></span>  
 <span data-ttu-id="91caf-117">W następnym przykładzie użyto <xref:System.IO.Compression.ZipArchive> klasy dostęp do istniejącego pliku zip, a następnie dodaje nowy plik do skompresowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="91caf-117">The next example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and adds a new file to the compressed file.</span></span> <span data-ttu-id="91caf-118">Nowy plik pobiera skompresowane po dodaniu go do istniejącego pliku zip.</span><span class="sxs-lookup"><span data-stu-id="91caf-118">The new file gets compressed when you add it to the existing .zip file.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="91caf-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="91caf-119">Example</span></span>  
 <span data-ttu-id="91caf-120">Można również użyć <xref:System.IO.Compression.GZipStream> i <xref:System.IO.Compression.DeflateStream> klasy do kompresji i dekompresji danych.</span><span class="sxs-lookup"><span data-stu-id="91caf-120">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="91caf-121">Używają tego samego algorytmu kompresji.</span><span class="sxs-lookup"><span data-stu-id="91caf-121">They use the same compression algorithm.</span></span> <span data-ttu-id="91caf-122">Skompresowane <xref:System.IO.Compression.GZipStream> obiektów, które są zapisywane do pliku, który ma rozszerzenie .gz można zdekompresować za pomocą wielu typowych narzędzi oprócz metody udostępniane przez <xref:System.IO.Compression.GZipStream>.</span><span class="sxs-lookup"><span data-stu-id="91caf-122">Compressed <xref:System.IO.Compression.GZipStream> objects that are written to a file that has an extension of .gz can be decompressed by using many common tools in addition to the methods provided by <xref:System.IO.Compression.GZipStream>.</span></span> <span data-ttu-id="91caf-123">W tym przykładzie pokazano, jak kompresji i dekompresji katalog plików przy użyciu <xref:System.IO.Compression.GZipStream> klasy.</span><span class="sxs-lookup"><span data-stu-id="91caf-123">This example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class.</span></span>  
  
 [!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
 [!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="91caf-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="91caf-124">See Also</span></span>  
 <xref:System.IO.Compression.ZipArchive>  
 <xref:System.IO.Compression.ZipFile>  
 <xref:System.IO.Compression.ZipArchiveEntry>  
 <xref:System.IO.Compression.DeflateStream>  
 <xref:System.IO.Compression.GZipStream>  
 [<span data-ttu-id="91caf-125">Plik i strumienia I-O</span><span class="sxs-lookup"><span data-stu-id="91caf-125">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
