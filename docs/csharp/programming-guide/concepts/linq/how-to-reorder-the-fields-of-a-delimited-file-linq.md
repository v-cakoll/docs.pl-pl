---
title: 'Instrukcje: Zmienianie kolejności pól w rozdzielonym pliku (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 4e62d82c-61b7-4f18-b9a1-86723746d7d2
ms.openlocfilehash: ff8782571bccabe17e9c01331339cf729ff6620a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314987"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a>Instrukcje: Zmienianie kolejności pól w rozdzielonym pliku (LINQ) (C#)
Plik wartości rozdzielanych przecinkami (CSV) to plik tekstowy, który jest często używana do przechowywania danych w arkuszu kalkulacyjnym lub inne dane tabelaryczne, który jest reprezentowany przez wierszy i kolumn. Za pomocą <xref:System.String.Split%2A> metodę, aby rozdzielić pola, jest bardzo proste w celu wykonywania zapytań i manipulowania plików CSV za pomocą LINQ. W rzeczywistości tej samej techniki można zmieniać kolejność części ze strukturą wiersza tekstu. nie jest ograniczona do plików CSV.  
  
 W poniższym przykładzie przyjęto założenie, że trzy kolumny reprezentują studentów "last name," "imię" i "identyfikator". Pola są w kolejności alfabetycznej, w oparciu o nazwiska uczniów. Zapytanie tworzy nową sekwencję, w której kolumna Identyfikatora pojawiają się pierwsze, następuje drugiej kolumny, która łączy imię i Nazwisko ucznia. Wiersze zostaną ponownie uporządkowane według pola identyfikator. Wyniki są zapisywane do nowego pliku i oryginalnych danych nie jest modyfikowany.  
  
### <a name="to-create-the-data-file"></a>Aby utworzyć plik danych  
  
1. Skopiuj następujące wiersze do zwykły plik tekstowy o nazwie spreadsheet1.csv. Zapisz plik w folderze projektu.  
  
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
 Utwórz projekt, który jest przeznaczony dla .NET Framework w wersji 3.5 lub nowszego, za pomocą odwołania do System.Core.dll i `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.  
  
## <a name="see-also"></a>Zobacz także

- [LINQ i ciągi (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
- [LINQ i katalogi plików (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
- [Instrukcje: Generowanie kodu XML z plików CSV (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)
