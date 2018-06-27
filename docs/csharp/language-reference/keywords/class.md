---
title: Class — słowo kluczowe (odwołanie w C#)
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 04e64e825e4297ceb432393c7bd145a6cf4fcb2c
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948514"
---
# <a name="class-c-reference"></a>class (odwołanie w C#)

Klasy są zadeklarowane za pomocą słowa kluczowego `class`, jak pokazano w poniższym przykładzie:

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a>Uwagi

Tylko pojedyncze dziedziczenie jest dozwolone w języku C#. Innymi słowy klasy mogą dziedziczyć implementacji tylko jedną klasę podstawową. Jednak klasy można zaimplementować więcej niż jeden interfejs. W poniższej tabeli przedstawiono przykłady dziedziczenia klas i implementacji interfejsu:

|Dziedziczenie|Przykład|
|-----------------|-------------|
|Brak|`class ClassA { }`|
|Single|`class DerivedClass: BaseClass { }`|
|Brak, implementuje dwa interfejsy|`class ImplClass: IFace1, IFace2 { }`|
|Jeden implementuje jeden interfejs.|`class ImplDerivedClass: BaseClass, IFace1 { }`|

Klasy, które deklaruje bezpośrednio z poziomu obszaru nazw, nie są zagnieżdżone w innych klas mogą być [publicznego](../../../csharp/language-reference/keywords/public.md) lub [wewnętrzny](../../../csharp/language-reference/keywords/internal.md). Występują następujące klasy `internal` domyślnie.

Elementów członkowskich klasy, w tym zagnieżdżonych klas, może być [publicznego](../../../csharp/language-reference/keywords/public.md), `protected internal`, [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), [prywatnej](../../../csharp/language-reference/keywords/private.md), lub `private protected`. Elementy członkowskie są [prywatnej](../../../csharp/language-reference/keywords/private.md) domyślnie.

Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md). 

Można zadeklarować klas ogólnych, które mają parametry typu. Aby uzyskać więcej informacji, zobacz [klas rodzajowych](../../../csharp/programming-guide/generics/generic-classes.md).

Klasa może zawierać deklaracje następujące elementy:

- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)

- [Stałe](../../../csharp/programming-guide/classes-and-structs/constants.md)

- [Pola](../../../csharp/programming-guide/classes-and-structs/fields.md)

- [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)

- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)

- [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)

- [Indeksatory](../../../csharp/programming-guide/indexers/index.md)

- [Operatory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)

- [Zdarzenia](../../../csharp/programming-guide/events/index.md)

- [Delegaci](../../../csharp/programming-guide/delegates/index.md)

- [Klasy](../../../csharp/programming-guide/classes-and-structs/classes.md)

- [Interfejsy](../../../csharp/programming-guide/interfaces/index.md)

- [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano deklarujący pola klasy konstruktory i metody. Przedstawiono również podczas tworzenia wystąpienia obiektu i drukowanie danych wystąpienia. W tym przykładzie są deklarowane jako dwóch klas. To pierwsza klasa `Child`, zawiera dwa pola prywatne (`name` i `age`), dwa konstruktory publiczne i jeden publiczny metody. Klasa sekundę `StringTest`, zawiera `Main`.

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a>Komentarze

Zwróć uwagę, że w poprzednim przykładzie pól prywatnych (`name` i `age`) jest możliwy tylko za pośrednictwem publicznej metody `Child` klasy. Na przykład nazwa tego elementu podrzędnego, nie można drukować z `Main` metodę, przy użyciu instrukcji następująco:

```csharp
Console.Write(child1.name);   // Error
```

Uzyskiwanie dostępu do członków prywatnych `Child` z `Main` byłoby możliwe w tylko jeśli `Main` zostały elementu członkowskiego klasy.

Typy zadeklarowane wewnątrz klasy bez domyślnego modyfikator dostępu do `private`, więc elementy członkowskie danych, w tym przykładzie nadal będzie `private` usunięcie słowa kluczowego.

Na koniec należy zauważyć, że dla obiektu, który został utworzony za pomocą konstruktora domyślnego (`child3`), wieku pole zostało zainicjowane do zera domyślnie.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
[Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
[Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
[Typy odwołań](../../../csharp/language-reference/keywords/reference-types.md)