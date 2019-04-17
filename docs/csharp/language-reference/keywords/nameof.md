---
title: nameof - C# odwołania
ms.custom: seodec18
ms.date: 06/16/2017
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 04de4dc6f320213c1a9c95b1abb92488fac0a81f
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59614093"
---
# <a name="nameof-c-reference"></a><span data-ttu-id="40bb4-102">nameof (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="40bb4-102">nameof (C# Reference)</span></span>

<span data-ttu-id="40bb4-103">Można uzyskać prosty ciąg (niekwalifikowanej) nazwy zmiennej, typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="40bb4-103">Used to obtain the simple (unqualified) string name of a variable, type, or member.</span></span>

<span data-ttu-id="40bb4-104">Podczas zgłaszania błędów w kodzie, Podłączanie model-view-controller (MVC) łączy, wyzwalanie zdarzenia zmiany właściwości, itd., często mają być przechwytywane nazwą parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="40bb4-104">When reporting errors in code, hooking up model-view-controller (MVC) links, firing property changed events, etc., you often want to capture the string name of a method.</span></span>  <span data-ttu-id="40bb4-105">Za pomocą `nameof` pomaga zapewnić kodu prawidłowe przy zmianie nazwy definicji.</span><span class="sxs-lookup"><span data-stu-id="40bb4-105">Using `nameof` helps keep your code valid when renaming definitions.</span></span>  <span data-ttu-id="40bb4-106">Wcześniej trzeba było Używaj literałów ciągów do odwoływania się do definicji, który jest elementem wrażliwym, podczas zmiany nazwy elementów kodu, ponieważ narzędzia nie wiadomo, aby sprawdzić te literałów ciągów.</span><span class="sxs-lookup"><span data-stu-id="40bb4-106">Before, you had to use string literals to refer to definitions, which is brittle when renaming code elements because tools do not know to check these string literals.</span></span>

<span data-ttu-id="40bb4-107">A `nameof` wyrażenie ma tę formę:</span><span class="sxs-lookup"><span data-stu-id="40bb4-107">A `nameof` expression has this form:</span></span>

```csharp
if (x == null) throw new ArgumentNullException(nameof(x));
WriteLine(nameof(person.Address.ZipCode)); // prints "ZipCode"
```

## <a name="key-use-cases"></a><span data-ttu-id="40bb4-108">Przypadki użycia klucza</span><span class="sxs-lookup"><span data-stu-id="40bb4-108">Key Use Cases</span></span>

<span data-ttu-id="40bb4-109">W poniższych przykładach pokazano przypadki użycia klucza `nameof`.</span><span class="sxs-lookup"><span data-stu-id="40bb4-109">These examples show the key use cases for `nameof`.</span></span>

<span data-ttu-id="40bb4-110">Waliduj parametry:</span><span class="sxs-lookup"><span data-stu-id="40bb4-110">Validate parameters:</span></span>

 ```csharp
void f(string s) {
    if (s == null) throw new ArgumentNullException(nameof(s));
}
```

<span data-ttu-id="40bb4-111">Akcja kontrolera MVC łącza:</span><span class="sxs-lookup"><span data-stu-id="40bb4-111">MVC Action links:</span></span>

```html
<%= Html.ActionLink("Sign up",
             @typeof(UserController),
             @nameof(UserController.SignUp))
%>
```

<span data-ttu-id="40bb4-112">INotifyPropertyChanged:</span><span class="sxs-lookup"><span data-stu-id="40bb4-112">INotifyPropertyChanged:</span></span>

```csharp
int p {
    get { return this.p; }
    set { this.p = value; PropertyChanged(this, new PropertyChangedEventArgs(nameof(this.p)); } // nameof(p) works too
}
```

<span data-ttu-id="40bb4-113">Właściwości zależności XAML:</span><span class="sxs-lookup"><span data-stu-id="40bb4-113">XAML dependency property:</span></span>

```csharp
public static DependencyProperty AgeProperty = DependencyProperty.Register(nameof(Age), typeof(int), typeof(C));
```

