---
title: Ograniczenia dotyczące używania poziomów ułatwień dostępu (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: bbe358822e885e5ddaba4cb9d982e89cefe1921e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a>Ograniczenia dotyczące używania poziomów ułatwień dostępu (odwołanie w C#)
Po określeniu typu w deklaracji, sprawdź, czy poziom dostępności typu zależy od poziomu dostępności elementu członkowskiego lub innego typu. Na przykład musi być co najmniej jako dostępne jako klasa pochodna bezpośredniej klasie podstawowej. Następujące deklaracje spowodować błąd kompilatora, ponieważ klasa podstawowa `BaseClass` jest mniej dostępny niż `MyClass`:  
  
```  
class BaseClass {...}  
public class MyClass: BaseClass {...} // Error  
```  
  
 W poniższej tabeli przedstawiono ograniczenia dotyczące poziomów ułatwień dostępu zadeklarowane.  
  
|Kontekst|Uwagi|  
|-------------|-------------|  
|[Klasy](../../../csharp/programming-guide/classes-and-structs/classes.md)|Bezpośrednia klasa podstawowa typu klasy musi być co najmniej jako dostępny jako samego typu klasy.|  
|[Interfejsy](../../../csharp/programming-guide/interfaces/index.md)|Jawne interfejsy podstawowego typu interfejsu muszą być co najmniej jako dostępne jako samego typu interfejsu.|  
|[Delegaci](../../../csharp/programming-guide/delegates/index.md)|Zwracany typ i typy parametrów typu delegata musi być co najmniej jako dostępny jako sam typ delegata.|  
|[Stałe](../../../csharp/programming-guide/classes-and-structs/constants.md)|Typ stałej musi być co najmniej dostępny jako stałej sam.|  
|[Pola](../../../csharp/programming-guide/classes-and-structs/fields.md)|Typ pola muszą być co najmniej jako dostępne jako samego pola.|  
|[Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)|Zwracany typ i typy parametrów, metody muszą być co najmniej jako dostępne jako tej metody.|  
|[Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)|Typ właściwości musi być co najmniej dostępny jako samej właściwości.|  
|[Zdarzenia](../../../csharp/programming-guide/events/index.md)|Typ zdarzenia musi być co najmniej dostępny jako samym zdarzeniu.|  
|[Indeksatory](../../../csharp/programming-guide/indexers/index.md)|Typy typu i parametru indeksatora muszą być co najmniej jako dostępne jako indeksatora samej siebie.|  
|[Operatory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|Zwracany typ i typy parametrów operatora musi być co najmniej jako dostępny jako operator samej siebie.|  
|[Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)|Typy parametrów konstruktora musi być co najmniej jako dostępny, co konstruktor samej siebie.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera błędne deklaracje różnych typów. Komentarz po każdej deklaracji wskazuje błąd kompilatora oczekiwanego.  
  
```  
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
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
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
