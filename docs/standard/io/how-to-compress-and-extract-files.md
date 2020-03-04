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
# <a name="how-to-compress-and-extract-files"></a>Instrukcje: kompresowanie i wyodrębnianie plików

Przestrzeń nazw <xref:System.IO.Compression> zawiera następujące typy służące do kompresowania i dekompresowania plików i strumieni. Możesz również użyć tych typów do odczytu i modyfikacji zawartości skompresowanego pliku.

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

W poniższych przykładach przedstawiono niektóre operacje, które można wykonywać przy użyciu skompresowanych plików.

## <a name="example-1-create-and-extract-a-zip-file"></a>Przykład 1: Tworzenie i Wyodrębnianie pliku zip

Poniższy przykład pokazuje, jak utworzyć i wyodrębnić skompresowany plik *zip* przy użyciu klasy <xref:System.IO.Compression.ZipFile>. Przykład kompresuje zawartość folderu do nowego pliku *zip* , a następnie wyodrębnia plik zip do nowego folderu.

Aby uruchomić przykład, należy utworzyć folder *startowy* w folderze programu i wypełnić go plikami do pliku zip.

Jeśli zostanie wyświetlony błąd kompilacji "nazwa" ZipFile "nie istnieje w bieżącym kontekście," Dodaj odwołanie do zestawu `System.IO.Compression.FileSystem` do projektu.

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a>Przykład 2: Wyodrębnienie określonych rozszerzeń plików

Następny przykład wykonuje iterację zawartości istniejącego pliku *. zip* i wyodrębnia pliki z rozszerzeniem *. txt* . Używa klasy <xref:System.IO.Compression.ZipArchive>, aby uzyskać dostęp do pliku zip, a Klasa <xref:System.IO.Compression.ZipArchiveEntry> do inspekcji poszczególnych wpisów. Metoda rozszerzenia <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> dla obiektu <xref:System.IO.Compression.ZipArchiveEntry> jest dostępna w klasie <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType>.

Aby uruchomić przykład, Umieść plik *zip* o nazwie *Result. zip* w folderze programu. Po wyświetleniu monitu podaj nazwę folderu do wyodrębnienia.

Jeśli zostanie wyświetlony błąd kompilacji "nazwa" ZipFile "nie istnieje w bieżącym kontekście," Dodaj odwołanie do zestawu `System.IO.Compression.FileSystem` do projektu.

Jeśli zostanie wyświetlony komunikat o błędzie "typ" ZipArchive "jest zdefiniowany w zestawie, do którego nie odwołuje się odwołanie," Dodaj odwołanie do zestawu `System.IO.Compression` do projektu.

> [!IMPORTANT]
> Podczas rozpakowywania plików należy wyszukać złośliwe ścieżki plików, które mogą wyjść z katalogu, w którym się znajdujesz. Jest to tzw. atak przechodzenia do lokalizacji. W poniższym przykładzie pokazano, jak wyszukiwać złośliwe ścieżki plików i zapewniać bezpieczną metodę rozpakowania.

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a>Przykład 3: Dodaj plik do istniejącego pliku zip

Poniższy przykład używa klasy <xref:System.IO.Compression.ZipArchive>, aby uzyskać dostęp do istniejącego pliku *. zip* i dodaje do niego plik. Nowy plik zostanie skompresowany po dodaniu go do istniejącego pliku zip.

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a>Przykład 4: kompresowanie i dekompresowanie plików. gz

Można również użyć klas <xref:System.IO.Compression.GZipStream> i <xref:System.IO.Compression.DeflateStream> do kompresowania i dekompresowania danych. Korzystają one z tego samego algorytmu kompresji. Można zdekompresować <xref:System.IO.Compression.GZipStream> obiektów, które są zapisywane w pliku *GZ* przy użyciu wielu popularnych narzędzi. Poniższy przykład przedstawia sposób kompresowania i dekompresowania katalogu plików przy użyciu klasy <xref:System.IO.Compression.GZipStream>:

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a>Zobacz też

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [We/wy plików i strumieni](../../../docs/standard/io/index.md)
