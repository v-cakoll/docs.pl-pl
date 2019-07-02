---
title: Porównywanie wierszy danych (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: 7c8687e0e14458c944e2dec2b51b9f78bb2377c3
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504222"
---
# <a name="comparing-datarows-linq-to-dataset"></a><span data-ttu-id="9786c-102">Porównywanie wierszy danych (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="9786c-102">Comparing DataRows (LINQ to DataSet)</span></span>
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] <span data-ttu-id="9786c-103">definiuje różne operatory zestawów do porównywania elementów źródła, aby zobaczyć, czy są równe.</span><span class="sxs-lookup"><span data-stu-id="9786c-103">defines various set operators to compare source elements to see if they are equal.</span></span> [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] <span data-ttu-id="9786c-104">udostępnia następujące operatory zestawów:</span><span class="sxs-lookup"><span data-stu-id="9786c-104">provides the following set operators:</span></span>  
  
- <xref:System.Linq.Enumerable.Distinct%2A>  
  
- <xref:System.Linq.Enumerable.Union%2A>  
  
- <xref:System.Linq.Enumerable.Intersect%2A>  
  
- <xref:System.Linq.Enumerable.Except%2A>  
  
 <span data-ttu-id="9786c-105">Te operatory porównania elementy źródłowe, wywołując <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> i <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> metody dla każdej kolekcji elementów.</span><span class="sxs-lookup"><span data-stu-id="9786c-105">These operators compare source elements by calling the <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> and <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> methods on each collection of elements.</span></span> <span data-ttu-id="9786c-106">W przypadku właściwości <xref:System.Data.DataRow>, te operatory wykonać porównanie odwołań, które zwykle nie jest idealnym rozwiązaniem zachowanie operacje na zestawie danych tabelarycznych.</span><span class="sxs-lookup"><span data-stu-id="9786c-106">In the case of a <xref:System.Data.DataRow>, these operators perform a reference comparison, which is generally not the ideal behavior for set operations over tabular data.</span></span> <span data-ttu-id="9786c-107">Dla operacji zestawu zazwyczaj chcesz określić, czy są równe wartości elementów i nie odwołania do elementu.</span><span class="sxs-lookup"><span data-stu-id="9786c-107">For set operations, you usually want to determine whether the element values are equal and not the element references.</span></span> <span data-ttu-id="9786c-108">W związku z tym <xref:System.Data.DataRowComparer> klasa została dodana do programu LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="9786c-108">Therefore, the <xref:System.Data.DataRowComparer> class has been added to LINQ to DataSet.</span></span> <span data-ttu-id="9786c-109">Tej klasy może służyć do porównywania wartości wierszy.</span><span class="sxs-lookup"><span data-stu-id="9786c-109">This class can be used to compare row values.</span></span>  
  
 <span data-ttu-id="9786c-110"><xref:System.Data.DataRowComparer> Klasa zawiera implementację porównania wartości <xref:System.Data.DataRow>, więc ta klasa może służyć do zestawu operacji takich jak <xref:System.Linq.Enumerable.Distinct%2A>.</span><span class="sxs-lookup"><span data-stu-id="9786c-110">The <xref:System.Data.DataRowComparer> class contains a value comparison implementation for <xref:System.Data.DataRow>, so this class can be used for set operations such as <xref:System.Linq.Enumerable.Distinct%2A>.</span></span> <span data-ttu-id="9786c-111">To nie można bezpośrednio utworzyć wystąpienia klasy; Zamiast tego <xref:System.Data.DataRowComparer.Default%2A> właściwość musi być używana do zwrócenia wystąpienia <xref:System.Data.DataRowComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="9786c-111">This class cannot be directly instantiated; instead, the <xref:System.Data.DataRowComparer.Default%2A> property must be used to return an instance of the <xref:System.Data.DataRowComparer%601>.</span></span> <span data-ttu-id="9786c-112"><xref:System.Data.DataRowComparer%601.Equals%2A> Następnie wywoływana jest metoda i dwa <xref:System.Data.DataRow> obiekty, które mają być porównane, są przekazywane w jako parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="9786c-112">The <xref:System.Data.DataRowComparer%601.Equals%2A> method is then called and the two <xref:System.Data.DataRow> objects to be compared are passed in as input parameters.</span></span> <span data-ttu-id="9786c-113"><xref:System.Data.DataRowComparer%601.Equals%2A> Metoda zwraca `true` Jeśli uporządkowany zestaw kolumn wartości w obu <xref:System.Data.DataRow> obiekty są równe; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="9786c-113">The <xref:System.Data.DataRowComparer%601.Equals%2A> method returns `true` if the ordered set of column values in both <xref:System.Data.DataRow> objects are equal; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9786c-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="9786c-114">Example</span></span>  
 <span data-ttu-id="9786c-115">W tym przykładzie użyto `Intersect` do zwrócenia kontakty, które pojawiają się w obu tabelach.</span><span class="sxs-lookup"><span data-stu-id="9786c-115">This example uses `Intersect` to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a><span data-ttu-id="9786c-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="9786c-116">Example</span></span>  
 <span data-ttu-id="9786c-117">Poniższy przykład porównuje dwa wiersze i pobiera ich kody skrótów.</span><span class="sxs-lookup"><span data-stu-id="9786c-117">The following example compares two rows and gets their hash codes.</span></span>  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a><span data-ttu-id="9786c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9786c-118">See also</span></span>

- <xref:System.Data.DataRowComparer>
- [<span data-ttu-id="9786c-119">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="9786c-119">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="9786c-120">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="9786c-120">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
