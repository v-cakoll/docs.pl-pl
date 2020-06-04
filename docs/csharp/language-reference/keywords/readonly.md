---
title: ReadOnly — słowo kluczowe — odwołanie w C#
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 66a096e8831f72a2216e8ba5dd9866046504624f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368624"
---
# <a name="readonly-c-reference"></a>readonly (odwołanie w C#)

`readonly`Słowo kluczowe jest modyfikatorem, który może być używany w czterech kontekstach:

- W [deklaracji pola](#readonly-field-example)wskazuje, `readonly` że przypisanie do pola może wystąpić tylko jako część deklaracji lub w konstruktorze w tej samej klasie. Pole tylko do odczytu można przypisać i ponownie przypisać wiele razy w deklaracji pola i konstruktorze.
  
  `readonly`Nie można przypisać pola po zakończeniu konstruktora. Ta reguła ma inne konsekwencje dla typów wartości i typów referencyjnych:
  
  - Ponieważ typy wartości bezpośrednio zawierają swoje dane, pole, które jest `readonly` typem wartości, jest niezmienne.
  - Ponieważ typy odwołań zawierają odwołanie do swoich danych, pole, które jest `readonly` typem referencyjnym, musi zawsze odwoływać się do tego samego obiektu. Ten obiekt nie jest niezmienny. `readonly`Modyfikator zapobiega zastąpieniu pola przez inne wystąpienie typu odwołania. Jednak modyfikator nie zapobiega modyfikowaniu danych wystąpienia pola za pośrednictwem pola tylko do odczytu.

  > [!WARNING]
  > Typ widoczny na zewnątrz, który zawiera zewnętrzny widoczny pole tylko do odczytu, które jest modyfikowalnym typem odwołania może być luką w zabezpieczeniach i może wyzwolić ostrzeżenie [CA2104](/visualstudio/code-quality/ca2104) : "nie deklaruj tylko odczytu modyfikowalnych typów odwołań".

- W `readonly struct` definicji typu wskazuje, `readonly` że typ struktury jest niezmienny. Aby uzyskać więcej informacji, zobacz sekcję [ `readonly` struktury](../builtin-types/struct.md#readonly-struct) w artykule [typy struktury](../builtin-types/struct.md) .
- W deklaracji elementu członkowskiego wystąpienia w typie struktury `readonly` wskazuje, że element członkowski wystąpienia nie modyfikuje stanu struktury. Aby uzyskać więcej informacji, zobacz sekcję [ `readonly` elementy członkowskie wystąpienia](../builtin-types/struct.md#readonly-instance-members) w artykule [typy struktury](../builtin-types/struct.md) .
- W [ `ref readonly` zwracanej metodzie](#ref-readonly-return-example) `readonly` modyfikator wskazuje, że metoda zwraca odwołanie, a zapisy nie są dozwolone dla tego odwołania.

`readonly struct` `ref readonly` Konteksty i zostały dodane w języku C# 7,2. `readonly`elementy członkowskie struktury zostały dodane w języku C# 8,0

## <a name="readonly-field-example"></a>Przykład pola tylko do odczytu

W tym przykładzie wartość pola `year` nie może zostać zmieniona w metodzie `ChangeYear` , mimo że jest przypisana wartość w konstruktorze klasy:

[!code-csharp[Readonly Field example](snippets/ReadonlyKeywordExamples.cs#ReadonlyField)]

Można przypisać wartość do `readonly` pola tylko w następujących kontekstach:

- Gdy zmienna jest inicjowana w deklaracji, na przykład:

  ```csharp
  public readonly int y = 5;
  ```

- W konstruktorze wystąpienia klasy, która zawiera deklarację pola wystąpienia.
- W konstruktorze statycznym klasy, która zawiera deklarację pola statycznego.

Te konteksty konstruktorów są również jedynymi kontekstami, w których są prawidłowe w celu przekazania `readonly` pola jako parametru [out](out-parameter-modifier.md) lub [ref](ref.md) .

> [!NOTE]
> `readonly`Słowo kluczowe różni się od słowa kluczowego [const](const.md) . `const`Pole może być inicjowane tylko w deklaracji pola. `readonly`Pole można przypisać wiele razy w deklaracji pola i w konstruktorze. W związku z tym `readonly` pola mogą mieć różne wartości w zależności od użytego konstruktora. Ponadto, gdy `const` pole jest stałą czasu kompilacji, `readonly` pole może być używane dla stałych czasu wykonywania, jak w poniższym przykładzie:
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](snippets/ReadonlyKeywordExamples.cs#InitReadonlyField)]

W poprzednim przykładzie, jeśli używasz instrukcji podobnej do poniższego przykładu:

```csharp
p2.y = 66;        // Error
```

zostanie wyświetlony komunikat o błędzie kompilatora:

**Nie można przypisać do pola tylko do odczytu (z wyjątkiem w konstruktorze lub inicjatorze zmiennych).**

## <a name="ref-readonly-return-example"></a>Przykład powrotu ref ReadOnly

`readonly`Modyfikator na `ref return` wskazuje, że zwracane odwołanie nie może być modyfikowane. Poniższy przykład zwraca odwołanie do źródła. Używa `readonly` modyfikatora, aby wskazać, że obiekty wywołujące nie mogą modyfikować pochodzenia:

[!code-csharp[readonly return example](snippets/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

Zwracany typ nie musi być `readonly struct` . Każdy typ, który może być zwracany przez, `ref` może być zwracany przez `ref readonly` .

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

Możesz również zobaczyć propozycje specyfikacji języka:

- [Typ ref i tylko do odczytu](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [elementy członkowskie struktury tylko do odczytu](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>Zobacz też

- [Odwołanie w C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory](index.md)
- [const](const.md)
- [Pola](../../programming-guide/classes-and-structs/fields.md)
