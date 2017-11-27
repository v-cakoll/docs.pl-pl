---
title: "Porady: pobieranie kolekcji plików z katalogu w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1c9245ab2593dfed5201640ecf84713582890334
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a>Porady: pobieranie kolekcji plików z katalogu w Visual Basic
Przeciążeń <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> metoda zwraca zbiór ciągów reprezentujących nazwy plików w katalogu tylko do odczytu:  
  
-   Użyj <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> przeciążenia wyszukiwania prostego pliku w określonym katalogu, bez podkatalogi wyszukiwania.  
  
-   Użyj <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> przeciążenia, aby określić dodatkowe opcje wyszukiwania. Można użyć `wildCards` parametr, aby określić kryteria wyszukiwania. Aby w wyszukiwaniu uwzględnić podkatalogów, ustaw `searchType` parametr <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.  
  
 Pusta kolekcja jest zwracany, jeśli znaleziono nie plików zgodnych z określonym wzorcem.  
  
### <a name="to-list-files-in-a-directory"></a>Aby wyświetlić listę plików w katalogu  
  
-   Użyj jednej z <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> przeciążenia metody, podając nazwę i ścieżkę katalogu do przeszukania `directory` parametru. Poniższy przykład zwraca wszystkie pliki w katalogu i dodaje je do `ListBox1`.  
  
     [!code-vb[VbVbcnMyFileSystem#32](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-get-the-collection-of-files-in-a-directory_1.vb)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `directory`nie istnieje (<xref:System.IO.DirectoryNotFoundException>).  
  
-   `directory`Wskazuje istniejący plik (<xref:System.IO.IOException>).  
  
-   Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).  
  
-   Nazwę pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
-   Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).  
  
-   Użytkownik nie ma wystarczających uprawnień (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>  
 [Porady: znajdowanie plików z określonym wzorcem](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)  
 [Porady: znajdowanie podkatalogów z określonym wzorcem](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
