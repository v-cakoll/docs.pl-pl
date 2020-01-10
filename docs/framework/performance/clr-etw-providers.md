---
title: Dostawcy CLR ETW
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
ms.openlocfilehash: dbdd4ad862ae300c330dc56a82fcd65b866855b6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716179"
---
# <a name="clr-etw-providers"></a>Dostawcy CLR ETW
Środowisko uruchomieniowe języka wspólnego (CLR) ma dwóch dostawców: dostawcę środowiska uruchomieniowego i dostawcę.  
  
 Dostawca środowiska uruchomieniowego zgłasza zdarzenia, w zależności od tego, które słowa kluczowe (kategorie zdarzeń) są włączone. Na przykład można zbierać zdarzenia modułu ładującego, włączając słowo kluczowe `LoaderKeyword`.  
  
 Zdarzenia śledzenia zdarzeń systemu Windows (ETW) są rejestrowane w pliku z rozszerzeniem. etl, które może później być przetworzone w plikach z wartościami rozdzielanymi przecinkami (CSV), zgodnie z wymaganiami. Informacje o sposobach konwertowania pliku. etl do pliku CSV znajdują się w temacie [sterowanie rejestrowaniem .NET Framework](controlling-logging.md).  
  
## <a name="the-runtime-provider"></a>Dostawca środowiska uruchomieniowego  
 Dostawca środowiska uruchomieniowego jest głównym dostawcą funkcji ETW CLR.  
  
 Identyfikator GUID dostawcy środowiska uruchomieniowego CLR to e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.  
  
 Aby zapoznać się z przykładami rejestrowania i wyświetlania zdarzeń ETW CLR przy użyciu powszechnie dostępnych narzędzi, zobacz [kontrolowanie rejestrowania .NET Framework](controlling-logging.md).  
  
 Oprócz używania słów kluczowych, takich jak `LoaderKeyword`, może być konieczne włączenie słów kluczowych do rejestrowania zdarzeń, które mogą być zgłaszane zbyt często. `StartEnumerationKeyword` i `EndEnumerationKeyword` słowa kluczowe umożliwiają te zdarzenia i są podsumowywane w [słowach kluczowych i poziomach CLR ETW](clr-etw-keywords-and-levels.md).  
  
## <a name="the-rundown-provider"></a>Dostawca uwalniania  
 Dostawca uwalniania musi być włączony do określonych zastosowań specjalnych. Jednak w przypadku większości użytkowników należy mieć wystarczające dla nich dostawca środowiska uruchomieniowego.  
  
 Identyfikator GUID dostawcy uwalniania CLR to A669021C-C450-4609-A035-5AF59AF4DF18.  
  
 Zwykle rejestrowanie ETW jest włączane przed uruchomieniem procesu, a rejestrowanie jest wyłączone po zakończeniu procesu. Jeśli jednak rejestrowanie funkcji ETW jest włączone podczas wykonywania procesu, należy uzyskać dodatkowe informacje o tym procesie. Na przykład w przypadku rozpoznawania symboli trzeba rejestrować zdarzenia metody dla metod, które zostały już załadowane przed włączeniem rejestrowania.  
  
 Zdarzenia `DCStart` i `DCEnd` przechwytują stan procesu, gdy zbieranie danych zostało rozpoczęte i zatrzymane. (Stan dotyczy informacji na wysokim poziomie, w tym metod, które zostały skompilowane wcześniej (JIT) i zestawów, które zostały załadowane.) Te dwa zdarzenia mogą dostarczyć informacji na temat tego, co się już stało w procesie; na przykład, które metody zostały skompilowane JIT i tak dalej.  
  
 Tylko zdarzenia z `DC`, `DCStart`, `DCEnd`lub `DCInit` w ich nazwach są zgłaszane w ramach dostawcy uwalniania. Ponadto te zdarzenia są wywoływane tylko w ramach dostawcy uwalniania.  
  
 Oprócz filtrów słów kluczowych zdarzenia dostawca uwalniania obsługuje również słowa kluczowe `StartRundownKeyword` i `EndRundownKeyword` w celu zapewnienia filtrowania.  
  
