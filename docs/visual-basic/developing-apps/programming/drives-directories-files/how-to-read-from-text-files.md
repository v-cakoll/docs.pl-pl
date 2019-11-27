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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334589"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a>Porady: odczyt z plików testowych w Visual Basic

Metoda <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> obiektu `My.Computer.FileSystem` umożliwia odczytywanie z pliku tekstowego. Kodowanie pliku może być określone, jeśli zawartość pliku używa kodowania, takiego jak ASCII lub UTF-8.

Podczas odczytu z pliku używającego znaków rozszerzonych, trzeba będzie określić kodowanie pliku.

> [!NOTE]
> Aby odczytywać pojedynczy wiersz tekstu w danym momencie, użyj metody <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> obiektu `My.Computer.FileSystem`. Metoda `OpenTextFileReader` zwraca obiekt <xref:System.IO.StreamReader>. Można użyć metody <xref:System.IO.StreamReader.ReadLine%2A> obiektu `StreamReader`, aby odczytywać plik jeden wiersz jednocześnie. Można testować pod kątem końca pliku przy użyciu metody <xref:System.IO.StreamReader.EndOfStream%2A> obiektu `StreamReader`.

## <a name="to-read-from-a-text-file"></a>Aby odczytać z pliku tekstowego

Użyj metody `ReadAllText` obiektu `My.Computer.FileSystem`, aby odczytać zawartość pliku tekstowego w ciągu, dostarczając ścieżkę. Poniższy przykład odczytuje zawartość test.txt jako ciąg i wyświetla go w oknie komunikatu.

[!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]

### <a name="to-read-from-a-text-file-that-is-encoded"></a>Aby odczytać z pliku tekstowego, który jest kodowany

Użyj metody `ReadAllText` obiektu `My.Computer.FileSystem`, aby odczytać zawartość pliku tekstowego w ciągu, podając ścieżkę i typ kodowania pliku. Poniższy przykład odczytuje zawartość pliku z kodowaniem UTF32 test.txt jako ciąg i wyświetla go w oknie komunikatu.

[!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]

## <a name="robust-programming"></a>Skuteczne programowanie

Następujące warunki mogą spowodować wyjątek:

- Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (<xref:System.ArgumentException>).

- Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` (<xref:System.ArgumentNullException>).

- Plik nie istnieje (<xref:System.IO.FileNotFoundException>).

- Plik jest używany przez inny proces lub wystąpił błąd we/wy (<xref:System.IO.IOException>).

- Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).

- Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format (<xref:System.NotSupportedException>).

- Za mało pamięci, aby zapisać ciąg do bufora (<xref:System.OutOfMemoryException>).

- Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).

Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik Form1. vb nie może być plikiem źródłowym Visual Basic.

Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji. Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [Odczyt z plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Instrukcje: odczyt z rozdzielonych przecinkami plików testowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Instrukcje: odczyt z plików testowych o stałej szerokości](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [Instrukcje: odczyt z plików tekstowych w wielu formatach](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Rozwiązywanie problemów: odczytywanie z plików tekstowych oraz zapisywanie w nich](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Przewodnik: manipulowanie plikami i katalogami w Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Kodowanie pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
