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
ms.openlocfilehash: 9ca1d302a0bc8e989e0b2dddf8cce68e89211d57
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163816"
---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="43038-102">Sub — procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43038-102">Sub procedures (Visual Basic)</span></span>

<span data-ttu-id="43038-103">Procedura `Sub` jest serią Visual Basic instrukcji ujętych w instrukcji `Sub` i `End Sub`.</span><span class="sxs-lookup"><span data-stu-id="43038-103">A `Sub` procedure is a series of Visual Basic statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="43038-104">Procedura `Sub` wykonuje zadanie, a następnie zwraca sterowanie do kodu wywołującego, ale nie zwraca wartości do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="43038-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>

<span data-ttu-id="43038-105">Za każdym razem, gdy procedura jest wywoływana, jej instrukcje są wykonywane, rozpoczynając od pierwszej instrukcji wykonywalnej po instrukcji `Sub` i kończąc na pierwszej instrukcji `End Sub`, `Exit Sub`lub `Return`.</span><span class="sxs-lookup"><span data-stu-id="43038-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>

<span data-ttu-id="43038-106">Można zdefiniować `Sub` procedury w modułach, klasach i strukturach.</span><span class="sxs-lookup"><span data-stu-id="43038-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="43038-107">Domyślnie jest `Public`, co oznacza, że można wywołać ją z dowolnego miejsca w aplikacji, która ma dostęp do modułu, klasy lub struktury, w której został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="43038-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="43038-108">Termin *Metoda* zawiera opis procedury `Sub` lub `Function`, do której dostęp można uzyskać spoza definicji modułu, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="43038-108">The term *method* describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="43038-109">Aby uzyskać więcej informacji, zobacz [procedur](./index.md).</span><span class="sxs-lookup"><span data-stu-id="43038-109">For more information, see [Procedures](./index.md).</span></span>

<span data-ttu-id="43038-110">Procedura `Sub` może przyjmować argumenty, takie jak stałe, zmienne lub wyrażenia, które są przekazane do niego przez wywołujący kod.</span><span class="sxs-lookup"><span data-stu-id="43038-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="43038-111">Składnia deklaracji</span><span class="sxs-lookup"><span data-stu-id="43038-111">Declaration syntax</span></span>

<span data-ttu-id="43038-112">Składnia do deklarowania procedury `Sub` jest następująca:</span><span class="sxs-lookup"><span data-stu-id="43038-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>

```vb
[modifiers] Sub SubName[(parameterList)]
    ' Statements of the Sub procedure.
End Sub
```

