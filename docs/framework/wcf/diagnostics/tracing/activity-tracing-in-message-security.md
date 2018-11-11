---
title: Śledzenie działania w ramach zabezpieczeń komunikatów
ms.date: 03/30/2017
ms.assetid: 68862534-3b2e-4270-b097-8121b12a2c97
ms.openlocfilehash: c3bd36598fd903dc016959149e563174624d084b
ms.sourcegitcommit: 296183dbe35077b5c5e5e74d5fbe7f399bc507ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "50982844"
---
# <a name="activity-tracing-in-message-security"></a>Śledzenie działania w ramach zabezpieczeń komunikatów
W tym temacie opisano śledzenie aktywności dla przetwarzania zabezpieczeń, co się stanie w następujące trzy etapy.  
  
-   Negocjowanie/SCT programu exchange. Może to nastąpić transportu (przez dane binarne exchange) lub warstwy komunikat (za pośrednictwem wymiany komunikatów protokołu SOAP).  
  
-   Komunikat operacji szyfrowania i odszyfrowywania, za pomocą uwierzytelniania i weryfikacji podpisu. Ślady są wyświetlane w działaniu, otoczenia, zazwyczaj "Action procesu".  
  
-   Autoryzacja i weryfikacji. Można to zrobić, lokalnie lub gdy komunikacja między punktami końcowymi.  
  
## <a name="negotiationsct-exchange"></a>Negocjowanie/SCT programu exchange  
 W fazie exchange negocjowania/SCT dwa typy działań są tworzone na komputerze klienckim: "Ustaw się zabezpieczyć sesja" i "Zamknij bezpiecznej sesji." "Konfigurowanie Secure sesji" obejmuje śladów RST/RSTR/SCT wymianę komunikatów, gdy "Zamknij sesję Secure" zawiera dane śledzenia dla komunikatu Anuluj.  
  
 Na serwerze każdego żądanie/nietypizowana odpowiedź dla RST/RSTR/SCT pojawia się w swoje własne działania. Jeśli `propagateActivity` = `true` na serwer i klienta, mają taki sam identyfikator działania na serwerze i pojawiają się razem w "Ustawienia zabezpieczenia sesji" podczas wyświetlania za pośrednictwem przeglądarki danych śledzenia usługi.  
  
 Ten model śledzenia działania jest prawidłowy dla użytkownika nazwy i hasła, uwierzytelnianie oparte na certyfikatach oraz uwierzytelnianie NTLM.  
  
 W poniższej tabeli wymieniono działania i ślady negocjacje i SCT programu exchange.  
  
||Czas, kiedy się stanie, negocjowania/SCT programu exchange|Kategoria Activities|ślady|  
|-|-------------------------------------------------|----------------|------------|  
|Zabezpieczenia transportu<br /><br /> (HTTPS, SSL)|Na pierwszy komunikat odebrany.|Ślady są emitowane w działaniu otoczenia.|-Ślady Exchange<br />-Należy zabezpieczyć kanał nawiązane<br />-Udostępnić klucze tajne uzyskany.|  
|Warstwa zabezpieczoną wiadomość<br /><br /> (WSHTTP)|Na pierwszy komunikat odebrany.|Na komputerze klienckim:<br /><br /> -"Instalatora bezpiecznej sesji" poza "Action procesu" ten pierwszy komunikat dla każdego żądanie/nietypizowana odpowiedź dla RST/RSTR/SCT.<br />-"Bezpiecznej sesji Zamknij" w wymianie ANULOWANIA, poza "działanie Zamknij serwer Proxy". To działanie może się zdarzyć z niektórych innych otoczenia działania, w zależności od tego, po zamknięciu bezpiecznej sesji.<br /><br /> Na serwerze:<br /><br /> — Jedno działanie "Proces Action" dla każdego żądanie/nietypizowana odpowiedź dla RST/SCT/anulować na serwerze. Jeśli `propagateActivity` = `true`RST/RSTR/SCT działań są scalane z "Ustaw się sesja zabezpieczeń" i Anuluj jest scalany z "Zamknij" działanie od klienta.<br /><br /> Istnieją dwa etapy "Ustaw się zabezpieczyć sesji":<br /><br /> 1.  Negocjowanie uwierzytelniania. Jest to opcjonalne, jeśli klient ma już prawidłowe poświadczenia. Ta faza może odbywać się przez bezpiecznym transportem, albo przez wymianę komunikatów. W tym ostatnim przypadku może się zdarzyć wymiany RST/RSTR 1 lub 2. Dla tych wymian dane śledzenia są emitowane w nowe działania żądanie/nietypizowana odpowiedź wcześniej zaprojektowana.<br />2.  Zabezpiecz ustanawiania sesji (SCT), w którym jeden exchange RST/RSTR się stanie, w tym miejscu. Ma takie same działania otoczenia, zgodnie z wcześniejszym opisem.|-Ślady Exchange<br />-Należy zabezpieczyć kanał nawiązane<br />-Udostępnić klucze tajne uzyskany.|  
  
> [!NOTE]
>  W trybie mieszanym zabezpieczeń negocjacji uwierzytelnianie odbywa się w binarnym wymiany, ale SCT odbywa się w wymianie wiadomości. W trybie transportu czystego negocjacji odbywa się tylko w przypadku transportu bez dodatkowych działań.  
  
## <a name="message-encryption-and-decryption"></a>Komunikat, szyfrowania i odszyfrowywania  
 Poniższa tabela zawiera listę działań i danych śledzenia dla operacji szyfrowania i odszyfrowywania wiadomości, a także uwierzytelniania sygnatury.  
  
||Zabezpieczenia transportu<br /><br /> (HTTPS, SSL) i zabezpieczanie warstwy wiadomości<br /><br /> (WSHTTP)|  
|-|---------------------------------------------------------------------------------|  
|Czas, kiedy również podpisu uwierzytelnianie odbywa się komunikatu szyfrowania i odszyfrowywania|Na odebranego komunikatu|  
|Kategoria Activities|Ślady są emitowane w działaniu ProcessAction na kliencie i serwerze.|  
|ślady|-sendSecurityHeader (nadawcy):<br />— Logowanie komunikat<br />-Szyfrowania danych na żądanie<br />-receiveSecurityHeader (odbiorca):<br />— Weryfikowanie podpisu<br />-Odszyfrowywania danych odpowiedzi<br />— Uwierzytelnianie|  
  
> [!NOTE]
>  W trybie transportu czystego szyfrowania i odszyfrowywania wiadomości odbywa się tylko w przypadku transportu bez dodatkowych działań.  
  
## <a name="authorization-and-verification"></a>Autoryzacja i weryfikacja  
 W poniższej tabeli wymieniono działania i ślady na potrzeby autoryzacji.  
  
||Czas, kiedy się dzieje autoryzacji|Kategoria Activities|ślady|  
|-|-------------------------------------|----------------|------------|  
|Lokalne (ustawienie domyślne)|Po wiadomości jest odszyfrowywany na serwerze|Ślady są emitowane w działaniu ProcessAction na serwerze.|Użytkownik autoryzowany.|  
|Zdalne|Po wiadomości jest odszyfrowywany na serwerze|Ślady są emitowane w nowe działanie wywoływane przez działanie ProcessAction.|Użytkownik autoryzowany.|