<span data-ttu-id="40bb4-114">Rejestrowanie:</span><span class="sxs-lookup"><span data-stu-id="40bb4-114">Logging:</span></span>

```csharp
void f(int i) {
    Log(nameof(f), "method entry");
}
```

<span data-ttu-id="40bb4-115">Atrybuty:</span><span class="sxs-lookup"><span data-stu-id="40bb4-115">Attributes:</span></span>

```csharp
[DebuggerDisplay("={" + nameof(GetString) + "()}")]
class C {
    string GetString() { }
}
```

## <a name="examples"></a><span data-ttu-id="40bb4-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="40bb4-116">Examples</span></span>

<span data-ttu-id="40bb4-117">C# przykłady:</span><span class="sxs-lookup"><span data-stu-id="40bb4-117">Some C# examples:</span></span>

```csharp
using Stuff = Some.Cool.Functionality
class C {
    static int Method1 (string x, int y) {}
    static int Method1 (string x, string y) {}
    int Method2 (int z) {}
    string f<T>() => nameof(T);
}

var c = new C()

class Test {
    static void Main (string[] args) {
        Console.WriteLine(nameof(C)); // -> "C"
        Console.WriteLine(nameof(C.Method1)); // -> "Method1"
        Console.WriteLine(nameof(C.Method2)); // -> "Method2"
        Console.WriteLine(nameof(c.Method1)); // -> "Method1"
        Console.WriteLine(nameof(c.Method2)); // -> "Method2"
        // Console.WriteLine(nameof(z)); -> "z" [inside of Method2 ok, inside Method1 is a compiler error]
        Console.WriteLine(nameof(Stuff)); // -> "Stuff"
        // Console.WriteLine(nameof(T)); -> "T" [works inside of method but not in attributes on the method]
        Console.WriteLine(nameof(f)); // -> "f"
        // Console.WriteLine(nameof(f<T>)); -> [syntax error]
        // Console.WriteLine(nameof(f<>)); -> [syntax error]
        // Console.WriteLine(nameof(Method2())); -> [error "This expression does not have a name"]
    }
}
```

## <a name="remarks"></a><span data-ttu-id="40bb4-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40bb4-118">Remarks</span></span>

<span data-ttu-id="40bb4-119">Argument `nameof` musi być prostą nazwą, kwalifikowana nazwa, dostęp do elementu członkowskiego, dostępu bazowego, z określonego elementu członkowskiego lub dostęp za pomocą określonego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="40bb4-119">The argument to `nameof` must be a simple name, qualified name, member access, base access with a specified member, or this access with a specified member.</span></span>  <span data-ttu-id="40bb4-120">Wyrażenie argumentu identyfikuje definicję kodu, ale nigdy nie jest obliczane.</span><span class="sxs-lookup"><span data-stu-id="40bb4-120">The argument expression identifies a code definition, but it is never evaluated.</span></span>

<span data-ttu-id="40bb4-121">Argument musi być wyrażeniem syntaktycznie, dlatego są niedozwolone, wiele rzeczy, które nie są przydatne do tworzenia listy.</span><span class="sxs-lookup"><span data-stu-id="40bb4-121">Because the argument needs to be an expression syntactically, there are many things disallowed that are not useful to list.</span></span>  <span data-ttu-id="40bb4-122">Następujące warto wspomnieć o, który generuje błędy: wstępnie zdefiniowanych typów (na przykład `int` lub `void`), typy dopuszczające wartości zerowe (`Point?`), tablicy typów (`Customer[,]`), typów wskaźnika (`Buffer*`), aliasu kwalifikowaną (`A::B` ), a wskazanych typów ogólnych (`Dictionary<,>`), przetwarzania wstępnego symbole (`DEBUG`) i etykiet (`loop:`).</span><span class="sxs-lookup"><span data-stu-id="40bb4-122">The following are worth mentioning that produce errors: predefined types (for example, `int` or `void`), nullable types (`Point?`), array types (`Customer[,]`), pointer types (`Buffer*`), qualified alias (`A::B`), and unbound generic types (`Dictionary<,>`), preprocessing symbols (`DEBUG`), and labels (`loop:`).</span></span>

