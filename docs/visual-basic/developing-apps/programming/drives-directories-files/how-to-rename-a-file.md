---
title: 'Porady: zmienianie nazwy pliku'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: e69dad9ad7f59002ad62b7a06299ff012488e534
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334552"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a>Porady: zmienianie nazwy pliku w Visual Basic

Użyj `RenameFile` metody `My.Computer.FileSystem` obiektu, aby zmienić nazwę pliku, dostarczając bieżącą lokalizację, nazwę pliku i nową nazwę pliku. Nie można użyć tej metody do przeniesienia pliku; Użyj `MoveFile` metody, aby przenieść plik i zmienić jego nazwę.  
  
### <a name="to-rename-a-file"></a>Aby zmienić nazwę pliku  
  
- Użyj metody `My.Computer.FileSystem.RenameFile` , aby zmienić nazwę pliku. Ten przykład zmienia nazwę pliku o nazwie `Test.txt` na. `SecondTest.txt`  
  
     [!code-vb[VbVbcnMyFileSystem#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#9)]  
  
 Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu wstawka znajduje się w **systemie plików — dyski, foldery i pliki**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą spowodować wyjątek:  
  
- Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od \\ \\.\\) (<xref:System.ArgumentException>).  
  
- `newName`zawiera informacje o ścieżce<xref:System.ArgumentException>().  
  
- Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` (<xref:System.ArgumentNullException>).  
  
- `newName`jest `Nothing` lub ciągiem pustym (<xref:System.ArgumentNullException>).  
  
- Plik źródłowy jest nieprawidłowy lub nie istnieje (<xref:System.IO.FileNotFoundException>).  
  
- Istnieje plik lub katalog o nazwie określonej w `newName` (<xref:System.IO.IOException>).  
  
- Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).  
  
- Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format (<xref:System.NotSupportedException>).  
  
- Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).  
  
- Użytkownik nie ma wymaganego uprawnienia (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [Porady: przenoszenie pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)
- [Tworzenie, usuwanie i przenoszenie plików i katalogów](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
- [Instrukcje: tworzenie kopii pliku w tym samym katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Instrukcje: tworzenie kopii pliku w innym katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
