---
title: Powiązania let w klasach (F#)
description: 'Dowiedz się, jak zdefiniować pola prywatne i prywatne funkcje dla klas F # za pomocą powiązania "let" w definicji klasy.'
ms.date: 05/16/2016
ms.openlocfilehash: 237eb98a57571a21c9187abf31f05160374cf4fc
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47210243"
---
# <a name="let-bindings-in-classes"></a>Powiązania let w klasach

Można zdefiniować pola prywatne i prywatne funkcje dla klas F # za pomocą `let` powiązania w definicji klasy.

## <a name="syntax"></a>Składnia

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>Uwagi

Składnia poprzednich pojawia się po deklaracjach nagłówek i dziedziczenie klasy, ale przed wszystkie definicje elementów członkowskich. Składnia jest podobne do metody `let` powiązania poza klasy, ale nazw zdefiniowana w klasie mają zakres, który jest ograniczony do klasy. A `let` powiązania tworzy pole prywatne lub funkcję; aby uwidocznić dane lub funkcje deklarować publicznie, właściwość lub metoda elementu członkowskiego.

A `let` powiązanie nie jest statyczna nosi nazwę wystąpienia `let` powiązania. Wystąpienie `let` powiązania wykonania podczas tworzenia obiektów. Statyczne `let` powiązania są częścią statycznego inicjatora dla klasy, która jest gwarantowane do wykonania przed pierwszym użyciu typu.

Kod w wystąpieniu `let` powiązania, można użyć parametrów konstruktora podstawowego.

Atrybuty i modyfikatory dostępności nie są dozwolone w `let` powiązania w klasach.

W poniższych przykładach kodu pokazano kilka typów `let` powiązania w klasach.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

Dane wyjściowe są następujące:

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>Alternatywne sposoby tworzenia pól

Można również użyć `val` — słowo kluczowe, aby utworzyć pole prywatne. Korzystając z `val` — słowo kluczowe, pole nie zostanie podany wartość, gdy obiekt zostanie utworzony, ale zamiast tego jest inicjowany z wartością domyślną. Aby uzyskać więcej informacji, zobacz [pola jawne: val — słowo kluczowe](explicit-fields-the-val-keyword.md).

Można również definiować pola prywatne w klasie, przy użyciu definicji elementu członkowskiego i dodanie słowa kluczowego `private` do definicji. Może to być przydatne, jeśli spodziewasz się Zmień dostępność elementu członkowskiego, bez konieczności ponownego zapisu kodu. Aby uzyskać więcej informacji, zobacz [kontroli dostępu](../access-control.md).

## <a name="see-also"></a>Zobacz także

- [Elementy członkowskie](index.md)
- [`do` Powiązania w klasach](do-bindings-in-classes.md)
- [`let` Powiązania](../functions/let-bindings.md)
