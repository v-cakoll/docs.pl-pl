---
title: "Porady: Implementowanie CopyToDataTable&lt;T&gt; gdzie ogólny typ T nie jest element DataRow"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1ca633d257b9eafcab646295667eb37ad41434a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-copytodatatablelttgt-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="beae5-102">Porady: Implementowanie CopyToDataTable&lt;T&gt; gdzie ogólny typ T nie jest element DataRow</span><span class="sxs-lookup"><span data-stu-id="beae5-102">How to: Implement CopyToDataTable&lt;T&gt; Where the Generic Type T Is Not a DataRow</span></span>
<span data-ttu-id="beae5-103"><xref:System.Data.DataTable> Obiekt jest często używany do wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="beae5-103">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="beae5-104"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda pobiera wyników zapytania i kopiuje dane na <xref:System.Data.DataTable>, której następnie można użyć dla powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="beae5-104">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="beae5-105"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metod, jednak wykonywać operacje tylko na <xref:System.Collections.Generic.IEnumerable%601> źródła gdzie parametr generyczny `T` jest typu <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="beae5-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="beae5-106">Chociaż jest to przydatne, nie zezwala tabele, aby utworzyć sekwencję typy skalarne, z zapytań, które typy anonimowe projektu lub z zapytań, które wykonują sprzężeń tabel.</span><span class="sxs-lookup"><span data-stu-id="beae5-106">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="beae5-107">W tym temacie opisano implementowania niestandardowych dwóch `CopyToDataTable<T>` metody rozszerzenia, które akceptują parametr ogólny `T` typu innego niż <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="beae5-107">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="beae5-108">Logika tworzenia <xref:System.Data.DataTable> z <xref:System.Collections.Generic.IEnumerable%601> źródła znajduje się w `ObjectShredder<T>` klasy, która jest następnie opakowane w dwóch przeciążony `CopyToDataTable<T>` metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="beae5-108">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="beae5-109">`Shred` Metody `ObjectShredder<T>` Klasa zwraca wypełniony <xref:System.Data.DataTable> i przyjmuje trzy parametry wejściowe: <xref:System.Collections.Generic.IEnumerable%601> źródła, <xref:System.Data.DataTable>, a <xref:System.Data.LoadOption> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="beae5-109">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="beae5-110">Początkowa schematu, zwracana <xref:System.Data.DataTable> opiera się na schemat typu `T`.</span><span class="sxs-lookup"><span data-stu-id="beae5-110">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="beae5-111">W przypadku istniejącej tabeli jako dane wejściowe schematu muszą być zgodne ze schematem typu `T`.</span><span class="sxs-lookup"><span data-stu-id="beae5-111">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="beae5-112">Każdej publicznej właściwości i pola typu `T` jest konwertowana na <xref:System.Data.DataColumn> w tabeli zwracanych.</span><span class="sxs-lookup"><span data-stu-id="beae5-112">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="beae5-113">Jeśli typ pochodny typu zawiera sekwencji źródłowej `T`, schemat tabeli zwracane jest rozwinięta dla wszelkie dodatkowe właściwości publiczne i pola.</span><span class="sxs-lookup"><span data-stu-id="beae5-113">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="beae5-114">Przykłady przy użyciu niestandardowego `CopyToDataTable<T>` metod, zobacz [tworzenie DataTable z zapytania](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="beae5-114">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="beae5-115">Implementacji niestandardowego CopyToDataTable\<T > metod w aplikacji</span><span class="sxs-lookup"><span data-stu-id="beae5-115">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1.  <span data-ttu-id="beae5-116">Implementowanie `ObjectShredder<T>` klasy w celu utworzenia <xref:System.Data.DataTable> z <xref:System.Collections.Generic.IEnumerable%601> źródła:</span><span class="sxs-lookup"><span data-stu-id="beae5-116">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  
  
2.  <span data-ttu-id="beae5-117">Implementowanie niestandardowego `CopyToDataTable<T>` metody rozszerzenia klasy:</span><span class="sxs-lookup"><span data-stu-id="beae5-117">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3.  <span data-ttu-id="beae5-118">Dodaj `ObjectShredder<T>` klasy i `CopyToDataTable<T>` metody rozszerzenia dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="beae5-118">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="beae5-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="beae5-119">See Also</span></span>  
 [<span data-ttu-id="beae5-120">Tworzenie elementu DataTable na podstawie zapytania</span><span class="sxs-lookup"><span data-stu-id="beae5-120">Creating a DataTable From a Query</span></span>](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)  
 [<span data-ttu-id="beae5-121">Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="beae5-121">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
