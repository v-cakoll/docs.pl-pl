---
title: 'Porady: Zmienianie kolejności pól w rozdzielonym pliku (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 4e62d82c-61b7-4f18-b9a1-86723746d7d2
ms.openlocfilehash: 4b7485ff80ef02b7d12980d8ede29cf926027f93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a>Porady: Zmienianie kolejności pól w rozdzielonym pliku (LINQ) (C#)
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
  
```csharp  
class CSVFiles  
{  
    static void Main(string[] args)  
    {  
        // Create the IEnumerable data source  
        string[] lines = System.IO.File.ReadAllLines(@"../../../spreadsheet1.csv");  
  
        // Create the query. Put field 2 first, then  
        // reverse and combine fields 0 and 1 from the old field  
        IEnumerable<string> query =  
            from line in lines  
            let x = line.Split(',')  
            orderby x[2]  
            select x[2] + ", " + (x[1] + " " + x[0]);  
  
        // Execute the query and write out the new file. Note that WriteAllLines  
        // takes a string[], so ToArray is called on the query.  
        System.IO.File.WriteAllLines(@"../../../spreadsheet2.csv", query.ToArray());  
  
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output to spreadsheet2.csv:  
111, Svetlana Omelchenko  
112, Claire O'Donnell  
113, Sven Mortensen  
114, Cesar Garcia  
115, Debra Garcia  
116, Fadi Fakhouri  
117, Hanying Feng  
118, Hugo Garcia  
119, Lance Tucker  
120, Terry Adams  
121, Eugene Zabokritski  
122, Michael Tucker  
 */  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ i ciągi (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 [LINQ i katalogi plików (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
 [Instrukcje: generowanie kodu XML z plików CSV](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd)
