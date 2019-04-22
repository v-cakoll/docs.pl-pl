---
title: Sub — Procedury (Visual Basic)
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
ms.openlocfilehash: b70594e002bbf08f0890586e78df901ccb26c7ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58843113"
---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="0280f-102">Sub — Procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0280f-102">Sub Procedures (Visual Basic)</span></span>
<span data-ttu-id="0280f-103">A `Sub` procedura jest szereg instrukcji ujęta w `Sub` i `End Sub` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0280f-103">A `Sub` procedure is a series of Visual Basic statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="0280f-104">`Sub` Procedura wykonuje zadanie, a następnie przekazuje sterowanie do kodu wywołującego, ale nie zwraca wartości do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="0280f-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>  
  
 <span data-ttu-id="0280f-105">Każdorazowo, procedura jest wywoływana, jego wykonywane są instrukcje, począwszy od pierwszej instrukcji wykonywalnej po `Sub` instrukcji i kończącą pierwszy `End Sub`, `Exit Sub`, lub `Return` instrukcji napotkany.</span><span class="sxs-lookup"><span data-stu-id="0280f-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="0280f-106">Można zdefiniować `Sub` procedury w modułach, klas i struktur.</span><span class="sxs-lookup"><span data-stu-id="0280f-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="0280f-107">Domyślnie jest `Public`, oznacza to, należy wywołać go z dowolnego miejsca w aplikacji, które ma dostęp do modułu, klasy lub struktury on zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="0280f-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="0280f-108">Termin, *metoda*, w tym artykule opisano `Sub` lub `Function` procedury, która jest dostępne spoza jej Definiowanie modułu, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="0280f-108">The term, *method*, describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="0280f-109">Aby uzyskać więcej informacji, zobacz [procedury](./index.md).</span><span class="sxs-lookup"><span data-stu-id="0280f-109">For more information, see [Procedures](./index.md).</span></span>  
  
 <span data-ttu-id="0280f-110">A `Sub` procedurę można wykonać argumentów, takich jak stałe, zmienne lub wyrażeń, które są przekazywane do niej przez kod wywołujący.</span><span class="sxs-lookup"><span data-stu-id="0280f-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="0280f-111">Składnia deklaracji</span><span class="sxs-lookup"><span data-stu-id="0280f-111">Declaration Syntax</span></span>  
 <span data-ttu-id="0280f-112">Składnia do deklarowania `Sub` procedura jest następująca:</span><span class="sxs-lookup"><span data-stu-id="0280f-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="0280f-113">`[` *Modyfikatory* `] Sub` *subname* `[(` *listaparametrów* `)]`</span><span class="sxs-lookup"><span data-stu-id="0280f-113">`[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`</span></span>  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 <span data-ttu-id="0280f-114">`modifiers` Można określić poziom dostępu i informacji o przeładowanie, zastępowanie, udostępnianie i cieniowania.</span><span class="sxs-lookup"><span data-stu-id="0280f-114">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="0280f-115">Aby uzyskać więcej informacji, zobacz [Sub — instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0280f-115">For more information, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="0280f-116">Deklaracja parametru</span><span class="sxs-lookup"><span data-stu-id="0280f-116">Parameter Declaration</span></span>  
 <span data-ttu-id="0280f-117">Możesz zadeklarować każdego parametru procedury, podobnie jak sposób Deklarujesz zmienną, określając parametr nazwę i typ danych.</span><span class="sxs-lookup"><span data-stu-id="0280f-117">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="0280f-118">Można również określić mechanizm przekazywania i czy parametr jest opcjonalny, lub tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="0280f-118">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>  
  
 <span data-ttu-id="0280f-119">Składnia dla każdego parametru na liście parametrów jest w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0280f-119">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 <span data-ttu-id="0280f-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *Nazwa parametru*`As`*typu danych*</span><span class="sxs-lookup"><span data-stu-id="0280f-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*</span></span>  
  
 <span data-ttu-id="0280f-121">Jeśli parametr jest opcjonalny, należy również podać wartości domyślnej w ramach swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="0280f-121">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="0280f-122">Składnia określająca wartość domyślna jest następująca:</span><span class="sxs-lookup"><span data-stu-id="0280f-122">The syntax for specifying a default value is as follows:</span></span>  
  
 <span data-ttu-id="0280f-123">`Optional [ByVal | ByRef]`  *Nazwa parametru*`As`*datatype*`=`*defaultvalue*</span><span class="sxs-lookup"><span data-stu-id="0280f-123">`Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*</span></span>  
  
### <a name="parameters-as-local-variables"></a><span data-ttu-id="0280f-124">Parametry jako zmienne lokalne</span><span class="sxs-lookup"><span data-stu-id="0280f-124">Parameters as Local Variables</span></span>  
 <span data-ttu-id="0280f-125">Jeśli kontrola przechodzi do procedury, każdy parametr jest traktowany jako zmienna lokalna.</span><span class="sxs-lookup"><span data-stu-id="0280f-125">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="0280f-126">Oznacza to, że jego okres istnienia jest taka sama, jak ta procedura, a jej zakres jest całej procedury.</span><span class="sxs-lookup"><span data-stu-id="0280f-126">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="0280f-127">Składnia wywoływania</span><span class="sxs-lookup"><span data-stu-id="0280f-127">Calling Syntax</span></span>  
 <span data-ttu-id="0280f-128">Wywołuje się `Sub` procedury jawnie za pomocą autonomicznego instrukcji wywołujące.</span><span class="sxs-lookup"><span data-stu-id="0280f-128">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="0280f-129">Nie można jej wywołać przy użyciu jego nazwy w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="0280f-129">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="0280f-130">Należy podać wartości w argumentach, które nie są opcjonalne, a na liście argumentów należy ująć w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="0280f-130">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="0280f-131">Jeśli zostały dostarczone żadne argumenty, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="0280f-131">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="0280f-132">Korzystanie z `Call` — słowo kluczowe jest opcjonalne, ale niezalecane.</span><span class="sxs-lookup"><span data-stu-id="0280f-132">The use of the `Call` keyword is optional but not recommended.</span></span>  
  
 <span data-ttu-id="0280f-133">Składnia służąca do wywołania `Sub` procedura jest następująca:</span><span class="sxs-lookup"><span data-stu-id="0280f-133">The syntax for a call to a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="0280f-134">`[Call]`  *subname* `[(` *listaargumentów* `)]`</span><span class="sxs-lookup"><span data-stu-id="0280f-134">`[Call]`  *subname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="0280f-135">Możesz wywołać `Sub` metody z poza klasy, który go definiuje.</span><span class="sxs-lookup"><span data-stu-id="0280f-135">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="0280f-136">Najpierw trzeba użyć `New` słowo kluczowe, aby utworzyć wystąpienia klasy lub wywołanie metody zwraca wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="0280f-136">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="0280f-137">Aby uzyskać więcej informacji, zobacz [operatora New](../../../../visual-basic/language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="0280f-137">For more information, see [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="0280f-138">Następnie można użyć następującej składni wywołać `Sub` metody dla obiektu wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="0280f-138">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>  
  
 <span data-ttu-id="0280f-139">*Obiekt*. *methodname*`[(`*listaargumentów*`)]`</span><span class="sxs-lookup"><span data-stu-id="0280f-139">*Object*.*methodname*`[(`*argumentlist*`)]`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="0280f-140">Ilustracja deklaracji i wywołanie</span><span class="sxs-lookup"><span data-stu-id="0280f-140">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="0280f-141">Następujące `Sub` procedura opisuje operator komputera zadań, która aplikacja ma wykonać i wyświetla również sygnaturę czasową.</span><span class="sxs-lookup"><span data-stu-id="0280f-141">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="0280f-142">Zamiast duplikowania ten kod na początku każdego zadania, po prostu wywołuje aplikację `tellOperator` z różnych lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="0280f-142">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="0280f-143">Każde wywołanie przekazuje ciąg w `task` argument, który identyfikuje zadanie jest uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="0280f-143">Each call passes a string in the `task` argument that identifies the task being started.</span></span>  
  
 [!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]  
  
 <span data-ttu-id="0280f-144">W poniższym przykładzie przedstawiono typowe wywołanie `tellOperator`.</span><span class="sxs-lookup"><span data-stu-id="0280f-144">The following example shows a typical call to `tellOperator`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="0280f-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0280f-145">See also</span></span>

- [<span data-ttu-id="0280f-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="0280f-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="0280f-147">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="0280f-147">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="0280f-148">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="0280f-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="0280f-149">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="0280f-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="0280f-150">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="0280f-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="0280f-151">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="0280f-151">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="0280f-152">Instrukcje: Wywoływanie procedury, która nie zwraca wartości</span><span class="sxs-lookup"><span data-stu-id="0280f-152">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [<span data-ttu-id="0280f-153">Instrukcje: Wywoływanie programu do obsługi zdarzeń w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0280f-153">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
