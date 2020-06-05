---
title: 'Instrukcje: Tworzenie kopii pliku w innym katalogu'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: 3b4b41e105d6bb6a17fbb688aa4718b33c23b9d6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401696"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a>Porady: tworzenie kopii pliku w innym katalogu w Visual Basic

`My.Computer.FileSystem.CopyFile`Metoda umożliwia kopiowanie plików. Jego parametry zapewniają możliwość zastępowania istniejących plików, zmiany nazwy pliku, wyświetlenia postępu operacji i umożliwienia użytkownikowi anulowania operacji.  
  
### <a name="to-copy-a-text-file-to-another-folder"></a>Aby skopiować plik tekstowy do innego folderu  
  
- Użyj `CopyFile` metody, aby skopiować plik, określić plik źródłowy i katalog docelowy. `overwrite`Parametr pozwala określić, czy zastąpić istniejące pliki. Poniższy przykład kodu pokazuje, jak korzystać z programu `CopyFile` .  
  
     [!code-vb[VbFileIOMisc#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#24)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą spowodować zgłoszenie wyjątku:  
  
- Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od \\ \\ . \\ ) (<xref:System.ArgumentException>).  
  
- System nie może pobrać ścieżki bezwzględnej ( <xref:System.ArgumentException> ).  
  
- Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` ( <xref:System.ArgumentNullException> ).  
  
- Plik źródłowy jest nieprawidłowy lub nie istnieje ( <xref:System.IO.FileNotFoundException> ).  
  
- Połączona ścieżka wskazuje istniejący katalog ( <xref:System.IO.IOException> ).  
  
- Plik docelowy istnieje i `overwrite` ma ustawioną wartość `False` ( <xref:System.IO.IOException> ).  
  
- Użytkownik nie ma wystarczających uprawnień dostępu do pliku ( <xref:System.IO.IOException> ).  
  
- Plik w folderze docelowym o tej samej nazwie jest używany ( <xref:System.IO.IOException> ).  
  
- Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format ( <xref:System.NotSupportedException> ).  
  
- `ShowUI`jest ustawiona na `True` , `onUserCancel` jest ustawiona na `ThrowException` , a użytkownik anulował operację ( <xref:System.OperationCanceledException> ).  
  
- `ShowUI`jest ustawiona na `True` , `onUserCancel` jest ustawiona na `ThrowException` , i Wystąpił nieokreślony błąd we/wy ( <xref:System.OperationCanceledException> ).  
  
- Ścieżka przekracza maksymalną długość zdefiniowaną przez system ( <xref:System.IO.PathTooLongException> ).  
  
- Użytkownik nie ma wymaganego uprawnienia ( <xref:System.UnauthorizedAccessException> ).  
  
- Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki ( <xref:System.Security.SecurityException> ).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [Instrukcje: Kopiowanie plików z określonym wzorcem do katalogu](how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [Instrukcje: Tworzenie kopii pliku w tym samym katalogu](how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Instrukcje: Kopiowanie katalogu do innego katalogu](how-to-copy-a-directory-to-another-directory.md)
- [Instrukcje: Zmienianie nazwy pliku](how-to-rename-a-file.md)
