---
title: 'Porady: przenoszenie pliku w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96c6d1d89c0dfe4720637202b42414047e96f146
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-move-a-file-in-visual-basic"></a>Porady: przenoszenie pliku w Visual Basic
`My.Computer.FileSystem.MoveFile` Metody można użyć do przeniesienia pliku do innego folderu. Strukturze docelowej nie istnieje, zostanie utworzona.  
  
### <a name="to-move-a-file"></a>Aby przenieść plik  
  
-   Użyj `MoveFile` metodę, aby przenieść plik, określając nazwę pliku i lokalizację dla pliku źródłowego i docelowego pliku. W tym przykładzie przenosi plik o nazwie `test.txt` z `TestDir1` do `TestDir2`. Należy pamiętać, że nazwa pliku docelowego jest określony, mimo że jest taka sama jak nazwa pliku źródłowego.  
  
     [!code-vb[VbVbcnMyFileSystem#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_1.vb)]  
  
### <a name="to-move-a-file-and-rename-it"></a>Aby przenieść plik i zmień jego nazwę  
  
-   Użyj `MoveFile` metodę, aby przenieść plik, określając nazwa pliku źródłowego i lokalizacji, lokalizacji docelowej i nową nazwę w lokalizacji docelowej. W tym przykładzie przenosi plik o nazwie `test.txt` z `TestDir1` do `TestDir2` i zmienia jego nazwę `nexttest.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#25](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_2.vb)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `destinationFileName`jest `Nothing` lub ciąg pusty (<xref:System.ArgumentNullException>).  
  
-   Plik źródłowy jest nieprawidłowy lub nie istnieje (<xref:System.IO.FileNotFoundException>).  
  
-   Punkty połączoną ścieżkę do istniejącego katalogu, plik docelowy istnieje i `overwrite` ustawiono `False`, plik w katalogu docelowym o takiej samej nazwie jest używany, lub użytkownik nie ma wystarczających uprawnień do dostępu do pliku (<xref:System.IO.IOException> ).  
  
-   Nazwę pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
-   `showUI`ustawiono `True`, `onUserCancel` ustawiono `ThrowException`i użytkownik anulował operację lub występuje Wystąpił nieokreślony błąd We/Wy (<xref:System.OperationCanceledException>).  
  
-   Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).  
  
-   Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).  
  
-   Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>  
 [Porady: Zmienianie nazwy pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 [Porady: tworzenie kopii pliku w innym katalogu](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)  
 [Porady: analizowanie ścieżek pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
