---
title: "Porady: inicjowanie zmiennej tablicy w języku Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3ccdbed601d3fa87acb0833bc153c199b17a4eba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a><span data-ttu-id="e1311-102">Porady: inicjowanie zmiennej tablicy w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e1311-102">How to: Initialize an Array Variable in Visual Basic</span></span>
<span data-ttu-id="e1311-103">Inicjowanie zmiennej tablicy przy tym literał w tablicy `New` klauzuli i określając wartość początkową tablicy.</span><span class="sxs-lookup"><span data-stu-id="e1311-103">You initialize an array variable by including an array literal in a `New` clause and specifying the initial values of the array.</span></span> <span data-ttu-id="e1311-104">Można określić typ lub zezwolić na można wywnioskować na podstawie wartości w tablicy literału.</span><span class="sxs-lookup"><span data-stu-id="e1311-104">You can either specify the type or allow it to be inferred from the values in the array literal.</span></span> <span data-ttu-id="e1311-105">Aby uzyskać więcej informacji o sposobie wywnioskować typu, zobacz "Podczas wypełniania tablicy o początkowej wartości" w [tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="e1311-105">For more information about how the type is inferred, see "Populating an Array with Initial Values" in [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a><span data-ttu-id="e1311-106">Aby inicjowanie zmiennej tablicy przy użyciu tablicy literału</span><span class="sxs-lookup"><span data-stu-id="e1311-106">To initialize an array variable by using an array literal</span></span>  
  
-   <span data-ttu-id="e1311-107">W `New` klauzuli, lub podczas przypisywania wartości tablicy, podaj wartości elementów w nawiasach klamrowych (`{}`).</span><span class="sxs-lookup"><span data-stu-id="e1311-107">Either in the `New` clause, or when you assign the array value, supply the element values inside braces (`{}`).</span></span> <span data-ttu-id="e1311-108">W poniższym przykładzie pokazano kilka sposobów, aby zadeklarować, Utwórz i zainicjuj zmienną zawiera tablicę, która ma elementy typu `Char`.</span><span class="sxs-lookup"><span data-stu-id="e1311-108">The following example shows several ways to declare, create, and initialize a variable to contain an array that has elements of type `Char`.</span></span>  
  
     [!code-vb[VbVbalrArrays#16](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_1.vb)]  
  
     <span data-ttu-id="e1311-109">Po wykonaniu każdego instrukcji, tablica, która jest tworzona ma długość wynosi 3 z elementami pod indeksem 0 za pomocą indeksu 2 zawierające wartości początkowe.</span><span class="sxs-lookup"><span data-stu-id="e1311-109">After each statement executes, the array that's created has a length of 3, with elements at index 0 through index 2 containing the initial values.</span></span> <span data-ttu-id="e1311-110">Jeśli podasz zarówno górną granicę, jak i wartości musi zawierać wartość dla każdego elementu z indeksem 0 za pomocą górnej granicy.</span><span class="sxs-lookup"><span data-stu-id="e1311-110">If you supply both the upper bound and the values, you must include a value for every element from index 0 through the upper bound.</span></span>  
  
     <span data-ttu-id="e1311-111">Zwróć uwagę, że nie trzeba określić indeks górna granica, jeśli podane wartości elementów w tablicy literału.</span><span class="sxs-lookup"><span data-stu-id="e1311-111">Notice that you do not have to specify the index upper bound if you supply element values in an array literal.</span></span> <span data-ttu-id="e1311-112">Jeśli nie górna granica jest określony, rozmiar tablicy jest wywnioskowany na podstawie liczby wartości w tablicy literału.</span><span class="sxs-lookup"><span data-stu-id="e1311-112">If no upper bound is specified, the size of the array is inferred based on the number of values in the array literal.</span></span>  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a><span data-ttu-id="e1311-113">Można zainicjować zmiennej tablicy wielowymiarowej przy użyciu literałów tablicy</span><span class="sxs-lookup"><span data-stu-id="e1311-113">To initialize a multidimensional array variable by using array literals</span></span>  
  
-   <span data-ttu-id="e1311-114">Zagnieździć wartości w nawiasach klamrowych (`{}`) w nawiasach klamrowych.</span><span class="sxs-lookup"><span data-stu-id="e1311-114">Nest values inside braces (`{}`) within braces.</span></span> <span data-ttu-id="e1311-115">Upewnij się, że literały tablica zagnieżdżona, którego wszystkie wnioskować tablicowego tego samego typu i długości.</span><span class="sxs-lookup"><span data-stu-id="e1311-115">Ensure that the nested array literals all infer as arrays of the same type and length.</span></span> <span data-ttu-id="e1311-116">W poniższym przykładzie kodu przedstawiono kilka przykładów inicjowanie tablicy wielowymiarowej.</span><span class="sxs-lookup"><span data-stu-id="e1311-116">The following code example shows several examples of multidimensional array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#17](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_2.vb)]  
  
-   <span data-ttu-id="e1311-117">Można jawnie określić zakresu tablicy lub Opuść je i kompilatora wnioskować na podstawie wartości w tablicy literału granice tablicy.</span><span class="sxs-lookup"><span data-stu-id="e1311-117">You can explicitly specify the array bounds, or leave them out and have the compiler infer the array bounds based on the values in the array literal.</span></span> <span data-ttu-id="e1311-118">Jeśli podasz zarówno górną granicę, jak i wartości musi zawierać wartość dla każdego elementu z indeksem 0 za pomocą górnej granicy w każdego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="e1311-118">If you supply both the upper bounds and the values, you must include a value for every element from index 0 through the upper bound in every dimension.</span></span> <span data-ttu-id="e1311-119">W poniższym przykładzie pokazano kilka sposobów, aby zadeklarować, Utwórz i zainicjuj zmienną zawiera jest tablicą dwuwymiarową, który ma elementy typu`Short`</span><span class="sxs-lookup"><span data-stu-id="e1311-119">The following example shows several ways to declare, create, and initialize a variable to contain a two-dimensional array that has elements of type `Short`</span></span>  
  
     [!code-vb[VbVbalrArrays#18](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_3.vb)]  
  
     <span data-ttu-id="e1311-120">Po wykonaniu każdego instrukcji, utworzony tablica zawiera sześć zainicjowane elementów, które mają indeksy `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, i `(1,2)`.</span><span class="sxs-lookup"><span data-stu-id="e1311-120">After each statement executes, the created array contains six initialized elements that have indexes `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, and `(1,2)`.</span></span> <span data-ttu-id="e1311-121">Każda lokalizacja tablica zawiera wartość `10`.</span><span class="sxs-lookup"><span data-stu-id="e1311-121">Each array location contains the value `10`.</span></span>  
  
-   <span data-ttu-id="e1311-122">Poniższy przykład iterację tablicy wielowymiarowej.</span><span class="sxs-lookup"><span data-stu-id="e1311-122">The following example iterates through a multidimensional array.</span></span> <span data-ttu-id="e1311-123">W aplikacji konsoli systemu Windows, która jest napisany w języku Visual Basic, Wklej kod wewnątrz `Sub Main()` metody.</span><span class="sxs-lookup"><span data-stu-id="e1311-123">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span> <span data-ttu-id="e1311-124">Ostatni komentarze Pokaż dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="e1311-124">The last comments show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#31](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_4.vb)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a><span data-ttu-id="e1311-125">Można zainicjować zmiennej tablicy nieregularnej przy użyciu literałów tablicy</span><span class="sxs-lookup"><span data-stu-id="e1311-125">To initialize a jagged array variable by using array literals</span></span>  
  
-   <span data-ttu-id="e1311-126">Zagnieździć wartości obiektów w nawiasach klamrowych (`{}`).</span><span class="sxs-lookup"><span data-stu-id="e1311-126">Nest object values inside braces (`{}`).</span></span> <span data-ttu-id="e1311-127">Mimo że można zagnieżdżać Literały tablicy, określających tablice różne długości w przypadku tablicy nieregularnej, upewnij się, że który literały tablica zagnieżdżona są ujęte w nawiasy (`()`).</span><span class="sxs-lookup"><span data-stu-id="e1311-127">Although you can also nest array literals that specify arrays of different lengths, in the case of a jagged array, make sure that that the nested array literals are enclosed in parentheses (`()`).</span></span> <span data-ttu-id="e1311-128">Nawiasy wymusić oceny literały tablica zagnieżdżona, a wynikowy tablice są używane jako wartość początkową tablicy nieregularnej.</span><span class="sxs-lookup"><span data-stu-id="e1311-128">The parentheses force the evaluation of the nested array literals, and the resulting arrays are used as the initial values of the jagged array.</span></span> <span data-ttu-id="e1311-129">W poniższym przykładzie kodu przedstawiono dwa przykłady inicjowanie tablicy nieregularnej.</span><span class="sxs-lookup"><span data-stu-id="e1311-129">The following code example shows two examples of jagged array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#19](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_5.vb)]  
  
-   <span data-ttu-id="e1311-130">Poniższy przykład iterację tablicą nieregularną.</span><span class="sxs-lookup"><span data-stu-id="e1311-130">The following example iterates through a jagged array.</span></span> <span data-ttu-id="e1311-131">W aplikacji konsoli systemu Windows, która jest napisany w języku Visual Basic, Wklej kod wewnątrz `Sub Main()` metody.</span><span class="sxs-lookup"><span data-stu-id="e1311-131">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span>  <span data-ttu-id="e1311-132">Ostatni komentarze w kodzie Pokaż dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="e1311-132">The last comments in the code show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#32](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e1311-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1311-133">See Also</span></span>  
 [<span data-ttu-id="e1311-134">Tablice</span><span class="sxs-lookup"><span data-stu-id="e1311-134">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="e1311-135">Rozwiązywanie problemów z tablicami</span><span class="sxs-lookup"><span data-stu-id="e1311-135">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
