---
title: Dostawcy CLR ETW
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
ms.openlocfilehash: 33ef7491c2bffeda4ef737ed8f826cdfbfbb119d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400079"
---
# <a name="clr-etw-providers"></a>Dostawcy CLR ETW
Środowisko uruchomieniowe języka wspólnego (CLR) ma dwóch dostawców: dostawcę środowiska wykonawczego i dostawcę wybiegu.  
  
 Dostawca środowiska wykonawczego wywołuje zdarzenia, w zależności od tego, które słowa kluczowe (kategorie zdarzeń) są włączone. Na przykład można zbierać zdarzenia modułu `LoaderKeyword` ładującego, włączając słowo kluczowe.  
  
 Zdarzenia śledzenia zdarzeń dla systemu Windows (ETW) są rejestrowane w pliku z rozszerzeniem .etl, które można później przetworzyć w plikach wartości oddzielonych przecinkami (csv). Aby uzyskać informacje dotyczące sposobu konwertowania pliku .etl na plik csv, zobacz [Kontrolowanie rejestrowania programu .NET Framework .](controlling-logging.md)  
  
## <a name="the-runtime-provider"></a>Dostawca środowiska wykonawczego  
 Dostawca środowiska wykonawczego jest głównym dostawcą CLR ETW.  
  
 Identyfikator GUID dostawcy środowiska wykonawczego CLR to e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.  
  
 Aby zapoznać się z przykładami sposobu rejestrowania i wyświetlania zdarzeń CLR ETW przy użyciu powszechnie dostępnych narzędzi, zobacz [Kontrolowanie rejestrowania programu .NET Framework .](controlling-logging.md)  
  
 Oprócz używania słów kluczowych, takich jak `LoaderKeyword`, może być wymagane włączenie słów kluczowych dla zdarzeń rejestrowania, które mogą być wywoływane zbyt często. I `StartEnumerationKeyword` `EndEnumerationKeyword` słowa kluczowe włączyć te zdarzenia i są podsumowane w [CLR ETW Słowa kluczowe i poziomy](clr-etw-keywords-and-levels.md).  
  
## <a name="the-rundown-provider"></a>Dostawca wybiegiem  
 Dostawca wybiegiem musi być włączony dla niektórych zastosowań specjalnego przeznaczenia. Jednak dla większości użytkowników dostawca środowiska wykonawczego powinien wystarczyć.  
  
 Identyfikator GUID dostawcy wybiegiem CLR to A669021C-C450-4609-A035-5AF59AF4DF18.  
  
 Zwykle rejestrowanie ETW jest włączone przed uruchomieniem procesu, a rejestrowanie jest wyłączone po zakończeniu procesu. Jeśli jednak rejestrowanie ETW jest włączone podczas wykonywania procesu, potrzebne są dodatkowe informacje o procesie. Na przykład dla rozpoznawania symbolu należy rejestrować zdarzenia metody dla metod, które zostały już załadowane przed włączeniem rejestrowania.  
  
 Zdarzenia `DCStart` `DCEnd` i zdarzenia przechwytują stan procesu podczas pobierania danych został uruchomiony i zatrzymany. (Stan odnosi się do informacji na wysokim poziomie, w tym metod, które zostały już just-in-time (JIT) skompilowane i zestawów, które zostały załadowane.) Te dwa zdarzenia mogą dostarczyć informacji o tym, co już się wydarzyło w procesie; na przykład, które metody były JIT- skompilowany, i tak dalej.  
  
 Tylko zdarzenia `DC`z `DCStart` `DCEnd`, `DCInit` , , lub w ich nazwach są wywoływane pod dostawcą rundown. Ponadto te zdarzenia są wywoływane tylko w ramach dostawcy rundown.  
  
 Oprócz filtrów słów kluczowych zdarzeń dostawca wybiegiem `StartRundownKeyword` obsługuje `EndRundownKeyword` również słowa kluczowe i słowa kluczowe, aby zapewnić ukierunkowane filtrowanie.  
  
### <a name="start-rundown"></a>Rozpocznij przegląd  
 Rundown start jest wyzwalany, gdy rejestrowanie w obszarze `StartRundownKeyword` dostawcy wybiegiem jest włączona za pomocą słowa kluczowego. Powoduje to, że `DCStart` zdarzenie ma zostać podniesione i przechwytuje stan systemu. Przed rozpoczęciem wyliczenia `DCStartInit` zdarzenie jest wywoływane. Na końcu wyliczenia `DCStartComplete` zdarzenie jest wywoływane, aby powiadomić kontrolera, że zbieranie danych zakończone normalnie.  
  
