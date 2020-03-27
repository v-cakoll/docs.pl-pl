---
title: readonly keyword - C# Reference
ms.date: 03/26/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 344d5e54fcd500e283c52fa7953c6366823f13f0
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345149"
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
- W [ `readonly` definicji](#readonly-member-examples) `readonly` elementu członkowskiego wskazuje, `struct` że element członkowski a nie mutuje stan wewnętrzny struktury.
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

## <a name="readonly-member-examples"></a>Readonly przykłady członków

Innym razem można utworzyć strukturę, która obsługuje mutację. W takich przypadkach kilka członków wystąpienia prawdopodobnie nie będzie modyfikować stan wewnętrzny struktury. Można zadeklarować te elementy `readonly` członkowskie wystąpienia za pomocą modyfikatora. Kompilator wymusza intencji. Jeśli ten element członkowski modyfikuje stan bezpośrednio lub uzyskuje `readonly` dostęp do elementu członkowskiego, który nie jest również zadeklarowany za pomocą modyfikatora, wynikiem jest błąd w czasie kompilacji. Modyfikator `readonly` jest `struct` prawidłowy `class` w `interface` deklaracjach elementów członkowskich, nie lub członkowskich.

Zyskujesz dwie zalety, `readonly` stosując modyfikator do odpowiednich `struct` metod. Co najważniejsze kompilator wymusza intencji. Kod, który modyfikuje stan `readonly` nie jest prawidłowy w metodzie. Kompilator może również korzystać z modyfikatora, `readonly` aby włączyć optymalizacje wydajności. Gdy `struct` duże typy `in` są przekazywane przez odwołanie, kompilator musi wygenerować kopię obronną, jeśli stan struktury może być modyfikowany. Jeśli `readonly` tylko elementy członkowskie są dostępne, kompilator nie może utworzyć kopii obronnej.

Modyfikator `readonly` jest prawidłowy dla `struct`większości elementów członkowskich , <xref:System.Object?displayProperty=nameWithType>w tym metod, które zastępują metody zadeklarowane w . Istnieją pewne ograniczenia:

- Nie można zadeklarować `readonly` metod statycznych lub właściwości.
- Nie można zadeklarować `readonly` konstruktorów.

`readonly` Modyfikator można dodać do właściwości lub deklaracji indeksatora:

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

Modyfikator można również dodać `get` `set` do poszczególnych lub akcesorów właściwości lub indeksatora: `readonly`

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

Nie można dodać `readonly` modyfikatora do właściwości i co najmniej jednego z akcesorów tej samej właściwości. To samo ograniczenie dotyczy indeksatorów.

Kompilator niejawnie `readonly` stosuje modyfikator do właściwości automatycznie implementowane, gdzie kompilator zaimplementowany kod nie modyfikuje stanu. Jest to równoważne z następującymi deklaracjami:

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
```

`readonly` Modyfikator można dodać w tych lokalizacjach, ale nie będzie miał znaczącego wpływu. `readonly` Modyfikator nie może być dodawany do zestawu właściwości zaimplementowanych automatycznie ani do właściwości automatycznie implementowanych odczytu/zapisu.

## <a name="ref-readonly-return-example"></a>Ref readonly return example (Przykład zwrotu tylko w celu odesłania)

Modyfikator `readonly` na `ref return` wskazuje, że zwracanego odwołania nie można zmodyfikować. Poniższy przykład zwraca odwołanie do pochodzenia. Używa modyfikatora, `readonly` aby wskazać, że wywołujący nie można zmodyfikować pochodzenia:

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

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
