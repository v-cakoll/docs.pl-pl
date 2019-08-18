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
ms.openlocfilehash: fcfe2dafe588dce57628bff63e3519f70d7a7725
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566257"
---
# <a name="built-in-reference-types-c-reference"></a><span data-ttu-id="c4709-103">Wbudowane typy odwołań (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="c4709-103">Built-in reference types (C# reference)</span></span>

<span data-ttu-id="c4709-104">C#ma wiele wbudowanych typów odwołań.</span><span class="sxs-lookup"><span data-stu-id="c4709-104">C# has a number of built-in reference types.</span></span> <span data-ttu-id="c4709-105">Mają słowa kluczowe lub operatory, które są synonimami dla typu w bibliotece .NET.</span><span class="sxs-lookup"><span data-stu-id="c4709-105">They have keywords or operators that are synonyms for a type in the .NET library.</span></span> 

## <a name="the-object-type"></a><span data-ttu-id="c4709-106">Typ obiektu</span><span class="sxs-lookup"><span data-stu-id="c4709-106">The object type</span></span>

<span data-ttu-id="c4709-107">Typ jest aliasem dla <xref:System.Object?displayProperty=nameWithType> platformy .NET. `object`</span><span class="sxs-lookup"><span data-stu-id="c4709-107">The `object` type is an alias for <xref:System.Object?displayProperty=nameWithType> in .NET.</span></span> <span data-ttu-id="c4709-108">W ujednoliconym systemie typów systemu C#, wszystkie typy, wstępnie zdefiniowane i zdefiniowane przez użytkownika, typy odwołań i typy wartości, dziedziczą bezpośrednio lub <xref:System.Object?displayProperty=nameWithType>pośrednio z.</span><span class="sxs-lookup"><span data-stu-id="c4709-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c4709-109">Do zmiennych typu `object`można przypisać wartości dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="c4709-109">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="c4709-110">Dowolna `object` zmienna może być przypisana do wartości domyślnej przy użyciu `null`literału.</span><span class="sxs-lookup"><span data-stu-id="c4709-110">Any `object` variable can be assigned to its default value using the literal `null`.</span></span> <span data-ttu-id="c4709-111">Gdy zmienna typu wartości jest konwertowana na obiekt, jest określana jako *opakowana*.</span><span class="sxs-lookup"><span data-stu-id="c4709-111">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="c4709-112">Gdy zmienna typu Object jest konwertowana na typ wartości, jest ona określana jako nieopakowana.</span><span class="sxs-lookup"><span data-stu-id="c4709-112">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="c4709-113">Aby uzyskać więcej informacji, zobacz [opakowanie i rozpakowywanie](../../programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="c4709-113">For more information, see [Boxing and Unboxing](../../programming-guide/types/boxing-and-unboxing.md).</span></span> 

## <a name="the-string-type"></a><span data-ttu-id="c4709-114">Typ ciągu</span><span class="sxs-lookup"><span data-stu-id="c4709-114">The string type</span></span>

<span data-ttu-id="c4709-115">`string` Typ reprezentuje sekwencję składającą się z zero lub więcej znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="c4709-115">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="c4709-116">`string`jest aliasem dla <xref:System.String?displayProperty=nameWithType> platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="c4709-116">`string` is an alias for <xref:System.String?displayProperty=nameWithType> in .NET.</span></span>