<span data-ttu-id="43038-113">`modifiers` można określić poziom dostępu i informacje dotyczące przeciążania, przesłaniania, udostępniania i przesłaniania.</span><span class="sxs-lookup"><span data-stu-id="43038-113">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="43038-114">Aby uzyskać więcej informacji, zobacz [Sub Statement](../../../language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="43038-114">For more information, see [Sub Statement](../../../language-reference/statements/sub-statement.md).</span></span>

## <a name="parameter-declaration"></a><span data-ttu-id="43038-115">Deklaracja parametru</span><span class="sxs-lookup"><span data-stu-id="43038-115">Parameter declaration</span></span>

<span data-ttu-id="43038-116">Każdy parametr procedury deklaruje się podobnie jak w przypadku deklarowania zmiennej, określając nazwę parametru i typ danych.</span><span class="sxs-lookup"><span data-stu-id="43038-116">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="43038-117">Można również określić mechanizm przekazywania oraz określać, czy parametr jest opcjonalny, czy też tablicą parametrów.</span><span class="sxs-lookup"><span data-stu-id="43038-117">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>

<span data-ttu-id="43038-118">Składnia każdego parametru na liście parametrów jest następująca:</span><span class="sxs-lookup"><span data-stu-id="43038-118">The syntax for each parameter in the parameter list is as follows:</span></span>

```vb
[Optional] [ByVal | ByRef] [ParamArray] parameterName As DataType
```

<span data-ttu-id="43038-119">Jeśli parametr jest opcjonalny, należy również podać wartość domyślną w ramach swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="43038-119">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="43038-120">Składnia określająca wartość domyślną jest następująca:</span><span class="sxs-lookup"><span data-stu-id="43038-120">The syntax for specifying a default value is as follows:</span></span>

```vb
Optional [ByVal | ByRef]  parameterName As DataType = defaultValue
```

### <a name="parameters-as-local-variables"></a><span data-ttu-id="43038-121">Parametry jako zmienne lokalne</span><span class="sxs-lookup"><span data-stu-id="43038-121">Parameters as local variables</span></span>

<span data-ttu-id="43038-122">Gdy kontrola przechodzi do procedury, każdy parametr jest traktowany jako zmienna lokalna.</span><span class="sxs-lookup"><span data-stu-id="43038-122">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="43038-123">Oznacza to, że jego okres istnienia jest taki sam jak w przypadku tej procedury, a jego zakres jest całą procedurą.</span><span class="sxs-lookup"><span data-stu-id="43038-123">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="43038-124">Składnia wywołania</span><span class="sxs-lookup"><span data-stu-id="43038-124">Calling syntax</span></span>

<span data-ttu-id="43038-125">Procedurę `Sub` należy wywoływać jawnie przy użyciu autonomicznej instrukcji wywołującej.</span><span class="sxs-lookup"><span data-stu-id="43038-125">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="43038-126">Nie można wywołać go przy użyciu jego nazwy w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="43038-126">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="43038-127">Musisz podać wartości dla wszystkich argumentów, które nie są opcjonalne, i należy ująć listę argumentów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="43038-127">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="43038-128">Jeśli nie podano argumentów, można opcjonalnie pominąć nawiasy.</span><span class="sxs-lookup"><span data-stu-id="43038-128">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="43038-129">Użycie słowa kluczowego `Call` jest opcjonalne, ale nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="43038-129">The use of the `Call` keyword is optional but not recommended.</span></span>

<span data-ttu-id="43038-130">Składnia wywołania procedury `Sub` jest następująca:</span><span class="sxs-lookup"><span data-stu-id="43038-130">The syntax for a call to a `Sub` procedure is as follows:</span></span>

```vb
[Call] SubName[(argumentlist)]
```

<span data-ttu-id="43038-131">Metodę `Sub` można wywołać spoza klasy, która go definiuje.</span><span class="sxs-lookup"><span data-stu-id="43038-131">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="43038-132">Najpierw należy użyć słowa kluczowego `New`, aby utworzyć wystąpienie klasy, lub wywołać metodę zwracającą wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="43038-132">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="43038-133">Aby uzyskać więcej informacji, zobacz [New Operator](../../../language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="43038-133">For more information, see [New Operator](../../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="43038-134">Następnie można użyć następującej składni, aby wywołać metodę `Sub` w obiekcie wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="43038-134">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>

```vb
object.MethodName[(argumentList)]
```

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="43038-135">Ilustracja deklaracji i wywołania</span><span class="sxs-lookup"><span data-stu-id="43038-135">Illustration of declaration and call</span></span>

<span data-ttu-id="43038-136">Poniższa procedura `Sub` informuje operatora komputera, który zadanie ma wykonać aplikacja, a także wyświetla sygnaturę czasową.</span><span class="sxs-lookup"><span data-stu-id="43038-136">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="43038-137">Zamiast duplikować ten kod na początku każdego zadania, aplikacja właśnie wywołuje `tellOperator` z różnych lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="43038-137">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="43038-138">Każde wywołanie przekazuje ciąg w argumencie `task`, który identyfikuje uruchomione zadanie.</span><span class="sxs-lookup"><span data-stu-id="43038-138">Each call passes a string in the `task` argument that identifies the task being started.</span></span>

[!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]

<span data-ttu-id="43038-139">Poniższy przykład przedstawia typowe wywołanie do `tellOperator`.</span><span class="sxs-lookup"><span data-stu-id="43038-139">The following example shows a typical call to `tellOperator`.</span></span>

[!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]

## <a name="see-also"></a><span data-ttu-id="43038-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43038-140">See also</span></span>

- [<span data-ttu-id="43038-141">Procedury</span><span class="sxs-lookup"><span data-stu-id="43038-141">Procedures</span></span>](./index.md)
- [<span data-ttu-id="43038-142">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="43038-142">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="43038-143">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="43038-143">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="43038-144">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="43038-144">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="43038-145">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="43038-145">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="43038-146">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="43038-146">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="43038-147">Instrukcje: wywoływanie procedury, która nie zwraca wartości</span><span class="sxs-lookup"><span data-stu-id="43038-147">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [<span data-ttu-id="43038-148">Instrukcje: wywoływanie procedury obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43038-148">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
