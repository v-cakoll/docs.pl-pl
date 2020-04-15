---
title: readonly keyword - C# Reference
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 03b0aa63eda3e7a9d8745baaa33479fd5e85b01b
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389054"
---
# <a name="readonly-c-reference"></a>readonly (odwołanie w C#)

Słowo `readonly` kluczowe jest modyfikatorem, który może być używany w czterech kontekstach:

- W [deklaracji](#readonly-field-example)pola `readonly` wskazuje, że przypisanie do pola może nastąpić tylko jako część deklaracji lub w konstruktorze w tej samej klasie. Pole tylko do odczytu można przypisać i przypisać ponownie wiele razy w deklaracji pola i konstruktora.
  
  Nie `readonly` można przypisać pola po zamknięciu konstruktora. Ta reguła ma różne implikacje dla typów wartości i typów odwołań:
  
  - Ponieważ typy wartości bezpośrednio zawierają ich dane, pole, które jest typem `readonly` wartości, jest niezmienne.
  - Ponieważ typy odwołań zawierają odwołanie do ich `readonly` danych, pole, które jest typem odwołania, musi zawsze odwoływać się do tego samego obiektu. Ten obiekt nie jest niezmienny. Modyfikator `readonly` zapobiega zastępowaniu pola przez inne wystąpienie typu odwołania. Jednak modyfikator nie zapobiega modyfikowaniu danych wystąpienia pola za pomocą pola tylko do odczytu.

  > [!WARNING]
  > Zewnętrznie widoczny typ, który zawiera zewnętrznie widoczne pole tylko do odczytu, które jest modyfikowalnym typem odwołania, może być luką w zabezpieczeniach i może wywołać ostrzeżenie [CA2104](/visualstudio/code-quality/ca2104) : "Nie zgłaszaj tylko do odczytu typów odwołań modyfikowalnych."

- W `readonly struct` definicji `readonly` typu wskazuje, że typ struktury jest niezmienny. Aby uzyskać więcej [ `readonly` ](../builtin-types/struct.md#readonly-struct) informacji, zobacz sekcję struktury [struktury struktury typów](../builtin-types/struct.md) artykułu.
- W deklaracji elementu członkowskiego wystąpienia `readonly` w typie struktury wskazuje, że element członkowski wystąpienia nie modyfikuje stanu struktury. Aby uzyskać więcej [ `readonly` ](../builtin-types/struct.md#readonly-instance-members) informacji, zobacz sekcję członków wystąpienia w artykule [Typy struktury.](../builtin-types/struct.md)
- W [ `ref readonly` powrocie](#ref-readonly-return-example)metody `readonly` modyfikator wskazuje, że metoda zwraca odwołanie i zapisy nie są dozwolone do tego odwołania.

`readonly struct` Konteksty `ref readonly` i zostały dodane w języku C# 7.2. `readonly`elementy strukturyzowania zostały dodane w języku C# 8.0

## <a name="readonly-field-example"></a>Przykład pola tylko do odczytu

W tym przykładzie nie `year` można zmienić wartości pola `ChangeYear`w metodzie, nawet jeśli jest przypisana wartość w konstruktorze klasy:

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

Wartość do `readonly` pola można przypisać tylko w następujących kontekstach:

- Gdy zmienna jest inicjowana w deklaracji, na przykład:

  ```csharp
  public readonly int y = 5;
  ```

- W konstruktorze instancji klasy, która zawiera deklarację pola wystąpienia.
- W statycznym konstruktorze klasy, która zawiera deklarację pola statycznego.

Te konteksty konstruktora są również tylko konteksty, `readonly` w których jest prawidłowy, aby przekazać pole jako [out](out-parameter-modifier.md) lub [ref](ref.md) parametru.

> [!NOTE]
> Słowo `readonly` kluczowe różni się od słowa kluczowego [const.](const.md) Pole `const` można zainicjować tylko w deklaracji pola. Pole `readonly` można przypisać wiele razy w deklaracji pola i w dowolnym konstruktorze. W związku `readonly` z tym pola mogą mieć różne wartości w zależności od używanego konstruktora. Ponadto, podczas `const` gdy pole jest stałą `readonly` w czasie kompilacji, pole może być używane dla stałych w czasie wykonywania, jak w poniższym przykładzie:
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

W poprzednim przykładzie, jeśli używasz instrukcji, jak w poniższym przykładzie:

```csharp
p2.y = 66;        // Error
```

zostanie wyświetlony komunikat o błędzie kompilatora:

**Nie można przypisać pola tylko do odczytu (z wyjątkiem konstruktora lub inicjatora zmiennej)**

## <a name="ref-readonly-return-example"></a>Ref readonly return example (Przykład zwrotu tylko w celu odesłania)

Modyfikator `readonly` na `ref return` wskazuje, że zwracanego odwołania nie można zmodyfikować. Poniższy przykład zwraca odwołanie do pochodzenia. Używa modyfikatora, `readonly` aby wskazać, że wywołujący nie można zmodyfikować pochodzenia:

[!code-csharp[readonly return example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

Zwracany typ nie musi być `readonly struct`. Każdy typ, który `ref` może zostać `ref readonly`zwrócony przez może być zwrócony przez .

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

Można również zobaczyć propozycje specyfikacji języka:

- [readonly ref i readonly struct](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [readonly strumyk elementów członkowskich](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [C# Przewodnik programowania](../../programming-guide/index.md)
- [C# Słowa kluczowe](index.md)
- [Modyfikatory](index.md)
- [const](const.md)
- [Pola](../../programming-guide/classes-and-structs/fields.md)
