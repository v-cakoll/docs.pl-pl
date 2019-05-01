---
title: do — Powiązania w klasach
description: Dowiedz się, jak używać F# "do" powiązanie w definicji klasy, która wykonuje akcje w przypadku, gdy obiekt jest konstruowany lub przy pierwszym użyciu typu.
ms.date: 05/16/2016
ms.openlocfilehash: 0ddf2b5ca458d0950c2e07bf2c37c205877e2173
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904595"
---
# <a name="do-bindings-in-classes"></a>do — Powiązania w klasach

A `do` powiązania w definicji klasy wykonuje akcje, gdy obiekt jest konstruowany lub, w przypadku statycznego `do` powiązania, gdy typ pierwszego.

## <a name="syntax"></a>Składnia

```fsharp
[static] do expression
```

## <a name="remarks"></a>Uwagi

A `do` powiązania pojawi się wraz z lub po `let` powiązania, ale przed definicje elementów członkowskich w definicji klasy. Mimo że `do` — słowo kluczowe jest opcjonalny w przypadku `do` powiązania na poziomie modułu nie jest opcjonalny w przypadku `do` powiązania w definicji klasy.

Do tworzenia wszystkich obiektów dowolnego danego typu, niestatycznej `do` powiązania i niestatycznych `let` powiązania są wykonywane w kolejności, w jakiej są wyświetlane w definicji klasy. Wiele `do` powiązania mogą wystąpić w jednym typie. Niestatyczna `let` powiązania i niestatycznych `do` powiązania stają się treść konstruktora podstawowego. Kod w niestatycznej `do` może odwoływać się w sekcji wiązania podstawowy Konstruktor parametrów i wartości lub funkcje, które są zdefiniowane w `let` sekcję wiązania.

Niestatycznych `do` powiązania mogą uzyskiwać dostęp do elementów członkowskich klasy tak długo, jak klasa ma własny identyfikator, który jest definiowany przez `as` — słowo kluczowe w klasie, nagłówek i tak długo, jak wszystkie przypadki użycia tych elementów członkowskich są kwalifikowany za pomocą własny identyfikator dla tej klasy.

Ponieważ `let` powiązania zainicjować pól prywatnych klasy, która często jest to niezbędne zagwarantować, że elementy Członkowskie zachowują się zgodnie z oczekiwaniami, `do` powiązania są zazwyczaj umieszczane po `let` powiązania tak, możesz pisać kod w `do` może powiązania są wykonywane z w pełni zainicjowanego obiektu. Jeśli kod próbuje przed zakończeniem inicjowania, należy użyć członka, zgłaszany jest InvalidOperationException.

Statyczne `do` powiązania mogą odwoływać się do statycznych elementów członkowskich lub pola otaczającej klasy, ale nie wystąpień elementów członkowskich lub pola. Statyczne `do` powiązania stają się częścią statycznego inicjatora dla klasy, która jest gwarantowane do wykonania przed pierwszym użyciu tej klasy.

Atrybuty są ignorowane w przypadku `do` powiązania w typach. Jeśli atrybut jest wymagany dla kodu, który jest wykonywany w `do` powiązania go muszą być stosowane do konstruktora podstawowego.

W poniższym kodzie klasy jest statyczną `do` powiązanie i niestatyczną `do` powiązania. Obiekt ma Konstruktor, który zawiera dwa parametry `a` i `b`, dwa pola prywatne są one definiowane w `let` powiązania dla tej klasy. Dwie właściwości są również określone. Wszystkie te znajdują się w zakresie w niestatycznej `do` sekcję wiązania, jak pokazano wiersza, który wyświetla wszystkie te wartości.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

Dane wyjściowe są następujące:

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a>Zobacz także

- [Elementy członkowskie](index.md)
- [Klasy](../classes.md)
- [Konstruktory](constructors.md)
- [`let` Powiązania w klasach](let-bindings-in-classes.md)
- [`do` Powiązania](../functions/do-Bindings.md)