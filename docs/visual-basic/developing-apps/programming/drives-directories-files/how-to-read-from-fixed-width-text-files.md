---
title: 'Porady: Odczyt z plików testowych o stałej szerokości w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: de60bbe111de151ac358c1b1c00a14dee225447d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344068"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a>Porady: Odczyt z plików testowych o stałej szerokości w Visual Basic
`TextFieldParser` Obiekt umożliwia łatwe oraz efektywne analizowanie strukturyzowanych plików tekstowych, takie jak dzienniki.  
  
 `TextFieldType` Właściwość definiuje, czy przeanalizowany plik jest rozdzielany plik lub taki, który ma pola o stałej szerokości tekstu. Plik tekstowy stałej szerokości pola na końcu mogą mieć szerokość zmiennej. Aby określić, że pole na końcu ma szerokość zmiennej, zdefiniuj ma szerokość mniejszą lub równą zero.  
  
### <a name="to-parse-a-fixed-width-text-file"></a>Aby przeanalizować plik tekstowy stałej szerokości  
  
1. Utwórz nową `TextFieldParser`. Poniższy kod tworzy `TextFieldParser` o nazwie `Reader` i otwiera plik `test.log`.  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. Zdefiniuj `TextFieldType` właściwość jako `FixedWidth`, definiując szerokość i formatowanie. Poniższy kod definiuje kolumny tekstu. Pierwsza to 5 znaki dwubajtowe, druga 10, 11 trzecia i czwarta to o zmiennej szerokości.  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. W pętli poprzez pól w pliku. Jeśli wiersze są uszkodzone, należy zgłosić błąd i kontynuować analizowanie.  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. Zamknij `While` i `Using` blokuje z `End While` i `End Using`.  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie odczytuje z pliku `test.log`.  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a>Skuteczne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nie można przeanalizować wiersz w określonym formacie (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Komunikat o wyjątku Określa wiersz, powoduje wyjątek, podczas gdy <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> właściwość jest przypisany do tekstu w wierszu.  
  
-   Określony plik nie istnieje (<xref:System.IO.FileNotFoundException>).  
  
-   Sytuacja częściowego zaufania, użytkownik nie ma wystarczających uprawnień dostępu do tego pliku. (<xref:System.Security.SecurityException>).  
  
-   Ścieżka jest zbyt długa (<xref:System.IO.PathTooLongException>).  
  
-   Użytkownik nie ma wystarczających uprawnień dostępu do pliku (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [Instrukcje: Odczyt z rozdzielonych przecinkami plików testowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Instrukcje: Odczyt z plików tekstowych w wielu formatach](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Analizowanie plików tekstowych za pomocą obiektu TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [Przewodnik: Manipulowanie plikami i katalogami w Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Rozwiązywanie problemów: Odczytywanie z plików tekstowych oraz zapisywanie w nich](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
