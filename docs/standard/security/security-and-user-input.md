---
title: "Zabezpieczenia i dane użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 157e20a80f0a76e157fad091bec6bfe635a9ccb8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="security-and-user-input"></a>Zabezpieczenia i dane użytkownika
Dane użytkownika, który jest dowolny rodzaj danych wejściowych (dane z żądania sieci Web lub adres URL, w danych wejściowych do formantów w aplikacji formularzy systemu Windows firmy Microsoft, i tak dalej), może negatywnie wpłynąć na kodu, ponieważ często używane dane bezpośrednio jako parametry, aby wywołać inny kod. Taka sytuacja jest odpowiednikiem złośliwego kodu wywoływanie kodu z parametrami dziwne, a sam ostrożności. Dane wejściowe użytkownika jest rzeczywiście trudniej upewnij bezpieczne, ponieważ nie istnieje żadne ramki stosu śledzenie obecności potencjalnie niezaufanych danych.  
  
 Są to między usterki subtlest i najtrudniejsze zabezpieczeń, aby dowiedzieć się, ponieważ istnieją w kodzie, który jest pozornie związana z zabezpieczeniami, są one bramy do przekazania złe dane za pośrednictwem do innego kodu. Aby znaleźć te błędy, wykonaj dowolny rodzaj danych wejściowych, Wyobraź sobie co zakresu możliwych wartości może być i należy wziąć pod uwagę, czy kod wyświetlać te dane można obsługiwać wszystkich tych przypadkach. Możesz rozwiązać te usterki w zakresie kontroli i odrzuca wszystkie wejściowy kod nie może obsłużyć.  
  
 Oto kilka istotnych kwestii dotyczących danych użytkownika:  
  
-   Wszystkie dane użytkownika w odpowiedzi serwer działa w kontekście serwera lokacji na kliencie. Jeśli serwer sieci Web pobiera dane użytkownika i wstawia go do zwróconej stronie sieci Web, na przykład może zawierać  **\<skryptu >** tagu i uruchom tak, jakby z serwera.  
  
-   Należy pamiętać, że klient może żądać dowolny adres URL.  
  
-   Należy wziąć pod uwagę ścieżek trudnych lub jest nieprawidłowy:  
  
    -   .. \, bardzo długie ścieżki.  
  
    -   Użycie symboli wieloznacznych (*).  
  
    -   Rozszerzenia token (token %).  
  
    -   Formularze dziwne ścieżek o specjalnym znaczeniu.  
  
    -   Alternatywne nazwy strumienia systemu plików, takich jak `filename::$DATA`.  
  
    -   Krótka wersji nazw plików, takich jak `longfi~1` dla `longfilename`.  
  
-   Należy pamiętać, że Eval(userdata) mogą wykonywać żadnych czynności.  
  
-   Uważaj, późnego wiązania na nazwę, która zawiera niektóre dane użytkowników.  
  
-   Jeśli mamy do czynienia z danych w sieci Web, należy wziąć pod uwagę różne rodzaje specjalne, które są dopuszczalne, w tym:  
  
    -   Wyprowadza szesnastkowym (% nn).  
  
    -   Specjalne Unicode (% nnn).  
  
    -   Przedłużoną specjalne UTF-8 (% nn % nn).  
  
    -   Wyprowadza Double (% nn staje się mmnn %, gdzie % mm jest ucieczki "%").  
  
-   Uważaj, nazw użytkowników, które mogą mieć więcej niż jeden format kanoniczny. Na przykład często służą albo moja_domena\\*username* formularza lub *username* @mydomain.example.com formularza.  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
