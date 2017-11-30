---
title: "Różnice pomiędzy parametrami i argumentami (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6613c64a24ef18239422b69f8b5320eadc95b92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="dd97b-102">Różnice pomiędzy parametrami i argumentami (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd97b-102">Differences Between Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="dd97b-103">W większości przypadków procedury musi mieć niektóre informacje na temat sytuacji, w których została wywołana.</span><span class="sxs-lookup"><span data-stu-id="dd97b-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="dd97b-104">Procedury, która wykonuje zadania wielokrotnego lub udostępnionego używa różne informacje dla każdego wywołania.</span><span class="sxs-lookup"><span data-stu-id="dd97b-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="dd97b-105">Te informacje składa się z zmienne, stałe i wyrażeń, które przekazujesz do procedury po jej wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="dd97b-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="dd97b-106">Do przekazywania tych informacji do procedury, definiuje procedurę *parametru*, i przekazuje kod wywołujący *argument* do tego parametru.</span><span class="sxs-lookup"><span data-stu-id="dd97b-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="dd97b-107">Można traktować jako odstępu parametr i argument jako samochodów.</span><span class="sxs-lookup"><span data-stu-id="dd97b-107">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="dd97b-108">Tak samo, jak różnych samochodów można zrezygnować w odstępu w różnym czasie, kod wywołujący może przekazać inny argument do tego samego parametru za każdym razem, gdy jego wywołuje procedurę.</span><span class="sxs-lookup"><span data-stu-id="dd97b-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="dd97b-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd97b-109">Parameters</span></span>  
 <span data-ttu-id="dd97b-110">A *parametr* reprezentuje wartość, która procedura oczekuje po jej wywołać.</span><span class="sxs-lookup"><span data-stu-id="dd97b-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="dd97b-111">Deklaracja procedury definiuje jego parametrów.</span><span class="sxs-lookup"><span data-stu-id="dd97b-111">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="dd97b-112">Podczas definiowania `Function` lub `Sub` procedury, możesz określić *listy parametrów* w nawiasach bezpośrednio po nazwie procedury.</span><span class="sxs-lookup"><span data-stu-id="dd97b-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="dd97b-113">Dla każdego parametru należy określić nazwę, typ danych i mechanizm przekazywania ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="dd97b-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="dd97b-114">Można również określić, że parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="dd97b-114">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="dd97b-115">Oznacza to, że kod wywołujący nie ma przekazać wartość jego.</span><span class="sxs-lookup"><span data-stu-id="dd97b-115">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="dd97b-116">Nazwa każdego parametru służy jako *zmiennej lokalnej* w procedurze.</span><span class="sxs-lookup"><span data-stu-id="dd97b-116">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="dd97b-117">Użyj nazwy parametru tak samo jak inne zmiennej.</span><span class="sxs-lookup"><span data-stu-id="dd97b-117">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="dd97b-118">Argumenty</span><span class="sxs-lookup"><span data-stu-id="dd97b-118">Arguments</span></span>  
 <span data-ttu-id="dd97b-119">*Argument* reprezentuje wartość, który jest przekazywany do parametru procedury wywołania tej procedury.</span><span class="sxs-lookup"><span data-stu-id="dd97b-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="dd97b-120">Kod wywołujący zawiera argumenty, gdy wywołuje procedurę.</span><span class="sxs-lookup"><span data-stu-id="dd97b-120">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="dd97b-121">Podczas wywoływania `Function` lub `Sub` procedury obejmują *listy argumentów* w nawiasach bezpośrednio po nazwie procedury.</span><span class="sxs-lookup"><span data-stu-id="dd97b-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="dd97b-122">Każdy argument odnosi się do parametru w tej samej pozycji w liście.</span><span class="sxs-lookup"><span data-stu-id="dd97b-122">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="dd97b-123">W przeciwieństwie do definicji parametru argumenty nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="dd97b-123">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="dd97b-124">Każdy argument jest wyrażenie, które może zawierać zero lub więcej zmiennych, stałe i literały.</span><span class="sxs-lookup"><span data-stu-id="dd97b-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="dd97b-125">Typ danych obliczane wyrażenie zwykle powinna być zgodna typu danych zdefiniowanego dla odpowiadającego mu parametru, a w każdym przypadku musi być możliwe do przekonwertowania na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="dd97b-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd97b-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd97b-126">See Also</span></span>  
 [<span data-ttu-id="dd97b-127">Procedury</span><span class="sxs-lookup"><span data-stu-id="dd97b-127">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="dd97b-128">Sub — procedury</span><span class="sxs-lookup"><span data-stu-id="dd97b-128">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="dd97b-129">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="dd97b-129">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="dd97b-130">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="dd97b-130">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="dd97b-131">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="dd97b-131">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="dd97b-132">Porady: Definiowanie parametru dla procedury</span><span class="sxs-lookup"><span data-stu-id="dd97b-132">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)  
 [<span data-ttu-id="dd97b-133">Porady: przekazywanie argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="dd97b-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="dd97b-134">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="dd97b-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="dd97b-135">Procedury cykliczne</span><span class="sxs-lookup"><span data-stu-id="dd97b-135">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="dd97b-136">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="dd97b-136">Procedure Overloading</span></span>](./procedure-overloading.md)
