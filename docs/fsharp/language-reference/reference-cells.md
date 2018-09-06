---
title: Komórki odwołań (F#)
description: 'Dowiedz się, jak komórki odwołań F # są lokalizacje przechowywania, które umożliwiają tworzenie modyfikowalnych wartości z semantyką odwołań.'
ms.date: 05/16/2016
ms.openlocfilehash: 133aec6b162a13306a05c9afa172f859890565eb
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892427"
---
# <a name="reference-cells"></a>Komórki odwołań

*Komórki odwołań* to lokalizacje przechowywania, które umożliwiają tworzenie modyfikowalnych wartości z semantyką odwołań.

## <a name="syntax"></a>Składnia

```fsharp
ref expression
```

## <a name="remarks"></a>Uwagi

Możesz użyć `ref` przed wartością operatora do utworzenia nowej komórki odwołania, która hermetyzuje wartość. Podstawową wartość można będzie wtedy zmieniać, ponieważ jest ona modyfikowalna.

Komórka odwołania zawiera wartość rzeczywistą, a nie sam adres. Podczas tworzenia komórek odwołań za pomocą `ref` operatora, Utwórz kopię podstawowej wartości jako hermetyzowana wartość modyfikowalna.

Komórkę odwołania można wyłuskać za pomocą `!` — operator (wykrzyknika).

Poniższy przykład kodu ilustruje deklarowanie i używanie komórek odwołań.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

Dane wyjściowe są `50`.

Komórki odwołań są wystąpieniami `Ref` ogólnego typu rekordu, który jest zadeklarowany w następujący sposób.

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

Typ `'a ref` jest synonimem dla `Ref<'a>`. Pierwszy zapis jest stosowany do wyświetlania tego typu w kompilatorze i technologii IntelliSense w środowisku IDE, jednak podstawowa definicja ma postać jak w drugim zapisie.

`ref` Operatora powoduje utworzenie nowej komórki odwołania. Poniższy kod stanowi deklarację `ref` operatora.

```fsharp
let ref x = { contents = x }
```

W poniższej tabeli przedstawiono funkcje, które są dostępne w komórce odwołania.

|Operator, element członkowski lub pole|Opis|Typ|Definicja|
|--------------------------|-----------|----|----------|
|`!` (operator dereferencji)|Zwraca podstawową wartość.|`'a ref -> 'a`|`let (!) r = r.contents`|
|`:=` (operator przypisania)|Zmienia podstawową wartość.|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|`ref` (operator)|Hermetyzuje wartość do nowej komórki odwołania.|`'a -> 'a ref`|`let ref x = { contents = x }`|
|`Value` (właściwość)|Pobiera lub ustawia podstawową wartość.|`unit -> 'a`|`member x.Value = x.contents`|
|`contents` (pole rekordu)|Pobiera lub ustawia podstawową wartość.|`'a`|`let ref x = { contents = x }`|
Istnieje kilka sposobów dostępu do podstawowej wartości. Wartość zwracana przez operator wyłuskania (`!`) nie jest przypisywalna. W związku z tym, jeśli w przypadku modyfikowania podstawowej wartości należy użyć operatora przypisania (`:=`) zamiast tego.

Zarówno `Value` właściwości i `contents` są przypisywalne. W związku z tym można za ich pomocą uzyskać dostęp do podstawowej wartości albo ją zmienić, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

Dane wyjściowe są następujące:

```
10
10
11
12
```

Pole `contents` zapewnia zgodność z innymi wersjami języka ML i spowoduje wygenerowanie ostrzeżenia podczas kompilacji. Aby wyłączyć to ostrzeżenie, użyj `--mlcompatibility` — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [opcje kompilatora](compiler-options.md).

Poniższy fragment kodu ilustruje używanie komórek odwołań w przekazywaniu parametrów. Typ Incrementor ma metodę inkrementacji, który przyjmuje parametr, który zawiera typ parametru byref. Byref w typie parametru wskazuje, że obiekty wywołujące muszą przekazywać komórkę odwołania lub adres typowej zmiennej o określonym typie, w tym przypadków int. Pozostały kod ilustruje sposób wywołania metody przyrostu z oboma tymi typami argumentów i pokazuje użycie operatora ref w zmiennej, aby utworzyć komórki odwołania (ref myDelta1). Następnie prezentuje użycie operatora address-of (&amp;) do wygenerowania odpowiedniego argumentu. Na koniec przyrost jest ponownie wywoływana metoda przy użyciu komórki odwołania, która jest zadeklarowana za pomocą powiązania let. Ostatni wiersz kodu ilustruje użycie! operator, który ma być wyłuskania komórki odwołania na potrzeby drukowania.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

Aby uzyskać więcej informacji na temat przekazywania odwołania, zobacz [parametrami i argumentami](parameters-and-arguments.md).

>[!NOTE]
Programiści języka C# wiedzieć, że ten ref działa inaczej w języku F # niż w języku C#. Na przykład użycie ref podczas przekazywania argumentu ma ten sam efekt w języku F # jak w języku C#.

>[!NOTE]
`mutable` Zmienne mogą zostać automatycznie podwyższony do `'a ref` przechwycone przez zamknięcie; zobacz [wartości](values/index.md).

## <a name="consuming-c-ref-returns"></a>C# — zużywanie `ref` zwraca

Począwszy od F # 4.1, mogą wykorzystywać `ref` zwraca generowane w języku C#.  Wynik takich wywołań to `byref<_>` wskaźnika.

Następujące metodę języka C#:

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

Może być przezroczysty wywołany przez język F # z nie specjalnej składni:

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

Można również zadeklarować funkcji, może to potrwać `ref` Zwróć jako danych wejściowych, na przykład:

```fsharp
let f (x: byref<int>) = &x
```

Obecnie nie istnieje sposób do generowania `ref` zwracany w języku F #, która może być używane w języku C#.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Parametry i argumenty](parameters-and-arguments.md)
- [Odwołanie do symboli i operatorów](symbol-and-operator-reference/index.md)
- [Wartości](values/index.md)
