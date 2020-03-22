---
title: 'Porady: odczyt z plików binarnych'
ms.date: 07/20/2015
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
ms.openlocfilehash: c33bc72a5c79901e3715ed6a587ffdb8e3565e48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74335296"
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a>Porady: odczyt z plików binarnych w Visual Basic

Obiekt `My.Computer.FileSystem` udostępnia `ReadAllBytes` metodę odczytu z plików binarnych.  
  
### <a name="to-read-from-a-binary-file"></a>Aby odczytać z pliku binarnego  
  
- Użyj `ReadAllBytes` metody, która zwraca zawartość pliku jako tablicy bajtowej. W tym przykładzie `C:/Documents and Settings/selfportrait.jpg`odczytuje się z pliku .  
  
     [!code-vb[VbVbcnMyFileSystem#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#78)]  
  
- W przypadku dużych plików binarnych można użyć <xref:System.IO.FileStream.Read%2A> metody <xref:System.IO.FileStream> obiektu do odczytu z pliku tylko określoną ilość w czasie. Następnie można ograniczyć, jaka część pliku jest ładowana do pamięci dla każdej operacji odczytu. Poniższy przykład kodu kopiuje plik i umożliwia wywołującemu określić, jaka część pliku jest odczytywana do pamięci na operację odczytu.  
  
     [!code-vb[VbVbcnMyFileSystem#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#91)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą powodować wyjątek:  
  
- Ścieżka nie jest prawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały<xref:System.ArgumentException>znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia ( ).  
  
- Ścieżka jest nieprawidłowa, `Nothing` ponieważ<xref:System.ArgumentNullException>jest ( ).  
  
- Plik nie istnieje<xref:System.IO.FileNotFoundException>( ).  
  
- Plik jest używany przez inny proces lub występuje błąd<xref:System.IO.IOException>we/wy ( ).  
  
- Ścieżka przekracza zdefiniowaną przez system<xref:System.IO.PathTooLongException>maksymalną długość ( ).  
  
- Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).  
  
- Nie ma wystarczającej ilości pamięci,<xref:System.OutOfMemoryException>aby zapisać ciąg do bufora ( ).  
  
- Użytkownik nie ma niezbędnych uprawnień do<xref:System.Security.SecurityException>wyświetlania ścieżki ( ).  
  
 Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik Form1.vb może nie być plikiem źródłowym języka Visual Basic.  
  
 Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji. Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Odczyt z plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Instrukcje: odczyt z plików tekstowych w wielu formatach](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Zapisywanie danych w schowku i odczytywanie ich z niego](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
