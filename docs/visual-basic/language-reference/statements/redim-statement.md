---
title: ReDim — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ReDim
- vb.Preserve
helpviewer_keywords:
- fixed-length strings [Visual Basic], declaring
- ReDim statement [Visual Basic], syntax
- dynamic arrays [Visual Basic], ReDim statement
- arrays [Visual Basic], reallocating
- arrays [Visual Basic], reinitializing
- arrays [Visual Basic], dimensions
- scalars, and arrays
- scalars
- declarations [Visual Basic], dynamic arrays
- variables [Visual Basic], scalar
- ReDim statement [Visual Basic]
- data types [Visual Basic], assigning
- As keyword [Visual Basic], in ReDim statement
- To keyword [Visual Basic], ReDim statement
- arrays [Visual Basic], declaring
- Preserve keyword [Visual Basic], ReDim statement
- storage [Visual Basic], allocating
- arrays [Visual Basic], and scalars
- declaration statements [Visual Basic]
- scalar variables [Visual Basic]
ms.assetid: ad1c5e07-dcd7-4ae1-a79e-ad3f2dcc2083
ms.openlocfilehash: 9536ea8a6274e0b4a2589caf5aefa271a3567d32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="redim-statement-visual-basic"></a><span data-ttu-id="26372-102">ReDim — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26372-102">ReDim Statement (Visual Basic)</span></span>
<span data-ttu-id="26372-103">Przydziela ponownie obszar przechowywania dla zmiennej tablicowej.</span><span class="sxs-lookup"><span data-stu-id="26372-103">Reallocates storage space for an array variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26372-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26372-104">Syntax</span></span>  
  
