---
title: "CType — Funkcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d804ce75929592675068fdc434a1ba7429fa5373
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="01ee1-102">CType — Funkcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01ee1-102">CType Function (Visual Basic)</span></span>
<span data-ttu-id="01ee1-103">Zwraca wynik jawnej konwersji wyrażenia do określonego typu danych, obiektu, struktury, klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="01ee1-103">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01ee1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="01ee1-104">Syntax</span></span>  
  
```  
CType(expression, typename)  
```  
  
## <a name="parts"></a><span data-ttu-id="01ee1-105">Części</span><span class="sxs-lookup"><span data-stu-id="01ee1-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="01ee1-106">Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="01ee1-106">Any valid expression.</span></span> <span data-ttu-id="01ee1-107">Jeśli wartość `expression` znajduje się poza zakresem dozwolone przez `typename`, Visual Basic zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="01ee1-107">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>  
  
 `typename`  
 <span data-ttu-id="01ee1-108">Dowolne wyrażenie, które jest dozwolony w `As` w klauzuli `Dim` instrukcji, oznacza to, że nazwa dowolnego typu danych, obiektu, struktury, klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="01ee1-108">Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01ee1-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01ee1-109">Remarks</span></span>  
  
> [!TIP]
>  <span data-ttu-id="01ee1-110">Aby dokonać konwersji typu można także użyć następujących funkcji:</span><span class="sxs-lookup"><span data-stu-id="01ee1-110">You can also use the following functions to perform a type conversion:</span></span>  
>   
>  -   <span data-ttu-id="01ee1-111">Funkcje konwersji wpisz na przykład `CByte`, `CDbl`, i `CInt` który wykonania konwersji na typ danych.</span><span class="sxs-lookup"><span data-stu-id="01ee1-111">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="01ee1-112">Aby uzyskać więcej informacji, zobacz [funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="01ee1-112">For more information, see [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
> -   <span data-ttu-id="01ee1-113">[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) lub [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="01ee1-113">[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span> <span data-ttu-id="01ee1-114">Operatory te wymagają, że jeden typ dziedziczył lub implementował z innego typu.</span><span class="sxs-lookup"><span data-stu-id="01ee1-114">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="01ee1-115">Udostępniają one nieco większą wydajność niż `CType` podczas konwersji do i z `Object` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="01ee1-115">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>  
  
 <span data-ttu-id="01ee1-116">`CType`jest skompilowany w tekście, co oznacza, że kod konwersji jest częścią kodu, który wylicza wartość wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="01ee1-116">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="01ee1-117">W niektórych przypadkach kod działa szybciej, ponieważ nie procedur są wywoływane w celu wykonania konwersji.</span><span class="sxs-lookup"><span data-stu-id="01ee1-117">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>  
  
 <span data-ttu-id="01ee1-118">Jeśli zdefiniowano brak konwersji z `expression` do `typename` (na przykład z `Integer` do `Date`), Visual Basic wyświetla komunikat o błędzie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="01ee1-118">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>  
  
 <span data-ttu-id="01ee1-119">W przypadku niepowodzenia konwersji w czasie wykonywania odpowiednich wyjątku.</span><span class="sxs-lookup"><span data-stu-id="01ee1-119">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="01ee1-120">W przypadku niepowodzenia konwersji zawężającej <xref:System.OverflowException> powstaje na podstawie najczęściej.</span><span class="sxs-lookup"><span data-stu-id="01ee1-120">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="01ee1-121">Jeśli zdefiniowano konwersji <xref:System.InvalidCastException> w zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="01ee1-121">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="01ee1-122">Na przykład, to może nastąpić, jeśli `expression` jest typu `Object` i jej typ środowiska wykonawczego nie ma brak konwersji na `typename`.</span><span class="sxs-lookup"><span data-stu-id="01ee1-122">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>  
  
 <span data-ttu-id="01ee1-123">Jeśli typ danych miary `expression` lub `typename` jest klasy lub struktury, zdefiniowany przez użytkownika, można zdefiniować `CType` dla tej klasy lub struktury jako operatora konwersji.</span><span class="sxs-lookup"><span data-stu-id="01ee1-123">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="01ee1-124">Dzięki temu `CType` pełnienie *Przeciążony operator*.</span><span class="sxs-lookup"><span data-stu-id="01ee1-124">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="01ee1-125">Jeśli to zrobisz, można kontrolować zachowanie konwersje do i z klasy lub struktury, w tym wyjątki, które mogą być generowane.</span><span class="sxs-lookup"><span data-stu-id="01ee1-125">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="01ee1-126">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="01ee1-126">Overloading</span></span>  
 <span data-ttu-id="01ee1-127">`CType` Również można przeciążać operatora dla klasy lub struktury zdefiniowane poza swój kod.</span><span class="sxs-lookup"><span data-stu-id="01ee1-127">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="01ee1-128">Jeśli kod konwertuje do lub z klasy lub struktury, trzeba koniecznie zapoznać się z zachowaniem jego `CType` operatora.</span><span class="sxs-lookup"><span data-stu-id="01ee1-128">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="01ee1-129">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="01ee1-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="converting-dynamic-objects"></a><span data-ttu-id="01ee1-130">Konwertowanie obiekty dynamiczne</span><span class="sxs-lookup"><span data-stu-id="01ee1-130">Converting Dynamic Objects</span></span>  
 <span data-ttu-id="01ee1-131">Konwersje typów obiektów dynamicznych są wykonywane przez zdefiniowane przez użytkownika konwersje dynamicznych, korzystających z <xref:System.Dynamic.DynamicObject.TryConvert%2A> lub <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="01ee1-131">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="01ee1-132">Jeśli pracujesz z obiektami dynamicznymi, użyj <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> metodę, aby przekonwertować obiekt dynamiczny.</span><span class="sxs-lookup"><span data-stu-id="01ee1-132">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01ee1-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="01ee1-133">Example</span></span>  
 <span data-ttu-id="01ee1-134">W poniższym przykładzie użyto `CType` funkcji konwersji wyrażenia do `Single` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="01ee1-134">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>  
  
 [!code-vb[VbVbalrFunctions#24](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/ctype-function_1.vb)]  
  
 <span data-ttu-id="01ee1-135">Aby uzyskać dodatkowe przykłady, zobacz [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="01ee1-135">For additional examples, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01ee1-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01ee1-136">See Also</span></span>  
 <xref:System.OverflowException>  
 <xref:System.InvalidCastException>  
 [<span data-ttu-id="01ee1-137">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="01ee1-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="01ee1-138">Funkcje konwersji</span><span class="sxs-lookup"><span data-stu-id="01ee1-138">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)  
 [<span data-ttu-id="01ee1-139">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="01ee1-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="01ee1-140">Instrukcje: definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="01ee1-140">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="01ee1-141">Konwersja typów w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="01ee1-141">Type Conversion in the .NET Framework</span></span>](../../../standard/base-types/type-conversion.md)
