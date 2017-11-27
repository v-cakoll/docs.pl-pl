---
title: Parametry i argumenty procedur (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 726667950cfb227a0359bd6238c202883561749c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="42376-102">Parametry i argumenty procedur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42376-102">Procedure Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="42376-103">W większości przypadków procedury potrzebuje pewnych informacji o okoliczności, w których została wywołana.</span><span class="sxs-lookup"><span data-stu-id="42376-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="42376-104">Procedury, która wykonuje zadania wielokrotnego lub udostępnionego używa różne informacje dla każdego wywołania.</span><span class="sxs-lookup"><span data-stu-id="42376-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="42376-105">Te informacje składa się z zmienne, stałe i wyrażeń, które przekazujesz do procedury po jej wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="42376-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="42376-106">A *parametr* reprezentuje wartość, która procedura oczekuje podania po jej wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="42376-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="42376-107">Deklaracja procedury definiuje jego parametrów.</span><span class="sxs-lookup"><span data-stu-id="42376-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="42376-108">Można zdefiniować procedury z żadnych parametrów, jeden parametr lub więcej niż jeden.</span><span class="sxs-lookup"><span data-stu-id="42376-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="42376-109">Nazywa się częścią definicji procedury, która określa parametry *listy parametrów*.</span><span class="sxs-lookup"><span data-stu-id="42376-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="42376-110">*Argument* reprezentuje należy podać wartość parametru procedury po wywołaniu procedury.</span><span class="sxs-lookup"><span data-stu-id="42376-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="42376-111">Kod wywołujący zawiera argumenty, gdy wywołuje procedurę.</span><span class="sxs-lookup"><span data-stu-id="42376-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="42376-112">Część wywołaniu procedury, która określa argumenty jest nazywany *listy argumentów*.</span><span class="sxs-lookup"><span data-stu-id="42376-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="42376-113">Na poniższej ilustracji przedstawiono wywołującego procedurę `safeSquareRoot` w dwóch różnych miejscach.</span><span class="sxs-lookup"><span data-stu-id="42376-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="42376-114">Pierwsze wywołanie przekazuje wartość zmiennej `x` (4.0) do parametru `number`, a wartość zwracana w `root` (2.0) jest przypisany do zmiennej `y`.</span><span class="sxs-lookup"><span data-stu-id="42376-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="42376-115">Drugie wywołanie przekazuje wartość literału 9.0 do `number`i przypisuje wartość zwrotna (3.0) do zmiennej `z`.</span><span class="sxs-lookup"><span data-stu-id="42376-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 <span data-ttu-id="42376-116">![Przekazywanie argumentów do parametru graficzny diagram](./media/parametersargue.gif "ParametersArgue")</span><span class="sxs-lookup"><span data-stu-id="42376-116">![Graphic diagram of passing argument to parameter](./media/parametersargue.gif "ParametersArgue")</span></span>  
<span data-ttu-id="42376-117">Przekazywanie argumentów do parametru</span><span class="sxs-lookup"><span data-stu-id="42376-117">Passing an argument to a parameter</span></span>  
  
 <span data-ttu-id="42376-118">Aby uzyskać więcej informacji, zobacz [różnice pomiędzy parametrami i argumentami](./differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="42376-118">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="42376-119">Typ danych parametru</span><span class="sxs-lookup"><span data-stu-id="42376-119">Parameter Data Type</span></span>  
 <span data-ttu-id="42376-120">Definiowanie typu danych dla parametru za pomocą `As` klauzuli w jego deklaracji.</span><span class="sxs-lookup"><span data-stu-id="42376-120">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="42376-121">Na przykład następująca funkcja akceptuje string i integer.</span><span class="sxs-lookup"><span data-stu-id="42376-121">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](./codesnippet/VisualBasic/procedure-parameters-and-arguments_1.vb)]  
  
 <span data-ttu-id="42376-122">Jeśli sprawdzanie typu przełącznik ([Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest `Off,` `As` klauzuli jest opcjonalny, z wyjątkiem tego, że wszystkie jeden parametr używa go, wszystkie parametry muszą używać.</span><span class="sxs-lookup"><span data-stu-id="42376-122">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="42376-123">Jeśli sprawdzanie, czy typ jest `On`, `As` klauzula jest wymagana dla wszystkich parametrów procedury.</span><span class="sxs-lookup"><span data-stu-id="42376-123">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="42376-124">Jeśli kod wywołujący oczekuje, że takie jak podać argument o typie danych innym niż odpowiadającego mu parametru `Byte` do `String` parametru, wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="42376-124">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
-   <span data-ttu-id="42376-125">Podaj tylko argumenty typów danych, które poszerzyć na typ danych parametru;</span><span class="sxs-lookup"><span data-stu-id="42376-125">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
-   <span data-ttu-id="42376-126">Ustaw `Option Strict Off` umożliwiają niejawnej konwersji zawężającej; lub</span><span class="sxs-lookup"><span data-stu-id="42376-126">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
-   <span data-ttu-id="42376-127">Użyj słowa kluczowego konwersji, aby jawnie przekonwertować na typ danych.</span><span class="sxs-lookup"><span data-stu-id="42376-127">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="42376-128">Parametry typów</span><span class="sxs-lookup"><span data-stu-id="42376-128">Type Parameters</span></span>  
 <span data-ttu-id="42376-129">A *ogólnego procedury* definiuje także co najmniej jeden *parametry typu* oprócz jego normalnej parametrów.</span><span class="sxs-lookup"><span data-stu-id="42376-129">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="42376-130">Procedury ogólne umożliwia kod wywołujący do przekazania różne typy danych zawsze wywołuje procedurę, więc można dostosować typy danych do każdego wywołania poszczególnych wymagań.</span><span class="sxs-lookup"><span data-stu-id="42376-130">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="42376-131">Zobacz [procedury ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="42376-131">See [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42376-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42376-132">See Also</span></span>  
 [<span data-ttu-id="42376-133">Procedury</span><span class="sxs-lookup"><span data-stu-id="42376-133">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="42376-134">Sub — procedury</span><span class="sxs-lookup"><span data-stu-id="42376-134">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="42376-135">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="42376-135">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="42376-136">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="42376-136">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="42376-137">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="42376-137">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="42376-138">Porady: Definiowanie parametru dla procedury</span><span class="sxs-lookup"><span data-stu-id="42376-138">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)  
 [<span data-ttu-id="42376-139">Porady: przekazywanie argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="42376-139">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="42376-140">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="42376-140">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="42376-141">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="42376-141">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="42376-142">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42376-142">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
