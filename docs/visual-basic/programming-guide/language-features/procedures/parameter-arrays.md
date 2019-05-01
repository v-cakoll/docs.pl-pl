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
ms.openlocfilehash: 8ea4c77056701b8f61c1ed5a53cf20d98ae913bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791954"
---
# <a name="parameter-arrays-visual-basic"></a><span data-ttu-id="69ca6-102">Parameter — Tablice (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69ca6-102">Parameter Arrays (Visual Basic)</span></span>
<span data-ttu-id="69ca6-103">Zwykle nie można wywołać procedury z więcej argumentów niż określa deklaracja procedury.</span><span class="sxs-lookup"><span data-stu-id="69ca6-103">Usually, you cannot call a procedure with more arguments than the procedure declaration specifies.</span></span> <span data-ttu-id="69ca6-104">Jeśli potrzebujesz nieokreśloną liczbę argumentów, można zadeklarować *tablicy parametrów*, co pozwala procedurę, aby zaakceptować tablicy wartości parametru.</span><span class="sxs-lookup"><span data-stu-id="69ca6-104">When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter.</span></span> <span data-ttu-id="69ca6-105">Nie trzeba znać liczbę elementów w tablicy parametrów podczas definiowania procedury.</span><span class="sxs-lookup"><span data-stu-id="69ca6-105">You do not have to know the number of elements in the parameter array when you define the procedure.</span></span> <span data-ttu-id="69ca6-106">Rozmiar tablicy jest określana indywidualnie przy każdym wywołaniu procedury.</span><span class="sxs-lookup"><span data-stu-id="69ca6-106">The array size is determined individually by each call to the procedure.</span></span>  
  
## <a name="declaring-a-paramarray"></a><span data-ttu-id="69ca6-107">Deklarowanie ParamArray</span><span class="sxs-lookup"><span data-stu-id="69ca6-107">Declaring a ParamArray</span></span>  
 <span data-ttu-id="69ca6-108">Możesz użyć [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) — słowo kluczowe do oznaczania tablicy parametrów na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="69ca6-108">You use the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list.</span></span> <span data-ttu-id="69ca6-109">Mają zastosowanie następujące zasady:</span><span class="sxs-lookup"><span data-stu-id="69ca6-109">The following rules apply:</span></span>  
  
- <span data-ttu-id="69ca6-110">Procedurę można zdefiniować tylko jedna Tablica parametrów i musi być ostatnim parametrem w definicji procedury.</span><span class="sxs-lookup"><span data-stu-id="69ca6-110">A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.</span></span>  
  
- <span data-ttu-id="69ca6-111">Tablica parametrów musi być przekazywany przez wartość.</span><span class="sxs-lookup"><span data-stu-id="69ca6-111">The parameter array must be passed by value.</span></span> <span data-ttu-id="69ca6-112">Jest dobrą praktyką, aby jawnie dołączyć znak programowania [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) — słowo kluczowe w definicji procedury.</span><span class="sxs-lookup"><span data-stu-id="69ca6-112">It is good programming practice to explicitly include the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword in the procedure definition.</span></span>  
  
- <span data-ttu-id="69ca6-113">Tablica parametrów jest automatycznie opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="69ca6-113">The parameter array is automatically optional.</span></span> <span data-ttu-id="69ca6-114">Jego wartość domyślna to puste Jednowymiarowa tablica typu elementu tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="69ca6-114">Its default value is an empty one-dimensional array of the parameter array's element type.</span></span>  
  
- <span data-ttu-id="69ca6-115">Wszystkie parametry z poprzednich tablicy parametrów musi być wymagane.</span><span class="sxs-lookup"><span data-stu-id="69ca6-115">All parameters preceding the parameter array must be required.</span></span> <span data-ttu-id="69ca6-116">Tablica parametrów musi być tylko opcjonalny parametr.</span><span class="sxs-lookup"><span data-stu-id="69ca6-116">The parameter array must be the only optional parameter.</span></span>  
  
## <a name="calling-a-paramarray"></a><span data-ttu-id="69ca6-117">Wywoływanie ParamArray</span><span class="sxs-lookup"><span data-stu-id="69ca6-117">Calling a ParamArray</span></span>  
 <span data-ttu-id="69ca6-118">Po wywołaniu procedury, która definiuje tablicy parametrów, należy podać argument w jednym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="69ca6-118">When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:</span></span>  
  
