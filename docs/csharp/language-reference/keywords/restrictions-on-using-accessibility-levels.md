---
title: Ograniczenia dotyczące używania poziomów ułatwień dostępu (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: fd2f9b11523aac1cb720559db44aa36029d52ddb
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960908"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a>Ograniczenia dotyczące używania poziomów ułatwień dostępu (odwołanie w C#)
Po określeniu typu w deklaracji, sprawdź, czy poziom dostępności tego typu jest zależne od poziomu dostępności elementu członkowskiego lub innego typu. Na przykład bezpośredniej klasy podstawowej musi być co najmniej tak samo dostępna jak klasy pochodnej. Następujące deklaracje spowodują błąd kompilatora, ponieważ klasa bazowa `BaseClass` jest mniej dostępny niż `MyClass`:  
  
```csharp  
class BaseClass {...}  
public class MyClass: BaseClass {...} // Error  
```  
  
 W poniższej tabeli podsumowano ograniczenia dotyczące poziomów deklarowana dostępność metody.  
  
|Kontekst|Uwagi|  
|-------------|-------------|  
|[Klasy](../../../csharp/programming-guide/classes-and-structs/classes.md)|Bezpośrednie klasy bazowej typu klasy musi być co najmniej tak samo dostępna jak samego typu klasy.|  
|[Interfejsy](../../../csharp/programming-guide/interfaces/index.md)|Jawne interfejsy podstawowe typu interfejsu, musi być co najmniej tak samo dostępna jak samego typu interfejsu.|  
|[Delegaci](../../../csharp/programming-guide/delegates/index.md)|Typ zwracany i typy parametrów typu delegowanego musi być co najmniej tak samo dostępna jak samego typu delegata.|  
|[Stałe](../../../csharp/programming-guide/classes-and-structs/constants.md)|Typ stałej musi być co najmniej tak samo dostępna jak stała się.|  
|[Pola](../../../csharp/programming-guide/classes-and-structs/fields.md)|Typ pola musi być co najmniej tak samo dostępna jak samo pole.|  
|[Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)|Typ zwracany i typy parametrów metody muszą być co najmniej tak samo dostępna jak sama metoda.|  
|[Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)|Typ właściwości musi być co najmniej tak samo dostępna jak samej właściwości.|  
|[Zdarzenia](../../../csharp/programming-guide/events/index.md)|Typ zdarzenia musi być co najmniej tak samo dostępna jak samego zdarzenia.|  
|[Indeksatory](../../../csharp/programming-guide/indexers/index.md)|Typ i parametrów typów indeksatora musi być co najmniej tak samo dostępna jak indeksatora, sam.|  
|[Operatory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|Typ zwracany i typy parametrów operatora musi być co najmniej tak samo dostępna jak operator sam.|  
|[Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)|Typy parametrów konstruktora musi być co najmniej tak samo dostępna jak sam Konstruktor.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera błędne deklaracje różnych typów. Komentarz po każdym deklaracji wskazuje błąd kompilatora oczekiwane.  
  
```csharp  
// Restrictions on Using Accessibility Levels  
// CS0052 expected as well as CS0053, CS0056, and CS0057  
// To make the program work, change access level of both class B  
// and MyPrivateMethod() to public.  
  
using System;  
  
// A delegate:  
delegate int MyDelegate();  
  
class B  
{  
    // A private method:  
    static int MyPrivateMethod()  
    {  
        return 0;  
    }  
}  
  
public class A  
{  
    // Error: The type B is less accessible than the field A.myField.  
    public B myField = new B();  
  
    // Error: The type B is less accessible  
    // than the constant A.myConst.  
    public readonly B myConst = new B();  
  
    public B MyMethod()  
    {  
        // Error: The type B is less accessible   
        // than the method A.MyMethod.  
        return new B();  
    }  
  
    // Error: The type B is less accessible than the property A.MyProp  
    public B MyProp  
    {  
        set  
        {  
        }  
    }  
  
    MyDelegate d = new MyDelegate(B.MyPrivateMethod);  
    // Even when B is declared public, you still get the error:   
    // "The parameter B.MyPrivateMethod is not accessible due to   
    // protection level."  
  
    public static B operator +(A m1, B m2)  
    {  
        // Error: The type B is less accessible  
        // than the operator A.operator +(A,B)  
        return new B();  
    }  
  
    static void Main()  
    {  
        Console.Write("Compiled successfully");  
    }  
}  
```  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Domena dostępności](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [Poziomy ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
