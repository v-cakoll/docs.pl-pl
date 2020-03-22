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

Użyj `RenameFile` metody obiektu, `My.Computer.FileSystem` aby zmienić nazwę pliku, podając bieżącą lokalizację, nazwę pliku i nową nazwę pliku. Tej metody nie można użyć do przenoszenia pliku; użyj `MoveFile` metody, aby przenieść i zmienić nazwę pliku.  
  
### <a name="to-rename-a-file"></a>Aby zmienić nazwę pliku  
  
- Użyj `My.Computer.FileSystem.RenameFile` metody, aby zmienić nazwę pliku. W tym przykładzie `Test.txt` zmienia `SecondTest.txt`nazwę pliku o nazwie .  
  
     [!code-vb[VbVbcnMyFileSystem#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#9)]  
  
 W tym przykładzie kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu fragment kodu fragment kodu znajduje się w **systemie plików — przetwarzanie dysków, folderów i plików**. Aby uzyskać więcej informacji, zobacz [Fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą spowodować wyjątek:  
  
- Ścieżka nie jest prawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, \\ \\\\zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od . ) (<xref:System.ArgumentException>).  
  
- `newName`zawiera informacje<xref:System.ArgumentException>o ścieżce ( ).  
  
- Ścieżka jest nieprawidłowa, `Nothing` ponieważ<xref:System.ArgumentNullException>jest ( ).  
  
- `newName`lub `Nothing` pusty ciąg<xref:System.ArgumentNullException>( ).  
  
- Plik źródłowy jest nieprawidłowy lub<xref:System.IO.FileNotFoundException>nie istnieje ( ).  
  
- Istnieje istniejący plik lub katalog o `newName` nazwie<xref:System.IO.IOException>określonej w ( ).  
  
- Ścieżka przekracza zdefiniowaną przez system<xref:System.IO.PathTooLongException>maksymalną długość ( ).  
  
- Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
- Użytkownik nie ma niezbędnych uprawnień do<xref:System.Security.SecurityException>wyświetlania ścieżki ( ).  
  
- Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [Porady: przenoszenie pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)
- [Tworzenie, usuwanie i przenoszenie plików i katalogów](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
- [Instrukcje: tworzenie kopii pliku w tym samym katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Instrukcje: tworzenie kopii pliku w innym katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
