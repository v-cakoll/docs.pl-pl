---
title: Obsługa wyjątków (F#)
description: 'Poznaj podstawy obsługi wyjątków w F # i łącza do obsługi wyrażeń i funkcji wyjątków.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 37b33f9387956ee462ff4977dd4ba34a82e89ec6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
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
