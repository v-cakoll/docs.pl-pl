---
title: 'Instrukcje: Przenoszenie pliku'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
ms.openlocfilehash: 2dafeb3b5f8b8c3a8976b25c1a57f405aebb32b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401605"
---
# <a name="how-to-move-a-file-in-visual-basic"></a>Porady: przenoszenie pliku w Visual Basic

`My.Computer.FileSystem.MoveFile`Metoda może służyć do przenoszenia pliku do innego folderu. Jeśli struktura docelowa nie istnieje, zostanie utworzona.  
  
### <a name="to-move-a-file"></a>Aby przenieść plik  
  
- Użyj `MoveFile` metody, aby przenieść plik, określić nazwę pliku i lokalizację zarówno dla pliku źródłowego, jak i pliku docelowego. Ten przykład przenosi plik o nazwie `test.txt` z `TestDir1` do `TestDir2` . Należy pamiętać, że nazwa pliku docelowego jest określona, mimo że jest taka sama jak nazwa pliku źródłowego.  
  
     [!code-vb[VbVbcnMyFileSystem#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#24)]  
  
### <a name="to-move-a-file-and-rename-it"></a>Aby przenieść plik i zmienić jego nazwę  
  
- Użyj `MoveFile` metody, aby przenieść plik, określić nazwę i lokalizację pliku źródłowego, lokalizację docelową oraz nową nazwę w lokalizacji docelowej. Ten przykład przenosi plik o nazwie `test.txt` z `TestDir1` do `TestDir2` i zmienia jego nazwę `nexttest.txt` .  
  
     [!code-vb[VbVbcnMyFileSystem#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#25)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą spowodować wyjątek:  
  
- Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od \\ \\ . \\ ) (<xref:System.ArgumentException>).  
  
- Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` ( <xref:System.ArgumentNullException> ).  
  
- `destinationFileName`jest `Nothing` lub ciągiem pustym ( <xref:System.ArgumentNullException> ).  
  
- Plik źródłowy jest nieprawidłowy lub nie istnieje ( <xref:System.IO.FileNotFoundException> ).  
  
- Połączona ścieżka wskazuje istniejący katalog, plik docelowy istnieje i `overwrite` ma ustawioną wartość `False` , plik w katalogu docelowym o tej samej nazwie jest używany lub użytkownik nie ma wystarczających uprawnień dostępu do pliku ( <xref:System.IO.IOException> ).  
  
- Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format ( <xref:System.NotSupportedException> ).  
  
- `showUI`jest ustawiona na `True` , `onUserCancel` jest ustawiona na `ThrowException` , a użytkownik anulował operację lub Wystąpił nieokreślony błąd we/wy ( <xref:System.OperationCanceledException> ).  
  
- Ścieżka przekracza maksymalną długość zdefiniowaną przez system ( <xref:System.IO.PathTooLongException> ).  
  
- Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki ( <xref:System.Security.SecurityException> ).  
  
- Użytkownik nie ma wymaganego uprawnienia ( <xref:System.UnauthorizedAccessException> ).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>
- [Instrukcje: Zmienianie nazwy pliku](how-to-rename-a-file.md)
- [Instrukcje: Tworzenie kopii pliku w innym katalogu](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [Instrukcje: Analizowanie ścieżek plików](how-to-parse-file-paths.md)
