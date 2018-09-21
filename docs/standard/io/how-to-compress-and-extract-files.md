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
ms.openlocfilehash: 669936d15cfe1ea125ed36ffdfcfd093b6aacbe1
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46530875"
---
# <a name="how-to-compress-and-extract-files"></a>Porady: kompresowanie i wyodrębnianie plików

<xref:System.IO.Compression> Przestrzeń nazw zawiera następujące typy do kompresowania i dekompresowania plików i strumieni. Można również używać tych typów może odczytywać i modyfikować zawartość skompresowanego pliku:

- <xref:System.IO.Compression.ZipFile>

- <xref:System.IO.Compression.ZipArchive>

- <xref:System.IO.Compression.ZipArchiveEntry>

- <xref:System.IO.Compression.DeflateStream>

- <xref:System.IO.Compression.GZipStream>

W poniższych przykładach pokazano niektóre z funkcji, które może wykonywać Pracując ze skompresowanymi plikami.

## <a name="example-1---create-and-extract-a-zip-file"></a>Przykład 1 — Tworzenie i Wyodrębnij plik zip

Poniższy przykład pokazuje, jak utworzyć i Wyodrębnij skompresowany plik, który ma rozszerzenie nazwy pliku zip przy użyciu <xref:System.IO.Compression.ZipFile> klasy. Jego kompresuje zawartość folderu do nowego pliku zip, a następnie wyodrębnia zawartość do nowego folderu. Aby użyć <xref:System.IO.Compression.ZipFile> klasy, należy odwołać `System.IO.Compression.FileSystem` zestawu w projekcie.

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2---extract-specific-file-extensions"></a>Przykład 2 - Extract określonych rozszerzeń plików

Następny przykład pokazuje, jak wykonać iterację zawartość istniejącego pliku zip i Wyodrębnij pliki z rozszerzeniem txt. Używa ona <xref:System.IO.Compression.ZipArchive> klasy w celu dostępu do istniejącego pliku zip, a <xref:System.IO.Compression.ZipArchiveEntry> klasy, aby sprawdzić poszczególne wpisy w pliku skompresowanym. Używa metody rozszerzenia (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) dla <xref:System.IO.Compression.ZipArchiveEntry> obiektu. Metoda rozszerzenia jest dostępna w <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> klasy. Aby użyć <xref:System.IO.Compression.ZipFileExtensions> klasy, należy odwołać `System.IO.Compression.FileSystem` zestawu w projekcie.

> [!IMPORTANT]
> Podczas rozpakowywania plików, możesz wyszukiwać ścieżki złośliwych plików, które można udosłownić się katalogu, w którym chcesz Rozpakuj do. Jest to znane jako atak przechodzenia przez ścieżkę.

Poniższy przykład pokazuje, jak sprawdzić, czy ścieżki złośliwych plików i zapewnia bezpieczny sposób, aby rozpakować:

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3---add-a-new-file-to-an-existing-zip-file"></a>Przykład 3 - Dodaj nowy plik do istniejącego pliku zip

W poniższym przykładzie użyto <xref:System.IO.Compression.ZipArchive> klasy dostępu do istniejącego pliku zip, a następnie dodaje nowy plik do skompresowanego pliku. Nowy plik pobiera skompresowane, dodanie do istniejącego pliku zip.

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4---compress-and-decompress-a-directory-of-gz-files"></a>Przykład 4 - kompresji i dekompresji katalog plików .gz

Można również użyć <xref:System.IO.Compression.GZipStream> i <xref:System.IO.Compression.DeflateStream> klasy do kompresji i dekompresji danych. Używają tego samego algorytmu kompresji. Skompresowany <xref:System.IO.Compression.GZipStream> obiektów, które są zapisywane w pliku, który ma rozszerzenie .gz może być dekompresowane przy użyciu wielu popularnych narzędzi, oprócz metod dostarczonych przez <xref:System.IO.Compression.GZipStream>. Poniższy przykład pokazuje, jak kompresję i dekompresję katalog plików za pomocą <xref:System.IO.Compression.GZipStream> klasy:

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a>Zobacz także

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [We/Wy plików i strumieni](../../../docs/standard/io/index.md)
