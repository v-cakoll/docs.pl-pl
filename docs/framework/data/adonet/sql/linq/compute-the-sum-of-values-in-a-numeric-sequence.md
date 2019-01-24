---
title: Obliczanie sumy wartości w sekwencji numerycznej
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: 699211e8e573f03935b5406f1759e6c3834718f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713171"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a><span data-ttu-id="97f5c-102">Obliczanie sumy wartości w sekwencji numerycznej</span><span class="sxs-lookup"><span data-stu-id="97f5c-102">Compute the Sum of Values in a Numeric Sequence</span></span>
<span data-ttu-id="97f5c-103">Użyj <xref:System.Linq.Enumerable.Sum%2A> operatora, aby obliczyć sumę wartości liczbowych z sekwencji.</span><span class="sxs-lookup"><span data-stu-id="97f5c-103">Use the <xref:System.Linq.Enumerable.Sum%2A> operator to compute the sum of numeric values in a sequence.</span></span>  
  
 <span data-ttu-id="97f5c-104">Należy zwrócić uwagę na następujące cechy `Sum` operatora w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="97f5c-104">Note the following characteristics of the `Sum` operator in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
-   <span data-ttu-id="97f5c-105">Aggregate-operator standardowej kwerendy operatora `Sum` osiągnie wartość zero dla pustej sekwencji lub sekwencję która zawiera tylko wartości null.</span><span class="sxs-lookup"><span data-stu-id="97f5c-105">The Standard Query Operator aggregate operator `Sum` evaluates to zero for an empty sequence or a sequence that contains only nulls.</span></span> <span data-ttu-id="97f5c-106">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], semantyki programu SQL Server są pozostawione bez zmian.</span><span class="sxs-lookup"><span data-stu-id="97f5c-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged.</span></span> <span data-ttu-id="97f5c-107">Z tego powodu `Sum` daje w wyniku wartość null zamiast zero sekwencję która zawiera tylko wartości null lub pustą sekwencją.</span><span class="sxs-lookup"><span data-stu-id="97f5c-107">For this reason, `Sum` evaluates to null instead of to zero for an empty sequence or for a sequence that contains only nulls.</span></span>  
  
-   <span data-ttu-id="97f5c-108">SQL na wyniki pośrednie ograniczenia wartości zagregowanych umieszczonych w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="97f5c-108">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="97f5c-109">Suma 32-bitowej liczby całkowitej ilości nie jest kolumną obliczaną, za pomocą 64-bitowych wyników i może wystąpić przepełnienie, dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczenia `Sum`.</span><span class="sxs-lookup"><span data-stu-id="97f5c-109">Sum of 32-bit integer quantities is not computed by using 64-bit results, and overflow can occur for the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Sum`.</span></span> <span data-ttu-id="97f5c-110">Nawet wtedy, gdy implementacja standardowej kwerendy operatora przepełnienie w odpowiedniej sekwencji w pamięci nie powoduje, że istnieje taka możliwość.</span><span class="sxs-lookup"><span data-stu-id="97f5c-110">This possibility exists even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97f5c-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="97f5c-111">Example</span></span>  
 <span data-ttu-id="97f5c-112">Poniższy przykład umożliwia znalezienie całkowita transport wszystkich zamówień w `Order` tabeli.</span><span class="sxs-lookup"><span data-stu-id="97f5c-112">The following example finds the total freight of all orders in the `Order` table.</span></span>  
  
 <span data-ttu-id="97f5c-113">Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, dane wyjściowe to: `64942.6900`.</span><span class="sxs-lookup"><span data-stu-id="97f5c-113">If you run this query against the Northwind sample database, the output is: `64942.6900`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="97f5c-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="97f5c-114">Example</span></span>  
 <span data-ttu-id="97f5c-115">Poniższy przykład umożliwia znalezienie całkowita liczba jednostek w kolejności dla wszystkich produktów.</span><span class="sxs-lookup"><span data-stu-id="97f5c-115">The following example finds the total number of units on order for all products.</span></span>  
  
 <span data-ttu-id="97f5c-116">Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, dane wyjściowe to: `780`.</span><span class="sxs-lookup"><span data-stu-id="97f5c-116">If you run this query against the Northwind sample database, the output is: `780`.</span></span>  
  
 <span data-ttu-id="97f5c-117">Należy zauważyć, że należy rzutować `short` typów (na przykład `UnitsOnOrder`) ponieważ `Sum` ma żadne przeciążenie dla typów krótkich.</span><span class="sxs-lookup"><span data-stu-id="97f5c-117">Note that you must cast `short` types (for example, `UnitsOnOrder`) because `Sum` has no overload for short types.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="97f5c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97f5c-118">See also</span></span>
- [<span data-ttu-id="97f5c-119">Zapytania zagregowane</span><span class="sxs-lookup"><span data-stu-id="97f5c-119">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [<span data-ttu-id="97f5c-120">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="97f5c-120">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
