---
title: ReadOnly — słowo C# kluczowe-odwołanie
ms.custom: seodec18
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 6c48806e54f11bce930d03a53b010c337e6658f8
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/26/2019
ms.locfileid: "72960851"
---
# <a name="readonly-c-reference"></a>readonly (odwołanie w C#)

Słowo kluczowe `readonly` jest modyfikatorem, który może być używany w czterech kontekstach:

- W [deklaracji pola](#readonly-field-example)`readonly` wskazuje, że przypisanie do pola może wystąpić tylko jako część deklaracji lub w konstruktorze w tej samej klasie. Pole tylko do odczytu można przypisać i ponownie przypisać wiele razy w deklaracji pola i konstruktorze. 
  
  Nie można przypisać pola `readonly` po zakończeniu konstruktora. Ta reguła ma inne konsekwencje dla typów wartości i typów referencyjnych:
  
  - Ponieważ typy wartości bezpośrednio zawierają swoje dane, pole, które jest `readonly` typem wartości jest niezmienne. 
  - Ponieważ typy odwołań zawierają odwołanie do swoich danych, pole, które jest typem referencyjnym `readonly` musi zawsze odwoływać się do tego samego obiektu. Ten obiekt nie jest niezmienny. Modyfikator `readonly` uniemożliwia zastąpienie pola przez inne wystąpienie typu odwołania. Jednak modyfikator nie zapobiega modyfikowaniu danych wystąpienia pola za pośrednictwem pola tylko do odczytu.

  > [!WARNING]
  > Typ widoczny na zewnątrz, który zawiera zewnętrzny widoczny pole tylko do odczytu, które jest modyfikowalnym typem odwołania może być luką w zabezpieczeniach i może wyzwolić ostrzeżenie [CA2104](/visualstudio/code-quality/ca2104-do-not-declare-read-only-mutable-reference-types) : "nie deklaruj tylko odczytu modyfikowalnych typów odwołań".

- W [definicji`readonly struct`](#readonly-struct-example)`readonly` wskazuje, że `struct` jest niezmienny.
- W [definicji elementu członkowskiego`readonly`](#readonly-member-examples)`readonly` wskazuje, że element członkowski `struct` nie ulega mutacji w wewnętrznym stanie struktury.
- W [`ref readonly` zwraca metodę](#ref-readonly-return-example), modyfikator `readonly` wskazuje, że metoda zwraca odwołanie, a zapisy nie są dozwolone dla tego odwołania.

Konteksty `readonly sturct` i `ref readonly` zostały dodane do C# 7,2. `readonly` członkowie struktury zostali dodani C# do 8,0

## <a name="readonly-field-example"></a>Przykład pola tylko do odczytu

W tym przykładzie nie można zmienić wartości pola `year` w metodzie `ChangeYear`, nawet jeśli przypisano mu wartość w konstruktorze klasy:

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

Wartość można przypisać do pola `readonly` tylko w następujących kontekstach:

- Gdy zmienna jest inicjowana w deklaracji, na przykład:

  ```csharp
  public readonly int y = 5;
  ```

- W konstruktorze wystąpienia klasy, która zawiera deklarację pola wystąpienia.
- W konstruktorze statycznym klasy, która zawiera deklarację pola statycznego.

Te konteksty konstruktorów są również jedynymi kontekstami, w których są poprawne do przekazywania pola `readonly` jako parametru [out](out-parameter-modifier.md) lub [ref](ref.md) .

> [!NOTE]
> Słowo kluczowe `readonly` różni się od słowa kluczowego [const](const.md) . Pole `const` można zainicjować tylko w deklaracji pola. Pole `readonly` można przypisać wiele razy w deklaracji pola i w konstruktorze. W związku z tym pola `readonly` mogą mieć różne wartości w zależności od użytego konstruktora. Ponadto, chociaż `const` pole jest stałą czasu kompilacji, pole `readonly` może być używane dla stałych środowiska uruchomieniowego, jak w poniższym przykładzie:
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

W poprzednim przykładzie, jeśli używasz instrukcji podobnej do poniższego przykładu:

```csharp
p2.y = 66;        // Error
```

zostanie wyświetlony komunikat o błędzie kompilatora:

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

## <a name="readonly-struct-example"></a>Przykład struktury ReadOnly

Modyfikator `readonly` w definicji `struct` deklaruje, że struktura jest **niezmienna**. Każde pole wystąpienia `struct` musi być oznaczone `readonly`, jak pokazano w następującym przykładzie:

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

Poprzedni przykład używa [Właściwości autoreadonly](../../properties.md#read-only) do deklarowania magazynu. Powoduje, że kompilator tworzy `readonly` pól zapasowych dla tych właściwości. Można również zadeklarować bezpośrednio `readonly` pól:

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

Dodawanie pola, które nie jest oznaczone `readonly` generuje błąd kompilatora `CS8340`: "wystąpienia pól struktur tylko do odczytu muszą być tylko do odczytu".

## <a name="readonly-member-examples"></a>Przykłady elementu członkowskiego tylko do odczytu

Innym razem można utworzyć strukturę, która obsługuje mutację. W takich przypadkach niektóre elementy członkowskie wystąpienia mogłyby nie modyfikować stanu wewnętrznego struktury. Można zadeklarować te elementy członkowskie wystąpienia za pomocą modyfikatora `readonly`. Kompilator wymusza przeznaczenie. Jeśli ten element członkowski modyfikuje stan bezpośrednio lub uzyskuje dostęp do elementu członkowskiego, który nie jest również zadeklarowany za pomocą modyfikatora `readonly`, wynikiem jest błąd czasu kompilacji. Modyfikator `readonly` jest prawidłowy dla elementów członkowskich `struct`, a nie `class` lub `interface` deklaracjach składowych.

Aby uzyskać dwie korzyści, należy zastosować modyfikator `readonly` do odpowiednich metod `struct`. Co najważniejsze, kompilator wymusza przeznaczenie. Kod, który modyfikuje stan, nie jest prawidłowy w metodzie `readonly`. Kompilator może również używać modyfikatora `readonly`, aby włączyć optymalizacje wydajności. Gdy duże typy `struct` są przesyłane przez odwołanie `in`, kompilator musi wygenerować kopię obronną, jeśli stan struktury może być modyfikowany. W przypadku uzyskiwania dostępu tylko do `readonly` członków kompilator nie może utworzyć kopii obronnej.

Modyfikator `readonly` jest prawidłowy dla większości elementów członkowskich `struct`, w tym metod, które zastępują metody zadeklarowane w <xref:System.Object?displayProperty=nameWithType>. Istnieją pewne ograniczenia:

- Nie można zadeklarować `readonly` statycznych elementów członkowskich.
- Nie można zadeklarować konstruktorów `readonly`.

Modyfikator `readonly` można dodać do deklaracji właściwości lub indeksatora:

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

Możliwe jest również dodanie modyfikatora `readonly` do poszczególnych `get` lub `set` metod dostępu do właściwości lub indeksatora:

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

Nie można dodać modyfikatora `readonly` do właściwości i co najmniej jednej metody dostępu tej samej właściwości. To samo ograniczenie dotyczy indeksatorów.

Kompilator niejawnie stosuje modyfikator `readonly`, aby wstępnie zaimplementowane właściwości, w których zaimplementowany kod kompilatora nie modyfikuje stanu. Jest to równoważne z następującymi deklaracjami:

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
``` 

Można dodać modyfikator `readonly` w tych lokalizacjach, ale nie będzie to miało znaczącego efektu. Nie można dodać modyfikatora `readonly` do autozaimplementowanej metody ustawiającej właściwości lub do właściwości autoimplementacji do odczytu/zapisu.

## <a name="ref-readonly-return-example"></a>Przykład powrotu ref ReadOnly

Modyfikator `readonly` na `ref return` wskazuje, że zwracane odwołanie nie może być modyfikowane. Poniższy przykład zwraca odwołanie do źródła. Używa modyfikatora `readonly`, aby wskazać, że obiekty wywołujące nie mogą modyfikować pochodzenia:

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
Zwrócony typ nie musi być `readonly struct`. Wszystkie typy, które mogą być zwracane przez `ref` mogą być zwracane przez `ref readonly`.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

Możesz również zobaczyć propozycje specyfikacji języka:

- [Typ ref i tylko do odczytu](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [elementy członkowskie struktury tylko do odczytu](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>Zobacz także

- [C#Odwoła](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory](modifiers.md)
- [const](const.md)
- [Pola](../../programming-guide/classes-and-structs/fields.md)
