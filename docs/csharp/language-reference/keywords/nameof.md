---
title: nameof (odwołanie w C#)
ms.date: 06/16/2017
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 8a850633bee26120a12f9d72e9d18b5af131d267
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="nameof-c-reference"></a>nameof (odwołanie w C#)

Używany do uzyskania prostego ciągu (niekwalifikowane) nazwę zmiennej, typu lub elementu członkowskiego.  

Podczas raportowania błędów w kodzie, Podłączanie model widok kontroler (MVC) łącza, wyzwalania zdarzenia zmiany właściwości, itd., często mają być przechwytywane nazwę ciągu metody.  Przy użyciu `nameof` pomaga zapewnić kodu prawidłowy przy zmianie nazwy definicji.  Przed konieczne było użycie literałów ciągów do odwoływania się do definicji, czyli łamliwa przy zmianie nazwy elementy kodu, ponieważ narzędzia nie wiadomo, aby sprawdzić te literałów ciągów.  
  
 A `nameof` wyrażenie ma tego formularza:  
  
```csharp  
if (x == null) throw new ArgumentNullException(nameof(x));  
WriteLine(nameof(person.Address.ZipCode)); // prints "ZipCode"  
```  
  
## <a name="key-use-cases"></a>Przypadki użycia klucza  
 Poniższe przykłady pokazują przypadków użycia klucza dla `nameof`.  
  
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
  
nameof(C) -> "C"  
nameof(C.Method1) -> "Method1"   
nameof(C.Method2) -> "Method2"  
nameof(c.Method1) -> "Method1"   
nameof(c.Method2) -> "Method2"  
nameof(z) -> "z" // inside of Method2 ok, inside Method1 is a compiler error  
nameof(Stuff) = "Stuff"  
nameof(T) -> "T" // works inside of method but not in attributes on the method  
nameof(f) -> "f"  
nameof(f<T>) -> syntax error  
nameof(f<>) -> syntax error  
nameof(Method2()) -> error "This expression does not have a name"  
```  
  
## <a name="remarks"></a>Uwagi  
 Argument `nameof` musi być prostą nazwą, nazwy kwalifikowanej, dostęp do elementu członkowskiego, dostępu bazowego z określonego elementu członkowskiego lub dostęp z określonego elementu członkowskiego.  Wyrażenie argumentu identyfikuje definicji kodu, ale nigdy nie jest obliczane.  
  
 Ponieważ argument musi być wyrażeniem składnię, istnieje wiele niedopuszczalne rzeczy, które nie są przydatne do tworzenia listy.  Warto zauważyć, że tworzy błędy są następujące: wstępnie zdefiniowanych typów (na przykład `int` lub `void`), typy dopuszczające wartości zerowe (`Point?`), typy tablicowe (`Customer[,]`), typów wskaźnika (`Buffer*`), kwalifikowaną alias (`A::B` ), a niepowiązanych typów ogólnych (`Dictionary<,>`), przetwarzania wstępnego symboli (`DEBUG`) oraz etykiety (`loop:`).  
  
 Jeśli trzeba uzyskać w pełni kwalifikowaną nazwę, możesz użyć `typeof` wyrażenie wraz z programem `nameof`.  Na przykład:
```csharp  
class C {
    void f(int i) {  
        Log($"{typeof(C)}.{nameof(f)}", "method entry");  
    }
}
``` 

 Niestety `typeof` nie jest wyrażeniem stałym, takich jak `nameof`, więc `typeof` nie można używać w połączeniu z `nameof` w tych samych umieszcza jako `nameof`.  Na przykład następujące mogłoby spowodować błąd kompilacji CS0182:
 ```csharp  
[DebuggerDisplay("={" + typeof(C) + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```    
 W przykładach Zobacz można użyć nazwy typu i dostęp do nazwy metody wystąpienia.  Nie trzeba mieć wystąpienia typu, jako wymaganego w obliczane wyrażenia.  Może być bardzo wygodny w niektórych sytuacjach i przy użyciu nazwy typu, ponieważ odnosi się tylko do nazwy i nie używa dane wystąpienia, nie trzeba przeprowadzać contrive wystąpienie zmiennej lub wyrażenie.  
  
 Możesz odwoływać się elementy członkowskie klasy w wyrażeniach atrybut klasy.  
  
 Nie istnieje sposób można pobrać informacji podpisów, takich jak "`Method1 (str, str)`".  Jedną z metod w tym celu jest użycie wyrażenia `Expression e = () => A.B.Method1("s1", "s2")`i ściągania MemberInfo z wynikowe drzewo wyrażeń.  
  
## <a name="language-specifications"></a>Specyfikacje języka  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [typeof](../../../csharp/language-reference/keywords/typeof.md)  
 
