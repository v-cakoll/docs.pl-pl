---
title: Zdarzenia ETW puli wątków
ms.date: 03/30/2017
helpviewer_keywords:
- thread pool events [.NET Framework]
- ETW, thread pool events (CLR)
ms.assetid: f2a21e3a-3b6c-4433-97f3-47ff16855ecc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: caacee591c4df8389cea241916618f50da56b22b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949165"
---
# <a name="thread-pool-etw-events"></a>Zdarzenia ETW puli wątków
<a name="top"></a> Te zdarzenia zbierać informacji na temat procesu roboczego i wątki We/Wy.  
  
 Istnieją dwie grupy zdarzenia puli wątków:  
  
- [Zdarzenia puli wątków roboczych](#worker), które zawierają informacje o jak aplikacja korzysta z puli wątków i efekt obciążeń na kontroli współbieżności.  
  
- [Zdarzenia puli wątków We/Wy](#io), które zawierają informacje o wątków We/Wy, które są tworzone wycofany, unretired lub przerwana w puli wątków.  
  
<a name="worker"></a>   
## <a name="worker-thread-pool-events"></a>Zdarzenia puli wątków procesów roboczych  
 Zdarzenia te odnoszą się do puli wątków procesów roboczych w środowisku uruchomieniowym i zapewniają powiadomienia o zdarzeniach wątku (na przykład, gdy wątek jest tworzony lub zatrzymana). Wątków roboczych używa adaptacyjnych algorytmów do sterowania współbieżnością, gdy liczba wątków jest obliczana na podstawie zmierzonego przepływności. Zdarzenia puli wątków roboczych może służyć do zrozumienia, jak aplikacja używa puli wątków oraz wpływ, jaki niektóre obciążenia mogą mieć sterowanie współbieżnością.  
  
### <a name="threadpoolworkerthreadstart-and-threadpoolworkerthreadstop"></a>ThreadPoolWorkerThreadStart i ThreadPoolWorkerThreadStop  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom dla tych zdarzeń. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-|-|-|  
|`ThreadPoolWorkerThreadStart`|50|Wątek roboczy jest tworzony.|  
|`ThreadPoolWorkerThreadStop`|51|Wątek roboczy jest zatrzymana.|  
|`ThreadPoolWorkerThreadRetirementStart`|52|Wątek roboczy wycofaniu.|  
|`ThreadPoolWorkerThreadRetirementStop`|53|Wątek roboczy wycofane ponownie staje się aktywny.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ActiveWorkerThreadCount|win: UInt32.|Liczba wątków roboczych dostępnych do przetworzenia pracy, w tym te, które są już przetwarzania.|  
|RetiredWorkerThreadCount|win: UInt32.|Liczba wątków roboczych, które nie są dostępne do przetwarzania pracy, ale trwa odbywające się w rezerwie w przypadku większej liczby wątków jest potrzebna później.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
### <a name="threadpoolworkerthreadadjustment"></a>ThreadPoolWorkerThreadAdjustment  
 Te zdarzenia puli wątków zawierają informacje do zrozumienia i debugowania zachowania algorytm (kontrola współbieżności) iniekcji wątku. Informacje są używane wewnętrznie przez wątków roboczych.  
  
#### <a name="threadpoolworkerthreadadjustmentsample"></a>ThreadPoolWorkerThreadAdjustmentSample  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentSample`|54|Odwołuje się do zbierania informacji dla jednego przykładu; oznacza to pomiar przepływności, zapewniając niektórych współbieżności poziomu, w chwili czasu.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Przepływność|win: Double|Liczba uzupełnienia na jednostkę czasu.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
#### <a name="threadpoolworkerthreadadjustmentadjustment"></a>ThreadPoolWorkerThreadAdjustmentAdjustment  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|55|Rejestruje zmiany w kontrolce, gdy wątek algorytm iniekcji (Wspinanie hill) określa zmiana poziomu współbieżności w miejscu.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|AverageThroughput|win: Double|Średniej przepływności wynoszącej próbkę pomiarów.|  
|NewWorkerThreadCount|win: UInt32.|Nowe liczba aktywnych wątków roboczych.|  
|Przyczyna|win: UInt32.|Przyczyna korekty.<br /><br /> 0x00 - rozgrzewania.<br /><br /> 0x01 — inicjowanie.<br /><br /> 0x02 — losowych przenoszenia.<br /><br /> 0x03 - Wspinanie się przenoszenia.<br /><br /> 0x04 — Zmień punkt.<br /><br /> 0x05 - stabilizowanie.<br /><br /> wartość-0x06 do zablokowania.<br /><br /> 0x07 - wątku upłynął limit czasu.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
#### <a name="threadpoolworkerthreadadjustmentstats"></a>ThreadPoolWorkerThreadAdjustmentStats  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentStats`|56|Zbiera dane w puli wątków.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Czas trwania|win: Double|Ilość czasu w sekundach, w których zebrano te statystyki.|  
|Przepływność|win: Double|Średnia liczba uzupełnienia na sekundę w tym przedziale czasu.|  
|ThreadWave|win: Double|Zarezerwowane do użytku wewnętrznego.|  
|ThroughputWave|win: Double|Zarezerwowane do użytku wewnętrznego.|  
|ThroughputErrorEstimate|win: Double|Zarezerwowane do użytku wewnętrznego.|  
|AverageThroughputErrorEstimate|win: Double|Zarezerwowane do użytku wewnętrznego.|  
|ThroughputRatio|win: Double|Względna poprawę przepływności spowodowane wahania liczby wątków aktywnego procesu roboczego w tym przedziale czasu.|  
|Ufność|win: Double|Miara ważności pola ThroughputRatio.|  
|NewcontrolSetting|win: Double|Liczba aktywnych wątków roboczych, które będzie służyć jako podstawa dla przyszłych wahania liczba aktywnych wątków.|  
|NewThreadWaveMagnitude|win: UInt16.|Wielkość przyszłe zmiany liczba aktywnych wątków.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="io"></a>   
## <a name="io-thread-events"></a>Zdarzenia wejścia/wyjścia wątku  
 Te zdarzenia puli wątków miejsce w przypadku wątków w puli wątków We/Wy (uzupełnianie porty), który jest asynchroniczna.  
  
### <a name="iothreadcreatev1"></a>IOThreadCreate_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-|-|-|  
|`IOThreadCreate_V1`|44|Wątek wiadomości we/wy jest tworzony w puli wątków.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Count|win:UInt64|Liczba wątków We/Wy, łącznie z nowo utworzonego wątku.|  
|NumRetired|win:UInt64|Liczba wątków roboczych wycofane.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
### <a name="iothreadretirev1"></a>IOThreadRetire_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`IOThreadRetire_V1`|46|Operacje We/Wy wątek staje się kandydat wycofania.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Count|win:UInt64|Liczba wątków We/Wy, które pozostało w puli wątków.|  
|NumRetired|win:UInt64|Liczba wycofanych wątków We/Wy.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
### <a name="iothreadunretirev1"></a>IOThreadUnretire_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`IOThreadUnretire_V1`|47|Wątek operacji We/Wy jest unretired ze względu na operacje We/Wy, przychodzący w okresie oczekiwania po wątek staje się kandydat wycofania.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Count|win:UInt64|Liczba operacji We/Wy wątków w puli wątków, w tym tego jednego.|  
|NumRetired|win:UInt64|Liczba wycofanych wątków We/Wy.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
### <a name="iothreadterminate"></a>IOThreadTerminate  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`IOThreadTerminate`|45|Wątek wiadomości we/wy jest tworzony w puli wątków.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Count|win:UInt64|Liczba wątków We/Wy, które pozostało w puli wątków.|  
|NumRetired|win:UInt64|Liczba wycofanych wątków We/Wy.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
