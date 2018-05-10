---
title: Administracja i diagnostyka
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, diagnostics
- Windows Communication Foundation, administration
- diagnostics [WCF]
- WCF, diagnostics
- administration [WCF]
- WCF, administration
ms.assetid: 34c81c08-0e0f-4fbc-9ae8-91948640ee43
ms.openlocfilehash: c69d5681b186fdfae168ceea8b35f5786eaf02c9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="administration-and-diagnostics"></a>Administracja i diagnostyka
Windows Communication Foundation (WCF) zawiera bogaty zestaw funkcji, które ułatwiają monitorowanie różnych etapach cyklu życia aplikacji. Na przykład można użyć konfiguracji do skonfigurowania usług i klientów na wdrożenie. Usługi WCF zawiera duży zbiór liczników wydajności, aby ocenić wydajność aplikacji. Usługa WCF umożliwia również dane inspekcji usługi w czasie wykonywania za pośrednictwem dostawcy usług WCF Instrumentacji zarządzania Windows (WMI). Gdy aplikacja ulegnie awarii lub rozpoczyna się działający nieprawidłowo, umożliwia dziennika zdarzeń czy znaczących niczego pojawił się w temacie. Umożliwia także rejestrowanie komunikatów i śledzenie, aby zobaczyć, jakie zdarzenia są w toku end-to-end w aplikacji. Funkcje te pomagają zarówno deweloperów i informatyków, rozwiązywania problemów z aplikacji WCF jest nie działa prawidłowo.  
  
> [!NOTE]
>  Jeśli otrzymujesz błędy bez informacji o określone informacje szczegółowe, należy włączyć `includeExceptionDetailInFaults` atrybutu [ \<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) element konfiguracji. To powoduje, że usługi WCF do wysyłania szczegóły wyjątku do klientów, dzięki czemu można wykrywać wiele typowych problemów bez konieczności bardziej zaawansowanych diagnostyki. Aby uzyskać więcej informacji, zobacz [wysyłanie i odbieranie błędów](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="diagnostics-features-provided-by-wcf"></a>Diagnostyka funkcje oferowane przez usługi WCF  
 Usługi WCF oferuje następujące funkcje diagnostyczne:  
  
-   Śledzenia end-To-End zawiera dane Instrumentacji do rozwiązywania problemów z aplikacji bez użycia debugera. Usługi WCF danych wyjściowych danych śledzenia dla procesu punktów kontrolnych, a także komunikaty o błędach. Mogą to być otwarcie fabryki kanałów lub wysyłania i odbierania wiadomości przez hosta usługi. Śledzenie można włączyć dla uruchomionej aplikacji można monitorować jej postęp. Aby uzyskać więcej informacji, zobacz [śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/index.md) tematu. Aby zrozumieć, jak umożliwia śledzenie debugowania aplikacji, zobacz [przy użyciu śledzenie, aby rozwiązać Twoja aplikacja](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md) tematu.  
  
-   Rejestrowanie komunikatów pozwala zobaczyć wiadomości przed i po transmisji. Aby uzyskać więcej informacji, zobacz [rejestrowania komunikatów](../../../../docs/framework/wcf/diagnostics/message-logging.md) tematu.  
  
-   Śledzenie zdarzeń zapisuje zdarzenia w dzienniku zdarzeń wszystkie poważne problemy. Można następnie użyj Podglądu zdarzeń, aby sprawdzić wszelkie nieprawidłowości. Aby uzyskać więcej informacji, zobacz [rejestrowania zdarzeń](../../../../docs/framework/wcf/diagnostics/event-logging/index.md) tematu.  
  
-   Liczniki wydajności za pośrednictwem Monitora wydajności pozwalają monitorować kondycję systemu i aplikacji. Aby uzyskać więcej informacji, zobacz [liczniki wydajności](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md) tematu.  
  
-   <xref:System.ServiceModel.Configuration> Przestrzeni nazw można ładować pliki konfiguracyjne i skonfiguruj punkt końcowy usługi lub klienta. Można użyć modelu obiektów do zmiany skryptu do wielu aplikacji, gdy należy wdrożyć aktualizacje na wielu komputerach. Alternatywnie można użyć [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) edytować ustawienia konfiguracji przy użyciu graficznego interfejsu użytkownika kreatora. Aby uzyskać więcej informacji, zobacz [Konfigurowanie Twoja aplikacja](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md) tematu.  
  
-   Usługi WMI można dowiedzieć się, jakie usługi nasłuchują na maszynie, powiązania, które są używane. Aby uzyskać więcej informacji, zobacz [przy użyciu Instrumentacji zarządzania Windows dla diagnostyki](../../../../docs/framework/wcf/diagnostics/wmi/index.md) tematu.  
  
 WCF zawiera także kilka narzędzi graficznego interfejsu użytkownika i wiersza polecenia, aby ułatwić umożliwiające tworzenie, wdrażanie i zarządzanie aplikacjami WCF. Aby uzyskać więcej informacji, zobacz [narzędzia programu Windows Communication Foundation](../../../../docs/framework/wcf/tools.md). Na przykład można użyć [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) można tworzyć i edytować ustawienia konfiguracji usługi WCF, za pomocą kreatora, zamiast bezpośredniego edytowania XML. Można również użyć [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) do wyświetlenia, grupy i filtrować komunikaty śledzenia, dzięki czemu można zdiagnozować, naprawy i sprawdź problemy z usługi WCF.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie własnej aplikacji](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)  
 [Wdrażanie usług](../../../../docs/framework/wcf/diagnostics/deploying-services.md)  
 [Dokumentacja wyjątków](../../../../docs/framework/wcf/diagnostics/exceptions-reference/index.md)  
 [Rejestrowanie zdarzeń](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [Rejestrowanie komunikatów](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [Narzędzie rejestracji modelu ServiceModel](../../../../docs/framework/wcf/diagnostics/servicemodel-registration-tool.md)  
 [Śledzenie](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Używanie Instrumentacji zarządzania Windows na potrzeby diagnostyki](../../../../docs/framework/wcf/diagnostics/wmi/index.md)  
 [Liczniki wydajności](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)  
 [Narzędzia programu Windows Communication Foundation](../../../../docs/framework/wcf/tools.md)
