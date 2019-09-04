---
title: 'Instrukcje: Zmień kolejność pól rozdzielanego pliku (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 4e62d82c-61b7-4f18-b9a1-86723746d7d2
ms.openlocfilehash: 31cb7b936f58653e6223501f3b03cd9472b92453
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253459"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a>Instrukcje: Zmień kolejność pól rozdzielanego pliku (LINQ) (C#)
Plik wartości rozdzielanych przecinkami (CSV) to plik tekstowy, który jest często używany do przechowywania danych arkusza kalkulacyjnego lub innych danych tabelarycznych, które są reprezentowane przez wiersze i kolumny. Za pomocą <xref:System.String.Split%2A> metody do rozdzielania pól, można bardzo łatwo wysyłać zapytania do plików CSV i manipulować nimi przy użyciu LINQ. W rzeczywistości ta sama technika może służyć do zmiany kolejności części dowolnego strukturalnego wiersza tekstu. nie jest to ograniczone do plików CSV.  
  
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
Utwórz projekt C# aplikacji konsolowej z `using` dyrektywami dotyczącymi przestrzeni nazw System. LINQ i system.IO.
  
## <a name="see-also"></a>Zobacz także

- [LINQ i ciągi (C#)](./linq-and-strings.md)
- [LINQ i katalogi plików (C#)](./linq-and-file-directories.md)
- [Instrukcje: Generuj XML z plików CSV (C#)](./how-to-generate-xml-from-csv-files.md)
