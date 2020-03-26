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
# <a name="how-to-compress-and-extract-files"></a>Jak: Kompresowanie i wyodrębnianie plików

Obszar <xref:System.IO.Compression> nazw zawiera następujące typy kompresji i dekompresji plików i strumieni. Za pomocą tych typów można również odczytać i zmodyfikować zawartość skompresowanego pliku.

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

Poniższe przykłady pokazują niektóre operacje, które można wykonać za pomocą skompresowanych plików. Te przykłady wymagają następujących pakietów NuGet, które mają zostać dodane do projektu:

- [System.IO.Kompresja](https://www.nuget.org/packages/System.IO.Compression)
- [Plik System.IO.Compression.ZipFile](https://www.nuget.org/packages/System.IO.Compression.ZipFile)

Jeśli używasz programu .NET Framework, dodaj odwołania do tych dwóch bibliotek do projektu:

- `System.IO.Compression`
- `System.IO.Compression.FileSystem`

## <a name="example-1-create-and-extract-a-zip-file"></a>Przykład 1: Tworzenie i wyodrębnianie pliku zip

W poniższym przykładzie pokazano, jak utworzyć i wyodrębnić skompresowany plik *zip* przy użyciu <xref:System.IO.Compression.ZipFile> klasy. W przykładzie zawartość folderu jest kompresowany do nowego pliku *zip,* a następnie wyodrębnia go do nowego folderu.

Aby uruchomić przykład, utwórz folder *startowy* w folderze programu i wypełnij go plikami do zip.

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a>Przykład 2: Wyodrębnianie określonych rozszerzeń plików

Następny przykład iteruje zawartość istniejącego pliku *zip* i wyodrębnia pliki, które mają rozszerzenie *txt.* Używa klasy, <xref:System.IO.Compression.ZipArchive> aby uzyskać dostęp do <xref:System.IO.Compression.ZipArchiveEntry> zip i klasy do kontroli poszczególnych wpisów. Metoda <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> rozszerzenia obiektu <xref:System.IO.Compression.ZipArchiveEntry> jest dostępna <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> w klasie.

Aby uruchomić próbkę, umieść plik *zip* o nazwie *result.zip* w folderze programu. Po wyświetleniu monitu podaj nazwę folderu, do którym chcesz wyodrębnić.

> [!IMPORTANT]
> Podczas rozpakowywania plików należy szukać złośliwych ścieżek plików, które mogą wydostać się z katalogu, do którego się rozpakujesz. Jest to znane jako atak przechodzenia ścieżki. W poniższym przykładzie pokazano, jak sprawdzić, czy złośliwe ścieżki plików i zapewnia bezpieczny sposób rozpakowania.

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a>Przykład 3: Dodawanie pliku do istniejącego kodu błyskawicznego

Poniższy przykład używa <xref:System.IO.Compression.ZipArchive> klasy, aby uzyskać dostęp do istniejącego pliku *zip* i dodaje do niego plik. Nowy plik zostanie skompresowany po dodaniu go do istniejącego kodu błyskawicznego.

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a>Przykład 4: Kompresowanie i dekompresja plików gz

Można również użyć <xref:System.IO.Compression.GZipStream> <xref:System.IO.Compression.DeflateStream> i klas do kompresji i dekompresji danych. Używają tego samego algorytmu kompresji. Można dekompresować <xref:System.IO.Compression.GZipStream> obiekty zapisywane w pliku *gz* przy użyciu wielu typowych narzędzi. W poniższym przykładzie pokazano, jak skompresować i <xref:System.IO.Compression.GZipStream> dekompresować katalog plików przy użyciu klasy:

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a>Zobacz też

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [We/wy plików i strumieni](../../../docs/standard/io/index.md)
