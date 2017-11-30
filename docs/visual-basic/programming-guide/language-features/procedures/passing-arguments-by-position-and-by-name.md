---
title: "Przekazywanie argumentów według pozycji i według nazwy (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 164f69fcf23049441a0acbe05058c792d5363a03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="f4d3a-102">Przekazywanie argumentów według pozycji i według nazwy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4d3a-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>
<span data-ttu-id="f4d3a-103">Podczas wywoływania `Sub` lub `Function` procedury, można przekazywać argumenty *według położenia* — w kolejności, w jakiej występują w definicji procedury — lub można przekazać *według nazwy*, bez w odniesieniu do pozycji.</span><span class="sxs-lookup"><span data-stu-id="f4d3a-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>  
  
 <span data-ttu-id="f4d3a-104">Jeśli argument według nazw, określ argument deklarowana przez nazwę dwukropek i znak równości (`:=`), a następnie wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="f4d3a-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="f4d3a-105">Możesz podać Argumenty nazwane w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="f4d3a-105">You can supply named arguments in any order.</span></span>  
  
 <span data-ttu-id="f4d3a-106">Na przykład następująca `Sub` procedury przyjmuje trzy argumenty:</span><span class="sxs-lookup"><span data-stu-id="f4d3a-106">For example, the following `Sub` procedure takes three arguments:</span></span>  
  
 [!code-vb[VbVbcnProcedures#41](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_1.vb)]  
  
 <span data-ttu-id="f4d3a-107">Podczas wywoływania tej procedury, można podać argumentów według pozycji, według nazwy lub za pomocą ich kombinacjami.</span><span class="sxs-lookup"><span data-stu-id="f4d3a-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>  
  
## <a name="passing-arguments-by-position"></a><span data-ttu-id="f4d3a-108">Przekazywanie argumentów według pozycji</span><span class="sxs-lookup"><span data-stu-id="f4d3a-108">Passing Arguments by Position</span></span>  
 <span data-ttu-id="f4d3a-109">Można wywołać procedury `studentInfo` z jego argumentów przekazywane według pozycji i rozdzielonych przecinkami, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f4d3a-109">You can call the procedure `studentInfo` with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#42](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_2.vb)]  
  
 <span data-ttu-id="f4d3a-110">W przypadku pominięcia opcjonalny argument w postaci listy argument pozycyjny, musi posiadać zamiast niej użyć przecinka.</span><span class="sxs-lookup"><span data-stu-id="f4d3a-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="f4d3a-111">Następujące przykładowe wywołania `studentInfo` bez `age` argumentu:</span><span class="sxs-lookup"><span data-stu-id="f4d3a-111">The following example calls `studentInfo` without the `age` argument:</span></span>  
  
 [!code-vb[VbVbcnProcedures#43](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_3.vb)]  
  
## <a name="passing-arguments-by-name"></a><span data-ttu-id="f4d3a-112">Przekazywanie argumentów według nazwy</span><span class="sxs-lookup"><span data-stu-id="f4d3a-112">Passing Arguments by Name</span></span>  
 <span data-ttu-id="f4d3a-113">Alternatywnie możesz wywołać `studentInfo` argumentów przekazywane według nazw, również rozdzielonych przecinkami, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f4d3a-113">Alternatively, you can call `studentInfo` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#44](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_4.vb)]  
  
## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="f4d3a-114">Mieszanie argumentów według pozycji i według nazwy</span><span class="sxs-lookup"><span data-stu-id="f4d3a-114">Mixing Arguments by Position and by Name</span></span>  
 <span data-ttu-id="f4d3a-115">Można podać argumenty zarówno według pozycji i według nazwy w wywołaniu procedury pojedynczego, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f4d3a-115">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#45](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_5.vb)]  
  
 <span data-ttu-id="f4d3a-116">W powyższym przykładzie nie dodatkowy przecinek jest niezbędne do przechowywania miejsca pominięcia `age` argumentu, ponieważ `birth` jest przekazywana przez nazwę.</span><span class="sxs-lookup"><span data-stu-id="f4d3a-116">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>  
  
 <span data-ttu-id="f4d3a-117">Jeśli podasz argumenty mieszaniną pozycji i nazwy, argumenty pozycyjne musi występować wszystkie pierwszy.</span><span class="sxs-lookup"><span data-stu-id="f4d3a-117">When you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="f4d3a-118">Po podasz argument o nazwie pozostałe argumenty muszą być wszystkie według nazwy.</span><span class="sxs-lookup"><span data-stu-id="f4d3a-118">Once you supply an argument by name, the remaining arguments must all be by name.</span></span>  
  
## <a name="supplying-optional-arguments-by-name"></a><span data-ttu-id="f4d3a-119">Podanie argumentów opcjonalnych według nazwy</span><span class="sxs-lookup"><span data-stu-id="f4d3a-119">Supplying Optional Arguments by Name</span></span>  
 <span data-ttu-id="f4d3a-120">Przekazywanie argumentów według nazwy jest szczególnie przydatna podczas wywoływania procedury, która ma więcej niż jeden argument opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f4d3a-120">Passing arguments by name is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="f4d3a-121">Należy podać argumenty według nazwy, nie trzeba używać przecinków kolejnych oznaczający brak argumenty pozycyjne.</span><span class="sxs-lookup"><span data-stu-id="f4d3a-121">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="f4d3a-122">Przekazywanie argumentów według nazwy również ułatwia do śledzenia argumenty, które są przekazywane i które pominięcie.</span><span class="sxs-lookup"><span data-stu-id="f4d3a-122">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>  
  
## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="f4d3a-123">Ograniczenia dotyczące określenie argumentów według nazwy</span><span class="sxs-lookup"><span data-stu-id="f4d3a-123">Restrictions on Supplying Arguments by Name</span></span>  
 <span data-ttu-id="f4d3a-124">Nie można przekazywać argumentów przez nazwę, aby uniknąć wprowadzenia wymaganych argumentów.</span><span class="sxs-lookup"><span data-stu-id="f4d3a-124">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="f4d3a-125">Można pominąć tylko argumenty opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="f4d3a-125">You can omit only the optional arguments.</span></span>  
  
 <span data-ttu-id="f4d3a-126">Tablica parametrów nie można przekazać według nazwy.</span><span class="sxs-lookup"><span data-stu-id="f4d3a-126">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="f4d3a-127">To dlatego po wywołaniu procedury, podaj nieokreśloną liczbę rozdzielone przecinkami argumenty dla tablicy parametrów, a kompilator nie można skojarzyć więcej niż jeden argument pod jedną nazwą.</span><span class="sxs-lookup"><span data-stu-id="f4d3a-127">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4d3a-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4d3a-128">See Also</span></span>  
 [<span data-ttu-id="f4d3a-129">Procedury</span><span class="sxs-lookup"><span data-stu-id="f4d3a-129">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="f4d3a-130">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="f4d3a-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="f4d3a-131">Porady: przekazywanie argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="f4d3a-131">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="f4d3a-132">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="f4d3a-132">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="f4d3a-133">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="f4d3a-133">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="f4d3a-134">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="f4d3a-134">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="f4d3a-135">Opcjonalne</span><span class="sxs-lookup"><span data-stu-id="f4d3a-135">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [<span data-ttu-id="f4d3a-136">ParamArray</span><span class="sxs-lookup"><span data-stu-id="f4d3a-136">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
