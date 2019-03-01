---
title: Pakowanie i rozpakowywanie - C# przewodnik programowania
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
ms.openlocfilehash: 333f8709fa3247be22c068b52e2fa937483acd3b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973109"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="1ca6c-102">Konwersja boxing i konwersja unboxing (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="1ca6c-102">Boxing and Unboxing (C# Programming Guide)</span></span>
<span data-ttu-id="1ca6c-103">OPAKOWYWANIE to proces konwersji [typu wartości](../../../csharp/language-reference/keywords/value-types.md) typowi `object` lub dowolny typ interfejsu implementowany przez ten typ wartości.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-103">Boxing is the process of converting a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="1ca6c-104">Gdy środowisko CLR opakowuje typ wartości, otacza wartość wewnątrz elementu System.Object i zapisuje go w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-104">When the CLR boxes a value type, it wraps the value inside a System.Object and stores it on the managed heap.</span></span> <span data-ttu-id="1ca6c-105">Rozpakowywanie wyodrębnia typ wartości z obiektu.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-105">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="1ca6c-106">OPAKOWYWANIE jest niejawne; Rozpakowywanie jest jawne.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-106">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="1ca6c-107">Pojęcie pakowania i rozpakowywania źródłową C# postrzega system typów, w którym wartość dowolnego typu może być traktowana jako obiekt.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-107">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>  
  
 <span data-ttu-id="1ca6c-108">W poniższym przykładzie zmienna liczba całkowita `i` jest *opakowany* i przypisana do obiektu `o`.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-108">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]  
  
 <span data-ttu-id="1ca6c-109">Obiekt `o` może następnie być rozpakowany i przypisany do zmiennej całkowitej `i`:</span><span class="sxs-lookup"><span data-stu-id="1ca6c-109">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]  
  
 <span data-ttu-id="1ca6c-110">Poniższe przykłady ilustrują, jak pakowanie jest używane w języku C#.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-110">The following examples illustrate how boxing is used in C#.</span></span>  
  
 [!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]  
  
## <a name="performance"></a><span data-ttu-id="1ca6c-111">Wydajność</span><span class="sxs-lookup"><span data-stu-id="1ca6c-111">Performance</span></span>  
 <span data-ttu-id="1ca6c-112">Stosunku do prostych zadań pakowanie i rozpakowywanie są obciążającymi procesami.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-112">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="1ca6c-113">Gdy typ wartości jest zapakowany, nowy obiekt musi być przydzielane i zbudowane.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-113">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="1ca6c-114">W mniejszym stopniu cast wymagany do rozpakowywania również jest kosztowne praktyce.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-114">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="1ca6c-115">Aby uzyskać więcej informacji, zobacz [wydajności](../../../../docs/framework/performance/performance-tips.md).</span><span class="sxs-lookup"><span data-stu-id="1ca6c-115">For more information, see [Performance](../../../../docs/framework/performance/performance-tips.md).</span></span>  
  
## <a name="boxing"></a><span data-ttu-id="1ca6c-116">Boxing</span><span class="sxs-lookup"><span data-stu-id="1ca6c-116">Boxing</span></span>  
 <span data-ttu-id="1ca6c-117">OPAKOWYWANIE służy do przechowywania typów wartości w stosie zebranych elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-117">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="1ca6c-118">OPAKOWYWANIE to niejawna konwersja [typu wartości](../../../csharp/language-reference/keywords/value-types.md) typowi `object` lub dowolny typ interfejsu implementowany przez ten typ wartości.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-118">Boxing is an implicit conversion of a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="1ca6c-119">Opakowanie typu wartości przydziela wystąpienie obiektu do stosu i kopiuje wartość do nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-119">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>  
  
 <span data-ttu-id="1ca6c-120">Rozważmy następującą deklarację zmiennej typu wartości:</span><span class="sxs-lookup"><span data-stu-id="1ca6c-120">Consider the following declaration of a value-type variable:</span></span>  
  
 [!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]  
  
 <span data-ttu-id="1ca6c-121">Poniższa instrukcja stosuje niejawnie operację pakowania na zmiennej `i`:</span><span class="sxs-lookup"><span data-stu-id="1ca6c-121">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]  
  
 <span data-ttu-id="1ca6c-122">Wyniku tego instrukcja tworzy odwołanie do obiektu `o`, na stosie, który odwołuje się do wartości typu `int`, na stosie.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-122">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="1ca6c-123">Ta wartość jest kopią wartości Typ-wartość przypisana do zmiennej `i`.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-123">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="1ca6c-124">Różnica między dwiema zmiennymi `i` i `o`, przedstawiono na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-124">The difference between the two variables, `i` and `o`, is illustrated in the following figure.</span></span>  
  
 <span data-ttu-id="1ca6c-125">![BoxingConversion — grafika](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")</span><span class="sxs-lookup"><span data-stu-id="1ca6c-125">![BoxingConversion graphic](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")</span></span>  
<span data-ttu-id="1ca6c-126">Konwersja boxing</span><span class="sxs-lookup"><span data-stu-id="1ca6c-126">Boxing Conversion</span></span>  
  
 <span data-ttu-id="1ca6c-127">Jest również możliwe przeprowadzenie pakowania, które jawnie jak w poniższym przykładzie, ale jawne pakowanie nigdy nie jest wymagane:</span><span class="sxs-lookup"><span data-stu-id="1ca6c-127">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>  
  
 [!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]  
  
