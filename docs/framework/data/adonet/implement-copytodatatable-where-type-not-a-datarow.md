---
title: 'Instrukcje: Implementowanie CopyToDataTable<T>, gdzie ogólny typ T nie jest elementem DataRow'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 120b4bf22e310bee73ba006cfe5a060d0ecd9d65
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338946"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="2b38c-102">Instrukcje: Implementowanie CopyToDataTable\<T > gdzie ogólny typ T nie jest elementem DataRow</span><span class="sxs-lookup"><span data-stu-id="2b38c-102">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>
<span data-ttu-id="2b38c-103"><xref:System.Data.DataTable> Obiektu jest często używana do wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="2b38c-103">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="2b38c-104"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda pobiera wyniki zapytania i kopiuje dane do <xref:System.Data.DataTable>, która następnie umożliwia powiązanie danych.</span><span class="sxs-lookup"><span data-stu-id="2b38c-104">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="2b38c-105"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metod, jednak działać tylko w odniesieniu <xref:System.Collections.Generic.IEnumerable%601> źródła gdzie parametr ogólny `T` typu <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="2b38c-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="2b38c-106">Mimo że jest to przydatne, nie zezwala tabel, które ma zostać utworzony z sekwencji typami skalarnymi, zapytania, które anonimowych typów projektów lub zapytania, które wykonują sprzężeń tabel.</span><span class="sxs-lookup"><span data-stu-id="2b38c-106">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="2b38c-107">W tym temacie opisano sposób implementacji niestandardowego dwóch `CopyToDataTable<T>` metody rozszerzenia, które akceptują parametr ogólny `T` typu innego niż <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="2b38c-107">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="2b38c-108">Logic Apps, aby utworzyć <xref:System.Data.DataTable> z <xref:System.Collections.Generic.IEnumerable%601> źródła znajduje się w `ObjectShredder<T>` klasy, która jest następnie opakowywany w dwóch przeciążone `CopyToDataTable<T>` metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="2b38c-108">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="2b38c-109">`Shred` Metody `ObjectShredder<T>` Klasa zwraca wypełniony <xref:System.Data.DataTable> i przyjmuje trzy parametry wejściowe: <xref:System.Collections.Generic.IEnumerable%601> źródła <xref:System.Data.DataTable>, a <xref:System.Data.LoadOption> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="2b38c-109">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="2b38c-110">Schemat początkowy zwracanego <xref:System.Data.DataTable> opiera się na schemat typu `T`.</span><span class="sxs-lookup"><span data-stu-id="2b38c-110">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="2b38c-111">Jeśli nie podano istniejącej tabeli jako dane wejściowe, schemat musi być spójne ze schematem typu `T`.</span><span class="sxs-lookup"><span data-stu-id="2b38c-111">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="2b38c-112">Każdej publicznej właściwości i pola typu `T` jest konwertowana na <xref:System.Data.DataColumn> w tabeli zwracane.</span><span class="sxs-lookup"><span data-stu-id="2b38c-112">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="2b38c-113">Jeśli sekwencja źródłowa zawiera typ pochodzący od `T`, schemat tabeli zwracane podzielonego na wszelkie dodatkowe właściwości publiczne i pola.</span><span class="sxs-lookup"><span data-stu-id="2b38c-113">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="2b38c-114">Przykłady użycia niestandardowej `CopyToDataTable<T>` metod, zobacz [Tworzenie elementu DataTable z zapytania](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="2b38c-114">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="2b38c-115">Implementacji niestandardowego CopyToDataTable\<T > metodami w aplikacji</span><span class="sxs-lookup"><span data-stu-id="2b38c-115">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1. <span data-ttu-id="2b38c-116">Implementowanie `ObjectShredder<T>` klasy w celu utworzenia <xref:System.Data.DataTable> z <xref:System.Collections.Generic.IEnumerable%601> źródła:</span><span class="sxs-lookup"><span data-stu-id="2b38c-116">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    <span data-ttu-id="2b38c-117">Poprzedni przykład założono, że właściwości `DataColumn` nie są typy dopuszczające wartości null.</span><span class="sxs-lookup"><span data-stu-id="2b38c-117">The preceding example assumes that the properties of the `DataColumn` are not nullable types.</span></span> <span data-ttu-id="2b38c-118">Aby obsłużyć właściwości z typami zerowalnymi, użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="2b38c-118">To handle properties with nullable types, use the following code:</span></span>

    ```csharp
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);
    ```

2. <span data-ttu-id="2b38c-119">Implementowanie niestandardowego `CopyToDataTable<T>` metody rozszerzenia w klasie:</span><span class="sxs-lookup"><span data-stu-id="2b38c-119">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. <span data-ttu-id="2b38c-120">Dodaj `ObjectShredder<T>` klasy i `CopyToDataTable<T>` metody rozszerzenia do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2b38c-120">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2b38c-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b38c-121">See also</span></span>

- [<span data-ttu-id="2b38c-122">Tworzenie elementu DataTable na podstawie zapytania</span><span class="sxs-lookup"><span data-stu-id="2b38c-122">Creating a DataTable From a Query</span></span>](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)
- [<span data-ttu-id="2b38c-123">Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="2b38c-123">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
