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
ms.openlocfilehash: d8a8d86f312c0c707ff9f60d4106cc2b5784c6a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963064"
---
# <a name="administration-and-diagnostics"></a>Administracja i diagnostyka
Windows Communication Foundation (WCF) oferuje bogaty zestaw funkcji, które mogą pomóc w monitorowaniu różnych etapów cyklu życia aplikacji. Na przykład możesz użyć konfiguracji, aby skonfigurować usługi i klientów podczas wdrażania. Program WCF zawiera duży zestaw liczników wydajności, które ułatwiają pomiar wydajności aplikacji. Funkcja WCF udostępnia również dane inspekcji usługi w czasie wykonywania za pomocą dostawcy usług WCF Instrumentacja zarządzania Windows (WMI). Gdy aplikacja napotyka błąd lub działa nieprawidłowo, można użyć dziennika zdarzeń, aby sprawdzić, czy wystąpił jakikolwiek istotny problem. Możesz również użyć rejestrowania i śledzenia komunikatów, aby sprawdzić, jakie zdarzenia kończą się w aplikacji. Te funkcje pomagają deweloperom i specjalistom IT w rozwiązywaniu problemów z aplikacją WCF, gdy nie działa prawidłowo.  
  
> [!NOTE]
> Jeśli otrzymujesz błędy bez szczegółowych informacji, należy włączyć `includeExceptionDetailInFaults` atrybut [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) elementu konfiguracji > serviceDebug. Powoduje to, że program WCF wysyła szczegóły wyjątku do klientów, co umożliwia wykrywanie wielu typowych problemów bez konieczności bardziej zaawansowanej diagnostyki. Aby uzyskać więcej informacji, zobacz [wysyłanie i otrzymywanie błędów](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="diagnostics-features-provided-by-wcf"></a>Funkcje diagnostyki udostępniane przez program WCF  
 Funkcja WCF oferuje następujące funkcje diagnostyczne:  
  
- Śledzenie kompleksowe zawiera dane instrumentacji do rozwiązywania problemów z aplikacją bez użycia debugera. Program WCF wyprowadza dane śledzenia dla punktów kontrolnych procesów, a także komunikaty o błędach. Może to obejmować otwarcie fabryki kanału lub wysłanie i odebranie komunikatów przez hosta usługi. Śledzenie można włączyć dla działającej aplikacji, aby monitorować jej postęp. Aby uzyskać więcej informacji, zobacz temat [śledzenie](../../../../docs/framework/wcf/diagnostics/tracing/index.md) . Aby zrozumieć, jak można użyć funkcji śledzenia do debugowania aplikacji, zobacz temat [Używanie śledzenia w celu rozwiązywania problemów z aplikacją](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md) .  
  
- Rejestrowanie komunikatów pozwala zobaczyć, jak komunikaty wyglądają zarówno przed, jak i po transmisji. Aby uzyskać więcej informacji, zobacz temat [Rejestrowanie komunikatów](../../../../docs/framework/wcf/diagnostics/message-logging.md) .  
  
- Śledzenie zdarzeń zapisuje zdarzenia w dzienniku zdarzeń pod kątem poważnych problemów. Następnie można użyć Podgląd zdarzeń, aby przejrzeć wszelkie nieprawidłowości. Aby uzyskać więcej informacji, zobacz temat [Rejestrowanie zdarzeń](../../../../docs/framework/wcf/diagnostics/event-logging/index.md) .  
  
- Liczniki wydajności udostępniane za poorednictwem monitora wydajności umożliwiają monitorowanie kondycji aplikacji i systemu. Aby uzyskać więcej informacji, zobacz temat [liczniki wydajności](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md) .  
  
- <xref:System.ServiceModel.Configuration> Przestrzeń nazw pozwala załadować pliki konfiguracji i skonfigurować usługę lub punkt końcowy klienta. Można użyć modelu obiektów do skryptu zmiany w wielu aplikacjach, gdy aktualizacje muszą zostać wdrożone na wielu komputerach. Alternatywnie można użyć [Narzędzia Edytora konfiguracji (SvcConfigEditor. exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) , aby edytować ustawienia konfiguracji za pomocą Kreatora graficznego interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md) .  
  
- Usługa WMI pozwala dowiedzieć się, które usługi nasłuchują na komputerze i powiązania, które są używane. Aby uzyskać więcej informacji, zobacz temat [używanie Instrumentacja zarządzania Windows do diagnostyki](../../../../docs/framework/wcf/diagnostics/wmi/index.md) .  
  
 Funkcja WCF udostępnia również kilka graficznych interfejsów użytkownika i narzędzi wiersza polecenia, które ułatwiają tworzenie i wdrażanie aplikacji WCF oraz zarządzanie nimi. Aby uzyskać więcej informacji, zobacz [narzędzia Windows Communication Foundation](../../../../docs/framework/wcf/tools.md). Na przykład można użyć [Narzędzia Edytora konfiguracji (SvcConfigEditor. exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) do tworzenia i edytowania ustawień konfiguracji WCF za pomocą kreatora, zamiast bezpośrednio edytować kod XML. Możesz również użyć [narzędzia Podgląd śledzenia usług (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) do wyświetlania, grupowania i filtrowania komunikatów śledzenia, co umożliwia diagnozowanie, naprawianie i weryfikowanie problemów z usługami WCF.  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie własnej aplikacji](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
- [Wdrażanie usług](../../../../docs/framework/wcf/diagnostics/deploying-services.md)
- [Dokumentacja wyjątków](../../../../docs/framework/wcf/diagnostics/exceptions-reference/index.md)
- [Rejestrowanie zdarzeń](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [Rejestrowanie komunikatów](../../../../docs/framework/wcf/diagnostics/message-logging.md)
- [Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)
- [Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [Narzędzie rejestracji modelu ServiceModel](../../../../docs/framework/wcf/diagnostics/servicemodel-registration-tool.md)
- [Śledzenie](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Używanie Instrumentacji zarządzania Windows na potrzeby diagnostyki](../../../../docs/framework/wcf/diagnostics/wmi/index.md)
- [Liczniki wydajności](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
- [Narzędzia programu Windows Communication Foundation](../../../../docs/framework/wcf/tools.md)
