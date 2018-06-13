---
title: Powiązania let w klasach (F#)
description: 'Dowiedz się, jak zdefiniować pól prywatnych i prywatne dla klas F # za pomocą powiązania "let" w definicji klasy.'
ms.date: 05/16/2016
ms.openlocfilehash: 1c17fe0edec14c28c9bdde86d0a2acb7c886cdf7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564550"
---
# <a name="let-bindings-in-classes"></a>Powiązania let w klasach

Można zdefiniować pól prywatnych i prywatne dla klas F # za pomocą `let` powiązania w definicji klasy.


## <a name="syntax"></a>Składnia

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>Uwagi
Poprzednie składni pojawia się po deklaracjach nagłówek i dziedziczenie klas, ale przed żadnych definicji elementu członkowskiego. Składnia jest na przykład systemu `let` powiązania poza klasy, ale nazw zdefiniowana w klasie mieć zakres, który jest ograniczona do klasy. A `let` powiązania tworzy pole prywatne lub funkcji; do udostępniania danych lub funkcje deklarować publicznie, właściwości lub metody elementu członkowskiego.

A `let` powiązanie nie jest statyczna nosi nazwę wystąpienia `let` powiązania. Wystąpienie `let` powiązania wykonania podczas tworzenia obiektów. Statyczne `let` powiązania są częścią inicjator statyczny dla klasy, która może wykonać przed pierwszym użyciu typu.

Kod w wystąpieniu `let` powiązania mogą używać parametrów podstawowego konstruktora.

Atrybuty i modyfikatory dostępności są niedozwolone w `let` powiązania w klasach.

Poniższe przykłady kodu przedstawiają kilka typów `let` powiązania w klasach.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

Dane wyjściowe są następujące:

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>Alternatywne metody tworzenia pól
Można również użyć `val` — słowo kluczowe, aby utworzyć pole prywatne. Korzystając z `val` — słowo kluczowe, pole nie zostanie podany, wartość, gdy obiekt jest tworzony, ale zamiast tego jest zainicjowany z wartością domyślną. Aby uzyskać więcej informacji, zobacz [pola jawne: val — słowo kluczowe](explicit-fields-the-val-keyword.md).

Można także zdefiniować pól prywatnych w klasie, przy użyciu definicji elementu członkowskiego i dodając słowo kluczowe `private` do definicji. Może to być przydatne, Jeśli przypuszczasz, że Zmień dostępność elementu członkowskiego bez ponownego tworzenia kodu. Aby uzyskać więcej informacji, zobacz [kontroli dostępu](../access-control.md).

## <a name="see-also"></a>Zobacz też
[Elementy członkowskie](index.md)

[`do` Powiązania w klasach](do-bindings-in-classes.md)

[`let` Powiązania](../functions/let-bindings.md)
