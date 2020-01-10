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
ms.openlocfilehash: 6a26d0ef529b81976c4d2caafed34bb5f08d8d46
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707748"
---
# <a name="how-to-enumerate-directories-and-files"></a>Instrukcje: Wyliczanie katalogów i plików
Wyliczalne kolekcje zapewniają lepszą wydajność niż tablice podczas pracy z dużymi kolekcjami katalogów i plików. Aby wyliczyć katalogi i pliki, użyj metod, które zwracają wyliczalną kolekcję nazw katalogów lub plików albo ich <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>lub <xref:System.IO.FileSystemInfo> obiektów.  
  
Jeśli chcesz wyszukać i zwrócić tylko nazwy katalogów lub plików, użyj metod wyliczania klasy <xref:System.IO.Directory>. Jeśli chcesz wyszukać i zwrócić inne właściwości katalogów lub plików, użyj klas <xref:System.IO.DirectoryInfo> i <xref:System.IO.FileSystemInfo>.  
  
Można użyć wyliczalnych kolekcji z tych metod jako parametru <xref:System.Collections.Generic.IEnumerable%601> dla konstruktorów klas kolekcji, takich jak <xref:System.Collections.Generic.List%601>.  
  
Poniższa tabela zawiera podsumowanie metod, które zwracają wyliczalne kolekcje plików i katalogów:  
  
|Aby wyszukać i zwrócić|Use, Metoda|  
|------------------|-------------------------------------|-------------------|  
|Nazwy katalogów|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Informacje o katalogu (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Nazwy plików|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Informacje o pliku (<xref:System.IO.FileInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Nazwy wpisów systemu plików|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|Informacje o wpisie systemu plików (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|Nazwy katalogów i plików |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> Mimo że można natychmiast wyliczyć wszystkie pliki w podkatalogach katalogu nadrzędnego przy użyciu opcji <xref:System.IO.SearchOption.AllDirectories> opcjonalne Wyliczenie <xref:System.IO.SearchOption>, <xref:System.UnauthorizedAccessException> błędy mogą spowodować niekompletne Wyliczenie. Te wyjątki można przechwytywać, wprowadzając najpierw katalogi i wyliczając pliki.  
  
## <a name="examples-use-the-directory-class"></a>Przykłady: Użyj klasy katalogu  
  
W poniższym przykładzie zastosowano metodę <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType>, aby uzyskać listę nazw katalogów najwyższego poziomu w określonej ścieżce.  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

W poniższym przykładzie zastosowano metodę <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType>, aby rekursywnie wyliczyć wszystkie nazwy plików w katalogu i podkatalogach zgodnych z określonym wzorcem. Następnie odczytuje każdy wiersz każdego pliku i wyświetla wiersze zawierające określony ciąg wraz z ich nazwami i ścieżkami.

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a>Przykłady: użycie klasy DirectoryInfo  
  
W poniższym przykładzie zastosowano metodę <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>, aby wyświetlić kolekcję katalogów najwyższego poziomu, których <xref:System.IO.FileSystemInfo.CreationTimeUtc> jest wcześniejsza niż określona wartość <xref:System.DateTime>.  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
W poniższym przykładzie zastosowano metodę <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>, aby wyświetlić listę wszystkich plików, których <xref:System.IO.FileInfo.Length> przekracza 10 MB. Ten przykład najpierw wylicza katalogi najwyższego poziomu, aby przechwycić możliwe nieautoryzowane wyjątki dostępu, a następnie wylicza pliki.  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [We/wy plików i strumieni](../../../docs/standard/io/index.md)
