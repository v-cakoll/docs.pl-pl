---
title: "Porady: Zmienianie kolejności pól w rozdzielonym pliku (LINQ) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c451c7db-663b-4daf-b8ba-a2093095d672
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f308495a21b671edf03fbd791ef77d668d55388d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a>Porady: Zmienianie kolejności pól w rozdzielonym pliku (LINQ) (Visual Basic)
Plik wartości rozdzielanych przecinkami (CSV) to plik tekstowy, który jest często używany do przechowywania danych arkusza kalkulacyjnego lub innych danych tabelarycznych reprezentowanego przez wierszy i kolumn. Za pomocą <xref:System.String.Split%2A> metodę, aby rozdzielić pola, jest bardzo proste w celu wykonywania zapytań i manipulowania plików CSV za pomocą LINQ. W rzeczywistości tę samą metodę można zmienić kolejność części strukturalnych wiersza tekstu. nie jest ograniczona do plików CSV.  
  
 W poniższym przykładzie przyjęto założenie, że trzy kolumny reprezentują studentów "nazwisko," "imię" i "Identyfikatora." Pola są w kolejności alfabetycznej na podstawie nazw ostatniego studentów. Zapytanie spowoduje utworzenie nowej sekwencji, w których w kolumnie Identyfikator występuje jako pierwszy, następuje drugiej kolumny, która łączy imię i nazwisko studenta. Wiersze zostaną ponownie uporządkowane według pola identyfikator. Wyniki są zapisywane w nowym pliku i oryginalnych danych nie jest modyfikowany.  
  
### <a name="to-create-the-data-file"></a>Aby utworzyć plik danych  
  
1.  Skopiuj następujące wiersze do zwykły plik tekstowy o nazwie spreadsheet1.csv. Zapisz plik w folderze projektu.  
  
    ```  
    Adams,Terry,120  
    Fakhouri,Fadi,116  
    Feng,Hanying,117  
    Garcia,Cesar,114  
    Garcia,Debra,115  
    Garcia,Hugo,118  
    Mortensen,Sven,113  
    O'Donnell,Claire,112  
    Omelchenko,Svetlana,111  
    Tucker,Lance,119  
    Tucker,Michael,122  
    Zabokritski,Eugene,121  
    ```  
  
## <a name="example"></a>Przykład  
  
```vb  
Class CSVFiles  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data source.  
        Dim lines As String() = System.IO.File.ReadAllLines("../../../spreadsheet1.csv")  
  
        ' Execute the query. Put field 2 first, then  
        ' reverse and combine fields 0 and 1 from the old field  
        Dim lineQuery = From line In lines   
                        Let x = line.Split(New Char() {","})   
                        Order By x(2)   
                        Select x(2) & ", " & (x(1) & " " & x(0))  
  
        ' Execute the query and write out the new file. Note that WriteAllLines  
        ' takes a string array, so ToArray is called on the query.  
        System.IO.File.WriteAllLines("../../../spreadsheet2.csv", lineQuery.ToArray())  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output to spreadsheet2.csv:  
' 111, Svetlana Omelchenko  
' 112, Claire O'Donnell  
' 113, Sven Mortensen  
' 114, Cesar Garcia  
' 115, Debra Garcia  
' 116, Fadi Fakhouri  
' 117, Hanying Feng  
' 118, Hugo Garcia  
' 119, Lance Tucker  
' 120, Terry Adams  
' 121, Eugene Zabokritski  
' 122, Michael Tucker  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ i ciągi (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 [LINQ i katalogi plików (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 [Porady: generowanie kodu XML z plików CSV](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd)
