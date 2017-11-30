---
title: "Skip While — Klauzula (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f447a6d9b2eb58fa546ced6c96b987caf68fb3e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="b8dee-102">Skip While — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8dee-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="b8dee-103">Pomija elementy w kolekcji, tak długo, jak jest określony warunek `true` , a następnie zwraca wszystkie pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="b8dee-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8dee-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8dee-104">Syntax</span></span>  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="b8dee-105">Części</span><span class="sxs-lookup"><span data-stu-id="b8dee-105">Parts</span></span>  
  
|<span data-ttu-id="b8dee-106">Termin</span><span class="sxs-lookup"><span data-stu-id="b8dee-106">Term</span></span>|<span data-ttu-id="b8dee-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="b8dee-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="b8dee-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b8dee-108">Required.</span></span> <span data-ttu-id="b8dee-109">Wyrażenie reprezentuje warunek do sprawdzenia elementów.</span><span class="sxs-lookup"><span data-stu-id="b8dee-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="b8dee-110">Wyrażenie musi zwracać `Boolean` wartość lub jej odpowiedniku funkcjonalne, takie jak `Integer` ma zostać obliczone jako `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b8dee-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8dee-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8dee-111">Remarks</span></span>  
 <span data-ttu-id="b8dee-112">`Skip While` Klauzuli pomija elementy od początku w wyniku zapytania do podane `expression` zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="b8dee-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="b8dee-113">Po `expression` zwraca `false`, gdy kwerenda zwraca wszystkie pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="b8dee-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="b8dee-114">`expression` Jest ignorowany w przypadku pozostałych wyników.</span><span class="sxs-lookup"><span data-stu-id="b8dee-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="b8dee-115">`Skip While` Klauzuli różni się od `Where` klauzuli w tym `Where` klauzuli można wykluczyć wszystkie elementy z zapytania, które nie spełniają określony warunek.</span><span class="sxs-lookup"><span data-stu-id="b8dee-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="b8dee-116">`Skip While` Klauzuli wyklucza elementy tylko dopiero po raz pierwszy warunek nie jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="b8dee-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="b8dee-117">`Skip While` Klauzula jest najbardziej przydatne podczas pracy z wynikiem uporządkowane zapytanie.</span><span class="sxs-lookup"><span data-stu-id="b8dee-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="b8dee-118">Można pominąć określoną liczbę wyników od początku w wyniku zapytania za pomocą `Skip` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="b8dee-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8dee-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="b8dee-119">Example</span></span>  
 <span data-ttu-id="b8dee-120">Poniższy przykład kodu wykorzystuje `Skip While` klauzuli obejść wyników, aż do znalezienia pierwszego klienta ze Stanów Zjednoczonych.</span><span class="sxs-lookup"><span data-stu-id="b8dee-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b8dee-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8dee-121">See Also</span></span>  
 [<span data-ttu-id="b8dee-122">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b8dee-122">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="b8dee-123">Zapytania</span><span class="sxs-lookup"><span data-stu-id="b8dee-123">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="b8dee-124">SELECT — klauzula</span><span class="sxs-lookup"><span data-stu-id="b8dee-124">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="b8dee-125">Klauzula FROM</span><span class="sxs-lookup"><span data-stu-id="b8dee-125">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="b8dee-126">SKIP — klauzula</span><span class="sxs-lookup"><span data-stu-id="b8dee-126">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="b8dee-127">Take While — klauzula</span><span class="sxs-lookup"><span data-stu-id="b8dee-127">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [<span data-ttu-id="b8dee-128">Gdy klauzula</span><span class="sxs-lookup"><span data-stu-id="b8dee-128">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
