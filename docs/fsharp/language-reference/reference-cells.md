---
title: Komórki odwołań (F#)
description: Dowiedz się, jak komórki odwołań F# są lokalizacje przechowywania, które umożliwiają tworzenie modyfikowalnych wartości z semantyką odwołań.
ms.date: 05/16/2016
ms.openlocfilehash: e2e1a91c62fd76e4992bc5ae11bb672766850718
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "44192271"
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

Programiści języka C# powinni wiedzieć, że `ref` w języku C# nie jest tak samo jak `ref` w języku F#. Równoważne konstrukcje w języku F# są [zkratka](byrefs.md), które są różne koncepcji z komórki odwołań.

Wartości oznaczone jako `mutable`może zostać automatycznie podwyższony do `'a ref` przechwycone przez zamknięcie; zobacz [wartości](values/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Parametry i argumenty](parameters-and-arguments.md)
- [Odwołanie do symboli i operatorów](symbol-and-operator-reference/index.md)
- [Wartości](values/index.md)
