---
title: Rejestrowanie zdarzeń w architekturze WCF
ms.date: 03/30/2017
helpviewer_keywords:
- event logging [WCF]
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
ms.openlocfilehash: c4f73480208fbf900bb8742eb6d7b2e2c0e6a4ff
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486627"
---
# <a name="event-logging-in-wcf"></a>Rejestrowanie zdarzeń w architekturze WCF
Windows Communication Foundation (WCF) śledzi wewnętrznego zdarzenia w dzienniku zdarzeń Windows.  
  
## <a name="viewing-event-logs"></a>Wyświetlanie dzienników zdarzeń  
 Rejestrowanie zdarzeń jest domyślnie automatycznie i nie ma mechanizmu go wyłączyć. Można przeglądać zdarzenia rejestrowane przez architekturę WCF, za pomocą Podglądu zdarzeń. Aby uruchomić to narzędzie, kliknij **Start**, kliknij przycisk **Panelu sterowania**, kliknij dwukrotnie **narzędzia administracyjne**, a następnie kliknij dwukrotnie **Podgląd zdarzeń**.  
  
### <a name="application-event-log"></a>Dziennik zdarzeń aplikacji  
 **Dziennik zdarzeń aplikacji** zawiera większość zdarzeń generowanych przez usługi WCF. Większość pozycji wskazują, że dana funkcja nie można uruchomić aplikacji. Przykłady obejmują:  
  
- Rejestrowanie/śledzenia komunikatów: WCF zapisuje zdarzenie w dzienniku zdarzeń, gdy śledzenie i rejestrowanie komunikatów nie powiodło się. Jednak nie każdy błąd śledzenia wyzwala zdarzenie. Aby zapobiec całkowicie wypełnione śledzenia błędów w dzienniku zdarzeń, usługi WCF implementuje okres niedostępności 10 minut na takie zdarzenie. Oznacza to, że jeśli WCF zapisuje błąd śledzenia do dziennika zdarzeń, nie będzie więc ponownie co najmniej 10 minut.  
  
- Odbiornik udostępnione: Usługa Udostępnianie portów TCP WCF rejestruje zdarzenie, gdy nie została uruchomiona.  
  
- CardSpace: Dzienniki zdarzeń, gdy nie można uruchomić usługi.  
  
- Krytyczne i błędy zdarzenia, takie jak błędy podczas uruchamiania lub awarie  
  
- Rejestrowanie komunikatów jest włączona: Dzienniki zdarzeń, gdy jest włączone rejestrowanie komunikatów. Jest to Powiadom administratora, że poufne informacje specyficzne dla aplikacji może zostać zarejestrowane w wiadomości, nagłówki i treść.  
  
- Zdarzenie jest rejestrowane po `enableLoggingKnownPII` atrybutu w `machineSettings` elementu `machine.config` plik jest ustawiony. Ten atrybut określa, w przypadku dowolnej aplikacji na maszynie jest uprawniony do logowania znanych identyfikowalne dane osobowe (PII).  
  
- Jeśli `logKnownPii` atrybut albo `app.config` lub `web.config` pliku jest ustawiona na `true` dla określonej aplikacji włączyć rejestrowanie dane osobowe, ale `enableLoggingKnownPII` atrybutu w `machineSettings` elementu `machine.config` plik jest ustawiony Aby `false`, zdarzenie jest rejestrowane. Ponadto, jeśli obie `logKnownPii` i `enableLoggingKnownPII` są ustawione na `true`, a zdarzenie jest rejestrowane. Aby uzyskać więcej informacji na temat tych ustawień konfiguracji, zobacz sekcję zabezpieczeń [Konfigurowanie rejestrowania komunikatów](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) tematu.  
  
### <a name="security-event-log"></a>Dziennik zdarzeń zabezpieczeń  
 **Dziennika zdarzeń zabezpieczeń** zawiera zdarzenia inspekcji zabezpieczeń, które są rejestrowane przez architekturę WCF.  
  
### <a name="system-event-log"></a>Dziennik zdarzeń systemu  
 Usługi WCF nie logują się nic **dziennik zdarzeń systemu**.  
  
### <a name="event-log-entries"></a>Wpisy dziennika zdarzeń  
 **Źródła** zdarzenia to nazwa zestawu, który generuje wpis dziennika.  
  
 Typ wpisu dziennika zdarzeń służy do wskazania ważność danego zdarzenia. Każde zdarzenie musi być jednego typu, który aplikacja wskazuje, kiedy zgłasza zdarzenie. Podgląd zdarzeń używa tego typu, aby określić, jaką ikonę wyświetlić w widoku listy dziennika. Dla typu zdarzeń wpis dziennika zdarzeń, zobacz <xref:System.Diagnostics.EventLogEntryType>.  
  
 Po kliknięciu przycisku "informacje dodatkowe" podczas wyświetlania zdarzeń w Podglądzie zdarzeń, w Podglądzie zdarzeń może wysłać informacje przez Internet. Aby uzyskać więcej informacji zobacz Pomoc Podglądu zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Informacje ogólne o zdarzeniach](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
