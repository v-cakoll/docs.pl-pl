---
title: Obsługa wyjątków
description: Naucz się podstaw obsługi wyjątków w F# i łącza do obsługi wyrażeń i funkcji wyjątków.
ms.date: 05/16/2016
ms.openlocfilehash: 0f4e57bfd643cba3dab5281df484ebb6162cb4b7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645487"
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
|[Wyjątki: `try...with` Wyrażenia](the-try-with-expression.md)|W tym artykule opisano konstrukcją języka pierwszej klasy, który obsługuje obsługi wyjątków.|
|[Wyjątki: `try...finally` Wyrażenia](the-try-finally-expression.md)|W tym artykule opisano konstrukcją języka pierwszej klasy, która pozwala na wykonywanie czyszczenia kodu rozwija stos, gdy wyjątek jest zgłaszany.|
|[Wyjątki: `raise` — funkcja](the-raise-Function.md)|W tym artykule opisano, jak zostać zgłoszony obiekt wyjątku.|
|[Wyjątki: `failwith` — Funkcja](the-failwith-function.md)|W tym artykule opisano sposób generowania ogólnego F# wyjątku.|
|[Wyjątki: `invalidArg` — Funkcja](the-invalidArg-function.md)|W tym artykule opisano, jak wygenerować wyjątek nieprawidłowego argumentu.|
