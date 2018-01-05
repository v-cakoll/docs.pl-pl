---
title: "Zdarzenia ETW puli wątków"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread pool events [.NET Framework]
- ETW, thread pool events (CLR)
ms.assetid: f2a21e3a-3b6c-4433-97f3-47ff16855ecc
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a68f35dc5abb653514034cf0d30b62457b933de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="thread-pool-etw-events"></a>Zdarzenia ETW puli wątków
<a name="top"></a>Te zdarzenia zbierać informacje o wątków We/Wy i proces roboczy.  
  
 Istnieją dwie grupy zdarzenia puli wątków:  
  
-   [Zdarzenia puli wątków roboczych](#worker), które zawierają informacje o jak aplikacja używa puli wątków i wpływu obciążeń na formant współbieżności.  
  
-   [Zdarzenia puli wątków We/Wy](#io), które zawierają informacje o wątków We/Wy, które są tworzone wycofane, unretired lub przerwane w puli wątków.  
  
<a name="worker"></a>   
## <a name="worker-thread-pool-events"></a>Zdarzenia puli wątków roboczych  
 Te zdarzenia są powiązane z puli wątków roboczych środowiska uruchomieniowego i podaj powiadomienia o zdarzeniach wątku (na przykład podczas tworzenia wątku lub zatrzymana). Puli wątków roboczych używa nieobsługiwanego algorytmu adaptacyjną do sterowania współbieżnością, gdy liczba wątków jest obliczana na podstawie zmierzona przepływności. Zdarzenia puli wątków roboczych można zrozumieć, jak aplikacja używa puli wątków oraz wpływ, jaki mają niektórych obciążeń na formant współbieżności.  
  
### <a name="threadpoolworkerthreadstart-and-threadpoolworkerthreadstop"></a>ThreadPoolWorkerThreadStart i ThreadPoolWorkerThreadStop  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom dla tych zdarzeń. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`ThreadingKeyword`(0x10000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-|-|-|  
|`ThreadPoolWorkerThreadStart`|50|Wątek roboczy jest tworzony.|  
|`ThreadPoolWorkerThreadStop`|51|Wątek roboczy jest zatrzymana.|  
|`ThreadPoolWorkerThreadRetirementStart`|52|Wątek roboczy wycofaniu.|  
|`ThreadPoolWorkerThreadRetirementStop`|53|Wątek roboczy wycofane ponownie staje się aktywny.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ActiveWorkerThreadCount|Windows: UInt32.|Liczba wątków dostępnych do przetworzenia pracy, w tym te, które są już przetwarzania pracy.|  
|RetiredWorkerThreadCount|Windows: UInt32.|Liczba wątków roboczych, które nie są dostępne do przetwarzania pracy, ale które zostały wstrzymane rezerwy w przypadku większej liczby wątków są potrzebne później.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
### <a name="threadpoolworkerthreadadjustment"></a>ThreadPoolWorkerThreadAdjustment  
 Te zdarzenia puli wątków zawierają informacje do zrozumienia i debugowania zachowanie algorytm wątku iniekcji (formant współbieżności). Informacje jest używana wewnętrznie przez puli wątków roboczych.  
  
#### <a name="threadpoolworkerthreadadjustmentsample"></a>ThreadPoolWorkerThreadAdjustmentSample  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`ThreadingKeyword`(0x10000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentSample`|54|Odwołuje się do zbierania informacji dla jednej próbki; oznacza to miara przepływności z niektórych współbieżności poziomu, natychmiastowe czasu.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Przepływność|Windows: Double|Liczba zakończeń na jednostkę czasu.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
#### <a name="threadpoolworkerthreadadjustmentadjustment"></a>ThreadPoolWorkerThreadAdjustmentAdjustment  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`ThreadingKeyword`(0x10000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|55|Rejestruje zmiany w formancie, wtedy, gdy wątek algorytm iniekcji (typu pod) określa, czy zmiana poziomu współbieżności jest w miejscu.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|AverageThroughput|Windows: Double|Średnia przepustowość próbki pomiarów.|  
|NewWorkerThreadCount|Windows: UInt32.|Nowe liczba aktywnych wątków roboczych.|  
|Przyczyna|Windows: UInt32.|Przyczyna korekty.<br /><br /> 0x00 - rozgrzewania.<br /><br /> 0x01 - inicjowania.<br /><br /> 0x02 — losowe przenoszenia.<br /><br /> 0x03 - typu move.<br /><br /> 0x04 — Zmień punkt.<br /><br /> 0x05 - stabilizacji.<br /><br /> wartość 0x06 - zablokowania.<br /><br /> 0x07 - wątek został przekroczony.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
#### <a name="threadpoolworkerthreadadjustmentstats"></a>ThreadPoolWorkerThreadAdjustmentStats  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`ThreadingKeyword`(0x10000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentStats`|56|Zbiera dane w puli wątków.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Czas trwania|Windows: Double|Ilość czasu w sekundach, w których zebrano te statystyki.|  
|Przepływność|Windows: Double|Średnia liczba zakończeń na sekundę w danym przedziale czasu.|  
|ThreadWave|Windows: Double|Zarezerwowany do użytku wewnętrznego.|  
|ThroughputWave|Windows: Double|Zarezerwowany do użytku wewnętrznego.|  
|ThroughputErrorEstimate|Windows: Double|Zarezerwowany do użytku wewnętrznego.|  
|AverageThroughputErrorEstimate|Windows: Double|Zarezerwowany do użytku wewnętrznego.|  
|ThroughputRatio|Windows: Double|Względne poprawy przepływności spowodowane zmienności liczba wątków roboczych active w danym przedziale czasu.|  
|Zaufania|Windows: Double|Miara ważności pole ThroughputRatio.|  
|NewcontrolSetting|Windows: Double|Liczba aktywnych wątków, które będzie służyć jako podstawowa dla przyszłych zmienności liczba aktywnych wątków.|  
|NewThreadWaveMagnitude|Windows: UInt16|Wielkość przyszłych zmienności liczba aktywnych wątków.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="io"></a>   
## <a name="io-thread-events"></a>Zdarzeń wątków We/Wy  
 Te zdarzenia puli wątków nastąpić wątków w puli wątków We/Wy (porty ukończenia), które jest asynchroniczne.  
  
### <a name="iothreadcreatev1"></a>IOThreadCreate_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`ThreadingKeyword`(0x10000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-|-|-|  
|`IOThreadCreate_V1`|44|W puli wątków jest tworzony wątek we/wy.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Liczba|Windows: UInt64|Liczba wątków We/Wy, łącznie z nowo utworzonego wątku.|  
|NumRetired|Windows: UInt64|Liczba wątków roboczych wycofane.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
### <a name="iothreadretirev1"></a>IOThreadRetire_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`ThreadingKeyword`(0x10000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`IOThreadRetire_V1`|46|Wątek we/wy staje się candidate wycofania.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Liczba|Windows: UInt64|Liczba wątków We/Wy, które pozostało w puli wątków.|  
|NumRetired|Windows: UInt64|Liczba wątków We/Wy wycofane.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
### <a name="iothreadunretirev1"></a>IOThreadUnretire_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`ThreadingKeyword`(0x10000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`IOThreadUnretire_V1`|47|Wątek we/wy jest unretired z powodu operacji We/Wy, przychodzący w okresie oczekiwania po wątek staje się candidate wycofania.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Liczba|Windows: UInt64|Liczba wątków We/Wy w puli wątków, łącznie z tego.|  
|NumRetired|Windows: UInt64|Liczba wątków We/Wy wycofane.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
### <a name="iothreadterminate"></a>IOThreadTerminate  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`ThreadingKeyword`(0x10000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`IOThreadTerminate`|45|W puli wątków jest tworzony wątek we/wy.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Liczba|Windows: UInt64|Liczba wątków We/Wy, które pozostało w puli wątków.|  
|NumRetired|Windows: UInt64|Liczba wątków We/Wy wycofane.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
