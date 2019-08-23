---
title: Parameter — Tablice (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: 5a2813b81490e7c2fcf1abcf5fd36ca89d9d7929
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933858"
---
# <a name="parameter-arrays-visual-basic"></a><span data-ttu-id="be74c-102">Parameter — Tablice (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be74c-102">Parameter Arrays (Visual Basic)</span></span>
<span data-ttu-id="be74c-103">Zazwyczaj nie można wywołać procedury z więcej argumentów niż Deklaracja procedury.</span><span class="sxs-lookup"><span data-stu-id="be74c-103">Usually, you cannot call a procedure with more arguments than the procedure declaration specifies.</span></span> <span data-ttu-id="be74c-104">Jeśli potrzebujesz nieograniczonej liczby argumentów, możesz zadeklarować *tablicę parametrów*, która umożliwia procedurę akceptowania tablicy wartości dla parametru.</span><span class="sxs-lookup"><span data-stu-id="be74c-104">When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter.</span></span> <span data-ttu-id="be74c-105">Podczas definiowania procedury nie trzeba znać liczby elementów w tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="be74c-105">You do not have to know the number of elements in the parameter array when you define the procedure.</span></span> <span data-ttu-id="be74c-106">Rozmiar tablicy jest określany indywidualnie przez każde wywołanie procedury.</span><span class="sxs-lookup"><span data-stu-id="be74c-106">The array size is determined individually by each call to the procedure.</span></span>  
  
## <a name="declaring-a-paramarray"></a><span data-ttu-id="be74c-107">Deklarowanie ParamArray</span><span class="sxs-lookup"><span data-stu-id="be74c-107">Declaring a ParamArray</span></span>  
 <span data-ttu-id="be74c-108">Za pomocą słowa kluczowego [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) można zauważyć tablicę parametrów na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="be74c-108">You use the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list.</span></span> <span data-ttu-id="be74c-109">Mają zastosowanie następujące zasady:</span><span class="sxs-lookup"><span data-stu-id="be74c-109">The following rules apply:</span></span>  
  
- <span data-ttu-id="be74c-110">Procedura może definiować tylko jedną tablicę parametrów i musi być ostatnim parametrem w definicji procedury.</span><span class="sxs-lookup"><span data-stu-id="be74c-110">A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.</span></span>  
  
- <span data-ttu-id="be74c-111">Tablica parametrów musi być przenoszona przez wartość.</span><span class="sxs-lookup"><span data-stu-id="be74c-111">The parameter array must be passed by value.</span></span> <span data-ttu-id="be74c-112">Dobrym sposobem programowania jest jawne dołączenie słowa kluczowego [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) w definicji procedury.</span><span class="sxs-lookup"><span data-stu-id="be74c-112">It is good programming practice to explicitly include the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword in the procedure definition.</span></span>  
  
- <span data-ttu-id="be74c-113">Tablica parametrów jest automatycznie opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="be74c-113">The parameter array is automatically optional.</span></span> <span data-ttu-id="be74c-114">Jego wartość domyślna to pusta Jednowymiarowa tablica typu elementu tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="be74c-114">Its default value is an empty one-dimensional array of the parameter array's element type.</span></span>  
  
- <span data-ttu-id="be74c-115">Wszystkie parametry poprzedzające tablicę parametrów muszą być wymagane.</span><span class="sxs-lookup"><span data-stu-id="be74c-115">All parameters preceding the parameter array must be required.</span></span> <span data-ttu-id="be74c-116">Tablica parametrów musi być jedynym opcjonalnym parametrem.</span><span class="sxs-lookup"><span data-stu-id="be74c-116">The parameter array must be the only optional parameter.</span></span>  
  
## <a name="calling-a-paramarray"></a><span data-ttu-id="be74c-117">Wywoływanie ParamArray</span><span class="sxs-lookup"><span data-stu-id="be74c-117">Calling a ParamArray</span></span>  
 <span data-ttu-id="be74c-118">Po wywołaniu procedury, która definiuje tablicę parametrów, można podać argument w jednym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="be74c-118">When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:</span></span>  
  
- <span data-ttu-id="be74c-119">Nic — to znaczy, że można pominąć argument [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) .</span><span class="sxs-lookup"><span data-stu-id="be74c-119">Nothing — that is, you can omit the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument.</span></span> <span data-ttu-id="be74c-120">W takim przypadku pusta tablica jest przenoszona do procedury.</span><span class="sxs-lookup"><span data-stu-id="be74c-120">In this case, an empty array is passed to the procedure.</span></span> <span data-ttu-id="be74c-121">Możesz również przekazać słowo kluczowe [Nothing](../../../../visual-basic/language-reference/nothing.md) bez tego samego efektu.</span><span class="sxs-lookup"><span data-stu-id="be74c-121">You can also pass the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, with the same effect.</span></span>  
  
- <span data-ttu-id="be74c-122">Lista dowolnej liczby argumentów oddzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="be74c-122">A list of an arbitrary number of arguments, separated by commas.</span></span> <span data-ttu-id="be74c-123">Typ danych każdego argumentu musi być niejawnie konwertowany na `ParamArray` typ elementu.</span><span class="sxs-lookup"><span data-stu-id="be74c-123">The data type of each argument must be implicitly convertible to the `ParamArray` element type.</span></span>  
  
- <span data-ttu-id="be74c-124">Tablica z tym samym typem elementu co typ elementu tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="be74c-124">An array with the same element type as the parameter array's element type.</span></span>  
  
 <span data-ttu-id="be74c-125">We wszystkich przypadkach kod w procedurze traktuje tablicę parametrów jako tablicę jednowymiarową z elementami tego samego typu danych co `ParamArray` typ danych.</span><span class="sxs-lookup"><span data-stu-id="be74c-125">In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="be74c-126">Za każdym razem, gdy zajmujesz się tablicą, która może być nienieskończona, istnieje ryzyko, że zachodzi taka Wewnętrzna pojemność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="be74c-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="be74c-127">Jeśli zaakceptujesz tablicę parametrów, należy sprawdzić rozmiar tablicy, do której przeszedł kod wywołujący.</span><span class="sxs-lookup"><span data-stu-id="be74c-127">If you accept a parameter array, you should test for the size of the array that the calling code passed to it.</span></span> <span data-ttu-id="be74c-128">Wykonaj odpowiednie kroki, jeśli są zbyt duże dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="be74c-128">Take appropriate steps if it is too large for your application.</span></span> <span data-ttu-id="be74c-129">Aby uzyskać więcej informacji, zobacz [tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="be74c-129">For more information, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="be74c-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="be74c-130">Example</span></span>  
 <span data-ttu-id="be74c-131">Poniższy przykład definiuje i wywołuje funkcję `calcSum`.</span><span class="sxs-lookup"><span data-stu-id="be74c-131">The following example defines and calls the function `calcSum`.</span></span> <span data-ttu-id="be74c-132">Modyfikator dla parametru `args` umożliwia funkcji akceptującej zmienną liczbę argumentów. `ParamArray`</span><span class="sxs-lookup"><span data-stu-id="be74c-132">The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 <span data-ttu-id="be74c-133">Poniższy przykład definiuje procedurę z tablicą parametrów i wyprowadza wartości wszystkich elementów tablicy przekazaną do tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="be74c-133">The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.</span></span>  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a><span data-ttu-id="be74c-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be74c-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="be74c-135">Procedury</span><span class="sxs-lookup"><span data-stu-id="be74c-135">Procedures</span></span>](./index.md)
- [<span data-ttu-id="be74c-136">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="be74c-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="be74c-137">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="be74c-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="be74c-138">Przekazywanie argumentów według pozycji i według nazwy</span><span class="sxs-lookup"><span data-stu-id="be74c-138">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="be74c-139">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="be74c-139">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="be74c-140">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="be74c-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="be74c-141">Tablice</span><span class="sxs-lookup"><span data-stu-id="be74c-141">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="be74c-142">Optional</span><span class="sxs-lookup"><span data-stu-id="be74c-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
