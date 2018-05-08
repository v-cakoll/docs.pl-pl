---
title: C# instrukcje — samouczek języka C#
description: Utwórz akcje programu C# przy użyciu instrukcji
ms.date: 11/06/2016
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: 2f25c07ccc0af27a503465b9414bf607c61d1b2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="statements"></a>Instrukcje

Akcje programu są wyrażane przy użyciu *instrukcje*. C# obsługuje wiele rodzajów instrukcje liczba zdefiniowanych pod względem instrukcji osadzonych.

A *bloku* zezwala na użycie wielu instrukcji w kontekstach, których jednej instrukcji jest dozwolone. Blok składa się z listy instrukcji zapisywane między ograniczniki `{` i `}`.

*Instrukcje deklaracji* są używane do deklarowania zmiennych lokalnych i stałe.

*Instrukcje wyrażeń* są używane do analizowania wyrażenia. Wyrażeń, które mogą być używane jako instrukcje obejmują wywołań metody opisywanego obiekt alokacji używających `new` operator, za pomocą przypisań `=` oraz złożone operatory przypisania, inkrementacja i dekrementacja operacje przy użyciu `++`i `--` operatory i `await` wyrażenia.

*Instrukcje wyboru* służą do wybierania jeden z wielu instrukcji możliwych do wykonania na podstawie wartości niektóre wyrażenia. W tej grupie są `if` i `switch` instrukcje.

*Instrukcje iteracji* są używane wielokrotnie wykonać instrukcję osadzonych. W tej grupie są `while`, `do`, `for`, i `foreach` instrukcje.

*Instrukcje skoku* są używane do przekazywania kontroli. W tej grupie są `break`, `continue`, `goto`, `throw`, `return`, i `yield` instrukcje.

`try`... `catch` przechwytują wyjątki, jakie występują podczas wykonywania blok, używana jest instrukcja i `try`... `finally` instrukcji służy do określania finalizacji kod, który jest zawsze wykonywana, czy nie wystąpił wyjątek.

`checked` i `unchecked` instrukcje są używane do kontrolowania kontekst sprawdzanie przepełnienia dla operacji arytmetycznych typem całkowitym i konwersji.

`lock` Instrukcji służy do uzyskania blokady wzajemnego wykluczeń dla danego obiektu, wykonania instrukcji, a następnie zwolnij blokady.

`using` Instrukcji jest używany do uzyskania zasobu, wykonania instrukcji i następnie usuwania tego zasobu.

Poniżej wymieniono rodzaje instrukcji, które mogą być używane i zawiera przykład dla każdego.

* Deklaracja zmiennej lokalnej:

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* Deklaracja stałej lokalna:

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
[Poprzednie](expressions.md)
[dalej](classes-and-objects.md)
