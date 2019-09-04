---
title: Obliczanie sumy wartości w sekwencji numerycznej
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: 3a404068c2d89610aa9b01b392bca40f82e17707
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247926"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a><span data-ttu-id="2ef9a-102">Obliczanie sumy wartości w sekwencji numerycznej</span><span class="sxs-lookup"><span data-stu-id="2ef9a-102">Compute the Sum of Values in a Numeric Sequence</span></span>
<span data-ttu-id="2ef9a-103">Użyj operatora <xref:System.Linq.Enumerable.Sum%2A> , aby obliczyć sumę wartości liczbowych w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="2ef9a-103">Use the <xref:System.Linq.Enumerable.Sum%2A> operator to compute the sum of numeric values in a sequence.</span></span>  
  
 <span data-ttu-id="2ef9a-104">Zwróć uwagę na następujące cechy `Sum` operatora w: [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ef9a-104">Note the following characteristics of the `Sum` operator in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="2ef9a-105">Operator `Sum` agregujący standardowego operatora zapytania ma wartość zero dla pustej sekwencji lub sekwencji zawierającej tylko wartości null.</span><span class="sxs-lookup"><span data-stu-id="2ef9a-105">The Standard Query Operator aggregate operator `Sum` evaluates to zero for an empty sequence or a sequence that contains only nulls.</span></span> <span data-ttu-id="2ef9a-106">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]programie semantyka SQL pozostaje niezmieniona.</span><span class="sxs-lookup"><span data-stu-id="2ef9a-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged.</span></span> <span data-ttu-id="2ef9a-107">Z tego powodu program `Sum` zwraca wartość null zamiast zero dla pustej sekwencji lub dla sekwencji zawierającej tylko wartości null.</span><span class="sxs-lookup"><span data-stu-id="2ef9a-107">For this reason, `Sum` evaluates to null instead of to zero for an empty sequence or for a sequence that contains only nulls.</span></span>  
  
- <span data-ttu-id="2ef9a-108">Ograniczenia SQL dotyczące wyników pośrednich stosują się [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]do agregacji w.</span><span class="sxs-lookup"><span data-stu-id="2ef9a-108">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="2ef9a-109">Suma 32-bitowych liczb całkowitych nie jest obliczana przy użyciu 64-bitowych wyników, a przepełnienie może wystąpić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] w przypadku `Sum`tłumaczenia.</span><span class="sxs-lookup"><span data-stu-id="2ef9a-109">Sum of 32-bit integer quantities is not computed by using 64-bit results, and overflow can occur for the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Sum`.</span></span> <span data-ttu-id="2ef9a-110">Taka możliwość istnieje, nawet jeśli implementacja standardowego operatora zapytań nie powoduje przepełnienia odpowiedniej sekwencji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="2ef9a-110">This possibility exists even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ef9a-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="2ef9a-111">Example</span></span>  
 <span data-ttu-id="2ef9a-112">Poniższy przykład umożliwia znalezienie łącznego frachtu wszystkich zamówień w `Order` tabeli.</span><span class="sxs-lookup"><span data-stu-id="2ef9a-112">The following example finds the total freight of all orders in the `Order` table.</span></span>  
  
 <span data-ttu-id="2ef9a-113">W przypadku uruchomienia tego zapytania względem przykładowej bazy danych Northwind dane wyjściowe to: `64942.6900`.</span><span class="sxs-lookup"><span data-stu-id="2ef9a-113">If you run this query against the Northwind sample database, the output is: `64942.6900`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="2ef9a-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="2ef9a-114">Example</span></span>  
 <span data-ttu-id="2ef9a-115">Poniższy przykład umożliwia znalezienie łącznej liczby jednostek w kolejności dla wszystkich produktów.</span><span class="sxs-lookup"><span data-stu-id="2ef9a-115">The following example finds the total number of units on order for all products.</span></span>  
  
 <span data-ttu-id="2ef9a-116">W przypadku uruchomienia tego zapytania względem przykładowej bazy danych Northwind dane wyjściowe to: `780`.</span><span class="sxs-lookup"><span data-stu-id="2ef9a-116">If you run this query against the Northwind sample database, the output is: `780`.</span></span>  
  
 <span data-ttu-id="2ef9a-117">Należy zauważyć, że należy `short` rzutować typy (na `UnitsOnOrder`przykład) `Sum` , ponieważ nie ma przeciążenia dla krótkich typów.</span><span class="sxs-lookup"><span data-stu-id="2ef9a-117">Note that you must cast `short` types (for example, `UnitsOnOrder`) because `Sum` has no overload for short types.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="2ef9a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ef9a-118">See also</span></span>

- [<span data-ttu-id="2ef9a-119">Zapytania zagregowane</span><span class="sxs-lookup"><span data-stu-id="2ef9a-119">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="2ef9a-120">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="2ef9a-120">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
