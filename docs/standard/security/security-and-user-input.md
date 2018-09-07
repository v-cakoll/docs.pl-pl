---
title: Zabezpieczenia i dane użytkownika
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27818d5e1779cd6e10e11830f91a20a3e638639a
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44066519"
---
# <a name="security-and-user-input"></a>Zabezpieczenia i dane użytkownika
Dane użytkownika, który jest dowolny rodzaj danych wejściowych z żądania sieci Web lub adresu URL, dane wejściowe do formantów w aplikacji Microsoft Windows Forms i tak dalej, mogą negatywnie wpłynąć na kod, ponieważ często używane dane bezpośrednio jako parametry, aby wywołać inny kod. Ta sytuacja jest odpowiednikiem złośliwego kodu, wywoływanie kodu z parametrami dziwne, a ten sam ostrożności. Dane wejściowe użytkownika jest faktycznie trudniejsze bezpieczne ponieważ nie ramek stosu śledzenia obecność potencjalnie niezaufanych danych.  
  
 Są wśród błędy subtlest i najtrudniejsze zabezpieczeń, aby znaleźć, ponieważ istnieją w kodzie, który jest pozornie związana z zabezpieczeniami, są one bramy do przekazania złe dane za pośrednictwem do innego kodu. Aby znaleźć te błędy, postępuj zgodnie z dowolnego rodzaju danych wejściowych, Wyobraź sobie, co zakres możliwych wartości mogą być i należy wziąć pod uwagę, czy kod wyświetlania tych danych może obsługiwać wszystkich tych przypadkach. Można naprawić te błędy w zakresie sprawdzania i odrzuca wszelkie wprowadzane, kod nie może obsłużyć.  
  
 Oto kilka istotnych kwestii dotyczących danych użytkownika:  
  
-   Wszystkie dane użytkownika w odpowiedzi serwer działa w kontekście serwera lokacji na komputerze klienckim. Jeśli serwer sieci Web pobiera dane użytkownika i wstawia ją zwróconej stronie internetowej, na przykład może obejmować  **\<script >** tagu i uruchom tak, jakby z serwera.  
  
-   Należy pamiętać, że klient może żądać dowolnego adresu URL.  
  
-   Należy wziąć pod uwagę trudne lub nieprawidłowe ścieżki:  
  
    -   .. \, bardzo długich ścieżek.  
  
    -   Użycie symboli wieloznacznych (*).  
  
    -   Rozszerzenie token (token %).  
  
    -   Otrzymano nieoczekiwany rodzaje ścieżek przy użyciu specjalnego znaczenia.  
  
    -   Alternatywne nazwy strumienia systemu plików, takich jak `filename::$DATA`.  
  
    -   Krótki wersje nazw plików, takich jak `longfi~1` dla `longfilename`.  
  
-   Należy pamiętać, że Eval(userdata) można nic robić.  
  
-   Uważaj, późnego wiązania na nazwę, która zawiera dane użytkownika.  
  
-   Jeśli masz do czynienia z danych w sieci Web, należy wziąć pod uwagę różne rodzaje sekwencje ucieczki, które są dozwolone w tym:  
  
    -   Szesnastkowe sekwencje ucieczki (% nn).  
  
    -   Sekwencje ucieczki Unicode (% nnn).  
  
    -   Przedłużoną anuluje UTF-8 (% nn % nn).  
  
    -   Anuluje Double (% nn staje się mmnn %, gdzie % mm jest znak ucieczki "%").  
  
-   Uważaj, nazw użytkowników, które może mieć więcej niż jeden kanoniczny format. Na przykład często używają obu moja_domena\\*username* formularza lub *username* @mydomain.example.com formularza.  
  
## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
