---
title: Różnice pomiędzy parametrami i argumentami (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
ms.openlocfilehash: a69b956c7cffcc2a26916d6fc92f23dd4e2322d7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838979"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="95fe1-102">Różnice pomiędzy parametrami i argumentami (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95fe1-102">Differences Between Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="95fe1-103">W większości przypadków procedura musi mieć pewne informacje o sytuacjach, w których została wywołana.</span><span class="sxs-lookup"><span data-stu-id="95fe1-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="95fe1-104">Procedura, która wykonuje zadania powtórzonych lub udostępnione używa różne informacje dla każdego wywołania.</span><span class="sxs-lookup"><span data-stu-id="95fe1-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="95fe1-105">Ten zawiera zmienne, stałe i wyrażeń, które przekazujesz do procedury, gdy wywołujesz ją.</span><span class="sxs-lookup"><span data-stu-id="95fe1-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="95fe1-106">Do przekazywania tych informacji do procedury, definiuje procedurę *parametru*, i kod wywołujący przekazuje *argument* do tego parametru.</span><span class="sxs-lookup"><span data-stu-id="95fe1-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="95fe1-107">Można traktować jako odstępu parametr i argument jako samochodów.</span><span class="sxs-lookup"><span data-stu-id="95fe1-107">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="95fe1-108">Tak samo, jak różnych samochodów można zrezygnować w odstępu w różnym czasie, kod wywołujący może przekazać innego argumentu do tego samego parametru, za każdym razem, gdy jej wywołuje procedurę.</span><span class="sxs-lookup"><span data-stu-id="95fe1-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="95fe1-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="95fe1-109">Parameters</span></span>  
 <span data-ttu-id="95fe1-110">A *parametr* reprezentuje wartość, która procedura oczekuje przekazania podczas jego wywoływania.</span><span class="sxs-lookup"><span data-stu-id="95fe1-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="95fe1-111">Deklaracja procedury definiuje jego parametrów.</span><span class="sxs-lookup"><span data-stu-id="95fe1-111">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="95fe1-112">Podczas definiowania `Function` lub `Sub` procedury, należy określić *listy parametrów* w nawiasach bezpośrednio po Nazwa procedury.</span><span class="sxs-lookup"><span data-stu-id="95fe1-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="95fe1-113">Dla każdego parametru, należy określić nazwę, typ danych i mechanizm przekazywania ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="95fe1-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="95fe1-114">Można również określić, że parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="95fe1-114">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="95fe1-115">Oznacza to, że kod wywołujący nie ma przekazać wartości.</span><span class="sxs-lookup"><span data-stu-id="95fe1-115">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="95fe1-116">Nazwa każdego parametru służy jako *zmienna lokalna* w procedurze.</span><span class="sxs-lookup"><span data-stu-id="95fe1-116">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="95fe1-117">Użyj nazwy parametru tak samo jak inne zmienne.</span><span class="sxs-lookup"><span data-stu-id="95fe1-117">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="95fe1-118">Argumenty</span><span class="sxs-lookup"><span data-stu-id="95fe1-118">Arguments</span></span>  
 <span data-ttu-id="95fe1-119">*Argument* reprezentuje wartość, którą przekazać do parametru procedury po wywołaniu procedury.</span><span class="sxs-lookup"><span data-stu-id="95fe1-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="95fe1-120">Kod wywołujący dostarcza argumentów, gdy wywołuje procedurę.</span><span class="sxs-lookup"><span data-stu-id="95fe1-120">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="95fe1-121">Gdy wywołujesz `Function` lub `Sub` procedury obejmują *listy argumentów* w nawiasach bezpośrednio po Nazwa procedury.</span><span class="sxs-lookup"><span data-stu-id="95fe1-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="95fe1-122">Każdy argument odnosi się do parametru w tej samej pozycji na liście.</span><span class="sxs-lookup"><span data-stu-id="95fe1-122">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="95fe1-123">W przeciwieństwie do definicji parametru argumentów nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="95fe1-123">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="95fe1-124">Każdy argument jest wyrażenia, które może zawierać zero lub więcej zmiennych, stałych i literały.</span><span class="sxs-lookup"><span data-stu-id="95fe1-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="95fe1-125">Typ danych obliczane wyrażenie zazwyczaj powinna być zgodna z typem danych zdefiniowanym dla odpowiedniego parametru, a w każdym przypadku musi być konwertowany na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="95fe1-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95fe1-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95fe1-126">See also</span></span>

- [<span data-ttu-id="95fe1-127">Procedury</span><span class="sxs-lookup"><span data-stu-id="95fe1-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="95fe1-128">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="95fe1-128">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="95fe1-129">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="95fe1-129">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="95fe1-130">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="95fe1-130">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="95fe1-131">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="95fe1-131">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="95fe1-132">Instrukcje: Definiowanie parametru dla procedury</span><span class="sxs-lookup"><span data-stu-id="95fe1-132">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="95fe1-133">Instrukcje: Przekazywanie argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="95fe1-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="95fe1-134">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="95fe1-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="95fe1-135">Procedury rekursywne</span><span class="sxs-lookup"><span data-stu-id="95fe1-135">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="95fe1-136">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="95fe1-136">Procedure Overloading</span></span>](./procedure-overloading.md)
