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
ms.openlocfilehash: 5aa25e265ed6ffb613e9916414c6f2335a4aaf57
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159380"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="16623-102">Instrukcje: kompresowanie i wyodrębnianie plików</span><span class="sxs-lookup"><span data-stu-id="16623-102">How to: Compress and extract files</span></span>

<span data-ttu-id="16623-103">Przestrzeń nazw <xref:System.IO.Compression> zawiera następujące typy służące do kompresowania i dekompresowania plików i strumieni.</span><span class="sxs-lookup"><span data-stu-id="16623-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="16623-104">Możesz również użyć tych typów do odczytu i modyfikacji zawartości skompresowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="16623-104">You can also use these types to read and modify the contents of a compressed file.</span></span>

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="16623-105">W poniższych przykładach przedstawiono niektóre operacje, które można wykonywać przy użyciu skompresowanych plików.</span><span class="sxs-lookup"><span data-stu-id="16623-105">The following examples show some of the operations you can perform with compressed files.</span></span>

## <a name="example-1-create-and-extract-a-zip-file"></a><span data-ttu-id="16623-106">Przykład 1: Tworzenie i Wyodrębnianie pliku zip</span><span class="sxs-lookup"><span data-stu-id="16623-106">Example 1: Create and extract a .zip file</span></span>

<span data-ttu-id="16623-107">Poniższy przykład pokazuje, jak utworzyć i wyodrębnić skompresowany plik *zip* przy użyciu klasy <xref:System.IO.Compression.ZipFile>.</span><span class="sxs-lookup"><span data-stu-id="16623-107">The following example shows how to create and extract a compressed *.zip* file by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="16623-108">Przykład kompresuje zawartość folderu do nowego pliku *zip* , a następnie wyodrębnia plik zip do nowego folderu.</span><span class="sxs-lookup"><span data-stu-id="16623-108">The example compresses the contents of a folder into a new *.zip* file, and then extracts the zip to a new folder.</span></span>

<span data-ttu-id="16623-109">Aby uruchomić przykład, należy utworzyć folder *startowy* w folderze programu i wypełnić go plikami do pliku zip.</span><span class="sxs-lookup"><span data-stu-id="16623-109">To run the sample, create a *start* folder in your program folder and populate it with files to zip.</span></span>

<span data-ttu-id="16623-110">Jeśli zostanie wyświetlony błąd kompilacji "nazwa" ZipFile "nie istnieje w bieżącym kontekście," Dodaj odwołanie do zestawu `System.IO.Compression.FileSystem` do projektu.</span><span class="sxs-lookup"><span data-stu-id="16623-110">If you get the build error "The name 'ZipFile' does not exist in the current context," add a reference to the `System.IO.Compression.FileSystem` assembly to your project.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a><span data-ttu-id="16623-111">Przykład 2: Wyodrębnienie określonych rozszerzeń plików</span><span class="sxs-lookup"><span data-stu-id="16623-111">Example 2: Extract specific file extensions</span></span>

<span data-ttu-id="16623-112">Następny przykład wykonuje iterację zawartości istniejącego pliku *. zip* i wyodrębnia pliki z rozszerzeniem *. txt* .</span><span class="sxs-lookup"><span data-stu-id="16623-112">The next example iterates through the contents of an existing *.zip* file and extracts files that have a *.txt* extension.</span></span> <span data-ttu-id="16623-113">Używa klasy <xref:System.IO.Compression.ZipArchive>, aby uzyskać dostęp do pliku zip, a Klasa <xref:System.IO.Compression.ZipArchiveEntry> do inspekcji poszczególnych wpisów.</span><span class="sxs-lookup"><span data-stu-id="16623-113">It uses the <xref:System.IO.Compression.ZipArchive> class to access the zip, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries.</span></span> <span data-ttu-id="16623-114">Metoda rozszerzenia <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> dla obiektu <xref:System.IO.Compression.ZipArchiveEntry> jest dostępna w klasie <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="16623-114">The extension method <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> for the <xref:System.IO.Compression.ZipArchiveEntry> object is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span>

