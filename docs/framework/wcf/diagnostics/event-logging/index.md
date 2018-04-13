---
title: Rejestrowanie zdarzeń w architekturze WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- event logging [WCF]
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4028772caef8e5c0301ab3a6a0bde2f180d821ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="event-logging-in-wcf"></a>Rejestrowanie zdarzeń w architekturze WCF
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]śledzi wewnętrznego zdarzenia w dzienniku zdarzeń systemu Windows.  
  
## <a name="viewing-event-logs"></a>Wyświetlanie dzienników zdarzeń  
 Rejestrowanie zdarzeń jest automatycznie włączone domyślnie i nie istnieje mechanizm je wyłączyć. Zdarzenia zarejestrowane przez [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] można wyświetlić za pomocą Podglądu zdarzeń. Aby uruchomić to narzędzie, kliknij przycisk **Start**, kliknij przycisk **Panelu sterowania**, kliknij dwukrotnie **narzędzia administracyjne**, a następnie kliknij dwukrotnie **Podgląd zdarzeń**.  
  
### <a name="application-event-log"></a>Dziennik zdarzeń aplikacji  
 **w dzienniku zdarzeń aplikacji** zawiera większość zdarzeń generowanych przez [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]. Większość pozycji wskazują, że poszczególnych funkcji nie można uruchomić aplikacji. Przykłady obejmują:  
  
-   Rejestrowanie komunikatów/śledzenie: [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zapisuje zdarzenie w dzienniku zdarzeń, gdy śledzenie i rejestrowanie komunikatów nie powiodło się. Jednak nie każdy błąd śledzenia wyzwala zdarzenie. Aby zapobiec całkowicie wypełnione błędów ślady dziennika zdarzeń [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] implementuje na 10 minut okres niedostępności takiego zdarzenia. Oznacza to, że jeśli [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Błąd śledzenia zapisuje w dzienniku zdarzeń nie ma tak ponownie dla co najmniej 10 minut.  
  
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
