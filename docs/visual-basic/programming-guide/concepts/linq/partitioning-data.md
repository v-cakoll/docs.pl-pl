---
title: Partycjonowanie danych (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 01e4e6d6db07a520b97911de5388b8e42b7e1acc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="75e05-102">Partycjonowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75e05-102">Partitioning Data (Visual Basic)</span></span>
<span data-ttu-id="75e05-103">Podział na partycje w składniku LINQ odwołuje się do funkcjonowania dzielenie sekwencji wejściowych na dwie sekcje bez zmienianie rozmieszczenia elementów, a następnie zwraca w sekcji.</span><span class="sxs-lookup"><span data-stu-id="75e05-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="75e05-104">Na poniższej ilustracji przedstawiono wyniki trzech różnych partycjonowania operacji na sekwencję znaków.</span><span class="sxs-lookup"><span data-stu-id="75e05-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="75e05-105">Pierwsza operacja zwraca pierwsze trzy elementy w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="75e05-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="75e05-106">Druga operacja pomija pierwszych trzech elementów i zwraca wszystkie pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="75e05-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="75e05-107">Trzeci operacji pomija pierwsze dwa elementy w sekwencji i zwraca trzech kolejnych elementów.</span><span class="sxs-lookup"><span data-stu-id="75e05-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="75e05-108">![LINQ partycjonowania operacji](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="75e05-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="75e05-109">Metody operator standardowej kwerendy, które partycji sekwencje są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="75e05-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="75e05-110">Operatory</span><span class="sxs-lookup"><span data-stu-id="75e05-110">Operators</span></span>  
  
|<span data-ttu-id="75e05-111">Nazwa operatora</span><span class="sxs-lookup"><span data-stu-id="75e05-111">Operator Name</span></span>|<span data-ttu-id="75e05-112">Opis</span><span class="sxs-lookup"><span data-stu-id="75e05-112">Description</span></span>|<span data-ttu-id="75e05-113">Składnia wyrażeń języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="75e05-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="75e05-114">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="75e05-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="75e05-115">Skip</span><span class="sxs-lookup"><span data-stu-id="75e05-115">Skip</span></span>|<span data-ttu-id="75e05-116">Pomija elementy do określonej pozycji w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="75e05-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="75e05-117">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="75e05-117">SkipWhile</span></span>|<span data-ttu-id="75e05-118">Pomija elementy oparte na funkcji predykatu, dopóki element nie spełnia warunku.</span><span class="sxs-lookup"><span data-stu-id="75e05-118">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="75e05-119">Take</span><span class="sxs-lookup"><span data-stu-id="75e05-119">Take</span></span>|<span data-ttu-id="75e05-120">Pobiera elementy do określonej pozycji w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="75e05-120">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="75e05-121">takeWhile</span><span class="sxs-lookup"><span data-stu-id="75e05-121">TakeWhile</span></span>|<span data-ttu-id="75e05-122">Pobiera elementy oparte na funkcji predykatu, dopóki element nie spełnia warunku.</span><span class="sxs-lookup"><span data-stu-id="75e05-122">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="75e05-123">Przykłady składni wyrażeń zapytania</span><span class="sxs-lookup"><span data-stu-id="75e05-123">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="75e05-124">Skip</span><span class="sxs-lookup"><span data-stu-id="75e05-124">Skip</span></span>  
 <span data-ttu-id="75e05-125">Poniższy przykład kodu wykorzystuje `Skip` klauzuli w języku Visual Basic, aby pominąć pierwsze cztery ciągów w tablicy ciągów przed zwróceniem pozostałe ciągi w tablicy.</span><span class="sxs-lookup"><span data-stu-id="75e05-125">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]  
  
### <a name="skipwhile"></a><span data-ttu-id="75e05-126">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="75e05-126">SkipWhile</span></span>  
 <span data-ttu-id="75e05-127">Poniższy przykład kodu wykorzystuje `Skip While` klauzuli w języku Visual Basic można pominąć ciągów w tablicy, gdy jest pierwszą literę ciągu "".</span><span class="sxs-lookup"><span data-stu-id="75e05-127">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="75e05-128">Pozostałe ciągów w tablicy są zwracane.</span><span class="sxs-lookup"><span data-stu-id="75e05-128">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]  
  
### <a name="take"></a><span data-ttu-id="75e05-129">Take</span><span class="sxs-lookup"><span data-stu-id="75e05-129">Take</span></span>  
 <span data-ttu-id="75e05-130">Poniższy przykład kodu wykorzystuje `Take` klauzuli w języku Visual Basic, aby powrócić do pierwsze dwa ciągi w tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="75e05-130">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]  
  
### <a name="takewhile"></a><span data-ttu-id="75e05-131">takeWhile</span><span class="sxs-lookup"><span data-stu-id="75e05-131">TakeWhile</span></span>  
 <span data-ttu-id="75e05-132">Poniższy przykład kodu wykorzystuje `Take While` klauzuli w języku Visual Basic do zwrócenia z tablicy ciągów, gdy długość ciągu jest pięć lub mniej.</span><span class="sxs-lookup"><span data-stu-id="75e05-132">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="75e05-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75e05-133">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="75e05-134">Operatory standardowe zapytań — omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75e05-134">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="75e05-135">Skip, klauzula</span><span class="sxs-lookup"><span data-stu-id="75e05-135">Skip Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="75e05-136">Skip While, klauzula</span><span class="sxs-lookup"><span data-stu-id="75e05-136">Skip While Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="75e05-137">Take, klauzula</span><span class="sxs-lookup"><span data-stu-id="75e05-137">Take Clause</span></span>](../../../../visual-basic/language-reference/queries/take-clause.md)  
 [<span data-ttu-id="75e05-138">Take While, klauzula</span><span class="sxs-lookup"><span data-stu-id="75e05-138">Take While Clause</span></span>](../../../../visual-basic/language-reference/queries/take-while-clause.md)
