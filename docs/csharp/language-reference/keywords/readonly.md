---
title: ReadOnly — słowo kluczowe (odwołanie w C#)
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: d09ce4ea972a3064298eebdf0b8b80999ee8441e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2018
ms.locfileid: "44227288"
---
# <a name="readonly-c-reference"></a>readonly (odwołanie w C#)

`readonly` — Słowo kluczowe jest modyfikator, który może być używana w kontekstach trzy:

- W [pola deklaracji](#readonly-field-example), `readonly` wskazuje przypisania do pola mogą występować wyłącznie jako część deklaracji lub za pomocą konstruktora w tej samej klasy.
- W [ `readonly struct` definicji](#readonly-struct-example), `readonly` wskazuje, że `struct` można modyfikować.
- W [ `ref readonly` zwrotu metody](#ref-readonly-return-example), `readonly` modyfikator wskazuje, że metoda zwraca odwołanie i zapisy są niedozwolone do tego odwołania.

Końcowe dwa konteksty zostały dodane w języku C# 7.2.

## <a name="readonly-field-example"></a>Przykład pola tylko do odczytu

W tym przykładzie wartość pola `year` nie można zmienić w metodzie `ChangeYear`, nawet jeśli jest do niej przypisana wartość w konstruktorze klasy:

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

Można przypisać wartości do `readonly` tylko w następujących kontekstów się:

- Gdy zmienna jest inicjowana w deklaracji, na przykład:

```csharp
public readonly int y = 5;
```

- W konstruktorze wystąpienia klasy, który zawiera deklarację pola wystąpienia.
- W konstruktorze statycznym klasy, który zawiera deklarację pola statycznego.

Tych kontekstach Konstruktor są również tylko kontekstów, w których jest on prawidłowy do przekazania `readonly` pola jako [się](out-parameter-modifier.md) lub [ref](ref.md) parametru.

> [!NOTE]
> `readonly` — Słowo kluczowe różni się od [const](const.md) — słowo kluczowe. A `const` pola mogą być inicjowane tylko na deklarację pola. A `readonly` pola mogą być inicjowane w deklaracji lub w konstruktorze. W związku z tym `readonly` pola mogą mieć różne wartości w zależności od używanego konstruktora. Ponadto, podczas gdy `const` pole jest stałą czasu kompilacji `readonly` pole może być używane dla stałych środowiska uruchomieniowego, jak w poniższym przykładzie:

```csharp
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

W poprzednim przykładzie, jeśli korzystasz z instrukcji, podobnie jak w poniższym przykładzie:

`p2.y = 66;        // Error`

zostanie wyświetlony komunikat o błędzie kompilatora:

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

## <a name="readonly-struct-example"></a>Przykład struktury tylko do odczytu

`readonly` Modyfikator na `struct` definicji oświadcza, że struktura **niezmienne**. Wszystkie pola wystąpienia `struct` muszą być oznaczone jako `readonly`, jak pokazano w poniższym przykładzie:

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

W poprzednim przykładzie użyto [tylko do odczytu właściwości automatyczne](../../properties.md#read-only) można zadeklarować magazynu. Która instruuje kompilator, aby utworzyć `readonly` kopii pola dla tych właściwości. Można również zadeklarować `readonly` pól bezpośrednio:

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

Dodawanie pola niezaznaczonych `readonly` generuje błąd kompilatora `CS8340`: "wystąpienia pól struktur tylko do odczytu muszą być tylko do odczytu."

## <a name="ref-readonly-return-example"></a>Przykład zwracane tylko do odczytu REF

`readonly` Modyfikator na `ref return` wskazuje, że zwracane odwołanie nie może być modyfikowany. Poniższy przykład zwraca odwołanie do źródła. Używa ona `readonly` modyfikator, aby wskazać, że obiekty wywołujące nie można zmodyfikować punkt początkowy:

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
Typ zwracany nie musi być `readonly struct`. Dowolny typ, który może zostać zwrócony przez `ref` mogą być zwrócone przez `ref readonly`

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory](modifiers.md)
- [const](const.md)
- [Pola](../../programming-guide/classes-and-structs/fields.md)
