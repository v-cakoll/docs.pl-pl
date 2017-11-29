---
title: "Parameter — Tablice (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8ca2b5f02ac4fb3eb613488c8a9852eb2aa4ce5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="parameter-arrays-visual-basic"></a><span data-ttu-id="1f55c-102">Parameter — Tablice (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f55c-102">Parameter Arrays (Visual Basic)</span></span>
<span data-ttu-id="1f55c-103">Zazwyczaj nie można wywołać procedury z więcej argumentów niż określa deklaracji procedury.</span><span class="sxs-lookup"><span data-stu-id="1f55c-103">Usually, you cannot call a procedure with more arguments than the procedure declaration specifies.</span></span> <span data-ttu-id="1f55c-104">Jeśli potrzebujesz nieokreśloną liczbę argumentów można zadeklarować *tablicy parametrów*, dzięki czemu procedury zaakceptować tablicy wartości parametru.</span><span class="sxs-lookup"><span data-stu-id="1f55c-104">When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter.</span></span> <span data-ttu-id="1f55c-105">Nie trzeba znać liczba elementów w tablicy parametrów podczas definiowania procedury.</span><span class="sxs-lookup"><span data-stu-id="1f55c-105">You do not have to know the number of elements in the parameter array when you define the procedure.</span></span> <span data-ttu-id="1f55c-106">Rozmiar tablicy jest ustalana indywidualnie przy każdym wywołaniu procedury.</span><span class="sxs-lookup"><span data-stu-id="1f55c-106">The array size is determined individually by each call to the procedure.</span></span>  
  
## <a name="declaring-a-paramarray"></a><span data-ttu-id="1f55c-107">Deklarowanie ParamArray</span><span class="sxs-lookup"><span data-stu-id="1f55c-107">Declaring a ParamArray</span></span>  
 <span data-ttu-id="1f55c-108">Możesz użyć [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) — słowo kluczowe do oznaczania tablicy parametrów na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="1f55c-108">You use the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list.</span></span> <span data-ttu-id="1f55c-109">Mają zastosowanie następujące zasady:</span><span class="sxs-lookup"><span data-stu-id="1f55c-109">The following rules apply:</span></span>  
  
-   <span data-ttu-id="1f55c-110">Procedurę można zdefiniować tylko jedną tablicy parametrów, a musi być ostatnim parametrem Definicja procedury.</span><span class="sxs-lookup"><span data-stu-id="1f55c-110">A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.</span></span>  
  
-   <span data-ttu-id="1f55c-111">Tablica parametrów muszą być przekazywane przez wartość.</span><span class="sxs-lookup"><span data-stu-id="1f55c-111">The parameter array must be passed by value.</span></span> <span data-ttu-id="1f55c-112">Jest dobrą praktyką jawnie włączyć programowania [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) — słowo kluczowe w definicji procedury.</span><span class="sxs-lookup"><span data-stu-id="1f55c-112">It is good programming practice to explicitly include the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword in the procedure definition.</span></span>  
  
-   <span data-ttu-id="1f55c-113">Tablica parametrów jest automatycznie opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="1f55c-113">The parameter array is automatically optional.</span></span> <span data-ttu-id="1f55c-114">Wartość domyślną jest pusta tablica jednowymiarowa typ elementu tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="1f55c-114">Its default value is an empty one-dimensional array of the parameter array's element type.</span></span>  
  
-   <span data-ttu-id="1f55c-115">Wszystkie parametry poprzedzających Tablica parametrów musi być wymagane.</span><span class="sxs-lookup"><span data-stu-id="1f55c-115">All parameters preceding the parameter array must be required.</span></span> <span data-ttu-id="1f55c-116">Tablica parametrów musi być tylko opcjonalny parametr.</span><span class="sxs-lookup"><span data-stu-id="1f55c-116">The parameter array must be the only optional parameter.</span></span>  
  
## <a name="calling-a-paramarray"></a><span data-ttu-id="1f55c-117">Wywoływanie ParamArray</span><span class="sxs-lookup"><span data-stu-id="1f55c-117">Calling a ParamArray</span></span>  
 <span data-ttu-id="1f55c-118">Po wywołaniu procedury, która definiuje tablicy parametrów, możesz podać argument w jednym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="1f55c-118">When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:</span></span>  
  
