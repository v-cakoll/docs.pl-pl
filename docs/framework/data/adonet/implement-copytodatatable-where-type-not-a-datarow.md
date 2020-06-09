---
title: 'Instrukcje: Implementowanie CopyToDataTable<T> gdzie ogólny typ T nie jest elementem DataRow'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: a1427747d03f01e52f1ee7ad1fc11d47d310edbe
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590608"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a>Instrukcje: Implementowanie CopyToDataTable\<T> gdzie ogólny typ T nie jest elementem DataRow
<xref:System.Data.DataTable>Obiekt jest często używany do wiązania danych. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Metoda pobiera wyniki zapytania i kopiuje dane do <xref:System.Data.DataTable> , które mogą być następnie używane do wiązania danych. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Metody, jednak działają tylko na <xref:System.Collections.Generic.IEnumerable%601> źródle, gdzie parametr generyczny `T` jest typu <xref:System.Data.DataRow> . Chociaż jest to przydatne, nie zezwala na tworzenie tabel z sekwencji typów skalarnych, od zapytań, które są typami anonimowymi projektu, lub z zapytań, które wykonują sprzężenia tabeli.  
  
 W tym temacie opisano sposób implementacji dwóch niestandardowych `CopyToDataTable<T>` metod rozszerzenia, które akceptują parametr ogólny `T` typu innego niż <xref:System.Data.DataRow> . Logika do utworzenia <xref:System.Data.DataTable> ze <xref:System.Collections.Generic.IEnumerable%601> źródła jest zawarta w `ObjectShredder<T>` klasie, która następnie jest opakowana w dwie przeciążone `CopyToDataTable<T>` metody rozszerzenia. `Shred`Metoda `ObjectShredder<T>` klasy zwraca wypełnione <xref:System.Data.DataTable> i akceptuje trzy parametry wejściowe: <xref:System.Collections.Generic.IEnumerable%601> Źródło, a <xref:System.Data.DataTable> i <xref:System.Data.LoadOption> Wyliczenie. Początkowy schemat zwracanych danych <xref:System.Data.DataTable> opiera się na schemacie typu `T` . Jeśli istniejąca tabela jest dostarczana jako dane wejściowe, schemat musi być spójny ze schematem typu `T` . Każda publiczna właściwość i pole typu `T` jest konwertowane na <xref:System.Data.DataColumn> w zwracanej tabeli. Jeśli sekwencja źródłowa zawiera typ pochodzący z `T` , zwracany schemat tabeli jest rozwinięty dla wszystkich dodatkowych właściwości publicznych lub pól.  
  
 Przykłady użycia `CopyToDataTable<T>` metod niestandardowych można znaleźć w temacie [Creating a DataTable from a Query](creating-a-datatable-from-a-query-linq-to-dataset.md).  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a>Aby zaimplementować niestandardowe metody CopyToDataTable \<T> w aplikacji  
  
1. Zaimplementuj `ObjectShredder<T>` klasę, aby utworzyć obiekt <xref:System.Data.DataTable> ze <xref:System.Collections.Generic.IEnumerable%601> źródła:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    W poprzednim przykładzie przyjęto założenie, że właściwości i pola typu `DataColumn` nie dopuszcza wartości null. Aby obsłużyć właściwości i pola z typami wartości null, użyj następującego kodu:

    ```csharp
    // Nullable-aware code for properties.
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);

    // Nullable-aware code for fields.
    DataColumn dc = table.Columns.Contains(f.Name) ? table.Columns[f.Name] : table.Columns.Add(f.Name, Nullable.GetUnderlyingType(f.FieldType) ?? f.FieldType);
    ```

2. Zaimplementuj niestandardowe `CopyToDataTable<T>` metody rozszerzenia w klasie:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. Dodaj `ObjectShredder<T>` klasę i `CopyToDataTable<T>` metody rozszerzenia do aplikacji.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie elementu DataTable na podstawie zapytania](creating-a-datatable-from-a-query-linq-to-dataset.md)
- [Przewodnik programowania](programming-guide-linq-to-dataset.md)
