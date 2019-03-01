---
title: 'Instrukcje: Odczyt z plików binarnych w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
ms.openlocfilehash: e9b30d119a404396e2bf37aa445a420f7823c57b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980389"
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a>Instrukcje: Odczyt z plików binarnych w Visual Basic
`My.Computer.FileSystem` Obiektu `ReadAllBytes` metody do odczytu z plików binarnych.  
  
### <a name="to-read-from-a-binary-file"></a>Odczytywanie pliku binarnego  
  
-   Użyj `ReadAllBytes` metody, która zwraca zawartość pliku w postaci tablicy bajtów. W tym przykładzie odczytuje z pliku `C:/Documents and Settings/selfportrait.jpg`.  
  
     [!code-vb[VbVbcnMyFileSystem#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#78)]  
  
-   W przypadku dużych plików binarnych, można użyć <xref:System.IO.FileStream.Read%2A> metody <xref:System.IO.FileStream> obiektu do odczytu z pliku określonej wartości w danym momencie. Następnie można ograniczyć, jaka część pliku jest ładowany do pamięci dla każdej operacji odczytu. Poniższy przykładowy kod kopiuje plik i umożliwia obiektowi wywołującemu określenie, ile plików jest odczytywany przez ilość pamięci na operacje odczytu.  
  
     [!code-vb[VbVbcnMyFileSystem#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#91)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować zgłoszenie wyjątku:  
  
-   Ścieżka nie jest prawidłowa dla jednego z następujących przyczyn: jest to ciąg o zerowej długości, zawiera tylko znak odstępu, zawiera nieprawidłowe znaki lub jest ścieżką do urządzenia (<xref:System.ArgumentException>).  
  
-   Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Plik nie istnieje (<xref:System.IO.FileNotFoundException>).  
  
-   Plik jest używany przez inny proces lub wystąpi błąd We/Wy (<xref:System.IO.IOException>).  
  
-   Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).  
  
-   Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
-   Nie ma wystarczającej ilości pamięci, aby zapisać ciąg do bufora (<xref:System.OutOfMemoryException>).  
  
-   Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).  
  
 Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik Form1.vb może nie być plik źródłowy w języku Visual Basic.  
  
 Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji. Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Odczyt z plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Instrukcje: Odczyt z plików tekstowych w wielu formatach](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Zapisywanie danych w schowku i odczytywanie ich z niego](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
