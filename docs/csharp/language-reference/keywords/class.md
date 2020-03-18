---
title: class — słowo kluczowe — odwołanie do języka C#
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 500160d3bc9280b866e5f5ba24c5edc623e752c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673098"
---
# <a name="class-c-reference"></a>class (odwołanie w C#)

Klasy są deklarowane `class`przy użyciu słowa kluczowego , jak pokazano w poniższym przykładzie:

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a>Uwagi

Tylko pojedyncze dziedziczenie jest dozwolone w języku C#. Innymi słowy klasy można dziedziczyć implementacji tylko z jednej klasy podstawowej. Jednak klasa może zaimplementować więcej niż jeden interfejs. W poniższej tabeli przedstawiono przykłady dziedziczenia klas i implementacji interfejsu:

|Dziedziczenie|Przykład|
|-----------------|-------------|
|Brak|`class ClassA { }`|
|Single|`class DerivedClass : BaseClass { }`|
|Brak, implementuje dwa interfejsy|`class ImplClass : IFace1, IFace2 { }`|
|Pojedynczy, implementuje jeden interfejs|`class ImplDerivedClass : BaseClass, IFace1 { }`|

Klasy, które deklarujesz bezpośrednio w obszarze nazw, nie zagnieżdżonych w innych klasach, mogą być [publiczne](./public.md) lub [wewnętrzne.](./internal.md) Klasy `internal` są domyślnie.

Członkowie klasy, w tym klasy zagnieżdżone, mogą być [publiczne,](public.md) [chronione wewnętrzne,](protected-internal.md) [chronione,](protected.md) [wewnętrzne,](internal.md) [prywatne](private.md)lub [prywatne chronione.](private-protected.md) Członkowie `private` są domyślnie.

Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md).

Można zadeklarować klas ogólnych, które mają parametry typu. Aby uzyskać więcej informacji, zobacz [Klasy ogólne](../../programming-guide/generics/generic-classes.md).

Klasa może zawierać deklaracje następujących elementów członkowskich:

- [Konstruktory](../../programming-guide/classes-and-structs/constructors.md)

- [Stałe](../../programming-guide/classes-and-structs/constants.md)

- [Pola](../../programming-guide/classes-and-structs/fields.md)

- [Finalizatory](../../programming-guide/classes-and-structs/destructors.md)

- [Metody](../../programming-guide/classes-and-structs/methods.md)

- [Właściwości](../../programming-guide/classes-and-structs/properties.md)

- [Indexers](../../programming-guide/indexers/index.md) (Indeksatory)

- [Operatory](../operators/index.md)

- [Zdarzenia](../../programming-guide/events/index.md)

- [Delegaty](../../programming-guide/delegates/index.md)

- [Klasy](../../programming-guide/classes-and-structs/classes.md)

- [Interfejsy](../../programming-guide/interfaces/index.md)

- [Typy konstrukcji](../builtin-types/struct.md)

- [Typy wyliczania](../builtin-types/enum.md)

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono deklarowanie pól klas, konstruktorów i metod. Pokazuje również wystąpienia obiektów i drukowanie danych wystąpienia. W tym przykładzie dwie klasy są zadeklarowane. Pierwsza klasa `Child`, zawiera dwa`name` pola `age`prywatne ( i ), dwa konstruktory publiczne i jedną metodę publiczną. Druga klasa, `StringTest`jest używana `Main`do zawierania .

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a>Komentarze

Należy zauważyć, że w poprzednim`name` `age`przykładzie pola prywatne ( i ) `Child` są dostępne tylko za pośrednictwem metody publicznej klasy. Na przykład nie można wydrukować imienia i `Main` nazwiska dziecka z metody, używając instrukcji w stylu:

```csharp
Console.Write(child1.name);   // Error
```

Dostęp do prywatnych `Child` `Main` członków from byłoby możliwe tylko wtedy, `Main` gdy były członkami klasy.

Typy zadeklarowane wewnątrz klasy bez modyfikatora dostępu domyślnie `private`, `private` więc elementy członkowskie danych w tym przykładzie będzie nadal, jeśli słowo kluczowe zostały usunięte.

Na koniec należy zauważyć, że dla obiektu utworzonego przy użyciu konstruktora bezparametrów (`child3`), `age` pole zostało zainicjowane domyślnie do zera.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Typy odwołań](./reference-types.md)