### <a name="end-rundown"></a>Koniec schyłk  
 Zakończenie rundown jest wyzwalany, gdy rejestrowanie w ramach `EndRundownKeyword` dostawcy rundown jest włączona za pomocą słowa kluczowego. Koniec spływu zatrzymuje profilowanie w procesie, który jest kontynuowany. Zdarzenia `DCEnd` przechwytują stan systemu po zatrzymaniu profilowania.  
  
 Przed rozpoczęciem wyliczenia `DCEndInit` zdarzenie jest wywoływane. Na końcu wyliczenia `DCEndComplete` zdarzenie jest wywoływane, aby powiadomić konsumenta, że zbieranie danych zakończone normalnie. Rundown start i end rundown są używane głównie do rozpoznawania symboli zarządzanych. Rozpocznij rundown może dostarczyć informacji o zakresie adresów dla metod, które zostały już Skompilowane JIT przed rozpoczęciem sesji profilowania. End rundown może dostarczyć informacji o zakresie adresów dla wszystkich metod, które zostały skompilowane przez JIT, gdy profilowanie ma zostać wyłączone.  
  
 Zakończenie zakończenia nie odbywa się automatycznie po zatrzymaniu sesji profilowania. Zamiast tego narzędzie, które stara się wykonać rozpoznawanie symboli zarządzanych musi jawnie `EndRundownKeyword` wywołać sesję dostawcy rundown CLR z włączoną słowem kluczowym, tuż przed zatrzymaniem profilowania.  
  
 Mimo że uruchomienie lub zakończenie rundown może dostarczyć informacji o zakresie adresów metody `EndRundownKeyword` dla rozpoznawania `DCEnd` symboli zarządzanych, `StartRundownKeyword` zaleca się `DCStart` użycie słowa kluczowego (które dostarcza zdarzenia) zamiast słowa kluczowego (które dostarcza zdarzenia). Za `StartRundownKeyword` pomocą powoduje, że rundown się podczas sesji profilowania, które mogą zakłócać profilowane scenariusz.  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a>Zbieranie danych ETW przy użyciu dostawców środowiska uruchomieniowego i wybiegiem  
 W poniższym przykładzie pokazano, jak używać dostawcy wybiegiem CLR w sposób, który umożliwia rozpoznawanie symboli zarządzanych procesów o minimalnym wpływie, niezależnie od tego, czy procesy rozpoczynają się, czy kończą wewnątrz, czy na zewnątrz okna profilowanego.  
  
1. Włącz rejestrowanie ETW przy użyciu dostawcy środowiska wykonawczego CLR:  
  
    ```console
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl
    ```  
  
     Dziennik zostanie zapisany w pliku clr1.etl.  
  
2. Aby zatrzymać profilowanie, podczas gdy proces jest kontynuowany, `DCEnd` uruchom dostawcę wybiegu, aby przechwycić zdarzenia:  
  
    ```console
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl
    ```  
  
     Dzięki temu kolekcja `DCEnd` zdarzeń, aby rozpocząć sesję schyłka. Może być konieczne odczekanie od 30 do 60 sekund na zebranie wszystkich zdarzeń. Dziennik zostanie zapisany w pliku clr1.et2.  
  
3. Wyłącz wszystkie profilowania ETW:  
  
    ```console
    xperf -stop clrRundown
    xperf -stop clr  
    ```  
  
4. Scal profile, aby utworzyć jeden plik dziennika:  
  
    ```console
    xperf -merge clr1.etl clr2.etl merged.etl  
    ```  
  
     Plik merged.etl będzie zawierał zdarzenia ze środowiska wykonawczego i sesji dostawcy wybiegu.  
  
 Narzędzie może wykonać kroki 2 i 3 (rozpoczęcie sesji wybiegiem, a następnie zakończenie profilowania) zamiast natychmiast wyłączyć profilowanie, gdy użytkownik zażąda zatrzymania profilowania. Narzędzie może również wykonać krok 4.  
  
## <a name="see-also"></a>Zobacz też

- [Zdarzenia ETW w środowisku CLR](etw-events-in-the-common-language-runtime.md)