```  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="26372-105">Części</span><span class="sxs-lookup"><span data-stu-id="26372-105">Parts</span></span>  
  
|<span data-ttu-id="26372-106">Termin</span><span class="sxs-lookup"><span data-stu-id="26372-106">Term</span></span>|<span data-ttu-id="26372-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="26372-107">Definition</span></span>|  
|----------|----------------|  
|`Preserve`|<span data-ttu-id="26372-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="26372-108">Optional.</span></span> <span data-ttu-id="26372-109">Modyfikator używane w celu zachowania danych w istniejącej tablicy po zmianie rozmiaru tylko ostatniego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="26372-109">Modifier used to preserve the data in the existing array when you change the size of only the last dimension.</span></span>|  
|`name`|<span data-ttu-id="26372-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="26372-110">Required.</span></span> <span data-ttu-id="26372-111">Nazwa zmiennej tablicy.</span><span class="sxs-lookup"><span data-stu-id="26372-111">Name of the array variable.</span></span> <span data-ttu-id="26372-112">Zobacz temat[Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="26372-112">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`boundlist`|<span data-ttu-id="26372-113">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="26372-113">Required.</span></span> <span data-ttu-id="26372-114">Lista granic dla każdego wymiaru tablicy ponownie zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="26372-114">List of bounds of each dimension of the redefined array.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26372-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="26372-115">Remarks</span></span>  
 <span data-ttu-id="26372-116">Można użyć `ReDim` instrukcji, aby zmienić rozmiar co najmniej jeden wymiar tablicy, która została już zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="26372-116">You can use the `ReDim` statement to change the size of one or more dimensions of an array that has already been declared.</span></span> <span data-ttu-id="26372-117">Jeśli masz dużą tablicę i niektóre z jego elementów, nie są już potrzebne `ReDim` można zwolnić pamięć, zmniejszając rozmiar tablicy.</span><span class="sxs-lookup"><span data-stu-id="26372-117">If you have a large array and you no longer need some of its elements, `ReDim` can free up memory by reducing the array size.</span></span> <span data-ttu-id="26372-118">Z drugiej strony, jeśli tablica wymaga więcej elementów `ReDim` je dodać.</span><span class="sxs-lookup"><span data-stu-id="26372-118">On the other hand, if your array needs more elements, `ReDim` can add them.</span></span>  
  
 <span data-ttu-id="26372-119">`ReDim` Instrukcja jest przeznaczona tylko dla tablic.</span><span class="sxs-lookup"><span data-stu-id="26372-119">The `ReDim` statement is intended only for arrays.</span></span> <span data-ttu-id="26372-120">Nie jest prawidłowy w funkcji skalarnych (zmienne, które zawierają tylko jedną wartość), kolekcji lub struktury.</span><span class="sxs-lookup"><span data-stu-id="26372-120">It's not valid on scalars (variables that contain only a single value), collections, or structures.</span></span> <span data-ttu-id="26372-121">Należy pamiętać, że jeśli zadeklarować zmiennej typu `Array`, `ReDim` instrukcji nie ma wystarczających informacji o typie, do utworzenia nowej tablicy.</span><span class="sxs-lookup"><span data-stu-id="26372-121">Note that if you declare a variable to be of type `Array`, the `ReDim` statement doesn't have sufficient type information to create the new array.</span></span>  
  
 <span data-ttu-id="26372-122">Można użyć `ReDim` tylko na poziomie procedury.</span><span class="sxs-lookup"><span data-stu-id="26372-122">You can use `ReDim` only at procedure level.</span></span> <span data-ttu-id="26372-123">W związku z tym kontekście deklaracji zmiennej musi być procedury; Nie można go plik źródłowy, przestrzeni nazw, interfejs, klasy, struktury, modułu lub bloku.</span><span class="sxs-lookup"><span data-stu-id="26372-123">Therefore, the declaration context for the variable must be a procedure; it can't be a source file, a namespace, an interface, a class, a structure, a module, or a block.</span></span> <span data-ttu-id="26372-124">Aby uzyskać więcej informacji, zobacz [Declaration Contexts and Default Access Level](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md) (Kontekst deklaracji i domyślne poziomy dostępu).</span><span class="sxs-lookup"><span data-stu-id="26372-124">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="26372-125">Reguły</span><span class="sxs-lookup"><span data-stu-id="26372-125">Rules</span></span>  
  
-   <span data-ttu-id="26372-126">**Wiele zmiennych.**</span><span class="sxs-lookup"><span data-stu-id="26372-126">**Multiple Variables.**</span></span> <span data-ttu-id="26372-127">Można zmienić rozmiar kilku zmiennych tablicowych w tej samej instrukcji deklaracji i określić `name` i `boundlist` części dla każdej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="26372-127">You can resize several array variables in the same declaration statement and specify the `name` and `boundlist` parts for each variable.</span></span> <span data-ttu-id="26372-128">Wiele zmiennych są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="26372-128">Multiple variables are separated by commas.</span></span>  
  
-   <span data-ttu-id="26372-129">**Granice tablicy.**</span><span class="sxs-lookup"><span data-stu-id="26372-129">**Array Bounds.**</span></span> <span data-ttu-id="26372-130">Każdy wpis `boundlist` można określić dolną i górną granicę tego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="26372-130">Each entry in `boundlist` can specify the lower and upper bounds of that dimension.</span></span> <span data-ttu-id="26372-131">Dolna granica jest zawsze 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="26372-131">The lower bound is always 0 (zero).</span></span> <span data-ttu-id="26372-132">Górna granica jest największa wartość indeksu możliwe w dla tego wymiaru nie długość wymiaru (czyli górna granica plus jeden).</span><span class="sxs-lookup"><span data-stu-id="26372-132">The upper bound is the highest possible index value for that dimension, not the length of the dimension (which is the upper bound plus one).</span></span> <span data-ttu-id="26372-133">Indeks dla każdego wymiaru może się różnić od 0 do jego górna granica wartości.</span><span class="sxs-lookup"><span data-stu-id="26372-133">The index for each dimension can vary from 0 through its upper bound value.</span></span>  
  
     <span data-ttu-id="26372-134">Liczba wymiarów w `boundlist` oryginalna liczba wymiarów (rangę) tablicy musi być zgodna.</span><span class="sxs-lookup"><span data-stu-id="26372-134">The number of dimensions in `boundlist` must match the original number of dimensions (rank) of the array.</span></span>  
  
-   <span data-ttu-id="26372-135">**Typy danych.**</span><span class="sxs-lookup"><span data-stu-id="26372-135">**Data Types.**</span></span> <span data-ttu-id="26372-136">`ReDim` Instrukcji nie można zmienić typ danych zmiennej tablicy lub jego elementów.</span><span class="sxs-lookup"><span data-stu-id="26372-136">The `ReDim` statement cannot change the data type of an array variable or its elements.</span></span>  
  
-   <span data-ttu-id="26372-137">**Inicjowanie.**</span><span class="sxs-lookup"><span data-stu-id="26372-137">**Initialization.**</span></span> <span data-ttu-id="26372-138">`ReDim` Instrukcja nie może zapewnić nowe wartości inicjowania dla elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="26372-138">The `ReDim` statement cannot provide new initialization values for the array elements.</span></span>  
  
-   <span data-ttu-id="26372-139">**Ranga.**</span><span class="sxs-lookup"><span data-stu-id="26372-139">**Rank.**</span></span> <span data-ttu-id="26372-140">`ReDim` Instrukcji nie można zmienić rangą tablicy (liczba wymiarów).</span><span class="sxs-lookup"><span data-stu-id="26372-140">The `ReDim` statement cannot change the rank (the number of dimensions) of the array.</span></span>  
  
-   <span data-ttu-id="26372-141">**Zmiana rozmiaru z zachowaniem.**</span><span class="sxs-lookup"><span data-stu-id="26372-141">**Resizing with Preserve.**</span></span> <span data-ttu-id="26372-142">Jeśli używasz `Preserve`, zmianie rozmiaru tylko ostatniego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="26372-142">If you use `Preserve`, you can resize only the last dimension of the array.</span></span> <span data-ttu-id="26372-143">Dla każdego wymiaru należy określić granica istniejącej tablicy.</span><span class="sxs-lookup"><span data-stu-id="26372-143">For every other dimension, you must specify the bound of the existing array.</span></span>  
  
     <span data-ttu-id="26372-144">Na przykład jeśli tablica ma tylko jeden wymiar, można zmienić rozmiar tego wymiaru i nadal zachować całą zawartość tablicy, ponieważ zmieniasz ostatnie i tylko wymiaru.</span><span class="sxs-lookup"><span data-stu-id="26372-144">For example, if your array has only one dimension, you can resize that dimension and still preserve all the contents of the array, because you are changing the last and only dimension.</span></span> <span data-ttu-id="26372-145">Jednak jeśli tablica ma co najmniej dwa wymiary, można zmienić rozmiaru tylko ostatniego wymiaru użycie `Preserve`.</span><span class="sxs-lookup"><span data-stu-id="26372-145">However, if your array has two or more dimensions, you can change the size of only the last dimension if you use `Preserve`.</span></span>  
  
-   <span data-ttu-id="26372-146">**właściwości.**</span><span class="sxs-lookup"><span data-stu-id="26372-146">**Properties.**</span></span> <span data-ttu-id="26372-147">Można użyć `ReDim` dla właściwości, która przechowuje tablicy wartości.</span><span class="sxs-lookup"><span data-stu-id="26372-147">You can use `ReDim` on a property that holds an array of values.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="26372-148">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="26372-148">Behavior</span></span>  
  
-   <span data-ttu-id="26372-149">**Zastąpienie tablicy.**</span><span class="sxs-lookup"><span data-stu-id="26372-149">**Array Replacement.**</span></span> <span data-ttu-id="26372-150">`ReDim` zwalnia istniejącej tablicy i tworzy nową macierz z taką samą rangę.</span><span class="sxs-lookup"><span data-stu-id="26372-150">`ReDim` releases the existing array and creates a new array with the same rank.</span></span> <span data-ttu-id="26372-151">Nowej tablicy zastępuje wydanych tablicy w zmiennej tablicy.</span><span class="sxs-lookup"><span data-stu-id="26372-151">The new array replaces the released array in the array variable.</span></span>  
  
-   <span data-ttu-id="26372-152">**Inicjowanie bez Preserve.**</span><span class="sxs-lookup"><span data-stu-id="26372-152">**Initialization without Preserve.**</span></span> <span data-ttu-id="26372-153">Jeśli nie określisz `Preserve`, `ReDim` inicjuje elementy nowej tablicy przy użyciu wartości domyślnej dla jego typu danych.</span><span class="sxs-lookup"><span data-stu-id="26372-153">If you do not specify `Preserve`, `ReDim` initializes the elements of the new array by using the default value for their data type.</span></span>  
  
-   <span data-ttu-id="26372-154">**Inicjacja za pomocą atrybutu Preserve.**</span><span class="sxs-lookup"><span data-stu-id="26372-154">**Initialization with Preserve.**</span></span> <span data-ttu-id="26372-155">Jeśli określisz `Preserve`, Visual Basic kopiuje elementy z istniejącej tablicy do nowej tablicy.</span><span class="sxs-lookup"><span data-stu-id="26372-155">If you specify `Preserve`, Visual Basic copies the elements from the existing array to the new array.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26372-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="26372-156">Example</span></span>  
 <span data-ttu-id="26372-157">Poniższy przykład zwiększa rozmiar ostatniego wymiaru tablicy dynamicznej bez utraty istniejących danych w tablicy, a następnie zmniejszenie rozmiaru z częściowa utrata danych.</span><span class="sxs-lookup"><span data-stu-id="26372-157">The following example increases the size of the last dimension of a dynamic array without losing any existing data in the array, and then decreases the size with partial data loss.</span></span> <span data-ttu-id="26372-158">Na koniec zmniejsza rozmiar do oryginalnej wartości i ponownie inicjuje wszystkie elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="26372-158">Finally, it decreases the size back to its original value and reinitializes all the array elements.</span></span>  
  
 [!code-vb[VbVbalrStatements#52](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/redim-statement_1.vb)]  
  
 <span data-ttu-id="26372-159">`Dim` Instrukcja tworzy nową macierz z trzech wymiarów.</span><span class="sxs-lookup"><span data-stu-id="26372-159">The `Dim` statement creates a new array with three dimensions.</span></span> <span data-ttu-id="26372-160">Każdy wymiar jest zadeklarowany z granicą 10, więc indeks tablicy dla każdego wymiaru mogą należeć do zakresu od 0 do 10.</span><span class="sxs-lookup"><span data-stu-id="26372-160">Each dimension is declared with a bound of 10, so the array index for each dimension can range from 0 through 10.</span></span> <span data-ttu-id="26372-161">W poniższych kwestii trzy wymiary są nazywane warstwy, wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="26372-161">In the following discussion, the three dimensions are referred to as layer, row, and column.</span></span>  
  
 <span data-ttu-id="26372-162">Pierwszy `ReDim` tworzy nowy tablicy, która zastępuje istniejącą tablicę w zmiennej `intArray`.</span><span class="sxs-lookup"><span data-stu-id="26372-162">The first `ReDim` creates a new array which replaces the existing array in variable `intArray`.</span></span> <span data-ttu-id="26372-163">`ReDim` kopiuje wszystkie elementy z istniejącej tablicy do nowej tablicy.</span><span class="sxs-lookup"><span data-stu-id="26372-163">`ReDim` copies all the elements from the existing array into the new array.</span></span> <span data-ttu-id="26372-164">Również dodaje 10 większą liczbę kolumn na końcu każdego wiersza w każdej warstwie i inicjuje elementów w tych nowych kolumn na wartość 0 (wartość domyślna `Integer`, który jest typem elementu tablicy).</span><span class="sxs-lookup"><span data-stu-id="26372-164">It also adds 10 more columns to the end of every row in every layer and initializes the elements in these new columns to 0 (the default value of `Integer`, which is the element type of the array).</span></span>  
  
 <span data-ttu-id="26372-165">Drugi `ReDim` tworzy innej tablicy nowy i kopiuje wszystkie elementy, które pasują do.</span><span class="sxs-lookup"><span data-stu-id="26372-165">The second `ReDim` creates another new array and copies all the elements that fit.</span></span> <span data-ttu-id="26372-166">Jednak pięć kolumn zostaną utracone po zakończeniu każdego wiersza w każdej warstwie.</span><span class="sxs-lookup"><span data-stu-id="26372-166">However, five columns are lost from the end of every row in every layer.</span></span> <span data-ttu-id="26372-167">Nie jest to problem, po zakończeniu przy użyciu tych kolumn.</span><span class="sxs-lookup"><span data-stu-id="26372-167">This is not a problem if you have finished using these columns.</span></span> <span data-ttu-id="26372-168">Zmniejszenie rozmiaru dużą tablicę można zwolnić pamięć, które nie są już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="26372-168">Reducing the size of a large array can free up memory that you no longer need.</span></span>  
  
 <span data-ttu-id="26372-169">Trzeci `ReDim` tworzy innej tablicy nowy i usuwa innego pięć kolumn z koniec każdego wiersza w każdej warstwie.</span><span class="sxs-lookup"><span data-stu-id="26372-169">The third `ReDim` creates another new array and removes another five columns from the end of every row in every layer.</span></span> <span data-ttu-id="26372-170">Tym razem nie kopiuje elementy.</span><span class="sxs-lookup"><span data-stu-id="26372-170">This time it does not copy any existing elements.</span></span> <span data-ttu-id="26372-171">Tej instrukcji zostanie przywrócona do oryginalnego rozmiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="26372-171">This statement reverts the array to its original size.</span></span> <span data-ttu-id="26372-172">Ponieważ nie zawiera instrukcji `Preserve` modyfikator, ustawia wszystkie elementy tablicy oryginalnych wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="26372-172">Because the statement doesn't include the `Preserve` modifier, it sets all array elements to their original default values.</span></span>  
  
 <span data-ttu-id="26372-173">Aby uzyskać dodatkowe przykłady, zobacz [tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="26372-173">For additional examples, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26372-174">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26372-174">See Also</span></span>  
 <xref:System.IndexOutOfRangeException>  
 [<span data-ttu-id="26372-175">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="26372-175">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="26372-176">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="26372-176">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="26372-177">Erase, instrukcja</span><span class="sxs-lookup"><span data-stu-id="26372-177">Erase Statement</span></span>](../../../visual-basic/language-reference/statements/erase-statement.md)  
 [<span data-ttu-id="26372-178">Nothing</span><span class="sxs-lookup"><span data-stu-id="26372-178">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="26372-179">Tablice</span><span class="sxs-lookup"><span data-stu-id="26372-179">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