<span data-ttu-id="c4709-117">Chociaż `string` jest typem referencyjnym, [Operatory `==` równości i są `!=` ](../operators/equality-operators.md#string-equality) zdefiniowane do porównywania wartości `string` obiektów, a nie odwołań.</span><span class="sxs-lookup"><span data-stu-id="c4709-117">Although `string` is a reference type, the [equality operators `==` and `!=`](../operators/equality-operators.md#string-equality) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="c4709-118">Dzięki temu testowanie w celu zapewnienia bardziej intuicyjnego testowania.</span><span class="sxs-lookup"><span data-stu-id="c4709-118">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="c4709-119">Przykład:</span><span class="sxs-lookup"><span data-stu-id="c4709-119">For example:</span></span>

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

<span data-ttu-id="c4709-120">Spowoduje to wyświetlenie wartości "true", a następnie wartości "false", ponieważ zawartość ciągów jest `a` równoważna, ale i `b` nie odwołuje się do tego samego wystąpienia ciągu.</span><span class="sxs-lookup"><span data-stu-id="c4709-120">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>

<span data-ttu-id="c4709-121">[Operator +](../operators/addition-operator.md#string-concatenation) łączy ciągi:</span><span class="sxs-lookup"><span data-stu-id="c4709-121">The [+ operator](../operators/addition-operator.md#string-concatenation) concatenates strings:</span></span>

```csharp
string a = "good " + "morning";
```

<span data-ttu-id="c4709-122">Spowoduje to utworzenie obiektu ciągu zawierającego "dobry rano".</span><span class="sxs-lookup"><span data-stu-id="c4709-122">This creates a string object that contains "good morning".</span></span>

<span data-ttu-id="c4709-123">Ciągi są *niezmienne*— zawartość obiektu String nie może zostać zmieniona po utworzeniu obiektu, mimo że składnia wygląda tak, jakby to możliwe.</span><span class="sxs-lookup"><span data-stu-id="c4709-123">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="c4709-124">Na przykład podczas pisania tego kodu kompilator w rzeczywistości tworzy nowy obiekt ciągu do przechowywania nowej sekwencji znaków, a nowy obiekt jest przypisany do `b`.</span><span class="sxs-lookup"><span data-stu-id="c4709-124">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to `b`.</span></span> <span data-ttu-id="c4709-125">Pamięć, która została przypisana dla `b` (gdy zawiera ciąg "h"), kwalifikuje się do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c4709-125">The memory that had been allocated for `b` (when it contained the string "h") is then eligible for garbage collection.</span></span>

```csharp
string b = "h";
b += "ello";
```

<span data-ttu-id="c4709-126">Operatora można używać do dostępu tylko do odczytu do [](../operators/member-access-operators.md#indexer-operator-) `string`poszczególnych znaków. `[]`</span><span class="sxs-lookup"><span data-stu-id="c4709-126">The `[]` [operator](../operators/member-access-operators.md#indexer-operator-) can be used for readonly access to individual characters of a `string`.</span></span> <span data-ttu-id="c4709-127">Prawidłowe wartości zaczynają `0` się od i muszą być mniejsze niż długość: `string`</span><span class="sxs-lookup"><span data-stu-id="c4709-127">Valid values start at `0` and must be less than the length of the `string`:</span></span>

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

<span data-ttu-id="c4709-128">W podobny sposób `[]` operator może być również używany do iteracji dla każdego znaku `string`w:</span><span class="sxs-lookup"><span data-stu-id="c4709-128">In similar fashion, the `[]` operator can also be used for iterating over each character in a `string`:</span></span>

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

<span data-ttu-id="c4709-129">Literały ciągu są typu `string` i mogą być zapisywane w dwóch postaciach, cytowane i `@`ujęte w cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="c4709-129">String literals are of type `string` and can be written in two forms, quoted and `@`-quoted.</span></span> <span data-ttu-id="c4709-130">Cudzysłowy ujęte w cudzysłów są ujęte w znaki podwójnego cudzysłowu ("):</span><span class="sxs-lookup"><span data-stu-id="c4709-130">Quoted string literals are enclosed in double quotation marks ("):</span></span>

```csharp
"good morning"  // a string literal
```

<span data-ttu-id="c4709-131">Literały ciągu mogą zawierać dowolny literał znakowy.</span><span class="sxs-lookup"><span data-stu-id="c4709-131">String literals can contain any character literal.</span></span> <span data-ttu-id="c4709-132">Sekwencje ucieczki są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="c4709-132">Escape sequences are included.</span></span> <span data-ttu-id="c4709-133">Poniższy przykład używa sekwencji `\\` unikowej dla ukośnika odwrotnego, `\u0066` dla litery f i `\n` dla nowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="c4709-133">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
\\ Output:
\\ \f
\\  F
```

> [!NOTE]
> <span data-ttu-id="c4709-134">Kod `\udddd` ucieczki (gdzie `dddd` jest liczbą czterocyfrową) reprezentuje znak Unicode U +`dddd`.</span><span class="sxs-lookup"><span data-stu-id="c4709-134">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="c4709-135">Są również rozpoznawane osiem cyfrowych kodów ucieczki `\Udddddddd`Unicode:.</span><span class="sxs-lookup"><span data-stu-id="c4709-135">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>

<span data-ttu-id="c4709-136">[Literały ciągu Verbatim](../tokens/verbatim.md) zaczynają `@` się od i są również ujęte w znaki podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="c4709-136">[Verbatim string literals](../tokens/verbatim.md) start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="c4709-137">Przykład:</span><span class="sxs-lookup"><span data-stu-id="c4709-137">For example:</span></span>

```csharp
@"good morning"  // a string literal
```

<span data-ttu-id="c4709-138">Zaletą ciągów Verbatim jest to, że sekwencje unikowe *nie* są przetwarzane, co ułatwia pisanie, na przykład w pełni kwalifikowanej nazwy pliku systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="c4709-138">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified Windows file name:</span></span>

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

<span data-ttu-id="c4709-139">Aby uwzględnić podwójny cudzysłów w @-quoted ciągu, należy go dwukrotnie:</span><span class="sxs-lookup"><span data-stu-id="c4709-139">To include a double quotation mark in an @-quoted string, double it:</span></span>

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a><span data-ttu-id="c4709-140">Typ delegata</span><span class="sxs-lookup"><span data-stu-id="c4709-140">The delegate type</span></span>

<span data-ttu-id="c4709-141">Deklaracja typu delegata jest podobna do sygnatury metody.</span><span class="sxs-lookup"><span data-stu-id="c4709-141">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="c4709-142">Ma ona wartość zwracaną i dowolną liczbę parametrów dowolnego typu:</span><span class="sxs-lookup"><span data-stu-id="c4709-142">It has a return value and any number of parameters of any type:</span></span>

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

<span data-ttu-id="c4709-143">W programie .NET `System.Action` i `System.Func` typy zapewniają definicje ogólne dla wielu typowych delegatów.</span><span class="sxs-lookup"><span data-stu-id="c4709-143">In .NET, `System.Action` and `System.Func` types provide generic definitions for many common delegates.</span></span> <span data-ttu-id="c4709-144">Być może nie trzeba definiować nowych typów delegatów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="c4709-144">You likely don't need to define new custom delegate types.</span></span> <span data-ttu-id="c4709-145">Zamiast tego można tworzyć wystąpienia podanych typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="c4709-145">Instead, you can create instantiations of the provided generic types.</span></span>

<span data-ttu-id="c4709-146">A `delegate` to typ referencyjny, który może służyć do hermetyzacji metody nazwanej lub anonimowej.</span><span class="sxs-lookup"><span data-stu-id="c4709-146">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="c4709-147">Delegaty są podobne do wskaźników funkcji C++w; Delegaty są jednak bezpieczne i bezpieczne dla typów.</span><span class="sxs-lookup"><span data-stu-id="c4709-147">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="c4709-148">W przypadku aplikacji delegatów zobacz [Delegaty](../../programming-guide/delegates/index.md) i [delegatów ogólnych](../../programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="c4709-148">For applications of delegates, see [Delegates](../../programming-guide/delegates/index.md) and [Generic Delegates](../../programming-guide/generics/generic-delegates.md).</span></span> <span data-ttu-id="c4709-149">Delegaty są podstawą dla [zdarzeń](../../programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="c4709-149">Delegates are the basis for [Events](../../programming-guide/events/index.md).</span></span> <span data-ttu-id="c4709-150">Można utworzyć wystąpienie delegata, kojarząc go z metodami nazwanymi lub anonimowymi.</span><span class="sxs-lookup"><span data-stu-id="c4709-150">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span>

<span data-ttu-id="c4709-151">Obiekt delegowany musi być skonkretyzowany przy użyciu metody lub wyrażenia lambda, które ma zgodny typ zwracany i parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="c4709-151">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="c4709-152">Aby uzyskać więcej informacji na temat stopnia wariancji, który jest dozwolony w sygnaturze metody, zobacz [Wariancja w delegatach](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="c4709-152">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="c4709-153">Aby można było korzystać z metod anonimowych, delegat i kod, który ma być skojarzony z nim, są deklarowane razem.</span><span class="sxs-lookup"><span data-stu-id="c4709-153">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> 

## <a name="the-dynamic-type"></a><span data-ttu-id="c4709-154">Typ dynamiczny</span><span class="sxs-lookup"><span data-stu-id="c4709-154">The dynamic type</span></span>

<span data-ttu-id="c4709-155">`dynamic` Typ wskazuje, że użycie zmiennej i odwołań do jej elementów członkowskich obejście sprawdzania typu w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c4709-155">The `dynamic` type indicates that use of the variable and references to its members bypass compile-time type checking.</span></span> <span data-ttu-id="c4709-156">Zamiast tego te operacje są rozwiązywane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c4709-156">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="c4709-157">`dynamic` Typ upraszcza dostęp do interfejsów API modelu COM, takich jak interfejsy API usługi Office Automation, do dynamicznych interfejsów API, takich jak biblioteki IronPython, oraz do Document Object Model HTML (dom).</span><span class="sxs-lookup"><span data-stu-id="c4709-157">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>

<span data-ttu-id="c4709-158">Typ `dynamic` zachowuje się jak typ `object` w większości sytuacji.</span><span class="sxs-lookup"><span data-stu-id="c4709-158">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="c4709-159">W szczególności każde wyrażenie o wartości innej niż null można przekonwertować na `dynamic` typ.</span><span class="sxs-lookup"><span data-stu-id="c4709-159">In particular, any non-null expression can be converted to the `dynamic` type.</span></span> <span data-ttu-id="c4709-160">Typ różni się od `object` w tym, że operacje zawierające wyrażenia typu `dynamic` nie są rozpoznawane lub typem sprawdzonym przez kompilator. `dynamic`</span><span class="sxs-lookup"><span data-stu-id="c4709-160">The `dynamic` type differs from `object` in that operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="c4709-161">Kompilator pakuje razem informacje o operacji, a informacje te są później używane do szacowania operacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c4709-161">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="c4709-162">W ramach procesu zmienne typu `dynamic` są kompilowane do zmiennych typu. `object`</span><span class="sxs-lookup"><span data-stu-id="c4709-162">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="c4709-163">W związku z `dynamic` tym, typ istnieje tylko w czasie kompilacji, a nie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c4709-163">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>

<span data-ttu-id="c4709-164">Poniższy przykład kontrastuje zmienną typu `dynamic` do zmiennej typu. `object`</span><span class="sxs-lookup"><span data-stu-id="c4709-164">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="c4709-165">Aby sprawdzić typ każdej zmiennej w czasie kompilacji, umieść wskaźnik myszy nad `dyn` lub `obj` w `WriteLine` instrukcjach.</span><span class="sxs-lookup"><span data-stu-id="c4709-165">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="c4709-166">Skopiuj poniższy kod do edytora, w którym jest dostępna funkcja IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c4709-166">Copy the following code into an editor where IntelliSense is available.</span></span> <span data-ttu-id="c4709-167">Funkcja IntelliSense wyświetla dynamiczne `dyn` dla **obiektów** `obj`i.</span><span class="sxs-lookup"><span data-stu-id="c4709-167">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<span data-ttu-id="c4709-168">Instrukcje wyświetlają `dyn` typy czasu wykonywania i `obj`. <xref:System.Console.WriteLine%2A></span><span class="sxs-lookup"><span data-stu-id="c4709-168">The <xref:System.Console.WriteLine%2A> statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="c4709-169">W tym momencie oba mają ten sam typ, liczba całkowita.</span><span class="sxs-lookup"><span data-stu-id="c4709-169">At that point, both have the same type, integer.</span></span> <span data-ttu-id="c4709-170">Generowane są następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="c4709-170">The following output is produced:</span></span>

```console
System.Int32
System.Int32
```

<span data-ttu-id="c4709-171">Aby wyświetlić różnicę między `dyn` i `obj` w czasie kompilacji, Dodaj następujące dwa wiersze `WriteLine` między deklaracjami i instrukcjami w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c4709-171">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 <span data-ttu-id="c4709-172">Zgłoszono błąd kompilatora dla próby dodania liczby całkowitej i obiektu w wyrażeniu `obj + 3`.</span><span class="sxs-lookup"><span data-stu-id="c4709-172">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="c4709-173">Nie jest jednak zgłaszany `dyn + 3`żaden błąd.</span><span class="sxs-lookup"><span data-stu-id="c4709-173">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="c4709-174">Wyrażenie, które zawiera `dyn` nie jest sprawdzane w czasie kompilacji, ponieważ `dyn` jest `dynamic`typem.</span><span class="sxs-lookup"><span data-stu-id="c4709-174">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>

<span data-ttu-id="c4709-175">Poniższy przykład używa `dynamic` w kilku deklaracjach.</span><span class="sxs-lookup"><span data-stu-id="c4709-175">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="c4709-176">Metoda `Main` ta również kontrastuje sprawdzanie typu czasu kompilacji z sprawdzaniem typu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c4709-176">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a><span data-ttu-id="c4709-177">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4709-177">See also</span></span>

- [<span data-ttu-id="c4709-178">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c4709-178">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c4709-179">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c4709-179">C# Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="c4709-180">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c4709-180">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="c4709-181">Używanie typu dynamicznego</span><span class="sxs-lookup"><span data-stu-id="c4709-181">Using Type dynamic</span></span>](../../programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="c4709-182">Najlepsze rozwiązania dotyczące używania ciągów</span><span class="sxs-lookup"><span data-stu-id="c4709-182">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)
- [<span data-ttu-id="c4709-183">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="c4709-183">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="c4709-184">Tworzenie nowych ciągów</span><span class="sxs-lookup"><span data-stu-id="c4709-184">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="c4709-185">Operatory testowania typu i rzutowania</span><span class="sxs-lookup"><span data-stu-id="c4709-185">Type-testing and cast operators</span></span>](../operators/type-testing-and-cast.md)
- [<span data-ttu-id="c4709-186">Instrukcje: bezpieczne rzutowanie przy użyciu dopasowania wzorca i operatorów AS i is</span><span class="sxs-lookup"><span data-stu-id="c4709-186">How to: safely cast using pattern matching and the as and is operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="c4709-187">Przewodnik: Tworzenie obiektów dynamicznych i korzystanie z nich</span><span class="sxs-lookup"><span data-stu-id="c4709-187">Walkthrough: creating and using dynamic objects</span></span>](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
