---
title: "do — Powiązania w klasach (F#)"
description: "Dowiedz się, jak używać F # \"do\" powiązanie w definicji klasy, która wykonuje akcje podczas konstruowania obiektu lub przy pierwszym użyciu typu."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 78987cb8-bdba-46e2-b5b2-994c83fe42c4
ms.openlocfilehash: f9582338306d87c3dd799425083037cc95b31b1e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="do-bindings-in-classes"></a>do — Powiązania w klasach

A `do` powiązanie w definicji klasy wykonuje akcje podczas konstruowania obiektu lub, w przypadku statycznego `do` powiązanie, gdy typ jest najpierw używany.


## <a name="syntax"></a>Składnia

```fsharp
[static] do expression
```

## <a name="remarks"></a>Uwagi
A `do` powiązania pojawi się wraz z lub po `let` powiązania, ale przed definicji elementu członkowskiego w definicji klasy. Mimo że `do` — słowo kluczowe jest opcjonalne dla `do` powiązania na poziomie modułu nie jest opcjonalny w przypadku `do` powiązania w definicji klasy.

Do tworzenia każdy obiekt dowolnego danego typu, niestatyczna `do` powiązania i niestatyczna `let` powiązania są wykonywane w kolejności, w jakiej występują w definicji klasy. Wiele `do` powiązania może wystąpić w jednym typie. Niestatyczna `let` powiązania i niestatyczna `do` powiązania stają się treści podstawowego konstruktora. Kod w niestatycznym `do` sekcji powiązania może odwoływać się parametrami konstruktora podstawowego oraz wartości lub funkcje, które są zdefiniowane w `let` sekcji powiązania.

Niestatyczne `do` powiązania mogą uzyskiwać dostęp do elementów członkowskich klasy, tak długo, jak klasa ma własnego identyfikatora, który jest zdefiniowany przez `as` — słowo kluczowe w klasie, nagłówek i tak długo, jak wszystkie używa tych członków jest kwalifikowany za pomocą własnego identyfikatora klasy.

Ponieważ `let` powiązania zainicjować pól prywatnych klasy, która jest często zagwarantowanie, że członkowie działać zgodnie z oczekiwaniami, `do` powiązania są zwykle umieszczane po `let` powiązania, który kod w `do` może powiązania wykonywane za pomocą obiektu pełni zainicjowany. Jeśli kod spróbuje przed zakończeniem inicjowania, należy użyć członka, InvalidOperationException jest wywoływane.

Statyczne `do` powiązania może odwoływać się elementy członkowskie static lub pola otaczającej klasy, ale nie wystąpienia elementów członkowskich lub pól. Statyczne `do` powiązania staną się częścią inicjator statyczny dla klasy, która może wykonać przed pierwszym użyciu tej klasy.

Atrybuty są ignorowane w przypadku `do` powiązania w typach. Jeśli atrybut jest wymagany dla kodu, który wykonuje `do` powiązanie, jego musi odnosić się do podstawowego konstruktora.

W poniższym kodzie klasa ma statycznych `do` powiązania i niestatyczną `do` powiązania. Obiekt ma konstruktora, który zawiera dwa parametry `a` i `b`, i dwa pola prywatne są zdefiniowane w `let` powiązania dla tej klasy. Również zdefiniowano dwie właściwości. Wszystkie te są w zakresie niestatyczna `do` sekcji powiązania, jak to pokazano wiersza, który wyświetla wszystkie te wartości.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

Dane wyjściowe są następujące:

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a>Zobacz też
[Elementy członkowskie](index.md)

[Klasy](../classes.md)

[Konstruktory](constructors.md)

[`let`Powiązania w klasach](let-bindings-in-classes.md)

[`do`Powiązania](../functions/do-Bindings.md)
