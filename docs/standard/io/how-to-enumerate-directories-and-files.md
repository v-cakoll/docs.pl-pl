---
title: "Porady: wyliczanie katalogów i ciągów"
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
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5d0f22853210144881e49c4192ea38a5c3e57cda
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-enumerate-directories-and-files"></a>Porady: wyliczanie katalogów i ciągów
Można wyliczyć katalogów i plików przy użyciu metody, które zwracają wyliczalny kolekcji ciągów ich nazw. Można również użyć metody, które zwracają wyliczalny zbiór <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, lub <xref:System.IO.FileSystemInfo> obiektów. Kolekcje wyliczalny zapewnić lepszą wydajność niż tablic, podczas pracy z dużych kolekcjach katalogów i plików.  
  
 Umożliwia także kolekcje wyliczalny uzyskane z tych metod do dostarczania <xref:System.Collections.Generic.IEnumerable%601> parametr dla konstruktorów kolekcji klas takich jak <xref:System.Collections.Generic.List%601> klasy.  
  
 Jeśli chcesz pobrać tylko nazwy katalogów i plików, użyj metody wyliczania <xref:System.IO.Directory> klasy. Aby uzyskać inne właściwości katalogów i plików, należy użyć <xref:System.IO.DirectoryInfo> i <xref:System.IO.FileSystemInfo> klasy.  
  
 Poniższa tabela zawiera przewodnik dotyczący metody, które zwracają kolekcje wyliczenia.  
  
|Aby wyliczyć|Wyliczalny kolekcji do zwrócenia|Metoda do użycia|  
|------------------|-------------------------------------|-------------------|  
|Katalogi|Nazwy katalogów|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||Informacje katalogu (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Pliki|Nazwy plików|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||Informacje o plikach (<xref:System.IO.FileInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Informacje o systemie plików|Wpisy systemu plików|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||Informacje o systemie plików (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 Mimo że można natychmiast wyliczyć wszystkie pliki w podkatalogach katalogu nadrzędnego przy użyciu <xref:System.IO.SearchOption.AllDirectories> dostarczonych przez opcję wyszukiwania <xref:System.IO.SearchOption> wyliczenia, wyjątki nieautoryzowanego dostępu (<xref:System.UnauthorizedAccessException>) może spowodować wyliczeniu, aby być niekompletne. Jeśli możliwe są następujące wyjątki, możesz je catch i kontynuować najpierw wyliczanie katalogów, a następnie wyliczania plików.  
  
### <a name="to-enumerate-directory-names"></a>Aby wyliczyć nazwy katalogów  
  
-   Użyj <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> metodę, aby uzyskać listę nazw własny katalog najwyższego poziomu w określonej ścieżce.  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a>Aby wyliczyć nazwy plików w katalogu i jego podkatalogach  
  
-   Użyj <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> metody do wyszukiwania i (opcjonalnie) jego podkatalogi katalogu, aby uzyskać listę nazw plików, które pasują do wzorca wyszukiwania określonego.  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a>Aby wyliczyć kolekcji obiektów DirectoryInfo  
  
-   Użyj <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> metodę, aby uzyskać kolekcję katalogów najwyższego poziomu.  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a>Aby wyliczyć kolekcję obiektów FileInfo we wszystkich katalogach  
  
-   Użyj <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> metodę, aby uzyskać kolekcję plików, które pasują do wzorca wyszukiwania określonego we wszystkich katalogach. W tym przykładzie najpierw wylicza najwyższego poziomu katalogów przechwytują wyjątki nieautoryzowanego dostępu, a następnie wylicza pliki.  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Plik i strumienia I-O](../../../docs/standard/io/index.md)
