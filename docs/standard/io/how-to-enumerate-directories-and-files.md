---
title: 'Porady: wyliczanie katalogów i ciągów'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3de83395df9e8c89a92e85b96ddd15e9f0be6ad5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44207697"
---
# <a name="how-to-enumerate-directories-and-files"></a>Porady: wyliczanie katalogów i ciągów
Za pomocą metody, które zwracają wyliczalny zbiór ciągów ich nazw, można wyliczyć katalogów i plików. Można również użyć metod, które zwracają wyliczalny zbiór <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, lub <xref:System.IO.FileSystemInfo> obiektów. Przeliczalne kolekcje zapewniają lepszą wydajność niż tablic, podczas pracy z dużych kolekcjach katalogów i plików.  
  
 Umożliwia także przeliczalne kolekcje uzyskany z tych metod do dostarczania <xref:System.Collections.Generic.IEnumerable%601> parametr dla konstruktorów kolekcji klasy, takie jak <xref:System.Collections.Generic.List%601> klasy.  
  
 Jeśli chcesz pobrać tylko nazwy katalogów i plików, należy użyć metod wyliczenie <xref:System.IO.Directory> klasy. Aby uzyskać inne właściwości katalogów i plików, należy użyć <xref:System.IO.DirectoryInfo> i <xref:System.IO.FileSystemInfo> klasy.  
  
 W poniższej tabeli przedstawiono wskazówki do metod, które zwracają przeliczalne kolekcje.  
  
|Aby wyliczyć|Wyliczalne kolekcji do zwrócenia|Metoda do użycia|  
|------------------|-------------------------------------|-------------------|  
|Katalogi|Nazwy katalogów|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||Informacje o katalogu (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Pliki|Nazwy plików|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||Informacje o pliku (<xref:System.IO.FileInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Informacje o systemie plików|We wpisach w plikach systemu|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||Informacje o systemie plików (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 Mimo że można od razu wyliczyć wszystkie pliki w podkatalogach katalogu nadrzędnego za pomocą <xref:System.IO.SearchOption.AllDirectories> dostarczone przez opcję wyszukiwania <xref:System.IO.SearchOption> wyliczenie, wyjątki przed nieautoryzowanym dostępem (<xref:System.UnauthorizedAccessException>) może spowodować, że wyliczenie do być niekompletne. Jeśli te wyjątki, można przechwytywać i Kontynuuj, najpierw wyliczanie katalogów i następnie Wyliczanie plików.  
  
### <a name="to-enumerate-directory-names"></a>Aby wyliczyć nazwy katalogów  
  
-   Użyj <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> metodę, aby uzyskać listę nazw własny katalog najwyższego poziomu w określonej ścieżce.  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a>Aby wyliczyć nazwy plików w katalogu i podkatalogach  
  
-   Użyj <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> metody do wyszukiwania i (opcjonalnie) jego podkatalogi katalogu, aby uzyskać listę nazw plików, które pasują do wzorca wyszukiwania.  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a>Aby wyliczyć kolekcji obiektów DirectoryInfo  
  
-   Użyj <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> metodę, aby uzyskać kolekcję katalogów najwyższego poziomu.  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a>Aby wyliczyć kolekcji obiektów FileInfo we wszystkich katalogach  
  
-   Użyj <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> metodę, aby uzyskać kolekcję plików, które pasują do wzorca wyszukiwania we wszystkich katalogach. W tym przykładzie najpierw wylicza najwyższego poziomu katalogów przechwytują wyjątki możliwe nieautoryzowanemu dostępowi, a następnie wylicza pliki.  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [We/Wy plików i strumieni](../../../docs/standard/io/index.md)
