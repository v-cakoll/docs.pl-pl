---
title: 'Instrukcje: Zmienianie kolejności pól w rozdzielonym pliku (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c451c7db-663b-4daf-b8ba-a2093095d672
ms.openlocfilehash: eaac777941e20dd93a5f352ec04c0c9843825791
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321008"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a>Instrukcje: Zmienianie kolejności pól w rozdzielonym pliku (LINQ) (Visual Basic)
Plik wartości rozdzielanych przecinkami (CSV) to plik tekstowy, który jest często używany do przechowywania danych arkusza kalkulacyjnego lub innych danych tabelarycznych, które są reprezentowane przez wiersze i kolumny. Za pomocą metody <xref:System.String.Split%2A> do rozdzielania pól, można bardzo łatwo wysyłać zapytania do plików CSV i manipulować nimi przy użyciu LINQ. W rzeczywistości ta sama technika może służyć do zmiany kolejności części dowolnego strukturalnego wiersza tekstu. nie jest to ograniczone do plików CSV.  
  
 W poniższym przykładzie Załóżmy, że trzy kolumny reprezentują uczniów "" nazwisko, "imię i nazwisko" i "ID". Pola są w kolejności alfabetycznej na podstawie nazwisk uczniów. Zapytanie generuje nową sekwencję, w której zostanie wyświetlona kolumna ID, a po niej druga kolumna łącząca imię i nazwisko studenta. Wiersze są zmieniane proporcjonalnie do pola ID. Wyniki są zapisywane w nowym pliku, a oryginalne dane nie są modyfikowane.  
  
### <a name="to-create-the-data-file"></a>Aby utworzyć plik danych  
  
1. Skopiuj następujące wiersze do zwykłego pliku tekstowego o nazwie spreadsheet1. csv. Zapisz plik w folderze projektu.  
  
    ```csv  
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
  
## <a name="see-also"></a>Zobacz także

- [LINQ i ciągi (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [LINQ i katalogi plików (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
- [Instrukcje: generowanie kodu XML z plików CSV](../../../../visual-basic/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)
