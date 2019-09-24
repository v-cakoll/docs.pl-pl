---
title: Komórki odwołań
description: Dowiedz F# się, w jaki sposób komórki referencyjne są lokalizacjami przechowywania, które umożliwiają tworzenie modyfikowalnych wartości przy użyciu semantyki odwołania.
ms.date: 05/16/2016
ms.openlocfilehash: 2bca7797b272c0e7d5bf54df07041dc08e33709a
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216769"
---
# <a name="reference-cells"></a>Komórki odwołań

*Komórki odwołań* to lokalizacje przechowywania, które umożliwiają tworzenie modyfikowalnych wartości z semantyką odwołania.

## <a name="syntax"></a>Składnia

```fsharp
ref expression
```

## <a name="remarks"></a>Uwagi

Użyj `ref` operatora przed wartością, aby utworzyć nową komórkę odwołania, która hermetyzuje wartość. Podstawową wartość można będzie wtedy zmieniać, ponieważ jest ona modyfikowalna.

Komórka odwołania zawiera wartość rzeczywistą, a nie sam adres. Podczas tworzenia komórki odniesienia przy użyciu `ref` operatora należy utworzyć kopię bazowej wartości jako hermetyzowaną wartość modyfikowalną.

Można usunąć odwołanie do komórki odwołania przy użyciu `!` operatora (wykrzyknika).

Poniższy przykład kodu ilustruje deklarowanie i używanie komórek odwołań.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

Dane wyjściowe to `50`.

Komórki odwołań są wystąpieniami `Ref` typu rekordu ogólnego, który jest zadeklarowany w następujący sposób.

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

Typ `'a ref` jest synonimem dla `Ref<'a>`. Pierwszy zapis jest stosowany do wyświetlania tego typu w kompilatorze i technologii IntelliSense w środowisku IDE, jednak podstawowa definicja ma postać jak w drugim zapisie.

`ref` Operator tworzy nową komórkę odwołania. Poniższy kod jest deklaracją `ref` operatora.

```fsharp
let ref x = { contents = x }
```

W poniższej tabeli przedstawiono funkcje, które są dostępne w komórce odwołania.

|Operator, element członkowski lub pole|Opis|Typ|Definicja|
|--------------------------|-----------|----|----------|
|`!`(operator dereferencji)|Zwraca podstawową wartość.|`'a ref -> 'a`|`let (!) r = r.contents`|
|`:=`(operator przypisania)|Zmienia podstawową wartość.|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|`ref`zakład|Hermetyzuje wartość do nowej komórki odwołania.|`'a -> 'a ref`|`let ref x = { contents = x }`|
|`Value`wartość|Pobiera lub ustawia podstawową wartość.|`unit -> 'a`|`member x.Value = x.contents`|
|`contents`(pole rekordu)|Pobiera lub ustawia podstawową wartość.|`'a`|`let ref x = { contents = x }`|

Istnieje kilka sposobów dostępu do podstawowej wartości. Wartość zwrócona przez operator dereferencji (`!`) nie jest wartością, którą można przypisać. W związku z tym, jeśli modyfikujesz wartość podstawową, należy zamiast tego użyć operatora przypisania`:=`().

`Value` Obie właściwości`contents` i pola są wartościami możliwymi do przypisania. W związku z tym można za ich pomocą uzyskać dostęp do podstawowej wartości albo ją zmienić, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

Dane wyjściowe są następujące:

```console
10
10
11
12
```

Pole `contents` jest zapewniane pod kątem zgodności z innymi wersjami ml i podczas kompilacji generuje ostrzeżenie. Aby wyłączyć ostrzeżenie, użyj `--mlcompatibility` opcji kompilatora. Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md).

C#Programiści powinni wiedzieć, `ref` że C# w programie nie są takie same `ref` jak F#w. Równoważne konstrukcje w F# to [ByRef](byrefs.md), które są różnymi koncepcjami z komórek odwołań.

Wartości oznaczone jako `mutable`mogą zostać automatycznie podwyższone `'a ref` do, jeśli zostały przechwycone przez zamknięcie; zobacz [wartości](./values/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Parametry i argumenty](parameters-and-arguments.md)
- [Odwołanie do symboli i operatorów](./symbol-and-operator-reference/index.md)
- [Wartości](./values/index.md)
