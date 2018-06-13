---
title: 'Porady: zmienianie nazwy pliku w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: ef024f90567d8d69bdd432499db96e4f67578ce5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586415"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a>Porady: zmienianie nazwy pliku w Visual Basic
Użyj `RenameFile` metody `My.Computer.FileSystem` obiektu, aby zmienić nazwę pliku, dostarczając bieżącą lokalizację, nazwy pliku i nową nazwę pliku. Nie można użyć tej metody można przenieść pliku; Użyj `MoveFile` metody przenoszenia i Zmień nazwę pliku.  
  
### <a name="to-rename-a-file"></a>Aby zmienić nazwę pliku  
  
-   Użyj `My.Computer.FileSystem.RenameFile` metody, aby zmienić nazwę pliku. W tym przykładzie zmienia nazwę pliku o nazwie `Test.txt` do `SecondTest.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-rename-a-file_1.vb)]  
  
 W tym przykładzie kodu jest również dostępny jako fragmentu kodu IntelliSense. W selektor wstawek kodu, fragment znajduje się w **systemu - przetwarzanie napędów, folderów i plików plików**. Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   `newName` zawiera informacje o ścieżce (<xref:System.ArgumentException>).  
  
-   Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `newName` jest `Nothing` lub ciąg pusty (<xref:System.ArgumentNullException>).  
  
-   Plik źródłowy jest nieprawidłowy lub nie istnieje (<xref:System.IO.FileNotFoundException>).  
  
-   Brak istniejący plik lub katalog o nazwie określonej w `newName` (<xref:System.IO.IOException>).  
  
-   Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).  
  
-   Nazwę pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
-   Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).  
  
-   Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>  
 [Instrukcje: przenoszenie pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)  
 [Tworzenie, usuwanie i przenoszenie plików i katalogów](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)  
 [Instrukcje: tworzenie kopii pliku w tym samym katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)  
 [Instrukcje: tworzenie kopii pliku w innym katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
