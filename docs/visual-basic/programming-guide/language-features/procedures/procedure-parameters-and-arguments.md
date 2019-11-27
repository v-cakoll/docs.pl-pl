---
title: Parametry i argumenty procedur
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
ms.openlocfilehash: 7dfbbcb39cf7bb05c8a62a7a252e425f287c9a09
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352581"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="bc3f9-102">Parametry i argumenty procedur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc3f9-102">Procedure Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="bc3f9-103">W większości przypadków procedura wymaga pewnych informacji na temat okoliczności, w których został wywołany.</span><span class="sxs-lookup"><span data-stu-id="bc3f9-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="bc3f9-104">Procedura wykonująca powtarzalne lub udostępnione zadania używa różnych informacji dla każdego wywołania.</span><span class="sxs-lookup"><span data-stu-id="bc3f9-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="bc3f9-105">Te informacje składają się ze zmiennych, stałych i wyrażeń, które są przekazywane do procedury po jej wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="bc3f9-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="bc3f9-106">*Parametr* reprezentuje wartość, którą procedura oczekuje na dostarczenie podczas jego wywoływania.</span><span class="sxs-lookup"><span data-stu-id="bc3f9-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="bc3f9-107">Deklaracja procedury definiuje jej parametry.</span><span class="sxs-lookup"><span data-stu-id="bc3f9-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="bc3f9-108">Można zdefiniować procedurę bez parametrów, jednego parametru lub więcej niż jeden.</span><span class="sxs-lookup"><span data-stu-id="bc3f9-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="bc3f9-109">Część definicji procedury, która określa parametry jest nazywana *listą parametrów*.</span><span class="sxs-lookup"><span data-stu-id="bc3f9-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="bc3f9-110">*Argument* reprezentuje wartość dostarczaną do parametru procedury po wywołaniu procedury.</span><span class="sxs-lookup"><span data-stu-id="bc3f9-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="bc3f9-111">Kod wywołujący dostarcza argumenty, gdy wywołuje procedurę.</span><span class="sxs-lookup"><span data-stu-id="bc3f9-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="bc3f9-112">Część wywołania procedury, która określa argumenty jest nazywana *listą argumentów*.</span><span class="sxs-lookup"><span data-stu-id="bc3f9-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="bc3f9-113">Poniższa ilustracja przedstawia kod wywołujący procedurę `safeSquareRoot` z dwóch różnych miejsc.</span><span class="sxs-lookup"><span data-stu-id="bc3f9-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="bc3f9-114">Pierwsze wywołanie przekazuje wartość zmiennej `x` (4,0) do `number`parametru, a wartość zwracana w `root` (2,0) jest przypisana do zmiennej `y`.</span><span class="sxs-lookup"><span data-stu-id="bc3f9-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="bc3f9-115">Drugie wywołanie przekazuje wartość literału 9,0 do `number`i przypisuje wartość zwracaną (3,0) do zmiennej `z`.</span><span class="sxs-lookup"><span data-stu-id="bc3f9-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 ![Diagram, który pokazuje przekazywanie argumentu do parametru](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 <span data-ttu-id="bc3f9-117">Aby uzyskać więcej informacji, zobacz [różnice między parametrami i argumentami](./differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="bc3f9-117">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="bc3f9-118">Typ danych parametru</span><span class="sxs-lookup"><span data-stu-id="bc3f9-118">Parameter Data Type</span></span>  
 <span data-ttu-id="bc3f9-119">Zdefiniowano typ danych dla parametru za pomocą klauzuli `As` w swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="bc3f9-119">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="bc3f9-120">Na przykład następująca funkcja akceptuje ciąg i liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="bc3f9-120">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 <span data-ttu-id="bc3f9-121">Jeśli przełącznik sprawdzania typu ([instrukcja Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest `Off,` klauzula `As` jest opcjonalna, z tą różnicą, że jeśli którykolwiek z nich używa tego parametru, wszystkie parametry muszą go używać.</span><span class="sxs-lookup"><span data-stu-id="bc3f9-121">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="bc3f9-122">Jeśli sprawdzanie typu jest `On`, klauzula `As` jest wymagana dla wszystkich parametrów procedury.</span><span class="sxs-lookup"><span data-stu-id="bc3f9-122">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="bc3f9-123">Jeśli kod wywołujący oczekuje argumentu z typem danych innym niż odpowiedni parametr, taki jak `Byte` do parametru `String`, musi wykonać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="bc3f9-123">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
- <span data-ttu-id="bc3f9-124">Dostarczaj tylko argumenty z typami danych, które rozszerzają się do typu danych parametru;</span><span class="sxs-lookup"><span data-stu-id="bc3f9-124">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
- <span data-ttu-id="bc3f9-125">Ustaw `Option Strict Off`, aby zezwalać na niejawne konwersje zawężające; oraz</span><span class="sxs-lookup"><span data-stu-id="bc3f9-125">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
- <span data-ttu-id="bc3f9-126">Użyj słowa kluczowego konwersji, aby jawnie skonwertować typ danych.</span><span class="sxs-lookup"><span data-stu-id="bc3f9-126">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="bc3f9-127">Parametry typów</span><span class="sxs-lookup"><span data-stu-id="bc3f9-127">Type Parameters</span></span>  
 <span data-ttu-id="bc3f9-128">*Procedura ogólna* definiuje także jeden lub więcej *parametrów typu* oprócz zwykłych parametrów.</span><span class="sxs-lookup"><span data-stu-id="bc3f9-128">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="bc3f9-129">Procedura ogólna pozwala wywołującemu kod przekazać różne typy danych przy każdym wywołaniu procedury, tak aby można było dostosować typy danych do wymagań poszczególnych wywołań.</span><span class="sxs-lookup"><span data-stu-id="bc3f9-129">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="bc3f9-130">Zapoznaj [się z procedurami ogólnymi w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="bc3f9-130">See [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc3f9-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc3f9-131">See also</span></span>

- [<span data-ttu-id="bc3f9-132">Procedury</span><span class="sxs-lookup"><span data-stu-id="bc3f9-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="bc3f9-133">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="bc3f9-133">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="bc3f9-134">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="bc3f9-134">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="bc3f9-135">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="bc3f9-135">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="bc3f9-136">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="bc3f9-136">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="bc3f9-137">Instrukcje: definiowanie parametru dla procedury</span><span class="sxs-lookup"><span data-stu-id="bc3f9-137">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="bc3f9-138">Instrukcje: przekazywanie argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="bc3f9-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="bc3f9-139">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="bc3f9-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="bc3f9-140">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="bc3f9-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="bc3f9-141">Konwersje typów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bc3f9-141">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
