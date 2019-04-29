---
title: Class — słowo kluczowe - C# odwołania
ms.custom: seodec18
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: fbb685abcc5c2e79a64501385edf8f6c2041861d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662000"
---
# <a name="class-c-reference"></a>class (odwołanie w C#)

Klasy są deklarowane przy użyciu słowa kluczowego `class`, jak pokazano w poniższym przykładzie:

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a>Uwagi

Tylko pojedyncze dziedziczenie jest dozwolone w języku C#. Innymi słowy klasy mogą dziedziczyć implementację tylko jedną klasę bazową. Jednak klasa może implementować więcej niż jednego interfejsu. W poniższej tabeli przedstawiono przykłady dziedziczenia klas oraz implementacji interfejsu:

|Dziedziczenie|Przykład|
|-----------------|-------------|
|Brak|`class ClassA { }`|
|Single|`class DerivedClass: BaseClass { }`|
|Brak, implementuje dwa interfejsy|`class ImplClass: IFace1, IFace2 { }`|
|Pojedyncze, implementuje jednego interfejsu.|`class ImplDerivedClass: BaseClass, IFace1 { }`|

Klasy, Zadeklaruj bezpośrednio z poziomu obszaru nazw, nie są zagnieżdżone w innych klas, które mogą być albo [publicznych](../../../csharp/language-reference/keywords/public.md) lub [wewnętrzny](../../../csharp/language-reference/keywords/internal.md). Klasy są `internal` domyślnie.

Składowych klasy, łącznie z klas zagnieżdżonych, może być [publicznych](public.md), [chronionych wewnętrznych](protected-internal.md), [chronione](protected.md), [wewnętrzny](internal.md), [ prywatne](private.md), lub [prywatny chroniony](private-protected.md). Elementy członkowskie są `private` domyślnie.

Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md). 

Można zadeklarować klasy ogólne, które mają parametry typu. Aby uzyskać więcej informacji, zobacz [klas ogólnych](../../../csharp/programming-guide/generics/generic-classes.md).

Klasa może zawierać deklaracje następujące elementy członkowskie:

- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)

- [Stałe](../../../csharp/programming-guide/classes-and-structs/constants.md)

- [Pola](../../../csharp/programming-guide/classes-and-structs/fields.md)

- [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)

- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)

- [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)

- [Indeksatory](../../../csharp/programming-guide/indexers/index.md)

- [Operatory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)

- [Zdarzenia](../../../csharp/programming-guide/events/index.md)

- [Delegaty](../../../csharp/programming-guide/delegates/index.md)

- [Klasy](../../../csharp/programming-guide/classes-and-structs/classes.md)

- [Interfejsy](../../../csharp/programming-guide/interfaces/index.md)

- [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)

- [Wyliczenia](../../../csharp/programming-guide/enumeration-types.md)

## <a name="example"></a>Przykład

Poniższy przykład pokazuje deklarującego pola klasy, konstruktory i metody. Ilustruje też tworzenia wystąpienia obiektu i drukowanie danych wystąpienia. W tym przykładzie dwie klasy są deklarowane. Pierwsza klasa `Child`, zawiera dwa pola prywatne (`name` i `age`), dwa konstruktory publiczne i jedną metodę publiczną. Druga klasa, `StringTest`, będącą `Main`.

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a>Komentarze

Należy zauważyć, że w poprzednim przykładzie pola prywatne (`name` i `age`) jest możliwy tylko za pośrednictwem publicznej metody `Child` klasy. Na przykład nie można drukować nazwy elementu podrzędnego z `Main` metody, przy użyciu instrukcji w następujący sposób:

```csharp
Console.Write(child1.name);   // Error
```

Uzyskiwanie dostępu do prywatnych składowych `Child` z `Main` byłoby możliwe w tylko jeśli `Main` zostały składową klasy.

Typy zadeklarowane wewnątrz klasy bez domyślnie modyfikator dostępu `private`, więc nadal będzie składowe danych, w tym przykładzie `private` usunięcie słowa kluczowego.

Na koniec Zwróć uwagę, że dla obiektu, który został utworzony za pomocą konstruktora bez parametrów (`child3`), `age` pole zostało inicjowane od zera domyślnie.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
- [Typy odwołań](../../../csharp/language-reference/keywords/reference-types.md)
