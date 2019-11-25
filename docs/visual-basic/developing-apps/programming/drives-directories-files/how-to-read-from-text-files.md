---
title: 'How to: Read From Text Files'
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

The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> method of the `My.Computer.FileSystem` object allows you to read from a text file. Kodowanie pliku może być określone, jeśli zawartość pliku używa kodowania, takiego jak ASCII lub UTF-8.

Podczas odczytu z pliku używającego znaków rozszerzonych, trzeba będzie określić kodowanie pliku.

> [!NOTE]
> To read a file a single line of text at a time, use the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> method of the `My.Computer.FileSystem` object. The `OpenTextFileReader` method returns a <xref:System.IO.StreamReader> object. You can use the <xref:System.IO.StreamReader.ReadLine%2A> method of the `StreamReader` object to read a file one line at a time. You can test for the end of the file using the <xref:System.IO.StreamReader.EndOfStream%2A> method of the `StreamReader` object.

## <a name="to-read-from-a-text-file"></a>Aby odczytać z pliku tekstowego

Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path. Poniższy przykład odczytuje zawartość test.txt jako ciąg i wyświetla go w oknie komunikatu.

[!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]

### <a name="to-read-from-a-text-file-that-is-encoded"></a>Aby odczytać z pliku tekstowego, który jest kodowany

Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path and file encoding type. Poniższy przykład odczytuje zawartość pliku z kodowaniem UTF32 test.txt jako ciąg i wyświetla go w oknie komunikatu.

[!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]

## <a name="robust-programming"></a>Niezawodne programowanie

Następujące warunki mogą spowodować wyjątek:

- The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).

- The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).

- The file does not exist (<xref:System.IO.FileNotFoundException>).

- The file is in use by another process or an I/O error occurs (<xref:System.IO.IOException>).

- The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).

- A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).

- There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).

- The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).

Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. For example, the file Form1.vb may not be a Visual Basic source file.

Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji. Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [Odczyt z plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Instrukcje: odczyt z rozdzielonych przecinkami plików testowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Instrukcje: odczyt z plików testowych o stałej szerokości](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [Instrukcje: odczyt z plików tekstowych w wielu formatach](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Rozwiązywanie problemów: odczytywanie z plików tekstowych oraz zapisywanie w nich](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Walkthrough: Manipulating Files and Directories in Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Kodowanie pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
