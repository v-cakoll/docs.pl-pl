---
title: Sub — Procedury
ms.date: 07/20/2015
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
ms.openlocfilehash: 7848dc07d6462622685cdbea92202585f4d5d2c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352525"
---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="3725f-102">Sub — Procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3725f-102">Sub Procedures (Visual Basic)</span></span>
<span data-ttu-id="3725f-103">Procedura `Sub` jest serią Visual Basic instrukcji ujętych w instrukcji `Sub` i `End Sub`.</span><span class="sxs-lookup"><span data-stu-id="3725f-103">A `Sub` procedure is a series of Visual Basic statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="3725f-104">Procedura `Sub` wykonuje zadanie, a następnie zwraca sterowanie do kodu wywołującego, ale nie zwraca wartości do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="3725f-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>  
  
 <span data-ttu-id="3725f-105">Za każdym razem, gdy procedura jest wywoływana, jej instrukcje są wykonywane, rozpoczynając od pierwszej instrukcji wykonywalnej po instrukcji `Sub` i kończąc na pierwszej instrukcji `End Sub`, `Exit Sub`lub `Return`.</span><span class="sxs-lookup"><span data-stu-id="3725f-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="3725f-106">Można zdefiniować `Sub` procedury w modułach, klasach i strukturach.</span><span class="sxs-lookup"><span data-stu-id="3725f-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="3725f-107">Domyślnie jest `Public`, co oznacza, że można wywołać ją z dowolnego miejsca w aplikacji, która ma dostęp do modułu, klasy lub struktury, w której został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="3725f-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="3725f-108">Termin, *Metoda*, opisuje procedurę `Sub` lub `Function`, do której uzyskano dostęp spoza zdefiniowanego modułu, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="3725f-108">The term, *method*, describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="3725f-109">Aby uzyskać więcej informacji, zobacz [procedur](./index.md).</span><span class="sxs-lookup"><span data-stu-id="3725f-109">For more information, see [Procedures](./index.md).</span></span>  
  
 <span data-ttu-id="3725f-110">Procedura `Sub` może przyjmować argumenty, takie jak stałe, zmienne lub wyrażenia, które są przekazane do niego przez wywołujący kod.</span><span class="sxs-lookup"><span data-stu-id="3725f-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="3725f-111">Składnia deklaracji</span><span class="sxs-lookup"><span data-stu-id="3725f-111">Declaration Syntax</span></span>  
 <span data-ttu-id="3725f-112">Składnia do deklarowania procedury `Sub` jest następująca:</span><span class="sxs-lookup"><span data-stu-id="3725f-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="3725f-113">`[` *modyfikatory* `] Sub`*SubName* `[(` *listaparametrów* `)]`</span><span class="sxs-lookup"><span data-stu-id="3725f-113">`[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`</span></span>  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 <span data-ttu-id="3725f-114">`modifiers` można określić poziom dostępu i informacje dotyczące przeciążania, przesłaniania, udostępniania i przesłaniania.</span><span class="sxs-lookup"><span data-stu-id="3725f-114">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="3725f-115">Aby uzyskać więcej informacji, zobacz [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3725f-115">For more information, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="3725f-116">Deklaracja parametru</span><span class="sxs-lookup"><span data-stu-id="3725f-116">Parameter Declaration</span></span>  
 <span data-ttu-id="3725f-117">Każdy parametr procedury deklaruje się podobnie jak w przypadku deklarowania zmiennej, określając nazwę parametru i typ danych.</span><span class="sxs-lookup"><span data-stu-id="3725f-117">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="3725f-118">Można również określić mechanizm przekazywania oraz określać, czy parametr jest opcjonalny, czy też tablicą parametrów.</span><span class="sxs-lookup"><span data-stu-id="3725f-118">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>  
  
 <span data-ttu-id="3725f-119">Składnia każdego parametru na liście parametrów jest następująca:</span><span class="sxs-lookup"><span data-stu-id="3725f-119">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 <span data-ttu-id="3725f-120">`[Optional] [ByVal | ByRef] [ParamArray]`*parametername*`As`*DataType*</span><span class="sxs-lookup"><span data-stu-id="3725f-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*</span></span>  
  
 <span data-ttu-id="3725f-121">Jeśli parametr jest opcjonalny, należy również podać wartość domyślną w ramach swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="3725f-121">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="3725f-122">Składnia określająca wartość domyślną jest następująca:</span><span class="sxs-lookup"><span data-stu-id="3725f-122">The syntax for specifying a default value is as follows:</span></span>  
  
 <span data-ttu-id="3725f-123">`Optional [ByVal | ByRef]`*parametername*`As`*DataType*`=`*DefaultValue*</span><span class="sxs-lookup"><span data-stu-id="3725f-123">`Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*</span></span>  
  
### <a name="parameters-as-local-variables"></a><span data-ttu-id="3725f-124">Parametry jako zmienne lokalne</span><span class="sxs-lookup"><span data-stu-id="3725f-124">Parameters as Local Variables</span></span>  
 <span data-ttu-id="3725f-125">Gdy kontrola przechodzi do procedury, każdy parametr jest traktowany jako zmienna lokalna.</span><span class="sxs-lookup"><span data-stu-id="3725f-125">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="3725f-126">Oznacza to, że jego okres istnienia jest taki sam jak w przypadku tej procedury, a jego zakres jest całą procedurą.</span><span class="sxs-lookup"><span data-stu-id="3725f-126">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="3725f-127">Składnia wywołania</span><span class="sxs-lookup"><span data-stu-id="3725f-127">Calling Syntax</span></span>  
 <span data-ttu-id="3725f-128">Procedurę `Sub` należy wywoływać jawnie przy użyciu autonomicznej instrukcji wywołującej.</span><span class="sxs-lookup"><span data-stu-id="3725f-128">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="3725f-129">Nie można wywołać go przy użyciu jego nazwy w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="3725f-129">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="3725f-130">Musisz podać wartości dla wszystkich argumentów, które nie są opcjonalne, i należy ująć listę argumentów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="3725f-130">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="3725f-131">Jeśli nie podano argumentów, można opcjonalnie pominąć nawiasy.</span><span class="sxs-lookup"><span data-stu-id="3725f-131">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="3725f-132">Użycie słowa kluczowego `Call` jest opcjonalne, ale nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="3725f-132">The use of the `Call` keyword is optional but not recommended.</span></span>  
  
 <span data-ttu-id="3725f-133">Składnia wywołania procedury `Sub` jest następująca:</span><span class="sxs-lookup"><span data-stu-id="3725f-133">The syntax for a call to a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="3725f-134">`[Call]`*SubName* `[(` *listaargumentów* `)]`</span><span class="sxs-lookup"><span data-stu-id="3725f-134">`[Call]`  *subname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="3725f-135">Metodę `Sub` można wywołać spoza klasy, która go definiuje.</span><span class="sxs-lookup"><span data-stu-id="3725f-135">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="3725f-136">Najpierw należy użyć słowa kluczowego `New`, aby utworzyć wystąpienie klasy, lub wywołać metodę zwracającą wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="3725f-136">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="3725f-137">Aby uzyskać więcej informacji, zobacz [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="3725f-137">For more information, see [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="3725f-138">Następnie można użyć następującej składni, aby wywołać metodę `Sub` w obiekcie wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="3725f-138">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>  
  
 <span data-ttu-id="3725f-139">*Obiekt*. *methodname*`[(`*listaargumentów*`)]`</span><span class="sxs-lookup"><span data-stu-id="3725f-139">*Object*.*methodname*`[(`*argumentlist*`)]`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="3725f-140">Ilustracja deklaracji i wywołania</span><span class="sxs-lookup"><span data-stu-id="3725f-140">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="3725f-141">Poniższa procedura `Sub` informuje operatora komputera, który zadanie ma wykonać aplikacja, a także wyświetla sygnaturę czasową.</span><span class="sxs-lookup"><span data-stu-id="3725f-141">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="3725f-142">Zamiast duplikować ten kod na początku każdego zadania, aplikacja właśnie wywołuje `tellOperator` z różnych lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="3725f-142">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="3725f-143">Każde wywołanie przekazuje ciąg w argumencie `task`, który identyfikuje uruchomione zadanie.</span><span class="sxs-lookup"><span data-stu-id="3725f-143">Each call passes a string in the `task` argument that identifies the task being started.</span></span>  
  
 [!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]  
  
 <span data-ttu-id="3725f-144">Poniższy przykład przedstawia typowe wywołanie do `tellOperator`.</span><span class="sxs-lookup"><span data-stu-id="3725f-144">The following example shows a typical call to `tellOperator`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="3725f-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3725f-145">See also</span></span>

- [<span data-ttu-id="3725f-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="3725f-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="3725f-147">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="3725f-147">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="3725f-148">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="3725f-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="3725f-149">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="3725f-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="3725f-150">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="3725f-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="3725f-151">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3725f-151">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="3725f-152">Instrukcje: wywoływanie procedury, która nie zwraca wartości</span><span class="sxs-lookup"><span data-stu-id="3725f-152">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [<span data-ttu-id="3725f-153">Instrukcje: wywoływanie procedury obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3725f-153">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