- <span data-ttu-id="69ca6-119">Nothing — oznacza to, możesz pominąć [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argumentu.</span><span class="sxs-lookup"><span data-stu-id="69ca6-119">Nothing — that is, you can omit the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument.</span></span> <span data-ttu-id="69ca6-120">W tym przypadku pusta tablica jest przekazywany do procedury.</span><span class="sxs-lookup"><span data-stu-id="69ca6-120">In this case, an empty array is passed to the procedure.</span></span> <span data-ttu-id="69ca6-121">Można również przekazać [nic](../../../../visual-basic/language-reference/nothing.md) — słowo kluczowe, w tym samym celu.</span><span class="sxs-lookup"><span data-stu-id="69ca6-121">You can also pass the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, with the same effect.</span></span>  
  
- <span data-ttu-id="69ca6-122">Lista dowolną liczbę argumentów, oddzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="69ca6-122">A list of an arbitrary number of arguments, separated by commas.</span></span> <span data-ttu-id="69ca6-123">Typ danych każdego argumentu musi być niejawnie konwertowane na `ParamArray` typ elementu.</span><span class="sxs-lookup"><span data-stu-id="69ca6-123">The data type of each argument must be implicitly convertible to the `ParamArray` element type.</span></span>  
  
- <span data-ttu-id="69ca6-124">Tablica z tego samego typu elementu jako typ elementu tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="69ca6-124">An array with the same element type as the parameter array's element type.</span></span>  
  
 <span data-ttu-id="69ca6-125">We wszystkich przypadkach kodu w ramach procedury traktuje tablicy parametrów jako tablicę jednowymiarową za pomocą elementów tego samego typu danych, co `ParamArray` typu danych.</span><span class="sxs-lookup"><span data-stu-id="69ca6-125">In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="69ca6-126">Zawsze, gdy użytkownik poradzić sobie z tablicy, które mogą być duże przez czas nieokreślony, istnieje ryzyko przekroczenia niektórych wewnętrznych wydajności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="69ca6-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="69ca6-127">Jeśli zdecydujesz się zaakceptować tablicy parametrów, należy sprawdzić rozmiar tablicy, która przekazany kod wywołujący.</span><span class="sxs-lookup"><span data-stu-id="69ca6-127">If you accept a parameter array, you should test for the size of the array that the calling code passed to it.</span></span> <span data-ttu-id="69ca6-128">Wykonaj kroki odpowiednie, jeśli jest zbyt duży dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="69ca6-128">Take appropriate steps if it is too large for your application.</span></span> <span data-ttu-id="69ca6-129">Aby uzyskać więcej informacji, zobacz [tablic](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="69ca6-129">For more information, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="69ca6-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="69ca6-130">Example</span></span>  
 <span data-ttu-id="69ca6-131">Poniższy przykład definiuje i wywołuje funkcję `calcSum`.</span><span class="sxs-lookup"><span data-stu-id="69ca6-131">The following example defines and calls the function `calcSum`.</span></span> <span data-ttu-id="69ca6-132">`ParamArray` Modyfikator parametru `args` włącza funkcję zaakceptować zmienną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="69ca6-132">The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 <span data-ttu-id="69ca6-133">Poniższy przykład definiuje procedurę z tablicą parametrów i wyświetla wartości wszystkie elementy tablicy przekazane do tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="69ca6-133">The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.</span></span>  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a><span data-ttu-id="69ca6-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69ca6-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="69ca6-135">Procedury</span><span class="sxs-lookup"><span data-stu-id="69ca6-135">Procedures</span></span>](./index.md)
- [<span data-ttu-id="69ca6-136">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="69ca6-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="69ca6-137">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="69ca6-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="69ca6-138">Przekazywanie argumentów według pozycji i według nazwy</span><span class="sxs-lookup"><span data-stu-id="69ca6-138">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="69ca6-139">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="69ca6-139">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="69ca6-140">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="69ca6-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="69ca6-141">Tablice</span><span class="sxs-lookup"><span data-stu-id="69ca6-141">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="69ca6-142">Optional</span><span class="sxs-lookup"><span data-stu-id="69ca6-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
