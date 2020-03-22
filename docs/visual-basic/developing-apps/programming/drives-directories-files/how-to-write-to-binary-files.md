---
title: 'Porady: zapis w plikach binarnych'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: 72d019f5f49868bd84d0507535e8ebc547b50e25
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334428"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a>Porady: zapis w plikach binarnych w Visual Basic

Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> zapisuje dane do pliku binarnego. Jeśli `append` parametr `True`jest , dołączy dane do pliku; w przeciwnym razie dane w pliku są zastępowane.

Jeśli określona ścieżka z wyłączeniem nazwy pliku <xref:System.IO.DirectoryNotFoundException> jest nieprawidłowa, zostanie zgłoszony wyjątek. Jeśli ścieżka jest prawidłowa, ale plik nie istnieje, zostanie utworzony plik.

## <a name="to-write-to-a-binary-file"></a>Aby zapisać do pliku binarnego

Użyj `WriteAllBytes` tej metody, podając ścieżkę pliku i nazwę oraz bajty, które mają zostać zapisane. W tym przykładzie dołącza `CustomerData` tablicę `CollectedData.dat`danych do pliku o nazwie .

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a>Niezawodne programowanie

Następujące warunki mogą powodować wyjątek:

- Ścieżka nie jest prawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości; zawiera tylko biały znak; lub zawiera nieprawidłowe znaki. (<xref:System.ArgumentException>).

- Ścieżka jest nieprawidłowa, `Nothing` ponieważ<xref:System.ArgumentNullException>jest ( ).

- `File`wskazuje ścieżkę, która nie<xref:System.IO.FileNotFoundException> <xref:System.IO.DirectoryNotFoundException>istnieje ( lub ).

- Plik jest używany przez inny proces lub występuje błąd<xref:System.IO.IOException>we/wy ( ).

- Ścieżka przekracza zdefiniowaną przez system<xref:System.IO.PathTooLongException>maksymalną długość ( ).

- Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).

- Użytkownik nie ma niezbędnych uprawnień do<xref:System.Security.SecurityException>wyświetlania ścieżki ( ).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Instrukcje: zapisywanie tekstu w plikach](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