<span data-ttu-id="40bb4-123">Jeśli musisz pobrać w pełni kwalifikowaną nazwę, możesz użyć `typeof` wraz z wyrażeniem `nameof`.</span><span class="sxs-lookup"><span data-stu-id="40bb4-123">If you need to get the fully-qualified name, you can use the `typeof` expression along with `nameof`.</span></span>  <span data-ttu-id="40bb4-124">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="40bb4-124">For example:</span></span>

```csharp
class C {
    void f(int i) {
        Log($"{typeof(C)}.{nameof(f)}", "method entry");
    }
}
```

<span data-ttu-id="40bb4-125">Niestety `typeof` nie jest wyrażeniem stałym, takich jak `nameof`, więc `typeof` nie można używać w połączeniu z `nameof` w tych samych miejsc co `nameof`.</span><span class="sxs-lookup"><span data-stu-id="40bb4-125">Unfortunately `typeof` is not a constant expression like `nameof`, so `typeof` cannot be used in conjunction with `nameof` in all the same places as `nameof`.</span></span>  <span data-ttu-id="40bb4-126">Na przykład następujące mogłoby spowodować błąd kompilacji CS0182:</span><span class="sxs-lookup"><span data-stu-id="40bb4-126">For example, the following would cause a CS0182 compile error:</span></span>

```csharp
[DebuggerDisplay("={" + typeof(C) + nameof(GetString) + "()}")]
class C {
    string GetString() { }
}
```

<span data-ttu-id="40bb4-127">W przykładach zobaczysz, że można użyć nazwy typu i dostęp do nazwy metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="40bb4-127">In the examples you see that you can use a type name and access an instance method name.</span></span>  <span data-ttu-id="40bb4-128">Nie trzeba mieć wystąpienia typu, jako wymaganego w wyrażenia ocenianego.</span><span class="sxs-lookup"><span data-stu-id="40bb4-128">You do not need to have an instance of the type, as required in evaluated expressions.</span></span>  <span data-ttu-id="40bb4-129">Może być wygodna w taki sposób, w niektórych sytuacjach i nazwy typu, ponieważ właśnie odwołujesz się do nazwy i nie używa danych wystąpienia, nie trzeba contrive wystąpienie zmiennej lub wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="40bb4-129">Using the type name can be very convenient in some situations, and since you are just referring to the name and not using instance data, you do not need to contrive an instance variable or expression.</span></span>

<span data-ttu-id="40bb4-130">Możesz odwoływać się elementy członkowskie klasy w wyrażeniach atrybut w klasie.</span><span class="sxs-lookup"><span data-stu-id="40bb4-130">You can reference the members of a class in attribute expressions on the class.</span></span>

<span data-ttu-id="40bb4-131">Nie ma możliwości można pobrać informacji podpisów, takie jak "`Method1 (str, str)`".</span><span class="sxs-lookup"><span data-stu-id="40bb4-131">There is no way to get a signatures information such as "`Method1 (str, str)`".</span></span>  <span data-ttu-id="40bb4-132">Jednym ze sposobów, aby to zrobić, jest użycie wyrażenia `Expression e = () => A.B.Method1("s1", "s2")`i ściąganie MemberInfo z wynikowego drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="40bb4-132">One way to do that is to use an Expression, `Expression e = () => A.B.Method1("s1", "s2")`, and pull the MemberInfo from the resulting expression tree.</span></span>

## <a name="language-specifications"></a><span data-ttu-id="40bb4-133">Specyfikacje języka</span><span class="sxs-lookup"><span data-stu-id="40bb4-133">Language Specifications</span></span>

<span data-ttu-id="40bb4-134">Aby uzyskać więcej informacji, zobacz [wyrażeń Nameof](~/_csharplang/spec/expressions.md#nameof-expressions) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="40bb4-134">For more information, see [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="40bb4-135">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="40bb4-135">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="40bb4-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40bb4-136">See also</span></span>

- [<span data-ttu-id="40bb4-137">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="40bb4-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="40bb4-138">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="40bb4-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="40bb4-139">typeof</span><span class="sxs-lookup"><span data-stu-id="40bb4-139">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)