-   <span data-ttu-id="1f55c-119">Nothing — to znaczy, można pominąć [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argumentu.</span><span class="sxs-lookup"><span data-stu-id="1f55c-119">Nothing — that is, you can omit the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument.</span></span> <span data-ttu-id="1f55c-120">W takim przypadku pusta tablica jest przekazywany do procedury.</span><span class="sxs-lookup"><span data-stu-id="1f55c-120">In this case, an empty array is passed to the procedure.</span></span> <span data-ttu-id="1f55c-121">Można również przekazać [nic](../../../../visual-basic/language-reference/nothing.md) — słowo kluczowe, w tym samym celu.</span><span class="sxs-lookup"><span data-stu-id="1f55c-121">You can also pass the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, with the same effect.</span></span>  
  
-   <span data-ttu-id="1f55c-122">Lista dowolnej liczby argumentów rozdzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="1f55c-122">A list of an arbitrary number of arguments, separated by commas.</span></span> <span data-ttu-id="1f55c-123">Należy umożliwiają niejawnej konwersji na typ danych argumentu `ParamArray` typ elementu.</span><span class="sxs-lookup"><span data-stu-id="1f55c-123">The data type of each argument must be implicitly convertible to the `ParamArray` element type.</span></span>  
  
-   <span data-ttu-id="1f55c-124">Tablica z tego samego typu elementu jako typ elementu tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="1f55c-124">An array with the same element type as the parameter array's element type.</span></span>  
  
 <span data-ttu-id="1f55c-125">We wszystkich przypadkach kodu w ramach procedury traktuje tablicy parametrów jako tablicą jednowymiarową z elementami typu danych jako `ParamArray` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="1f55c-125">In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1f55c-126">Zawsze, gdy praca z tablicy, która może być duży czas nieokreślony, istnieje ryzyko przekroczenia niektórych wewnętrzny wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1f55c-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="1f55c-127">Jeśli akceptujesz tablicy parametrów, należy przetestować rozmiaru tablicy, która kod wywołujący przekazana do niej.</span><span class="sxs-lookup"><span data-stu-id="1f55c-127">If you accept a parameter array, you should test for the size of the array that the calling code passed to it.</span></span> <span data-ttu-id="1f55c-128">Jeśli jest ona za duża dla aplikacji, należy podjąć odpowiednie kroki.</span><span class="sxs-lookup"><span data-stu-id="1f55c-128">Take appropriate steps if it is too large for your application.</span></span> <span data-ttu-id="1f55c-129">Aby uzyskać więcej informacji, zobacz [tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="1f55c-129">For more information, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f55c-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="1f55c-130">Example</span></span>  
 <span data-ttu-id="1f55c-131">W poniższym przykładzie definiuje i wywołuje funkcję `calcSum`.</span><span class="sxs-lookup"><span data-stu-id="1f55c-131">The following example defines and calls the function `calcSum`.</span></span> <span data-ttu-id="1f55c-132">`ParamArray` Modyfikator parametru `args` włącza funkcję zaakceptować zmienną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="1f55c-132">The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](../../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-arrays_1.vb)]  
  
 <span data-ttu-id="1f55c-133">Poniższy przykład definiuje procedurę z tablicą parametrów, a następnie generuje wartości elementów tablicy przekazany do tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="1f55c-133">The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.</span></span>  
  
 [!code-vb[VbVbcnProcedures#48](./codesnippet/VisualBasic/parameter-arrays_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#49](./codesnippet/VisualBasic/parameter-arrays_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1f55c-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f55c-134">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [<span data-ttu-id="1f55c-135">Procedury</span><span class="sxs-lookup"><span data-stu-id="1f55c-135">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="1f55c-136">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="1f55c-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="1f55c-137">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="1f55c-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="1f55c-138">Przekazywanie argumentów według pozycji i według nazwy</span><span class="sxs-lookup"><span data-stu-id="1f55c-138">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="1f55c-139">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="1f55c-139">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="1f55c-140">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="1f55c-140">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="1f55c-141">Tablice</span><span class="sxs-lookup"><span data-stu-id="1f55c-141">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="1f55c-142">Opcjonalne</span><span class="sxs-lookup"><span data-stu-id="1f55c-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
