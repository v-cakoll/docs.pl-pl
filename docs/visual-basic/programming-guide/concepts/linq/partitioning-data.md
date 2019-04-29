---
title: Partycjonowanie danych (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 2da63a1f6b73c8592d6036a90fa374a0d4385f4c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665903"
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="76f5e-102">Partycjonowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76f5e-102">Partitioning Data (Visual Basic)</span></span>
<span data-ttu-id="76f5e-103">Partycjonowanie w składniku LINQ odnosi się do funkcjonowania dzielenie sekwencji wejściowych na dwie sekcje bez rozmieszczanie elementów, a następnie powrotu w sekcji.</span><span class="sxs-lookup"><span data-stu-id="76f5e-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="76f5e-104">Poniższa ilustracja przedstawia wyniki trzech różnych partycjonowania operacji na sekwencję znaków.</span><span class="sxs-lookup"><span data-stu-id="76f5e-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="76f5e-105">Pierwsza operacja zwraca pierwsze trzy elementy w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="76f5e-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="76f5e-106">Drugą operację pomija pierwszych trzech elementów i zwraca wszystkie pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="76f5e-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="76f5e-107">Operacja trzeci pomija pierwszych dwóch elementów w sekwencji i zwraca następne trzy elementy.</span><span class="sxs-lookup"><span data-stu-id="76f5e-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Ilustracja przedstawiająca trzy operacje partycjonowania LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="76f5e-109">Metody standardowego operatora zapytań, partycji sekwencji, które są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="76f5e-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="76f5e-110">Operatory</span><span class="sxs-lookup"><span data-stu-id="76f5e-110">Operators</span></span>  
  
|<span data-ttu-id="76f5e-111">Nazwa operatora</span><span class="sxs-lookup"><span data-stu-id="76f5e-111">Operator Name</span></span>|<span data-ttu-id="76f5e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="76f5e-112">Description</span></span>|<span data-ttu-id="76f5e-113">Składnia wyrażeń języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="76f5e-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="76f5e-114">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="76f5e-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="76f5e-115">Skip</span><span class="sxs-lookup"><span data-stu-id="76f5e-115">Skip</span></span>|<span data-ttu-id="76f5e-116">Pomija elementy do określonej pozycji w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="76f5e-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="76f5e-117">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="76f5e-117">SkipWhile</span></span>|<span data-ttu-id="76f5e-118">Pomija elementy oparte na funkcji predykatu, dopóki element nie spełnia warunku.</span><span class="sxs-lookup"><span data-stu-id="76f5e-118">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="76f5e-119">Take</span><span class="sxs-lookup"><span data-stu-id="76f5e-119">Take</span></span>|<span data-ttu-id="76f5e-120">Pobiera elementy do określonej pozycji w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="76f5e-120">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="76f5e-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="76f5e-121">TakeWhile</span></span>|<span data-ttu-id="76f5e-122">Pobiera elementy oparte na funkcji predykatu, dopóki element nie spełnia warunku.</span><span class="sxs-lookup"><span data-stu-id="76f5e-122">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="76f5e-123">Przykłady składni wyrażeń zapytania</span><span class="sxs-lookup"><span data-stu-id="76f5e-123">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="76f5e-124">Skip</span><span class="sxs-lookup"><span data-stu-id="76f5e-124">Skip</span></span>  
 <span data-ttu-id="76f5e-125">Poniższy przykład kodu wykorzystuje `Skip` klauzuli w Visual Basic, aby pominąć pierwsze cztery ciągi w tablicy ciągów przed zwróceniem pozostałe ciągi w tablicy.</span><span class="sxs-lookup"><span data-stu-id="76f5e-125">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a><span data-ttu-id="76f5e-126">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="76f5e-126">SkipWhile</span></span>  
 <span data-ttu-id="76f5e-127">Poniższy przykład kodu wykorzystuje `Skip While` klauzuli w Visual Basic, aby pominąć ciągów w tablicy, podczas pierwszej litery w ciągu "".</span><span class="sxs-lookup"><span data-stu-id="76f5e-127">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="76f5e-128">Pozostałe parametry w tablicy są zwracane.</span><span class="sxs-lookup"><span data-stu-id="76f5e-128">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a><span data-ttu-id="76f5e-129">Take</span><span class="sxs-lookup"><span data-stu-id="76f5e-129">Take</span></span>  
 <span data-ttu-id="76f5e-130">Poniższy przykład kodu wykorzystuje `Take` klauzuli w języku Visual Basic, aby zwrócić pierwsze dwa ciągi w tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="76f5e-130">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a><span data-ttu-id="76f5e-131">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="76f5e-131">TakeWhile</span></span>  
 <span data-ttu-id="76f5e-132">Poniższy przykład kodu wykorzystuje `Take While` klauzuli w języku Visual Basic do zwrócenia z tablicy ciągów, podczas gdy długość ciągu jest pięć lub mniej.</span><span class="sxs-lookup"><span data-stu-id="76f5e-132">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="76f5e-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76f5e-133">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="76f5e-134">Omówienie operatorów standardowej kwerendy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76f5e-134">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="76f5e-135">Skip, klauzula</span><span class="sxs-lookup"><span data-stu-id="76f5e-135">Skip Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="76f5e-136">Skip While, klauzula</span><span class="sxs-lookup"><span data-stu-id="76f5e-136">Skip While Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="76f5e-137">Take, klauzula</span><span class="sxs-lookup"><span data-stu-id="76f5e-137">Take Clause</span></span>](../../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="76f5e-138">Take While, klauzula</span><span class="sxs-lookup"><span data-stu-id="76f5e-138">Take While Clause</span></span>](../../../../visual-basic/language-reference/queries/take-while-clause.md)
