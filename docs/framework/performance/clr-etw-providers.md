---
title: Dostawcy CLR ETW
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 639ebe1552fd3950bd77acd7b5730b0d3bdb150f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302624"
---
# <a name="clr-etw-providers"></a>Dostawcy CLR ETW
Środowisko uruchomieniowe języka wspólnego (CLR) ma dwóch dostawców: dostawcę środowiska uruchomieniowego i dostawcę podsumowania.  
  
 Dostawca środowiska uruchomieniowego wywołuje zdarzenia, w zależności od tego, które są włączone słów kluczowych (kategorie zdarzeń). Na przykład, można zbierać zdarzenia ładowania, włączając `LoaderKeyword` — słowo kluczowe.  
  
 Zdarzenia śledzenia dla zdarzeń Windows (ETW) są rejestrowane w pliku z rozszerzeniem .etl, które później mogą być używane po tej operacji przetwarzane w plikach wartości rozdzielanych przecinkami (CSV), zgodnie z potrzebami. Aby uzyskać informacje o sposobie konwertowania pliku etl do pliku CSV, zobacz [kontrolowanie rejestrowania .NET Framework](../../../docs/framework/performance/controlling-logging.md).  
  
## <a name="the-runtime-provider"></a>Dostawca środowiska uruchomieniowego  
 Dostawca środowiska uruchomieniowego jest głównym dostawcą CLR ETW.  
  
 Identyfikator GUID dostawcy środowiska uruchomieniowego CLR to e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.  
  
 Aby zapoznać się z przykładami sposobu rejestrowania i przeglądania zdarzeń CLR ETW przy użyciu powszechnie dostępnych narzędzi, zobacz [kontrolowanie rejestrowania .NET Framework](../../../docs/framework/performance/controlling-logging.md).  
  
 Oprócz używania słów kluczowych, takich jak `LoaderKeyword`, może zajść potrzeba włączenia słów kluczowych do rejestrowania zdarzeń, które mogą być wywoływane zbyt często. `StartEnumerationKeyword` i `EndEnumerationKeyword` słowa kluczowe włączają te zdarzenia i są podsumowane w [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).  
  
## <a name="the-rundown-provider"></a>Dostawca podsumowań  
 Dostawca podsumowań musi być włączona dla niektórych zastosowań specjalnych. Jednak w przypadku większości użytkowników dostawca środowiska uruchomieniowego powinien wystarczyć.  
  
 Identyfikator GUID dostawcy podsumowań CLR jest A669021C-C450-4609-A035-5AF59AF4DF18.  
  
 Zwykle rejestrowanie ETW jest włączane, zanim proces zostanie uruchomiony, a rejestrowanie jest wyłączone, po zakończeniu procesu. Jednakże jeśli rejestrowanie ETW jest włączona, gdy proces jest wykonywany, potrzebne są dodatkowe informacje o procesie. Na przykład dla rozpoznawania symboli należy rejestrować zdarzenia metody dla metod, które zostały już załadowane przed włączeniem rejestrowania.  
  
 `DCStart` i `DCEnd` zdarzenia przechwytują stan procesu, gdy zbieranie danych zostało uruchomione i zatrzymane. (Stan odnosi się do informacji na wysokim poziomie, łącznie z metod, które zostały już just-in-time (JIT) skompilowane i zestawy, które zostały załadowane). Te dwa zdarzenia mogą dostarczyć informacji o tym co już stało się w procesie; na przykład, które metody były skompilowane JIT, i tak dalej.  
  
 Tylko zdarzenia o `DC`, `DCStart`, `DCEnd`, lub `DCInit` w nazwach są wywoływane w obszarze dostawcy podsumowań. Ponadto te zdarzenia są wywoływane tylko w obszarze dostawcy podsumowań.  
  
 Oprócz filtrów słów kluczowych zdarzeń dostawca podsumowań obsługuje także `StartRundownKeyword` i `EndRundownKeyword` słów kluczowych, aby zapewnić ukierunkowane filtrowanie.  
  
