---
title: Wbudowane typy odwołań — odwołanie do języka C#
description: Dowiedz się więcej o typach odwołań, które mają słowa kluczowe języka C#, których możesz użyć do ich zadeklarowania.
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
ms.openlocfilehash: c2c03f47babd9ccf87eb60d33b9d65d1a9c82e2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399645"
---
# <a name="built-in-reference-types-c-reference"></a><span data-ttu-id="1e5fc-103">Wbudowane typy odwołań (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="1e5fc-103">Built-in reference types (C# reference)</span></span>

<span data-ttu-id="1e5fc-104">C# ma wiele wbudowanych typów odwołań.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-104">C# has a number of built-in reference types.</span></span> <span data-ttu-id="1e5fc-105">Mają słowa kluczowe lub operatory, które są synonimami dla typu w bibliotece .NET.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-105">They have keywords or operators that are synonyms for a type in the .NET library.</span></span>

## <a name="the-object-type"></a><span data-ttu-id="1e5fc-106">Typ obiektu</span><span class="sxs-lookup"><span data-stu-id="1e5fc-106">The object type</span></span>

<span data-ttu-id="1e5fc-107">Typ `object` jest aliasem <xref:System.Object?displayProperty=nameWithType> w .NET.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-107">The `object` type is an alias for <xref:System.Object?displayProperty=nameWithType> in .NET.</span></span> <span data-ttu-id="1e5fc-108">W ujednoliconym systemie typów Języka C#wszystkie typy, wstępnie zdefiniowane i zdefiniowane przez użytkownika, <xref:System.Object?displayProperty=nameWithType>typy odwołań i typy wartości dziedziczą bezpośrednio lub pośrednio z .</span><span class="sxs-lookup"><span data-stu-id="1e5fc-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1e5fc-109">Wartości dowolnego typu można przypisać do zmiennych typu `object`.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-109">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="1e5fc-110">Do `object` dowolnej zmiennej można przypisać wartość `null`domyślną za pomocą literału .</span><span class="sxs-lookup"><span data-stu-id="1e5fc-110">Any `object` variable can be assigned to its default value using the literal `null`.</span></span> <span data-ttu-id="1e5fc-111">Gdy zmienna typu wartości jest konwertowana na obiekt, mówi się, że *jest zapakowana*.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-111">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="1e5fc-112">Gdy zmienna `object` typu jest konwertowana na typ wartości, mówi się, że *jest rozpakowana*.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-112">When a variable of type `object` is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="1e5fc-113">Aby uzyskać więcej informacji, zobacz [Boks i Unboxing](../../programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="1e5fc-113">For more information, see [Boxing and Unboxing](../../programming-guide/types/boxing-and-unboxing.md).</span></span>

## <a name="the-string-type"></a><span data-ttu-id="1e5fc-114">Typ ciągu</span><span class="sxs-lookup"><span data-stu-id="1e5fc-114">The string type</span></span>

<span data-ttu-id="1e5fc-115">Typ `string` reprezentuje sekwencję zero lub więcej znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-115">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="1e5fc-116">`string`jest aliasem <xref:System.String?displayProperty=nameWithType> w .NET.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-116">`string` is an alias for <xref:System.String?displayProperty=nameWithType> in .NET.</span></span>

<span data-ttu-id="1e5fc-117">Mimo `string` że jest typem odwołania, [operatory `==` równości i `!=` ](../operators/equality-operators.md#string-equality) są zdefiniowane do porównywania `string` wartości obiektów, a nie odwołań.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-117">Although `string` is a reference type, the [equality operators `==` and `!=`](../operators/equality-operators.md#string-equality) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="1e5fc-118">To sprawia, że testowanie równości ciągów bardziej intuicyjne.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-118">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="1e5fc-119">Przykład:</span><span class="sxs-lookup"><span data-stu-id="1e5fc-119">For example:</span></span>

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

<span data-ttu-id="1e5fc-120">Spowoduje to wyświetlenie "True", a następnie "False", ponieważ `a` zawartość `b` ciągów są równoważne, ale i nie odnoszą się do tego samego wystąpienia ciągu.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-120">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>

<span data-ttu-id="1e5fc-121">Operator [+](../operators/addition-operator.md#string-concatenation) łączy ciągi:</span><span class="sxs-lookup"><span data-stu-id="1e5fc-121">The [+ operator](../operators/addition-operator.md#string-concatenation) concatenates strings:</span></span>

```csharp
string a = "good " + "morning";
```

<span data-ttu-id="1e5fc-122">Spowoduje to utworzenie obiektu ciągu, który zawiera "dzień dobry".</span><span class="sxs-lookup"><span data-stu-id="1e5fc-122">This creates a string object that contains "good morning".</span></span>

<span data-ttu-id="1e5fc-123">Ciągi są *niezmienne*- zawartość obiektu ciągu nie można zmienić po utworzeniu obiektu, chociaż składnia sprawia, że wydaje się, jakby można to zrobić.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-123">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="1e5fc-124">Na przykład podczas pisania tego kodu kompilator faktycznie tworzy nowy obiekt ciągu do przechowywania nowej sekwencji znaków i że nowy obiekt jest przypisany do `b`.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-124">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to `b`.</span></span> <span data-ttu-id="1e5fc-125">Pamięć, która została `b` przydzielona do (gdy zawierała ciąg "h") kwalifikuje się do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-125">The memory that had been allocated for `b` (when it contained the string "h") is then eligible for garbage collection.</span></span>

```csharp
string b = "h";
b += "ello";
```

<span data-ttu-id="1e5fc-126">Operator `[]` [operator](../operators/member-access-operators.md#indexer-operator-) może służyć do odczytutylko dostęp do poszczególnych znaków ciągu.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-126">The `[]` [operator](../operators/member-access-operators.md#indexer-operator-) can be used for readonly access to individual characters of a string.</span></span> <span data-ttu-id="1e5fc-127">Prawidłowe wartości indeksu `0` zaczynają się od i muszą być mniejsze niż długość ciągu:</span><span class="sxs-lookup"><span data-stu-id="1e5fc-127">Valid index values start at `0` and must be less than the length of the string:</span></span>

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

<span data-ttu-id="1e5fc-128">W podobny sposób `[]` operator może być również używany do iteracji nad każdym znakiem w ciągu:</span><span class="sxs-lookup"><span data-stu-id="1e5fc-128">In similar fashion, the `[]` operator can also be used for iterating over each character in a string:</span></span>

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
```

<span data-ttu-id="1e5fc-129">Literały ciągów `string` są typu i mogą być `@`napisane w dwóch formach, cytowany i -quoted.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-129">String literals are of type `string` and can be written in two forms, quoted and `@`-quoted.</span></span> <span data-ttu-id="1e5fc-130">Cytowane literały ciągów są ujęte w podwójne cudzysłowy ("):</span><span class="sxs-lookup"><span data-stu-id="1e5fc-130">Quoted string literals are enclosed in double quotation marks ("):</span></span>

```csharp
"good morning"  // a string literal
```

<span data-ttu-id="1e5fc-131">Literały ciągów mogą zawierać dowolne literały znaków.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-131">String literals can contain any character literal.</span></span> <span data-ttu-id="1e5fc-132">Sekwencje ucieczki są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-132">Escape sequences are included.</span></span> <span data-ttu-id="1e5fc-133">W poniższym przykładzie `\\` użyto `\u0066` sekwencji ucieczki dla `\n` ukośnika odwrotnego, dla litery f i dla nowej linii.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-133">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
// Output:
// \f
//  F
```

> [!NOTE]
> <span data-ttu-id="1e5fc-134">Kod `\udddd` ucieczki (gdzie `dddd` jest liczbą czterocyfrową) reprezentuje znak`dddd`Unicode U+ .</span><span class="sxs-lookup"><span data-stu-id="1e5fc-134">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="1e5fc-135">Rozpoznawane są również ośmiocyfrowe kody `\Udddddddd`uchyłowane unicode: .</span><span class="sxs-lookup"><span data-stu-id="1e5fc-135">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>

<span data-ttu-id="1e5fc-136">[Dosłowne literały ciągów](../tokens/verbatim.md) zaczynają się `@` od i są również ujęte w podwójne cudzysłowy.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-136">[Verbatim string literals](../tokens/verbatim.md) start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="1e5fc-137">Przykład:</span><span class="sxs-lookup"><span data-stu-id="1e5fc-137">For example:</span></span>

```csharp
@"good morning"  // a string literal
```

<span data-ttu-id="1e5fc-138">Zaletą ciągów dosłownych jest to, że sekwencje ucieczki *nie* są przetwarzane, co ułatwia pisanie, na przykład, w pełni kwalifikowanej nazwy pliku systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="1e5fc-138">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified Windows file name:</span></span>

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

<span data-ttu-id="1e5fc-139">Aby dołączyć podwójny cudzysłów w @-quoted ciągu, podwoić go:</span><span class="sxs-lookup"><span data-stu-id="1e5fc-139">To include a double quotation mark in an @-quoted string, double it:</span></span>

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a><span data-ttu-id="1e5fc-140">Typ pełnomocnika</span><span class="sxs-lookup"><span data-stu-id="1e5fc-140">The delegate type</span></span>

<span data-ttu-id="1e5fc-141">Deklaracja typu delegata jest podobna do podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-141">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="1e5fc-142">Ma wartość zwracaną i dowolną liczbę parametrów dowolnego typu:</span><span class="sxs-lookup"><span data-stu-id="1e5fc-142">It has a return value and any number of parameters of any type:</span></span>

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

<span data-ttu-id="1e5fc-143">W .NET `System.Action` `System.Func` i typy zawierają ogólne definicje dla wielu wspólnych delegatów.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-143">In .NET, `System.Action` and `System.Func` types provide generic definitions for many common delegates.</span></span> <span data-ttu-id="1e5fc-144">Prawdopodobnie nie trzeba definiować nowych typów delegatów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-144">You likely don't need to define new custom delegate types.</span></span> <span data-ttu-id="1e5fc-145">Zamiast tego można utworzyć wystąpienia typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-145">Instead, you can create instantiations of the provided generic types.</span></span>

<span data-ttu-id="1e5fc-146">A `delegate` jest typem odwołania, który może służyć do hermetyzacji nazwie lub metody anonimowej.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-146">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="1e5fc-147">Delegaty są podobne do wskaźników funkcji w języku C++; jednak delegaci są bezpieczne typu i bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-147">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="1e5fc-148">Aby uzyskać aplikacje delegatów, zobacz [delegatów](../../programming-guide/delegates/index.md) i [delegatów ogólnych](../../programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="1e5fc-148">For applications of delegates, see [Delegates](../../programming-guide/delegates/index.md) and [Generic Delegates](../../programming-guide/generics/generic-delegates.md).</span></span> <span data-ttu-id="1e5fc-149">Delegaci są podstawą [do zdarzeń](../../programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="1e5fc-149">Delegates are the basis for [Events](../../programming-guide/events/index.md).</span></span> <span data-ttu-id="1e5fc-150">Pełnomocnika można utworzyć przez kojarzenie go z metodą o nazwie lub anonimowy.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-150">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span>

<span data-ttu-id="1e5fc-151">Delegat musi być tworzone za pomocą metody lub wyrażenia lambda, który ma zgodny typ zwracany i parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-151">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="1e5fc-152">Aby uzyskać więcej informacji na temat stopnia wariancji dozwolonej w podpisie metody, zobacz [Wariancja w delegatach](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="1e5fc-152">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="1e5fc-153">Do użytku z metodami anonimowymi delegat a kod, który ma być z nim skojarzony, są zadeklarowane razem.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-153">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span>

## <a name="the-dynamic-type"></a><span data-ttu-id="1e5fc-154">Typ dynamiczny</span><span class="sxs-lookup"><span data-stu-id="1e5fc-154">The dynamic type</span></span>

<span data-ttu-id="1e5fc-155">Typ `dynamic` wskazuje, że użycie zmiennej i odwołania do jej elementów członkowskich pomijają sprawdzanie typu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-155">The `dynamic` type indicates that use of the variable and references to its members bypass compile-time type checking.</span></span> <span data-ttu-id="1e5fc-156">Zamiast tego te operacje są rozwiązywane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-156">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="1e5fc-157">Typ `dynamic` ten upraszcza dostęp do interfejsów API COM, takich jak interfejsy API automatyzacji pakietu Office, do dynamicznych interfejsów API, takich jak biblioteki IronPython, oraz do modelu obiektu dokumentu HTML (DOM).</span><span class="sxs-lookup"><span data-stu-id="1e5fc-157">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>

<span data-ttu-id="1e5fc-158">Typ `dynamic` zachowuje się `object` jak typ w większości przypadków.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-158">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="1e5fc-159">W szczególności każde wyrażenie inne niż null `dynamic` można przekonwertować na typ.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-159">In particular, any non-null expression can be converted to the `dynamic` type.</span></span> <span data-ttu-id="1e5fc-160">Typ `dynamic` różni się `object` od tego, że operacje, które zawierają wyrażenia typu `dynamic` nie są rozpoznawane lub typu sprawdzane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-160">The `dynamic` type differs from `object` in that operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="1e5fc-161">Kompilator łączy informacje o operacji, a te informacje są później używane do oceny operacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-161">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="1e5fc-162">W ramach procesu zmienne typu `dynamic` są kompilowane do zmiennych typu `object`.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-162">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="1e5fc-163">W związku `dynamic` z tym typ istnieje tylko w czasie kompilacji, a nie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-163">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>

<span data-ttu-id="1e5fc-164">Poniższy przykład kontrastuje zmienną `dynamic` typu ze `object`zmienną typu .</span><span class="sxs-lookup"><span data-stu-id="1e5fc-164">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="1e5fc-165">Aby sprawdzić typ każdej zmiennej w czasie kompilacji, `obj` umieść `WriteLine` wskaźnik myszy nad `dyn` lub w instrukcjach.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-165">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="1e5fc-166">Skopiuj następujący kod do edytora, w którym dostępny jest program IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-166">Copy the following code into an editor where IntelliSense is available.</span></span> <span data-ttu-id="1e5fc-167">IntelliSense **dynamic** pokazuje `dyn` dynamiczny dla `obj`i **obiekt** dla .</span><span class="sxs-lookup"><span data-stu-id="1e5fc-167">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<span data-ttu-id="1e5fc-168">Instrukcje <xref:System.Console.WriteLine%2A> wyświetlają typy czasu `dyn` wykonywania i `obj`.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-168">The <xref:System.Console.WriteLine%2A> statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="1e5fc-169">W tym momencie oba mają tego samego typu, liczba całkowita.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-169">At that point, both have the same type, integer.</span></span> <span data-ttu-id="1e5fc-170">Zostaną wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="1e5fc-170">The following output is produced:</span></span>

```console
System.Int32
System.Int32
```

<span data-ttu-id="1e5fc-171">Aby zobaczyć różnicę między `dyn` i `obj` w czasie kompilacji, dodaj następujące `WriteLine` dwa wiersze między deklaracjami i instrukcjami w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-171">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 <span data-ttu-id="1e5fc-172">Błąd kompilatora jest zgłaszany dla próby dodania `obj + 3`liczby całkowitej i obiektu w wyrażeniu .</span><span class="sxs-lookup"><span data-stu-id="1e5fc-172">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="1e5fc-173">Jednak nie zgłaszano `dyn + 3`żadnego błędu dla .</span><span class="sxs-lookup"><span data-stu-id="1e5fc-173">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="1e5fc-174">Wyrażenie, które `dyn` zawiera nie jest sprawdzana w `dyn` czasie `dynamic`kompilacji, ponieważ typem jest .</span><span class="sxs-lookup"><span data-stu-id="1e5fc-174">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>

<span data-ttu-id="1e5fc-175">Poniższy przykład `dynamic` używa w kilku deklaracjach.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-175">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="1e5fc-176">Metoda `Main` kontrastuje również sprawdzanie typu kompilacji z sprawdzaniem typu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1e5fc-176">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a><span data-ttu-id="1e5fc-177">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1e5fc-177">See also</span></span>

- [<span data-ttu-id="1e5fc-178">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="1e5fc-178">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1e5fc-179">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="1e5fc-179">C# Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="1e5fc-180">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="1e5fc-180">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="1e5fc-181">Używanie typu dynamicznego</span><span class="sxs-lookup"><span data-stu-id="1e5fc-181">Using Type dynamic</span></span>](../../programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="1e5fc-182">Najlepsze rozwiązania dotyczące używania ciągów</span><span class="sxs-lookup"><span data-stu-id="1e5fc-182">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)
- [<span data-ttu-id="1e5fc-183">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="1e5fc-183">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="1e5fc-184">Tworzenie nowych ciągów</span><span class="sxs-lookup"><span data-stu-id="1e5fc-184">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="1e5fc-185">Operatory testowania typu i rzutowania</span><span class="sxs-lookup"><span data-stu-id="1e5fc-185">Type-testing and cast operators</span></span>](../operators/type-testing-and-cast.md)
- [<span data-ttu-id="1e5fc-186">Jak bezpiecznie oddać za pomocą dopasowania wzoru i jak i jest operatorzy</span><span class="sxs-lookup"><span data-stu-id="1e5fc-186">How to safely cast using pattern matching and the as and is operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="1e5fc-187">Instruktaż: tworzenie i używanie obiektów dynamicznych</span><span class="sxs-lookup"><span data-stu-id="1e5fc-187">Walkthrough: creating and using dynamic objects</span></span>](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
