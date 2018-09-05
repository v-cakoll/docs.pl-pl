---
title: 'Porady: Zmienianie kolejności pól w rozdzielonym pliku (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c451c7db-663b-4daf-b8ba-a2093095d672
ms.openlocfilehash: 7d385473c461540c81d35d42d664ef0a8b7c054b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527892"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a>Porady: Zmienianie kolejności pól w rozdzielonym pliku (LINQ) (Visual Basic)
Plik wartości rozdzielanych przecinkami (CSV) to plik tekstowy, który jest często używana do przechowywania danych w arkuszu kalkulacyjnym lub inne dane tabelaryczne, który jest reprezentowany przez wierszy i kolumn. Za pomocą <xref:System.String.Split%2A> metodę, aby rozdzielić pola, jest bardzo proste w celu wykonywania zapytań i manipulowania plików CSV za pomocą LINQ. W rzeczywistości tej samej techniki można zmieniać kolejność części ze strukturą wiersza tekstu. nie jest ograniczona do plików CSV.  
  
 W poniższym przykładzie przyjęto założenie, że trzy kolumny reprezentują studentów "last name," "imię" i "identyfikator". Pola są w kolejności alfabetycznej, w oparciu o nazwiska uczniów. Zapytanie tworzy nową sekwencję, w której kolumna Identyfikatora pojawiają się pierwsze, następuje drugiej kolumny, która łączy imię i Nazwisko ucznia. Wiersze zostaną ponownie uporządkowane według pola identyfikator. Wyniki są zapisywane do nowego pliku i oryginalnych danych nie jest modyfikowany.  
  
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
 [Instrukcje: generowanie kodu XML z plików CSV](https://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd)
