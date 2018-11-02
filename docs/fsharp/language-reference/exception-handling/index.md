---
title: Obsługa wyjątków (F#)
description: Naucz się podstaw obsługi wyjątków w F# i łącza do obsługi wyrażeń i funkcji wyjątków.
ms.date: 05/16/2016
ms.openlocfilehash: fc89feb0d21bc823cb105e435413f8309cd6174c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "33564329"
---
# <a name="exception-handling"></a>Obsługa wyjątków

Ta sekcja zawiera informacje o pomocy technicznej w obsłudze wyjątków F# języka.


## <a name="exception-handling-basics"></a>Podstawy obsługi wyjątków
Obsługa wyjątków jest standardowym sposobem obsługi błędów w programie .NET Framework. W związku z tym, dowolnego języka platformy .NET musi obsługiwać ten mechanizm tym F#. *Wyjątek* jest obiektem, który hermetyzuje informacje o błędzie. Jeśli wystąpią błędy, wyjątki są zatrzymuje podniesione i regularnego wykonywania. Zamiast tego środowisko uruchomieniowe wyszukuje odpowiedni program obsługi wyjątku. Wyszukiwanie rozpoczyna się bieżącą funkcję i przechodzi w górę stosu za pośrednictwem warstw obiektów wywołujących, aż do znalezienia pasującej klauzuli obsługi. Następnie program obsługi jest wykonywana.

Ponadto, ponieważ stos jest odwijany, środowisko uruchomieniowe wykonuje każdy kod `finally` bloków, aby zagwarantować, że obiekty są czyszczone poprawnie podczas procesu odwijania.


## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----|-----------|
|[Typy wyjątków](exception-types.md)|W tym artykule opisano, jak zadeklarować typ wyjątku.|
|[Wyjątki: `try...with` wyrażenia](the-try-with-expression.md)|W tym artykule opisano konstrukcją języka pierwszej klasy, który obsługuje obsługi wyjątków.|
|[Wyjątki: `try...finally` wyrażenia](the-try-finally-expression.md)|W tym artykule opisano konstrukcją języka pierwszej klasy, która pozwala na wykonywanie czyszczenia kodu rozwija stos, gdy wyjątek jest zgłaszany.|
|[Wyjątki: `raise` — funkcja](the-raise-Function.md)|W tym artykule opisano, jak zostać zgłoszony obiekt wyjątku.|
|[Wyjątki: `failwith` — funkcja](the-failwith-function.md)|W tym artykule opisano sposób generowania ogólnego F# wyjątku.|
|[Wyjątki: `invalidArg` — funkcja](the-invalidArg-function.md)|W tym artykule opisano, jak wygenerować wyjątek nieprawidłowego argumentu.|
