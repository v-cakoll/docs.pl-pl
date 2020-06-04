---
title: Take While, klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 4b6133efdbd9c46ab85201ad454671e5538b6a81
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359583"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="b7860-102">Take While — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7860-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="b7860-103">Zawiera elementy w kolekcji, tak długo, jak określony warunek jest `true` i pomija pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="b7860-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7860-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b7860-104">Syntax</span></span>  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="b7860-105">Części</span><span class="sxs-lookup"><span data-stu-id="b7860-105">Parts</span></span>  
  
|<span data-ttu-id="b7860-106">Termin</span><span class="sxs-lookup"><span data-stu-id="b7860-106">Term</span></span>|<span data-ttu-id="b7860-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="b7860-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="b7860-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b7860-108">Required.</span></span> <span data-ttu-id="b7860-109">Wyrażenie reprezentujące warunek, dla którego mają zostać przetestowane elementy.</span><span class="sxs-lookup"><span data-stu-id="b7860-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="b7860-110">Wyrażenie musi zwracać `Boolean` wartość lub odpowiedni odpowiednik funkcjonalny, na przykład, `Integer` Aby można było je oszacować jako `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="b7860-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7860-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b7860-111">Remarks</span></span>  
 <span data-ttu-id="b7860-112">`Take While`Klauzula zawiera elementy od początku wyniku zapytania do podanej wartości `expression` zwracanej `false` .</span><span class="sxs-lookup"><span data-stu-id="b7860-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="b7860-113">Po `expression` powrocie `false` zapytanie spowoduje obejście wszystkich pozostałych elementów.</span><span class="sxs-lookup"><span data-stu-id="b7860-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="b7860-114">Wartość `expression` jest ignorowana dla pozostałych wyników.</span><span class="sxs-lookup"><span data-stu-id="b7860-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="b7860-115">`Take While`Klauzula różni się od `Where` klauzuli, w której `Where` klauzula może być używana do dołączania wszystkich elementów z zapytania, które spełniają określony warunek.</span><span class="sxs-lookup"><span data-stu-id="b7860-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="b7860-116">`Take While`Klauzula zawiera elementy tylko do pierwszego niespełnienia warunku.</span><span class="sxs-lookup"><span data-stu-id="b7860-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="b7860-117">`Take While`Klauzula jest najbardziej przydatna podczas pracy z wynikiem kwerendy uporządkowanej.</span><span class="sxs-lookup"><span data-stu-id="b7860-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7860-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="b7860-118">Example</span></span>  
 <span data-ttu-id="b7860-119">Poniższy przykład kodu używa klauzuli, `Take While` Aby pobrać wyniki do momentu, w którym nie zostanie znaleziony pierwszy klient bez zamówień.</span><span class="sxs-lookup"><span data-stu-id="b7860-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b7860-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7860-120">See also</span></span>

- [<span data-ttu-id="b7860-121">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b7860-121">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="b7860-122">Zapytania</span><span class="sxs-lookup"><span data-stu-id="b7860-122">Queries</span></span>](index.md)
- [<span data-ttu-id="b7860-123">SELECT — klauzula</span><span class="sxs-lookup"><span data-stu-id="b7860-123">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="b7860-124">Klauzula from</span><span class="sxs-lookup"><span data-stu-id="b7860-124">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="b7860-125">Take, klauzula</span><span class="sxs-lookup"><span data-stu-id="b7860-125">Take Clause</span></span>](take-clause.md)
- [<span data-ttu-id="b7860-126">Skip While, klauzula</span><span class="sxs-lookup"><span data-stu-id="b7860-126">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="b7860-127">Klauzula WHERE</span><span class="sxs-lookup"><span data-stu-id="b7860-127">Where Clause</span></span>](where-clause.md)
