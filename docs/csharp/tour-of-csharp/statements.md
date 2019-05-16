---
title: C#Instrukcje — Przewodnik po przykładzie C# języka
description: Utwórz akcje C# program za pomocą instrukcji
ms.date: 11/06/2016
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: 26b151bc116dde9120757f954bdcf3aee041c5f5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634543"
---
# <a name="statements"></a>Instrukcje

Akcje programu są wyrażone za pomocą *instrukcji*. C# obsługuje wiele rodzajów instrukcji, z których są definiowane zgodnie z osadzonych instrukcji.

A *bloku* zezwala na wiele instrukcji, które ma zostać zapisany w kontekstach, których jest dozwolone pojedynczej instrukcji. Blok zawiera listę instrukcji, zapisywane między ogranicznikami `{` i `}`.

*Instrukcje deklaracji* są używane do deklarowania stałe i zmienne lokalne.

*Instrukcje wyrażeń* są używane do oceny wyrażenia. Wyrażenia, które mogą służyć jako stwierdzenia obejmują wywołań metod obiektu alokacje za pomocą `new` operator, za pomocą przypisań `=` i operatorów przypisania złożonego, operacje inkrementacji i dekrementacji przy użyciu `++`i `--` operatorów i `await` wyrażenia.

*Instrukcje wyboru* są używane, aby wybrać jeden z wielu możliwych instrukcji do wykonania na podstawie wartości w wyrażeniu. W tej grupie są `if` i `switch` instrukcji.

*Instrukcje iteracji* są używane do wykonywania wielokrotnie osadzona instrukcja. W tej grupie są `while`, `do`, `for`, i `foreach` instrukcji.

*Instrukcje skoku* służą do przekazywania kontroli. W tej grupie są `break`, `continue`, `goto`, `throw`, `return`, i `yield` instrukcji.

`try`... `catch` instrukcja jest używane do przechwytywania wyjątków, które występują podczas wykonywania blok, a `try`... `finally` instrukcja jest używane do określenia kod finalizacji, który jest zawsze wykonywana, czy wystąpił wyjątek, czy nie.

`checked` i `unchecked` instrukcje są używane do kontrolowania kontekstu sprawdzającego przepełnienie typu całkowitego operacje arytmetyczne i konwersje.

`lock` Instrukcja jest używane do uzyskania blokadę wykluczania wzajemnego dla danego obiektu, wykonania instrukcji i następnie zwalnia blokadę.

`using` Instrukcja jest używane do uzyskania zasobu, należy wykonać instrukcję, a następnie usunąć tego zasobu.

Poniżej wymieniono rodzaje instrukcji, które mogą być używane i przedstawiono przykład dla każdego.

* Deklaracji zmiennej lokalnej:

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* Deklaracji stałej lokalnej:

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* Instrukcja wyrażeń:

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* `if` Instrukcja:

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* `switch` Instrukcja:

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* `while` Instrukcja:

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* `do` Instrukcja:

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* `for` Instrukcja:

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* `foreach` Instrukcja:

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* `break` Instrukcja:

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* `continue` Instrukcja:

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* `goto` Instrukcja:

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* `return` Instrukcja:

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* `yield` Instrukcja:

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* `throw` instrukcje i `try` instrukcji:

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* `checked` i `unchecked` instrukcji:

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* `lock` Instrukcja:

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* `using` Instrukcja:

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
>[Poprzednie](expressions.md)
>[dalej](classes-and-objects.md)
