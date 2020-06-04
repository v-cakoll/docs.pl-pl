---
title: 'Instrukcje: odczyt z plików tekstowych o stałej szerokości'
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: 77b2e0a4ebe36b68501f821ef5731935ee3b16a7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411632"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a>Instrukcje: odczyt z plików tekstowych o stałej szerokości w Visual Basic

`TextFieldParser`Obiekt umożliwia łatwe i wydajne analizowanie strukturalnych plików tekstowych, takich jak dzienniki.  
  
 `TextFieldType`Właściwość określa, czy przeanalizowany plik jest plikiem rozdzielanym, czy też ma pola o stałej szerokości tekstu. W pliku tekstowym o stałej szerokości pole na końcu może mieć zmienną szerokość. Aby określić, że pole na końcu ma zmienną szerokość, zdefiniuj ją tak, aby miała szerokość mniejszą lub równą zero.  
  
### <a name="to-parse-a-fixed-width-text-file"></a>Aby przeanalizować plik tekstowy o stałej szerokości  
  
1. Utwórz nowy element `TextFieldParser`. Poniższy kod tworzy `TextFieldParser` nazwę `Reader` i otwiera plik `test.log` .  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. Zdefiniuj `TextFieldType` Właściwość jako `FixedWidth` definiującą szerokość i format. Poniższy kod definiuje kolumny tekstu. pierwsze z nich to 5 znaków szerokości, drugi 10, trzeci 11, a czwarta jest szerokość zmiennej.  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. Przepętlenie przez pola w pliku. Jeśli wszystkie wiersze są uszkodzone, zgłoś błąd i Kontynuuj analizowanie.  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. Zamknij `While` bloki i i `Using` `End While` `End Using` .  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a>Przykład  

 Ten przykład odczytuje z pliku `test.log` .  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą spowodować wyjątek:  
  
- Nie można przeanalizować wiersza przy użyciu określonego formatu ( <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> ). Komunikat o wyjątku określa wiersz powodujący wyjątek, podczas gdy <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> Właściwość jest przypisana do tekstu zawartego w wierszu.  
  
- Określony plik nie istnieje ( <xref:System.IO.FileNotFoundException> ).  
  
- Sytuacja częściowej relacji zaufania, w której użytkownik nie ma wystarczających uprawnień dostępu do pliku. (<xref:System.Security.SecurityException>).  
  
- Ścieżka jest za długa ( <xref:System.IO.PathTooLongException> ).  
  
- Użytkownik nie ma wystarczających uprawnień dostępu do pliku ( <xref:System.UnauthorizedAccessException> ).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [Instrukcje: Odczyt z rozdzielonych przecinkami plików testowych](how-to-read-from-comma-delimited-text-files.md)
- [Instrukcje: Odczyt z plików tekstowych w wielu formatach](how-to-read-from-text-files-with-multiple-formats.md)
- [Analizowanie plików tekstowych za pomocą obiektu TextFieldParser](parsing-text-files-with-the-textfieldparser-object.md)
- [Wskazówki: manipulowanie plikami i katalogami w Visual Basic](walkthrough-manipulating-files-and-directories.md)
- [Rozwiązywanie problemów: Odczytywanie z plików tekstowych oraz zapisywanie w nich](troubleshooting-reading-from-and-writing-to-text-files.md)
