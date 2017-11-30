---
title: "Porady: kopiowanie plików z określonym wzorcem do katalogu w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ead158a95d7f3ef4d0cd650b3b1a1db7042ccb29
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a>Porady: kopiowanie plików z określonym wzorcem do katalogu w Visual Basic
<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> Metoda zwraca zbiór ciągów reprezentujących nazw ścieżek do plików tylko do odczytu. Można użyć `wildCards` parametr, aby określić określonego wzorca.  
  
 W przypadku znalezienia pasujących plików, zwracana jest pustej kolekcji.  
  
 Można użyć <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> metodę, aby skopiować pliki do katalogu.  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a>Aby skopiować pliki z określonym wzorcem do katalogu  
  
1.  Użyj `GetFiles` metodę, aby zwrócić listę plików. W tym przykładzie zwraca wszystkie .rtf — pliki w określonym katalogu.  
  
     [!code-vb[VbFileIOMisc#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_1.vb)]  
  
2.  Użyj `CopyFile` metodę, aby skopiować pliki. W tym przykładzie kopiuje pliki do katalogu o nazwie `testdirectory`.  
  
     [!code-vb[VbVbcnMyFileSystem#88](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_2.vb)]  
  
3.  Zamknij `For` instrukcji z `Next` instrukcji.  
  
     [!code-vb[VbVbcnMyFileSystem#89](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_3.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia powyżej fragmentów w pełnej postaci kopiuje wszystkie pliki .rtf w określonym katalogu katalog o nazwie `testdirectory`.  
  
 [!code-vb[VbFileIOMisc#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_4.vb)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Katalog nie istnieje (<xref:System.IO.DirectoryNotFoundException>).  
  
-   Punkty katalogu do istniejącego pliku (<xref:System.IO.IOException>).  
  
-   Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).  
  
-   Nazwę pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
-   Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>). Użytkownik nie ma wystarczających uprawnień (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>  
 <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>  
 [Porady: znajdowanie podkatalogów z określonym wzorcem](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)  
 [Rozwiązywanie problemów: Odczytywanie z oraz zapisywanie w plikach tekstowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 [Porady: pobieranie kolekcji plików z katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
