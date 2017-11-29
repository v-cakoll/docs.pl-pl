---
title: Dostawcy CLR ETW
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 18353939108d58eb2aaffee97e059e4430b25e3a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="clr-etw-providers"></a>Dostawcy CLR ETW
Środowisko uruchomieniowe języka wspólnego (CLR) ma dwóch dostawców: stert dostawcy i dostawcy środowiska wykonawczego.  
  
 Dostawcy środowiska uruchomieniowego informuje o zdarzeniach, w zależności od tego, które są włączone słowa kluczowe (kategorie zdarzeń). Na przykład może zbierać zdarzenia modułu ładującego, włączając `LoaderKeyword` — słowo kluczowe.  
  
 Zdarzenia śledzenia zdarzeń systemu Windows (ETW) są rejestrowane w pliku, który ma rozszerzenie etl, które później mogą być używane po przetwarzane w plikach plik wartości rozdzielanych przecinkami (.csv) zgodnie z potrzebami. Aby uzyskać informacje na temat konwertowania pliku etl do pliku CSV, zobacz [kontrolowanie rejestrowania Framework .NET](../../../docs/framework/performance/controlling-logging.md).  
  
## <a name="the-runtime-provider"></a>Dostawcy środowiska wykonawczego  
 Dostawca środowiska uruchomieniowego jest głównym dostawcy CLR ETW.  
  
 Dostawca środowiska uruchomieniowego CLR identyfikator GUID jest e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.  
  
 Przykłady tego, jak rejestrować i przeglądać zdarzenia CLR ETW za pomocą powszechnie dostępnych narzędzi, zobacz [kontrolowanie rejestrowania Framework .NET](../../../docs/framework/performance/controlling-logging.md).  
  
 Oprócz przy użyciu słów kluczowych, takich jak `LoaderKeyword`, trzeba włączyć słowa kluczowe do rejestrowania zdarzeń, które może być uruchamiany zbyt często. `StartEnumerationKeyword` i `EndEnumerationKeyword` słów kluczowych, Włącz te zdarzenia i podsumowano w [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).  
  
## <a name="the-rundown-provider"></a>Dostawca stert  
 Stert dostawcy musi być włączona w niektórych specjalnych. Jednak w przypadku większości użytkowników dostawcy środowiska uruchomieniowego powinny wystarczyć.  
  
 Dostawca stert CLR identyfikator GUID jest A669021C-C450-4609-A035-5AF59AF4DF18.  
  
 Zwykle ETW rejestrowanie jest włączone, przed uruchamia proces i rejestrowanie jest wyłączone, po zamknięciu procesu. Jednak jeśli rejestrowanie funkcji ETW jest włączona, gdy proces jest wykonywany, dodatkowe potrzebne są informacje o procesie. Na przykład do rozpoznawania symboli należy rejestrować zdarzenia metod dla metod, które zostały już załadowane przed włączone rejestrowanie.  
  
 `DCStart` i `DCEnd` zdarzenia przechwytywania stanu procesu, gdy funkcja zbierania danych został uruchamiania i zatrzymywania. (Stan odwołuje się do informacji na wysokim poziomie, łącznie z metod, które zostały już just-in-time (JIT) skompilowany i zestawy, które zostały załadowane). Te dwa zdarzenia zawiera informacje o co została już wykonana w procesie; na przykład które metody zostały JIT-skompilowany i tak dalej.  
  
 Tylko zdarzenia o `DC`, `DCStart`, `DCEnd`, lub `DCInit` w nazwach pojawienia się w obszarze stert dostawcy. Ponadto te zdarzenia są generowane tylko w przypadku zamknięcia dostawcy.  
  
 Oprócz filtrów słów kluczowych zdarzeń, obsługuje również dostawcę stert `StartRundownKeyword` i `EndRundownKeyword` słów kluczowych w celu zapewnienia docelowe filtrowania.  
  
### <a name="start-rundown"></a>Uruchom uwalniania  
 Uwalniania rozpoczęcia jest wyzwalane, gdy włączono rejestrowanie w obszarze dostawcy stert z `StartRundownKeyword` — słowo kluczowe. Powoduje to `DCStart` się zdarzenia i przechwytywanie stanu systemu. Przed rozpoczęciem wyliczania `DCStartInit` zdarzenia. Na koniec wyliczenia `DCStartComplete` zdarzenia powiadomiono kontrolerem zbierania danych zakończone normalnie.  
  
