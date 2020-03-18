---
title: Ograniczenia dotyczące korzystania z poziomów ułatwień dostępu — odwołanie do języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 48ab765db7c839ed0dd14df5e6b30f5bd6c0d29b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173539"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a>Ograniczenia dotyczące korzystania z poziomów ułatwień dostępu (odwołanie do języka C#)

Po określeniu typu w deklaracji, sprawdź, czy poziom ułatwień dostępu typu zależy od poziomu ułatwień dostępu elementu członkowskiego lub innego typu. Na przykład klasa podstawowa bezpośrednia musi być co najmniej tak samo dostępna jak klasa pochodna. Następujące deklaracje powodują błąd kompilatora, ponieważ klasa `BaseClass` podstawowa jest mniej dostępna niż: `MyClass`

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

W poniższej tabeli podsumowano ograniczenia dotyczące zadeklarowanych poziomów ułatwień dostępu.

|Kontekst|Uwagi|
|-------------|-------------|
|[Klasy](../../programming-guide/classes-and-structs/classes.md)|Bezpośrednia klasa podstawowa typu klasy musi być co najmniej tak samo dostępna jak sam typ klasy.|
|[Interfejsy](../../programming-guide/interfaces/index.md)|Jawne interfejsy podstawowe typu interfejsu muszą być co najmniej tak samo dostępne, jak sam typ interfejsu.|
|[Delegaty](../../programming-guide/delegates/index.md)|Typ zwracany i typy parametrów typu delegata muszą być co najmniej tak samo dostępne, jak sam typ delegata.|
|[Stałe](../../programming-guide/classes-and-structs/constants.md)|Typ stałej musi być co najmniej tak samo dostępny jak sama stała.|
|[Pola](../../programming-guide/classes-and-structs/fields.md)|Typ pola musi być co najmniej tak samo dostępny jak samo pole.|
|[Metody](../../programming-guide/classes-and-structs/methods.md)|Typ zwracany i typy parametrów metody muszą być co najmniej tak samo dostępne jak sama metoda.|
|[Właściwości](../../programming-guide/classes-and-structs/properties.md)|Typ właściwości musi być co najmniej tak samo dostępny jak sama właściwość.|
|[Zdarzenia](../../programming-guide/events/index.md)|Typ zdarzenia musi być co najmniej tak samo dostępne, jak samo zdarzenie.|
|[Indexers](../../programming-guide/indexers/index.md) (Indeksatory)|The type and parameter types of an indexer must be at least as accessible as the indexer itself.|
|[Operatory](../operators/index.md)|Typ zwracany i typy parametrów operatora muszą być co najmniej tak samo dostępne jak sam operator.|
|[Konstruktory](../../programming-guide/classes-and-structs/constructors.md)|Typy parametrów konstruktora musi być co najmniej tak samo dostępne jak sam konstruktor.|

## <a name="example"></a>Przykład

Poniższy przykład zawiera błędne deklaracje różnych typów. Komentarz po każdej deklaracji wskazuje oczekiwany błąd kompilatora.

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

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../../language-reference/index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](../../language-reference/keywords/index.md)
- [Modyfikatory dostępu](../../language-reference/keywords/access-modifiers.md)
- [Domena dostępności](../../language-reference/keywords/accessibility-domain.md)
- [Poziomy ułatwień dostępu](../../language-reference/keywords/accessibility-levels.md)
- [Modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Publicznego](../../language-reference/keywords/public.md)
- [Prywatny](../../language-reference/keywords/private.md)
- [protected](../../language-reference/keywords/protected.md)
- [Wewnętrznego](../../language-reference/keywords/internal.md)
