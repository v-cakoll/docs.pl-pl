---
title: Powiązania let w klasach
description: Dowiedz się, jak definiować pola prywatne i prywatne F# funkcje dla klas przy użyciu powiązań "let" w definicji klasy.
ms.date: 05/16/2016
ms.openlocfilehash: 1366ab8f1f4f606fe5947a8fc4df10de49346b3e
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216529"
---
# <a name="let-bindings-in-classes"></a>Powiązania let w klasach

Można definiować pola prywatne i prywatne funkcje dla F# klas przy użyciu `let` powiązań w definicji klasy.

## <a name="syntax"></a>Składnia

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>Uwagi

Poprzednia składnia jest wyświetlana po nagłówku klasy i deklaracji dziedziczenia, ale przed żadną definicją elementu członkowskiego. Składnia jest taka sama jak `let` w przypadku powiązań poza klasami, ale nazwy zdefiniowane w klasie mają zakres, który jest ograniczony do klasy. `let` Powiązanie tworzy pole prywatne lub funkcję, aby ujawnić dane lub funkcje publicznie, deklaruj właściwość lub metodę elementu członkowskiego.

Powiązanie, które nie jest statyczne jest nazywane powiązaniem `let`wystąpienia. `let` Powiązania `let` wystąpień są wykonywane podczas tworzenia obiektów. Powiązania `let` statyczne są częścią inicjatora statycznego dla klasy, która jest gwarantowana do wykonania przed pierwszym użyciem typu.

Kod w powiązaniach `let` wystąpień może używać parametrów konstruktora podstawowego.

Atrybuty i Modyfikatory dostępności są niedozwolone w `let` powiązaniach klas.

Poniższe przykłady kodu ilustrują kilka typów `let` powiązań w klasach.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

Dane wyjściowe są następujące:

```console
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>Alternatywne sposoby tworzenia pól

Możesz również użyć słowa kluczowego, `val` aby utworzyć pole prywatne. Przy użyciu `val` słowa kluczowego, pole nie otrzymuje wartości podczas tworzenia obiektu, ale zamiast tego jest inicjowane z wartością domyślną. Aby uzyskać więcej informacji, [Zobacz pola jawne: Val — słowo](explicit-fields-the-val-keyword.md)kluczowe.

Można również zdefiniować pola prywatne w klasie za pomocą definicji elementu członkowskiego i dodać słowo kluczowe `private` do definicji. Może to być przydatne, jeśli zamierzasz zmienić dostępność elementu członkowskiego bez konieczności ponownego pisania kodu. Aby uzyskać więcej informacji, zobacz [Access Control](../access-control.md).

## <a name="see-also"></a>Zobacz także

- [Elementy członkowskie](index.md)
- [`do`Powiązania w klasach](do-bindings-in-classes.md)
- [`let`Powiązań](../functions/let-bindings.md)
