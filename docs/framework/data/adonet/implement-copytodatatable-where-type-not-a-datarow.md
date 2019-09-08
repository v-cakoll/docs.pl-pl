---
title: 'Instrukcje: Implementowanie CopyToDataTable<T>, gdzie ogólny typ T nie jest elementem DataRow'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 27df5e88b93914d317f0f59c704382bde67534d2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794999"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a>Instrukcje: Zaimplementuj\<CopyToDataTable T >, gdzie typ ogólny t nie jest typem DataRow
<xref:System.Data.DataTable> Obiekt jest często używany do wiązania danych. Metoda pobiera wyniki zapytania i kopiuje dane <xref:System.Data.DataTable>do, które mogą być następnie używane do wiązania danych. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metody, jednak działają tylko <xref:System.Collections.Generic.IEnumerable%601> na źródle, gdzie parametr `T` generyczny jest typu <xref:System.Data.DataRow>. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Chociaż jest to przydatne, nie zezwala na tworzenie tabel z sekwencji typów skalarnych, od zapytań, które są typami anonimowymi projektu, lub z zapytań, które wykonują sprzężenia tabeli.  
  
 W tym temacie opisano sposób implementacji dwóch niestandardowych `CopyToDataTable<T>` metod rozszerzenia, które akceptują parametr `T` ogólny typu innego niż <xref:System.Data.DataRow>. Logika <xref:System.Data.DataTable> do utworzenia <xref:System.Collections.Generic.IEnumerable%601> ze `ObjectShredder<T>` źródła jest zawarta w klasie, która następnie jest opakowana w dwie przeciążone `CopyToDataTable<T>` metody rozszerzenia. `Shred` Metoda <xref:System.Collections.Generic.IEnumerable%601> klasyzwraca<xref:System.Data.DataTable>wypełnione iakceptuje<xref:System.Data.LoadOption> trzy parametry wejściowe: Źródło, a i Wyliczenie. <xref:System.Data.DataTable> `ObjectShredder<T>` Początkowy schemat zwracanych <xref:System.Data.DataTable> danych opiera się na schemacie typu `T`. Jeśli istniejąca tabela jest dostarczana jako dane wejściowe, schemat musi być spójny ze schematem typu `T`. Każda publiczna właściwość i pole typu `T` jest konwertowane <xref:System.Data.DataColumn> na w zwracanej tabeli. Jeśli sekwencja źródłowa zawiera typ pochodzący z `T`, zwracany schemat tabeli jest rozwinięty dla wszystkich dodatkowych właściwości publicznych lub pól.  
  
 Przykłady użycia metod niestandardowych `CopyToDataTable<T>` można znaleźć w temacie [Creating a DataTable from a Query](creating-a-datatable-from-a-query-linq-to-dataset.md).  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a>Aby zaimplementować niestandardowe metody CopyToDataTable\<> T w aplikacji  
  
1. Zaimplementuj <xref:System.Data.DataTable> <xref:System.Collections.Generic.IEnumerable%601> klasę, aby utworzyć obiekt ze źródła: `ObjectShredder<T>`  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    W poprzednim przykładzie przyjęto założenie, że `DataColumn` właściwości nie są typami dopuszczającymi wartość null. Aby obsłużyć właściwości z typami dopuszczających wartości null, użyj następującego kodu:

    ```csharp
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);
    ```

2. Zaimplementuj niestandardowe `CopyToDataTable<T>` metody rozszerzenia w klasie:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. Dodaj klasę i `CopyToDataTable<T>` metody rozszerzenia do aplikacji. `ObjectShredder<T>`  
  
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

- [Tworzenie elementu DataTable na podstawie zapytania](creating-a-datatable-from-a-query-linq-to-dataset.md)
- [Przewodnik programowania](programming-guide-linq-to-dataset.md)
