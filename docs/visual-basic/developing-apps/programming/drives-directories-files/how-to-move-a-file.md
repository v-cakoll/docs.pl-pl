---
title: 'Instrukcje: Przenieś plik w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
ms.openlocfilehash: 0c909e3dfce1af17cc74ca526ba0409d5e9f93f8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58843724"
---
# <a name="how-to-move-a-file-in-visual-basic"></a>Instrukcje: Przenieś plik w języku Visual Basic
`My.Computer.FileSystem.MoveFile` Metoda może służyć do przenoszenia pliku do innego folderu. Struktura docelowa nie istnieje, zostanie utworzony.  
  
### <a name="to-move-a-file"></a>Aby przenieść plik  
  
-   Użyj `MoveFile` metodę, aby przenieść plik, określając nazwę pliku i lokalizację pliku źródłowego i pliku docelowego. W tym przykładzie przenosi plik o nazwie `test.txt` z `TestDir1` do `TestDir2`. Należy pamiętać, że nazwa pliku docelowego jest określony, nawet jeśli jest taka sama jak nazwa pliku źródłowego.  
  
     [!code-vb[VbVbcnMyFileSystem#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#24)]  
  
### <a name="to-move-a-file-and-rename-it"></a>Aby przenieść plik i zmień jego nazwę  
  
-   Użyj `MoveFile` metodę, aby przenieść plik, określając nazwę pliku źródłowego i lokalizacji, lokalizacji docelowej i Nowa nazwa w lokalizacji docelowej. W tym przykładzie przenosi plik o nazwie `test.txt` z `TestDir1` do `TestDir2` i zmienia ją `nexttest.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#25)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Ścieżka nie jest prawidłowa dla jednego z następujących przyczyn: jest to ciąg o zerowej długości, zawiera tylko znak odstępu, zawiera nieprawidłowe znaki lub jest ścieżką do urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `destinationFileName` jest `Nothing` ani być pustym ciągiem (<xref:System.ArgumentNullException>).  
  
-   Plik źródłowy jest nieprawidłowy lub nie istnieje (<xref:System.IO.FileNotFoundException>).  
  
-   Punkty połączone ścieżki do istniejącego katalogu, plik docelowy istnieje i `overwrite` ustawiono `False`, plik w katalogu docelowym o takiej samej nazwie jest używany, lub użytkownik nie ma wystarczających uprawnień dostępu do pliku (<xref:System.IO.IOException> ).  
  
-   Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
-   `showUI` ustawiono `True`, `onUserCancel` ustawiono `ThrowException`oraz użytkownik anulował operację lub nieokreślony błąd We/Wy (<xref:System.OperationCanceledException>).  
  
-   Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).  
  
-   Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).  
  
-   Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>
- [Instrukcje: Zmienianie nazwy pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
- [Instrukcje: Tworzenie kopii pliku w innym katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [Instrukcje: Analizowanie ścieżek pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
