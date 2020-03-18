---
title: Zabezpieczenia i dane użytkownika
description: Kod może przekazywać dane wprowadzone przez użytkownika jako parametry do innego kodu, co może mieć wpływ na bezpieczeństwo. Można wykonać sprawdzanie zakresu, aby odrzucić problematyczne dane wejściowe.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: fa9f8d4708e928c51e446d8369c9b4556fc6fb77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186104"
---
# <a name="security-and-user-input"></a>Zabezpieczenia i dane użytkownika

Dane użytkownika, który jest wszelkiego rodzaju danych wejściowych (dane z żądania sieci Web lub adresu URL, dane wejściowe do formantów aplikacji Microsoft Windows Forms i tak dalej), może niekorzystnie wpływać na kod, ponieważ często te dane są używane bezpośrednio jako parametry do wywołania innego kodu. Ta sytuacja jest analogiczna do złośliwego kodu wywołującego kod z dziwnymi parametrami i należy podjąć te same środki ostrożności. Dane wejściowe użytkownika jest rzeczywiście trudniejsze do bezpiecznego, ponieważ nie ma ramki stosu do śledzenia obecności potencjalnie niezaufanych danych.

Są to jedne z najsubtelniejszych i najtrudniejszych błędów zabezpieczeń do znalezienia, ponieważ chociaż mogą istnieć w kodzie, który pozornie nie ma związku z zabezpieczeniami, są bramą do przekazywania złych danych do innego kodu. Aby wyszukać te błędy, należy wykonać wszelkiego rodzaju danych wejściowych, wyobrazić sobie, jaki zakres możliwych wartości może być i zastanów się, czy kod widząc te dane może obsłużyć wszystkie te przypadki. Można naprawić te błędy poprzez sprawdzanie zakresu i odrzucanie wszelkich danych wejściowych kod nie może obsłużyć.

Oto kilka ważnych kwestii związanych z danymi użytkownika:

- Wszystkie dane użytkownika w odpowiedzi serwera są uruchamiane w kontekście lokacji serwera na kliencie. Jeśli serwer sieci Web pobiera dane użytkownika i wstawia je do zwróconej strony sieci Web, może na przykład zawierać ** \<skrypt>** tagu i uruchamiać tak, jakby z serwera.

- Pamiętaj, że klient może zażądać dowolnego adresu URL.

- Rozważ trudne lub nieprawidłowe ścieżki:

  - .. \ , bardzo długie ścieżki.

  - Użycie symboli wieloznacznych (*).

  - Rozszerzanie tokenu (%token%).

  - Dziwne formy ścieżek o szczególnym znaczeniu.

  - Alternatywne nazwy strumienia `filename::$DATA`systemu plików, takie jak .

  - Krótkie wersje nazw `longfi~1` plików, takie jak dla `longfilename`.

- Pamiętaj, że Eval (userdata) może zrobić wszystko.

- Uważaj na późne powiązanie z nazwą, która zawiera pewne dane użytkownika.

- Jeśli masz do czynienia z danymi sieci Web, należy wziąć pod uwagę różne formy ucieczki, które są dopuszczalne, w tym:

  - Szesnastkowa ucieczka (%nn).

  - Unicode ucieka (%nnn).

  - Overlong UTF-8 ucieka (%nn%nn).

  - Podwójne ucieczki (%nn staje się %mmnn, gdzie %mm jest ucieczką dla '%').

- Uważaj na nazwy użytkowników, które mogą mieć więcej niż jeden format kanoniczny. Na przykład często można użyć formularza\\*nazwa użytkownika* MYDOMAIN lub formularza nazwy@mydomain.example.com *użytkownika.*

## <a name="see-also"></a>Zobacz też

- [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
