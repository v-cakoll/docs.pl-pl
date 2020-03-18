---
title: słowo kluczowe tylko do odczytu — odwołanie do języka C#
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 165b6287e1610e013b289601e1535a08fdd3b5c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399358"
---
# <a name="readonly-c-reference"></a>readonly (odwołanie w C#)

Słowo `readonly` kluczowe jest modyfikatorem, który może być używany w czterech kontekstach:

- W [deklaracji](#readonly-field-example)pola `readonly` wskazuje, że przypisanie do pola może wystąpić tylko jako część deklaracji lub w konstruktorze w tej samej klasie. Pole tylko do odczytu można przypisać i przypisać je wielokrotnie w ramach deklaracji pola i konstruktora.
  
  Nie `readonly` można przypisać pola po wyjściu konstruktora. Ta reguła ma różne implikacje dla typów wartości i typów odwołań:
  
  - Ponieważ typy wartości bezpośrednio zawierają ich dane, pole, które jest typem `readonly` wartości jest niezmienne.
  - Ponieważ typy odwołań zawierają odwołanie do ich `readonly` danych, pole, które jest typem odwołania, musi zawsze odwoływać się do tego samego obiektu. Ten obiekt nie jest niezmienny. Modyfikator `readonly` zapobiega zastępowaniu pola innym wystąpieniem typu odwołania. Jednak modyfikator nie uniemożliwia modyfikowania danych wystąpienia pola za pomocą pola tylko do odczytu.

  > [!WARNING]
  > Typ widoczny zewnętrznie, który zawiera widoczne z zewnątrz pole tylko do odczytu, które jest typu odwołanie mofntabela może być luka w zabezpieczeniach i może wyzwolić ostrzeżenie [CA2104:](/visualstudio/code-quality/ca2104) "Nie deklarują tylko do odczytu typy odwołań tylko do odczytu."

- W [ `readonly struct` definicji](#readonly-struct-example) `readonly` wskazuje, `struct` że jest niezmienny.
- W [ `readonly` definicji elementu członkowskiego](#readonly-member-examples)wskazuje, `struct` `readonly` że element członkowski nie mutuje stanu wewnętrznego struktury.
- W [ `ref readonly` zwracanej metodzie](#ref-readonly-return-example) `readonly` modyfikator wskazuje, że metoda zwraca odwołanie i zapisuje nie są dozwolone do tego odwołania.

I `readonly struct` `ref readonly` konteksty zostały dodane w języku C# 7.2. `readonly`elementy składek zostały dodane w języku C# 8.0

## <a name="readonly-field-example"></a>Przykład pola tylko do odczytu

W tym przykładzie wartość pola `year` nie można zmienić w `ChangeYear`metodzie, mimo że jest przypisana wartość w konstruktorze klasy:

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

Wartość można przypisać do `readonly` pola tylko w następujących kontekstach:

- Gdy zmienna jest inicjowana w deklaracji, na przykład:

  ```csharp
  public readonly int y = 5;
  ```

- W konstruktora wystąpienia klasy, która zawiera deklarację pola wystąpienia.
- W konstruktorze statycznym klasy, która zawiera deklarację pola statycznego.

Te konstruktory konteksty są również tylko konteksty, `readonly` w których jest prawidłowy przekazać pole jako [out](out-parameter-modifier.md) lub [ref](ref.md) parametru.

> [!NOTE]
> Słowo `readonly` kluczowe różni się od słowa kluczowego [const.](const.md) Pole `const` można zainicjować tylko w deklaracji pola. Pole `readonly` można przypisać wiele razy w deklaracji pola i w dowolnym konstruktorze. W `readonly` związku z tym pola mogą mieć różne wartości w zależności od konstruktora używane. Ponadto, gdy `const` pole jest stałą w `readonly` czasie kompilacji, pole może służyć do stałych w czasie wykonywania, jak w poniższym przykładzie:
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

W poprzednim przykładzie, jeśli używasz instrukcji, takich jak w poniższym przykładzie:

```csharp
p2.y = 66;        // Error
```

pojawi się komunikat o błędzie kompilatora:

**Nie można przypisać pola tylko do odczytu (z wyjątkiem konstruktora lub inicjatora zmiennego)**

## <a name="readonly-struct-example"></a>Przykład struktury tylko do odczytu

Modyfikator `readonly` `struct` definicji deklaruje, że struktura jest **niezmienna**. Każde pole wystąpienia `struct` musi `readonly`być oznaczone, jak pokazano w poniższym przykładzie:

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

W poprzednim przykładzie używa [właściwości auto tylko do odczytu,](../../properties.md#read-only) aby zadeklarować jego magazyn. Który instruuje kompilator, aby utworzyć `readonly` pola zapasowe dla tych właściwości. Można również `readonly` zadeklarować pola bezpośrednio:

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

Dodanie pola nie `readonly` oznaczonego generuje `CS8340`błąd kompilatora: "Pola wystąpienia struktur tylko do odczytu muszą być tylko do odczytu".

## <a name="readonly-member-examples"></a>Przykłady członków tylko do odczytu

Innym razem, można utworzyć strukturę, która obsługuje mutacji. W takich przypadkach kilka elementów członkowskich wystąpienia prawdopodobnie nie zmodyfikuje stan wewnętrzny struktury. Można zadeklarować tych elementów `readonly` członkowskich wystąpienia z modyfikatorem. Kompilator wymusza intencji. Jeśli ten element członkowski modyfikuje stan bezpośrednio lub uzyskuje dostęp do elementu członkowskiego, który nie jest również zadeklarowany za pomocą `readonly` modyfikatora, wynik jest błąd w czasie kompilacji. Modyfikator `readonly` jest `struct` prawidłowy `class` `interface` na członków, nie lub deklaracji elementów członkowskich.

Zyskujesz dwie zalety, `readonly` stosując `struct` modyfikator do odpowiednich metod. Co najważniejsze kompilator wymusza intencji. Kod, który modyfikuje stan nie `readonly` jest prawidłowy w metodzie. Kompilator może również `readonly` korzystać z modyfikatora, aby włączyć optymalizacje wydajności. Gdy `struct` duże typy `in` są przekazywane przez odwołanie, kompilator musi wygenerować kopię obronną, jeśli stan struktury może zostać zmodyfikowany. Jeśli `readonly` dostęp są tylko elementy członkowskie, kompilator nie może utworzyć kopię obronną.

Modyfikator `readonly` jest prawidłowy `struct`dla większości elementów członkowskich , w <xref:System.Object?displayProperty=nameWithType>tym metody, które zastępują metody zadeklarowane w . Istnieją pewne ograniczenia:

- Nie można zadeklarować `readonly` metod ani właściwości statycznych.
- Nie można zadeklarować `readonly` konstruktorów.

`readonly` Modyfikator można dodać do deklaracji właściwości lub indeksatora:

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

Można również dodać `readonly` modyfikator do poszczególnych `get` lub `set` akcesorów właściwości lub indeksatora:

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

Nie można dodać `readonly` modyfikatora do właściwości i jeden lub więcej akcesorów tej samej właściwości. To samo ograniczenie dotyczy indeksatorów.

Kompilator niejawnie `readonly` stosuje modyfikator do właściwości implementowane automatycznie, gdzie kompilator zaimplementowany kod nie modyfikuje stan. Jest to równoważne z następującymi deklaracjami:

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
```

Możesz dodać `readonly` modyfikator w tych lokalizacjach, ale nie będzie miał znaczącego wpływu. `readonly` Modyfikator nie może być dodawany do automatycznie implementowane go właściwości ustawiające właściwości lub do odczytu/zapisu właściwości autoimplementowane.

## <a name="ref-readonly-return-example"></a>Przykład zwrotu tylko do odczytu ref

Modyfikator `readonly` `ref return` na wskazuje, że zwrócone odwołanie nie można modyfikować. Poniższy przykład zwraca odwołanie do początku. Używa modyfikatora, `readonly` aby wskazać, że obiekty wywołujące nie można modyfikować pochodzenia:

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
Zwracany typ nie musi być `readonly struct`. Każdy typ, który może `ref` zostać zwrócony `ref readonly`przez mogą być zwracane przez .

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

Możesz również zobaczyć propozycje specyfikacji języka:

- [readonly ref i readonly struct](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [tylko do odczytu elementy składowe](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory](index.md)
- [const](const.md)
- [Pola](../../programming-guide/classes-and-structs/fields.md)
