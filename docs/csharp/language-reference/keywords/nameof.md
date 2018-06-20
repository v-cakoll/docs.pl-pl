---
title: nameof (odwołanie w C#)
ms.date: 06/16/2017
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 2695095aa4bf2035d8766f3cbcb82f4fbb290e22
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208377"
---
# <a name="nameof-c-reference"></a><span data-ttu-id="1578b-102">nameof (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1578b-102">nameof (C# Reference)</span></span>

<span data-ttu-id="1578b-103">Używany do uzyskania prostego ciągu (niekwalifikowane) nazwę zmiennej, typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="1578b-103">Used to obtain the simple (unqualified) string name of a variable, type, or member.</span></span>  

<span data-ttu-id="1578b-104">Podczas raportowania błędów w kodzie, Podłączanie model widok kontroler (MVC) łącza, wyzwalania zdarzenia zmiany właściwości, itd., często mają być przechwytywane nazwę ciągu metody.</span><span class="sxs-lookup"><span data-stu-id="1578b-104">When reporting errors in code, hooking up model-view-controller (MVC) links, firing property changed events, etc., you often want to capture the string name of a method.</span></span>  <span data-ttu-id="1578b-105">Przy użyciu `nameof` pomaga zapewnić kodu prawidłowy przy zmianie nazwy definicji.</span><span class="sxs-lookup"><span data-stu-id="1578b-105">Using `nameof` helps keep your code valid when renaming definitions.</span></span>  <span data-ttu-id="1578b-106">Przed konieczne było użycie literałów ciągów do odwoływania się do definicji, czyli łamliwa przy zmianie nazwy elementy kodu, ponieważ narzędzia nie wiadomo, aby sprawdzić te literałów ciągów.</span><span class="sxs-lookup"><span data-stu-id="1578b-106">Before, you had to use string literals to refer to definitions, which is brittle when renaming code elements because tools do not know to check these string literals.</span></span>  
  
 <span data-ttu-id="1578b-107">A `nameof` wyrażenie ma tego formularza:</span><span class="sxs-lookup"><span data-stu-id="1578b-107">A `nameof` expression has this form:</span></span>  
  
```csharp  
if (x == null) throw new ArgumentNullException(nameof(x));  
WriteLine(nameof(person.Address.ZipCode)); // prints "ZipCode"  
```  
  
## <a name="key-use-cases"></a><span data-ttu-id="1578b-108">Przypadki użycia klucza</span><span class="sxs-lookup"><span data-stu-id="1578b-108">Key Use Cases</span></span>  
 <span data-ttu-id="1578b-109">Poniższe przykłady pokazują przypadków użycia klucza dla `nameof`.</span><span class="sxs-lookup"><span data-stu-id="1578b-109">These examples show the key use cases for `nameof`.</span></span>  
  
 <span data-ttu-id="1578b-110">Waliduj parametry:</span><span class="sxs-lookup"><span data-stu-id="1578b-110">Validate parameters:</span></span>  
 ```csharp  
void f(string s) {  
    if (s == null) throw new ArgumentNullException(nameof(s));  
}  
```  
  
 <span data-ttu-id="1578b-111">Akcja kontrolera MVC łącza:</span><span class="sxs-lookup"><span data-stu-id="1578b-111">MVC Action links:</span></span>  
 ```html  
<%= Html.ActionLink("Sign up",  
             @typeof(UserController),  
             @nameof(UserController.SignUp))  
%>  
```  
  
 <span data-ttu-id="1578b-112">INotifyPropertyChanged:</span><span class="sxs-lookup"><span data-stu-id="1578b-112">INotifyPropertyChanged:</span></span>  
 ```csharp  
int p {  
    get { return this.p; }  
    set { this.p = value; PropertyChanged(this, new PropertyChangedEventArgs(nameof(this.p)); } // nameof(p) works too  
}  
```  
  
 <span data-ttu-id="1578b-113">Właściwości zależności XAML:</span><span class="sxs-lookup"><span data-stu-id="1578b-113">XAML dependency property:</span></span>  
 ```csharp  
public static DependencyProperty AgeProperty = DependencyProperty.Register(nameof(Age), typeof(int), typeof(C));  
```  
  
 <span data-ttu-id="1578b-114">Rejestrowanie:</span><span class="sxs-lookup"><span data-stu-id="1578b-114">Logging:</span></span>  
 ```csharp  
void f(int i) {  
    Log(nameof(f), "method entry");  
}  
```  
  
 <span data-ttu-id="1578b-115">Atrybuty:</span><span class="sxs-lookup"><span data-stu-id="1578b-115">Attributes:</span></span>  
 ```csharp  
[DebuggerDisplay("={" + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```  
  
## <a name="examples"></a><span data-ttu-id="1578b-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="1578b-116">Examples</span></span>  
 <span data-ttu-id="1578b-117">C# przykłady:</span><span class="sxs-lookup"><span data-stu-id="1578b-117">Some C# examples:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="1578b-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1578b-118">Remarks</span></span>  
 <span data-ttu-id="1578b-119">Argument `nameof` musi być prostą nazwą, nazwy kwalifikowanej, dostęp do elementu członkowskiego, dostępu bazowego z określonego elementu członkowskiego lub dostęp z określonego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="1578b-119">The argument to `nameof` must be a simple name, qualified name, member access, base access with a specified member, or this access with a specified member.</span></span>  <span data-ttu-id="1578b-120">Wyrażenie argumentu identyfikuje definicji kodu, ale nigdy nie jest obliczane.</span><span class="sxs-lookup"><span data-stu-id="1578b-120">The argument expression identifies a code definition, but it is never evaluated.</span></span>  
  
 <span data-ttu-id="1578b-121">Ponieważ argument musi być wyrażeniem składnię, istnieje wiele niedopuszczalne rzeczy, które nie są przydatne do tworzenia listy.</span><span class="sxs-lookup"><span data-stu-id="1578b-121">Because the argument needs to be an expression syntactically, there are many things disallowed that are not useful to list.</span></span>  <span data-ttu-id="1578b-122">Warto zauważyć, że tworzy błędy są następujące: wstępnie zdefiniowanych typów (na przykład `int` lub `void`), typy dopuszczające wartości zerowe (`Point?`), typy tablicowe (`Customer[,]`), typów wskaźnika (`Buffer*`), kwalifikowaną alias (`A::B` ), a niepowiązanych typów ogólnych (`Dictionary<,>`), przetwarzania wstępnego symboli (`DEBUG`) oraz etykiety (`loop:`).</span><span class="sxs-lookup"><span data-stu-id="1578b-122">The following are worth mentioning that produce errors: predefined types (for example, `int` or `void`), nullable types (`Point?`), array types (`Customer[,]`), pointer types (`Buffer*`), qualified alias (`A::B`), and unbound generic types (`Dictionary<,>`), preprocessing symbols (`DEBUG`), and labels (`loop:`).</span></span>  
  
 <span data-ttu-id="1578b-123">Jeśli trzeba uzyskać w pełni kwalifikowaną nazwę, możesz użyć `typeof` wyrażenie wraz z programem `nameof`.</span><span class="sxs-lookup"><span data-stu-id="1578b-123">If you need to get the fully-qualified name, you can use the `typeof` expression along with `nameof`.</span></span>  <span data-ttu-id="1578b-124">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1578b-124">For example:</span></span>
```csharp  
class C {
    void f(int i) {  
        Log($"{typeof(C)}.{nameof(f)}", "method entry");  
    }
}
``` 

 <span data-ttu-id="1578b-125">Niestety `typeof` nie jest wyrażeniem stałym, takich jak `nameof`, więc `typeof` nie można używać w połączeniu z `nameof` w tych samych umieszcza jako `nameof`.</span><span class="sxs-lookup"><span data-stu-id="1578b-125">Unfortunately `typeof` is not a constant expression like `nameof`, so `typeof` cannot be used in conjunction with `nameof` in all the same places as `nameof`.</span></span>  <span data-ttu-id="1578b-126">Na przykład następujące mogłoby spowodować błąd kompilacji CS0182:</span><span class="sxs-lookup"><span data-stu-id="1578b-126">For example, the following would cause a CS0182 compile error:</span></span>
 ```csharp  
[DebuggerDisplay("={" + typeof(C) + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```    
 <span data-ttu-id="1578b-127">W przykładach Zobacz można użyć nazwy typu i dostęp do nazwy metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1578b-127">In the examples you see that you can use a type name and access an instance method name.</span></span>  <span data-ttu-id="1578b-128">Nie trzeba mieć wystąpienia typu, jako wymaganego w obliczane wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1578b-128">You do not need to have an instance of the type, as required in evaluated expressions.</span></span>  <span data-ttu-id="1578b-129">Może być bardzo wygodny w niektórych sytuacjach i przy użyciu nazwy typu, ponieważ odnosi się tylko do nazwy i nie używa dane wystąpienia, nie trzeba przeprowadzać contrive wystąpienie zmiennej lub wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="1578b-129">Using the type name can be very convenient in some situations, and since you are just referring to the name and not using instance data, you do not need to contrive an instance variable or expression.</span></span>  
  
 <span data-ttu-id="1578b-130">Możesz odwoływać się elementy członkowskie klasy w wyrażeniach atrybut klasy.</span><span class="sxs-lookup"><span data-stu-id="1578b-130">You can reference the members of a class in attribute expressions on the class.</span></span>  
  
 <span data-ttu-id="1578b-131">Nie istnieje sposób można pobrać informacji podpisów, takich jak "`Method1 (str, str)`".</span><span class="sxs-lookup"><span data-stu-id="1578b-131">There is no way to get a signatures information such as "`Method1 (str, str)`".</span></span>  <span data-ttu-id="1578b-132">Jedną z metod w tym celu jest użycie wyrażenia `Expression e = () => A.B.Method1("s1", "s2")`i ściągania MemberInfo z wynikowe drzewo wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="1578b-132">One way to do that is to use an Expression, `Expression e = () => A.B.Method1("s1", "s2")`, and pull the MemberInfo from the resulting expression tree.</span></span>  
  
## <a name="language-specifications"></a><span data-ttu-id="1578b-133">Specyfikacje języka</span><span class="sxs-lookup"><span data-stu-id="1578b-133">Language Specifications</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1578b-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1578b-134">See Also</span></span>  
 [<span data-ttu-id="1578b-135">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1578b-135">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1578b-136">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1578b-136">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1578b-137">typeof</span><span class="sxs-lookup"><span data-stu-id="1578b-137">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)  
 
