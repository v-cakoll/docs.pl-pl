---
title: C#Instrukcje — przewodnik po C# języku
description: Tworzenie akcji C# programu przy użyciu instrukcji
ms.date: 02/27/2020
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: ced13b1bfd17977acb98bf33c0a477161cf08a93
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159107"
---
# <a name="statements"></a>Instrukcje

Akcje programu są wyrażane przy użyciu *instrukcji*. C#obsługuje kilka różnych rodzajów instrukcji, które są zdefiniowane w zakresie osadzonych instrukcji.

*Blok* umożliwia zapisanie wielu instrukcji w kontekstach, w których Pojedyncza instrukcja jest dozwolona. Blok składa się z listy instrukcji zapisanych między ogranicznikami `{` i `}`.

*Instrukcje deklaracji* są używane do deklarowania zmiennych lokalnych i stałych.

*Instrukcje wyrażeń* są używane do obliczania wyrażeń. Wyrażenia, które mogą być używane jako instrukcje, obejmują wywołania metod, alokacje obiektów za pomocą operatora `new`, przypisania przy użyciu `=` i operatory przypisania złożonego, operacje zwiększania i zmniejszania przy użyciu operatorów `++` i `--` oraz wyrażeń `await`.

*Instrukcje wyboru* są używane do wybierania jednej z wielu możliwych instrukcji do wykonania na podstawie wartości niektórych wyrażeń. Ta grupa zawiera instrukcje `if` i `switch`.

*Instrukcje iteracji* są używane do wielokrotnego wykonywania osadzonej instrukcji. Ta grupa zawiera instrukcje `while`, `do`, `for`i `foreach`.

*Instrukcje skoku* są używane do transferowania kontroli. Ta grupa zawiera instrukcje `break`, `continue`, `goto`, `throw`, `return`i `yield`.

Instrukcja `try`...`catch` służy do przechwytywania wyjątków występujących podczas wykonywania bloku, a instrukcja `try`...`finally` służy do określania kodu finalizacji, który jest zawsze wykonywany, niezależnie od tego, czy wystąpił wyjątek, czy nie.

Instrukcje `checked` i `unchecked` są używane do kontrolowania kontekstu sprawdzania przepełnienia dla operacji arytmetycznych typu całkowitego i konwersji.

Instrukcja `lock` służy do uzyskiwania blokady wzajemnego wykluczania dla danego obiektu, wykonywania instrukcji i zwalniania blokady.

Instrukcja `using` służy do uzyskiwania zasobu, wykonywania instrukcji i usuwania tego zasobu.

Poniżej wymieniono rodzaje instrukcji, które mogą być używane, i przedstawiono przykład dla każdego z nich.

* Deklaracja zmiennej lokalnej:

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* Lokalna deklaracja stała:

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* Instrukcja wyrażenia:

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* Instrukcja `if`:

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* Instrukcja `switch`:

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* Instrukcja `while`:

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* Instrukcja `do`:

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* Instrukcja `for`:

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* Instrukcja `foreach`:

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* Instrukcja `break`:

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* Instrukcja `continue`:

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* Instrukcja `goto`:

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* Instrukcja `return`:

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* Instrukcja `yield`:

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* instrukcje `throw` i instrukcje `try`:

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* instrukcje `checked` i `unchecked`:

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* Instrukcja `lock`:

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* Instrukcja `using`:

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
>[Poprzednie](expressions.md)
>[dalej](classes-and-objects.md)
