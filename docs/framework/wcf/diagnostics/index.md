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
ms.openlocfilehash: 5df95c6b5f91cd4f36bd03c1bd291f7a44025ee9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64600086"
---
# <a name="administration-and-diagnostics"></a>Administracja i diagnostyka
Windows Communication Foundation (WCF) zapewnia bogaty zestaw funkcji, które mogą ułatwić monitorowanie różnych etapach cyklu życia aplikacji. Na przykład można użyć konfiguracji do skonfigurowania usług i klientów we wdrożeniu. Usługi WCF zawierają duży zestaw liczników wydajności, aby ułatwić mierzyć wydajność aplikacji. Usługa WCF umożliwia również dane inspekcji usługi w czasie wykonywania za pośrednictwem dostawcy Instrumentacji zarządzania Windows (WMI) WCF. Podczas ulegnie awarii lub rozpoczyna się nieprawidłowo działających aplikacji, można użyć w dzienniku zdarzeń, aby zobaczyć, czy ma żadnych znaczących wystąpił. Aby zobaczyć, jakie zdarzenia są występuje end-to-end w aplikacji, można użyć rejestrowania komunikatów i śledzenia. Funkcje te pomagają zarówno deweloperów i specjalistów IT, aby rozwiązywać problemy z aplikacją usługi WCF, gdy go nie zachowuje się poprawnie.  
  
> [!NOTE]
>  Jeśli otrzymujesz błędy bez określonych szczegółowych informacji, należy włączyć `includeExceptionDetailInFaults` atrybutu [ \<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) element konfiguracji. To powoduje, że wysyłać szczegóły wyjątku do klientów, WCF, która umożliwia wykrywanie wielu typowych problemów bez konieczności bardziej zaawansowanej diagnostyki. Aby uzyskać więcej informacji, zobacz [wysyłanie i odbieranie błędów](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="diagnostics-features-provided-by-wcf"></a>Funkcje diagnostyczne przez architekturę WCF  
 Usługi WCF udostępnia następujące funkcje diagnostyki:  
  
- Śledzenie end-To-End udostępnia dane instrumentacji dla rozwiązywania problemów z aplikacją, bez korzystania z debugera. Usługi WCF danych wyjściowych danych śledzenia dla procesu punktów kontrolnych, a także komunikaty o błędach. Może to obejmować otwarcie fabryki kanałów lub wysyłania i odbierania wiadomości przez hosta usługi. Śledzenie można włączyć dla uruchomionej aplikacji, aby monitorować jej postęp. Aby uzyskać więcej informacji, zobacz [śledzenie](../../../../docs/framework/wcf/diagnostics/tracing/index.md) tematu. Aby dowiedzieć się, jak można użyć z funkcji śledzenia podczas debugowania aplikacji, zobacz [przy użyciu śledzenia do Rozwiązywanie problemów aplikacji](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md) tematu.  
  
- Rejestrowanie komunikatów pozwala sprawdzić wygląd komunikatów przed i po transmisji. Aby uzyskać więcej informacji, zobacz [rejestrowania komunikatów](../../../../docs/framework/wcf/diagnostics/message-logging.md) tematu.  
  
- Śledzenie zdarzeń zapisuje zdarzenia w dzienniku zdarzeń wszystkie poważne problemy. Możesz następnie Podglądzie zdarzeń, aby sprawdzić wszelkie nieprawidłowości. Aby uzyskać więcej informacji, zobacz [rejestrowania zdarzeń](../../../../docs/framework/wcf/diagnostics/event-logging/index.md) tematu.  
  
- Liczniki wydajności udostępniane za pośrednictwem Monitora wydajności pozwalają monitorować aplikację i kondycji systemu. Aby uzyskać więcej informacji, zobacz [liczniki wydajności](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md) tematu.  
  
- <xref:System.ServiceModel.Configuration> Przestrzeni nazw można ładować pliki konfiguracyjne i skonfiguruj punkt końcowy usługi lub klienta. Podczas aktualizacji należy wdrożyć na wielu komputerach, można użyć modelu obiektów do skryptu zmian do wielu aplikacji. Alternatywnie, można użyć [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) Aby edytować ustawienia konfiguracji, za pomocą Kreatora graficznego interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [konfigurowania aplikacji](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md) tematu.  
  
- WMI umożliwia dowiedzieć się, które usługi nasłuchują na maszynie, powiązania, które są używane. Aby uzyskać więcej informacji, zobacz [przy użyciu Instrumentacji zarządzania Windows Diagnostics](../../../../docs/framework/wcf/diagnostics/wmi/index.md) tematu.  
  
 Usługi WCF zawiera także kilka narzędzi graficzny interfejs użytkownika i wiersza polecenia, aby ułatwić umożliwiające tworzenie, wdrażanie i zarządzanie aplikacjami usługi WCF. Aby uzyskać więcej informacji, zobacz [narzędzia programu Windows Communication Foundation](../../../../docs/framework/wcf/tools.md). Na przykład, można użyć [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) można tworzyć i edytować ustawienia konfiguracji programu WCF za pomocą kreatora, a nie bezpośrednio edycji XML. Można również użyć [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) do wyświetlania, grupy i filtrować komunikaty śledzenia, dzięki czemu możesz zdiagnozować, naprawy i sprawdź problemów w przypadku usług WCF.  
  
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
