---
title: 'Instrukcje: Wyliczanie katalogów i plików'
description: Informacje na temat wyliczania katalogów i plików przy użyciu wyliczalnych kolekcji, które mogą zapewnić lepszą wydajność niż tablice w programie .NET.
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
ms.openlocfilehash: 276668f4a3eee89610a81b1256820770d1f72dc3
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662579"
---
# <a name="how-to-enumerate-directories-and-files"></a>Instrukcje: Wyliczanie katalogów i plików
Wyliczalne kolekcje zapewniają lepszą wydajność niż tablice podczas pracy z dużymi kolekcjami katalogów i plików. Aby wyliczyć katalogi i pliki, należy użyć metod, które zwracają wyliczalną kolekcję nazw katalogów lub plików, lub ich <xref:System.IO.DirectoryInfo> , <xref:System.IO.FileInfo> lub <xref:System.IO.FileSystemInfo> obiektów.  
  
Jeśli chcesz wyszukać i zwrócić tylko nazwy katalogów lub plików, użyj metod wyliczenia <xref:System.IO.Directory> klasy. Jeśli chcesz wyszukać i zwrócić inne właściwości katalogów lub plików, użyj <xref:System.IO.DirectoryInfo> <xref:System.IO.FileSystemInfo> klas i.  
  
Można użyć wyliczalnych kolekcji z tych metod jako <xref:System.Collections.Generic.IEnumerable%601> parametru dla konstruktorów klas kolekcji, takich jak <xref:System.Collections.Generic.List%601> .  
  
Poniższa tabela zawiera podsumowanie metod, które zwracają wyliczalne kolekcje plików i katalogów:  
  
|Aby wyszukać i zwrócić|Use, Metoda|  
|------------------|-------------------------------------|-------------------|  
|Nazwy katalogów|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Informacje o katalogu ( <xref:System.IO.DirectoryInfo> )|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Nazwy plików|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Informacje o pliku ( <xref:System.IO.FileInfo> )|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Nazwy wpisów systemu plików|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|Informacje o wpisie systemu plików ( <xref:System.IO.FileSystemInfo> )|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|Nazwy katalogów i plików |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> Chociaż można natychmiast wyliczyć wszystkie pliki w podkatalogach katalogu nadrzędnego przy użyciu <xref:System.IO.SearchOption.AllDirectories> opcji opcjonalne <xref:System.IO.SearchOption> Wyliczenie, <xref:System.UnauthorizedAccessException> błędy mogą spowodować, że Wyliczenie nie jest kompletne. Te wyjątki można przechwytywać, wprowadzając najpierw katalogi i wyliczając pliki.  
  
## <a name="examples-use-the-directory-class"></a>Przykłady: Użyj klasy katalogu  
  
Poniższy przykład używa metody, <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> Aby uzyskać listę nazw katalogów najwyższego poziomu w określonej ścieżce.  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

Poniższy przykład używa metody, <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> Aby rekursywnie wyliczyć wszystkie nazwy plików w katalogu i podkatalogach zgodnych z określonym wzorcem. Następnie odczytuje każdy wiersz każdego pliku i wyświetla wiersze zawierające określony ciąg wraz z ich nazwami i ścieżkami.

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a>Przykłady: użycie klasy DirectoryInfo  
  
W poniższym przykładzie zastosowano <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> metodę, aby wyświetlić kolekcję katalogów najwyższego poziomu, których <xref:System.IO.FileSystemInfo.CreationTimeUtc> wartość jest wcześniejsza niż określona <xref:System.DateTime> .  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
Poniższy przykład używa metody, <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> Aby wyświetlić listę wszystkich plików, których <xref:System.IO.FileInfo.Length> rozmiar przekracza 10 MB. Ten przykład najpierw wylicza katalogi najwyższego poziomu, aby przechwycić możliwe nieautoryzowane wyjątki dostępu, a następnie wylicza pliki.  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [We/wy plików i strumieni](index.md)
