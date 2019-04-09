---
title: Zwracanie średniej wartości z sekwencji numerycznej
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee3b8673-a2e7-4b2d-9b5c-4972ff9e665d
ms.openlocfilehash: eea1439337b29fee51c422238425491fc2345211
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095090"
---
# <a name="return-the-average-value-from-a-numeric-sequence"></a><span data-ttu-id="a5dbf-102">Zwracanie średniej wartości z sekwencji numerycznej</span><span class="sxs-lookup"><span data-stu-id="a5dbf-102">Return the Average Value From a Numeric Sequence</span></span>
<span data-ttu-id="a5dbf-103"><xref:System.Linq.Enumerable.Average%2A> Operator oblicza średnią sekwencję wartości liczbowych.</span><span class="sxs-lookup"><span data-stu-id="a5dbf-103">The <xref:System.Linq.Enumerable.Average%2A> operator computes the average of a sequence of numeric values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5dbf-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Tłumaczenia `Average` liczby całkowitej wartości jest obliczany jako liczba całkowita, nie jako wartość o podwójnej precyzji.</span><span class="sxs-lookup"><span data-stu-id="a5dbf-104">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Average` of integer values is computed as an integer, not as a double.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5dbf-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5dbf-105">Example</span></span>  
 <span data-ttu-id="a5dbf-106">Poniższy przykład zwraca średnią `Freight` wartości w `Orders` tabeli.</span><span class="sxs-lookup"><span data-stu-id="a5dbf-106">The following example returns the average of `Freight` values in the `Orders` table.</span></span>  
  
 <span data-ttu-id="a5dbf-107">Wyniki z przykładowej bazy danych Northwind będą `78.2442`.</span><span class="sxs-lookup"><span data-stu-id="a5dbf-107">Results from the sample Northwind database would be `78.2442`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#1)]
 [!code-vb[DLinqQueryExamples#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="a5dbf-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5dbf-108">Example</span></span>  
 <span data-ttu-id="a5dbf-109">Poniższy przykład zwraca średnią cenę jednostkową wszystkich `Products` w `Products` tabeli.</span><span class="sxs-lookup"><span data-stu-id="a5dbf-109">The following example returns the average of the unit price of all `Products` in the `Products` table.</span></span>  
  
 <span data-ttu-id="a5dbf-110">Wyniki z przykładowej bazy danych Northwind będą `28.8663`.</span><span class="sxs-lookup"><span data-stu-id="a5dbf-110">Results from the sample Northwind database would be `28.8663`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#2)]
 [!code-vb[DLinqQueryExamples#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="a5dbf-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5dbf-111">Example</span></span>  
 <span data-ttu-id="a5dbf-112">W poniższym przykładzie użyto `Average` operatora, aby znaleźć te `Products` których cena jednostkowa jest wyższa niż średnia cena jednostkowa kategorii, należy ona do.</span><span class="sxs-lookup"><span data-stu-id="a5dbf-112">The following example uses the `Average` operator to find those `Products` whose unit price is higher than the average unit price of the category it belongs to.</span></span> <span data-ttu-id="a5dbf-113">Przykład następnie wyświetla wyniki w grupach.</span><span class="sxs-lookup"><span data-stu-id="a5dbf-113">The example then displays the results in groups.</span></span>  
  
 <span data-ttu-id="a5dbf-114">Należy pamiętać, że w tym przykładzie wymaga użycia `var` — słowo kluczowe w C#, ponieważ zwracany typ jest anonimowy.</span><span class="sxs-lookup"><span data-stu-id="a5dbf-114">Note that this example requires the use of the `var` keyword in C#, because the return type is anonymous.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#3)]
 [!code-vb[DLinqQueryExamples#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#3)]  
  
 <span data-ttu-id="a5dbf-115">Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, wyniki powinien przypominać poniższe:</span><span class="sxs-lookup"><span data-stu-id="a5dbf-115">If you run this query against the Northwind sample database, the results should resemble of the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `Ipoh Coffee`  
  
 `2`  
  
 `Grandma's Boysenberry Spread`  
  
 `Northwoods Cranberry Sauce`  
  
 `Sirop d'érable`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `Gumbär Gummibärchen`  
  
 `Schoggi Schokolade`  
  
 `Tarte au sucre`  
  
 `4`  
  
 `Queso Manchego La Pastora`  
  
 `Mascarpone Fabioli`  
  
 `Raclette Courdavault`  
  
 `Camembert Pierrot`  
  
 `Gudbrandsdalsost`  
  
 `Mozzarella di Giovanni`  
  
 `5`  
  
 `Gustaf's Knäckebröd`  
  
 `Gnocchi di nonna Alice`  
  
 `Wimmers gute Semmelknödel`  
  
 `6`  
  
 `Mishi Kobe Niku`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Rössle Sauerkraut`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Ikura`  
  
 `Carnarvon Tigers`  
  
 `Nord-Ost Matjeshering`  
  
 `Gravad lax`  
  
## <a name="see-also"></a><span data-ttu-id="a5dbf-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5dbf-116">See also</span></span>

- [<span data-ttu-id="a5dbf-117">Zapytania zagregowane</span><span class="sxs-lookup"><span data-stu-id="a5dbf-117">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
