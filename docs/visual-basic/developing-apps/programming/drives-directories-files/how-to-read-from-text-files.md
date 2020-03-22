---
title: 'Instrukcje: odczyt z plików tekstowych'
ms.date: 07/20/2015
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
ms.openlocfilehash: 8af088ad269cc77bc5c83aedb86bde9af2e37a15
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334589"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a>Porady: odczyt z plików testowych w Visual Basic

Metoda <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> `My.Computer.FileSystem` obiektu umożliwia odczyt z pliku tekstowego. Kodowanie pliku może być określone, jeśli zawartość pliku używa kodowania, takiego jak ASCII lub UTF-8.

Podczas odczytu z pliku używającego znaków rozszerzonych, trzeba będzie określić kodowanie pliku.

> [!NOTE]
> Aby odczytać plik pojedynczy wiersz tekstu naraz, <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> użyj `My.Computer.FileSystem` metody obiektu. Metoda `OpenTextFileReader` zwraca obiekt <xref:System.IO.StreamReader>. Można użyć <xref:System.IO.StreamReader.ReadLine%2A> metody obiektu, `StreamReader` aby odczytać plik po jednym wierszu naraz. Można przetestować na końcu pliku <xref:System.IO.StreamReader.EndOfStream%2A> przy użyciu `StreamReader` metody obiektu.

## <a name="to-read-from-a-text-file"></a>Aby odczytać z pliku tekstowego

Użyj `ReadAllText` metody obiektu, `My.Computer.FileSystem` aby odczytać zawartość pliku tekstowego w ciągu, podając ścieżkę. Poniższy przykład odczytuje zawartość test.txt jako ciąg i wyświetla go w oknie komunikatu.

[!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]

### <a name="to-read-from-a-text-file-that-is-encoded"></a>Aby odczytać z pliku tekstowego, który jest kodowany

Użyj `ReadAllText` metody `My.Computer.FileSystem` obiektu, aby odczytać zawartość pliku tekstowego do ciągu, podając ścieżkę i typ kodowania plików. Poniższy przykład odczytuje zawartość pliku z kodowaniem UTF32 test.txt jako ciąg i wyświetla go w oknie komunikatu.

[!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]

## <a name="robust-programming"></a>Niezawodne programowanie

Następujące warunki mogą spowodować wyjątek:

- Ścieżka nie jest prawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały<xref:System.ArgumentException>znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia ( ).

- Ścieżka jest nieprawidłowa, `Nothing` ponieważ<xref:System.ArgumentNullException>jest ( ).

- Plik nie istnieje<xref:System.IO.FileNotFoundException>( ).

- Plik jest używany przez inny proces lub występuje<xref:System.IO.IOException>błąd we/wy ( ).

- Ścieżka przekracza zdefiniowaną przez system<xref:System.IO.PathTooLongException>maksymalną długość ( ).

- Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).

- Nie ma wystarczającej ilości pamięci,<xref:System.OutOfMemoryException>aby zapisać ciąg do bufora ( ).

- Użytkownik nie ma niezbędnych uprawnień do<xref:System.Security.SecurityException>wyświetlania ścieżki ( ).

Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik Form1.vb może nie być plikiem źródłowym języka Visual Basic.

Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji. Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [Odczyt z plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Porady: odczyt z rozdzielonych przecinkami plików testowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Porady: odczyt z plików testowych o stałej szerokości](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [Instrukcje: odczyt z plików tekstowych w wielu formatach](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Rozwiązywanie problemów: odczytywanie z oraz zapisywanie w plikach tekstowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Wskazówki: manipulowanie plikami i katalogami w Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Kodowanie pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
