---
title: 'Jak: czytać z tekstu o stałej szerokości Pliki'
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: 3cea9bfe2388f0ca510b15cb020f899b81c4603c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334626"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a>Jak: odczyt z plików tekstowych o stałej szerokości w języku Visual Basic

Obiekt `TextFieldParser` umożliwia łatwą i wydajną analizowanie plików tekstowych strukturalnych, takich jak dzienniki.  
  
 Właściwość `TextFieldType` określa, czy analizowany plik jest plikiem rozdzielanym, czy plikiem zawierającym pola tekstu o stałej szerokości. W pliku tekstowym o stałej szerokości pole na końcu może mieć zmienną szerokość. Aby określić, że pole na końcu ma zmienną szerokość, zdefiniuj go tak, aby szerokość była mniejsza lub równa zeru.  
  
### <a name="to-parse-a-fixed-width-text-file"></a>Aby przeanalizować plik tekstowy o stałej szerokości  
  
1. Utwórz nowy element `TextFieldParser`. Poniższy kod `TextFieldParser` tworzy `Reader` nazwany i `test.log`otwiera plik .  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. Zdefiniuj `TextFieldType` właściwość jako `FixedWidth`, definiując szerokość i format. Poniższy kod definiuje kolumny tekstu; pierwszy ma szerokość 5 znaków, drugi 10, trzeci 11, a czwarty ma zmienną szerokość.  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. Pętla przez pola w pliku. Jeśli którekolwiek wiersze są uszkodzone, zgłoś błąd i kontynuuj analizowanie.  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. Zamknij `While` i `Using` bloki `End While` `End Using`z i .  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a>Przykład  

 W tym przykładzie `test.log`odczytuje się z pliku .  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a>Solidne programowanie  

 Następujące warunki mogą spowodować wyjątek:  
  
- Nie można przeanalizować wiersza przy<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>użyciu określonego formatu ( ). Komunikat o wyjątku określa wiersz powodujący <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> wyjątek, podczas gdy właściwość jest przypisana do tekstu zawartego w wierszu.  
  
- Określony plik nie istnieje<xref:System.IO.FileNotFoundException>( ).  
  
- Sytuacja częściowego zaufania, w której użytkownik nie ma wystarczających uprawnień dostępu do pliku. (<xref:System.Security.SecurityException>).  
  
- Ścieżka jest za<xref:System.IO.PathTooLongException>długa ( ).  
  
- Użytkownik nie ma wystarczających uprawnień dostępu<xref:System.UnauthorizedAccessException>do pliku ( ).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [Porady: odczyt z rozdzielonych przecinkami plików testowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Instrukcje: odczyt z plików tekstowych w wielu formatach](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Analizowanie plików tekstowych za pomocą obiektu TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [Wskazówki: manipulowanie plikami i katalogami w Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Rozwiązywanie problemów: odczytywanie z oraz zapisywanie w plikach tekstowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
