---
title: "Konwersja boxing i konwersja unboxing (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
caps.latest.revision: "34"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 893ef47c5e7522581b5d02489100942e47023a63
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="3b3d9-102">Konwersja boxing i konwersja unboxing (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="3b3d9-102">Boxing and Unboxing (C# Programming Guide)</span></span>
<span data-ttu-id="3b3d9-103">Opakowanie jest proces konwersji [typu wartości](../../../csharp/language-reference/keywords/value-types.md) do typu `object` lub do dowolnego typu interfejsu zaimplementowany przez ten typ wartości.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-103">Boxing is the process of converting a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="3b3d9-104">Gdy CLR pola typu wartości, opakowuje wartość wewnątrz elementu System.Object i zapisze go na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-104">When the CLR boxes a value type, it wraps the value inside a System.Object and stores it on the managed heap.</span></span> <span data-ttu-id="3b3d9-105">Rozpakowywanie wyodrębnia typ wartości z obiektu.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-105">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="3b3d9-106">Opakowanie jest niejawne; Rozpakowywanie jest jawne.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-106">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="3b3d9-107">Pojęcie boxing i konwersja unboxing źródłową widoku unified C# system typów, w którym wartość dowolnego typu może być traktowana jako obiekt.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-107">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>  
  
 <span data-ttu-id="3b3d9-108">W poniższym przykładzie zmienna całkowitoliczbowa `i` jest *opakowany* i przypisany do obiektu `o`.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-108">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#14](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_1.cs)]  
  
 <span data-ttu-id="3b3d9-109">Obiekt `o` może następnie być rozpakowany i przypisane zmienna całkowitoliczbowa `i`:</span><span class="sxs-lookup"><span data-stu-id="3b3d9-109">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#15](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_2.cs)]  
  
 <span data-ttu-id="3b3d9-110">Poniższe przykłady przedstawiają sposób opakowanie jest używana w języku C#.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-110">The following examples illustrate how boxing is used in C#.</span></span>  
  
 [!code-csharp[csProgGuideTypes#47](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_3.cs)]  
  
## <a name="performance"></a><span data-ttu-id="3b3d9-111">Wydajność</span><span class="sxs-lookup"><span data-stu-id="3b3d9-111">Performance</span></span>  
 <span data-ttu-id="3b3d9-112">W odniesieniu do przypisania prostego opakowywanie i rozpakowywanie to procesy praktyce kosztowne.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-112">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="3b3d9-113">Gdy typ wartości jest opakowany, nowy obiekt musi przydzielone i zbudowane.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-113">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="3b3d9-114">W mniejszym stopniu rzutowanie wymagane dla Rozpakowywanie również jest kosztowne praktyce.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-114">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="3b3d9-115">Aby uzyskać więcej informacji, zobacz [wydajności](https://msdn.microsoft.com/library/ms173196(VS.110).aspx).</span><span class="sxs-lookup"><span data-stu-id="3b3d9-115">For more information, see [Performance](https://msdn.microsoft.com/library/ms173196(VS.110).aspx).</span></span>  
  
## <a name="boxing"></a><span data-ttu-id="3b3d9-116">Boxing</span><span class="sxs-lookup"><span data-stu-id="3b3d9-116">Boxing</span></span>  
 <span data-ttu-id="3b3d9-117">Opakowanie jest używany do przechowywania typów wartości w stercie zbierane pamięci.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-117">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="3b3d9-118">Opakowanie jest niejawnej konwersji wartości [typu wartości](../../../csharp/language-reference/keywords/value-types.md) do typu `object` lub do dowolnego typu interfejsu zaimplementowany przez ten typ wartości.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-118">Boxing is an implicit conversion of a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="3b3d9-119">Konwersja boxing typów wartości przydziela wystąpienia obiektów na stercie i skopiowanie wartości do nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-119">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>  
  
 <span data-ttu-id="3b3d9-120">Należy wziąć pod uwagę następujące deklaracja zmiennej typu wartość:</span><span class="sxs-lookup"><span data-stu-id="3b3d9-120">Consider the following declaration of a value-type variable:</span></span>  
  
 [!code-csharp[csProgGuideTypes#17](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_4.cs)]  
  
 <span data-ttu-id="3b3d9-121">Następująca instrukcja niejawnie stosuje operacja opakowanie w zmiennej `i`:</span><span class="sxs-lookup"><span data-stu-id="3b3d9-121">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#18](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_5.cs)]  
  
 <span data-ttu-id="3b3d9-122">Wynik tej instrukcji jest utworzenie odwołania do obiektu `o`, na stosie, który odwołuje się do wartości typu `int`, na stosie.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-122">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="3b3d9-123">Ta wartość jest kopią wartości typu wartość przypisaną do zmiennej `i`.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-123">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="3b3d9-124">Różnica między dwie zmienne `i` i `o`, przedstawiono na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-124">The difference between the two variables, `i` and `o`, is illustrated in the following figure.</span></span>  
  
 <span data-ttu-id="3b3d9-125">![BoxingConversion — grafika](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")</span><span class="sxs-lookup"><span data-stu-id="3b3d9-125">![BoxingConversion graphic](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")</span></span>  
<span data-ttu-id="3b3d9-126">Konwersja boxing</span><span class="sxs-lookup"><span data-stu-id="3b3d9-126">Boxing Conversion</span></span>  
  
 <span data-ttu-id="3b3d9-127">Istnieje również możliwość wykonania konwersji boxing jawnie jak w poniższym przykładzie, ale jawnej konwersji boxing nigdy nie jest wymagane:</span><span class="sxs-lookup"><span data-stu-id="3b3d9-127">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>  
  
 [!code-csharp[csProgGuideTypes#19](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_6.cs)]  
  
## <a name="description"></a><span data-ttu-id="3b3d9-128">Opis</span><span class="sxs-lookup"><span data-stu-id="3b3d9-128">Description</span></span>  
 <span data-ttu-id="3b3d9-129">W tym przykładzie konwertuje zmienna całkowitoliczbowa `i` do obiektu `o` za pomocą konwersji boxing.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-129">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="3b3d9-130">Następnie, wartość przechowywana w zmiennej `i` została zmieniona z `123` do `456`.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-130">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="3b3d9-131">W przykładzie pokazano, że oryginalny typ wartości obiektu spakowanego lokalizacjami osobną pamięć i dlatego mogą przechowywać różne wartości.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-131">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b3d9-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b3d9-132">Example</span></span>  
 [!code-csharp[csProgGuideTypes#16](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_7.cs)]  
  
## <a name="unboxing"></a><span data-ttu-id="3b3d9-133">Rozpakowywanie</span><span class="sxs-lookup"><span data-stu-id="3b3d9-133">Unboxing</span></span>  
 <span data-ttu-id="3b3d9-134">Rozpakowywanie jest jawna konwersja z typu `object` do [typu wartości](../../../csharp/language-reference/keywords/value-types.md) lub z typu interfejsu do typu wartości, który implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-134">Unboxing is an explicit conversion from the type `object` to a [value type](../../../csharp/language-reference/keywords/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="3b3d9-135">Rozpakowywanie operacja obejmuje:</span><span class="sxs-lookup"><span data-stu-id="3b3d9-135">An unboxing operation consists of:</span></span>  
  
-   <span data-ttu-id="3b3d9-136">Sprawdzanie, czy wystąpienie obiektu do upewnij się, że jest wartości spakowanej typu podanej wartości.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-136">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>  
  
-   <span data-ttu-id="3b3d9-137">Kopiowanie wartości z wystąpienia w zmiennej typu wartości.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-137">Copying the value from the instance into the value-type variable.</span></span>  
  
 <span data-ttu-id="3b3d9-138">Poniższe instrukcje pokazują zarówno konwersja boxing i rozpakowywanie operacje:</span><span class="sxs-lookup"><span data-stu-id="3b3d9-138">The following statements demonstrate both boxing and unboxing operations:</span></span>  
  
 [!code-csharp[csProgGuideTypes#21](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_8.cs)]  
  
 <span data-ttu-id="3b3d9-139">Na poniższym rysunku pokazano wyniku poprzednich instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-139">The following figure demonstrates the result of the previous statements.</span></span>  
  
 <span data-ttu-id="3b3d9-140">![Grafika konwersji Rozpakowującej](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")</span><span class="sxs-lookup"><span data-stu-id="3b3d9-140">![UnBoxing Conversion graphic](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")</span></span>  
<span data-ttu-id="3b3d9-141">Konwersja unboxing</span><span class="sxs-lookup"><span data-stu-id="3b3d9-141">Unboxing Conversion</span></span>  
  
 <span data-ttu-id="3b3d9-142">Dla Rozpakowywanie typów wartości się pomyślnie w czasie wykonywania element trwa rozpakowany musi być odwołaniem do obiektu, który został wcześniej utworzony przez konwersja boxing wystąpienia tego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-142">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="3b3d9-143">Podjęto próbę unbox — `null` powoduje, że <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-143">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="3b3d9-144">Podjęto próbę unbox — odwołanie do niezgodną wartość typu przyczyny <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-144">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b3d9-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b3d9-145">Example</span></span>  
 <span data-ttu-id="3b3d9-146">W poniższym przykładzie pokazano przypadku nieprawidłowy Rozpakowywanie i powstałe w ten sposób `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-146">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="3b3d9-147">Przy użyciu `try` i `catch`, gdy wystąpi błąd jest wyświetlany komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="3b3d9-147">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>  
  
 [!code-csharp[csProgGuideTypes#20](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_9.cs)]  
  
 <span data-ttu-id="3b3d9-148">Ten program danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="3b3d9-148">This program outputs:</span></span>  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 <span data-ttu-id="3b3d9-149">Jeśli zmienisz instrukcji:</span><span class="sxs-lookup"><span data-stu-id="3b3d9-149">If you change the statement:</span></span>  
  
```  
int j = (short) o;  
```  
  
 <span data-ttu-id="3b3d9-150">na:</span><span class="sxs-lookup"><span data-stu-id="3b3d9-150">to:</span></span>  
  
```  
int j = (int) o;  
```  
  
 <span data-ttu-id="3b3d9-151">Konwersja zostanie wykonane, a otrzymasz dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="3b3d9-151">the conversion will be performed, and you will get the output:</span></span>  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="3b3d9-152">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3b3d9-152">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a><span data-ttu-id="3b3d9-153">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="3b3d9-153">Related Sections</span></span>  
 <span data-ttu-id="3b3d9-154">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="3b3d9-154">For more information:</span></span>  
  
-   [<span data-ttu-id="3b3d9-155">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="3b3d9-155">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="3b3d9-156">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="3b3d9-156">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="3b3d9-157">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3b3d9-157">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3b3d9-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b3d9-158">See Also</span></span>  
 [<span data-ttu-id="3b3d9-159">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3b3d9-159">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
