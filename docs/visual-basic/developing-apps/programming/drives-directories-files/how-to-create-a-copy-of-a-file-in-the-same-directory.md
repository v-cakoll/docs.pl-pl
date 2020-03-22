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

Użyj `My.Computer.FileSystem.CopyFile` metody kopiowania plików. Parametry umożliwiają zastąpienie istniejących plików, zmianę nazwy pliku, wyświetlenie postępu operacji i umożliwienie użytkownikowi anulowania operacji.  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a>Aby utworzyć kopię pliku w tym samym folderze  
  
- Użyj `CopyFile` metody, podając plik docelowy i lokalizację. Poniższy przykład tworzy `test.txt` kopię `test2.txt`wywoływanego .  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a>Aby utworzyć kopię pliku w tym samym folderze, zastępowanie istniejących plików  
  
- Użyj `CopyFile` metody, podając plik docelowy i `overwrite` `True`lokalizację oraz ustawiając na . Poniższy przykład tworzy `test.txt` kopię `test2.txt` wywoływane i zastępuje wszystkie istniejące pliki o tej nazwie.  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą powodować wyjątek:  
  
- Ścieżka nie jest prawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, \\ \\\\zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od . ) (<xref:System.ArgumentException>).  
  
- System nie może pobrać ścieżki<xref:System.ArgumentException>bezwzględnej ( ).  
  
- Ścieżka jest nieprawidłowa, `Nothing` ponieważ<xref:System.ArgumentNullException>jest ( ).  
  
- Plik źródłowy jest nieprawidłowy lub<xref:System.IO.FileNotFoundException>nie istnieje ( ).  
  
- Połączona ścieżka wskazuje istniejący<xref:System.IO.IOException>katalog ( ).  
  
- Plik docelowy istnieje `overwrite` i `False` jest<xref:System.IO.IOException>ustawiony na ( ).  
  
- Użytkownik nie ma wystarczających uprawnień dostępu<xref:System.IO.IOException>do pliku ( ).  
  
- Plik w folderze docelowym o tej<xref:System.IO.IOException>samej nazwie jest używany ( ).  
  
- Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
- `ShowUI`jest `True`ustawiona `onUserCancel` na `ThrowException`, a użytkownik anulował operację<xref:System.OperationCanceledException>( ).  
  
- `ShowUI`jest `True`ustawiona `onUserCancel` na `ThrowException`, i występuje nieokreślony błąd we/wy (<xref:System.OperationCanceledException>).  
  
- Ścieżka przekracza zdefiniowaną przez system<xref:System.IO.PathTooLongException>maksymalną długość ( ).  
  
- Użytkownik nie ma wymaganych<xref:System.UnauthorizedAccessException>uprawnień ( ).  
  
- Użytkownik nie ma niezbędnych uprawnień do<xref:System.Security.SecurityException>wyświetlania ścieżki ( ).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [Instrukcje: kopiowanie plików z określonym wzorcem do katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [Instrukcje: tworzenie kopii pliku w innym katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [Porady: kopiowanie katalogu do innego katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [Porady: zmienianie nazwy pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
