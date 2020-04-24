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

`My.Computer.FileSystem.CopyFile` Metoda umożliwia kopiowanie plików. Jego parametry zapewniają możliwość zastępowania istniejących plików, zmiany nazwy pliku, wyświetlenia postępu operacji i umożliwienia użytkownikowi anulowania operacji.  
  
### <a name="to-copy-a-text-file-to-another-folder"></a>Aby skopiować plik tekstowy do innego folderu  
  
- Użyj `CopyFile` metody, aby skopiować plik, określić plik źródłowy i katalog docelowy. `overwrite` Parametr pozwala określić, czy zastąpić istniejące pliki. Poniższy przykład kodu pokazuje, jak korzystać `CopyFile`z programu.  
  
     [!code-vb[VbFileIOMisc#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#24)]  
  
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
- [Instrukcje: tworzenie kopii pliku w tym samym katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Porady: kopiowanie katalogu do innego katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [Porady: zmienianie nazwy pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
