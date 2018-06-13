---
title: 'Porady: zapis w plikach binarnych w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: 59edf84c1addd287eb1d1615c46258f329b1c7e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587205"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a>Porady: zapis w plikach binarnych w Visual Basic
<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> Metody zapisuje dane w pliku binarnym. Jeśli `append` parametr jest `True`, dołączy danych do pliku; w przeciwnym razie dane w pliku są zastępowane.  
  
 Jeśli określona ścieżka, z wyłączeniem nazwa pliku nie jest prawidłowy, <xref:System.IO.DirectoryNotFoundException> zostanie wygenerowany wyjątek. Jeśli ścieżka jest prawidłowa, ale plik nie istnieje, zostanie utworzony plik.  
  
### <a name="to-write-to-a-binary-file"></a>Można zapisać do pliku binarnego  
  
-   Użyj `WriteAllBytes` metody, podając ścieżkę pliku i nazwa i liczba bajtów do zapisania. W tym przykładzie dołącza tablicy danych `CustomerData` pliku o nazwie `CollectedData.dat`.  
  
     [!code-vb[VbVbcnMyFileSystem#27](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-to-binary-files_1.vb)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Poniższe warunki mogą utworzyć wyjątek:  
  
-   Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest ciąg o zerowej długości. zawiera tylko biały znak lub zawiera nieprawidłowe znaki. (<xref:System.ArgumentException>).  
  
-   Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `File` wskazuje na ścieżkę, która nie istnieje (<xref:System.IO.FileNotFoundException> lub <xref:System.IO.DirectoryNotFoundException>).  
  
-   Plik jest używany przez inny proces lub błąd We/Wy (<xref:System.IO.IOException>).  
  
-   Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).  
  
-   Nazwę pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
-   Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>  
 [Instrukcje: zapisywanie tekstu w plikach](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
