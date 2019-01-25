---
title: 'Instrukcje: Wyliczanie katalogów i plików'
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 463c751ab03875b6af89c325981c65b7bc69d0ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580463"
---
# <a name="how-to-enumerate-directories-and-files"></a>Instrukcje: Wyliczanie katalogów i plików
Przeliczalne kolekcje zapewniają lepszą wydajność niż tablic, podczas pracy z dużych kolekcjach katalogów i plików. Aby wyliczanie katalogów i plików, należy użyć metody, które zwracają wyliczalny zbiór nazwy pliku lub katalogu, lub ich <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, lub <xref:System.IO.FileSystemInfo> obiektów.  
  
Jeśli chcesz wyszukać i zwrócić tylko nazwy katalogów i plików, należy użyć metod wyliczenie <xref:System.IO.Directory> klasy. Jeśli chcesz wyszukać i zwrócić inne właściwości katalogów i plików, użyj <xref:System.IO.DirectoryInfo> i <xref:System.IO.FileSystemInfo> klasy.  
  
Możesz użyć przeliczalne kolekcje z tych metod jako <xref:System.Collections.Generic.IEnumerable%601> parametr konstruktory klas kolekcji, takie jak <xref:System.Collections.Generic.List%601>.  
  
W poniższej tabeli przedstawiono metody, które zwracają przeliczalne kolekcje plików i katalogów:  
  
|Aby wyszukać i zwrócić|Użyj metody|  
|------------------|-------------------------------------|-------------------|  
|Nazwy katalogów|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Informacje o katalogu (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Nazwy plików|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Informacje o pliku (<xref:System.IO.FileInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Nazwy wpisów systemu plików|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|Plik informacji o systemie wejścia (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|Nazwy katalogów i plików |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> Mimo że można od razu wyliczyć wszystkie pliki w podkatalogach katalogu nadrzędnego za pomocą <xref:System.IO.SearchOption.AllDirectories> możliwości opcjonalny <xref:System.IO.SearchOption> wyliczenia, <xref:System.UnauthorizedAccessException> błędy pomijana wyliczenia niekompletne. Najpierw wyliczanie katalogów, a następnie Wyliczanie plików może przechwytywać te wyjątki.  
  
## <a name="examples-use-the-directory-class"></a>Przykłady: Korzystanie z klasy katalogu  
  
W poniższym przykładzie użyto <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> metodę, aby uzyskać listę nazw własny katalog najwyższego poziomu w określonej ścieżce.  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

W poniższym przykładzie użyto <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> metody rekursywnie wyliczyć wszystkie nazwy plików w katalogu i podkatalogów, które pasują do określonych wzorca. Następnie odczytuje każdej linii każdego pliku i wyświetla wiersze zawierające określony ciąg, wraz z ich nazw plików i ścieżek.

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a>Przykłady: Korzystanie z klasy DirectoryInfo  
  
W poniższym przykładzie użyto <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> metody, aby wyświetlić listę kolekcji katalogów najwyższego poziomu którego <xref:System.IO.FileSystemInfo.CreationTimeUtc> jest starsza niż określony <xref:System.DateTime> wartość.  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
W poniższym przykładzie użyto <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> metodę, aby wyświetlić listę wszystkich plików, których <xref:System.IO.FileInfo.Length> przekracza 10 MB. W tym przykładzie najpierw wylicza najwyższego poziomu katalogów przechwytują wyjątki możliwe nieautoryzowanym dostępem i następnie wylicza pliki.  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

[We/Wy plików i strumieni](../../../docs/standard/io/index.md)
