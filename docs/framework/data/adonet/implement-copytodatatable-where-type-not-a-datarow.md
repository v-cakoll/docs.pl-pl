---
title: 'Instrukcje: Implementowanie CopyToDataTable<T>, gdzie ogólny typ T nie jest elementem DataRow'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 4ec609ac38b3fa91a4b11b93e24b465f48696a9e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159236"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a>Instrukcje: Implementowanie CopyToDataTable\<T > gdzie ogólny typ T nie jest elementem DataRow
<xref:System.Data.DataTable> Obiektu jest często używana do wiązania danych. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda pobiera wyniki zapytania i kopiuje dane do <xref:System.Data.DataTable>, która następnie umożliwia powiązanie danych. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metod, jednak działać tylko w odniesieniu <xref:System.Collections.Generic.IEnumerable%601> źródła gdzie parametr ogólny `T` typu <xref:System.Data.DataRow>. Mimo że jest to przydatne, nie zezwala tabel, które ma zostać utworzony z sekwencji typami skalarnymi, zapytania, które anonimowych typów projektów lub zapytania, które wykonują sprzężeń tabel.  
  
 W tym temacie opisano sposób implementacji niestandardowego dwóch `CopyToDataTable<T>` metody rozszerzenia, które akceptują parametr ogólny `T` typu innego niż <xref:System.Data.DataRow>. Logic Apps, aby utworzyć <xref:System.Data.DataTable> z <xref:System.Collections.Generic.IEnumerable%601> źródła znajduje się w `ObjectShredder<T>` klasy, która jest następnie opakowywany w dwóch przeciążone `CopyToDataTable<T>` metody rozszerzenia. `Shred` Metody `ObjectShredder<T>` Klasa zwraca wypełniony <xref:System.Data.DataTable> i przyjmuje trzy parametry wejściowe: <xref:System.Collections.Generic.IEnumerable%601> źródła <xref:System.Data.DataTable>, a <xref:System.Data.LoadOption> wyliczenia. Schemat początkowy zwracanego <xref:System.Data.DataTable> opiera się na schemat typu `T`. Jeśli nie podano istniejącej tabeli jako dane wejściowe, schemat musi być spójne ze schematem typu `T`. Każdej publicznej właściwości i pola typu `T` jest konwertowana na <xref:System.Data.DataColumn> w tabeli zwracane. Jeśli sekwencja źródłowa zawiera typ pochodzący od `T`, schemat tabeli zwracane podzielonego na wszelkie dodatkowe właściwości publiczne i pola.  
  
 Przykłady użycia niestandardowej `CopyToDataTable<T>` metod, zobacz [Tworzenie elementu DataTable z zapytania](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a>Implementacji niestandardowego CopyToDataTable\<T > metodami w aplikacji  
  
1.  Implementowanie `ObjectShredder<T>` klasy w celu utworzenia <xref:System.Data.DataTable> z <xref:System.Collections.Generic.IEnumerable%601> źródła:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    Poprzedni przykład założono, że właściwości `DataColumn` nie są typy dopuszczające wartości null. Aby obsłużyć właściwości z typami zerowalnymi, użyj następującego kodu:

    ```csharp
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);
    ```

2.  Implementowanie niestandardowego `CopyToDataTable<T>` metody rozszerzenia w klasie:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3.  Dodaj `ObjectShredder<T>` klasy i `CopyToDataTable<T>` metody rozszerzenia do aplikacji.  
  
```vb  
Module Module1  
    Sub Main()  
        ' Your application code using CopyToDataTable<T>.  
    End Sub  
End Module  
  
Public Module CustomLINQtoDataSetMethods  
…  
End Module  
  
Public Class ObjectShredder(Of T)  
…  
End Class
```
  
```csharp
class Program  
{  
    static void Main(string[] args)  
    {  
        // Your application code using CopyToDataTable<T>.  
    }  
}  
public static class CustomLINQtoDataSetMethods  
{  
…  
}  
public class ObjectShredder<T>  
{  
…  
}  
```
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie elementu DataTable na podstawie zapytania](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)
- [Przewodnik programowania](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
