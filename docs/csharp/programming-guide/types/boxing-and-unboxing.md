---
title: Pakowanie i rozpakowywanie — C# Przewodnik programistyczny
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: 849983bb9cce6c9e0f41247a898747300fd29435
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588536"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="41678-102">Konwersja boxing i konwersja unboxing (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="41678-102">Boxing and Unboxing (C# Programming Guide)</span></span>
<span data-ttu-id="41678-103">Opakowanie to proces konwersji [typu wartości](../../language-reference/keywords/value-types.md) na typ `object` lub dowolny typ interfejsu implementowany przez ten typ wartości.</span><span class="sxs-lookup"><span data-stu-id="41678-103">Boxing is the process of converting a [value type](../../language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="41678-104">Gdy środowisko CLR pola typu wartości, zawija wartość wewnątrz <xref:System.Object?displayProperty=nameWithType> wystąpienia i zapisuje je na stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="41678-104">When the CLR boxes a value type, it wraps the value inside a <xref:System.Object?displayProperty=nameWithType> instance and stores it on the managed heap.</span></span> <span data-ttu-id="41678-105">Rozpakowywanie wyodrębnia typ wartości z obiektu.</span><span class="sxs-lookup"><span data-stu-id="41678-105">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="41678-106">Opakowanie jest niejawne; Rozpakowywanie jest jawne.</span><span class="sxs-lookup"><span data-stu-id="41678-106">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="41678-107">Pojęcie opakowania i rozpakowywanie opiera się na C# ujednoliconym widoku systemu typów, w którym wartość dowolnego typu może być traktowana jako obiekt.</span><span class="sxs-lookup"><span data-stu-id="41678-107">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>  
  
 <span data-ttu-id="41678-108">W poniższym przykładzie zmienna `i` Integer jest *opakowana* i przypisana do obiektu. `o`</span><span class="sxs-lookup"><span data-stu-id="41678-108">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]  
  
 <span data-ttu-id="41678-109">Obiekt `o` może być następnie nieopakowany i przypisany do zmiennej `i`całkowitej:</span><span class="sxs-lookup"><span data-stu-id="41678-109">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]  
  
 <span data-ttu-id="41678-110">W poniższych przykładach pokazano, jak opakowanie jest używane C#w programie.</span><span class="sxs-lookup"><span data-stu-id="41678-110">The following examples illustrate how boxing is used in C#.</span></span>  
  
 [!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]  
  
## <a name="performance"></a><span data-ttu-id="41678-111">Wydajność</span><span class="sxs-lookup"><span data-stu-id="41678-111">Performance</span></span>  
 <span data-ttu-id="41678-112">W odniesieniu do prostych przydziałów, opakowanie i rozpakowywanie są w sposób obliczeniowy kosztowny.</span><span class="sxs-lookup"><span data-stu-id="41678-112">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="41678-113">Gdy typ wartości jest opakowany, nowy obiekt musi być przydzielony i skonstruowany.</span><span class="sxs-lookup"><span data-stu-id="41678-113">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="41678-114">W mniejszym stopniu rzutowanie wymagane do rozpakowywania jest również kosztowne w praktyce.</span><span class="sxs-lookup"><span data-stu-id="41678-114">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="41678-115">Aby uzyskać więcej informacji, zobacz [wydajność](../../../framework/performance/performance-tips.md).</span><span class="sxs-lookup"><span data-stu-id="41678-115">For more information, see [Performance](../../../framework/performance/performance-tips.md).</span></span>  
  
## <a name="boxing"></a><span data-ttu-id="41678-116">Boxing</span><span class="sxs-lookup"><span data-stu-id="41678-116">Boxing</span></span>  
 <span data-ttu-id="41678-117">Opakowanie jest używane do przechowywania typów wartości w stosie zebranych elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="41678-117">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="41678-118">Opakowanie jest niejawną konwersją [typu wartości](../../language-reference/keywords/value-types.md) na typ `object` lub dowolny typ interfejsu implementowany przez ten typ wartości.</span><span class="sxs-lookup"><span data-stu-id="41678-118">Boxing is an implicit conversion of a [value type](../../language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="41678-119">Opakowanie typu wartości przydziela wystąpienie obiektu na stercie i kopiuje wartość do nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="41678-119">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>  
  
 <span data-ttu-id="41678-120">Rozważmy następującą deklarację zmiennej typu wartości:</span><span class="sxs-lookup"><span data-stu-id="41678-120">Consider the following declaration of a value-type variable:</span></span>  
  
 [!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]  
  
 <span data-ttu-id="41678-121">Poniższa instrukcja niejawnie stosuje operację pakowania na zmiennej `i`:</span><span class="sxs-lookup"><span data-stu-id="41678-121">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]  
  
 <span data-ttu-id="41678-122">Wynikiem tej instrukcji jest utworzenie odwołania `o`do obiektu na stosie, który odwołuje się do wartości typu `int`na stercie.</span><span class="sxs-lookup"><span data-stu-id="41678-122">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="41678-123">Ta wartość jest kopią wartości typu wartości przypisanej do zmiennej `i`.</span><span class="sxs-lookup"><span data-stu-id="41678-123">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="41678-124">Różnica między dwoma zmiennymi, `i` a `o`, jest zilustrowana na poniższej ilustracji konwersji pakującej:</span><span class="sxs-lookup"><span data-stu-id="41678-124">The difference between the two variables, `i` and `o`, is illustrated in the following image of boxing conversion:</span></span>  
  
 ![Ilustracja przedstawiająca różnicę między zmiennymi i i o.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)    
  
 <span data-ttu-id="41678-126">Istnieje również możliwość, że opakowanie zostało jawnie wykonane, jak w poniższym przykładzie, ale jawne opakowanie nigdy nie jest wymagane:</span><span class="sxs-lookup"><span data-stu-id="41678-126">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>  
  
 [!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]  
  
