---
title: 'Porady: tworzenie kopii pliku w tym samym katalogu'
ms.date: 07/20/2015
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
ms.openlocfilehash: 33a4f5424ac50de7b5dc988034ca15127dc1ed02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348824"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a>Porady: tworzenie kopii pliku w tym samym katalogu w Visual Basic

Użyj metody `My.Computer.FileSystem.CopyFile` , aby skopiować pliki. Parametry umożliwiają zastąpienie istniejących plików, zmiana nazwy pliku, wyświetlenie postępu operacji i umożliwienie użytkownikowi anulowania operacji.  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a>Aby utworzyć kopię pliku w tym samym folderze  
  
- Użyj `CopyFile` metody, dostarczając plik docelowy i lokalizację. Poniższy przykład tworzy kopię o `test.txt` nazwie. `test2.txt`  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a>Aby utworzyć kopię pliku w tym samym folderze, zastępując istniejące pliki  
  
- Użyj `CopyFile` metody, podając docelowy plik i lokalizację, a następnie ustaw `overwrite` wartość. `True` Poniższy przykład tworzy kopię o `test.txt` nazwie `test2.txt` i zastępuje wszystkie istniejące pliki o tej nazwie.  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą spowodować zgłoszenie wyjątku:  
  
- Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od \\ \\.\\) (<xref:System.ArgumentException>).  
  
- System nie może pobrać ścieżki bezwzględnej (<xref:System.ArgumentException>).  
  
- Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` (<xref:System.ArgumentNullException>).  
  
- Plik źródłowy jest nieprawidłowy lub nie istnieje (<xref:System.IO.FileNotFoundException>).  
  
- Połączona ścieżka wskazuje istniejący katalog (<xref:System.IO.IOException>).  
  
- Plik docelowy istnieje i `overwrite` ma ustawioną wartość `False` (<xref:System.IO.IOException>).  
  
- Użytkownik nie ma wystarczających uprawnień dostępu do pliku (<xref:System.IO.IOException>).  
  
- Plik w folderze docelowym o tej samej nazwie jest używany (<xref:System.IO.IOException>).  
  
- Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format (<xref:System.NotSupportedException>).  
  
- `ShowUI`jest ustawiona na `True`, `onUserCancel` jest ustawiona na `ThrowException`, a użytkownik anulował operację (<xref:System.OperationCanceledException>).  
  
- `ShowUI`jest ustawiona na `True`, `onUserCancel` jest ustawiona na `ThrowException`, i Wystąpił nieokreślony błąd we/wy (<xref:System.OperationCanceledException>).  
  
- Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).  
  
- Użytkownik nie ma wymaganego uprawnienia (<xref:System.UnauthorizedAccessException>).  
  
- Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [Instrukcje: kopiowanie plików z określonym wzorcem do katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [Instrukcje: tworzenie kopii pliku w innym katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [Porady: kopiowanie katalogu do innego katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [Porady: zmienianie nazwy pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
