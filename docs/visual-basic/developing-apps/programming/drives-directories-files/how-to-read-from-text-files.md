---
title: 'Instrukcje: Odczyt z plików tekstowych'
ms.date: 07/20/2015
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
ms.openlocfilehash: 0d99209ed123686355e8d49c82ba23f94084f895
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411619"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a>Porady: odczyt z plików testowych w Visual Basic

<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A>Metoda `My.Computer.FileSystem` obiektu umożliwia odczytywanie z pliku tekstowego. Kodowanie pliku może być określone, jeśli zawartość pliku używa kodowania, takiego jak ASCII lub UTF-8.

Podczas odczytu z pliku używającego znaków rozszerzonych, trzeba będzie określić kodowanie pliku.

> [!NOTE]
> Aby odczytać plik pojedynczy wiersz tekstu, użyj <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> metody `My.Computer.FileSystem` obiektu. Metoda `OpenTextFileReader` zwraca obiekt <xref:System.IO.StreamReader>. Można użyć <xref:System.IO.StreamReader.ReadLine%2A> metody `StreamReader` obiektu, aby odczytać plik jeden wiersz jednocześnie. Można testować pod kątem końca pliku przy użyciu <xref:System.IO.StreamReader.EndOfStream%2A> metody `StreamReader` obiektu.

## <a name="to-read-from-a-text-file"></a>Aby odczytać z pliku tekstowego

Użyj `ReadAllText` metody `My.Computer.FileSystem` obiektu, aby odczytać zawartość pliku tekstowego w ciągu, dostarczając ścieżkę. Poniższy przykład odczytuje zawartość test.txt jako ciąg i wyświetla go w oknie komunikatu.

[!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]

### <a name="to-read-from-a-text-file-that-is-encoded"></a>Aby odczytać z pliku tekstowego, który jest kodowany

Użyj `ReadAllText` metody `My.Computer.FileSystem` obiektu, aby odczytać zawartość pliku tekstowego w ciągu, podając ścieżkę i typ kodowania pliku. Poniższy przykład odczytuje zawartość pliku z kodowaniem UTF32 test.txt jako ciąg i wyświetla go w oknie komunikatu.

[!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]

## <a name="robust-programming"></a>Niezawodne programowanie

Następujące warunki mogą spowodować wyjątek:

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

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [Odczyt z plików](reading-from-files.md)
- [Instrukcje: Odczyt z rozdzielonych przecinkami plików testowych](how-to-read-from-comma-delimited-text-files.md)
- [Instrukcje: Odczyt z plików testowych o stałej szerokości](how-to-read-from-fixed-width-text-files.md)
- [Instrukcje: Odczyt z plików tekstowych w wielu formatach](how-to-read-from-text-files-with-multiple-formats.md)
- [Rozwiązywanie problemów: Odczytywanie z plików tekstowych oraz zapisywanie w nich](troubleshooting-reading-from-and-writing-to-text-files.md)
- [Wskazówki: manipulowanie plikami i katalogami w Visual Basic](walkthrough-manipulating-files-and-directories.md)
- [Kodowanie pliku](file-encodings.md)
