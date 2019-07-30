---
title: do — Powiązania w klasach
description: Dowiedz się, jak F# używać powiązania "do" w definicji klasy, która wykonuje akcje, gdy obiekt jest konstruowany lub gdy typ jest używany jako pierwszy.
ms.date: 05/16/2016
ms.openlocfilehash: ced4f1bb17d9e23bf51cc79b5a275cc334cca013
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627588"
---
# <a name="do-bindings-in-classes"></a>do — Powiązania w klasach

Powiązanie w definicji klasy wykonuje akcje, gdy obiekt jest konstruowany lub dla powiązania statycznego `do` , gdy typ jest używany jako pierwszy. `do`

## <a name="syntax"></a>Składnia

```fsharp
[static] do expression
```

## <a name="remarks"></a>Uwagi

Powiązanie występuje razem z lub po `let` powiązaniach, ale przed definicjami elementów członkowskich w definicji klasy. `do` Chociaż słowo kluczowe jest opcjonalne dla `do` powiązań na poziomie modułu, nie jest opcjonalne dla `do` powiązań w definicji klasy. `do`

Dla konstrukcji każdego obiektu dowolnego danego typu, niestatyczne `do` powiązania i niestatyczne `let` powiązania są wykonywane w kolejności, w jakiej występują w definicji klasy. W `do` jednym typie może wystąpić wiele powiązań. Powiązania niestatyczne `let` i powiązania niestatyczne `do` stają się treścią głównego konstruktora. Kod w sekcji powiązania niestatyczne `do` może odwoływać się do parametrów konstruktora podstawowego i wszelkich wartości lub funkcji, które są zdefiniowane `let` w sekcji powiązania.

Niestatyczne `do` powiązania mogą uzyskać dostęp do elementów członkowskich klasy, o ile Klasa ma własny identyfikator, który jest zdefiniowany `as` przez słowo kluczowe w nagłówku klasy, i tak długo, jak wszystkie zastosowania tych elementów są kwalifikowane przy użyciu samodzielnego identyfikatora dla klasy.

Ze `let` względu na to, że powiązania inicjują pola prywatne klasy, co jest często niezbędne do zagwarantowania `do` , że elementy członkowskie zachowują się zgodnie z oczekiwaniami, `do` powiązania są zwykle umieszczane po `let` powiązaniach, aby kod w powiązaniu mógł Wykonaj z w pełni zainicjowanym obiektem. Jeśli kod próbuje użyć elementu członkowskiego przed ukończeniem inicjowania, zostanie zgłoszony InvalidOperationException.

Powiązania `do` statyczne mogą odwoływać się do statycznych elementów członkowskich lub pól z otaczającej klasy, ale nie elementów członkowskich lub pól wystąpień. Powiązania `do` statyczne stają się częścią inicjatora statycznego dla klasy, która jest gwarantowana do wykonania przed pierwszym użyciem klasy.

Atrybuty są ignorowane dla `do` powiązań w typach. Jeśli atrybut jest wymagany dla kodu, który jest wykonywany w `do` powiązaniu, musi zostać zastosowany do głównego konstruktora.

W poniższym kodzie Klasa ma powiązanie statyczne `do` i powiązanie niestatyczne. `do` Obiekt ma Konstruktor, który ma dwa parametry, `a` i `b`i dwa prywatne `let` pola są zdefiniowane w powiązaniach dla klasy. Zdefiniowano również dwie właściwości. Wszystkie te elementy znajdują się w zakresie w sekcji powiązania `do` niestatyczne, jak pokazano w wierszu, który drukuje wszystkie wartości.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

Dane wyjściowe są następujące:

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a>Zobacz także

- [Elementy członkowskie](index.md)
- [Klasy](../classes.md)
- [Konstruktory](constructors.md)
- [`let`Powiązania w klasach](let-bindings-in-classes.md)
- [`do`Powiązań](../functions/do-Bindings.md)
