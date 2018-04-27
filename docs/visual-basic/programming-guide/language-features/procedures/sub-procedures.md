---
title: Sub — Procedury (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Sub procedures [Visual Basic], about Sub procedures
- statement blocks
- Sub procedures [Visual Basic], calling
- procedures [Visual Basic], calling
- Sub procedures [Visual Basic], syntax
- Sub procedures
- procedures [Visual Basic], Sub
- syntax [Visual Basic], Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7258d57d2677042a2020097893a4f7a0adb35508
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="18b62-102">Sub — Procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18b62-102">Sub Procedures (Visual Basic)</span></span>
<span data-ttu-id="18b62-103">A `Sub` procedura jest serię instrukcji języka Visual Basic otoczony `Sub` i `End Sub` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="18b62-103">A `Sub` procedure is a series of Visual Basic statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="18b62-104">`Sub` Procedury wykonuje zadanie, a następnie zwraca sterowania do kodu wywołującego, ale nie zwraca wartości do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="18b62-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>  
  
 <span data-ttu-id="18b62-105">Każdorazowo po wywołaniu procedury jego instrukcje są wykonywane, zaczynając od pierwszej instrukcji wykonywalnej po `Sub` instrukcji i kończąc pierwszy `End Sub`, `Exit Sub`, lub `Return` Napotkano instrukcję.</span><span class="sxs-lookup"><span data-stu-id="18b62-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="18b62-106">Można zdefiniować `Sub` procedury w modułach, klasy i struktury.</span><span class="sxs-lookup"><span data-stu-id="18b62-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="18b62-107">Domyślnie jest `Public`, co oznacza, należy go wywoływać z dowolnego miejsca w aplikacji, który ma dostęp do modułu, klasy lub struktury ona zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="18b62-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="18b62-108">Termin, *metody*, w tym artykule opisano `Sub` lub `Function` procedury, która jest dostępne spoza jej definiowania modułu, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="18b62-108">The term, *method*, describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="18b62-109">Aby uzyskać więcej informacji, zobacz [procedury](./index.md).</span><span class="sxs-lookup"><span data-stu-id="18b62-109">For more information, see [Procedures](./index.md).</span></span>  
  
 <span data-ttu-id="18b62-110">A `Sub` może potrwać argumenty, takie jak stałe, zmiennych lub wyrażeń, które są przekazywane do niej przez kod wywołujący.</span><span class="sxs-lookup"><span data-stu-id="18b62-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="18b62-111">Składnia deklaracji</span><span class="sxs-lookup"><span data-stu-id="18b62-111">Declaration Syntax</span></span>  
 <span data-ttu-id="18b62-112">Składnia deklaracji `Sub` procedura wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="18b62-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="18b62-113">`[` *Modyfikatory* `] Sub` *subname* `[(` *listaparametrów*  `)]`</span><span class="sxs-lookup"><span data-stu-id="18b62-113">`[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`</span></span>  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 <span data-ttu-id="18b62-114">`modifiers` Można określić poziom dostępu i informacji o przeciążeniu, zastępowanie udostępniania i przesłanianie.</span><span class="sxs-lookup"><span data-stu-id="18b62-114">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="18b62-115">Aby uzyskać więcej informacji, zobacz [Sub — instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="18b62-115">For more information, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="18b62-116">Deklaracja parametru</span><span class="sxs-lookup"><span data-stu-id="18b62-116">Parameter Declaration</span></span>  
 <span data-ttu-id="18b62-117">Należy zadeklarować każdego parametru procedury, podobnie jak jak Zmienna zadeklarowana, określając parametr nazwę i typ danych.</span><span class="sxs-lookup"><span data-stu-id="18b62-117">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="18b62-118">Można również określić mechanizm przekazywania i określa, czy parametr jest opcjonalny lub tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="18b62-118">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>  
  
 <span data-ttu-id="18b62-119">Dla każdego parametru na liście parametrów ma następującą składnię:</span><span class="sxs-lookup"><span data-stu-id="18b62-119">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 <span data-ttu-id="18b62-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *Nazwa parametru*`As`*typu danych* </span><span class="sxs-lookup"><span data-stu-id="18b62-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*</span></span>  
  
 <span data-ttu-id="18b62-121">Jeśli parametr jest opcjonalny, należy również podać wartości domyślnej jako części swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="18b62-121">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="18b62-122">Składnia służąca do określania wartości domyślnej jest następujący:</span><span class="sxs-lookup"><span data-stu-id="18b62-122">The syntax for specifying a default value is as follows:</span></span>  
  
 <span data-ttu-id="18b62-123">`Optional [ByVal | ByRef]`  *Nazwa parametru*`As`*datatype*`=`*defaultvalue* </span><span class="sxs-lookup"><span data-stu-id="18b62-123">`Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*</span></span>  
  
### <a name="parameters-as-local-variables"></a><span data-ttu-id="18b62-124">Parametry jako zmienne lokalne</span><span class="sxs-lookup"><span data-stu-id="18b62-124">Parameters as Local Variables</span></span>  
 <span data-ttu-id="18b62-125">Gdy formant przechodzi do procedury, każdy parametr jest traktowany jako zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="18b62-125">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="18b62-126">Oznacza to, że jego okres istnienia jest taka sama, jak te procedury, a jej zakres całej procedury.</span><span class="sxs-lookup"><span data-stu-id="18b62-126">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="18b62-127">Składnia wywoływania</span><span class="sxs-lookup"><span data-stu-id="18b62-127">Calling Syntax</span></span>  
 <span data-ttu-id="18b62-128">Wywołuje się `Sub` procedury jawnie z autonomicznej instrukcji wywoływania.</span><span class="sxs-lookup"><span data-stu-id="18b62-128">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="18b62-129">Nie można wywołać ją przy użyciu nazwy w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="18b62-129">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="18b62-130">Należy podać wartości dla wszystkich argumentów, które nie są opcjonalne i listy argumentów należy ująć w nawias.</span><span class="sxs-lookup"><span data-stu-id="18b62-130">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="18b62-131">Jeśli nie jest dostarczony bez argumentów, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="18b62-131">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="18b62-132">Korzystanie z `Call` — słowo kluczowe jest opcjonalne, ale nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="18b62-132">The use of the `Call` keyword is optional but not recommended.</span></span>  
  
 <span data-ttu-id="18b62-133">Składnia wywołania `Sub` procedura wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="18b62-133">The syntax for a call to a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="18b62-134">`[Call]`  *subname* `[(` *listaargumentów* `)]`</span><span class="sxs-lookup"><span data-stu-id="18b62-134">`[Call]`  *subname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="18b62-135">Możesz wywołać `Sub` metody z poza klasą, który definiuje go.</span><span class="sxs-lookup"><span data-stu-id="18b62-135">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="18b62-136">Po pierwsze, należy użyć `New` — słowo kluczowe w celu utworzenia wystąpienia klasy lub wywołanie metody, która zwraca wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="18b62-136">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="18b62-137">Aby uzyskać więcej informacji, zobacz [operatora New](../../../../visual-basic/language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="18b62-137">For more information, see [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="18b62-138">Następnie można następującej składni wywołań `Sub` metody wystąpienia obiektu:</span><span class="sxs-lookup"><span data-stu-id="18b62-138">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>  
  
 <span data-ttu-id="18b62-139">*Obiekt*. *methodname*`[(`*listaargumentów*`)]`</span><span class="sxs-lookup"><span data-stu-id="18b62-139">*Object*.*methodname*`[(`*argumentlist*`)]`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="18b62-140">Ilustracja deklaracji i wywołanie</span><span class="sxs-lookup"><span data-stu-id="18b62-140">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="18b62-141">Następujące `Sub` procedury informuje operator komputera zadań, która aplikacja ma wykonać, a także sygnaturę czasową.</span><span class="sxs-lookup"><span data-stu-id="18b62-141">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="18b62-142">Zamiast duplikowania ten kod na początku każdego zadania, po prostu wywołuje aplikację `tellOperator` z różnych lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="18b62-142">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="18b62-143">Każde wywołanie przekazuje ciąg w `task` argumentu, który identyfikuje zadań jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="18b62-143">Each call passes a string in the `task` argument that identifies the task being started.</span></span>  
  
 [!code-vb[VbVbcnProcedures#2](./codesnippet/VisualBasic/sub-procedures_1.vb)]  
  
 <span data-ttu-id="18b62-144">W poniższym przykładzie przedstawiono typowe wywołania `tellOperator`.</span><span class="sxs-lookup"><span data-stu-id="18b62-144">The following example shows a typical call to `tellOperator`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#3](./codesnippet/VisualBasic/sub-procedures_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="18b62-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="18b62-145">See Also</span></span>  
 [<span data-ttu-id="18b62-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="18b62-146">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="18b62-147">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="18b62-147">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="18b62-148">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="18b62-148">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="18b62-149">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="18b62-149">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="18b62-150">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="18b62-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="18b62-151">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="18b62-151">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="18b62-152">Instrukcje: wywoływanie procedury, która nie zwraca wartości</span><span class="sxs-lookup"><span data-stu-id="18b62-152">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)  
 [<span data-ttu-id="18b62-153">Porady: wywoływanie procedury obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="18b62-153">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
