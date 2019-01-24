---
title: 'Porady: Odczyt z plików tekstowych rozdzielonych przecinkami, w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: 050f8635e1cb0fa1a2dd29249873e3bf12dad121
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520389"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a>Porady: Odczyt z plików tekstowych rozdzielonych przecinkami, w języku Visual Basic
`TextFieldParser` Obiekt umożliwia łatwe oraz efektywne analizowanie strukturyzowanych plików tekstowych, takie jak dzienniki. `TextFieldType` Właściwość definiuje, czy jest rozdzielonym pliku lub jednego z polami o stałej szerokości tekstu.  
  
### <a name="to-parse-a-comma-delimited-text-file"></a>Aby przeanalizować z przecinkiem na końcu, rozdzielanego pliku tekstowego  
  
1.  Utwórz nową `TextFieldParser`. Poniższy kod tworzy `TextFieldParser` o nazwie `MyReader` i otwiera plik `test.txt`.  
  
     [!code-vb[VbFileIORead#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_1.vb)]  
  
2.  Zdefiniuj `TextField` typu i ogranicznik. Poniższy kod definiuje `TextFieldType` właściwość jako `Delimited` i ogranicznik jako ",".  
  
     [!code-vb[VbFileIORead#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_2.vb)]  
  
3.  W pętli poprzez pól w pliku. Jeśli wiersze są uszkodzone, należy zgłosić błąd i kontynuować analizowanie. Poniższy kod wykonuje pętlę za pomocą pliku, z kolei wyświetlania poszczególnych pól i raportowanie wszystkich pól, które są niepoprawnie sformatowane.  
  
     [!code-vb[VbFileIORead#17](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_3.vb)]  
  
4.  Zamknij `While` i `Using` blokuje z `End While` i `End Using`.  
  
     [!code-vb[VbFileIORead#18](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_4.vb)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie odczytuje z pliku `test.txt`.  
  
 [!code-vb[VbFileIORead#19](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_5.vb)]  
  
## <a name="robust-programming"></a>Skuteczne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nie można przeanalizować wiersz w określonym formacie (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Komunikat o wyjątku Określa wiersz, powoduje wyjątek, podczas gdy <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> właściwość jest przypisany tekst zawarty w wierszu.  
  
-   Określony plik nie istnieje (<xref:System.IO.FileNotFoundException>).  
  
-   Sytuacja częściowego zaufania, użytkownik nie ma wystarczających uprawnień dostępu do tego pliku. (<xref:System.Security.SecurityException>).  
  
-   Ścieżka jest zbyt długa (<xref:System.IO.PathTooLongException>).  
  
-   Użytkownik nie ma wystarczających uprawnień dostępu do pliku (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [Instrukcje: Odczyt z plików testowych o stałej szerokości](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [Instrukcje: Odczyt z plików tekstowych w wielu formatach](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Analizowanie plików tekstowych za pomocą obiektu TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [Przewodnik: Manipulowanie plikami i katalogami w Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Rozwiązywanie problemów: Odczytywanie z oraz zapisywanie w plikach tekstowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
