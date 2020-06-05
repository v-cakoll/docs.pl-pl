---
title: CType — Funkcja
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 88d609146648fe1b0c3124b99a65e85293fc0707
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406433"
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="4bb23-102">CType — Funkcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4bb23-102">CType Function (Visual Basic)</span></span>

<span data-ttu-id="4bb23-103">Zwraca wynik jawnej konwersji wyrażenia do określonego typu danych, obiektu, struktury, klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4bb23-103">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="4bb23-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4bb23-104">Syntax</span></span>

```vb
CType(expression, typename)
```

## <a name="parts"></a><span data-ttu-id="4bb23-105">Części</span><span class="sxs-lookup"><span data-stu-id="4bb23-105">Parts</span></span>

<span data-ttu-id="4bb23-106">`expression`Dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="4bb23-106">`expression` Any valid expression.</span></span> <span data-ttu-id="4bb23-107">Jeśli wartość `expression` znajduje się poza zakresem dozwolonym przez `typename` , Visual Basic zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="4bb23-107">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>

<span data-ttu-id="4bb23-108">`typename`Dowolne wyrażenie, które jest dozwolone w `As` klauzuli w `Dim` instrukcji, czyli nazwę dowolnego typu danych, obiektu, struktury, klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4bb23-108">`typename` Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>

## <a name="remarks"></a><span data-ttu-id="4bb23-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4bb23-109">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="4bb23-110">Aby przeprowadzić konwersję typu, można również użyć następujących funkcji:</span><span class="sxs-lookup"><span data-stu-id="4bb23-110">You can also use the following functions to perform a type conversion:</span></span>
>
> - <span data-ttu-id="4bb23-111">Wpisz funkcje konwersji, takie jak `CByte` , `CDbl` , i wykonując `CInt` konwersję do określonego typu danych.</span><span class="sxs-lookup"><span data-stu-id="4bb23-111">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="4bb23-112">Aby uzyskać więcej informacji, zobacz [funkcje konwersji typów](type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="4bb23-112">For more information, see [Type Conversion Functions](type-conversion-functions.md).</span></span>
> - <span data-ttu-id="4bb23-113">[Operator DirectCast](../operators/directcast-operator.md) lub [operator TryCast](../operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="4bb23-113">[DirectCast Operator](../operators/directcast-operator.md) or [TryCast Operator](../operators/trycast-operator.md).</span></span> <span data-ttu-id="4bb23-114">Operatory te wymagają, aby jeden typ dziedziczył z lub zaimplementował inny typ.</span><span class="sxs-lookup"><span data-stu-id="4bb23-114">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="4bb23-115">Mogą one zapewnić nieco lepszą wydajność niż `CType` podczas konwersji do i z `Object` typu danych.</span><span class="sxs-lookup"><span data-stu-id="4bb23-115">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>

<span data-ttu-id="4bb23-116">`CType`jest kompilowany w tekście, co oznacza, że kod konwersji jest częścią kodu, który szacuje wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="4bb23-116">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="4bb23-117">W niektórych przypadkach kod działa szybciej, ponieważ żadne procedury nie są wywoływane w celu przeprowadzenia konwersji.</span><span class="sxs-lookup"><span data-stu-id="4bb23-117">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>

<span data-ttu-id="4bb23-118">Jeśli konwersja nie jest zdefiniowana z `expression` do `typename` (na przykład z `Integer` do `Date` ), Visual Basic wyświetla komunikat o błędzie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4bb23-118">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>

<span data-ttu-id="4bb23-119">Jeśli konwersja nie powiedzie się w czasie wykonywania, zostanie zgłoszony odpowiedni wyjątek.</span><span class="sxs-lookup"><span data-stu-id="4bb23-119">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="4bb23-120">Jeśli konwersja nie powiedzie się, <xref:System.OverflowException> jest to najbardziej typowy wynik.</span><span class="sxs-lookup"><span data-stu-id="4bb23-120">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="4bb23-121">Jeśli konwersja jest niezdefiniowana, <xref:System.InvalidCastException> w zgłoszonych.</span><span class="sxs-lookup"><span data-stu-id="4bb23-121">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="4bb23-122">Na przykład może się tak zdarzyć, jeśli `expression` jest typu `Object` , a jego typ czasu wykonywania nie ma konwersji na `typename` .</span><span class="sxs-lookup"><span data-stu-id="4bb23-122">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>

<span data-ttu-id="4bb23-123">Jeśli typem danych `expression` lub `typename` jest zdefiniowana Klasa lub struktura, można zdefiniować `CType` dla tej klasy lub struktury jako operator konwersji.</span><span class="sxs-lookup"><span data-stu-id="4bb23-123">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="4bb23-124">Dzięki temu `CType` działa jako *przeciążony operator*.</span><span class="sxs-lookup"><span data-stu-id="4bb23-124">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="4bb23-125">W takim przypadku można kontrolować zachowanie konwersji do i z klasy lub struktury, łącznie z wyjątkami, które mogą być zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="4bb23-125">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>

## <a name="overloading"></a><span data-ttu-id="4bb23-126">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="4bb23-126">Overloading</span></span>

<span data-ttu-id="4bb23-127">`CType`Operator może być również przeciążony na klasie lub strukturze zdefiniowanej poza kodem.</span><span class="sxs-lookup"><span data-stu-id="4bb23-127">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="4bb23-128">Jeśli kod jest konwertowany na lub z takiej klasy lub struktury, upewnij się, że rozumiesz zachowanie jego `CType` operatora.</span><span class="sxs-lookup"><span data-stu-id="4bb23-128">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="4bb23-129">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="4bb23-129">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="converting-dynamic-objects"></a><span data-ttu-id="4bb23-130">Konwertowanie obiektów dynamicznych</span><span class="sxs-lookup"><span data-stu-id="4bb23-130">Converting Dynamic Objects</span></span>

<span data-ttu-id="4bb23-131">Konwersje typów obiektów dynamicznych są wykonywane przez zdefiniowane przez użytkownika Konwersje dynamiczne, które używają <xref:System.Dynamic.DynamicObject.TryConvert%2A> metod lub <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> .</span><span class="sxs-lookup"><span data-stu-id="4bb23-131">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="4bb23-132">Jeśli pracujesz z obiektami dynamicznymi, użyj <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> metody do przekonwertowania obiektu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="4bb23-132">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>

## <a name="example"></a><span data-ttu-id="4bb23-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="4bb23-133">Example</span></span>

<span data-ttu-id="4bb23-134">Poniższy przykład używa funkcji, `CType` Aby przekonwertować wyrażenie na `Single` Typ danych.</span><span class="sxs-lookup"><span data-stu-id="4bb23-134">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

<span data-ttu-id="4bb23-135">Aby uzyskać więcej przykładów, zobacz [konwersje niejawne i jawne](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="4bb23-135">For additional examples, see [Implicit and Explicit Conversions](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4bb23-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4bb23-136">See also</span></span>

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [<span data-ttu-id="4bb23-137">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="4bb23-137">Type Conversion Functions</span></span>](type-conversion-functions.md)
- [<span data-ttu-id="4bb23-138">Funkcje konwersji</span><span class="sxs-lookup"><span data-stu-id="4bb23-138">Conversion Functions</span></span>](conversion-functions.md)
- [<span data-ttu-id="4bb23-139">Operator — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="4bb23-139">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="4bb23-140">Instrukcje: definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="4bb23-140">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="4bb23-141">Konwersja typów w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4bb23-141">Type Conversion in the .NET Framework</span></span>](../../../standard/base-types/type-conversion.md)