### <a name="start-rundown"></a>Początek podsumowania  
 Początek podsumowania jest wyzwalany, gdy jest włączone rejestrowanie dostawcy podsumowań, ze `StartRundownKeyword` — słowo kluczowe. Powoduje to, że `DCStart` zdarzenia i przechwytuje stan systemu. Przed rozpoczęciem wyliczania `DCStartInit` zdarzenie jest wywoływane. Na koniec wyliczenia `DCStartComplete` zdarzenie jest zgłaszane, aby powiadomić kontrolera że zbieranie danych zostało zakończone normalnie.  
  
### <a name="end-rundown"></a>Koniec podsumowania  
 Koniec podsumowania jest wyzwalany, gdy jest włączone rejestrowanie dostawcy podsumowań, ze `EndRundownKeyword` — słowo kluczowe. Koniec podsumowania zatrzymuje profilowanie procesu, którego wykonywanie będzie kontynuowane. `DCEnd` Zdarzenia Przechwytywanie stanu systemu po zatrzymaniu profilowania.  
  
 Przed rozpoczęciem wyliczania `DCEndInit` zdarzenie jest wywoływane. Na koniec wyliczenia `DCEndComplete` zdarzenie jest zgłaszane, aby powiadomić konsumenta, że zbieranie danych zostało zakończone normalnie. Początek podsumowania i koniec podsumowania są głównie używane do rozpoznawania symboli zarządzanych. Początek podsumowania może dostarczyć informacji o zakresie adresów dla metod, które zostały już skompilowane JIT przed uruchomieniem sesji profilowania. Koniec podsumowania może dostarczyć informacji o zakresie adresów dla wszystkich metod, które zostały skompilowane JIT gdy profilowanie ma być wyłączona.  
  
 Koniec podsumowania nie odbywa się automatycznie po zatrzymaniu sesji profilowania. Zamiast tego narzędzia, które dąży do wykonania rozpoznania symboli zarządzanych musi jawnie wywołać sesję dostawcy podsumowań CLR z `EndRundownKeyword` — słowo kluczowe włączone, przed zatrzymaniem profilowania.  
  
 Chociaż Początek podsumowania i koniec podsumowania zapewniają informacje dotyczące zakresów adresów metody dla rozpoznawania symboli zarządzanych, zaleca się używanie `EndRundownKeyword` — słowo kluczowe (które dostarcza `DCEnd` zdarzenia) zamiast `StartRundownKeyword` — słowo kluczowe (który dostarcza `DCStart` zdarzenia). Za pomocą `StartRundownKeyword` powoduje wywołanie podsumowania podczas sesji profilowania, co może zakłócać profilowany scenariusz.  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a>Zbieranie danych ETW za pomocą środowiska uruchomieniowego i podsumowania dostawców  
 Poniższy przykład pokazuje sposób użycia dostawcy podsumowania CLR w sposób umożliwiający rozpoznawanie symboli procesów zarządzanych z minimalnym wpływem, niezależnie od tego, czy procesy rozpoczęły lub zakończyły się wewnątrz lub poza oknem profilowania.  
  
1. Włącz rejestrowanie ETW za pomocą dostawcy środowiska uruchomieniowego CLR:  
  
    ```  
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     Dziennik zostanie zapisany do pliku clr1.etl.  
  
2. Aby zatrzymać profilowanie, podczas gdy proces kontynuuje wykonywanie, Rozpocznij dostawcę podsumowań do przechwytywania `DCEnd` zdarzenia:  
  
    ```  
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     Umożliwia to kolekcja `DCEnd` zdarzenia, które można uruchomić sesji podsumowania. Należy poczekać 30 do 60 sekund, aby wszystkie zdarzenia mają być zbierane. Dziennik zostanie zapisany do pliku clr1.et2.  
  
3. Wyłącz wszystkie profilowania ETW:  
  
    ```  
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4. Scal profile Aby utworzyć jeden plik dziennika:  
  
    ```  
    xperf -merge clr1.etl clr2.etl merged.etl  
    ```  
  
     Plik merged.etl zawiera zdarzenia środowiska uruchomieniowego i sesje dostawcy podsumowań.  
  
 Narzędzie może wykonać kroki 2 i 3 (uruchamianie sesji podsumowania, a następnie zakończenie profilowania) zamiast natychmiastowego wyłączenia profilowania, gdy użytkownik żądania zatrzymania profilowania. To narzędzie może również wykonać krok 4.  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia ETW w środowisku CLR](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
