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
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="12b5f-102">Instrukcje: Implementowanie CopyToDataTable\<T> gdzie ogólny typ T nie jest elementem DataRow</span><span class="sxs-lookup"><span data-stu-id="12b5f-102">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>
<span data-ttu-id="12b5f-103"><xref:System.Data.DataTable>Obiekt jest często używany do wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="12b5f-103">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="12b5f-104"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Metoda pobiera wyniki zapytania i kopiuje dane do <xref:System.Data.DataTable> , które mogą być następnie używane do wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="12b5f-104">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="12b5f-105"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Metody, jednak działają tylko na <xref:System.Collections.Generic.IEnumerable%601> źródle, gdzie parametr generyczny `T` jest typu <xref:System.Data.DataRow> .</span><span class="sxs-lookup"><span data-stu-id="12b5f-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="12b5f-106">Chociaż jest to przydatne, nie zezwala na tworzenie tabel z sekwencji typów skalarnych, od zapytań, które są typami anonimowymi projektu, lub z zapytań, które wykonują sprzężenia tabeli.</span><span class="sxs-lookup"><span data-stu-id="12b5f-106">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="12b5f-107">W tym temacie opisano sposób implementacji dwóch niestandardowych `CopyToDataTable<T>` metod rozszerzenia, które akceptują parametr ogólny `T` typu innego niż <xref:System.Data.DataRow> .</span><span class="sxs-lookup"><span data-stu-id="12b5f-107">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="12b5f-108">Logika do utworzenia <xref:System.Data.DataTable> ze <xref:System.Collections.Generic.IEnumerable%601> źródła jest zawarta w `ObjectShredder<T>` klasie, która następnie jest opakowana w dwie przeciążone `CopyToDataTable<T>` metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="12b5f-108">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="12b5f-109">`Shred`Metoda `ObjectShredder<T>` klasy zwraca wypełnione <xref:System.Data.DataTable> i akceptuje trzy parametry wejściowe: <xref:System.Collections.Generic.IEnumerable%601> Źródło, a <xref:System.Data.DataTable> i <xref:System.Data.LoadOption> Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="12b5f-109">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="12b5f-110">Początkowy schemat zwracanych danych <xref:System.Data.DataTable> opiera się na schemacie typu `T` .</span><span class="sxs-lookup"><span data-stu-id="12b5f-110">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="12b5f-111">Jeśli istniejąca tabela jest dostarczana jako dane wejściowe, schemat musi być spójny ze schematem typu `T` .</span><span class="sxs-lookup"><span data-stu-id="12b5f-111">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="12b5f-112">Każda publiczna właściwość i pole typu `T` jest konwertowane na <xref:System.Data.DataColumn> w zwracanej tabeli.</span><span class="sxs-lookup"><span data-stu-id="12b5f-112">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="12b5f-113">Jeśli sekwencja źródłowa zawiera typ pochodzący z `T` , zwracany schemat tabeli jest rozwinięty dla wszystkich dodatkowych właściwości publicznych lub pól.</span><span class="sxs-lookup"><span data-stu-id="12b5f-113">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="12b5f-114">Przykłady użycia `CopyToDataTable<T>` metod niestandardowych można znaleźć w temacie [Creating a DataTable from a Query](creating-a-datatable-from-a-query-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="12b5f-114">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="12b5f-115">Aby zaimplementować niestandardowe metody CopyToDataTable \<T> w aplikacji</span><span class="sxs-lookup"><span data-stu-id="12b5f-115">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1. <span data-ttu-id="12b5f-116">Zaimplementuj `ObjectShredder<T>` klasę, aby utworzyć obiekt <xref:System.Data.DataTable> ze <xref:System.Collections.Generic.IEnumerable%601> źródła:</span><span class="sxs-lookup"><span data-stu-id="12b5f-116">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    <span data-ttu-id="12b5f-117">W poprzednim przykładzie przyjęto założenie, że właściwości i pola typu `DataColumn` nie dopuszcza wartości null.</span><span class="sxs-lookup"><span data-stu-id="12b5f-117">The preceding example assumes that the properties and fields of the `DataColumn` are not nullable value types.</span></span> <span data-ttu-id="12b5f-118">Aby obsłużyć właściwości i pola z typami wartości null, użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="12b5f-118">To handle properties and fields with nullable value types, use the following code:</span></span>

    ```csharp
    // Nullable-aware code for properties.
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);

    // Nullable-aware code for fields.
    DataColumn dc = table.Columns.Contains(f.Name) ? table.Columns[f.Name] : table.Columns.Add(f.Name, Nullable.GetUnderlyingType(f.FieldType) ?? f.FieldType);
    ```

2. <span data-ttu-id="12b5f-119">Zaimplementuj niestandardowe `CopyToDataTable<T>` metody rozszerzenia w klasie:</span><span class="sxs-lookup"><span data-stu-id="12b5f-119">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. <span data-ttu-id="12b5f-120">Dodaj `ObjectShredder<T>` klasę i `CopyToDataTable<T>` metody rozszerzenia do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="12b5f-120">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="12b5f-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12b5f-121">See also</span></span>

- [<span data-ttu-id="12b5f-122">Tworzenie elementu DataTable na podstawie zapytania</span><span class="sxs-lookup"><span data-stu-id="12b5f-122">Creating a DataTable From a Query</span></span>](creating-a-datatable-from-a-query-linq-to-dataset.md)
- [<span data-ttu-id="12b5f-123">Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="12b5f-123">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)
