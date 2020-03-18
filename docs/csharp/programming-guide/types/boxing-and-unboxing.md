---
title: Boks i unboxing - Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: 62df08bf4ae3580e9b8d5b3aab0697d396674ca1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76745414"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="8e240-102">Konwersja boxing i konwersja unboxing (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="8e240-102">Boxing and Unboxing (C# Programming Guide)</span></span>

<span data-ttu-id="8e240-103">Boks jest procesem konwertowania [typu](../../language-reference/builtin-types/value-types.md) wartości `object` na typ lub dowolny typ interfejsu zaimplementowany przez ten typ wartości.</span><span class="sxs-lookup"><span data-stu-id="8e240-103">Boxing is the process of converting a [value type](../../language-reference/builtin-types/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="8e240-104">Gdy program CLR (Common Language runtime) zawiera wartość, zawija wartość wewnątrz <xref:System.Object?displayProperty=nameWithType> wystąpienia i przechowuje ją na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="8e240-104">When the common language runtime (CLR) boxes a value type, it wraps the value inside a <xref:System.Object?displayProperty=nameWithType> instance and stores it on the managed heap.</span></span> <span data-ttu-id="8e240-105">Rozpakowywanie wyodrębnia typ wartości z obiektu.</span><span class="sxs-lookup"><span data-stu-id="8e240-105">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="8e240-106">Boks jest niejawny; unboxing jest jawny.</span><span class="sxs-lookup"><span data-stu-id="8e240-106">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="8e240-107">Pojęcie boksu i rozpakowywania leży u podstaw zunifikowanego widoku c# systemu typów, w którym wartość dowolnego typu może być traktowana jako obiekt.</span><span class="sxs-lookup"><span data-stu-id="8e240-107">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>

<span data-ttu-id="8e240-108">W poniższym przykładzie zmienna `i` całkowita jest *zapakowana* i przypisana do obiektu `o`.</span><span class="sxs-lookup"><span data-stu-id="8e240-108">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>

[!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]

<span data-ttu-id="8e240-109">Obiekt `o` można następnie rozpakować i przypisać do `i`zmiennej całkowitej:</span><span class="sxs-lookup"><span data-stu-id="8e240-109">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>

[!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]

<span data-ttu-id="8e240-110">Poniższe przykłady ilustrują sposób, w jaki boks jest używany w języku C#.</span><span class="sxs-lookup"><span data-stu-id="8e240-110">The following examples illustrate how boxing is used in C#.</span></span>

[!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]

## <a name="performance"></a><span data-ttu-id="8e240-111">Wydajność</span><span class="sxs-lookup"><span data-stu-id="8e240-111">Performance</span></span>

<span data-ttu-id="8e240-112">W odniesieniu do prostych zadań, boks i rozpakowywanie są obliczeniowo kosztownymi procesami.</span><span class="sxs-lookup"><span data-stu-id="8e240-112">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="8e240-113">Gdy typ wartości jest zapakowany, nowy obiekt musi zostać przydzielony i skonstruowany.</span><span class="sxs-lookup"><span data-stu-id="8e240-113">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="8e240-114">W mniejszym stopniu, oddanych wymaganych do unboxing jest również drogie obliczeniowo.</span><span class="sxs-lookup"><span data-stu-id="8e240-114">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="8e240-115">Aby uzyskać więcej informacji, zobacz [Wydajność](../../../framework/performance/performance-tips.md).</span><span class="sxs-lookup"><span data-stu-id="8e240-115">For more information, see [Performance](../../../framework/performance/performance-tips.md).</span></span>

## <a name="boxing"></a><span data-ttu-id="8e240-116">Boxing</span><span class="sxs-lookup"><span data-stu-id="8e240-116">Boxing</span></span>

<span data-ttu-id="8e240-117">Boks służy do przechowywania typów wartości w stercie zebrane jut.</span><span class="sxs-lookup"><span data-stu-id="8e240-117">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="8e240-118">Boks jest niejawną konwersją typu `object` [wartości](../../language-reference/builtin-types/value-types.md) na typ lub dowolny typ interfejsu zaimplementowany przez ten typ wartości.</span><span class="sxs-lookup"><span data-stu-id="8e240-118">Boxing is an implicit conversion of a [value type](../../language-reference/builtin-types/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="8e240-119">Boksuje typ wartości przydziela wystąpienie obiektu na stercie i kopiuje wartość do nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="8e240-119">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>

<span data-ttu-id="8e240-120">Należy wziąć pod uwagę następującą deklarację zmiennej typu wartości:</span><span class="sxs-lookup"><span data-stu-id="8e240-120">Consider the following declaration of a value-type variable:</span></span>

[!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]

<span data-ttu-id="8e240-121">Następująca instrukcja niejawnie stosuje operację bokserską na zmiennej: `i`</span><span class="sxs-lookup"><span data-stu-id="8e240-121">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>

[!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]

<span data-ttu-id="8e240-122">Wynikiem tej instrukcji jest tworzenie `o`odwołania do obiektu , na stosie, który odwołuje się do wartości typu `int`, na stercie.</span><span class="sxs-lookup"><span data-stu-id="8e240-122">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="8e240-123">Ta wartość jest kopią wartości typu przypisanej `i`do zmiennej .</span><span class="sxs-lookup"><span data-stu-id="8e240-123">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="8e240-124">Różnica między dwiema `i` zmiennymi, i `o`, jest zilustrowana na poniższym obrazie konwersji bokserskiej:</span><span class="sxs-lookup"><span data-stu-id="8e240-124">The difference between the two variables, `i` and `o`, is illustrated in the following image of boxing conversion:</span></span>

![Grafika pokazująca różnicę między zmiennymi i i i o.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)

<span data-ttu-id="8e240-126">Możliwe jest również jawnie wykonywanie boksu, jak w poniższym przykładzie, ale jawne boks nigdy nie jest wymagane:</span><span class="sxs-lookup"><span data-stu-id="8e240-126">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>

[!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]

## <a name="description"></a><span data-ttu-id="8e240-127">Opis</span><span class="sxs-lookup"><span data-stu-id="8e240-127">Description</span></span>

<span data-ttu-id="8e240-128">W tym przykładzie konwertuje zmienną `i` całkowitą na obiekt `o` przy użyciu boksu.</span><span class="sxs-lookup"><span data-stu-id="8e240-128">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="8e240-129">Następnie wartość przechowywana w `i` zmiennej `123` `456`zostanie zmieniona z na .</span><span class="sxs-lookup"><span data-stu-id="8e240-129">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="8e240-130">W przykładzie pokazano, że oryginalny typ wartości i obiekt w pudełku używają oddzielnych lokalizacji pamięci i dlatego mogą przechowywać różne wartości.</span><span class="sxs-lookup"><span data-stu-id="8e240-130">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>

## <a name="example"></a><span data-ttu-id="8e240-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="8e240-131">Example</span></span>

[!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]

## <a name="unboxing"></a><span data-ttu-id="8e240-132">Unboxing</span><span class="sxs-lookup"><span data-stu-id="8e240-132">Unboxing</span></span>

<span data-ttu-id="8e240-133">Unboxing jest jawną konwersją z typu `object` na typ [wartości](../../language-reference/builtin-types/value-types.md) lub z typu interfejsu do typu wartości, który implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="8e240-133">Unboxing is an explicit conversion from the type `object` to a [value type](../../language-reference/builtin-types/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="8e240-134">Operacja rozpakowywania składa się z:</span><span class="sxs-lookup"><span data-stu-id="8e240-134">An unboxing operation consists of:</span></span>

- <span data-ttu-id="8e240-135">Sprawdzanie wystąpienia obiektu, aby upewnić się, że jest to wartość zapakowana danego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="8e240-135">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>

- <span data-ttu-id="8e240-136">Kopiowanie wartości z wystąpienia do zmiennej typu wartości.</span><span class="sxs-lookup"><span data-stu-id="8e240-136">Copying the value from the instance into the value-type variable.</span></span>

<span data-ttu-id="8e240-137">Następujące instrukcje pokazują operacje bokserskie i rozpakowywania:</span><span class="sxs-lookup"><span data-stu-id="8e240-137">The following statements demonstrate both boxing and unboxing operations:</span></span>

[!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]

<span data-ttu-id="8e240-138">Na poniższym rysunku przedstawiono wynik poprzednich instrukcji:</span><span class="sxs-lookup"><span data-stu-id="8e240-138">The following figure demonstrates the result of the previous statements:</span></span>

![Grafika przedstawiająca konwersję rozpakowywania.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)

<span data-ttu-id="8e240-140">Dla rozpakowywania typów wartości, aby odnieść sukces w czasie wykonywania, element jest unboxed musi być odwołanie do obiektu, który został wcześniej utworzony przez bokserskie wystąpienie tego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="8e240-140">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="8e240-141">Próba rozpakowywania `null` <xref:System.NullReferenceException>powoduje .</span><span class="sxs-lookup"><span data-stu-id="8e240-141">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="8e240-142">Próba odpakowania odwołania do niezgodnego typu <xref:System.InvalidCastException>wartości powoduje , że .</span><span class="sxs-lookup"><span data-stu-id="8e240-142">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>

## <a name="example"></a><span data-ttu-id="8e240-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="8e240-143">Example</span></span>

<span data-ttu-id="8e240-144">W poniższym przykładzie przedstawiono przypadek nieprawidłowego unboxing `InvalidCastException`i wynikowy .</span><span class="sxs-lookup"><span data-stu-id="8e240-144">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="8e240-145">Po `try` `catch`wystąpieniu błędu wyświetlany jest komunikat o błędzie i o błędzie.</span><span class="sxs-lookup"><span data-stu-id="8e240-145">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>

[!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]

<span data-ttu-id="8e240-146">Ten program wyprowadza:</span><span class="sxs-lookup"><span data-stu-id="8e240-146">This program outputs:</span></span>

`Specified cast is not valid. Error: Incorrect unboxing.`

<span data-ttu-id="8e240-147">Jeśli zmienisz instrukcję:</span><span class="sxs-lookup"><span data-stu-id="8e240-147">If you change the statement:</span></span>

```csharp
int j = (short) o;
```

<span data-ttu-id="8e240-148">na:</span><span class="sxs-lookup"><span data-stu-id="8e240-148">to:</span></span>

```csharp
int j = (int) o;
```

<span data-ttu-id="8e240-149">konwersja zostanie wykonana, a otrzymasz dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="8e240-149">the conversion will be performed, and you will get the output:</span></span>

`Unboxing OK.`

## <a name="c-language-specification"></a><span data-ttu-id="8e240-150">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8e240-150">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="8e240-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e240-151">See also</span></span>

- [<span data-ttu-id="8e240-152">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8e240-152">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="8e240-153">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="8e240-153">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="8e240-154">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="8e240-154">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
