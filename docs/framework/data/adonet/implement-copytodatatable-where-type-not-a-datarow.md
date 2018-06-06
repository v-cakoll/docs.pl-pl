---
title: 'Porady: Implementowanie CopyToDataTable&lt;T&gt; gdzie ogólny typ T nie jest element DataRow'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 106442c26f0bb02cf57dcc5d8b1ac534c70320ac
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753516"
---
# <a name="how-to-implement-copytodatatablelttgt-where-the-generic-type-t-is-not-a-datarow"></a>Porady: Implementowanie CopyToDataTable&lt;T&gt; gdzie ogólny typ T nie jest element DataRow
<xref:System.Data.DataTable> Obiekt jest często używany do wiązania danych. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda pobiera wyników zapytania i kopiuje dane na <xref:System.Data.DataTable>, której następnie można użyć dla powiązania danych. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metod, jednak wykonywać operacje tylko na <xref:System.Collections.Generic.IEnumerable%601> źródła gdzie parametr generyczny `T` jest typu <xref:System.Data.DataRow>. Chociaż jest to przydatne, nie zezwala tabele, aby utworzyć sekwencję typy skalarne, z zapytań, które typy anonimowe projektu lub z zapytań, które wykonują sprzężeń tabel.  
  
 W tym temacie opisano implementowania niestandardowych dwóch `CopyToDataTable<T>` metody rozszerzenia, które akceptują parametr ogólny `T` typu innego niż <xref:System.Data.DataRow>. Logika tworzenia <xref:System.Data.DataTable> z <xref:System.Collections.Generic.IEnumerable%601> źródła znajduje się w `ObjectShredder<T>` klasy, która jest następnie opakowane w dwóch przeciążony `CopyToDataTable<T>` metody rozszerzenia. `Shred` Metody `ObjectShredder<T>` Klasa zwraca wypełniony <xref:System.Data.DataTable> i przyjmuje trzy parametry wejściowe: <xref:System.Collections.Generic.IEnumerable%601> źródła, <xref:System.Data.DataTable>, a <xref:System.Data.LoadOption> wyliczenia. Początkowa schematu, zwracana <xref:System.Data.DataTable> opiera się na schemat typu `T`. W przypadku istniejącej tabeli jako dane wejściowe schematu muszą być zgodne ze schematem typu `T`. Każdej publicznej właściwości i pola typu `T` jest konwertowana na <xref:System.Data.DataColumn> w tabeli zwracanych. Jeśli typ pochodny typu zawiera sekwencji źródłowej `T`, schemat tabeli zwracane jest rozwinięta dla wszelkie dodatkowe właściwości publiczne i pola.  
  
 Przykłady przy użyciu niestandardowego `CopyToDataTable<T>` metod, zobacz [tworzenie DataTable z zapytania](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a>Implementacji niestandardowego CopyToDataTable\<T > metod w aplikacji  
  
1.  Implementowanie `ObjectShredder<T>` klasy w celu utworzenia <xref:System.Data.DataTable> z <xref:System.Collections.Generic.IEnumerable%601> źródła:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    Powyższy przykład zakłada się, że właściwości `DataColumn` nie są typy dopuszczające wartości zerowe. Aby obsługiwać właściwości z typami wartości null, należy użyć poniższego kodu:

    ```csharp
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);
    ```

2.  Implementowanie niestandardowego `CopyToDataTable<T>` metody rozszerzenia klasy:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3.  Dodaj `ObjectShredder<T>` klasy i `CopyToDataTable<T>` metody rozszerzenia dla aplikacji.  
  
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
 [Tworzenie elementu DataTable na podstawie zapytania](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)  
 [Przewodnik programowania](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
