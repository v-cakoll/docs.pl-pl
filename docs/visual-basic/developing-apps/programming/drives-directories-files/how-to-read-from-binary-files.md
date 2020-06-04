---
title: 'Instrukcje: Odczyt z plików binarnych'
ms.date: 07/20/2015
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
ms.openlocfilehash: 3b4108034b86d99143fff6943e68ca0077ebd21b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359932"
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a>Porady: odczyt z plików binarnych w Visual Basic

`My.Computer.FileSystem`Obiekt udostępnia `ReadAllBytes` metodę odczytu z plików binarnych.  
  
### <a name="to-read-from-a-binary-file"></a>Aby odczytywać dane z pliku binarnego  
  
- Użyj `ReadAllBytes` metody, która zwraca zawartość pliku jako tablicę bajtów. Ten przykład odczytuje z pliku `C:/Documents and Settings/selfportrait.jpg` .  
  
     [!code-vb[VbVbcnMyFileSystem#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#78)]  
  
- W przypadku dużych plików binarnych można użyć <xref:System.IO.FileStream.Read%2A> metody <xref:System.IO.FileStream> obiektu do odczytu z pliku tylko określonej wartości w danym momencie. Następnie można ograniczyć ilość pliku do załadowania do pamięci dla każdej operacji odczytu. Poniższy przykład kodu kopiuje plik i umożliwia obiektowi wywołującemu określenie, jaka część pliku jest odczytywana do pamięci na potrzeby operacji odczytu.  
  
     [!code-vb[VbVbcnMyFileSystem#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#91)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą spowodować zgłoszenie wyjątku:  
  
- Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia ( <xref:System.ArgumentException> ).  
  
- Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` ( <xref:System.ArgumentNullException> ).  
  
- Plik nie istnieje ( <xref:System.IO.FileNotFoundException> ).  
  
- Plik jest używany przez inny proces lub wystąpił błąd we/wy ( <xref:System.IO.IOException> ).  
  
- Ścieżka przekracza maksymalną długość zdefiniowaną przez system ( <xref:System.IO.PathTooLongException> ).  
  
- Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format ( <xref:System.NotSupportedException> ).  
  
- Za mało pamięci, aby zapisać ciąg do bufora ( <xref:System.OutOfMemoryException> ).  
  
- Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki ( <xref:System.Security.SecurityException> ).  
  
 Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik Form1. vb nie może być plikiem źródłowym Visual Basic.  
  
 Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji. Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Odczyt z plików](reading-from-files.md)
- [Instrukcje: Odczyt z plików tekstowych w wielu formatach](how-to-read-from-text-files-with-multiple-formats.md)
- [Zapisywanie danych w schowku i odczytywanie ich z niego](../computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
