---
title: "Porady: Odczyt z plików testowych o stałej szerokości w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a5caa124af1bf4681a4c061f453ce5e09ec2dae7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a>Porady: Odczyt z plików testowych o stałej szerokości w Visual Basic
`TextFieldParser` Obiektu pozwala łatwo i efektywnie przeanalizować strukturyzowanych plików tekstowych, takich jak dzienniki.  
  
 `TextFieldType` Właściwość określa, czy plik przeanalizowany jest rozdzielonym pliku lub takie, które ma pola o stałej szerokości tekstu. Plik tekstowy stałej szerokości pola na końcu mogą mieć szerokość zmiennej. Aby określić, czy pole na końcu ma o zmiennej szerokości, zdefiniuj on mieć szerokość mniejszą lub równą zero.  
  
### <a name="to-parse-a-fixed-width-text-file"></a>Aby przeanalizować plik tekstowy stałej szerokości  
  
1.  Utwórz nową `TextFieldParser`. Poniższy kod tworzy `TextFieldParser` o nazwie `Reader` i otwarcie pliku `test.log`.  
  
     [!code-vb[VbFileIORead#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_1.vb)]  
  
2.  Zdefiniuj `TextFieldType` właściwość jako `FixedWidth`, definiowanie szerokość i sformatować. Poniższy kod definiuje kolumn tekstu; Pierwsza to 5 znaków, druga 10, 11 trzeci, a czwarta jest o zmiennej szerokości.  
  
     [!code-vb[VbFileIORead#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_2.vb)]  
  
3.  Pętli pól w pliku. Jeśli wiersze są uszkodzone, zgłoś błąd i kontynuować analizowanie.  
  
     [!code-vb[VbFileIORead#11](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_3.vb)]  
  
4.  Zamknij `While` i `Using` blokuje z `End While` i `End Using`.  
  
     [!code-vb[VbFileIORead#12](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_4.vb)]  
  
## <a name="example"></a>Przykład  
 Ten przykład odczytuje z pliku `test.log`.  
  
 [!code-vb[VbFileIORead#13](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_5.vb)]  
  
## <a name="robust-programming"></a>Skuteczne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nie można analizować wiersza w określonym formacie (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Komunikat o wyjątku Określa wiersz przyczyną tego wyjątku, podczas gdy <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> właściwości jest przypisany do zawartych w wierszu tekstu.  
  
-   Określony plik nie istnieje (<xref:System.IO.FileNotFoundException>).  
  
-   Sytuacja częściowego zaufania, użytkownik nie ma wystarczających uprawnień dostępu do tego pliku. (<xref:System.Security.SecurityException>).  
  
-   Ścieżka jest za długa (<xref:System.IO.PathTooLongException>).  
  
-   Użytkownik nie ma wystarczających uprawnień do dostępu do pliku (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Zobacz także  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>  
 [Porady: Odczyt z plików tekstowych rozdzielanych przecinkami](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [Porady: Odczyt z plików tekstowych w wielu formatach](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [Analizowanie plików tekstowych za pomocą obiektu TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 [Wskazówki: Manipulowanie plikami i katalogami w Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 [Rozwiązywanie problemów: Odczytywanie z oraz zapisywanie w plikach tekstowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 
