---
title: "Wywoływanie właściwości lub metody za pomocą nazwy ciągu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- passing operators [Visual Basic]
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls [Visual Basic], strings
- methods [Visual Basic], calling with string names
- calling methods [Visual Basic], string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c5974257fb82fe83c66a480225da200c14338898
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a><span data-ttu-id="27975-102">Wywoływanie właściwości lub metody za pomocą nazwy ciągu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27975-102">Calling a Property or Method Using a String Name (Visual Basic)</span></span>
<span data-ttu-id="27975-103">W większości przypadków może odnajdywać właściwości i metody obiektu w czasie projektowania, a do ich obsługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="27975-103">In most cases, you can discover the properties and methods of an object at design time, and write code to handle them.</span></span> <span data-ttu-id="27975-104">Jednak w niektórych przypadkach użytkownik może nie wiedzieć o właściwości i metod obiektu z wyprzedzeniem, lub po prostu chcesz elastyczność włączania użytkownika końcowego określić właściwości lub wykonywanie metod w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="27975-104">However, in some cases you may not know about an object's properties and methods in advance, or you may just want the flexibility of enabling an end user to specify properties or execute methods at run time.</span></span>  
  
## <a name="callbyname-function"></a><span data-ttu-id="27975-105">CallByName — funkcja</span><span class="sxs-lookup"><span data-stu-id="27975-105">CallByName Function</span></span>  
 <span data-ttu-id="27975-106">Należy wziąć pod uwagę, na przykład aplikacji klienckiej, która ocenia wyrażenia wprowadzony przez użytkownika, przekazując operator składnika modelu COM.</span><span class="sxs-lookup"><span data-stu-id="27975-106">Consider, for example, a client application that evaluates expressions entered by the user by passing an operator to a COM component.</span></span> <span data-ttu-id="27975-107">Załóżmy, że stale dodajesz nowe funkcje do składnika, który wymaga nowych operatorów.</span><span class="sxs-lookup"><span data-stu-id="27975-107">Suppose you are constantly adding new functions to the component that require new operators.</span></span> <span data-ttu-id="27975-108">Korzystając z techniki dostępu standardowego obiektu, należy ponownie skompilować i wykonać ponowną dystrybucję aplikacji klienckiej, zanim można używać nowych operatorów.</span><span class="sxs-lookup"><span data-stu-id="27975-108">When you use standard object access techniques, you must recompile and redistribute the client application before it could use the new operators.</span></span> <span data-ttu-id="27975-109">Aby tego uniknąć, można użyć `CallByName` funkcji przekazanie nowych operatorów jako ciągi, bez konieczności zmieniania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="27975-109">To avoid this, you can use the `CallByName` function to pass the new operators as strings, without changing the application.</span></span>  
  
 <span data-ttu-id="27975-110">`CallByName` Funkcji umożliwia określenie właściwości lub metody w czasie wykonywania za pomocą ciągu.</span><span class="sxs-lookup"><span data-stu-id="27975-110">The `CallByName` function lets you use a string to specify a property or method at run time.</span></span> <span data-ttu-id="27975-111">Podpis dla `CallByName` funkcja wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="27975-111">The signature for the `CallByName` function looks like this:</span></span>  
  
 <span data-ttu-id="27975-112">*Wynik* = `CallByName`(*obiektu*, *Nazwaprocedury*, *Typ_wywołania*, *argumenty*())</span><span class="sxs-lookup"><span data-stu-id="27975-112">*Result* = `CallByName`(*Object*, *ProcedureName*, *CallType*, *Arguments*())</span></span>  
  
 <span data-ttu-id="27975-113">Pierwszy argument *obiektu*, przyjmuje nazwę obiektu, który ma być wykonywane działania.</span><span class="sxs-lookup"><span data-stu-id="27975-113">The first argument, *Object*, takes the name of the object you want to act upon.</span></span> <span data-ttu-id="27975-114">*Nazwaprocedury* ciąg znaków zawierający nazwę metody lub właściwości procedury wywoływanej przyjmuje argumentu.</span><span class="sxs-lookup"><span data-stu-id="27975-114">The *ProcedureName* argument takes a string that contains the name of the method or property procedure to be invoked.</span></span> <span data-ttu-id="27975-115">*Typ_wywołania* argument ma stałą, który reprezentuje typ procedury, aby wywołać: metody (`Microsoft.VisualBasic.CallType.Method`), właściwości do odczytu (`Microsoft.VisualBasic.CallType.Get`), lub ustaw właściwość (`Microsoft.VisualBasic.CallType.Set`).</span><span class="sxs-lookup"><span data-stu-id="27975-115">The *CallType* argument takes a constant that represents the type of procedure to invoke: a method (`Microsoft.VisualBasic.CallType.Method`), a property read (`Microsoft.VisualBasic.CallType.Get`), or a property set (`Microsoft.VisualBasic.CallType.Set`).</span></span> <span data-ttu-id="27975-116">*Argumenty* argument, który jest opcjonalny, pobiera tablicę typu `Object` zawierający żadnych argumentów do procedury.</span><span class="sxs-lookup"><span data-stu-id="27975-116">The *Arguments* argument, which is optional, takes an array of type `Object` that contains any arguments to the procedure.</span></span>  
  
 <span data-ttu-id="27975-117">Można użyć `CallByName` z klasami bieżącego rozwiązania, ale jest najczęściej używana dostęp do obiektów COM lub obiektów z [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawów.</span><span class="sxs-lookup"><span data-stu-id="27975-117">You can use `CallByName` with classes in your current solution, but it is most often used to access COM objects or objects from [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies.</span></span>  
  
 <span data-ttu-id="27975-118">Załóżmy, że możesz dodać odwołania do zestawu zawierającego klasę o nazwie `MathClass`, która zawiera nową funkcję o nazwie `SquareRoot`, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="27975-118">Suppose you add a reference to an assembly that contains a class named `MathClass`, which has a new function named `SquareRoot`, as shown in the following code:</span></span>  
  
 [!code-vb[VbVbalrOOP#53](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]  
  
 <span data-ttu-id="27975-119">Aplikacja może używać formantów pól tekstowych do argumentów i kontroli, która metoda zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="27975-119">Your application could use text box controls to control which method will be called and its arguments.</span></span> <span data-ttu-id="27975-120">Na przykład jeśli `TextBox1` zawiera wyrażenie, które ma zostać obliczone i `TextBox2` jest używana, wprowadź nazwę funkcji, można użyć poniższego kodu do wywołania `SquareRoot` funkcji na wyrażeniu w `TextBox1`:</span><span class="sxs-lookup"><span data-stu-id="27975-120">For example, if `TextBox1` contains the expression to be evaluated, and `TextBox2` is used to enter the name of the function, you can use the following code to invoke the `SquareRoot` function on the expression in `TextBox1`:</span></span>  
  
 [!code-vb[VbVbalrOOP#54](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]  
  
 <span data-ttu-id="27975-121">Po wprowadzeniu "64" w `TextBox1`, "SquareRoot" w `TextBox2`, a następnie wywołać `CallMath` procedury, pierwiastek kwadratowy liczby w `TextBox1` jest obliczane.</span><span class="sxs-lookup"><span data-stu-id="27975-121">If you enter "64" in `TextBox1`, "SquareRoot" in `TextBox2`, and then call the `CallMath` procedure, the square root of the number in `TextBox1` is evaluated.</span></span> <span data-ttu-id="27975-122">Kod w przykładzie wywołuje `SquareRoot` funkcji (który przyjmuje ciąg, który zawiera wyrażenie, które ma być traktowane jako wymagany argument) i zwraca "8" w `TextBox1` (pierwiastek kwadratowy liczby 64).</span><span class="sxs-lookup"><span data-stu-id="27975-122">The code in the example invokes the `SquareRoot` function (which takes a string that contains the expression to be evaluated as a required argument) and returns "8" in `TextBox1` (the square root of 64).</span></span> <span data-ttu-id="27975-123">Oczywiście, jeśli użytkownik wprowadzi nieprawidłowy ciąg w `TextBox2`, jeśli ciąg zawiera nazwę właściwości zamiast metody lub metody, gdyby dodatkowe wymaganego argumentu, występuje błąd w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="27975-123">Of course, if the user enters an invalid string in `TextBox2`, if the string contains the name of a property instead of a method, or if the method had an additional required argument, a run-time error occurs.</span></span> <span data-ttu-id="27975-124">Należy dodać niezawodne kodu obsługi błędu, gdy używasz `CallByName` przewidywania te lub inne błędy.</span><span class="sxs-lookup"><span data-stu-id="27975-124">You have to add robust error-handling code when you use `CallByName` to anticipate these or any other errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27975-125">Gdy `CallByName` funkcja może być przydatna w niektórych przypadkach, należy porównać przydatności przed jego wpływu na wydajność — przy użyciu `CallByName` do wywołania procedury jest nieco wolniej niż wywołania z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="27975-125">While the `CallByName` function may be useful in some cases, you must weigh its usefulness against the performance implications — using `CallByName` to invoke a procedure is slightly slower than a late-bound call.</span></span> <span data-ttu-id="27975-126">Jeśli są wywoływania funkcji wywoływanej cyklicznie, takie jak wewnątrz pętli, `CallByName` mogą mieć poważny wpływ na wydajność.</span><span class="sxs-lookup"><span data-stu-id="27975-126">If you are invoking a function that is called repeatedly, such as inside a loop, `CallByName` can have a severe effect on performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27975-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27975-127">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>  
 [<span data-ttu-id="27975-128">Określanie typu obiektu</span><span class="sxs-lookup"><span data-stu-id="27975-128">Determining Object Type</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)
