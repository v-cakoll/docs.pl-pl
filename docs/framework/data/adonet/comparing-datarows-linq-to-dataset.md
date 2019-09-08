---
title: Porównywanie wierszy DataRows (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: 30a782f5e37e867c7a0e4dfd800f4b2c2836d070
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784929"
---
# <a name="comparing-datarows-linq-to-dataset"></a><span data-ttu-id="1e3f3-102">Porównywanie wierszy DataRows (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="1e3f3-102">Comparing DataRows (LINQ to DataSet)</span></span>
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]<span data-ttu-id="1e3f3-103">definiuje różne operatory zestawów do porównywania elementów źródłowych, aby sprawdzić, czy są równe.</span><span class="sxs-lookup"><span data-stu-id="1e3f3-103">defines various set operators to compare source elements to see if they are equal.</span></span> [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]<span data-ttu-id="1e3f3-104">udostępnia następujące operatory zestawu:</span><span class="sxs-lookup"><span data-stu-id="1e3f3-104">provides the following set operators:</span></span>  
  
- <xref:System.Linq.Enumerable.Distinct%2A>  
  
- <xref:System.Linq.Enumerable.Union%2A>  
  
- <xref:System.Linq.Enumerable.Intersect%2A>  
  
- <xref:System.Linq.Enumerable.Except%2A>  
  
 <span data-ttu-id="1e3f3-105">Te operatory porównują elementy źródłowe, <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> wywołując <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> metody i dla każdej kolekcji elementów.</span><span class="sxs-lookup"><span data-stu-id="1e3f3-105">These operators compare source elements by calling the <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> and <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> methods on each collection of elements.</span></span> <span data-ttu-id="1e3f3-106">W przypadku <xref:System.Data.DataRow>, te operatory wykonują porównanie odwołań, które zwykle nie jest idealnym zachowaniem dla operacji ustawiania w danych tabelarycznych.</span><span class="sxs-lookup"><span data-stu-id="1e3f3-106">In the case of a <xref:System.Data.DataRow>, these operators perform a reference comparison, which is generally not the ideal behavior for set operations over tabular data.</span></span> <span data-ttu-id="1e3f3-107">W przypadku operacji ustawiania zazwyczaj należy określić, czy wartości elementów są równe, a nie odwołania do elementów.</span><span class="sxs-lookup"><span data-stu-id="1e3f3-107">For set operations, you usually want to determine whether the element values are equal and not the element references.</span></span> <span data-ttu-id="1e3f3-108">W związku z tym KlasazostaładodanadoLINQtoDataSet.<xref:System.Data.DataRowComparer></span><span class="sxs-lookup"><span data-stu-id="1e3f3-108">Therefore, the <xref:System.Data.DataRowComparer> class has been added to LINQ to DataSet.</span></span> <span data-ttu-id="1e3f3-109">Ta klasa może służyć do porównywania wartości wierszy.</span><span class="sxs-lookup"><span data-stu-id="1e3f3-109">This class can be used to compare row values.</span></span>  
  
 <span data-ttu-id="1e3f3-110">Klasa zawiera implementację porównania wartości dla <xref:System.Data.DataRow>, więc ta klasa może być używana do ustawiania operacji, takich jak <xref:System.Linq.Enumerable.Distinct%2A>. <xref:System.Data.DataRowComparer></span><span class="sxs-lookup"><span data-stu-id="1e3f3-110">The <xref:System.Data.DataRowComparer> class contains a value comparison implementation for <xref:System.Data.DataRow>, so this class can be used for set operations such as <xref:System.Linq.Enumerable.Distinct%2A>.</span></span> <span data-ttu-id="1e3f3-111">Nie można bezpośrednio utworzyć wystąpienia tej klasy; Zamiast tego <xref:System.Data.DataRowComparer%601>właściwość musi być używana do zwracania wystąpienia. <xref:System.Data.DataRowComparer.Default%2A></span><span class="sxs-lookup"><span data-stu-id="1e3f3-111">This class cannot be directly instantiated; instead, the <xref:System.Data.DataRowComparer.Default%2A> property must be used to return an instance of the <xref:System.Data.DataRowComparer%601>.</span></span> <span data-ttu-id="1e3f3-112">Metoda jest następnie wywoływana, a dwa <xref:System.Data.DataRow> obiekty, które mają być porównane, są przenoszone jako parametry wejściowe. <xref:System.Data.DataRowComparer%601.Equals%2A></span><span class="sxs-lookup"><span data-stu-id="1e3f3-112">The <xref:System.Data.DataRowComparer%601.Equals%2A> method is then called and the two <xref:System.Data.DataRow> objects to be compared are passed in as input parameters.</span></span> <span data-ttu-id="1e3f3-113"><xref:System.Data.DataRow> Metoda zwraca `true` , czyuporządkowanyzestawwartościkolumnwobuobiektachjestrówny;wprzeciwnymrazie.`false` <xref:System.Data.DataRowComparer%601.Equals%2A></span><span class="sxs-lookup"><span data-stu-id="1e3f3-113">The <xref:System.Data.DataRowComparer%601.Equals%2A> method returns `true` if the ordered set of column values in both <xref:System.Data.DataRow> objects are equal; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e3f3-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="1e3f3-114">Example</span></span>  
 <span data-ttu-id="1e3f3-115">Ten przykład używa `Intersect` do zwracania kontaktów, które pojawiają się w obu tabelach.</span><span class="sxs-lookup"><span data-stu-id="1e3f3-115">This example uses `Intersect` to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a><span data-ttu-id="1e3f3-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="1e3f3-116">Example</span></span>  
 <span data-ttu-id="1e3f3-117">Poniższy przykład porównuje dwa wiersze i pobiera ich kody skrótów.</span><span class="sxs-lookup"><span data-stu-id="1e3f3-117">The following example compares two rows and gets their hash codes.</span></span>  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a><span data-ttu-id="1e3f3-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e3f3-118">See also</span></span>

- <xref:System.Data.DataRowComparer>
- [<span data-ttu-id="1e3f3-119">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="1e3f3-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="1e3f3-120">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="1e3f3-120">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
