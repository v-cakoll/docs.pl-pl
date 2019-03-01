---
title: ReDim, instrukcja (Visual Basic)
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
ms.openlocfilehash: 6ee30e885a08d3e8302d7b6083c1c65e525006c5
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973434"
---
# <a name="redim-statement-visual-basic"></a><span data-ttu-id="6b575-102">ReDim, instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b575-102">ReDim Statement (Visual Basic)</span></span>
<span data-ttu-id="6b575-103">Przydziela ponownie obszar przechowywania dla zmiennej tablicowej.</span><span class="sxs-lookup"><span data-stu-id="6b575-103">Reallocates storage space for an array variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b575-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b575-104">Syntax</span></span>  
  
```  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="6b575-105">Części</span><span class="sxs-lookup"><span data-stu-id="6b575-105">Parts</span></span>  
  
|<span data-ttu-id="6b575-106">Termin</span><span class="sxs-lookup"><span data-stu-id="6b575-106">Term</span></span>|<span data-ttu-id="6b575-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="6b575-107">Definition</span></span>|  
|----------|----------------|  
|`Preserve`|<span data-ttu-id="6b575-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="6b575-108">Optional.</span></span> <span data-ttu-id="6b575-109">Modyfikator używany w celu zachowania danych w istniejącej tablicy, gdy zmieniany jest rozmiar tylko ostatniego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="6b575-109">Modifier used to preserve the data in the existing array when you change the size of only the last dimension.</span></span>|  
|`name`|<span data-ttu-id="6b575-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="6b575-110">Required.</span></span> <span data-ttu-id="6b575-111">Nazwa zmiennej tablicowej.</span><span class="sxs-lookup"><span data-stu-id="6b575-111">Name of the array variable.</span></span> <span data-ttu-id="6b575-112">Zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="6b575-112">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`boundlist`|<span data-ttu-id="6b575-113">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="6b575-113">Required.</span></span> <span data-ttu-id="6b575-114">Lista granic każdego wymiaru dla ponownie definiowanej tablicy.</span><span class="sxs-lookup"><span data-stu-id="6b575-114">List of bounds of each dimension of the redefined array.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b575-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b575-115">Remarks</span></span>  
 <span data-ttu-id="6b575-116">Za pomocą instrukcji `ReDim` można zmienić rozmiar co najmniej jednego wymiaru tablicy, która została już zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="6b575-116">You can use the `ReDim` statement to change the size of one or more dimensions of an array that has already been declared.</span></span> <span data-ttu-id="6b575-117">Jeśli tablica jest duża i niektóre z jej elementów nie są już potrzebne, instrukcja `ReDim` może zwolnić pamięć, zmniejszając rozmiar tablicy.</span><span class="sxs-lookup"><span data-stu-id="6b575-117">If you have a large array and you no longer need some of its elements, `ReDim` can free up memory by reducing the array size.</span></span> <span data-ttu-id="6b575-118">Z drugiej strony, jeśli tablica wymaga więcej elementów, instrukcja `ReDim` może je dodać.</span><span class="sxs-lookup"><span data-stu-id="6b575-118">On the other hand, if your array needs more elements, `ReDim` can add them.</span></span>  
  
 <span data-ttu-id="6b575-119">Instrukcja `ReDim` jest przeznaczona tylko dla tablic.</span><span class="sxs-lookup"><span data-stu-id="6b575-119">The `ReDim` statement is intended only for arrays.</span></span> <span data-ttu-id="6b575-120">Nie jest odpowiednia dla właściwości skalarnych (zmienne, które zawierają tylko jedną wartość), kolekcji ani struktur.</span><span class="sxs-lookup"><span data-stu-id="6b575-120">It's not valid on scalars (variables that contain only a single value), collections, or structures.</span></span> <span data-ttu-id="6b575-121">Pamiętaj, że jeśli deklarujesz zmienną typu `Array`, instrukcja `ReDim` nie ma wystarczających informacji o typie, aby utworzyć nową tablicę.</span><span class="sxs-lookup"><span data-stu-id="6b575-121">Note that if you declare a variable to be of type `Array`, the `ReDim` statement doesn't have sufficient type information to create the new array.</span></span>  
  
 <span data-ttu-id="6b575-122">Instrukcji `ReDim` można używać tylko na poziomie procedury.</span><span class="sxs-lookup"><span data-stu-id="6b575-122">You can use `ReDim` only at procedure level.</span></span> <span data-ttu-id="6b575-123">W związku z tym, kontekstem deklaracji zmiennej musi być procedura, a nie plik źródłowy, przestrzeń nazw, interfejs, klasa, struktura, moduł czy blok.</span><span class="sxs-lookup"><span data-stu-id="6b575-123">Therefore, the declaration context for the variable must be a procedure; it can't be a source file, a namespace, an interface, a class, a structure, a module, or a block.</span></span> <span data-ttu-id="6b575-124">Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6b575-124">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6b575-125">reguły</span><span class="sxs-lookup"><span data-stu-id="6b575-125">Rules</span></span>  
  
-   <span data-ttu-id="6b575-126">**Wiele zmiennych.**</span><span class="sxs-lookup"><span data-stu-id="6b575-126">**Multiple Variables.**</span></span> <span data-ttu-id="6b575-127">Można zmienić rozmiar kilku zmiennych tablicowych w tej samej instrukcji deklaracji oraz określić części `name` i `boundlist` dla każdej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6b575-127">You can resize several array variables in the same declaration statement and specify the `name` and `boundlist` parts for each variable.</span></span> <span data-ttu-id="6b575-128">Wiele zmiennych rozdziela się przecinkami.</span><span class="sxs-lookup"><span data-stu-id="6b575-128">Multiple variables are separated by commas.</span></span>  
  
-   <span data-ttu-id="6b575-129">**Granice tablicy.**</span><span class="sxs-lookup"><span data-stu-id="6b575-129">**Array Bounds.**</span></span> <span data-ttu-id="6b575-130">Każdy wpis w części `boundlist` może określać dolną i górną granicę tego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="6b575-130">Each entry in `boundlist` can specify the lower and upper bounds of that dimension.</span></span> <span data-ttu-id="6b575-131">Dolna granica jest zawsze równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="6b575-131">The lower bound is always 0 (zero).</span></span> <span data-ttu-id="6b575-132">Górna granica jest najwyższą możliwą wartością indeksu dla tego wymiaru, a nie długością wymiaru (która jest większa o jeden od górnej granicy).</span><span class="sxs-lookup"><span data-stu-id="6b575-132">The upper bound is the highest possible index value for that dimension, not the length of the dimension (which is the upper bound plus one).</span></span> <span data-ttu-id="6b575-133">Indeks dla każdego wymiaru może się zmieniać od 0 do górnej wartości.</span><span class="sxs-lookup"><span data-stu-id="6b575-133">The index for each dimension can vary from 0 through its upper bound value.</span></span>  
  
     <span data-ttu-id="6b575-134">Liczba wymiarów w części `boundlist` musi być zgodna z oryginalną liczbą wymiarów (rangą) tablicy.</span><span class="sxs-lookup"><span data-stu-id="6b575-134">The number of dimensions in `boundlist` must match the original number of dimensions (rank) of the array.</span></span>  
  
-   <span data-ttu-id="6b575-135">**Typy danych.**</span><span class="sxs-lookup"><span data-stu-id="6b575-135">**Data Types.**</span></span> <span data-ttu-id="6b575-136">Instrukcja `ReDim` nie może zmieniać typu danych zmiennej tablicowej ani jej elementów.</span><span class="sxs-lookup"><span data-stu-id="6b575-136">The `ReDim` statement cannot change the data type of an array variable or its elements.</span></span>  
  
-   <span data-ttu-id="6b575-137">**Inicjowanie.**</span><span class="sxs-lookup"><span data-stu-id="6b575-137">**Initialization.**</span></span> <span data-ttu-id="6b575-138">Instrukcja `ReDim` nie może podawać nowych wartości inicjalizacji dla elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="6b575-138">The `ReDim` statement cannot provide new initialization values for the array elements.</span></span>  
  
-   <span data-ttu-id="6b575-139">**Ranga.**</span><span class="sxs-lookup"><span data-stu-id="6b575-139">**Rank.**</span></span> <span data-ttu-id="6b575-140">Instrukcja `ReDim` nie może zmienić rangi (liczby wymiarów) tablicy.</span><span class="sxs-lookup"><span data-stu-id="6b575-140">The `ReDim` statement cannot change the rank (the number of dimensions) of the array.</span></span>  
  
-   <span data-ttu-id="6b575-141">**Zmiana rozmiaru z zachowaniem zawartości.**</span><span class="sxs-lookup"><span data-stu-id="6b575-141">**Resizing with Preserve.**</span></span> <span data-ttu-id="6b575-142">Jeśli używasz części `Preserve`, możesz zmienić rozmiar tylko ostatniego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="6b575-142">If you use `Preserve`, you can resize only the last dimension of the array.</span></span> <span data-ttu-id="6b575-143">Dla wszystkich pozostałych wymiarów musisz określić granicę istniejącej tablicy.</span><span class="sxs-lookup"><span data-stu-id="6b575-143">For every other dimension, you must specify the bound of the existing array.</span></span>  
  
     <span data-ttu-id="6b575-144">Na przykład jeśli tablica ma tylko jeden wymiar, możesz zmienić rozmiar tego wymiaru i nadal zachować całą zawartość tablicy, ponieważ zmieniasz ostatni i jedyny wymiar.</span><span class="sxs-lookup"><span data-stu-id="6b575-144">For example, if your array has only one dimension, you can resize that dimension and still preserve all the contents of the array, because you are changing the last and only dimension.</span></span> <span data-ttu-id="6b575-145">Jednak jeśli Twoja tablica ma co najmniej dwa wymiary, korzystając z części `Preserve` możesz zmienić rozmiar tylko ostatniego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="6b575-145">However, if your array has two or more dimensions, you can change the size of only the last dimension if you use `Preserve`.</span></span>  
  
-   <span data-ttu-id="6b575-146">**Właściwości.**</span><span class="sxs-lookup"><span data-stu-id="6b575-146">**Properties.**</span></span> <span data-ttu-id="6b575-147">Instrukcji `ReDim` można użyć dla właściwości, która przechowuje tablicę wartości.</span><span class="sxs-lookup"><span data-stu-id="6b575-147">You can use `ReDim` on a property that holds an array of values.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="6b575-148">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="6b575-148">Behavior</span></span>  
  
-   <span data-ttu-id="6b575-149">**Zamiana tablicy.**</span><span class="sxs-lookup"><span data-stu-id="6b575-149">**Array Replacement.**</span></span> <span data-ttu-id="6b575-150">Instrukcja `ReDim` zwalnia istniejącą tablicę i tworzy nową tablicę o tej samej randze.</span><span class="sxs-lookup"><span data-stu-id="6b575-150">`ReDim` releases the existing array and creates a new array with the same rank.</span></span> <span data-ttu-id="6b575-151">Nowa tablica zastępuje zwalnianą tablicę w zmiennej tablicowej.</span><span class="sxs-lookup"><span data-stu-id="6b575-151">The new array replaces the released array in the array variable.</span></span>  
  
-   <span data-ttu-id="6b575-152">**Inicjowanie bez zachowania zawartości.**</span><span class="sxs-lookup"><span data-stu-id="6b575-152">**Initialization without Preserve.**</span></span> <span data-ttu-id="6b575-153">Jeśli nie określisz części `Preserve`, instrukcja `ReDim` zainicjuje elementy nowej tablicy, używając domyślnej wartości dla ich typu danych.</span><span class="sxs-lookup"><span data-stu-id="6b575-153">If you do not specify `Preserve`, `ReDim` initializes the elements of the new array by using the default value for their data type.</span></span>  
  
-   <span data-ttu-id="6b575-154">**Inicjowanie z zachowaniem zawartości**</span><span class="sxs-lookup"><span data-stu-id="6b575-154">**Initialization with Preserve.**</span></span> <span data-ttu-id="6b575-155">Jeśli określisz część `Preserve`, język Visual Basic skopiuje elementy z istniejącej tablicy do nowej tablicy.</span><span class="sxs-lookup"><span data-stu-id="6b575-155">If you specify `Preserve`, Visual Basic copies the elements from the existing array to the new array.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b575-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="6b575-156">Example</span></span>  
 <span data-ttu-id="6b575-157">W poniższym przykładzie jest pokazane zwiększenie rozmiaru ostatniego wymiaru tablicy dynamicznej bez utraty istniejących danych w tablicy, a następnie zmniejszenie rozmiaru z częściową utratą danych.</span><span class="sxs-lookup"><span data-stu-id="6b575-157">The following example increases the size of the last dimension of a dynamic array without losing any existing data in the array, and then decreases the size with partial data loss.</span></span> <span data-ttu-id="6b575-158">Na koniec następuje zmniejszenie rozmiaru do oryginalnej wartości i ponownie inicjowanie wszystkich elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="6b575-158">Finally, it decreases the size back to its original value and reinitializes all the array elements.</span></span>  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 <span data-ttu-id="6b575-159">Instrukcja `Dim` tworzy nową tablicę z trzema wymiarami.</span><span class="sxs-lookup"><span data-stu-id="6b575-159">The `Dim` statement creates a new array with three dimensions.</span></span> <span data-ttu-id="6b575-160">Każdy wymiar jest zadeklarowany z granicą 10, więc indeks tablicy dla każdego wymiaru może wynosić od 0 do 10.</span><span class="sxs-lookup"><span data-stu-id="6b575-160">Each dimension is declared with a bound of 10, so the array index for each dimension can range from 0 through 10.</span></span> <span data-ttu-id="6b575-161">W poniższym omówieniu te trzy wymiary są określane jako warstwa, wiersz i kolumna.</span><span class="sxs-lookup"><span data-stu-id="6b575-161">In the following discussion, the three dimensions are referred to as layer, row, and column.</span></span>  
  
 <span data-ttu-id="6b575-162">Pierwsza instrukcja `ReDim` tworzy nową tablicę, która zastępuje istniejącą tablicę w zmiennej `intArray`.</span><span class="sxs-lookup"><span data-stu-id="6b575-162">The first `ReDim` creates a new array which replaces the existing array in variable `intArray`.</span></span> <span data-ttu-id="6b575-163">Instrukcja `ReDim` kopiuje wszystkie elementy z istniejącej tablicy do nowej tablicy.</span><span class="sxs-lookup"><span data-stu-id="6b575-163">`ReDim` copies all the elements from the existing array into the new array.</span></span> <span data-ttu-id="6b575-164">Dodaje również dodatkowe 10 kolumn na końcu każdego wiersza w każdej warstwie i inicjuje elementy w tych nowych kolumnach z wartością 0 (wartość domyślna `Integer`, który jest typem elementu tablicy).</span><span class="sxs-lookup"><span data-stu-id="6b575-164">It also adds 10 more columns to the end of every row in every layer and initializes the elements in these new columns to 0 (the default value of `Integer`, which is the element type of the array).</span></span>  
  
 <span data-ttu-id="6b575-165">Druga instrukcja `ReDim` tworzy kolejną nową tablicę i kopiuje wszystkie mieszczące się elementy.</span><span class="sxs-lookup"><span data-stu-id="6b575-165">The second `ReDim` creates another new array and copies all the elements that fit.</span></span> <span data-ttu-id="6b575-166">Jednak pięć kolumn od końca każdego wiersza w każdej warstwie jest traconych.</span><span class="sxs-lookup"><span data-stu-id="6b575-166">However, five columns are lost from the end of every row in every layer.</span></span> <span data-ttu-id="6b575-167">Nie stanowi to problemu, jeśli już nie używasz tych kolumn.</span><span class="sxs-lookup"><span data-stu-id="6b575-167">This is not a problem if you have finished using these columns.</span></span> <span data-ttu-id="6b575-168">Zmniejszenie rozmiaru dużej tablicy może zwolnić pamięć, której już nie potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="6b575-168">Reducing the size of a large array can free up memory that you no longer need.</span></span>  
  
 <span data-ttu-id="6b575-169">Trzecia instrukcja `ReDim` tworzy kolejną nową tablicę i usuwa kolejne pięć kolumn od końca każdego wiersza w każdej warstwie.</span><span class="sxs-lookup"><span data-stu-id="6b575-169">The third `ReDim` creates another new array and removes another five columns from the end of every row in every layer.</span></span> <span data-ttu-id="6b575-170">Tym razem nie kopiuje żadnych istniejących elementów.</span><span class="sxs-lookup"><span data-stu-id="6b575-170">This time it does not copy any existing elements.</span></span> <span data-ttu-id="6b575-171">Ta instrukcja przywraca tablicę do jej oryginalnego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="6b575-171">This statement reverts the array to its original size.</span></span> <span data-ttu-id="6b575-172">Ponieważ instrukcja nie zawiera modyfikatora `Preserve`, ustawia wszystkie elementy tablicy na pierwotne wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="6b575-172">Because the statement doesn't include the `Preserve` modifier, it sets all array elements to their original default values.</span></span>  
  
 <span data-ttu-id="6b575-173">Aby uzyskać dodatkowe przykłady, zobacz [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="6b575-173">For additional examples, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b575-174">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b575-174">See also</span></span>
- <xref:System.IndexOutOfRangeException>
- [<span data-ttu-id="6b575-175">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6b575-175">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="6b575-176">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6b575-176">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="6b575-177">Erase, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6b575-177">Erase Statement</span></span>](../../../visual-basic/language-reference/statements/erase-statement.md)
- [<span data-ttu-id="6b575-178">Nothing</span><span class="sxs-lookup"><span data-stu-id="6b575-178">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="6b575-179">Tablice</span><span class="sxs-lookup"><span data-stu-id="6b575-179">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
