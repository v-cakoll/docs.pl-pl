---
title: Komórki odwołań (F#)
description: 'Dowiedz się, jak F # odwołanie do komórki są lokalizacje magazynu, które umożliwiają tworzenie wartości modyfikowalne z semantykę odwołania.'
ms.date: 05/16/2016
ms.openlocfilehash: d68726619bdfce5a9ed9bd94d6434427644cd9f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="reference-cells"></a>Komórki odwołań

*Odwołanie do komórki* są lokalizacje magazynu, które umożliwiają tworzenie wartości modyfikowalne z semantykę odwołania.

## <a name="syntax"></a>Składnia

```fsharp
ref expression
```

## <a name="remarks"></a>Uwagi
Możesz użyć `ref` operator przed wartością do utworzenia nowego hermetyzujący wartość komórki odwołania. Podstawową wartość można będzie wtedy zmieniać, ponieważ jest ona modyfikowalna.

Komórka odwołania zawiera wartość rzeczywistą, a nie sam adres. Po utworzeniu komórka odwołania przy użyciu `ref` operatora, Utwórz kopię odpowiednia wartość jako hermetyzowany modyfikowalne wartości.

Odwołanie do komórki można wyłuskać przy użyciu `!` — operator (eliminacja).

Poniższy przykład kodu ilustruje deklarowanie i używanie komórek odwołań.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

Dane wyjściowe `50`.

Komórki odwołań są wystąpieniami klasy `Ref` typu ogólnego rekordu, który został zadeklarowany w następujący sposób.

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

Typ `'a ref` jest synonimem `Ref<'a>`. Pierwszy zapis jest stosowany do wyświetlania tego typu w kompilatorze i technologii IntelliSense w środowisku IDE, jednak podstawowa definicja ma postać jak w drugim zapisie.

`ref` Operator tworzy nowe odwołanie do komórki. Następujący kod jest deklaracja `ref` operatora.

```fsharp
let ref x = { contents = x }
```

W poniższej tabeli przedstawiono funkcje, które są dostępne w komórce odwołania.

|Operator, element członkowski lub pole|Opis|Typ|Definicja|
|--------------------------|-----------|----|----------|
|`!` (operatora anulowania odwołania do)|Zwraca podstawową wartość.|`'a ref -> 'a`|`let (!) r = r.contents`|
|`:=` (operator przypisania)|Zmienia podstawową wartość.|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|`ref` (operator)|Hermetyzuje wartość do nowej komórki odwołania.|`'a -> 'a ref`|`let ref x = { contents = x }`|
|`Value` (właściwości)|Pobiera lub ustawia podstawową wartość.|`unit -> 'a`|`member x.Value = x.contents`|
|`contents` (pola rekordu)|Pobiera lub ustawia podstawową wartość.|`'a`|`let ref x = { contents = x }`|
Istnieje kilka sposobów dostępu do podstawowej wartości. Wartość zwracana przez dereference operator (`!`) nie jest możliwa do przypisania wartości. W związku z tym jeśli modyfikujesz odpowiednia wartość, należy użyć operatora przypisania (`:=`) zamiast tego.

Zarówno `Value` właściwości i `contents` pola są można przypisać wartości. W związku z tym można za ich pomocą uzyskać dostęp do podstawowej wartości albo ją zmienić, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

Dane wyjściowe są następujące:

```
10
10
11
12
```

Pole `contents` zapewnia zgodność z innymi wersjami programu ML i spowoduje wygenerowanie ostrzeżenia podczas kompilacji. Aby wyłączyć ostrzeżenia, należy użyć `--mlcompatibility` — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md).

Poniższy fragment kodu ilustruje używanie komórek odwołań w przekazywaniu parametrów. Typ Incrementor ma metodę przyrostu, która przyjmuje parametr, który zawiera parametr typu byref. Byref w typ parametru wskazuje, że obiekty wywołujące musi upłynąć komórka odwołania lub adresu zmiennej typowe określonego typu w tej sprawy int. Pozostały kod przedstawia sposób wywołania przyrostu z obu typów argumentów i pokazano sposób użycia operatora ref w zmiennej, aby utworzyć komórka odwołania (ref myDelta1). Następnie przedstawiono użycie address-of — operator (&amp;) do generowania odpowiednich argumentu. Na koniec Increment — metoda jest wywoływana ponownie przy użyciu komórka odwołania, które są zadeklarowane za pomocą powiązania let. Końcowe wiersz kodu przedstawiono użycie! operatora, aby usunąć odwołania do komórka odwołania do drukowania.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

Aby uzyskać więcej informacji na temat przekazywane przez odwołanie, zobacz [parametry i argumenty](parameters-and-arguments.md).

>[!NOTE]
C# programistów wiedzieć, że ten ref działa inaczej w języku F # niż w języku C#. Na przykład użycie ref, jeśli argument nie ma ten sam efekt w języku F # jak w języku C#.

## <a name="consuming-c-ref-returns"></a>C# — zużywanie `ref` zwraca

Począwszy od 4.1 F #, będzie można korzystać z `ref` zwraca wygenerowany w języku C#.  Wynik wywołania takie jest `byref<_>` wskaźnika.

Następujące C# metody:

```csharp
namespace RefReturns
{
    public static class RefClass
    {
        public static ref int Find(int val, int[] vals)
        {
            for (int i = 0; i < vals.Length; i++)
            {
                if (vals[i] == val)
                {
                    return ref numbers[i]; // Returns the location, not the value
                }
            }

            throw new IndexOutOfRangeException($"{nameof(number)} not found");
        }
    }
}
```

Może być przezroczysty wywołany przez język F # z nie specjalnych składni:

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

Można również zadeklarować funkcji, które można podjąć `ref` zwracać jako danych wejściowych, na przykład:

```fsharp
let f (x: byref<int>) = &x
```

Obecnie nie istnieje sposób do generowania `ref` zwracany w języku F #, który może być używana w języku C#.

## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)

[Parametry i argumenty](parameters-and-arguments.md)

[Odwołanie do symboli i operatorów](symbol-and-operator-reference/index.md)
