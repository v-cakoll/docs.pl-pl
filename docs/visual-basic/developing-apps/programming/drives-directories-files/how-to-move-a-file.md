---
title: 'Porady: przenoszenie pliku'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
ms.openlocfilehash: 29c64a7a81028d47bf489212e6d8faec5e8dda75
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74335360"
---
# <a name="how-to-move-a-file-in-visual-basic"></a>Porady: przenoszenie pliku w Visual Basic

Metoda `My.Computer.FileSystem.MoveFile` ta może służyć do przenoszenia pliku do innego folderu. Jeśli struktura docelowa nie istnieje, zostanie utworzona.  
  
### <a name="to-move-a-file"></a>Aby przenieść plik  
  
- Użyj `MoveFile` metody przenoszenia pliku, określając nazwę pliku i lokalizację zarówno dla pliku źródłowego, jak i pliku docelowego. W tym przykładzie `test.txt` `TestDir1` przenosi `TestDir2`plik o nazwie z do . Należy zauważyć, że nazwa pliku docelowego jest określona, mimo że jest taka sama jak nazwa pliku źródłowego.  
  
     [!code-vb[VbVbcnMyFileSystem#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#24)]  
  
### <a name="to-move-a-file-and-rename-it"></a>Aby przenieść plik i zmienić jego nazwę  
  
- Użyj `MoveFile` metody, aby przenieść plik, określając nazwę i lokalizację pliku źródłowego, lokalizację docelową i nową nazwę w lokalizacji docelowej. W tym przykładzie `test.txt` `TestDir1` przenosi `TestDir2` nazwany plik `nexttest.txt`z do i zmienia jego nazwę .  
  
     [!code-vb[VbVbcnMyFileSystem#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#25)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą spowodować wyjątek:  
  
- Ścieżka nie jest prawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, \\ \\\\zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od . ) (<xref:System.ArgumentException>).  
  
- Ścieżka jest nieprawidłowa, `Nothing` ponieważ<xref:System.ArgumentNullException>jest ( ).  
  
- `destinationFileName`lub `Nothing` pusty ciąg<xref:System.ArgumentNullException>( ).  
  
- Plik źródłowy jest nieprawidłowy lub<xref:System.IO.FileNotFoundException>nie istnieje ( ).  
  
- Połączona ścieżka wskazuje istniejący katalog, plik docelowy istnieje i `overwrite` jest ustawiony na `False`, plik w katalogu docelowym o tej samej nazwie jest<xref:System.IO.IOException>w użyciu lub użytkownik nie ma wystarczających uprawnień dostępu do pliku ( ).  
  
- Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
- `showUI`jest `True`ustawiona `onUserCancel` na `ThrowException`, i albo użytkownik anulował operację lub występuje nieokreślony błąd we/wy (<xref:System.OperationCanceledException>).  
  
- Ścieżka przekracza zdefiniowaną przez system<xref:System.IO.PathTooLongException>maksymalną długość ( ).  
  
- Użytkownik nie ma niezbędnych uprawnień do<xref:System.Security.SecurityException>wyświetlania ścieżki ( ).  
  
- Użytkownik nie ma wymaganych<xref:System.UnauthorizedAccessException>uprawnień ( ).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>
- [Porady: zmienianie nazwy pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
- [Instrukcje: tworzenie kopii pliku w innym katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [Porady: analizowanie ścieżek pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
