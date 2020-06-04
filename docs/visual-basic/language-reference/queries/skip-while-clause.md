---
title: Skip While, klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: b357320a92ace1b7a261991737ed653d54d0eeab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359648"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="ebfb4-102">Skip While — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebfb4-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="ebfb4-103">Pomija elementy w kolekcji, tak długo, jak określony warunek jest `true` , a następnie zwraca pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="ebfb4-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebfb4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ebfb4-104">Syntax</span></span>  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="ebfb4-105">Części</span><span class="sxs-lookup"><span data-stu-id="ebfb4-105">Parts</span></span>  
  
|<span data-ttu-id="ebfb4-106">Termin</span><span class="sxs-lookup"><span data-stu-id="ebfb4-106">Term</span></span>|<span data-ttu-id="ebfb4-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="ebfb4-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="ebfb4-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="ebfb4-108">Required.</span></span> <span data-ttu-id="ebfb4-109">Wyrażenie reprezentujące warunek, dla którego mają zostać przetestowane elementy.</span><span class="sxs-lookup"><span data-stu-id="ebfb4-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="ebfb4-110">Wyrażenie musi zwracać `Boolean` wartość lub odpowiedni odpowiednik funkcjonalny, na przykład, `Integer` Aby można było je oszacować jako `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="ebfb4-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebfb4-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ebfb4-111">Remarks</span></span>  
 <span data-ttu-id="ebfb4-112">`Skip While`Klauzula pomija elementy od początku wyniku zapytania do momentu podania podanej `expression` wartości `false` .</span><span class="sxs-lookup"><span data-stu-id="ebfb4-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="ebfb4-113">Po `expression` zwracaniu `false` zapytanie zwraca wszystkie pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="ebfb4-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="ebfb4-114">Wartość `expression` jest ignorowana dla pozostałych wyników.</span><span class="sxs-lookup"><span data-stu-id="ebfb4-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="ebfb4-115">`Skip While`Klauzula różni się od `Where` klauzuli, w której `Where` klauzula może służyć do wykluczenia wszystkich elementów z zapytania, które nie spełniają określonego warunku.</span><span class="sxs-lookup"><span data-stu-id="ebfb4-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="ebfb4-116">`Skip While`Klauzula wyklucza elementy tylko do pierwszego niespełnienia warunku.</span><span class="sxs-lookup"><span data-stu-id="ebfb4-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="ebfb4-117">`Skip While`Klauzula jest najbardziej przydatna podczas pracy z wynikiem kwerendy uporządkowanej.</span><span class="sxs-lookup"><span data-stu-id="ebfb4-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="ebfb4-118">Można pominąć określoną liczbę wyników od początku wyniku zapytania przy użyciu `Skip` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="ebfb4-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebfb4-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="ebfb4-119">Example</span></span>  
 <span data-ttu-id="ebfb4-120">Poniższy przykład kodu używa klauzuli, `Skip While` Aby pominąć wyniki do momentu, gdy zostanie znaleziony pierwszy klient z Stany Zjednoczone.</span><span class="sxs-lookup"><span data-stu-id="ebfb4-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ebfb4-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebfb4-121">See also</span></span>

- [<span data-ttu-id="ebfb4-122">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ebfb4-122">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="ebfb4-123">Zapytania</span><span class="sxs-lookup"><span data-stu-id="ebfb4-123">Queries</span></span>](index.md)
- [<span data-ttu-id="ebfb4-124">SELECT — klauzula</span><span class="sxs-lookup"><span data-stu-id="ebfb4-124">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="ebfb4-125">Klauzula from</span><span class="sxs-lookup"><span data-stu-id="ebfb4-125">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="ebfb4-126">Skip, klauzula</span><span class="sxs-lookup"><span data-stu-id="ebfb4-126">Skip Clause</span></span>](skip-clause.md)
- [<span data-ttu-id="ebfb4-127">Take While, klauzula</span><span class="sxs-lookup"><span data-stu-id="ebfb4-127">Take While Clause</span></span>](take-while-clause.md)
- [<span data-ttu-id="ebfb4-128">Klauzula WHERE</span><span class="sxs-lookup"><span data-stu-id="ebfb4-128">Where Clause</span></span>](where-clause.md)
