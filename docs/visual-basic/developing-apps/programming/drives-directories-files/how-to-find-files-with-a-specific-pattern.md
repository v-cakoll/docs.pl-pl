---
title: "Porady: znajdowanie plików z określonym wzorcem w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ce37e7241eb33c3d4f18355d3b5375e0de95b28f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a>Porady: znajdowanie plików z określonym wzorcem w Visual Basic
<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> Metoda zwraca zbiór ciągów reprezentujących nazw ścieżek do plików tylko do odczytu. Można użyć `wildCards` parametr, aby określić określonego wzorca. Jeśli chcesz w wyszukiwaniu uwzględnić podkatalogów, ustaw `searchType` parametr `SearchOption.SearchAllSubDirectories`.  
  
 Pusta kolekcja jest zwracany, jeśli znaleziono nie plików zgodnych z określonym wzorcem.  
  
> [!NOTE]
>  Aby uzyskać informacje dotyczące zwracania listy plików za pomocą `DirectoryInfo` klasy `System.IO` przestrzeni nazw, zobacz <xref:System.IO.DirectoryInfo.GetFiles%2A>.  
  
### <a name="to-find-files-with-a-specified-pattern"></a>Aby znaleźć plików z określonym wzorcem  
  
-   Użyj `GetFiles` metody, podając nazwę i ścieżkę katalogu do przeszukania, a następnie określając wzorzec. Poniższy przykład zwraca wszystkie pliki z rozszerzeniem `.dll` w katalogu i dodaje je do `ListBox1`.  
  
     [!code-vb[VbFileIOMisc#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-find-files-with-a-specific-pattern_1.vb)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `directory`nie istnieje (<xref:System.IO.DirectoryNotFoundException>).  
  
-   `directory`Wskazuje istniejący plik (<xref:System.IO.IOException>).  
  
-   Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).  
  
-   Nazwę pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
-   Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).  
  
-   Użytkownik nie ma wystarczających uprawnień (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>  
 [Porady: znajdowanie podkatalogów z określonym wzorcem](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)  
 [Rozwiązywanie problemów: Odczytywanie z oraz zapisywanie w plikach tekstowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 [Porady: pobieranie kolekcji plików z katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
