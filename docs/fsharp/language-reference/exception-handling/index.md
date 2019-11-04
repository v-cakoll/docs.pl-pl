---
title: Obsługa wyjątków
description: Poznaj podstawy obsługi wyjątków w F# i Znajdź linki do wyrażeń obsługi wyjątków i funkcji.
ms.date: 05/16/2016
ms.openlocfilehash: e34a65dd7da9d706153254ac28e729de0745e4d0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423060"
---
# <a name="exception-handling"></a>Obsługa wyjątków

Ta sekcja zawiera informacje dotyczące obsługi wyjątków w F# języku.

## <a name="exception-handling-basics"></a>Podstawowe informacje o obsłudze wyjątków

Obsługa wyjątków jest standardowym sposobem obsługi warunków błędów w .NET Framework. Z tego względu każdy język .NET musi obsługiwać ten mechanizm F#, w tym. *Wyjątek* to obiekt, który hermetyzuje informacje o błędzie. W przypadku wystąpienia błędów są zgłaszane wyjątki i regularne wykonywanie. Zamiast tego, środowisko uruchomieniowe wyszukuje odpowiednią procedurę obsługi dla wyjątku. Wyszukiwanie rozpoczyna się w bieżącej funkcji i przechodzi przez stosy za pomocą warstw obiektów wywołujących do momentu znalezienia zgodnej procedury obsługi. Następnie jest wykonywany program obsługi.

Ponadto, ponieważ stos jest oddzielony, środowisko uruchomieniowe wykonuje dowolny kod w blokach `finally`, aby zagwarantować, że obiekty są czyszczone prawidłowo podczas procesu odwinięcia.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----|-----------|
|[Typy wyjątków](exception-types.md)|Opisuje sposób deklarowania typu wyjątku.|
|[Wyjątki: wyrażenie `try...with`](the-try-with-expression.md)|Opisuje konstrukcję języka, która obsługuje obsługę wyjątków.|
|[Wyjątki: wyrażenie `try...finally`](the-try-finally-expression.md)|Opisuje konstrukcję języka, która umożliwia wykonywanie kodu czyszczącego jako rozwinięcia stosu, gdy zostanie zgłoszony wyjątek.|
|[Wyjątki: funkcja `raise`](the-raise-Function.md)|Opisuje, jak zgłosić obiekt wyjątku.|
|[Wyjątki: funkcja `failwith`](the-failwith-function.md)|Opisuje sposób generowania wyjątku ogólnego F# .|
|[Wyjątki: funkcja `invalidArg`](the-invalidArg-function.md)|Opisuje sposób generowania wyjątku nieprawidłowego argumentu.|
