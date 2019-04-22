---
title: 'Instrukcje: Zapis w plikach binarnych w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: e8aa1c96766fc1b63326415c879e9821dc1de7f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833693"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a>Instrukcje: Zapis w plikach binarnych w Visual Basic
<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> Metoda zapisuje dane w pliku binarnym. Jeśli `append` parametr jest `True`, dołączy je do pliku; w przeciwnym razie zostanie zastąpiony dane w pliku.  
  
 Jeśli określona ścieżka, z wyjątkiem nazwy pliku nie jest prawidłowy, <xref:System.IO.DirectoryNotFoundException> zostanie zgłoszony wyjątek. Jeśli ścieżka jest prawidłowa, ale plik nie istnieje, zostanie utworzony plik.  
  
### <a name="to-write-to-a-binary-file"></a>Można zapisać do pliku binarnego  
  
-   Użyj `WriteAllBytes` metody, podając ścieżkę i nazwę i bajtów do zapisania. W tym przykładzie dołącza tablicy danych `CustomerData` pliku o nazwie `CollectedData.dat`.  
  
     [!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą utworzyć wyjątek:  
  
-   Ścieżka nie jest prawidłowa dla jednego z następujących przyczyn: jest to ciąg o zerowej długości; zawiera tylko znak odstępu; lub zawiera nieprawidłowe znaki. (<xref:System.ArgumentException>).  
  
-   Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `File` Wskazuje ścieżkę, która nie istnieje (<xref:System.IO.FileNotFoundException> lub <xref:System.IO.DirectoryNotFoundException>).  
  
-   Plik jest używany przez inny proces lub wystąpi błąd We/Wy (<xref:System.IO.IOException>).  
  
-   Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).  
  
-   Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
-   Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Instrukcje: Zapisywanie tekstu do plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
