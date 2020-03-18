---
title: C# Instrukcje — przewodnik po języku Języka C#
description: Akcje programu C# można tworzyć przy użyciu instrukcji
ms.date: 02/27/2020
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: ced13b1bfd17977acb98bf33c0a477161cf08a93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159107"
---
# <a name="statements"></a>Instrukcje

Akcje programu są wyrażane za pomocą *instrukcji*. C# obsługuje kilka różnych rodzajów instrukcji, z których wiele jest zdefiniowanych w kategoriach osadzonych instrukcji.

*Blok* zezwala na wiele instrukcji do zapisu w kontekstach, w których pojedyncza instrukcja jest dozwolona. Blok składa się z listy instrukcji napisanych `{` `}`między ogranicznikami i .

*Instrukcje deklaracji* są używane do deklarowania zmiennych lokalnych i stałych.

*Instrukcje wyrażenia* są używane do oceny wyrażeń. Wyrażenia, które mogą być używane jako instrukcje obejmują wywołania `new` metody, alokacje obiektów przy użyciu operatora, przypisania `=` przy `++` `--` użyciu `await` i operatorów przypisania złożonego, operacje przyrostu i zmniejszania przy użyciu i operatorów i wyrażeń.

*Instrukcje wyboru* są używane do wybierania jednej z wielu możliwych instrukcji do wykonania na podstawie wartości niektórych wyrażeń. Ta grupa `if` zawiera `switch` i instrukcje.

*Instrukcje iteracji* są używane do wykonywania wielokrotnie osadzone instrukcji. Ta grupa `while`zawiera `do` `for`, `foreach` , i instrukcje.

*Instrukcje skoku* są używane do przenoszenia kontroli. Ta grupa `break`zawiera `continue` `goto`, `throw` `return`, `yield` , , i instrukcje.

W `try`... `catch` instrukcja służy do wychwytywania wyjątków, które występują podczas wykonywania bloku, a `try`... `finally` instrukcja służy do określania kodu finalizacji, który jest zawsze wykonywany, niezależnie od tego, czy wystąpił wyjątek, czy nie.

I `checked` `unchecked` instrukcje są używane do kontrolowania kontekstu sprawdzania przepełnienia dla operacji arytmetycznych typu integralnego i konwersji.

Instrukcja `lock` jest używana do uzyskania blokady wzajemnego wykluczenia dla danego obiektu, wykonać instrukcję, a następnie zwolnić blokadę.

Instrukcja `using` jest używana do uzyskania zasobu, wykonania instrukcji, a następnie usunięcia tego zasobu.

Poniżej wymieniono rodzaje instrukcji, które mogą być używane i stanowi przykład dla każdego.

* Deklaracja zmiennej lokalnej:

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* Stała deklaracja lokalna:

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* Instrukcja wyrażenia:

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* `if`Instrukcja:

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* `switch`Instrukcja:

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* `while`Instrukcja:

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* `do`Instrukcja:

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* `for`Instrukcja:

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* `foreach`Instrukcja:

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* `break`Instrukcja:

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* `continue`Instrukcja:

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* `goto`Instrukcja:

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* `return`Instrukcja:

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* `yield`Instrukcja:

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* `throw`oświadczenia `try` i oświadczenia:

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* `checked`i `unchecked` oświadczenia:

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* `lock`Instrukcja:

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* `using`Instrukcja:

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
>[Poprzedni](expressions.md)
>[następny](classes-and-objects.md)
