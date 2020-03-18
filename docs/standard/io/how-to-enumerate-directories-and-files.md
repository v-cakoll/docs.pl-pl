---
title: 'Jak: Wyliczanie katalogów i plików'
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
ms.openlocfilehash: 6a26d0ef529b81976c4d2caafed34bb5f08d8d46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707748"
---
# <a name="how-to-enumerate-directories-and-files"></a>Jak: Wyliczanie katalogów i plików
Kolekcje wyliczalne zapewniają lepszą wydajność niż tablice podczas pracy z dużymi kolekcjami katalogów i plików. Aby wyliczyć katalogi i pliki, należy użyć metod zwracających wyliczoną <xref:System.IO.DirectoryInfo> <xref:System.IO.FileInfo>kolekcję <xref:System.IO.FileSystemInfo> nazw katalogów lub plików lub ich , lub obiektów.  
  
Jeśli chcesz wyszukać i zwrócić tylko nazwy katalogów lub plików, użyj <xref:System.IO.Directory> metod wyliczenia klasy. Jeśli chcesz wyszukać i zwrócić inne właściwości katalogów <xref:System.IO.DirectoryInfo> lub <xref:System.IO.FileSystemInfo> plików, należy użyć i klas.  
  
Można użyć niezliczonych kolekcji z tych <xref:System.Collections.Generic.IEnumerable%601> metod jako parametru dla <xref:System.Collections.Generic.List%601>konstruktorów klas kolekcji, takich jak .  
  
W poniższej tabeli podsumowano metody zwracające wyliczalne kolekcje plików i katalogów:  
  
|Aby wyszukać i powrócić|Użyj metody|  
|------------------|-------------------------------------|-------------------|  
|Nazwy katalogów|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Informacje katalogowe (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Nazwy plików|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Informacje o<xref:System.IO.FileInfo>pliku ( )|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Nazwy wejściówek systemu plików|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|Informacje o wpisie systemu plików (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|Nazwy katalogów i plików |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> Chociaż można natychmiast wyliczyć wszystkie pliki w podkatalogach katalogu nadrzędnego przy użyciu <xref:System.IO.SearchOption.AllDirectories> opcji opcjonalnego <xref:System.IO.SearchOption> wyliczenia, błędy mogą sprawić, <xref:System.UnauthorizedAccessException> że wyliczenie będzie niekompletne. Można przechwycić te wyjątki, najpierw wyliczając katalogi, a następnie wyliczając pliki.  
  
## <a name="examples-use-the-directory-class"></a>Przykłady: Użyj klasy Directory  
  
W poniższym <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> przykładzie użyto metody, aby uzyskać listę nazw katalogów najwyższego poziomu w określonej ścieżce.  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

W poniższym <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> przykładzie użyto metody do rekursyjnie wyliczyć wszystkie nazwy plików w katalogu i podkatalogów, które pasują do określonego wzorca. Następnie odczytuje każdy wiersz każdego pliku i wyświetla wiersze zawierające określony ciąg, z ich nazwami plików i ścieżkami.

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a>Przykłady: Użyj klasy DirectoryInfo  
  
W poniższym <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> przykładzie użyto metody do listy kolekcji <xref:System.IO.FileSystemInfo.CreationTimeUtc> katalogów najwyższego <xref:System.DateTime> poziomu, których jest wcześniejsza niż określona wartość.  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
W poniższym <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> przykładzie użyto metody <xref:System.IO.FileInfo.Length> do listy wszystkich plików, których przekracza 10 MB. W tym przykładzie najpierw wylicza katalogi najwyższego poziomu, aby przechwycić możliwe wyjątki nieautoryzowanego dostępu, a następnie wylicza pliki.  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- [Plik i strumień we/wy](../../../docs/standard/io/index.md)
