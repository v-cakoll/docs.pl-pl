---
title: Różnice między parametrami i argumentami
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
ms.openlocfilehash: c4249dbf86bd1bfa7ef08e94059d2880333e9a92
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341373"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="a8c3f-102">Różnice pomiędzy parametrami i argumentami (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8c3f-102">Differences Between Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="a8c3f-103">W większości przypadków procedura musi mieć pewne informacje dotyczące okoliczności, w których zostało wywołane.</span><span class="sxs-lookup"><span data-stu-id="a8c3f-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="a8c3f-104">Procedura wykonująca powtarzalne lub udostępnione zadania używa różnych informacji dla każdego wywołania.</span><span class="sxs-lookup"><span data-stu-id="a8c3f-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="a8c3f-105">Te informacje składają się ze zmiennych, stałych i wyrażeń, które są przekazywane do procedury po jej wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="a8c3f-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="a8c3f-106">Aby przekazać te informacje do procedury, procedura definiuje *parametr*, a wywoływany kod przekazuje *argument* do tego parametru.</span><span class="sxs-lookup"><span data-stu-id="a8c3f-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="a8c3f-107">Można traktować parametr jako miejsce parkingowe i argument jako urządzenie przenośne.</span><span class="sxs-lookup"><span data-stu-id="a8c3f-107">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="a8c3f-108">Podobnie jak w przypadku różnych samochodów można zaparkować w miejscu parkingowym w różnych godzinach, kod wywołujący może przekazać inny argument do tego samego parametru przy każdym wywołaniu procedury.</span><span class="sxs-lookup"><span data-stu-id="a8c3f-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="a8c3f-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8c3f-109">Parameters</span></span>  
 <span data-ttu-id="a8c3f-110">*Parametr* reprezentuje wartość, którą procedura oczekuje na przekazanie po wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="a8c3f-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="a8c3f-111">Deklaracja procedury definiuje jej parametry.</span><span class="sxs-lookup"><span data-stu-id="a8c3f-111">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="a8c3f-112">Podczas definiowania `Function` lub `Sub` procedury należy określić *listę parametrów* w nawiasach bezpośrednio po nazwie procedury.</span><span class="sxs-lookup"><span data-stu-id="a8c3f-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="a8c3f-113">Dla każdego parametru należy określić nazwę, typ danych i mechanizm przekazywania ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="a8c3f-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="a8c3f-114">Możesz również wskazać, że parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a8c3f-114">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="a8c3f-115">Oznacza to, że wywoływany kod nie musi przekazać do niego wartości.</span><span class="sxs-lookup"><span data-stu-id="a8c3f-115">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="a8c3f-116">Nazwa każdego parametru służy jako *zmienna lokalna* w procedurze.</span><span class="sxs-lookup"><span data-stu-id="a8c3f-116">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="a8c3f-117">Nazwa parametru jest używana w taki sam sposób, jak w przypadku innych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="a8c3f-117">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="a8c3f-118">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a8c3f-118">Arguments</span></span>  
 <span data-ttu-id="a8c3f-119">*Argument* reprezentuje wartość przekazana do parametru procedury po wywołaniu procedury.</span><span class="sxs-lookup"><span data-stu-id="a8c3f-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="a8c3f-120">Kod wywołujący dostarcza argumenty, gdy wywołuje procedurę.</span><span class="sxs-lookup"><span data-stu-id="a8c3f-120">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="a8c3f-121">Po wywołaniu procedury `Function` lub `Sub`, w nawiasach należy dodać *listę argumentów* bezpośrednio po nazwie procedury.</span><span class="sxs-lookup"><span data-stu-id="a8c3f-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="a8c3f-122">Każdy argument odpowiada parametrowi w tej samej pozycji na liście.</span><span class="sxs-lookup"><span data-stu-id="a8c3f-122">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="a8c3f-123">W przeciwieństwie do definicji parametrów, argumenty nie mają nazw.</span><span class="sxs-lookup"><span data-stu-id="a8c3f-123">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="a8c3f-124">Każdy argument jest wyrażeniem, które może zawierać zero lub więcej zmiennych, stałych i literałów.</span><span class="sxs-lookup"><span data-stu-id="a8c3f-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="a8c3f-125">Typ danych obliczanego wyrażenia powinien zwykle być zgodny z typem danych zdefiniowanym dla odpowiedniego parametru, a w każdym przypadku musi być konwertowany na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="a8c3f-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8c3f-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8c3f-126">See also</span></span>

- [<span data-ttu-id="a8c3f-127">Procedury</span><span class="sxs-lookup"><span data-stu-id="a8c3f-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="a8c3f-128">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="a8c3f-128">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="a8c3f-129">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="a8c3f-129">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="a8c3f-130">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="a8c3f-130">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="a8c3f-131">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="a8c3f-131">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="a8c3f-132">Instrukcje: definiowanie parametru dla procedury</span><span class="sxs-lookup"><span data-stu-id="a8c3f-132">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="a8c3f-133">Instrukcje: przekazywanie argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="a8c3f-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="a8c3f-134">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="a8c3f-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="a8c3f-135">Procedury rekursywne</span><span class="sxs-lookup"><span data-stu-id="a8c3f-135">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="a8c3f-136">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="a8c3f-136">Procedure Overloading</span></span>](./procedure-overloading.md)