## <a name="description"></a><span data-ttu-id="41678-127">Opis</span><span class="sxs-lookup"><span data-stu-id="41678-127">Description</span></span>  
 <span data-ttu-id="41678-128">Ten przykład konwertuje zmienną `i` całkowitą na obiekt `o` przy użyciu opakowania.</span><span class="sxs-lookup"><span data-stu-id="41678-128">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="41678-129">Następnie wartość przechowywana w zmiennej `i` zostanie zmieniona z `123` na `456`.</span><span class="sxs-lookup"><span data-stu-id="41678-129">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="41678-130">W przykładzie pokazano, że oryginalny typ wartości i obiekt opakowany używają oddzielnych lokalizacji pamięci, w związku z czym można przechowywać różne wartości.</span><span class="sxs-lookup"><span data-stu-id="41678-130">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41678-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="41678-131">Example</span></span>  
 [!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]  
  
## <a name="unboxing"></a><span data-ttu-id="41678-132">Rozpakowywanie</span><span class="sxs-lookup"><span data-stu-id="41678-132">Unboxing</span></span>  
 <span data-ttu-id="41678-133">Rozpakowywanie jest jawną konwersją z typu `object` na [Typ wartości](../../language-reference/keywords/value-types.md) lub z typu interfejsu do typu wartości, który implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="41678-133">Unboxing is an explicit conversion from the type `object` to a [value type](../../language-reference/keywords/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="41678-134">Odpakowywanie operacji składa się z:</span><span class="sxs-lookup"><span data-stu-id="41678-134">An unboxing operation consists of:</span></span>  
  
- <span data-ttu-id="41678-135">Sprawdzanie wystąpienia obiektu, aby upewnić się, że jest to opakowana wartość danego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="41678-135">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>  
  
- <span data-ttu-id="41678-136">Kopiowanie wartości z wystąpienia do zmiennej typu wartości.</span><span class="sxs-lookup"><span data-stu-id="41678-136">Copying the value from the instance into the value-type variable.</span></span>  
  
 <span data-ttu-id="41678-137">Następujące instrukcje przedstawiają operacje pakowania i rozpakowywania:</span><span class="sxs-lookup"><span data-stu-id="41678-137">The following statements demonstrate both boxing and unboxing operations:</span></span>  
  
 [!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]  
  
 <span data-ttu-id="41678-138">Na poniższej ilustracji przedstawiono wynik poprzednich instrukcji:</span><span class="sxs-lookup"><span data-stu-id="41678-138">The following figure demonstrates the result of the previous statements:</span></span> 
  
 ![Ilustracja przedstawiająca konwersję rozpakowywanie.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)
  
 <span data-ttu-id="41678-140">Aby rozpakowywanie typów wartości zakończyło się pomyślnie w czasie wykonywania, element, który jest rozpakowany, musi być odwołaniem do obiektu, który został wcześniej utworzony przez opakowanie wystąpienia tego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="41678-140">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="41678-141">Próba Unbox `null` <xref:System.NullReferenceException>powoduje.</span><span class="sxs-lookup"><span data-stu-id="41678-141">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="41678-142">Próba Unbox odwołania do niezgodnego typu wartości powoduje wystąpienie <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="41678-142">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41678-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="41678-143">Example</span></span>  
 <span data-ttu-id="41678-144">Poniższy przykład ilustruje przypadek nieprawidłowego rozpakowywania i wyniki `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="41678-144">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="41678-145">Przy `try` użyciu `catch`i, komunikat o błędzie jest wyświetlany po wystąpieniu błędu.</span><span class="sxs-lookup"><span data-stu-id="41678-145">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>  
  
 [!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]  
  
 <span data-ttu-id="41678-146">Ten program wyprowadza:</span><span class="sxs-lookup"><span data-stu-id="41678-146">This program outputs:</span></span>  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 <span data-ttu-id="41678-147">W przypadku zmiany instrukcji:</span><span class="sxs-lookup"><span data-stu-id="41678-147">If you change the statement:</span></span>  
  
```csharp
int j = (short) o;  
```  
  
 <span data-ttu-id="41678-148">na:</span><span class="sxs-lookup"><span data-stu-id="41678-148">to:</span></span>  
  
```csharp
int j = (int) o;  
```  
  
 <span data-ttu-id="41678-149">Konwersja zostanie wykonana i otrzymasz dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="41678-149">the conversion will be performed, and you will get the output:</span></span>  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="41678-150">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="41678-150">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a><span data-ttu-id="41678-151">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="41678-151">Related Sections</span></span>  
 <span data-ttu-id="41678-152">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="41678-152">For more information:</span></span>  
  
- [<span data-ttu-id="41678-153">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="41678-153">Reference Types</span></span>](../../language-reference/keywords/reference-types.md)  
  
- [<span data-ttu-id="41678-154">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="41678-154">Value Types</span></span>](../../language-reference/keywords/value-types.md)  
  
## <a name="see-also"></a><span data-ttu-id="41678-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41678-155">See also</span></span>

- [<span data-ttu-id="41678-156">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="41678-156">C# Programming Guide</span></span>](../index.md)
