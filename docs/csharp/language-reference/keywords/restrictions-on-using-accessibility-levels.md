---
title: Ograniczenia dotyczące używania poziomów ułatwień dostępu (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 2bcf2b12d1aa1488e6d3e46f5b37ac9535b138dd
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46002115"
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
|[Klasy](../../programming-guide/classes-and-structs/classes.md)|Bezpośrednie klasy bazowej typu klasy musi być co najmniej tak samo dostępna jak samego typu klasy.|
|[Interfejsy](../../programming-guide/interfaces/index.md)|Jawne interfejsy podstawowe typu interfejsu, musi być co najmniej tak samo dostępna jak samego typu interfejsu.|
|[Delegaci](../../programming-guide/delegates/index.md)|Typ zwracany i typy parametrów typu delegowanego musi być co najmniej tak samo dostępna jak samego typu delegata.|
|[Stałe](../../programming-guide/classes-and-structs/constants.md)|Typ stałej musi być co najmniej tak samo dostępna jak stała się.|
|[Pola](../../programming-guide/classes-and-structs/fields.md)|Typ pola musi być co najmniej tak samo dostępna jak samo pole.|
|[Metody](../../programming-guide/classes-and-structs/methods.md)|Typ zwracany i typy parametrów metody muszą być co najmniej tak samo dostępna jak sama metoda.|
|[Właściwości](../../programming-guide/classes-and-structs/properties.md)|Typ właściwości musi być co najmniej tak samo dostępna jak samej właściwości.|
|[Zdarzenia](../../programming-guide/events/index.md)|Typ zdarzenia musi być co najmniej tak samo dostępna jak samego zdarzenia.|
|[Indeksatory](../../programming-guide/indexers/index.md)|Typ i parametrów typów indeksatora musi być co najmniej tak samo dostępna jak indeksatora, sam.|
|[Operatory](../../programming-guide/statements-expressions-operators/operators.md)|Typ zwracany i typy parametrów operatora musi być co najmniej tak samo dostępna jak operator sam.|
|[Konstruktory](../../programming-guide/classes-and-structs/constructors.md)|Typy parametrów konstruktora musi być co najmniej tak samo dostępna jak sam Konstruktor.|

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

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../language-reference/index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](../../language-reference/keywords/index.md)
- [Modyfikatory dostępu](../../language-reference/keywords/access-modifiers.md)
- [Domena dostępności](../../language-reference/keywords/accessibility-domain.md)
- [Poziomy ułatwień dostępu](../../language-reference/keywords/accessibility-levels.md)
- [Modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [public](../../language-reference/keywords/public.md)
- [private](../../language-reference/keywords/private.md)
- [protected](../../language-reference/keywords/protected.md)
- [internal](../../language-reference/keywords/internal.md)