## <a name="description"></a><span data-ttu-id="1ca6c-128">Opis</span><span class="sxs-lookup"><span data-stu-id="1ca6c-128">Description</span></span>  
 <span data-ttu-id="1ca6c-129">Ten przykład konwertuje zmienną całkowitą `i` do obiektu `o` za pomocą pakowania.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-129">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="1ca6c-130">Następnie wartość przechowywana w zmiennej `i` zostało zmienione z `123` do `456`.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-130">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="1ca6c-131">W przykładzie pokazano, że oryginalny typ wartości i spakowany obiekt Użyj lokalizacji pamięci i dlatego mogą przechowywać różne wartości.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-131">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ca6c-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ca6c-132">Example</span></span>  
 [!code-csharp[csProgGuideTypes#16](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_7.cs)]  
  
## <a name="unboxing"></a><span data-ttu-id="1ca6c-133">Rozpakowywanie</span><span class="sxs-lookup"><span data-stu-id="1ca6c-133">Unboxing</span></span>  
 <span data-ttu-id="1ca6c-134">Rozpakowywanie to konwersja jawna z typu `object` do [typu wartości](../../../csharp/language-reference/keywords/value-types.md) lub z typu interfejsu na typ wartości, która implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-134">Unboxing is an explicit conversion from the type `object` to a [value type](../../../csharp/language-reference/keywords/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="1ca6c-135">Operacja rozpakowania składa się z:</span><span class="sxs-lookup"><span data-stu-id="1ca6c-135">An unboxing operation consists of:</span></span>  
  
-   <span data-ttu-id="1ca6c-136">Sprawdzanie wystąpienie obiektu, aby upewnić się, że jest zapakowaną wartością danego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-136">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>  
  
-   <span data-ttu-id="1ca6c-137">Kopiowanie wartości z instancji do zmiennej typu wartości.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-137">Copying the value from the instance into the value-type variable.</span></span>  
  
 <span data-ttu-id="1ca6c-138">Następujące instrukcje pokazują zarówno pakowania, jak i rozpakowania operacje:</span><span class="sxs-lookup"><span data-stu-id="1ca6c-138">The following statements demonstrate both boxing and unboxing operations:</span></span>  
  
 [!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]  
  
 <span data-ttu-id="1ca6c-139">Następujący rysunek ilustruje wynik poprzednich instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-139">The following figure demonstrates the result of the previous statements.</span></span>  
  
 <span data-ttu-id="1ca6c-140">![Grafika przedstawiająca konwersję unBoxing](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")</span><span class="sxs-lookup"><span data-stu-id="1ca6c-140">![UnBoxing Conversion graphic](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")</span></span>  
<span data-ttu-id="1ca6c-141">Konwersja rozpakowująca</span><span class="sxs-lookup"><span data-stu-id="1ca6c-141">Unboxing Conversion</span></span>  
  
 <span data-ttu-id="1ca6c-142">Dla rozpakowywania typów wartości, które zakończyło się sukcesem w czasie wykonywania, rozpakowywany element musi być odwołaniem do obiektu, który został wcześniej utworzony przez pakowanie instancji tego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-142">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="1ca6c-143">Próba rozpakowania `null` powoduje, że <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-143">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="1ca6c-144">Próba rozpakowania odwołania do niezgodną wartość typu powoduje, że <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-144">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ca6c-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ca6c-145">Example</span></span>  
 <span data-ttu-id="1ca6c-146">Poniższy przykład ilustruje przypadek nieprawidłowy Rozpakowywanie i wynikowy `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-146">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="1ca6c-147">Za pomocą `try` i `catch`, komunikat o błędzie jest wyświetlany, gdy wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="1ca6c-147">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>  
  
 [!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]  
  
 <span data-ttu-id="1ca6c-148">Ten program wyświetla:</span><span class="sxs-lookup"><span data-stu-id="1ca6c-148">This program outputs:</span></span>  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 <span data-ttu-id="1ca6c-149">Jeśli zmienisz instrukcję:</span><span class="sxs-lookup"><span data-stu-id="1ca6c-149">If you change the statement:</span></span>  
  
```csharp
int j = (short) o;  
```  
  
 <span data-ttu-id="1ca6c-150">na:</span><span class="sxs-lookup"><span data-stu-id="1ca6c-150">to:</span></span>  
  
```csharp
int j = (int) o;  
```  
  
 <span data-ttu-id="1ca6c-151">Konwersja zostanie przeprowadzona i otrzymasz dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="1ca6c-151">the conversion will be performed, and you will get the output:</span></span>  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="1ca6c-152">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1ca6c-152">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a><span data-ttu-id="1ca6c-153">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="1ca6c-153">Related Sections</span></span>  
 <span data-ttu-id="1ca6c-154">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="1ca6c-154">For more information:</span></span>  
  
-   [<span data-ttu-id="1ca6c-155">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="1ca6c-155">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="1ca6c-156">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="1ca6c-156">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="see-also"></a><span data-ttu-id="1ca6c-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ca6c-157">See also</span></span>

- [<span data-ttu-id="1ca6c-158">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1ca6c-158">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
