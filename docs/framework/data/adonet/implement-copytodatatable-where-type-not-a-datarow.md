---
title: 'Instrukcje: Implementowanie CopyToDataTable<T> gdzie ogólny typ T nie jest elementem DataRow'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 6c14e87c5caede4fea52867d9f184f3f64a5ed3b
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249646"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a>Jak: Implementowanie copytodatatable\<T>, w którym typ ogólny T nie jest datarow
Obiekt <xref:System.Data.DataTable> jest często używany do wiązania danych. Metoda <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> pobiera wyniki kwerendy i kopiuje <xref:System.Data.DataTable>dane do programu , który następnie może służyć do wiązania danych. Metody <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> działają jednak tylko na <xref:System.Collections.Generic.IEnumerable%601> źródle, w `T` którym <xref:System.Data.DataRow>parametr ogólny jest typu . Chociaż jest to przydatne, nie zezwala na tworzenie tabel z sekwencji typów skalarnych, z kwerend, które projektują typy anonimowe lub z kwerend, które wykonują sprzężenia tabeli.  
  
 W tym temacie opisano `CopyToDataTable<T>` sposób implementacji dwóch `T` niestandardowych metod <xref:System.Data.DataRow>rozszerzenia, które akceptują ogólny parametr typu innego niż . Logika do <xref:System.Data.DataTable> tworzenia <xref:System.Collections.Generic.IEnumerable%601> ze źródła znajduje `ObjectShredder<T>` się w klasie, która jest `CopyToDataTable<T>` następnie zawijana w dwie przeciążone metody rozszerzenia. Metoda `Shred` `ObjectShredder<T>` <xref:System.Data.DataTable> klasy zwraca wypełnione i akceptuje trzy parametry <xref:System.Collections.Generic.IEnumerable%601> wejściowe: <xref:System.Data.DataTable>źródło, <xref:System.Data.LoadOption> a , i wyliczenie. Początkowy schemat zwracanego <xref:System.Data.DataTable> jest oparty na schemacie `T`typu . Jeśli istniejąca tabela jest dostarczana jako dane wejściowe, schemat `T`musi być zgodny ze schematem typu . Każda właściwość publiczna `T` i pole typu <xref:System.Data.DataColumn> jest konwertowana na w tabeli zwracanej. Jeśli sekwencja źródłowsza `T`zawiera typ pochodny , zwracany schemat tabeli jest rozwijany dla wszelkich dodatkowych właściwości publicznych lub pól.  
  
 Aby zapoznać się `CopyToDataTable<T>` z przykładami użycia metod niestandardowych, zobacz [Tworzenie tabeli data z kwerendy](creating-a-datatable-from-a-query-linq-to-dataset.md).  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a>Aby zaimplementować niestandardowe metody> W> CopyToDataTable\<w aplikacji  
  
1. `ObjectShredder<T>` Zaimplementuj <xref:System.Data.DataTable> klasę, aby utworzyć źródło: <xref:System.Collections.Generic.IEnumerable%601>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    W poprzednim przykładzie przyjęto założenie, `DataColumn` że właściwości nie są typami wartości nullable. Aby obsłużyć właściwości z typami wartości z do wartości null, należy użyć następującego kodu:

    ```csharp
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);
    ```

2. Zaimplementuj niestandardowe `CopyToDataTable<T>` metody rozszerzenia w klasie:  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. `ObjectShredder<T>` Dodaj klasy `CopyToDataTable<T>` i metody rozszerzenia do aplikacji.  
  
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
- [Przewodnik po programowaniu](programming-guide-linq-to-dataset.md)
