---
title: Rejestrowanie zdarzeń w architekturze WCF
ms.date: 03/30/2017
helpviewer_keywords:
- event logging [WCF]
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
ms.openlocfilehash: ea0e6f3dc66bf40d631077c0dce20ea46f3a6688
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="event-logging-in-wcf"></a>Rejestrowanie zdarzeń w architekturze WCF
Windows Communication Foundation (WCF) śledzi wewnętrznego zdarzenia w dzienniku zdarzeń systemu Windows.  
  
## <a name="viewing-event-logs"></a>Wyświetlanie dzienników zdarzeń  
 Rejestrowanie zdarzeń jest automatycznie włączone domyślnie i nie istnieje mechanizm je wyłączyć. Zdarzenia zarejestrowane przez usługę WCF można wyświetlić za pomocą Podglądu zdarzeń. Aby uruchomić to narzędzie, kliknij przycisk **Start**, kliknij przycisk **Panelu sterowania**, kliknij dwukrotnie **narzędzia administracyjne**, a następnie kliknij dwukrotnie **Podgląd zdarzeń**.  
  
### <a name="application-event-log"></a>Dziennik zdarzeń aplikacji  
 **w dzienniku zdarzeń aplikacji** zawiera większość zdarzeń wygenerowanych przez usługę WCF. Większość pozycji wskazują, że poszczególnych funkcji nie można uruchomić aplikacji. Przykłady obejmują:  
  
-   Rejestrowanie komunikatów/śledzenie: WCF powoduje zapisanie zdarzenia w dzienniku zdarzeń, gdy śledzenia i rejestrowania komunikatów nie powiodło się. Jednak nie każdy błąd śledzenia wyzwala zdarzenie. Aby zapobiec całkowicie wypełnione błędów ślady dziennika zdarzeń, usługi WCF implementuje na 10 minut okres niedostępności takiego zdarzenia. Oznacza to, że jeśli WCF zapisów śledzenia awarii w dzienniku zdarzeń nie ma tak ponownie dla co najmniej 10 minut.  
  
-   Udostępnione odbiornika: Usługa Udostępnianie portów TCP WCF rejestruje zdarzenie, gdy nie powiedzie się uruchomienie.  
  
-   [!INCLUDE[infocard](../../../../../includes/infocard-md.md)]: Dzienniki zdarzeń, gdy nie można uruchomić usługi.  
  
-   Błąd i krytyczne zdarzenia, takie jak błędy podczas uruchamiania lub awarii (Crash)  
  
-   Rejestrowanie komunikatów jest włączona: dzienniki zdarzeń, gdy jest włączone rejestrowanie komunikatów. To Powiadom administratora, czy informacje poufne, specyficzne dla aplikacji mogą być rejestrowane w nagłówkach wiadomości i treści.  
  
-   Zdarzenie jest rejestrowane po `enableLoggingKnownPII` atrybutu w `machineSettings` elementu `machine.config` plik jest ustawiony. Ten atrybut określa, czy dowolnej aplikacji uruchomionych na komputerze jest uprawniony do logowania znane dane osobowe (dane osobowe).  
  
-   Jeśli `logKnownPii` atrybutu w jednym `app.config` lub `web.config` plik ma ustawioną wartość `true` dla określonej aplikacji włączyć rejestrowanie danych osobowych, ale `enableLoggingKnownPII` atrybutu w `machineSettings` elementu `machine.config` ustawiono pliku Aby `false`, zdarzenie jest rejestrowane. Ponadto, jeśli obie `logKnownPii` i `enableLoggingKnownPII` są ustawione na `true`, a zdarzenie jest rejestrowane. Aby uzyskać więcej informacji na temat tych ustawień konfiguracji, zobacz sekcję zabezpieczeń [Konfigurowanie rejestrowania komunikatów](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) tematu.  
  
### <a name="security-event-log"></a>Dziennik zdarzeń zabezpieczeń  
 **Dziennika zdarzeń zabezpieczeń** zawiera zdarzenia inspekcji zabezpieczeń, które są rejestrowane przez usługę WCF.  
  
### <a name="system-event-log"></a>W dzienniku zdarzeń systemowych  
 Usługi WCF nie logują się niczego **w dzienniku zdarzeń systemowych**.  
  
### <a name="event-log-entries"></a>Wpisy dziennika zdarzeń  
 **Źródła** zdarzenia jest nazwą zestawu, który generuje wpis dziennika.  
  
 Typ wpisu dziennika zdarzeń służy do wskazuje ważność danego zdarzenia. Każde zdarzenie musi być jednego typu, który aplikacja wskazuje, kiedy zgłasza zdarzenie. Podgląd zdarzeń używa tego typu, aby określić ikonę wyświetlaną w widoku listy dziennika. Dla typu zdarzeń wpis dziennika zdarzeń, zobacz <xref:System.Diagnostics.EventLogEntryType>.  
  
 Po kliknięciu przycisku "więcej informacji" podczas wyświetlania zdarzeń w Podglądzie zdarzeń, Podgląd zdarzeń może wysłać informacje przez Internet. Aby uzyskać więcej informacji zobacz Pomoc Podglądu zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Informacje ogólne o zdarzeniach](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
