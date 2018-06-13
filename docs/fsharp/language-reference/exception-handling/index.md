---
title: Obsługa wyjątków (F#)
description: 'Poznaj podstawy obsługi wyjątków w F # i łącza do obsługi wyrażeń i funkcji wyjątków.'
ms.date: 05/16/2016
ms.openlocfilehash: fc89feb0d21bc823cb105e435413f8309cd6174c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564329"
---
# <a name="exception-handling"></a>Obsługa wyjątków

Ta sekcja zawiera informacje o pomocy technicznej w języku F # obsługi wyjątków.


## <a name="exception-handling-basics"></a>Podstawowe informacje dotyczące obsługi wyjątków
Obsługa wyjątków jest standardowym sposobem obsługi błędów w programie .NET Framework. W związku z tym dowolnego języka .NET musi obsługiwać ten mechanizm, w tym F #. *Wyjątek* jest obiekt hermetyzujący informacje o błędzie. Jeśli wystąpią błędy, wyjątki są zatrzymuje wykonywanie zostaje zgłoszone, a regularne. Zamiast tego środowiska uruchomieniowego wyszukuje odpowiednią obsługę wyjątku. Wyszukiwanie rozpoczyna się bieżącą funkcję i będzie kontynuowana górę stosu za pośrednictwem warstw obiektów wywołujących, aż do znalezienia zgodnego programu obsługi. Następnie program obsługi jest wykonywany.

Ponadto, ponieważ stos jest oddzielić, środowiska uruchomieniowego wykonuje żadnego kodu w `finally` bloków, aby zagwarantować, że obiekty są czyszczone poprawnie podczas procesu odwijaniem.


## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----|-----------|
|[Typy wyjątków](exception-types.md)|Opisuje sposób zadeklarować typ wyjątku.|
|[Wyjątki: `try...with` wyrażenia](the-try-with-expression.md)|W tym artykule opisano konstrukcji języka, który obsługuje obsługi wyjątków.|
|[Wyjątki: `try...finally` wyrażenia](the-try-finally-expression.md)|W tym artykule opisano konstrukcji języka, który pozwala na wykonywanie czyszczenia kodu cofa stosu, gdy jest zgłaszany wyjątek.|
|[Wyjątki: `raise` — funkcja](the-raise-Function.md)|Opisuje sposób throw obiekt wyjątku.|
|[Wyjątki: `failwith` — funkcja](the-failwith-function.md)|Opisuje sposób generowania ogólny wyjątek F #.|
|[Wyjątki: `invalidArg` — funkcja](the-invalidArg-function.md)|Opisuje sposób generowania wyjątek nieprawidłowego argumentu.|
