---
title: nameof - C# odwołania
ms.custom: seodec18
ms.date: 06/16/2017
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 61c0744168a6fef0f8c8cfb589602e7aeff0c48b
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241496"
---
# <a name="nameof-c-reference"></a>nameof (odwołanie w C#)

Można uzyskać prosty ciąg (niekwalifikowanej) nazwy zmiennej, typu lub elementu członkowskiego.  

Podczas zgłaszania błędów w kodzie, Podłączanie model-view-controller (MVC) łączy, wyzwalanie zdarzenia zmiany właściwości, itd., często mają być przechwytywane nazwą parametrów metody.  Za pomocą `nameof` pomaga zapewnić kodu prawidłowe przy zmianie nazwy definicji.  Wcześniej trzeba było Używaj literałów ciągów do odwoływania się do definicji, który jest elementem wrażliwym, podczas zmiany nazwy elementów kodu, ponieważ narzędzia nie wiadomo, aby sprawdzić te literałów ciągów.  
  
 A `nameof` wyrażenie ma tę formę:  
  
```csharp  
if (x == null) throw new ArgumentNullException(nameof(x));  
WriteLine(nameof(person.Address.ZipCode)); // prints "ZipCode"  
```  
  
## <a name="key-use-cases"></a>Przypadki użycia klucza  
 W poniższych przykładach pokazano przypadki użycia klucza `nameof`.  
  
 Waliduj parametry:  
 ```csharp  
void f(string s) {  
    if (s == null) throw new ArgumentNullException(nameof(s));  
}  
```  
  
 Akcja kontrolera MVC łącza:  
 ```html  
<%= Html.ActionLink("Sign up",  
             @typeof(UserController),  
             @nameof(UserController.SignUp))  
%>  
```  
  
 INotifyPropertyChanged:  
 ```csharp  
int p {  
    get { return this.p; }  
    set { this.p = value; PropertyChanged(this, new PropertyChangedEventArgs(nameof(this.p)); } // nameof(p) works too  
}  
```  
  
 Właściwości zależności XAML:  
 ```csharp  
public static DependencyProperty AgeProperty = DependencyProperty.Register(nameof(Age), typeof(int), typeof(C));  
```  
  
 Rejestrowanie:  
 ```csharp  
void f(int i) {  
    Log(nameof(f), "method entry");  
}  
```  
  
 Atrybuty:  
 ```csharp  
[DebuggerDisplay("={" + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```  
  
## <a name="examples"></a>Przykłady  
 C# przykłady:  
  
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
  
## <a name="remarks"></a>Uwagi  
 Argument `nameof` musi być prostą nazwą, kwalifikowana nazwa, dostęp do elementu członkowskiego, dostępu bazowego, z określonego elementu członkowskiego lub dostęp za pomocą określonego elementu członkowskiego.  Wyrażenie argumentu identyfikuje definicję kodu, ale nigdy nie jest obliczane.  
  
 Argument musi być wyrażeniem syntaktycznie, dlatego są niedozwolone, wiele rzeczy, które nie są przydatne do tworzenia listy.  Następujące warto wspomnieć o, który generuje błędy: wstępnie zdefiniowanych typów (na przykład `int` lub `void`), typy dopuszczające wartości zerowe (`Point?`), tablicy typów (`Customer[,]`), typów wskaźnika (`Buffer*`), aliasu kwalifikowaną (`A::B` ), a wskazanych typów ogólnych (`Dictionary<,>`), przetwarzania wstępnego symbole (`DEBUG`) i etykiet (`loop:`).  
  
 Jeśli musisz pobrać w pełni kwalifikowaną nazwę, możesz użyć `typeof` wraz z wyrażeniem `nameof`.  Na przykład:
```csharp  
class C {
    void f(int i) {  
        Log($"{typeof(C)}.{nameof(f)}", "method entry");  
    }
}
``` 

 Niestety `typeof` nie jest wyrażeniem stałym, takich jak `nameof`, więc `typeof` nie można używać w połączeniu z `nameof` w tych samych miejsc co `nameof`.  Na przykład następujące mogłoby spowodować błąd kompilacji CS0182:
 ```csharp  
[DebuggerDisplay("={" + typeof(C) + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```    
 W przykładach zobaczysz, że można użyć nazwy typu i dostęp do nazwy metody wystąpienia.  Nie trzeba mieć wystąpienia typu, jako wymaganego w wyrażenia ocenianego.  Może być wygodna w taki sposób, w niektórych sytuacjach i nazwy typu, ponieważ właśnie odwołujesz się do nazwy i nie używa danych wystąpienia, nie trzeba contrive wystąpienie zmiennej lub wyrażenia.  
  
 Możesz odwoływać się elementy członkowskie klasy w wyrażeniach atrybut w klasie.  
  
 Nie ma możliwości można pobrać informacji podpisów, takie jak "`Method1 (str, str)`".  Jednym ze sposobów, aby to zrobić, jest użycie wyrażenia `Expression e = () => A.B.Method1("s1", "s2")`i ściąganie MemberInfo z wynikowego drzewa wyrażeń.  
  
## <a name="language-specifications"></a>Specyfikacje języka  

Aby uzyskać więcej informacji, zobacz [wyrażeń Nameof](~/_csharplang/spec/expressions.md#nameof-expressions) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
 
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [typeof](../../../csharp/language-reference/keywords/typeof.md)  
