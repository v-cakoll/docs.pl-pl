---
title: Wbudowane typy referencyjne - C# odwołania
description: Więcej informacji na temat typów odwołań, które mają C# słów kluczowych, można użyć, aby zadeklarować je.
ms.date: 06/25/2019
f1_keywords:
- object_CSharpKeyword
- object
- delegate_CSharpKeyword
- delegate
- dynamic_CSharpKeyword
- string
- string_CSharpKeyword
helpviewer_keywords:
- object keyword [C#]
- delegate keyword [C#]
- function pointers [C#]
- dynamic [C#]
- dynamic keyword [C#]
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.openlocfilehash: 4bc93216d74e2732870e08edd4bdb9570391cf5f
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877196"
---
# <a name="built-in-reference-types-c-reference"></a><span data-ttu-id="0d7d0-103">Wbudowane typy referencyjne (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="0d7d0-103">Built-in reference types (C# reference)</span></span>

<span data-ttu-id="0d7d0-104">C#zawiera liczbę wbudowane typy referencyjne.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-104">C# has a number of built-in reference types.</span></span> <span data-ttu-id="0d7d0-105">Mają one słów kluczowych lub operatorów, które są synonimy dla typu w bibliotece programu .NET.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-105">They have keywords or operators that are synonyms for a type in the .NET library.</span></span> 

## <a name="the-object-type"></a><span data-ttu-id="0d7d0-106">Typ obiektu</span><span class="sxs-lookup"><span data-stu-id="0d7d0-106">The object type</span></span>

<span data-ttu-id="0d7d0-107">`object` Typu jest aliasem dla <xref:System.Object?displayProperty=nameWithType> na platformie .NET.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-107">The `object` type is an alias for <xref:System.Object?displayProperty=nameWithType> in .NET.</span></span> <span data-ttu-id="0d7d0-108">W systemie zunifikowany typ w języku C#, wszystkie typy, wstępnie zdefiniowanych i zdefiniowanych przez użytkownika typy odwołań i typy wartości dziedziczyć bezpośrednio lub pośrednio <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0d7d0-109">Można przypisać wartości dowolnego typu do zmiennych typu `object`.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-109">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="0d7d0-110">Wszelkie `object` zmiennej można przypisać do wartości domyślnej przy użyciu literału `null`.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-110">Any `object` variable can be assigned to its default value using the literal `null`.</span></span> <span data-ttu-id="0d7d0-111">Kiedy zmienną typu wartości jest konwertowany na obiekt, jest określany jako *opakowany*.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-111">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="0d7d0-112">Zmienną obiektu typu jest konwertowany na typ wartości, jest określane jako *rozpakowany*.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-112">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="0d7d0-113">Aby uzyskać więcej informacji, zobacz [opakowywanie i rozpakowywanie](../../programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="0d7d0-113">For more information, see [Boxing and Unboxing](../../programming-guide/types/boxing-and-unboxing.md).</span></span> 

## <a name="the-string-type"></a><span data-ttu-id="0d7d0-114">Typ ciągu</span><span class="sxs-lookup"><span data-stu-id="0d7d0-114">The string type</span></span>

<span data-ttu-id="0d7d0-115">`string` Typu reprezentuje sekwencję zero lub więcej znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-115">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="0d7d0-116">`string` jest aliasem dla <xref:System.String?displayProperty=nameWithType> na platformie .NET.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-116">`string` is an alias for <xref:System.String?displayProperty=nameWithType> in .NET.</span></span>

<span data-ttu-id="0d7d0-117">Mimo że `string` jest typem referencyjnym [Operatory równości `==` i `!=` ](../operators/equality-operators.md#string-equality) są zdefiniowane w celu porównania wartości `string` obiektów, nie odwołuje się.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-117">Although `string` is a reference type, the [equality operators `==` and `!=`](../operators/equality-operators.md#string-equality) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="0d7d0-118">To sprawia, że testowanie dla równości ciągu bardziej intuicyjne.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-118">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="0d7d0-119">Przykład:</span><span class="sxs-lookup"><span data-stu-id="0d7d0-119">For example:</span></span>

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

<span data-ttu-id="0d7d0-120">Spowoduje to wyświetlenie "True" i następnie "False", ponieważ zawartość ciągi są równoważne, ale `a` i `b` odwołuje się do tego samego wystąpienia ciągu.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-120">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>

<span data-ttu-id="0d7d0-121">[+ — Operator](../operators/addition-operator.md#string-concatenation) łączy ciągi:</span><span class="sxs-lookup"><span data-stu-id="0d7d0-121">The [+ operator](../operators/addition-operator.md#string-concatenation) concatenates strings:</span></span>

```csharp
string a = "good " + "morning";
```

<span data-ttu-id="0d7d0-122">Spowoduje to utworzenie obiekt ciągu zawierający "good morning".</span><span class="sxs-lookup"><span data-stu-id="0d7d0-122">This creates a string object that contains "good morning".</span></span>

<span data-ttu-id="0d7d0-123">Ciągi są *niezmienne*— nie można zmienić zawartość obiekt ciągu, po utworzeniu obiektu, mimo że składnia sprawia, że wyświetlane tak, jakby można to zrobić.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-123">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="0d7d0-124">Na przykład podczas pisania tego kodu, kompilator tworzy obiekt ciągu do przechowywania nową sekwencję znaków, a nowy obiekt jest przypisany do `b`.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-124">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to `b`.</span></span> <span data-ttu-id="0d7d0-125">Pamięć, która zostały przydzielone dla `b` (gdy zawiera ciąg "h") jest uprawniona do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-125">The memory that had been allocated for `b` (when it contained the string "h") is then eligible for garbage collection.</span></span>

```csharp
string b = "h";
b += "ello";
```

<span data-ttu-id="0d7d0-126">`[]` [Operator](../operators/member-access-operators.md#indexer-operator-) umożliwia dostęp tylko do odczytu do pojedynczych znaków z `string`.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-126">The `[]` [operator](../operators/member-access-operators.md#indexer-operator-) can be used for readonly access to individual characters of a `string`.</span></span> <span data-ttu-id="0d7d0-127">Prawidłowe wartości rozpoczynają się od `0` i musi być mniejsza niż długość `string`:</span><span class="sxs-lookup"><span data-stu-id="0d7d0-127">Valid values start at `0` and must be less than the length of the `string`:</span></span>

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

<span data-ttu-id="0d7d0-128">W podobny sposób `[]` operator może również służyć do Iterowanie po każdego znaku w `string`:</span><span class="sxs-lookup"><span data-stu-id="0d7d0-128">In similar fashion, the `[]` operator can also be used for iterating over each character in a `string`:</span></span>

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

<span data-ttu-id="0d7d0-129">Literały ciągów są typu `string` i mogą być zapisywane w dwóch formach, w cudzysłowach i `@`— w cudzysłowach.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-129">String literals are of type `string` and can be written in two forms, quoted and `@`-quoted.</span></span> <span data-ttu-id="0d7d0-130">Jako ciąg, który literały są ujęte w podwójny cudzysłów ("):</span><span class="sxs-lookup"><span data-stu-id="0d7d0-130">Quoted string literals are enclosed in double quotation marks ("):</span></span>

```csharp
"good morning"  // a string literal
```

<span data-ttu-id="0d7d0-131">Literały ciągu może zawierać dowolny znak literału.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-131">String literals can contain any character literal.</span></span> <span data-ttu-id="0d7d0-132">Sekwencje unikowe są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-132">Escape sequences are included.</span></span> <span data-ttu-id="0d7d0-133">W poniższym przykładzie użyto sekwencja unikowa `\\` dla ukośnikiem, po którym `\u0066` literę f, i `\n` dla nowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-133">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
\\ Output:
\\ \f
\\  F
```

> [!NOTE]
> <span data-ttu-id="0d7d0-134">Kod escape `\udddd` (gdzie `dddd` jest liczbę czterocyfrową) reprezentuje znak Unicode U +`dddd`.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-134">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="0d7d0-135">Kodów wyjścia Unicode ośmiu cyfr, również są rozpoznawane: `\Udddddddd`.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-135">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>

<span data-ttu-id="0d7d0-136">[Ciąg Verbatim literały](../tokens/verbatim.md) rozpoczynać `@` i również są ujęte w podwójny cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-136">[Verbatim string literals](../tokens/verbatim.md) start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="0d7d0-137">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0d7d0-137">For example:</span></span>

```csharp
@"good morning"  // a string literal
```

<span data-ttu-id="0d7d0-138">Zaletą ciągi verbatim jest, że sekwencje ucieczki to *nie* przetwarzany, która ułatwia zapisu, na przykład w pełni kwalifikowanej nazwy pliku Windows:</span><span class="sxs-lookup"><span data-stu-id="0d7d0-138">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified Windows file name:</span></span>

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

<span data-ttu-id="0d7d0-139">Aby uwzględnić znak podwójnego cudzysłowu w @-quoted ciąg, podwój go:</span><span class="sxs-lookup"><span data-stu-id="0d7d0-139">To include a double quotation mark in an @-quoted string, double it:</span></span>

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a><span data-ttu-id="0d7d0-140">Typ delegata</span><span class="sxs-lookup"><span data-stu-id="0d7d0-140">The delegate type</span></span>

<span data-ttu-id="0d7d0-141">Deklaracja typu delegata jest podobny do podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-141">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="0d7d0-142">Ma wartość zwracaną i dowolną liczbę parametrów, dowolnego typu:</span><span class="sxs-lookup"><span data-stu-id="0d7d0-142">It has a return value and any number of parameters of any type:</span></span>

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

<span data-ttu-id="0d7d0-143">Na platformie .NET `System.Action` i `System.Func` typy zapewniają ogólne definicji dla wielu typowych obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-143">In .NET, `System.Action` and `System.Func` types provide generic definitions for many common delegates.</span></span> <span data-ttu-id="0d7d0-144">Prawdopodobnie nie trzeba definiować nowe typy niestandardową klasę delegatów.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-144">You likely don't need to define new custom delegate types.</span></span> <span data-ttu-id="0d7d0-145">Zamiast tego można tworzyć wystąpień typów ogólnych podana.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-145">Instead, you can create instantiations of the provided generic types.</span></span>

<span data-ttu-id="0d7d0-146">Element `delegate` jest typem referencyjnym, który może służyć do hermetyzacji nazwane lub metodę anonimową.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-146">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="0d7d0-147">Delegaty są podobne do wskaźników funkcji języka C++; Jednak obiekty delegowane są bezpieczne i bezpieczny typowo.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-147">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="0d7d0-148">W przypadku aplikacji delegatów, zobacz [delegatów](../../programming-guide/delegates/index.md) i [delegatów ogólnych](../../programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="0d7d0-148">For applications of delegates, see [Delegates](../../programming-guide/delegates/index.md) and [Generic Delegates](../../programming-guide/generics/generic-delegates.md).</span></span> <span data-ttu-id="0d7d0-149">Obiekty delegowane są podstawą [zdarzenia](../../programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="0d7d0-149">Delegates are the basis for [Events](../../programming-guide/events/index.md).</span></span> <span data-ttu-id="0d7d0-150">Pełnomocnik może być utworzone przez skojarzenie przy użyciu metody nazwane i anonimowe.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-150">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span>

<span data-ttu-id="0d7d0-151">Za pomocą metody lub wyrażenia lambda zgodne zwracany typ i parametry wejściowe, można utworzyć wystąpienia obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-151">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="0d7d0-152">Aby uzyskać więcej informacji na temat stopień odchylenia, jaki jest dozwolony w podpisie metody, zobacz [wariancje w Delegatach](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="0d7d0-152">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="0d7d0-153">Do użytku z metod anonimowych delegat i kodu, które ma zostać skojarzony z nim są zadeklarowane jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-153">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> 

## <a name="the-dynamic-type"></a><span data-ttu-id="0d7d0-154">Typ dynamiczny</span><span class="sxs-lookup"><span data-stu-id="0d7d0-154">The dynamic type</span></span>

<span data-ttu-id="0d7d0-155">`dynamic` Typu wskazuje, które używają zmiennej i odwołuje się do jego elementów członkowskich pomijanie typów w czasie kompilacji sprawdzania.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-155">The `dynamic` type indicates that use of the variable and references to its members bypass compile-time type checking.</span></span> <span data-ttu-id="0d7d0-156">Zamiast tego te operacje są rozwiązywane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-156">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="0d7d0-157">`dynamic` Typu upraszcza dostęp do interfejsów API modelu COM, takich jak interfejsy API usługi Automation pakietu Office, aby dynamicznych interfejsów API, takich jak biblioteki IronPython i aby HTML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="0d7d0-157">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>

<span data-ttu-id="0d7d0-158">Typ `dynamic` zachowuje się jak typ `object` w większości przypadków.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-158">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="0d7d0-159">W szczególności dowolne wyrażenie, inną niż null można przekonwertować na `dynamic` typu.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-159">In particular, any non-null expression can be converted to the `dynamic` type.</span></span> <span data-ttu-id="0d7d0-160">`dynamic` Typ różni się od `object` w tej operacji, które zawierają wyrażenia typu `dynamic` nie są rozpoznawane lub typ sprawdzana przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-160">The `dynamic` type differs from `object` in that operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="0d7d0-161">Pakiety kompilatora, które razem informacje na temat operacji, a te informacje później użyte do oceny operacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-161">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="0d7d0-162">W ramach procesu, a zmienne typu `dynamic` są kompilowane do zmiennych typu `object`.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-162">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="0d7d0-163">W związku z tym, wpisz `dynamic` istnieje tylko w czasie kompilacji, nie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-163">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>

<span data-ttu-id="0d7d0-164">Poniższy przykład zachowanie różni się od zmiennej typu `dynamic` do zmiennej typu `object`.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-164">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="0d7d0-165">Aby sprawdzić typ każdej zmiennej w czasie kompilacji, umieść wskaźnik myszy nad `dyn` lub `obj` w `WriteLine` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-165">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="0d7d0-166">Skopiuj następujący kod do edytora, w których jest dostępna funkcja IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-166">Copy the following code into an editor where IntelliSense is available.</span></span> <span data-ttu-id="0d7d0-167">Funkcja IntelliSense pokazuje **dynamiczne** dla `dyn` i **obiektu** dla `obj`.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-167">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<span data-ttu-id="0d7d0-168"><xref:System.Console.WriteLine%2A> Instrukcji prezentuje typy środowiska wykonawczego `dyn` i `obj`.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-168">The <xref:System.Console.WriteLine%2A> statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="0d7d0-169">W tym momencie mają ten sam typ, liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-169">At that point, both have the same type, integer.</span></span> <span data-ttu-id="0d7d0-170">Są następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="0d7d0-170">The following output is produced:</span></span>

```console
System.Int32
System.Int32
```

<span data-ttu-id="0d7d0-171">Aby zobaczyć różnicę między `dyn` i `obj` w czasie kompilacji, Dodaj następujące dwa wiersze między deklaracjami i `WriteLine` instrukcji w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-171">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 <span data-ttu-id="0d7d0-172">Błąd kompilatora jest zgłaszany, próba dodanie całkowitą, a obiekt w wyrażeniu `obj + 3`.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-172">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="0d7d0-173">Jednak błąd nie jest zgłaszany, `dyn + 3`.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-173">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="0d7d0-174">Wyrażenie, które zawiera `dyn` nie jest sprawdzana w czasie kompilacji, ponieważ typ `dyn` jest `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-174">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>

<span data-ttu-id="0d7d0-175">W poniższym przykładzie użyto `dynamic` w kilka deklaracji.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-175">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="0d7d0-176">`Main` Metoda również zachowanie różni się od typu w czasie kompilacji sprawdzania ze sprawdzaniem typu run-time.</span><span class="sxs-lookup"><span data-stu-id="0d7d0-176">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a><span data-ttu-id="0d7d0-177">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d7d0-177">See also</span></span>

- [<span data-ttu-id="0d7d0-178">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0d7d0-178">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0d7d0-179">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="0d7d0-179">C# Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="0d7d0-180">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0d7d0-180">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="0d7d0-181">Używanie typu dynamicznego</span><span class="sxs-lookup"><span data-stu-id="0d7d0-181">Using Type dynamic</span></span>](../../programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="0d7d0-182">Najlepsze rozwiązania dotyczące używania ciągów</span><span class="sxs-lookup"><span data-stu-id="0d7d0-182">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)
- [<span data-ttu-id="0d7d0-183">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="0d7d0-183">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="0d7d0-184">Tworzenie nowych ciągów</span><span class="sxs-lookup"><span data-stu-id="0d7d0-184">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="0d7d0-185">Operatory badania typu i konwersji</span><span class="sxs-lookup"><span data-stu-id="0d7d0-185">Type-testing and conversion operators</span></span>](../operators/type-testing-and-conversion-operators.md)
- [<span data-ttu-id="0d7d0-186">Porady: bezpieczne rzutowanie za pomocą dopasowywania do wzorca i as operatorów i is</span><span class="sxs-lookup"><span data-stu-id="0d7d0-186">How to: safely cast using pattern matching and the as and is operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="0d7d0-187">Wskazówki: Tworzenie obiektów dynamicznych i posługiwanie</span><span class="sxs-lookup"><span data-stu-id="0d7d0-187">Walkthrough: creating and using dynamic objects</span></span>](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