### <a name="end-rundown"></a>Uwalnianie zakończenia  
 Uwalniania zakończenia jest wyzwalane, gdy włączono rejestrowanie w obszarze dostawcy stert z `EndRundownKeyword` — słowo kluczowe. Końcowy stert zatrzymuje profilowanie na proces, która kontynuuje wykonywanie. `DCEnd` Zdarzenia Przechwytywanie stanu systemu, gdy profilowania jest zatrzymana.  
  
 Przed rozpoczęciem wyliczania `DCEndInit` zdarzenia. Na koniec wyliczenia `DCEndComplete` zdarzenie jest wywoływane w celu powiadomienia klienta, która zbierania danych zwykle przerwana. Uruchom stert i uwalniania celu są używane przede wszystkim do rozpoznawania zarządzanego symbolu. Start uwalniania może dostarczyć informacji zakres adresów dla metod, które już zostały skompilowane JIT zanim sesja profilowania został uruchomiony. Uwalnianie zakończenia może dostarczyć informacji zakres adresów dla wszystkich metod, które zostały skompilowane JIT podczas profilowania ma zostać wyłączone.  
  
 Uwalnianie end nie odbywa się automatycznie po zatrzymaniu sesji profilowania. Zamiast tego narzędzia, który chce rozpoznawać zarządzanego symbolu ma jawnie wywołać sesji stert dostawcy CLR z `EndRundownKeyword` — słowo kluczowe włączone tuż przed profilowania jest zatrzymana.  
  
 Mimo że uwalniania rozpoczęcia lub zakończenia uwalniania może dostarczyć metody adres zakresu informacji rozpoznanie zarządzanego symbolu, zaleca się używanie `EndRundownKeyword` — słowo kluczowe (które dostaw `DCEnd` zdarzeń) zamiast `StartRundownKeyword` — słowo kluczowe (który dostarcza `DCStart` zdarzeń). Przy użyciu `StartRundownKeyword` powoduje, że uwalniania do mają miejsce podczas sesji profilowania, która może przeszkadzać PROFILOWANEGO scenariusza.  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a>Zbieranie danych funkcji ETW za pomocą środowiska uruchomieniowego i dostawców stert  
 W poniższym przykładzie pokazano sposób użycia dostawcy stert CLR w sposób umożliwiający rozpoznawanie symboli procesów zarządzanych przy minimalnym wpływie, niezależnie od tego, czy procesy początku ani na końcu wewnątrz lub na zewnątrz PROFILOWANEGO okna.  
  
1.  Włącz rejestrowanie funkcji ETW przy użyciu dostawcy środowiska uruchomieniowego CLR:  
  
    ```  
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     Dziennika są zapisywane do pliku clr1.etl.  
  
2.  Aby zatrzymać profilowanie podczas procesu kontynuuje wykonywanie, uruchom stert dostawcy, aby przechwycić `DCEnd` zdarzenia:  
  
    ```  
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     Umożliwia to kolekcja `DCEnd` zdarzeń, aby rozpocząć sesję zamknięcia. Może być konieczne odczekanie 30 do 60 sekund dla wszystkich zdarzeń mają być zbierane. Dziennika są zapisywane do pliku clr1.et2.  
  
3.  Wyłącz wszystkie profilowania ETW:  
  
    ```  
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4.  Scalanie profili można utworzyć jeden plik dziennika:  
  
    ```  
    xperf -merge -d clr1.etl clr2.etl merged.etl  
    ```  
  
     Plik merged.etl będzie zawierał zdarzenia środowiska uruchomieniowego i sesje stert dostawcy.  
  
 To narzędzie można wykonać kroki 2 i 3 (uruchamianie zamknięcia sesji i następnie Kończenie profilowania) zamiast natychmiast wyłączenie profilowania, gdy użytkownik żądań profilowanie, aby zostać zatrzymane. Narzędzia można również wykonać krok 4.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia ETW w środowisko uruchomieniowe języka wspólnego](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
