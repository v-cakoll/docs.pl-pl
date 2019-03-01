---
title: Parametry i argumenty procedur (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: f7291d809c754249c155eb9382f3fcd8a63c20c7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972561"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="efa8d-102">Parametry i argumenty procedur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efa8d-102">Procedure Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="efa8d-103">W większości przypadków procedura potrzebuje pewnych informacji o sytuacjach, w których została wywołana.</span><span class="sxs-lookup"><span data-stu-id="efa8d-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="efa8d-104">Procedura, która wykonuje zadania powtórzonych lub udostępnione używa różne informacje dla każdego wywołania.</span><span class="sxs-lookup"><span data-stu-id="efa8d-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="efa8d-105">Ten zawiera zmienne, stałe i wyrażeń, które przekazujesz do procedury, gdy wywołujesz ją.</span><span class="sxs-lookup"><span data-stu-id="efa8d-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="efa8d-106">A *parametr* reprezentuje wartość, która oczekuje procedury, trzeba będzie podać podczas jego wywoływania.</span><span class="sxs-lookup"><span data-stu-id="efa8d-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="efa8d-107">Deklaracja procedury definiuje jego parametrów.</span><span class="sxs-lookup"><span data-stu-id="efa8d-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="efa8d-108">Można zdefiniować procedurę z bez parametrów, jeden parametr lub więcej niż jeden.</span><span class="sxs-lookup"><span data-stu-id="efa8d-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="efa8d-109">Nazywa się częścią definicji procedury, która określa parametry *listy parametrów*.</span><span class="sxs-lookup"><span data-stu-id="efa8d-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="efa8d-110">*Argument* reprezentuje wartość, należy podać parametr procedury po wywołaniu procedury.</span><span class="sxs-lookup"><span data-stu-id="efa8d-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="efa8d-111">Kod wywołujący dostarcza argumentów, gdy wywołuje procedurę.</span><span class="sxs-lookup"><span data-stu-id="efa8d-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="efa8d-112">Część po wywołaniu procedury, która określa argumenty nosi nazwę *listy argumentów*.</span><span class="sxs-lookup"><span data-stu-id="efa8d-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="efa8d-113">Na poniższej ilustracji przedstawiono kodu wywołującego procedurę `safeSquareRoot` w dwóch różnych miejscach.</span><span class="sxs-lookup"><span data-stu-id="efa8d-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="efa8d-114">Pierwsze wywołanie przekazuje wartość zmiennej `x` (4.0) do parametru `number`i wartość zwracana w `root` (2.0) jest przypisany do zmiennej `y`.</span><span class="sxs-lookup"><span data-stu-id="efa8d-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="efa8d-115">Drugie wywołanie przekazuje wartość literału 9.0 do `number`, a następnie przypisuje wartość zwracaną (3.0) do zmiennej `z`.</span><span class="sxs-lookup"><span data-stu-id="efa8d-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 <span data-ttu-id="efa8d-116">![Przekazywanie argumentów do parametrów graficzny diagram](./media/parametersargue.gif "ParametersArgue")</span><span class="sxs-lookup"><span data-stu-id="efa8d-116">![Graphic diagram of passing argument to parameter](./media/parametersargue.gif "ParametersArgue")</span></span>  
<span data-ttu-id="efa8d-117">Przekazywanie argumentu do parametru</span><span class="sxs-lookup"><span data-stu-id="efa8d-117">Passing an argument to a parameter</span></span>  
  
 <span data-ttu-id="efa8d-118">Aby uzyskać więcej informacji, zobacz [różnice pomiędzy parametrami i argumentami](./differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="efa8d-118">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="efa8d-119">Typ danych parametru</span><span class="sxs-lookup"><span data-stu-id="efa8d-119">Parameter Data Type</span></span>  
 <span data-ttu-id="efa8d-120">Zdefiniuj typ danych parametru za pomocą `As` klauzuli w jego deklaracji.</span><span class="sxs-lookup"><span data-stu-id="efa8d-120">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="efa8d-121">Na przykład następująca funkcja akceptuje string i integer.</span><span class="sxs-lookup"><span data-stu-id="efa8d-121">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 <span data-ttu-id="efa8d-122">Jeśli kontrola typów w przełącznik ([Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest `Off,` `As` klauzula jest opcjonalne, z tą różnicą, że wszelkie jeden parametr używa go, wszystkie parametry muszą używać.</span><span class="sxs-lookup"><span data-stu-id="efa8d-122">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="efa8d-123">W przypadku sprawdzania typu `On`, `As` klauzula jest wymagana dla wszystkich parametrów procedury.</span><span class="sxs-lookup"><span data-stu-id="efa8d-123">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="efa8d-124">Jeśli kod wywołujący oczekuje, że takie jak podać argument o typie danych innym niż odpowiadającego mu parametru `Byte` do `String` parametru, wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="efa8d-124">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
-   <span data-ttu-id="efa8d-125">Podaj tylko argumenty z typami danych, które mogą zostać poszerzone do do typu parametru.</span><span class="sxs-lookup"><span data-stu-id="efa8d-125">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
-   <span data-ttu-id="efa8d-126">Ustaw `Option Strict Off` umożliwia niejawne konwersje zawężające; lub</span><span class="sxs-lookup"><span data-stu-id="efa8d-126">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
-   <span data-ttu-id="efa8d-127">Użyj słowa kluczowego konwersji można jawnie przekonwertować na typ danych.</span><span class="sxs-lookup"><span data-stu-id="efa8d-127">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="efa8d-128">Parametry typów</span><span class="sxs-lookup"><span data-stu-id="efa8d-128">Type Parameters</span></span>  
 <span data-ttu-id="efa8d-129">A *ogólna procedura* definiuje także co najmniej jeden *parametry typu* oprócz normalnych parametry.</span><span class="sxs-lookup"><span data-stu-id="efa8d-129">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="efa8d-130">Ogólna procedura pozwala kod wywołujący, aby przekazać zawsze wywołuje procedurę, dzięki czemu można dostosować, typy danych do wymagań poszczególnych wywołań różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="efa8d-130">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="efa8d-131">Zobacz [procedury ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="efa8d-131">See [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efa8d-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efa8d-132">See also</span></span>
- [<span data-ttu-id="efa8d-133">Procedury</span><span class="sxs-lookup"><span data-stu-id="efa8d-133">Procedures</span></span>](./index.md)
- [<span data-ttu-id="efa8d-134">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="efa8d-134">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="efa8d-135">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="efa8d-135">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="efa8d-136">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="efa8d-136">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="efa8d-137">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="efa8d-137">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="efa8d-138">Instrukcje: Definiowanie parametru dla procedury</span><span class="sxs-lookup"><span data-stu-id="efa8d-138">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="efa8d-139">Instrukcje: Przekazywanie argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="efa8d-139">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="efa8d-140">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="efa8d-140">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="efa8d-141">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="efa8d-141">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="efa8d-142">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="efa8d-142">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
