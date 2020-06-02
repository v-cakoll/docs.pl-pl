---
title: Zabezpieczenia i dane użytkownika
description: Kod może przekazać dane wprowadzone przez użytkownika jako parametry do innego kodu, co może mieć wpływ na zabezpieczenia. Sprawdzanie zakresu pozwala odrzucać problematyczne dane wejściowe.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: 995af30385790a88718193e7abad1db7bc4b56c3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84275948"
---
# <a name="security-and-user-input"></a>Zabezpieczenia i dane użytkownika

Dane użytkownika, czyli dowolny rodzaj danych wejściowych (dane z żądania sieci Web lub adresu URL, dane wejściowe do kontrolek aplikacji Microsoft Windows Forms itd.), mogą mieć negatywny wpływ na kod, ponieważ często dane są używane bezpośrednio jako parametry wywołania innego kodu. Ta sytuacja jest analogiczna do złośliwego kodu wywołującego kod przy użyciu dziwnych parametrów i należy podjąć te same środki ostrożności. Dane wejściowe użytkownika są naprawdę trudniejsze do zagwarantowania, ponieważ nie ma ramki stosu do śledzenia obecności potencjalnie niezaufanych danych.

Znajdują się one wśród delikatnych i najtrudniejszych usterek związanych z bezpieczeństwem, które mogą znajdować się w kodzie, który wydaje się niezwiązany z zabezpieczeniami, są bramą do przekazywania nieprawidłowych danych do innego kodu. Aby wyszukać te błędy, postępuj zgodnie z dowolnym rodzajem danych wejściowych, Wyobraź sobie, jakie może być zakres możliwych wartości, i rozważ, czy kod, który widzi te dane, może obsłużyć wszystkie te przypadki. Można naprawić te usterki poprzez sprawdzenie zakresu i odrzucenie wszelkich danych wejściowych, których kod nie może obsłużyć.

Poniżej wymieniono istotne zagadnienia dotyczące danych użytkownika:

- Wszystkie dane użytkownika w odpowiedzi serwera są uruchamiane w kontekście lokacji serwera na kliencie programu. Jeśli serwer sieci Web pobiera dane użytkownika i wstawia je do zwróconej strony sieci Web, może na przykład zawierać **\<script>** tag i działać jako Jeśli z serwera.

- Należy pamiętać, że klient może zażądać dowolnego adresu URL.

- Weź pod uwagę lewę lub nieprawidłowe ścieżki:

  - .. \, bardzo długie ścieżki.

  - Użycie znaków wieloznacznych (*).

  - Rozszerzenie tokenu (% token%).

  - Nietypowe formy ścieżek o specjalnym znaczeniu.

  - Alternatywne nazwy strumieni systemu plików, takie jak `filename::$DATA` .

  - Krótkie wersje plików, `longfi~1` na przykład `longfilename` .

- Pamiętaj, że w ramach oceny (UserData) można wykonać dowolną czynność.

- Uważaj na późne wiązanie do nazwy zawierającej pewne dane użytkownika.

- W przypadku pracy z danymi w sieci Web należy wziąć pod uwagę różne formy ucieczki, takie jak:

  - Szesnastkowe znaki ucieczki (% nn).

  - Ucieczki Unicode (% NNN).

  - Nadlongowe sekwencje UTF-8 (% nn% nn).

  - Podwójne ucieczki (% nn staną się% mmnn, gdzie% mm jest ucieczką dla "%").

- Należy ostrożnie wymusić nazwy użytkowników, które mogą mieć więcej niż jeden format kanoniczny. Można na przykład użyć \\ formularza*username* lub formularza *username* @mydomain.example.com .

## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](secure-coding-guidelines.md)
