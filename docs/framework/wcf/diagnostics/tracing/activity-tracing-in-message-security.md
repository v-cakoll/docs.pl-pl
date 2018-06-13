---
title: Śledzenie działania w ramach zabezpieczeń komunikatów
ms.date: 03/30/2017
ms.assetid: 68862534-3b2e-4270-b097-8121b12a2c97
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 31882dfff746aa8e0e45698f70b0f19ae413d66a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474860"
---
# <a name="activity-tracing-in-message-security"></a>Śledzenie działania w ramach zabezpieczeń komunikatów
W tym temacie opisano działania śledzenia dla przetwarzania zabezpieczeń, które odbywa się w następujących trzech etapów.  
  
-   Negocjowanie/SCT programu exchange. Może to nastąpić w transportu (przez dane binarne wymiany) lub warstwy komunikatu (poprzez wymianę wiadomości SOAP).  
  
-   Komunikat szyfrowania i odszyfrowywania, uwierzytelniania i weryfikacji podpisu. Ślady są wyświetlane w działaniu otoczenia, zazwyczaj "Akcja procesu".  
  
-   Autoryzacja i weryfikacji. Przyczyną może być lokalnie lub podczas komunikacji między punktami końcowymi.  
  
## <a name="negotiationsct-exchange"></a>Negocjowanie/SCT programu exchange  
 W fazie negocjacji/SCT programu exchange na klienta są tworzone dwa typy działań: "Ustaw zapasowej bezpieczną sesję" i "Close bezpiecznej sesji." "Skonfiguruj bezpieczną sesję" obejmuje śladów do wymiany wiadomości SCT-RST/odpowiedź RSTR, podczas "Close bezpieczną sesję" zawiera dane śledzenia dla komunikatu Anuluj.  
  
 Na serwerze każdego żądania/odpowiedzi dla RST/odpowiedź RSTR/SCT pojawia się w jego własnej działania. Jeśli `propagateActivity` = `true` na serwera i klienta, mają ten sam identyfikator działania na serwerze, a występować razem w "Instalator bezpieczną sesję" podczas przeglądania za pomocą przeglądarki danych śledzenia usługi.  
  
 Ten model śledzenie działania jest prawidłowy dla użytkownika nazwa/hasło, uwierzytelnianie oparte na certyfikatach oraz uwierzytelnianie NTLM.  
  
 W poniższej tabeli wymieniono działań i ślady negocjacji i SCT programu exchange.  
  
||Czas, kiedy sytuacji negocjacji/SCT exchange|Kategoria Activities|Dane śledzenia|  
|-|-------------------------------------------------|----------------|------------|  
|Zabezpieczenia transportu<br /><br /> (HTTPS, SSL)|Na pierwszy komunikat.|Ślady są emitowane w działaniu otoczenia.|— Exchange śledzenie<br />-Bezpieczny kanał ustanowić<br />-Udostępnianie kluczy tajnych uzyskany.|  
|Warstwa zabezpieczoną wiadomość<br /><br /> (WSHTTP)|Na pierwszy komunikat.|Na komputerze klienckim:<br /><br /> -"Ustawienia bezpiecznej sesji" poza "Działania procesu" ten pierwszy komunikat dla każdego żądania/odpowiedzi dla SCT-RST/odpowiedź RSTR.<br />-"Zamknij bezpiecznej sesji" dla programu exchange Anuluj poza "działanie Zamknij serwera Proxy." To działanie może się zdarzyć, niektóre inne otoczenia działania poza, w zależności od zamknięcia bezpiecznej sesji.<br /><br /> Na serwerze:<br /><br /> -Jedno działanie "Akcja procesu" dla każdego żądania/odpowiedzi dla Anuluj-RST/SCT na serwerze. Jeśli `propagateActivity` = `true`SCT-RST/odpowiedź RSTR działania są scalane z "Ustaw się sesja zabezpieczeń" i Anuluj jest scalany z działania "Zamknij", z klienta.<br /><br /> Istnieją dwa etapy dla "Ustaw zapasowej bezpieczną sesję":<br /><br /> 1.  Negocjowanie uwierzytelniania. Jest to opcjonalne, jeśli klient ma już odpowiednie poświadczenia. Ta faza może odbywać się za pośrednictwem bezpiecznego transportu, lub wymiany komunikatów. W tym ostatnim przypadku może się zdarzyć wymiany RST/odpowiedź RSTR 1 lub 2. Dla tych wymian dane śledzenia są emitowane w nowych działań żądania/odpowiedzi wcześniej zaprojektowane.<br />2.  Zabezpiecz ustanawiania sesji (SCT), w którym exchange RST/odpowiedź RSTR co się stanie w tym miejscu. Ma takie same działania otoczenia, jak opisano wcześniej.|— Exchange śledzenie<br />-Bezpieczny kanał ustanowić<br />-Udostępnianie kluczy tajnych uzyskany.|  
  
> [!NOTE]
>  W trybie mieszanym zabezpieczeń negocjacji uwierzytelnianie odbywa się wymianę binarne, ale SCT odbywa się w wymianie wiadomości. W trybie transportu czysty negocjacji odbywa się tylko w transporcie bez dodatkowych działań.  
  
## <a name="message-encryption-and-decryption"></a>Komunikat szyfrowania i odszyfrowywania  
 W poniższej tabeli wymieniono działań i danych śledzenia komunikatów szyfrowania i odszyfrowywania, a także uwierzytelniania podpisu.  
  
||Zabezpieczenia transportu<br /><br /> (HTTPS, SSL) i bezpieczne warstwy komunikatów<br /><br /> (WSHTTP)|  
|-|---------------------------------------------------------------------------------|  
|Godzinę komunikatów szyfrowania i odszyfrowywania, a także podpisu uwierzytelnianie odbywa się|Na odebrany komunikat|  
|Kategoria Activities|Ślady są emitowane w działaniu ProcessAction na kliencie i serwerze.|  
|Dane śledzenia|-sendSecurityHeader (nadawcy):<br />— Znak komunikat<br />-Szyfrowania danych żądania<br />-receiveSecurityHeader (odbiorca):<br />-Zweryfikować podpisu<br />-Odszyfrować dane odpowiedzi<br />— Uwierzytelnianie|  
  
> [!NOTE]
>  W trybie transportu czystego szyfrowania i odszyfrowywania wiadomości odbywa się tylko w transporcie bez dodatkowych działań.  
  
## <a name="authorization-and-verification"></a>Autoryzacja i weryfikacji  
 W poniższej tabeli wymieniono działań i śladów do autoryzacji.  
  
||Czas, kiedy sytuacji autoryzacji|Kategoria Activities|Dane śledzenia|  
|-|-------------------------------------|----------------|------------|  
|Lokalne (ustawienie domyślne)|Po wiadomość jest odszyfrowywany na serwerze|Ślady są emitowane w działaniu ProcessAction na serwerze.|Użytkownik jest autoryzowany.|  
|Zdalne|Po wiadomość jest odszyfrowywany na serwerze|Ślady są emitowane w wywołanym przez działanie ProcessAction nowe działanie.|Użytkownik jest autoryzowany.|
