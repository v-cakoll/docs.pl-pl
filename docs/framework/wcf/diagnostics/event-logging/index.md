---
title: Rejestrowanie zdarzeń w architekturze WCF
ms.date: 03/30/2017
helpviewer_keywords:
- event logging [WCF]
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
ms.openlocfilehash: 0c74b93be026007a5593372c938cf73e08fafb15
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797796"
---
# <a name="event-logging-in-wcf"></a>Rejestrowanie zdarzeń w architekturze WCF
Windows Communication Foundation (WCF) śledzi wewnętrzne zdarzenia w dzienniku zdarzeń systemu Windows.  
  
## <a name="viewing-event-logs"></a>Przeglądanie dzienników zdarzeń  
 Rejestrowanie zdarzeń jest domyślnie włączane automatycznie i nie ma mechanizmu wyłączenia go. Zdarzenia zarejestrowane przez funkcję WCF można wyświetlić przy użyciu Podgląd zdarzeń. Aby uruchomić to narzędzie, kliknij przycisk **Start**, kliknij przycisk **Panel sterowania**, kliknij dwukrotnie przycisk **Narzędzia administracyjne**, a następnie kliknij dwukrotnie przycisk **Podgląd zdarzeń**.  
  
### <a name="application-event-log"></a>Dziennik zdarzeń aplikacji  
 **Dziennik zdarzeń aplikacji** zawiera większość zdarzeń wygenerowanych przez program WCF. Większość wpisów wskazuje, że nie można uruchomić konkretnej funkcji dla aplikacji. Przykłady obejmują:  
  
- Rejestrowanie/śledzenie komunikatów: Usługa WCF zapisuje zdarzenie w dzienniku zdarzeń, gdy śledzenie i rejestrowanie komunikatów nie powiedzie się. Jednak nie wszystkie błędy śledzenia wyzwalają zdarzenie. Aby zapobiec całkowitemu wypełnieniu dziennika zdarzeń z błędami śledzenia, funkcja WCF implementuje okres niedostępności 10 minut dla takiego zdarzenia. Oznacza to, że jeśli program WCF zapisuje błąd śledzenia w dzienniku zdarzeń, nie wykona tego ponownie przez co najmniej 10 minut.  
  
- Udostępniony odbiornik: Usługa udostępniania portów TCP WCF rejestruje zdarzenie w przypadku niepowodzenia uruchomienia.  
  
- CardSpace Rejestruje zdarzenia, gdy uruchomienie usługi nie powiedzie się.  
  
- Zdarzenia krytyczne i błędy, takie jak błędy uruchamiania lub awarie  
  
- Włączono rejestrowanie komunikatów: Rejestruje zdarzenia po włączeniu rejestrowania komunikatów. Jest to powiadomienie administratora, że informacje specyficzne dla aplikacji mogą być rejestrowane w nagłówkach i treściach komunikatów.  
  
- Zdarzenie jest rejestrowane, `enableLoggingKnownPII` gdy atrybut `machineSettings` w elemencie `machine.config` pliku jest ustawiony. Ten atrybut określa, czy dowolna aplikacja działająca na komputerze może rejestrować znane dane osobowe.  
  
- `web.config` `enableLoggingKnownPII` `machine.config` Jeśli atrybut w `app.config` pliku lub jest ustawiony na `true` dla określonej aplikacji w `machineSettings` celu włączenia rejestrowania przez dane osobowe, ale atrybut w elemencie pliku jest ustawiony `logKnownPii` `false`to zdarzenie jest rejestrowane. Ponadto, jeśli oba `logKnownPii` i `enableLoggingKnownPII` są ustawione na `true`, a zdarzenie jest rejestrowane. Więcej informacji o tych ustawieniach konfiguracji znajduje się w sekcji Zabezpieczenia w temacie [Konfigurowanie rejestrowania komunikatów](../configuring-message-logging.md) .  
  
### <a name="security-event-log"></a>Dziennik zdarzeń zabezpieczeń  
 **Dziennik zdarzeń zabezpieczeń** zawiera zdarzenia inspekcji zabezpieczeń, które są rejestrowane przez program WCF.  
  
### <a name="system-event-log"></a>Systemowy dziennik zdarzeń  
 Usługa WCF nie rejestruje żadnych informacji w **dzienniku zdarzeń systemu**.  
  
### <a name="event-log-entries"></a>Wpisy dziennika zdarzeń  
 **Źródłem** zdarzenia jest nazwa zestawu, który generuje wpis dziennika.  
  
 Typ wpisu dziennika zdarzeń służy do wskazywania ważności zdarzenia. Każde zdarzenie musi być typu pojedynczego, który ma być wyświetlany podczas raportowania zdarzenia. Podgląd zdarzeń używa tego typu, aby określić ikonę, która ma być wyświetlana w widoku listy dziennika. Dla innego typu zdarzenia wpisu dziennika zdarzeń, zobacz <xref:System.Diagnostics.EventLogEntryType>.  
  
 Po kliknięciu przycisku "więcej informacji" podczas wyświetlania zdarzenia w Podgląd zdarzeń Podgląd zdarzeń może wysłać informacje przez Internet. Aby uzyskać więcej informacji, zobacz Pomoc Podgląd zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- [Administracja i diagnostyka](../index.md)
- [Informacje ogólne o zdarzeniach](events-general-reference.md)
