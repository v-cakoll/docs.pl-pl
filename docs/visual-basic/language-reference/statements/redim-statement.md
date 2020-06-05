---
title: ReDim, instrukcja
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
ms.openlocfilehash: 82f19762865fdf3c3f32a0349e21e3b97bebd567
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404281"
---
# <a name="redim-statement-visual-basic"></a><span data-ttu-id="9a773-102">ReDim — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a773-102">ReDim Statement (Visual Basic)</span></span>
<span data-ttu-id="9a773-103">Ponownie przydziela miejsce do magazynowania dla zmiennej tablicowej.</span><span class="sxs-lookup"><span data-stu-id="9a773-103">Reallocates storage space for an array variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a773-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a773-104">Syntax</span></span>  
  
```vb  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="9a773-105">Części</span><span class="sxs-lookup"><span data-stu-id="9a773-105">Parts</span></span>  
  
|<span data-ttu-id="9a773-106">Termin</span><span class="sxs-lookup"><span data-stu-id="9a773-106">Term</span></span>|<span data-ttu-id="9a773-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="9a773-107">Definition</span></span>|  
|----------|----------------|  
|`Preserve`|<span data-ttu-id="9a773-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9a773-108">Optional.</span></span> <span data-ttu-id="9a773-109">Modyfikator używany do zachowania danych w istniejącej tablicy po zmianie rozmiaru tylko ostatniego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="9a773-109">Modifier used to preserve the data in the existing array when you change the size of only the last dimension.</span></span>|  
|`name`|<span data-ttu-id="9a773-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="9a773-110">Required.</span></span> <span data-ttu-id="9a773-111">Nazwa zmiennej tablicowej.</span><span class="sxs-lookup"><span data-stu-id="9a773-111">Name of the array variable.</span></span> <span data-ttu-id="9a773-112">Zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="9a773-112">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`boundlist`|<span data-ttu-id="9a773-113">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="9a773-113">Required.</span></span> <span data-ttu-id="9a773-114">Lista granic każdego wymiaru ponownie zdefiniowanej tablicy.</span><span class="sxs-lookup"><span data-stu-id="9a773-114">List of bounds of each dimension of the redefined array.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a773-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a773-115">Remarks</span></span>  
 <span data-ttu-id="9a773-116">Możesz użyć instrukcji, `ReDim` Aby zmienić rozmiar co najmniej jednego wymiaru tablicy, która została już zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="9a773-116">You can use the `ReDim` statement to change the size of one or more dimensions of an array that has already been declared.</span></span> <span data-ttu-id="9a773-117">Jeśli masz dużą tablicę i nie potrzebujesz już niektórych jej elementów, `ReDim` można zwolnić pamięć, zmniejszając rozmiar tablicy.</span><span class="sxs-lookup"><span data-stu-id="9a773-117">If you have a large array and you no longer need some of its elements, `ReDim` can free up memory by reducing the array size.</span></span> <span data-ttu-id="9a773-118">Z drugiej strony, jeśli tablica wymaga więcej elementów, `ReDim` można je dodać.</span><span class="sxs-lookup"><span data-stu-id="9a773-118">On the other hand, if your array needs more elements, `ReDim` can add them.</span></span>  
  
 <span data-ttu-id="9a773-119">`ReDim`Instrukcja jest przeznaczona tylko dla tablic.</span><span class="sxs-lookup"><span data-stu-id="9a773-119">The `ReDim` statement is intended only for arrays.</span></span> <span data-ttu-id="9a773-120">Nie jest on prawidłowy w przypadku wartości skalarnych (zmiennych, które zawierają tylko jedną wartość), kolekcji lub struktur.</span><span class="sxs-lookup"><span data-stu-id="9a773-120">It's not valid on scalars (variables that contain only a single value), collections, or structures.</span></span> <span data-ttu-id="9a773-121">Należy pamiętać, że Jeśli zadeklarujesz zmienną do typu `Array` , `ReDim` instrukcja nie ma wystarczających informacji o typie, aby utworzyć nową tablicę.</span><span class="sxs-lookup"><span data-stu-id="9a773-121">Note that if you declare a variable to be of type `Array`, the `ReDim` statement doesn't have sufficient type information to create the new array.</span></span>  
  
 <span data-ttu-id="9a773-122">Można używać `ReDim` tylko na poziomie procedury.</span><span class="sxs-lookup"><span data-stu-id="9a773-122">You can use `ReDim` only at procedure level.</span></span> <span data-ttu-id="9a773-123">W związku z tym, kontekst deklaracji dla zmiennej musi być procedurą; nie może być plikiem źródłowym, przestrzenią nazw, interfejsem, klasą, strukturą, modułem lub blokiem.</span><span class="sxs-lookup"><span data-stu-id="9a773-123">Therefore, the declaration context for the variable must be a procedure; it can't be a source file, a namespace, an interface, a class, a structure, a module, or a block.</span></span> <span data-ttu-id="9a773-124">Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="9a773-124">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="9a773-125">Reguły</span><span class="sxs-lookup"><span data-stu-id="9a773-125">Rules</span></span>  
  
- <span data-ttu-id="9a773-126">**Wiele zmiennych.**</span><span class="sxs-lookup"><span data-stu-id="9a773-126">**Multiple Variables.**</span></span> <span data-ttu-id="9a773-127">Można zmienić rozmiar kilku zmiennych tablicowych w tej samej instrukcji deklaracji i określić `name` `boundlist` części i dla każdej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9a773-127">You can resize several array variables in the same declaration statement and specify the `name` and `boundlist` parts for each variable.</span></span> <span data-ttu-id="9a773-128">Wiele zmiennych jest oddzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="9a773-128">Multiple variables are separated by commas.</span></span>  
  
- <span data-ttu-id="9a773-129">**Granice tablicy.**</span><span class="sxs-lookup"><span data-stu-id="9a773-129">**Array Bounds.**</span></span> <span data-ttu-id="9a773-130">Każdy wpis w programie `boundlist` może określać dolną i górną granicę tego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="9a773-130">Each entry in `boundlist` can specify the lower and upper bounds of that dimension.</span></span> <span data-ttu-id="9a773-131">Dolna granica jest zawsze równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="9a773-131">The lower bound is always 0 (zero).</span></span> <span data-ttu-id="9a773-132">Górna granica to najwyższa możliwa wartość indeksu dla tego wymiaru, a nie długość wymiaru (jest to górna granica plus jeden).</span><span class="sxs-lookup"><span data-stu-id="9a773-132">The upper bound is the highest possible index value for that dimension, not the length of the dimension (which is the upper bound plus one).</span></span> <span data-ttu-id="9a773-133">Indeks każdego wymiaru może się różnić od 0 za pośrednictwem jego górnej wartości powiązanej.</span><span class="sxs-lookup"><span data-stu-id="9a773-133">The index for each dimension can vary from 0 through its upper bound value.</span></span>  
  
     <span data-ttu-id="9a773-134">Liczba wymiarów w `boundlist` musi być zgodna z oryginalną liczbą wymiarów (rangą) tablicy.</span><span class="sxs-lookup"><span data-stu-id="9a773-134">The number of dimensions in `boundlist` must match the original number of dimensions (rank) of the array.</span></span>  
  
- <span data-ttu-id="9a773-135">**Typy danych.**</span><span class="sxs-lookup"><span data-stu-id="9a773-135">**Data Types.**</span></span> <span data-ttu-id="9a773-136">`ReDim`Instrukcja nie może zmienić typu danych zmiennej tablicowej ani jej elementów.</span><span class="sxs-lookup"><span data-stu-id="9a773-136">The `ReDim` statement cannot change the data type of an array variable or its elements.</span></span>  
  
- <span data-ttu-id="9a773-137">**Zainicjować.**</span><span class="sxs-lookup"><span data-stu-id="9a773-137">**Initialization.**</span></span> <span data-ttu-id="9a773-138">`ReDim`Instrukcja nie może podawać nowych wartości inicjujących dla elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="9a773-138">The `ReDim` statement cannot provide new initialization values for the array elements.</span></span>  
  
- <span data-ttu-id="9a773-139">**Stopni.**</span><span class="sxs-lookup"><span data-stu-id="9a773-139">**Rank.**</span></span> <span data-ttu-id="9a773-140">`ReDim`Instrukcja nie może zmienić rangi (liczby wymiarów) tablicy.</span><span class="sxs-lookup"><span data-stu-id="9a773-140">The `ReDim` statement cannot change the rank (the number of dimensions) of the array.</span></span>  
  
- <span data-ttu-id="9a773-141">**Zmienianie rozmiarów przy zachowaniu.**</span><span class="sxs-lookup"><span data-stu-id="9a773-141">**Resizing with Preserve.**</span></span> <span data-ttu-id="9a773-142">Jeśli używasz `Preserve` , możesz zmienić rozmiar tylko ostatniego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="9a773-142">If you use `Preserve`, you can resize only the last dimension of the array.</span></span> <span data-ttu-id="9a773-143">Dla każdego innego wymiaru należy określić granicę istniejącej tablicy.</span><span class="sxs-lookup"><span data-stu-id="9a773-143">For every other dimension, you must specify the bound of the existing array.</span></span>  
  
     <span data-ttu-id="9a773-144">Na przykład jeśli tablica ma tylko jeden wymiar, można zmienić rozmiar tego wymiaru i nadal zachować całą zawartość tablicy, ponieważ zmieniany jest ostatni i tylko wymiar.</span><span class="sxs-lookup"><span data-stu-id="9a773-144">For example, if your array has only one dimension, you can resize that dimension and still preserve all the contents of the array, because you are changing the last and only dimension.</span></span> <span data-ttu-id="9a773-145">Jeśli jednak tablica ma dwa lub więcej wymiarów, można zmienić rozmiar tylko ostatniego wymiaru, jeśli używasz `Preserve` .</span><span class="sxs-lookup"><span data-stu-id="9a773-145">However, if your array has two or more dimensions, you can change the size of only the last dimension if you use `Preserve`.</span></span>  
  
- <span data-ttu-id="9a773-146">**Aœciwoœci.**</span><span class="sxs-lookup"><span data-stu-id="9a773-146">**Properties.**</span></span> <span data-ttu-id="9a773-147">Można użyć `ReDim` na właściwości, która przechowuje tablicę wartości.</span><span class="sxs-lookup"><span data-stu-id="9a773-147">You can use `ReDim` on a property that holds an array of values.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="9a773-148">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="9a773-148">Behavior</span></span>  
  
- <span data-ttu-id="9a773-149">**Zastępowanie tablicy.**</span><span class="sxs-lookup"><span data-stu-id="9a773-149">**Array Replacement.**</span></span> <span data-ttu-id="9a773-150">`ReDim`zwalnia istniejącą tablicę i tworzy nową tablicę o tej samej rangi.</span><span class="sxs-lookup"><span data-stu-id="9a773-150">`ReDim` releases the existing array and creates a new array with the same rank.</span></span> <span data-ttu-id="9a773-151">Nowa tablica zastępuje wydaną tablicę w zmiennej tablicowej.</span><span class="sxs-lookup"><span data-stu-id="9a773-151">The new array replaces the released array in the array variable.</span></span>  
  
- <span data-ttu-id="9a773-152">**Inicjalizacja bez zachowania.**</span><span class="sxs-lookup"><span data-stu-id="9a773-152">**Initialization without Preserve.**</span></span> <span data-ttu-id="9a773-153">Jeśli nie określisz `Preserve` , `ReDim` inicjuje elementy nowej tablicy przy użyciu wartości domyślnej dla ich typu danych.</span><span class="sxs-lookup"><span data-stu-id="9a773-153">If you do not specify `Preserve`, `ReDim` initializes the elements of the new array by using the default value for their data type.</span></span>  
  
- <span data-ttu-id="9a773-154">**Inicjowanie z zachowaniem.**</span><span class="sxs-lookup"><span data-stu-id="9a773-154">**Initialization with Preserve.**</span></span> <span data-ttu-id="9a773-155">Jeśli określisz `Preserve` , Visual Basic Kopiuje elementy z istniejącej tablicy do nowej tablicy.</span><span class="sxs-lookup"><span data-stu-id="9a773-155">If you specify `Preserve`, Visual Basic copies the elements from the existing array to the new array.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a773-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a773-156">Example</span></span>  
 <span data-ttu-id="9a773-157">Poniższy przykład zwiększa rozmiar ostatniego wymiaru tablicy dynamicznej bez utraty istniejących danych w tablicy, a następnie zmniejsza rozmiar ze częściową utratą danych.</span><span class="sxs-lookup"><span data-stu-id="9a773-157">The following example increases the size of the last dimension of a dynamic array without losing any existing data in the array, and then decreases the size with partial data loss.</span></span> <span data-ttu-id="9a773-158">Na koniec zmniejsza rozmiar z powrotem do pierwotnej wartości i ponownie inicjuje wszystkie elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="9a773-158">Finally, it decreases the size back to its original value and reinitializes all the array elements.</span></span>  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 <span data-ttu-id="9a773-159">`Dim`Instrukcja tworzy nową tablicę z trzema wymiarami.</span><span class="sxs-lookup"><span data-stu-id="9a773-159">The `Dim` statement creates a new array with three dimensions.</span></span> <span data-ttu-id="9a773-160">Każdy wymiar jest zadeklarowany z granicą 10, więc indeks tablicy dla każdego wymiaru może nastąpić z przedziału od 0 do 10.</span><span class="sxs-lookup"><span data-stu-id="9a773-160">Each dimension is declared with a bound of 10, so the array index for each dimension can range from 0 through 10.</span></span> <span data-ttu-id="9a773-161">W poniższej dyskusji trzy wymiary są określane jako warstwy, wiersze i kolumny.</span><span class="sxs-lookup"><span data-stu-id="9a773-161">In the following discussion, the three dimensions are referred to as layer, row, and column.</span></span>  
  
 <span data-ttu-id="9a773-162">Najpierw `ReDim` tworzy nową tablicę, która zastąpi istniejącą tablicę zmienną `intArray` .</span><span class="sxs-lookup"><span data-stu-id="9a773-162">The first `ReDim` creates a new array which replaces the existing array in variable `intArray`.</span></span> <span data-ttu-id="9a773-163">`ReDim`Kopiuje wszystkie elementy z istniejącej tablicy do nowej tablicy.</span><span class="sxs-lookup"><span data-stu-id="9a773-163">`ReDim` copies all the elements from the existing array into the new array.</span></span> <span data-ttu-id="9a773-164">Dodaje także 10 większej liczby kolumn do końca każdego wiersza w każdej warstwie i inicjuje elementy w tych nowych kolumnach do 0 (wartość domyślna `Integer` , która jest typem elementu tablicy).</span><span class="sxs-lookup"><span data-stu-id="9a773-164">It also adds 10 more columns to the end of every row in every layer and initializes the elements in these new columns to 0 (the default value of `Integer`, which is the element type of the array).</span></span>  
  
 <span data-ttu-id="9a773-165">Druga `ReDim` tworzy kolejną nową tablicę i kopiuje wszystkie elementy, które pasują do siebie.</span><span class="sxs-lookup"><span data-stu-id="9a773-165">The second `ReDim` creates another new array and copies all the elements that fit.</span></span> <span data-ttu-id="9a773-166">Jednak pięć kolumn zostanie utraconych od końca każdego wiersza w każdej warstwie.</span><span class="sxs-lookup"><span data-stu-id="9a773-166">However, five columns are lost from the end of every row in every layer.</span></span> <span data-ttu-id="9a773-167">Nie jest to problem, Jeśli zakończysz korzystanie z tych kolumn.</span><span class="sxs-lookup"><span data-stu-id="9a773-167">This is not a problem if you have finished using these columns.</span></span> <span data-ttu-id="9a773-168">Zmniejszenie rozmiaru dużej tablicy może zwolnić pamięć, która nie jest już potrzebna.</span><span class="sxs-lookup"><span data-stu-id="9a773-168">Reducing the size of a large array can free up memory that you no longer need.</span></span>  
  
 <span data-ttu-id="9a773-169">Trzecia `ReDim` tworzy kolejną nową tablicę i usuwa kolejną pięć kolumn na końcu każdego wiersza w każdej warstwie.</span><span class="sxs-lookup"><span data-stu-id="9a773-169">The third `ReDim` creates another new array and removes another five columns from the end of every row in every layer.</span></span> <span data-ttu-id="9a773-170">Tym razem nie kopiuje żadnych istniejących elementów.</span><span class="sxs-lookup"><span data-stu-id="9a773-170">This time it does not copy any existing elements.</span></span> <span data-ttu-id="9a773-171">Ta instrukcja przywraca pierwotny rozmiar tablicy.</span><span class="sxs-lookup"><span data-stu-id="9a773-171">This statement reverts the array to its original size.</span></span> <span data-ttu-id="9a773-172">Ponieważ instrukcja nie zawiera `Preserve` modyfikatora, ustawia wszystkie elementy tablicy na ich pierwotne wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="9a773-172">Because the statement doesn't include the `Preserve` modifier, it sets all array elements to their original default values.</span></span>  
  
 <span data-ttu-id="9a773-173">Aby uzyskać więcej przykładów, zobacz [tablice](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="9a773-173">For additional examples, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a773-174">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9a773-174">See also</span></span>

- <xref:System.IndexOutOfRangeException>
- [<span data-ttu-id="9a773-175">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9a773-175">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="9a773-176">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9a773-176">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="9a773-177">Erase, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9a773-177">Erase Statement</span></span>](erase-statement.md)
- [<span data-ttu-id="9a773-178">Nothing</span><span class="sxs-lookup"><span data-stu-id="9a773-178">Nothing</span></span>](../nothing.md)
- [<span data-ttu-id="9a773-179">Tablice</span><span class="sxs-lookup"><span data-stu-id="9a773-179">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