<span data-ttu-id="16623-115">Aby uruchomić przykład, Umieść plik *zip* o nazwie *Result. zip* w folderze programu.</span><span class="sxs-lookup"><span data-stu-id="16623-115">To run the sample, place a *.zip* file called *result.zip* in your program folder.</span></span> <span data-ttu-id="16623-116">Po wyświetleniu monitu podaj nazwę folderu do wyodrębnienia.</span><span class="sxs-lookup"><span data-stu-id="16623-116">When prompted, provide a folder name to extract to.</span></span>

<span data-ttu-id="16623-117">Jeśli zostanie wyświetlony błąd kompilacji "nazwa" ZipFile "nie istnieje w bieżącym kontekście," Dodaj odwołanie do zestawu `System.IO.Compression.FileSystem` do projektu.</span><span class="sxs-lookup"><span data-stu-id="16623-117">If you get the build error "The name 'ZipFile' does not exist in the current context," add a reference to the `System.IO.Compression.FileSystem` assembly to your project.</span></span>

<span data-ttu-id="16623-118">Jeśli zostanie wyświetlony komunikat o błędzie "typ" ZipArchive "jest zdefiniowany w zestawie, do którego nie odwołuje się odwołanie," Dodaj odwołanie do zestawu `System.IO.Compression` do projektu.</span><span class="sxs-lookup"><span data-stu-id="16623-118">If you get the error "The type 'ZipArchive' is defined in an assembly that is not referenced," add a reference to the `System.IO.Compression` assembly to your project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="16623-119">Podczas rozpakowywania plików należy wyszukać złośliwe ścieżki plików, które mogą wyjść z katalogu, w którym się znajdujesz.</span><span class="sxs-lookup"><span data-stu-id="16623-119">When unzipping files, you must look for malicious file paths, which can escape out of the directory you unzip into.</span></span> <span data-ttu-id="16623-120">Jest to tzw. atak przechodzenia do lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="16623-120">This is known as a path traversal attack.</span></span> <span data-ttu-id="16623-121">W poniższym przykładzie pokazano, jak wyszukiwać złośliwe ścieżki plików i zapewniać bezpieczną metodę rozpakowania.</span><span class="sxs-lookup"><span data-stu-id="16623-121">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a><span data-ttu-id="16623-122">Przykład 3: Dodaj plik do istniejącego pliku zip</span><span class="sxs-lookup"><span data-stu-id="16623-122">Example 3: Add a file to an existing zip</span></span>

<span data-ttu-id="16623-123">Poniższy przykład używa klasy <xref:System.IO.Compression.ZipArchive>, aby uzyskać dostęp do istniejącego pliku *. zip* i dodaje do niego plik.</span><span class="sxs-lookup"><span data-stu-id="16623-123">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing *.zip* file, and adds a file to it.</span></span> <span data-ttu-id="16623-124">Nowy plik zostanie skompresowany po dodaniu go do istniejącego pliku zip.</span><span class="sxs-lookup"><span data-stu-id="16623-124">The new file gets compressed when you add it to the existing zip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a><span data-ttu-id="16623-125">Przykład 4: kompresowanie i dekompresowanie plików. gz</span><span class="sxs-lookup"><span data-stu-id="16623-125">Example 4: Compress and decompress .gz files</span></span>

<span data-ttu-id="16623-126">Można również użyć klas <xref:System.IO.Compression.GZipStream> i <xref:System.IO.Compression.DeflateStream> do kompresowania i dekompresowania danych.</span><span class="sxs-lookup"><span data-stu-id="16623-126">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="16623-127">Korzystają one z tego samego algorytmu kompresji.</span><span class="sxs-lookup"><span data-stu-id="16623-127">They use the same compression algorithm.</span></span> <span data-ttu-id="16623-128">Można zdekompresować <xref:System.IO.Compression.GZipStream> obiektów, które są zapisywane w pliku *GZ* przy użyciu wielu popularnych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="16623-128">You can decompress <xref:System.IO.Compression.GZipStream> objects that are written to a *.gz* file by using many common tools.</span></span> <span data-ttu-id="16623-129">Poniższy przykład przedstawia sposób kompresowania i dekompresowania katalogu plików przy użyciu klasy <xref:System.IO.Compression.GZipStream>:</span><span class="sxs-lookup"><span data-stu-id="16623-129">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="16623-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16623-130">See also</span></span>

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [<span data-ttu-id="16623-131">We/wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="16623-131">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
