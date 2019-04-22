---
title: 'Instrukcje: Zmień nazwę pliku w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: b86797018e1471590fd4c89848921e696afbc819
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814156"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a>Instrukcje: Zmień nazwę pliku w Visual Basic
Użyj `RenameFile` metody `My.Computer.FileSystem` obiektu, aby zmienić nazwę pliku, podając bieżącą lokalizację, nazwę pliku i nową nazwę pliku. Nie można użyć tej metody można przenieść pliku; Użyj `MoveFile` metodą Przenieś i Zmień nazwę pliku.  
  
### <a name="to-rename-a-file"></a>Aby zmienić nazwę pliku  
  
-   Użyj `My.Computer.FileSystem.RenameFile` metodę, aby zmienić nazwę pliku. Ten przykład zmienia nazwę pliku o nazwie `Test.txt` do `SecondTest.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#9)]  
  
 Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu, fragment kodu znajduje się w **system - przetwarzanie napędów, folderów i plików plików**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Ścieżka nie jest prawidłowa dla jednego z następujących przyczyn: jest to ciąg o zerowej długości, zawiera tylko znak odstępu, zawiera nieprawidłowe znaki lub jest ścieżką do urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   `newName` zawiera informacje o ścieżce (<xref:System.ArgumentException>).  
  
-   Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `newName` jest `Nothing` ani być pustym ciągiem (<xref:System.ArgumentNullException>).  
  
-   Plik źródłowy jest nieprawidłowy lub nie istnieje (<xref:System.IO.FileNotFoundException>).  
  
-   Brak istniejący plik lub katalog o nazwie określonej w `newName` (<xref:System.IO.IOException>).  
  
-   Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).  
  
-   Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
-   Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).  
  
-   Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [Instrukcje: Przenoszenie pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)
- [Tworzenie, usuwanie i przenoszenie plików i katalogów](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
- [Instrukcje: Tworzenie kopii pliku w tym samym katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Instrukcje: Tworzenie kopii pliku w innym katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
