---
title: 'Porady: tworzenie kopii pliku w tym samym katalogu w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af592e16bb1f7f0bbb188b2ea39394ec1074d302
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a>Porady: tworzenie kopii pliku w tym samym katalogu w Visual Basic
Użyj `My.Computer.FileSystem.CopyFile` metoda kopiowania plików. Parametry pozwalają na zastąpienie istniejących plików, Zmień nazwę pliku, Pokaż postęp operacji i Zezwalaj użytkownikowi na anulowanie operacji.  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a>Aby utworzyć kopię pliku w folderze  
  
-   Użyj `CopyFile` metody dostarczania pliku docelowego i lokalizacji. Poniższy przykład tworzy kopię `test.txt` o nazwie `test2.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#51](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_1.vb)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a>Aby utworzyć kopii pliku w tym samym folderze, zastępując istniejące pliki  
  
-   Użyj `CopyFile` metody, podając pliku docelowego i lokalizacji, a ustawienie `overwrite` do `True`. Poniższy przykład tworzy kopię `test.txt` o nazwie `test2.txt` i zastępuje istniejące pliki o tej nazwie.  
  
     [!code-vb[VbVbcnMyFileSystem#52](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_2.vb)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Poniższe warunki mogą spowodować wyjątków:  
  
-   Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   System nie może pobrać ścieżkę bezwzględną (<xref:System.ArgumentException>).  
  
-   Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Plik źródłowy jest nieprawidłowy lub nie istnieje (<xref:System.IO.FileNotFoundException>).  
  
-   Łączna ścieżka wskazuje na istniejący katalog (<xref:System.IO.IOException>).  
  
-   Plik docelowy istnieje i `overwrite` ustawiono `False` (<xref:System.IO.IOException>).  
  
-   Użytkownik nie ma wystarczających uprawnień do dostępu do pliku (<xref:System.IO.IOException>).  
  
-   Plik w folderze docelowym o takiej samej nazwie jest w użyciu (<xref:System.IO.IOException>).  
  
-   Nazwę pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
-   `ShowUI`ustawiono `True`, `onUserCancel` ustawiono `ThrowException`, a użytkownik anulował operację (<xref:System.OperationCanceledException>).  
  
-   `ShowUI`ustawiono `True`, `onUserCancel` ustawiono `ThrowException`, i występuje Wystąpił nieokreślony błąd We/Wy (<xref:System.OperationCanceledException>).  
  
-   Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).  
  
-   Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).  
  
-   Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>  
 [Porady: kopiowanie plików z określonym wzorcem do katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)  
 [Porady: tworzenie kopii pliku w innym katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)  
 [Porady: kopiowanie katalogu do innego katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)  
 [Porady: Zmienianie nazwy pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
