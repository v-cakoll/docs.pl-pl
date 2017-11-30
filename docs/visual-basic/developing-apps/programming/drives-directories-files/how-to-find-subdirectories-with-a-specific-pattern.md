---
title: "Porady: znajdowanie podkatalogów z określonym wzorcem w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0c4549f417e86e82897ca32d8d7cf22aaf462c90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>Porady: znajdowanie podkatalogów z określonym wzorcem w Visual Basic
<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> Metoda zwraca zbiór ciągów reprezentujących nazwy ścieżki dla podkatalogów w katalogu tylko do odczytu. Można użyć `wildCards` parametr, aby określić określonego wzorca. Jeśli chcesz w wyszukiwaniu uwzględnić zawartość podkatalogów, ustaw `searchType` parametr `SearchOption.SearchAllSubDirectories`.  
  
 Pusta kolekcja jest zwracany, gdy zostaną znalezione nie katalogi zgodne z określonym wzorcem.  
  
### <a name="to-find-subdirectories-with-a-specific-pattern"></a>Aby znajdowanie podkatalogów z określonym wzorcem  
  
-   Użyj `GetDirectories` metody, podając nazwę i ścieżkę katalogu do przeszukania. Poniższy przykład zwraca wszystkie katalogi w strukturze katalogów, zawierające słowo "Dzienniki" w nazwie, a następnie dodanie ich do `ListBox1`.  
  
     [!code-vb[VbVbcnFileAccess#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-find-subdirectories-with-a-specific-pattern_1.vb)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Co najmniej jeden określony symboli wieloznacznych jest `Nothing`, ciągiem pustym lub zawiera tylko spacje (<xref:System.ArgumentNullException>).  
  
-   `directory`nie istnieje (<xref:System.IO.DirectoryNotFoundException>).  
  
-   `directory`Wskazuje istniejący plik (<xref:System.IO.IOException>).  
  
-   Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).  
  
-   Nazwę pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
-   Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).  
  
-   Użytkownik nie ma wystarczających uprawnień (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>  
 [Porady: znajdowanie plików z określonym wzorcem](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
