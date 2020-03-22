---
title: 'Porady: tworzenie kopii pliku w innym katalogu'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: e9a14e1f3743979548b92a3db653d09a470a1875
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348834"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a>Porady: tworzenie kopii pliku w innym katalogu w Visual Basic

Metoda `My.Computer.FileSystem.CopyFile` umożliwia kopiowanie plików. Jego parametry umożliwiają zastąpienie istniejących plików, zmianę nazwy pliku, wyświetlenie postępu operacji i umożliwienie użytkownikowi anulowania operacji.  
  
### <a name="to-copy-a-text-file-to-another-folder"></a>Aby skopiować plik tekstowy do innego folderu  
  
- Użyj `CopyFile` tej metody, aby skopiować plik, określając plik źródłowy i katalog docelowy. Parametr `overwrite` umożliwia określenie, czy należy zastąpić istniejące pliki. Poniższe przykłady kodu pokazują, jak używać `CopyFile`.  
  
     [!code-vb[VbFileIOMisc#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#24)]  
  
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
- [Instrukcje: tworzenie kopii pliku w tym samym katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Porady: kopiowanie katalogu do innego katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [Porady: zmienianie nazwy pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
