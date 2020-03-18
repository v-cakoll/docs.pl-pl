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
# <a name="how-to-compress-and-extract-files"></a>Jak: Kompresować i wyodrębniać pliki

Obszar <xref:System.IO.Compression> nazw zawiera następujące typy kompresji i dekompresji plików i strumieni. Za pomocą tych typów można również odczytywać i modyfikować zawartość skompresowanego pliku.

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

W poniższych przykładach przedstawiono niektóre operacje, które można wykonać z skompresowanymi plikami.

## <a name="example-1-create-and-extract-a-zip-file"></a>Przykład 1: Tworzenie i wyodrębnianie pliku zip

W poniższym przykładzie pokazano, jak utworzyć i wyodrębnić skompresowany plik *zip* przy użyciu <xref:System.IO.Compression.ZipFile> klasy. Przykład kompresuje zawartość folderu do nowego pliku *zip,* a następnie wyodrębnia zip do nowego folderu.

Aby uruchomić przykład, utwórz folder *startowy* w folderze programu i wypełnij go plikami do zip.

Jeśli pojawi się błąd kompilacji "Nazwa "ZipFile" nie istnieje w bieżącym `System.IO.Compression.FileSystem` kontekście," dodaj odwołanie do zestawu do projektu.

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a>Przykład 2: Wyodrębnianie określonych rozszerzeń plików

Następny przykład iteforuje zawartość istniejącego pliku *zip* i wyodrębnia pliki, które mają rozszerzenie *txt.* Używa klasy, <xref:System.IO.Compression.ZipArchive> aby uzyskać dostęp <xref:System.IO.Compression.ZipArchiveEntry> do zip i klasy do kontroli poszczególnych wpisów. Metoda <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> rozszerzenia dla <xref:System.IO.Compression.ZipArchiveEntry> obiektu jest <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> dostępna w klasie.

Aby uruchomić próbkę, umieść plik *zip* o nazwie *result.zip* w folderze programu. Po wyświetleniu monitu podaj nazwę folderu, do który chcesz wyodrębnić.

Jeśli pojawi się błąd kompilacji "Nazwa "ZipFile" nie istnieje w bieżącym `System.IO.Compression.FileSystem` kontekście," dodaj odwołanie do zestawu do projektu.

Jeśli pojawi się błąd "Typ "ZipArchive" jest zdefiniowany w zestawie, do `System.IO.Compression` którego nie odwołuje się", dodaj odwołanie do zestawu do projektu.

> [!IMPORTANT]
> Podczas rozpakowywania plików należy szukać złośliwych ścieżek plików, które mogą wydostać się z katalogu, do którego rozpakujesz. Jest to nazywane atakiem przechodzenia ścieżki. W poniższym przykładzie pokazano, jak sprawdzić, czy nie ma złośliwych ścieżek plików i zapewnia bezpieczny sposób rozpakowywania.

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a>Przykład 3: Dodawanie pliku do istniejącego zamka błyskawicznego

W poniższym <xref:System.IO.Compression.ZipArchive> przykładzie użyto klasy, aby uzyskać dostęp do istniejącego pliku *zip* i dodaje plik do niego. Nowy plik zostanie skompresowany po dodaniu go do istniejącego zip.

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a>Przykład 4: Kompresowanie i dekompresowanie plików .gz

Można również użyć <xref:System.IO.Compression.GZipStream> <xref:System.IO.Compression.DeflateStream> i klas do kompresji i dekompresji danych. Używają tego samego algorytmu kompresji. Można dekompresować <xref:System.IO.Compression.GZipStream> obiekty zapisane w pliku *gz* przy użyciu wielu typowych narzędzi. W poniższym przykładzie pokazano, jak kompresować i <xref:System.IO.Compression.GZipStream> dekompresować katalog plików przy użyciu klasy:

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a>Zobacz też

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [Plik i strumień we/wy](../../../docs/standard/io/index.md)
