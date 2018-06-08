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
# <a name="how-to-compress-and-extract-files"></a>Porady: kompresowanie i wyodrębnianie plików

<xref:System.IO.Compression> Przestrzeń nazw zawiera następujące typy kompresji i dekompresji plików i strumieni. Można również używać tych typów może odczytywać i modyfikować zawartość skompresowanego pliku:

- <xref:System.IO.Compression.ZipFile>

- <xref:System.IO.Compression.ZipArchive>

- <xref:System.IO.Compression.ZipArchiveEntry>

- <xref:System.IO.Compression.DeflateStream>

- <xref:System.IO.Compression.GZipStream>

W poniższych przykładach pokazano niektóre funkcje, które można wykonać podczas pracy z skompresowane pliki.

## <a name="example-1---create-and-extract-a-zip-file"></a>Przykład 1 — Tworzenie i Wyodrębnij plik zip

Poniższy przykład przedstawia sposób tworzenia i Wyodrębnij skompresowany plik z rozszerzeniem .zip przy użyciu <xref:System.IO.Compression.ZipFile> klasy. Kompresuje zawartość folderu do nowego pliku zip, a następnie wyodrębnia zawartość do nowego folderu. Aby użyć <xref:System.IO.Compression.ZipFile> klasy, należy wskazać `System.IO.Compression.FileSystem` zestawu w projekcie.

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2---extract-specific-file-extensions"></a>Przykład 2 - Extract określonych rozszerzeń plików

Kolejnym przykładzie pokazano, jak do iteracji zawartość istniejący plik zip i Wyodrębnij pliki z rozszerzeniem txt. Używa <xref:System.IO.Compression.ZipArchive> klasę, aby uzyskać dostęp do istniejącego pliku .zip i <xref:System.IO.Compression.ZipArchiveEntry> klasy do zbadania poszczególne pozycje w skompresowany plik. Używa metody rozszerzenia (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) dla <xref:System.IO.Compression.ZipArchiveEntry> obiektu. Metody rozszerzenia jest dostępna w <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> klasy. Aby użyć <xref:System.IO.Compression.ZipFileExtensions> klasy, należy wskazać `System.IO.Compression.FileSystem` zestawu w projekcie.

> [!IMPORTANT]
> Gdy rozpakować pliki, możesz wyszukiwać ścieżki złośliwych plików, które można wprowadzić limit katalogu miejscu Rozpakuj do. Jest to nazywane atak przechodzenie ścieżki.

W poniższym przykładzie pokazano, jak i sprawdź, czy ścieżki złośliwych plików i zapewnia bezpieczny sposób, aby rozpakować:

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3---add-a-new-file-to-an-existing-zip-file"></a>Przykład 3 - Dodaj nowy plik do istniejącego pliku zip

W poniższym przykładzie użyto <xref:System.IO.Compression.ZipArchive> klasy dostęp do istniejącego pliku zip, a następnie dodaje nowy plik do skompresowanego pliku. Nowy plik pobiera skompresowane po dodaniu go do istniejącego pliku zip.

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4---compress-and-decompress-a-directory-of-gz-files"></a>Przykład 4 - kompresji i dekompresji katalogu plików .gz

Można również użyć <xref:System.IO.Compression.GZipStream> i <xref:System.IO.Compression.DeflateStream> klasy do kompresji i dekompresji danych. Używają tego samego algorytmu kompresji. Skompresowane <xref:System.IO.Compression.GZipStream> obiektów, które są zapisywane do pliku, który ma rozszerzenie .gz można zdekompresować za pomocą wielu typowych narzędzi oprócz metody udostępniane przez <xref:System.IO.Compression.GZipStream>. Poniższy przykład przedstawia sposób kompresji i dekompresji katalog plików przy użyciu <xref:System.IO.Compression.GZipStream> klasy:

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a>Zobacz także

<xref:System.IO.Compression.ZipArchive>  
<xref:System.IO.Compression.ZipFile>  
<xref:System.IO.Compression.ZipArchiveEntry>  
<xref:System.IO.Compression.DeflateStream>  
<xref:System.IO.Compression.GZipStream>  
[We/Wy plików i strumieni](../../../docs/standard/io/index.md)
