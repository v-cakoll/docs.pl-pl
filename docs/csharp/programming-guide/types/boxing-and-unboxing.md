---
title: Pakowanie i rozpakowywanie — C# Przewodnik programistyczny
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: 32156ad0fe4b3dce4371fe757d15f5b8040aaf19
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115851"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="47981-102">Konwersja boxing i konwersja unboxing (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="47981-102">Boxing and Unboxing (C# Programming Guide)</span></span>

<span data-ttu-id="47981-103">Opakowanie to proces konwersji [typu wartości](../../language-reference/keywords/value-types.md) na typ `object` lub na dowolny typ interfejsu implementowany przez ten typ wartości.</span><span class="sxs-lookup"><span data-stu-id="47981-103">Boxing is the process of converting a [value type](../../language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="47981-104">Gdy typ wartości pola środowiska uruchomieniowego języka wspólnego (CLR), zawija wartość wewnątrz instancji <xref:System.Object?displayProperty=nameWithType> i zapisuje ją na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="47981-104">When the common language runtime (CLR) boxes a value type, it wraps the value inside a <xref:System.Object?displayProperty=nameWithType> instance and stores it on the managed heap.</span></span> <span data-ttu-id="47981-105">Rozpakowywanie wyodrębnia typ wartości z obiektu.</span><span class="sxs-lookup"><span data-stu-id="47981-105">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="47981-106">Opakowanie jest niejawne; Rozpakowywanie jest jawne.</span><span class="sxs-lookup"><span data-stu-id="47981-106">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="47981-107">Pojęcie opakowania i rozpakowywanie opiera się na C# ujednoliconym widoku systemu typów, w którym wartość dowolnego typu może być traktowana jako obiekt.</span><span class="sxs-lookup"><span data-stu-id="47981-107">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>

<span data-ttu-id="47981-108">W poniższym przykładzie zmienna Integer `i` jest *opakowana* i przypisana do `o`obiektu.</span><span class="sxs-lookup"><span data-stu-id="47981-108">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>

[!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]

<span data-ttu-id="47981-109">Obiekt `o` może być następnie rozpakowany i przypisany do zmiennej całkowitej `i`:</span><span class="sxs-lookup"><span data-stu-id="47981-109">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>

[!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]

<span data-ttu-id="47981-110">W poniższych przykładach pokazano, jak opakowanie jest używane C#w programie.</span><span class="sxs-lookup"><span data-stu-id="47981-110">The following examples illustrate how boxing is used in C#.</span></span>

[!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]

## <a name="performance"></a><span data-ttu-id="47981-111">Wydajność</span><span class="sxs-lookup"><span data-stu-id="47981-111">Performance</span></span>

<span data-ttu-id="47981-112">W odniesieniu do prostych przydziałów, opakowanie i rozpakowywanie są w sposób obliczeniowy kosztowny.</span><span class="sxs-lookup"><span data-stu-id="47981-112">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="47981-113">Gdy typ wartości jest opakowany, nowy obiekt musi być przydzielony i skonstruowany.</span><span class="sxs-lookup"><span data-stu-id="47981-113">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="47981-114">W mniejszym stopniu rzutowanie wymagane do rozpakowywania jest również kosztowne w praktyce.</span><span class="sxs-lookup"><span data-stu-id="47981-114">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="47981-115">Aby uzyskać więcej informacji, zobacz [wydajność](../../../framework/performance/performance-tips.md).</span><span class="sxs-lookup"><span data-stu-id="47981-115">For more information, see [Performance](../../../framework/performance/performance-tips.md).</span></span>

## <a name="boxing"></a><span data-ttu-id="47981-116">Boxing</span><span class="sxs-lookup"><span data-stu-id="47981-116">Boxing</span></span>

<span data-ttu-id="47981-117">Opakowanie jest używane do przechowywania typów wartości w stosie zebranych elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="47981-117">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="47981-118">Opakowanie jest niejawną konwersją [typu wartości](../../language-reference/keywords/value-types.md) na typ `object` lub do dowolnego typu interfejsu zaimplementowanego przez ten typ wartości.</span><span class="sxs-lookup"><span data-stu-id="47981-118">Boxing is an implicit conversion of a [value type](../../language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="47981-119">Opakowanie typu wartości przydziela wystąpienie obiektu na stercie i kopiuje wartość do nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="47981-119">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>

<span data-ttu-id="47981-120">Rozważmy następującą deklarację zmiennej typu wartości:</span><span class="sxs-lookup"><span data-stu-id="47981-120">Consider the following declaration of a value-type variable:</span></span>

[!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]

<span data-ttu-id="47981-121">Poniższa instrukcja niejawnie stosuje operację pakowania na zmiennej `i`:</span><span class="sxs-lookup"><span data-stu-id="47981-121">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>

[!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]

<span data-ttu-id="47981-122">Wynikiem tej instrukcji jest utworzenie odwołania do obiektu `o`na stosie, który odwołuje się do wartości typu `int`, na stercie.</span><span class="sxs-lookup"><span data-stu-id="47981-122">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="47981-123">Ta wartość jest kopią wartości typu wartości przypisanej do zmiennej `i`.</span><span class="sxs-lookup"><span data-stu-id="47981-123">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="47981-124">Różnica między dwoma zmiennymi, `i` i `o`, przedstawiono na poniższej ilustracji konwersji pakującej:</span><span class="sxs-lookup"><span data-stu-id="47981-124">The difference between the two variables, `i` and `o`, is illustrated in the following image of boxing conversion:</span></span>

![Ilustracja przedstawiająca różnicę między zmiennymi i i o.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)

<span data-ttu-id="47981-126">Istnieje również możliwość, że opakowanie zostało jawnie wykonane, jak w poniższym przykładzie, ale jawne opakowanie nigdy nie jest wymagane:</span><span class="sxs-lookup"><span data-stu-id="47981-126">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>

[!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]

## <a name="description"></a><span data-ttu-id="47981-127">Opis</span><span class="sxs-lookup"><span data-stu-id="47981-127">Description</span></span>

<span data-ttu-id="47981-128">Ten przykład konwertuje zmienną typu Integer `i` do obiektu `o` przy użyciu opakowania.</span><span class="sxs-lookup"><span data-stu-id="47981-128">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="47981-129">Następnie wartość przechowywana w zmiennej `i` jest zmieniana z `123` na `456`.</span><span class="sxs-lookup"><span data-stu-id="47981-129">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="47981-130">W przykładzie pokazano, że oryginalny typ wartości i obiekt opakowany używają oddzielnych lokalizacji pamięci, w związku z czym można przechowywać różne wartości.</span><span class="sxs-lookup"><span data-stu-id="47981-130">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>

## <a name="example"></a><span data-ttu-id="47981-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="47981-131">Example</span></span>

[!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]

## <a name="unboxing"></a><span data-ttu-id="47981-132">Rozpakowywanie</span><span class="sxs-lookup"><span data-stu-id="47981-132">Unboxing</span></span>

<span data-ttu-id="47981-133">Rozpakowywanie jest jawną konwersją z typu `object` do [typu wartości](../../language-reference/keywords/value-types.md) lub z typu interfejsu na typ wartości implementującej interfejs.</span><span class="sxs-lookup"><span data-stu-id="47981-133">Unboxing is an explicit conversion from the type `object` to a [value type](../../language-reference/keywords/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="47981-134">Odpakowywanie operacji składa się z:</span><span class="sxs-lookup"><span data-stu-id="47981-134">An unboxing operation consists of:</span></span>

- <span data-ttu-id="47981-135">Sprawdzanie wystąpienia obiektu, aby upewnić się, że jest to opakowana wartość danego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="47981-135">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>

- <span data-ttu-id="47981-136">Kopiowanie wartości z wystąpienia do zmiennej typu wartości.</span><span class="sxs-lookup"><span data-stu-id="47981-136">Copying the value from the instance into the value-type variable.</span></span>

<span data-ttu-id="47981-137">Następujące instrukcje przedstawiają operacje pakowania i rozpakowywania:</span><span class="sxs-lookup"><span data-stu-id="47981-137">The following statements demonstrate both boxing and unboxing operations:</span></span>

[!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]

<span data-ttu-id="47981-138">Na poniższej ilustracji przedstawiono wynik poprzednich instrukcji:</span><span class="sxs-lookup"><span data-stu-id="47981-138">The following figure demonstrates the result of the previous statements:</span></span>

![Ilustracja przedstawiająca konwersję rozpakowywanie.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)

<span data-ttu-id="47981-140">Aby rozpakowywanie typów wartości zakończyło się pomyślnie w czasie wykonywania, element, który jest rozpakowany, musi być odwołaniem do obiektu, który został wcześniej utworzony przez opakowanie wystąpienia tego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="47981-140">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="47981-141">Próba Unbox `null` powoduje <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="47981-141">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="47981-142">Próba Unbox odwołania do niezgodnego typu wartości powoduje wystąpienie <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="47981-142">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>

## <a name="example"></a><span data-ttu-id="47981-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="47981-143">Example</span></span>

<span data-ttu-id="47981-144">Poniższy przykład ilustruje przypadek nieprawidłowego rozpakowywania i powstające `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="47981-144">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="47981-145">Przy użyciu `try` i `catch`, zostanie wyświetlony komunikat o błędzie po wystąpieniu błędu.</span><span class="sxs-lookup"><span data-stu-id="47981-145">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>

[!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]

<span data-ttu-id="47981-146">Ten program wyprowadza:</span><span class="sxs-lookup"><span data-stu-id="47981-146">This program outputs:</span></span>

`Specified cast is not valid. Error: Incorrect unboxing.`

<span data-ttu-id="47981-147">W przypadku zmiany instrukcji:</span><span class="sxs-lookup"><span data-stu-id="47981-147">If you change the statement:</span></span>

```csharp
int j = (short) o;
```

<span data-ttu-id="47981-148">na:</span><span class="sxs-lookup"><span data-stu-id="47981-148">to:</span></span>

```csharp
int j = (int) o;
```

<span data-ttu-id="47981-149">Konwersja zostanie wykonana i otrzymasz dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="47981-149">the conversion will be performed, and you will get the output:</span></span>

`Unboxing OK.`

## <a name="c-language-specification"></a><span data-ttu-id="47981-150">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="47981-150">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="related-sections"></a><span data-ttu-id="47981-151">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="47981-151">Related sections</span></span>

<span data-ttu-id="47981-152">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="47981-152">For more information:</span></span>

- [<span data-ttu-id="47981-153">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="47981-153">Reference Types</span></span>](../../language-reference/keywords/reference-types.md)

- [<span data-ttu-id="47981-154">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="47981-154">Value Types</span></span>](../../language-reference/keywords/value-types.md)

## <a name="see-also"></a><span data-ttu-id="47981-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47981-155">See also</span></span>

- [<span data-ttu-id="47981-156">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="47981-156">C# Programming Guide</span></span>](../index.md)
