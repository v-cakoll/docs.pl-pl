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
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255006"
---
# <a name="how-to-compress-and-extract-files"></a>Instrukcje: Kompresowanie i wyodrębnianie plików

<xref:System.IO.Compression> Przestrzeń nazw zawiera następujące typy do kompresowania i dekompresowania plików i strumieni. Można również użyć tych typów może odczytywać i modyfikować zawartość skompresowanego pliku.

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

W poniższych przykładach pokazano niektóre operacje, które można wykonywać za pomocą skompresowanych plików.

## <a name="example-1-create-and-extract-a-zip-file"></a>Przykład 1: Tworzenie i Wyodrębnij plik zip

Poniższy przykład pokazuje, jak utworzyć i Wyodrębnij skompresowane *zip* plików przy użyciu <xref:System.IO.Compression.ZipFile> klasy. Przykład kompresuje zawartość folderu do nowego *zip* pliku, a następnie wyodrębnia pliku zip do nowego folderu. 

Aby uruchomić przykład, utworzyć *start* folderu w folderze program i wypełnić ją plikami zip. 

Jeśli wystąpi błąd kompilacji "Name"ZipFile"nie istnieje w bieżącym kontekście", Dodaj odwołanie do `System.IO.Compression.FileSystem` zestawu do projektu.

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a>Przykład 2: Wyodrębnianie określonych rozszerzeń plików

Następny przykład wykonuje iterację przez zawartość do istniejącego *zip* plików i wyodrębnienie plików, które mają *.txt* rozszerzenia. Używa ona <xref:System.IO.Compression.ZipArchive> klasy w celu dostępu do pliku zip, a <xref:System.IO.Compression.ZipArchiveEntry> klasy, aby sprawdzić poszczególne wpisy. Metoda rozszerzenia <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> dla <xref:System.IO.Compression.ZipArchiveEntry> obiekt jest dostępny w <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> klasy. 

Aby uruchomić przykład, umieść *zip* pliku o nazwie *result.zip* w folderze program. Po wyświetleniu monitu podaj nazwę folderu, aby wyodrębnić. 

Jeśli wystąpi błąd kompilacji "Name"ZipFile"nie istnieje w bieżącym kontekście", Dodaj odwołanie do `System.IO.Compression.FileSystem` zestawu do projektu.

Jeśli zostanie wyświetlony błąd "Type"Obiekt ZipArchive"jest zdefiniowany w zestawie, który nie odwołuje się" Dodaj odwołanie do `System.IO.Compression` zestawu do projektu. 

> [!IMPORTANT]
> Podczas rozpakowywania plików, możesz wyszukiwać ścieżki złośliwych plików, które można udosłownić spoza katalogu w którym Rozpakuj do. Jest to znane jako atak przechodzenia przez ścieżkę. Poniższy przykład pokazuje, jak sprawdzić, czy ścieżki złośliwych plików i zapewnia bezpieczny sposób Rozpakuj go.

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a>Przykład 3: Dodaj plik do istniejącego pliku zip

W poniższym przykładzie użyto <xref:System.IO.Compression.ZipArchive> klasy w celu uzyskania dostępu do istniejącego *zip* pliku i dodaje plik do niego. Nowy plik pobiera skompresowany, gdy zostanie on dodany do istniejącego pliku zip.

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a>Przykład 4: Kompresję i dekompresję plików .gz

Można również użyć <xref:System.IO.Compression.GZipStream> i <xref:System.IO.Compression.DeflateStream> klasy do kompresji i dekompresji danych. Używają tego samego algorytmu kompresji. Można zdekompresować <xref:System.IO.Compression.GZipStream> obiektów, które są zapisywane w *.gz* plików przy użyciu wielu popularnych narzędzi. Poniższy przykład pokazuje, jak kompresję i dekompresję katalog plików za pomocą <xref:System.IO.Compression.GZipStream> klasy:

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a>Zobacz także

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [We/Wy plików i strumieni](../../../docs/standard/io/index.md)
