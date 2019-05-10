---
title: 'Instrukcje: Tworzenie kopii pliku w tym samym katalogu w Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
ms.openlocfilehash: 747d985cbd9e2f2cc7f9b07f5723455a63a87b8f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64629083"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a>Instrukcje: Tworzenie kopii pliku w tym samym katalogu w Visual Basic
Użyj `My.Computer.FileSystem.CopyFile` metoda kopiowania plików. Parametry umożliwiają Nadpisz istniejące pliki, Zmień nazwę pliku, wyświetlić postęp operacji i umożliwia użytkownikowi anulować operację.  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a>Aby utworzyć kopię pliku, w tym samym folderze  
  
- Użyj `CopyFile` metodę podawania pliku docelowego i lokalizacji. Poniższy przykład tworzy kopię `test.txt` o nazwie `test2.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a>Aby utworzyć kopię pliku, w tym samym folderze, zastępując istniejące pliki  
  
- Użyj `CopyFile` metody dostarczenie pliku docelowego i lokalizację, a ustawienie `overwrite` do `True`. Poniższy przykład tworzy kopię `test.txt` o nazwie `test2.txt` i zastępuje wszelkie istniejące pliki o tej nazwie.  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować zgłoszenie wyjątku:  
  
- Ścieżka nie jest prawidłowa dla jednego z następujących przyczyn: jest to ciąg o zerowej długości, zawiera tylko znak odstępu, zawiera nieprawidłowe znaki lub jest ścieżką do urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).  
  
- System nie może pobrać ścieżki bezwzględnej (<xref:System.ArgumentException>).  
  
- Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
- Plik źródłowy jest nieprawidłowy lub nie istnieje (<xref:System.IO.FileNotFoundException>).  
  
- Połączone ścieżka wskazuje na istniejący katalog (<xref:System.IO.IOException>).  
  
- Plik docelowy istnieje i `overwrite` ustawiono `False` (<xref:System.IO.IOException>).  
  
- Użytkownik nie ma wystarczających uprawnień dostępu do pliku (<xref:System.IO.IOException>).  
  
- Plik w folderze docelowym o takiej samej nazwie jest w użyciu (<xref:System.IO.IOException>).  
  
- Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
- `ShowUI` ustawiono `True`, `onUserCancel` ustawiono `ThrowException`, a użytkownik anulował operację (<xref:System.OperationCanceledException>).  
  
- `ShowUI` ustawiono `True`, `onUserCancel` ustawiono `ThrowException`, i nieokreślony błąd We/Wy (<xref:System.OperationCanceledException>).  
  
- Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).  
  
- Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).  
  
- Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [Instrukcje: Kopiowanie plików z określonym wzorcem do katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [Instrukcje: Tworzenie kopii pliku w innym katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [Instrukcje: Kopiowanie katalogu do innego katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [Instrukcje: Zmienianie nazwy pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
