---
title: Administracja i diagnostyka
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, diagnostics
- Windows Communication Foundation, administration
- diagnostics [WCF]
- WCF, diagnostics
- administration [WCF]
- WCF, administration
ms.assetid: 34c81c08-0e0f-4fbc-9ae8-91948640ee43
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2f103570cf7d94a9ac6256f3db991c44767fa7c4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="administration-and-diagnostics"></a>Administracja i diagnostyka
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]zawiera bogaty zestaw funkcji, które ułatwiają monitorowanie różnych etapach cyklu życia aplikacji. Na przykład można użyć konfiguracji do skonfigurowania usług i klientów na wdrożenie. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zawiera duży zbiór liczników wydajności, aby ocenić wydajność aplikacji. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]udostępnia również kontroli danych w czasie wykonywania za pośrednictwem usługi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dostawcy Instrumentacji zarządzania Windows (WMI). Gdy aplikacja ulegnie awarii lub rozpoczyna się działający nieprawidłowo, umożliwia dziennika zdarzeń czy znaczących niczego pojawił się w temacie. Umożliwia także rejestrowanie komunikatów i śledzenie, aby zobaczyć, jakie zdarzenia są w toku end-to-end w aplikacji. Funkcje te pomagają zarówno deweloperów i specjalistów IT, aby rozwiązać [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji, gdy jest nie działa prawidłowo.  
  
> [!NOTE]
>  Jeśli otrzymujesz błędy bez informacji o określone informacje szczegółowe, należy włączyć `includeExceptionDetailInFaults` atrybutu [ \<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) element konfiguracji. To powoduje, że [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wysłać szczegóły wyjątku do klientów, które pozwala wykrywać wiele typowych problemów bez konieczności bardziej zaawansowanych diagnostyki. Aby uzyskać więcej informacji, zobacz [wysyłanie i odbieranie błędów](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="diagnostics-features-provided-by-wcf"></a>Diagnostyka funkcje oferowane przez usługi WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zapewnia następujące funkcje diagnostyczne:  
  
-   Śledzenia end-To-End zawiera dane Instrumentacji do rozwiązywania problemów z aplikacji bez użycia debugera. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]dane wyjściowe śledzenia dla procesu punktów kontrolnych, a także komunikaty o błędach. Mogą to być otwarcie fabryki kanałów lub wysyłania i odbierania wiadomości przez hosta usługi. Śledzenie można włączyć dla uruchomionej aplikacji można monitorować jej postęp. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/index.md) tematu. Aby zrozumieć, jak umożliwia śledzenie debugowania aplikacji, zobacz [przy użyciu śledzenie, aby rozwiązać Twoja aplikacja](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md) tematu.  
  
-   Rejestrowanie komunikatów pozwala zobaczyć wiadomości przed i po transmisji. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][rejestrowania komunikatów](../../../../docs/framework/wcf/diagnostics/message-logging.md) tematu.  
  
-   Śledzenie zdarzeń zapisuje zdarzenia w dzienniku zdarzeń wszystkie poważne problemy. Można następnie użyj Podglądu zdarzeń, aby sprawdzić wszelkie nieprawidłowości. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][rejestrowania zdarzeń](../../../../docs/framework/wcf/diagnostics/event-logging/index.md) tematu.  
  
-   Liczniki wydajności za pośrednictwem Monitora wydajności pozwalają monitorować kondycję systemu i aplikacji. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][liczniki wydajności](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md) tematu.  
  
-   <xref:System.ServiceModel.Configuration> Przestrzeni nazw można ładować pliki konfiguracyjne i skonfiguruj punkt końcowy usługi lub klienta. Można użyć modelu obiektów do zmiany skryptu do wielu aplikacji, gdy należy wdrożyć aktualizacje na wielu komputerach. Alternatywnie można użyć [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) edytować ustawienia konfiguracji przy użyciu graficznego interfejsu użytkownika kreatora. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Konfigurowanie Twoja aplikacja](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md) tematu.  
  
-   Usługi WMI można dowiedzieć się, jakie usługi nasłuchują na maszynie, powiązania, które są używane. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][przy użyciu Instrumentacji zarządzania Windows dla diagnostyki](../../../../docs/framework/wcf/diagnostics/wmi/index.md) tematu.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]udostępnia również kilka graficznego interfejsu użytkownika i narzędzia wiersza polecenia, aby ułatwić tworzenie, wdrażanie i zarządzanie nimi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Narzędzia programu Windows Communication Foundation](../../../../docs/framework/wcf/tools.md). Na przykład można użyć [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) można tworzyć i edytować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ustawienia konfiguracji za pomocą kreatora, zamiast bezpośredniego edytowania XML. Można również użyć [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) do wyświetlenia, grupy i filtrować komunikaty śledzenia, dzięki czemu można zdiagnozować, naprawy i sprawdź problemy z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie aplikacji](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)  
 [Wdrażanie usług](../../../../docs/framework/wcf/diagnostics/deploying-services.md)  
 [Informacje o wyjątkach](../../../../docs/framework/wcf/diagnostics/exceptions-reference/index.md)  
 [Rejestrowanie zdarzeń](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [Rejestrowanie komunikatów](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Narzędzie podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [Narzędzie rejestracji modelu ServiceModel](../../../../docs/framework/wcf/diagnostics/servicemodel-registration-tool.md)  
 [Śledzenie](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Za pomocą Instrumentacji zarządzania Windows dla diagnostyki](../../../../docs/framework/wcf/diagnostics/wmi/index.md)  
 [Liczniki wydajności](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)  
 [Narzędzia programu Windows Communication Foundation](../../../../docs/framework/wcf/tools.md)
