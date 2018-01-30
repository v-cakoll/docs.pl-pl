---
title: "enum (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 36d33387dda68270e0490eaa6c792f95d058651e
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="enum-c-reference"></a><span data-ttu-id="598ef-102">enum (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="598ef-102">enum (C# Reference)</span></span>
<span data-ttu-id="598ef-103">`enum` — Słowo kluczowe służy do deklarowania wyliczenie różne typu, który zawiera zestaw stałe nazwane o nazwie listy modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="598ef-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>  
  
 <span data-ttu-id="598ef-104">Zazwyczaj najlepiej jest zdefiniowanie wyliczenia bezpośrednio z poziomu obszaru nazw, tak aby wszystkie klasy w przestrzeni nazw do niego dostęp z wygody takie same.</span><span class="sxs-lookup"><span data-stu-id="598ef-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="598ef-105">Jednak wyliczenia mogą być zagnieżdżone w obrębie klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="598ef-105">However, an enum can also be nested within a class or struct.</span></span>  
  
 <span data-ttu-id="598ef-106">Domyślnie pierwszy modułu wyliczającego ma wartość 0, a wartość każdego kolejnych modułu wyliczającego jest zwiększana o 1.</span><span class="sxs-lookup"><span data-stu-id="598ef-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="598ef-107">Na przykład w następujących wyliczenia `Sat` jest `0`, `Sun` jest `1`, `Mon` jest `2`, itd.</span><span class="sxs-lookup"><span data-stu-id="598ef-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>  
  
```  
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="598ef-108">Moduły wyliczające umożliwia inicjatory zastąpić wartości domyślne, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="598ef-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>  
  
```  
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="598ef-109">W tym wyliczeniu sekwencję elementów wymusza na uruchamianie z `1` zamiast `0`.</span><span class="sxs-lookup"><span data-stu-id="598ef-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="598ef-110">Jednak zaleca się tym stałą, który ma wartość 0.</span><span class="sxs-lookup"><span data-stu-id="598ef-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="598ef-111">Aby uzyskać więcej informacji, zobacz [Typy wyliczeniowe](../../../csharp/programming-guide/enumeration-types.md).</span><span class="sxs-lookup"><span data-stu-id="598ef-111">For more information, see [Enumeration Types](../../../csharp/programming-guide/enumeration-types.md).</span></span>  
  
 <span data-ttu-id="598ef-112">Każdy typ wyliczeniowy ma odpowiedni typ, który może być dowolnego typu całkowitego z wyjątkiem [char](../../../csharp/language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="598ef-112">Every enumeration type has an underlying type, which can be any integral type except [char](../../../csharp/language-reference/keywords/char.md).</span></span> <span data-ttu-id="598ef-113">Domyślny typ bazowy typu wyliczenia elementów jest [int](../../../csharp/language-reference/keywords/int.md). Aby zadeklarować wyliczenie innego typu całkowitego, takich jak [bajtów](../../../csharp/language-reference/keywords/byte.md), użyj dwukropka po identyfikatorze, a następnie według typu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="598ef-113">The default underlying type of enumeration elements is [int](../../../csharp/language-reference/keywords/int.md). To declare an enum of another integral type, such as [byte](../../../csharp/language-reference/keywords/byte.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>  
  
```  
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="598ef-114">Istnieją typy zatwierdzone dla wyliczenia [bajtów](../../../csharp/language-reference/keywords/byte.md), [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [krótki](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [długi](../../../csharp/language-reference/keywords/long.md), lub [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="598ef-114">The approved types for an enum are [byte](../../../csharp/language-reference/keywords/byte.md), [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
 <span data-ttu-id="598ef-115">Zmienna typu `Day` można przypisać dowolną wartość z zakresu od typu źródłowego; wartości nie są ograniczone do stałe nazwane.</span><span class="sxs-lookup"><span data-stu-id="598ef-115">A variable of type `Day` can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>  
  
 <span data-ttu-id="598ef-116">Wartość domyślna `enum E` jest wartością produkowane przez wyrażenie `(E)0`.</span><span class="sxs-lookup"><span data-stu-id="598ef-116">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="598ef-117">Moduł wyliczający nie może zawierać biały znak w nazwie.</span><span class="sxs-lookup"><span data-stu-id="598ef-117">An enumerator cannot contain white space in its name.</span></span>  
  
 <span data-ttu-id="598ef-118">Podstawowy typ Określa, ile miejsca do magazynowania jest przydzielona dla każdego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="598ef-118">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="598ef-119">Jednak jawnego rzutowania jest niezbędne do przekonwertowania z `enum` typu na typ całkowity.</span><span class="sxs-lookup"><span data-stu-id="598ef-119">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="598ef-120">Na przykład następująca instrukcja przypisuje modułu wyliczającego `Sun` do zmiennej typu [int](../../../csharp/language-reference/keywords/int.md) przy użyciu rzutowanie do przekonwertowania z `enum` do `int`.</span><span class="sxs-lookup"><span data-stu-id="598ef-120">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](../../../csharp/language-reference/keywords/int.md) by using a cast to convert from `enum` to `int`.</span></span>  
  
```  
int x = (int)Day.Sun;  
```  
  
 <span data-ttu-id="598ef-121">Po zastosowaniu <xref:System.FlagsAttribute?displayProperty=nameWithType> na wyliczenie, który zawiera elementy, które można łączyć z bitowego `OR` operacji, ten atrybut ma wpływ na zachowanie `enum` gdy jest używana z niektóre narzędzia.</span><span class="sxs-lookup"><span data-stu-id="598ef-121">When you apply <xref:System.FlagsAttribute?displayProperty=nameWithType> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="598ef-122">Można zauważyć tych zmian, korzystając z narzędzi takich jak <xref:System.Console> klas, metod i ewaluatora wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="598ef-122">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="598ef-123">(Zobacz przykład trzeci).</span><span class="sxs-lookup"><span data-stu-id="598ef-123">(See the third example.)</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="598ef-124">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="598ef-124">Robust Programming</span></span>  
 <span data-ttu-id="598ef-125">Tak jak w przypadku dowolnego stała wszystkie odwołania do poszczególnych wartości wyliczenia są konwertowane na literałach numerycznych w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="598ef-125">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="598ef-126">To utworzenie potencjalne problemy z wersjonowaniem, zgodnie z opisem w [stałe](../../../csharp/programming-guide/classes-and-structs/constants.md).</span><span class="sxs-lookup"><span data-stu-id="598ef-126">This can create potential versioning issues as described in [Constants](../../../csharp/programming-guide/classes-and-structs/constants.md).</span></span>  
  
 <span data-ttu-id="598ef-127">Przypisywanie wartości dodatkowe do nowej wersji wyliczenia lub zmianę wartości członkowie wyliczenia w nowej wersji, mogą powodować problemy dla kodu źródłowego zależnych.</span><span class="sxs-lookup"><span data-stu-id="598ef-127">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="598ef-128">Wartości wyliczenia są często używane w [przełącznika](../../../csharp/language-reference/keywords/switch.md) instrukcje.</span><span class="sxs-lookup"><span data-stu-id="598ef-128">Enum values often are used in [switch](../../../csharp/language-reference/keywords/switch.md) statements.</span></span> <span data-ttu-id="598ef-129">Jeśli dodatkowe elementy zostały dodane do `enum` typu, domyślnej sekcji instrukcji switch można wybrać nieoczekiwanie.</span><span class="sxs-lookup"><span data-stu-id="598ef-129">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>  
  
 <span data-ttu-id="598ef-130">Inni deweloperzy użycie kodu, wskazówki dotyczące sposobu ich kod powinien reagują, gdy nowe elementy są dodawane do dowolnego należy zapewnić `enum` typów.</span><span class="sxs-lookup"><span data-stu-id="598ef-130">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="598ef-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="598ef-131">Example</span></span>  
 <span data-ttu-id="598ef-132">W poniższym przykładzie wyliczenie `Day`, jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="598ef-132">In the following example, an enumeration, `Day`, is declared.</span></span> <span data-ttu-id="598ef-133">Dwa moduły wyliczające jawnie przekonwertować na liczbę całkowitą i przypisane do zmiennych liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="598ef-133">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="598ef-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="598ef-134">Example</span></span>  
 <span data-ttu-id="598ef-135">W poniższym przykładzie opcji typu base służy do deklarowania `enum` której członkami są typu `long`.</span><span class="sxs-lookup"><span data-stu-id="598ef-135">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="598ef-136">Należy zauważyć, że nawet jeśli typ podstawowy wyliczenia jest `long`, elementy członkowskie wyliczenia nadal musi być jawnie przekonwertować na typ `long` przy użyciu rzutowanie.</span><span class="sxs-lookup"><span data-stu-id="598ef-136">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="598ef-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="598ef-137">Example</span></span>  
 <span data-ttu-id="598ef-138">Poniższy przykładowy kod przedstawia użycie i wpływu <xref:System.FlagsAttribute?displayProperty=nameWithType> atrybutu `enum` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="598ef-138">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute on an `enum` declaration.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_3.cs)]  
  
## <a name="comments"></a><span data-ttu-id="598ef-139">Komentarze</span><span class="sxs-lookup"><span data-stu-id="598ef-139">Comments</span></span>  
 <span data-ttu-id="598ef-140">Jeśli usuniesz `Flags`, przykładzie wyświetlane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="598ef-140">If you remove `Flags`, the example displays the following values:</span></span>  
  
 `5`  
  
 `5`  
  
## <a name="c-language-specification"></a><span data-ttu-id="598ef-141">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="598ef-141">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="598ef-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="598ef-142">See Also</span></span>  
 [<span data-ttu-id="598ef-143">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="598ef-143">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="598ef-144">Typy wyliczeniowe</span><span class="sxs-lookup"><span data-stu-id="598ef-144">Enumeration Types</span></span>](../../../csharp/programming-guide/enumeration-types.md)  
 [<span data-ttu-id="598ef-145">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="598ef-145">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="598ef-146">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="598ef-146">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="598ef-147">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="598ef-147">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="598ef-148">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="598ef-148">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="598ef-149">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="598ef-149">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [<span data-ttu-id="598ef-150">Konwencje nazewnictwa wyliczenia</span><span class="sxs-lookup"><span data-stu-id="598ef-150">Enum Naming Conventions</span></span>](https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-classes-structs-and-interfaces#naming-enumerations)
