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
# <a name="how-to-compress-and-extract-files"></a>Porady: kompresowanie i wyodrębnianie plików
<xref:System.IO.Compression> Przestrzeń nazw zawiera następujące typy kompresji i dekompresji plików i strumieni. Można również używać tych typów może odczytywać i modyfikować zawartość skompresowanego pliku:  
  
-   <xref:System.IO.Compression.ZipFile>  
  
-   <xref:System.IO.Compression.ZipArchive>  
  
-   <xref:System.IO.Compression.ZipArchiveEntry>  
  
-   <xref:System.IO.Compression.DeflateStream>  
  
-   <xref:System.IO.Compression.GZipStream>  
  
 W poniższych przykładach pokazano niektóre funkcje, które można wykonać podczas pracy z skompresowane pliki.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak utworzyć i Wyodrębnij skompresowany plik z rozszerzeniem .zip przy użyciu <xref:System.IO.Compression.ZipFile> klasy. Kompresuje zawartość folderu do nowego pliku zip, a następnie wyodrębnia zawartość do nowego folderu. Aby użyć <xref:System.IO.Compression.ZipFile> klasy, należy wskazać `System.IO.Compression.FileSystem` zestawu w projekcie.  
  
 [!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]  
  
## <a name="example"></a>Przykład  
 Kolejnym przykładzie pokazano, jak do iteracji zawartość istniejący plik zip i Wyodrębnij pliki z rozszerzeniem txt. Używa <xref:System.IO.Compression.ZipArchive> klasę, aby uzyskać dostęp do istniejącego pliku .zip i <xref:System.IO.Compression.ZipArchiveEntry> klasy do zbadania poszczególne pozycje w skompresowany plik. Używa metody rozszerzenia (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) dla <xref:System.IO.Compression.ZipArchiveEntry> obiektu. Metody rozszerzenia jest dostępna w <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> klasy. Aby użyć <xref:System.IO.Compression.ZipFileExtensions> klasy, należy wskazać `System.IO.Compression.FileSystem` zestawu w projekcie.  
  
 [!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]  
  
## <a name="example"></a>Przykład  
 W następnym przykładzie użyto <xref:System.IO.Compression.ZipArchive> klasy dostęp do istniejącego pliku zip, a następnie dodaje nowy plik do skompresowanego pliku. Nowy plik pobiera skompresowane po dodaniu go do istniejącego pliku zip.  
  
 [!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]  
  
## <a name="example"></a>Przykład  
 Można również użyć <xref:System.IO.Compression.GZipStream> i <xref:System.IO.Compression.DeflateStream> klasy do kompresji i dekompresji danych. Używają tego samego algorytmu kompresji. Skompresowane <xref:System.IO.Compression.GZipStream> obiektów, które są zapisywane do pliku, który ma rozszerzenie .gz można zdekompresować za pomocą wielu typowych narzędzi oprócz metody udostępniane przez <xref:System.IO.Compression.GZipStream>. W tym przykładzie pokazano, jak kompresji i dekompresji katalog plików przy użyciu <xref:System.IO.Compression.GZipStream> klasy.  
  
 [!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
 [!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.Compression.ZipArchive>  
 <xref:System.IO.Compression.ZipFile>  
 <xref:System.IO.Compression.ZipArchiveEntry>  
 <xref:System.IO.Compression.DeflateStream>  
 <xref:System.IO.Compression.GZipStream>  
 [Plik i strumienia I-O](../../../docs/standard/io/index.md)
