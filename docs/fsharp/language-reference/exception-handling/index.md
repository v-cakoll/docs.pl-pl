---
title: "Obsługa wyjątków (F#)"
description: "Poznaj podstawy obsługi wyjątków w F # i łącza do obsługi wyrażeń i funkcji wyjątków."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ad475c4a-d94e-47d9-b27b-3ff000b65f8e
ms.openlocfilehash: b61af66e0a70fdf9b86df37418c0284957d1f99e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
