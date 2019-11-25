---
title: Wbudowane typy odwołań — C# odwołanie
description: Dowiedz się więcej na temat C# typów referencyjnych, które mają słowa kluczowe, których można użyć do deklarowania ich.
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
ms.openlocfilehash: d8858acb2743b26cc3a5172edf4765976d81adf4
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973011"
---
# <a name="built-in-reference-types-c-reference"></a><span data-ttu-id="485a9-103">Wbudowane typy odwołań (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="485a9-103">Built-in reference types (C# reference)</span></span>

<span data-ttu-id="485a9-104">C#ma wiele wbudowanych typów odwołań.</span><span class="sxs-lookup"><span data-stu-id="485a9-104">C# has a number of built-in reference types.</span></span> <span data-ttu-id="485a9-105">Mają słowa kluczowe lub operatory, które są synonimami dla typu w bibliotece .NET.</span><span class="sxs-lookup"><span data-stu-id="485a9-105">They have keywords or operators that are synonyms for a type in the .NET library.</span></span> 

## <a name="the-object-type"></a><span data-ttu-id="485a9-106">Typ obiektu</span><span class="sxs-lookup"><span data-stu-id="485a9-106">The object type</span></span>

<span data-ttu-id="485a9-107">Typ `object` jest aliasem dla <xref:System.Object?displayProperty=nameWithType> w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="485a9-107">The `object` type is an alias for <xref:System.Object?displayProperty=nameWithType> in .NET.</span></span> <span data-ttu-id="485a9-108">W ujednoliconym systemie typów systemu C#, wszystkie typy, wstępnie zdefiniowane i zdefiniowane przez użytkownika, typy odwołań i typy wartości, dziedziczą bezpośrednio lub pośrednio z <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="485a9-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="485a9-109">Wartości dowolnego typu można przypisać do zmiennych typu `object`.</span><span class="sxs-lookup"><span data-stu-id="485a9-109">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="485a9-110">Dowolna zmienna `object` może być przypisana do jej wartości domyślnej przy użyciu `null`literału.</span><span class="sxs-lookup"><span data-stu-id="485a9-110">Any `object` variable can be assigned to its default value using the literal `null`.</span></span> <span data-ttu-id="485a9-111">Gdy zmienna typu wartości jest konwertowana na obiekt, jest określana jako *opakowana*.</span><span class="sxs-lookup"><span data-stu-id="485a9-111">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="485a9-112">Gdy zmienna typu Object jest konwertowana na typ wartości, jest ona określana jako *nieopakowana*.</span><span class="sxs-lookup"><span data-stu-id="485a9-112">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="485a9-113">Aby uzyskać więcej informacji, zobacz [opakowanie i rozpakowywanie](../../programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="485a9-113">For more information, see [Boxing and Unboxing](../../programming-guide/types/boxing-and-unboxing.md).</span></span> 

## <a name="the-string-type"></a><span data-ttu-id="485a9-114">Typ ciągu</span><span class="sxs-lookup"><span data-stu-id="485a9-114">The string type</span></span>

<span data-ttu-id="485a9-115">Typ `string` reprezentuje sekwencję zero lub więcej znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="485a9-115">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="485a9-116">`string` jest alias <xref:System.String?displayProperty=nameWithType> na platformie .NET.</span><span class="sxs-lookup"><span data-stu-id="485a9-116">`string` is an alias for <xref:System.String?displayProperty=nameWithType> in .NET.</span></span>

