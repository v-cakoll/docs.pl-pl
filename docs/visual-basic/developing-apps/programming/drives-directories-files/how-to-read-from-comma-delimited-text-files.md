---
title: 'Instrukcje: odczyt z rozdzielonych przecinkami plików tekstowych'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: ba62a0226a1a83326cbc7ab393d135763a7c7cb2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411645"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a>Instrukcje: odczyt z rozdzielonych przecinkami plików tekstowych w Visual Basic

`TextFieldParser`Obiekt umożliwia łatwe i wydajne analizowanie strukturalnych plików tekstowych, takich jak dzienniki. `TextFieldType`Właściwość określa, czy jest to plik rozdzielany, czy jeden z polami o stałej szerokości tekstu.  
  
### <a name="to-parse-a-comma-delimited-text-file"></a>Aby przeanalizować plik tekstowy rozdzielany przecinkami  
  
1. Utwórz nowy element `TextFieldParser`. Poniższy kod tworzy `TextFieldParser` nazwę `MyReader` i otwiera plik `test.txt` .  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. Zdefiniuj `TextField` Typ i ogranicznik. Poniższy kod definiuje `TextFieldType` Właściwość jako `Delimited` i ogranicznik jako ",".  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. Przepętlenie przez pola w pliku. Jeśli wszystkie wiersze są uszkodzone, zgłoś błąd i Kontynuuj analizowanie. Poniższy kod pętle za pomocą pliku, wyświetlając każde pole z kolei i zgłasza wszystkie pola, które są sformatowane nieprawidłowo.  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. Zamknij `While` bloki i i `Using` `End While` `End Using` .  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a>Przykład  

 Ten przykład odczytuje z pliku `test.txt` .  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą spowodować wyjątek:  
  
- Nie można przeanalizować wiersza przy użyciu określonego formatu ( <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> ). Komunikat o wyjątku określa wiersz powodujący wyjątek, podczas gdy <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> Właściwość jest przypisana do tekstu zawartego w wierszu.  
  
- Określony plik nie istnieje ( <xref:System.IO.FileNotFoundException> ).  
  
- Sytuacja częściowej relacji zaufania, w której użytkownik nie ma wystarczających uprawnień dostępu do pliku. (<xref:System.Security.SecurityException>).  
  
- Ścieżka jest za długa ( <xref:System.IO.PathTooLongException> ).  
  
- Użytkownik nie ma wystarczających uprawnień dostępu do pliku ( <xref:System.UnauthorizedAccessException> ).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [Instrukcje: Odczyt z plików testowych o stałej szerokości](how-to-read-from-fixed-width-text-files.md)
- [Instrukcje: Odczyt z plików tekstowych w wielu formatach](how-to-read-from-text-files-with-multiple-formats.md)
- [Analizowanie plików tekstowych za pomocą obiektu TextFieldParser](parsing-text-files-with-the-textfieldparser-object.md)
- [Wskazówki: manipulowanie plikami i katalogami w Visual Basic](walkthrough-manipulating-files-and-directories.md)
- [Rozwiązywanie problemów: Odczytywanie z plików tekstowych oraz zapisywanie w nich](troubleshooting-reading-from-and-writing-to-text-files.md)
