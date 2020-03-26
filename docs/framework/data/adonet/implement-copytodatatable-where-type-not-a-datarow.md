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
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="5af0e-102">Jak: Implementowanie copytodatatable\<T>, w którym typ ogólny T nie jest datarow</span><span class="sxs-lookup"><span data-stu-id="5af0e-102">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>
<span data-ttu-id="5af0e-103">Obiekt <xref:System.Data.DataTable> jest często używany do wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="5af0e-103">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="5af0e-104">Metoda <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> pobiera wyniki kwerendy i kopiuje <xref:System.Data.DataTable>dane do programu , który następnie może służyć do wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="5af0e-104">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="5af0e-105">Metody <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> działają jednak tylko na <xref:System.Collections.Generic.IEnumerable%601> źródle, w `T` którym <xref:System.Data.DataRow>parametr ogólny jest typu .</span><span class="sxs-lookup"><span data-stu-id="5af0e-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="5af0e-106">Chociaż jest to przydatne, nie zezwala na tworzenie tabel z sekwencji typów skalarnych, z kwerend, które projektują typy anonimowe lub z kwerend, które wykonują sprzężenia tabeli.</span><span class="sxs-lookup"><span data-stu-id="5af0e-106">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="5af0e-107">W tym temacie opisano `CopyToDataTable<T>` sposób implementacji dwóch `T` niestandardowych metod <xref:System.Data.DataRow>rozszerzenia, które akceptują ogólny parametr typu innego niż .</span><span class="sxs-lookup"><span data-stu-id="5af0e-107">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="5af0e-108">Logika do <xref:System.Data.DataTable> tworzenia <xref:System.Collections.Generic.IEnumerable%601> ze źródła znajduje `ObjectShredder<T>` się w klasie, która jest `CopyToDataTable<T>` następnie zawijana w dwie przeciążone metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="5af0e-108">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="5af0e-109">Metoda `Shred` `ObjectShredder<T>` <xref:System.Data.DataTable> klasy zwraca wypełnione i akceptuje trzy parametry <xref:System.Collections.Generic.IEnumerable%601> wejściowe: <xref:System.Data.DataTable>źródło, <xref:System.Data.LoadOption> a , i wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="5af0e-109">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="5af0e-110">Początkowy schemat zwracanego <xref:System.Data.DataTable> jest oparty na schemacie `T`typu .</span><span class="sxs-lookup"><span data-stu-id="5af0e-110">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="5af0e-111">Jeśli istniejąca tabela jest dostarczana jako dane wejściowe, schemat `T`musi być zgodny ze schematem typu .</span><span class="sxs-lookup"><span data-stu-id="5af0e-111">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="5af0e-112">Każda właściwość publiczna `T` i pole typu <xref:System.Data.DataColumn> jest konwertowana na w tabeli zwracanej.</span><span class="sxs-lookup"><span data-stu-id="5af0e-112">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="5af0e-113">Jeśli sekwencja źródłowsza `T`zawiera typ pochodny , zwracany schemat tabeli jest rozwijany dla wszelkich dodatkowych właściwości publicznych lub pól.</span><span class="sxs-lookup"><span data-stu-id="5af0e-113">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="5af0e-114">Aby zapoznać się `CopyToDataTable<T>` z przykładami użycia metod niestandardowych, zobacz [Tworzenie tabeli data z kwerendy](creating-a-datatable-from-a-query-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="5af0e-114">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="5af0e-115">Aby zaimplementować niestandardowe metody> W> CopyToDataTable\<w aplikacji</span><span class="sxs-lookup"><span data-stu-id="5af0e-115">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1. <span data-ttu-id="5af0e-116">`ObjectShredder<T>` Zaimplementuj <xref:System.Data.DataTable> klasę, aby utworzyć źródło: <xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="5af0e-116">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    <span data-ttu-id="5af0e-117">W poprzednim przykładzie przyjęto założenie, `DataColumn` że właściwości nie są typami wartości nullable.</span><span class="sxs-lookup"><span data-stu-id="5af0e-117">The preceding example assumes that the properties of the `DataColumn` are not nullable value types.</span></span> <span data-ttu-id="5af0e-118">Aby obsłużyć właściwości z typami wartości z do wartości null, należy użyć następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="5af0e-118">To handle properties with nullable value types, use the following code:</span></span>

    ```csharp
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);
    ```

2. <span data-ttu-id="5af0e-119">Zaimplementuj niestandardowe `CopyToDataTable<T>` metody rozszerzenia w klasie:</span><span class="sxs-lookup"><span data-stu-id="5af0e-119">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. <span data-ttu-id="5af0e-120">`ObjectShredder<T>` Dodaj klasy `CopyToDataTable<T>` i metody rozszerzenia do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5af0e-120">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5af0e-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5af0e-121">See also</span></span>

- [<span data-ttu-id="5af0e-122">Tworzenie elementu DataTable na podstawie zapytania</span><span class="sxs-lookup"><span data-stu-id="5af0e-122">Creating a DataTable From a Query</span></span>](creating-a-datatable-from-a-query-linq-to-dataset.md)
- [<span data-ttu-id="5af0e-123">Przewodnik po programowaniu</span><span class="sxs-lookup"><span data-stu-id="5af0e-123">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)