<span data-ttu-id="485a9-117">Chociaż `string` jest typem referencyjnym, [Operatory równości `==` i `!=`](../operators/equality-operators.md#string-equality) są zdefiniowane w celu porównania wartości obiektów `string`, a nie odwołań.</span><span class="sxs-lookup"><span data-stu-id="485a9-117">Although `string` is a reference type, the [equality operators `==` and `!=`](../operators/equality-operators.md#string-equality) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="485a9-118">Dzięki temu testowanie w celu zapewnienia bardziej intuicyjnego testowania.</span><span class="sxs-lookup"><span data-stu-id="485a9-118">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="485a9-119">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="485a9-119">For example:</span></span>

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

<span data-ttu-id="485a9-120">Spowoduje to wyświetlenie wartości "true", a następnie wartości "false", ponieważ zawartość ciągów jest równoważna, ale `a` i `b` nie odwołują się do tego samego wystąpienia ciągu.</span><span class="sxs-lookup"><span data-stu-id="485a9-120">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>

<span data-ttu-id="485a9-121">[Operator +](../operators/addition-operator.md#string-concatenation) łączy ciągi:</span><span class="sxs-lookup"><span data-stu-id="485a9-121">The [+ operator](../operators/addition-operator.md#string-concatenation) concatenates strings:</span></span>

```csharp
string a = "good " + "morning";
```

<span data-ttu-id="485a9-122">Spowoduje to utworzenie obiektu ciągu zawierającego "dobry rano".</span><span class="sxs-lookup"><span data-stu-id="485a9-122">This creates a string object that contains "good morning".</span></span>

<span data-ttu-id="485a9-123">Ciągi są *niezmienne*— zawartość obiektu String nie może zostać zmieniona po utworzeniu obiektu, mimo że składnia wygląda tak, jakby to możliwe.</span><span class="sxs-lookup"><span data-stu-id="485a9-123">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="485a9-124">Na przykład podczas pisania tego kodu kompilator tworzy nowy obiekt String, aby pomieścić nową sekwencję znaków i nowy obiekt został przypisany do `b`.</span><span class="sxs-lookup"><span data-stu-id="485a9-124">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to `b`.</span></span> <span data-ttu-id="485a9-125">Pamięć, która została przypisana do `b` (gdy zawiera ciąg "h"), kwalifikuje się do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="485a9-125">The memory that had been allocated for `b` (when it contained the string "h") is then eligible for garbage collection.</span></span>

```csharp
string b = "h";
b += "ello";
```

<span data-ttu-id="485a9-126">[Operatora](../operators/member-access-operators.md#indexer-operator-) `[]` można używać do dostępu tylko do odczytu do poszczególnych znaków `string`.</span><span class="sxs-lookup"><span data-stu-id="485a9-126">The `[]` [operator](../operators/member-access-operators.md#indexer-operator-) can be used for readonly access to individual characters of a `string`.</span></span> <span data-ttu-id="485a9-127">Prawidłowe wartości zaczynają się o `0` i muszą być mniejsze niż długość `string`:</span><span class="sxs-lookup"><span data-stu-id="485a9-127">Valid values start at `0` and must be less than the length of the `string`:</span></span>

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

<span data-ttu-id="485a9-128">W podobny sposób operator `[]` może być również używany do iteracji dla każdego znaku w `string`:</span><span class="sxs-lookup"><span data-stu-id="485a9-128">In similar fashion, the `[]` operator can also be used for iterating over each character in a `string`:</span></span>

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

<span data-ttu-id="485a9-129">Literały ciągu są typu `string` i mogą być zapisywane w dwóch postaciach, cytowane i `@`.</span><span class="sxs-lookup"><span data-stu-id="485a9-129">String literals are of type `string` and can be written in two forms, quoted and `@`-quoted.</span></span> <span data-ttu-id="485a9-130">Cudzysłowy ujęte w cudzysłów są ujęte w znaki podwójnego cudzysłowu ("):</span><span class="sxs-lookup"><span data-stu-id="485a9-130">Quoted string literals are enclosed in double quotation marks ("):</span></span>

```csharp
"good morning"  // a string literal
```

<span data-ttu-id="485a9-131">Literały ciągu mogą zawierać dowolny literał znakowy.</span><span class="sxs-lookup"><span data-stu-id="485a9-131">String literals can contain any character literal.</span></span> <span data-ttu-id="485a9-132">Sekwencje ucieczki są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="485a9-132">Escape sequences are included.</span></span> <span data-ttu-id="485a9-133">W poniższym przykładzie zastosowano sekwencję ucieczki `\\` dla ukośnika odwrotnego, `\u0066` dla litery f i `\n` dla nowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="485a9-133">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
\\ Output:
\\ \f
\\  F
```

> [!NOTE]
> <span data-ttu-id="485a9-134">Kod ucieczki `\udddd` (gdzie `dddd` jest liczbą czterocyfrową) reprezentuje znak Unicode U +`dddd`.</span><span class="sxs-lookup"><span data-stu-id="485a9-134">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="485a9-135">Są również rozpoznawane osiem cyfrowych kodów ucieczki Unicode: `\Udddddddd`.</span><span class="sxs-lookup"><span data-stu-id="485a9-135">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>

<span data-ttu-id="485a9-136">[Literały ciągu Verbatim](../tokens/verbatim.md) rozpoczynają się od `@` i są również ujęte w znaki podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="485a9-136">[Verbatim string literals](../tokens/verbatim.md) start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="485a9-137">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="485a9-137">For example:</span></span>

```csharp
@"good morning"  // a string literal
```

<span data-ttu-id="485a9-138">Zaletą ciągów Verbatim jest to, że sekwencje unikowe *nie* są przetwarzane, co ułatwia pisanie, na przykład w pełni kwalifikowanej nazwy pliku systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="485a9-138">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified Windows file name:</span></span>

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

<span data-ttu-id="485a9-139">Aby uwzględnić podwójny cudzysłów w ciągu @-quoted, należy go dwukrotnie:</span><span class="sxs-lookup"><span data-stu-id="485a9-139">To include a double quotation mark in an @-quoted string, double it:</span></span>

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a><span data-ttu-id="485a9-140">Typ delegata</span><span class="sxs-lookup"><span data-stu-id="485a9-140">The delegate type</span></span>

<span data-ttu-id="485a9-141">Deklaracja typu delegata jest podobna do sygnatury metody.</span><span class="sxs-lookup"><span data-stu-id="485a9-141">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="485a9-142">Ma ona wartość zwracaną i dowolną liczbę parametrów dowolnego typu:</span><span class="sxs-lookup"><span data-stu-id="485a9-142">It has a return value and any number of parameters of any type:</span></span>

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

<span data-ttu-id="485a9-143">W programie .NET typy `System.Action` i `System.Func` zapewniają definicje ogólne dla wielu typowych delegatów.</span><span class="sxs-lookup"><span data-stu-id="485a9-143">In .NET, `System.Action` and `System.Func` types provide generic definitions for many common delegates.</span></span> <span data-ttu-id="485a9-144">Być może nie trzeba definiować nowych typów delegatów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="485a9-144">You likely don't need to define new custom delegate types.</span></span> <span data-ttu-id="485a9-145">Zamiast tego można tworzyć wystąpienia podanych typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="485a9-145">Instead, you can create instantiations of the provided generic types.</span></span>

<span data-ttu-id="485a9-146">`delegate` jest typem referencyjnym, którego można użyć do hermetyzacji metody nazwanej lub anonimowej.</span><span class="sxs-lookup"><span data-stu-id="485a9-146">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="485a9-147">Delegaty są podobne do wskaźników funkcji C++w; Delegaty są jednak bezpieczne i bezpieczne dla typów.</span><span class="sxs-lookup"><span data-stu-id="485a9-147">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="485a9-148">W przypadku aplikacji delegatów zobacz [Delegaty](../../programming-guide/delegates/index.md) i [delegatów ogólnych](../../programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="485a9-148">For applications of delegates, see [Delegates](../../programming-guide/delegates/index.md) and [Generic Delegates](../../programming-guide/generics/generic-delegates.md).</span></span> <span data-ttu-id="485a9-149">Delegaty są podstawą dla [zdarzeń](../../programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="485a9-149">Delegates are the basis for [Events](../../programming-guide/events/index.md).</span></span> <span data-ttu-id="485a9-150">Można utworzyć wystąpienie delegata, kojarząc go z metodami nazwanymi lub anonimowymi.</span><span class="sxs-lookup"><span data-stu-id="485a9-150">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span>

<span data-ttu-id="485a9-151">Obiekt delegowany musi być skonkretyzowany przy użyciu metody lub wyrażenia lambda, które ma zgodny typ zwracany i parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="485a9-151">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="485a9-152">Aby uzyskać więcej informacji na temat stopnia wariancji, który jest dozwolony w sygnaturze metody, zobacz [Wariancja w delegatach](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="485a9-152">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="485a9-153">Aby można było korzystać z metod anonimowych, delegat i kod, który ma być skojarzony z nim, są deklarowane razem.</span><span class="sxs-lookup"><span data-stu-id="485a9-153">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> 

## <a name="the-dynamic-type"></a><span data-ttu-id="485a9-154">Typ dynamiczny</span><span class="sxs-lookup"><span data-stu-id="485a9-154">The dynamic type</span></span>

<span data-ttu-id="485a9-155">Typ `dynamic` wskazuje, że użycie zmiennej i odwołań do jej elementów członkowskich obejście sprawdzania typu w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="485a9-155">The `dynamic` type indicates that use of the variable and references to its members bypass compile-time type checking.</span></span> <span data-ttu-id="485a9-156">Zamiast tego te operacje są rozwiązywane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="485a9-156">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="485a9-157">Typ `dynamic` upraszcza dostęp do interfejsów API modelu COM, takich jak interfejsy API usługi Office Automation, do dynamicznych interfejsów API, takich jak biblioteki IronPython, oraz do Document Object Model HTML (DOM).</span><span class="sxs-lookup"><span data-stu-id="485a9-157">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>

<span data-ttu-id="485a9-158">Typ `dynamic` zachowuje się jak typ `object` w większości sytuacji.</span><span class="sxs-lookup"><span data-stu-id="485a9-158">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="485a9-159">W szczególności każde wyrażenie o wartości innej niż null można przekonwertować na typ `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="485a9-159">In particular, any non-null expression can be converted to the `dynamic` type.</span></span> <span data-ttu-id="485a9-160">Typ `dynamic` różni się od `object` w tym, że operacje, które zawierają wyrażenia typu `dynamic` nie są rozpoznawane lub typem sprawdzonym przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="485a9-160">The `dynamic` type differs from `object` in that operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="485a9-161">Kompilator pakuje razem informacje o operacji, a informacje te są później używane do szacowania operacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="485a9-161">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="485a9-162">W ramach procesu zmienne typu `dynamic` są kompilowane do zmiennych typu `object`.</span><span class="sxs-lookup"><span data-stu-id="485a9-162">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="485a9-163">W związku z tym, typ `dynamic` istnieje tylko w czasie kompilacji, a nie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="485a9-163">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>

<span data-ttu-id="485a9-164">Poniższy przykład kontrastuje zmienną typu `dynamic` do zmiennej typu `object`.</span><span class="sxs-lookup"><span data-stu-id="485a9-164">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="485a9-165">Aby sprawdzić typ każdej zmiennej w czasie kompilacji, umieść wskaźnik myszy nad `dyn` lub `obj` w instrukcji `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="485a9-165">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="485a9-166">Skopiuj poniższy kod do edytora, w którym jest dostępna funkcja IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="485a9-166">Copy the following code into an editor where IntelliSense is available.</span></span> <span data-ttu-id="485a9-167">Funkcja IntelliSense wyświetla **dynamiczny** dla `dyn` i **obiektu** dla `obj`.</span><span class="sxs-lookup"><span data-stu-id="485a9-167">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<span data-ttu-id="485a9-168">Instrukcje <xref:System.Console.WriteLine%2A> wyświetlają typy czasu wykonywania `dyn` i `obj`.</span><span class="sxs-lookup"><span data-stu-id="485a9-168">The <xref:System.Console.WriteLine%2A> statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="485a9-169">W tym momencie oba mają ten sam typ, liczba całkowita.</span><span class="sxs-lookup"><span data-stu-id="485a9-169">At that point, both have the same type, integer.</span></span> <span data-ttu-id="485a9-170">Generowane są następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="485a9-170">The following output is produced:</span></span>

```console
System.Int32
System.Int32
```

<span data-ttu-id="485a9-171">Aby zobaczyć różnicę między `dyn` i `obj` w czasie kompilacji, Dodaj następujące dwa wiersze między deklaracjami i instrukcjami `WriteLine` w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="485a9-171">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 <span data-ttu-id="485a9-172">Zgłoszono błąd kompilatora dla próby dodania liczby całkowitej i obiektu w wyrażeniu `obj + 3`.</span><span class="sxs-lookup"><span data-stu-id="485a9-172">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="485a9-173">Nie jest jednak zgłaszany żaden błąd dla `dyn + 3`.</span><span class="sxs-lookup"><span data-stu-id="485a9-173">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="485a9-174">Wyrażenie zawierające `dyn` nie jest sprawdzane w czasie kompilacji, ponieważ typ `dyn` jest `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="485a9-174">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>

<span data-ttu-id="485a9-175">Poniższy przykład używa `dynamic` w kilku deklaracjach.</span><span class="sxs-lookup"><span data-stu-id="485a9-175">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="485a9-176">Metoda `Main` również kontrastuje sprawdzanie typu w czasie kompilacji przy użyciu sprawdzania typu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="485a9-176">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a><span data-ttu-id="485a9-177">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="485a9-177">See also</span></span>

- [<span data-ttu-id="485a9-178">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="485a9-178">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="485a9-179">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="485a9-179">C# Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="485a9-180">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="485a9-180">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="485a9-181">Używanie typu dynamicznego</span><span class="sxs-lookup"><span data-stu-id="485a9-181">Using Type dynamic</span></span>](../../programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="485a9-182">Najlepsze rozwiązania dotyczące używania ciągów</span><span class="sxs-lookup"><span data-stu-id="485a9-182">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)
- [<span data-ttu-id="485a9-183">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="485a9-183">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="485a9-184">Tworzenie nowych ciągów</span><span class="sxs-lookup"><span data-stu-id="485a9-184">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="485a9-185">Operatory testowania typu i rzutowania</span><span class="sxs-lookup"><span data-stu-id="485a9-185">Type-testing and cast operators</span></span>](../operators/type-testing-and-cast.md)
- [<span data-ttu-id="485a9-186">Jak bezpiecznie rzutować przy użyciu dopasowania wzorca i operatorów AS i is</span><span class="sxs-lookup"><span data-stu-id="485a9-186">How to safely cast using pattern matching and the as and is operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="485a9-187">Przewodnik: Tworzenie obiektów dynamicznych i korzystanie z nich</span><span class="sxs-lookup"><span data-stu-id="485a9-187">Walkthrough: creating and using dynamic objects</span></span>](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