### <a name="start-rundown"></a>Rozpocznij uwalnianie  
 Rozpocznij uwalnianie jest wyzwalane, gdy rejestrowanie w ramach dostawcy uwalniania jest włączone za pomocą słowa kluczowego `StartRundownKeyword`. Powoduje to wygenerowanie zdarzenia `DCStart` i przechwycenie stanu systemu. Przed rozpoczęciem wyliczania zostanie zgłoszone zdarzenie `DCStartInit`. Na końcu wyliczenia zostanie zgłoszone zdarzenie `DCStartComplete`, aby powiadomić kontroler, że zbieranie danych zostało zakończone normalnie.  
  
### <a name="end-rundown"></a>Zakończ uwalnianie  
 Zakończenie uwalniania jest wyzwalane, gdy rejestrowanie w ramach dostawcy uwalniania jest włączone za pomocą słowa kluczowego `EndRundownKeyword`. Zakończenie końca spowoduje zatrzymanie profilowania dla procesu, który jest nadal wykonywany. Zdarzenia `DCEnd` przechwytują stan systemu, gdy profilowanie zostało zatrzymane.  
  
 Przed rozpoczęciem wyliczania zostanie zgłoszone zdarzenie `DCEndInit`. Na końcu wyliczenia zostanie zgłoszone zdarzenie `DCEndComplete`, aby powiadomić odbiorcę o tym, że zbieranie danych zostało zakończone normalnie. Początkowy i końcowy uwalnianie są używane głównie do rozpoznawania symboli zarządzanych. Rozpocznij uwalnianie może dostarczyć informacji o zakresie adresów dla metod, które zostały już skompilowane JIT przed uruchomieniem sesji profilowania. Końcowa kompilacja może dostarczyć informacji o zakresie adresów dla wszystkich metod, które zostały skompilowane JIT, gdy profilowanie ma zostać wyłączone.  
  
 Zakończenie uwalniania nie odbywa się automatycznie, gdy sesja profilowania zostanie zatrzymana. Zamiast tego narzędzie, które poszukuje funkcji rozpoznawania symboli zarządzanych, musi jawnie wywołać sesję dostawcy uwalniania środowiska CLR z włączonym słowem kluczowym `EndRundownKeyword`, tuż przed zatrzymaniem profilowania.  
  
 Chociaż parametr początkowy lub końcowy, może dostarczyć informacji o zakresie adresów metody dla rozpoznawania symboli zarządzanych, zalecamy użycie słowa kluczowego `EndRundownKeyword` (które dostarcza `DCEnd` zdarzeń) zamiast słowa kluczowego `StartRundownKeyword` (które dostarcza zdarzenia `DCStart`). Użycie `StartRundownKeyword` powoduje, że uwalnianie odbywa się podczas sesji profilowania, co może zakłócać profilowany scenariusz.  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a>Zbieranie danych funkcji ETW przy użyciu dostawców środowiska uruchomieniowego i uwalniania  
 W poniższym przykładzie pokazano, jak używać dostawcy uwalniania środowiska CLR w taki sposób, aby umożliwiać Rozpoznawanie symboli zarządzanych procesów z minimalnym wpływem, niezależnie od tego, czy procesy są uruchamiane, czy kończyć się w oknie profilowanym.  
  
1. Włącz rejestrowanie funkcji ETW przy użyciu dostawcy środowiska uruchomieniowego CLR:  
  
    ```console
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     Dziennik zostanie zapisany w pliku pliku clr1. etl.  
  
2. Aby zatrzymać profilowanie, gdy proces jest kontynuowany, należy uruchomić dostawcę, aby przechwycić `DCEnd` zdarzenia:  
  
    ```console
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     Umożliwia to zbieranie zdarzeń `DCEnd`, aby rozpocząć sesję sesji. W przypadku wszystkich zdarzeń, które mają być zbierane, może być konieczne odczekanie od 30 do 60 sekund. Dziennik zostanie zapisany w pliku pliku clr1. ET2.  
  
3. Wyłącz wszystkie profilowania ETW:  
  
    ```console
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4. Scal profile, aby utworzyć jeden plik dziennika:  
  
    ```console
    xperf -merge clr1.etl clr2.etl merged.etl  
    ```  
  
     Scalony plik. etl będzie zawierać zdarzenia z sesji dostawcy środowiska uruchomieniowego i.  
  
 Za pomocą narzędzia można wykonać kroki 2 i 3 (rozpoczęcie sesji uwalniania, a następnie zakończenie profilowania) zamiast natychmiastowego wyłączenia profilowania, gdy użytkownik zażąda zatrzymania profilowania. Narzędzie może również wykonać krok 4.  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia ETW w środowisku CLR](etw-events-in-the-common-language-runtime.md)
