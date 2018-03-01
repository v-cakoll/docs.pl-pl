---
title: "Przepływ pracy, kontrola i śledzenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- programming [WF], tracking and tracing
ms.assetid: b965ded6-370a-483d-8790-f794f65b137e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c7383d899af741e4a6c85b40e2316a6b759aa416
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-tracking-and-tracing"></a>Przepływ pracy, kontrola i śledzenie
Śledzenie przepływu pracy systemu Windows jest [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] funkcja zapewnia wgląd w wykonywania przepływu pracy. Zapewnia infrastrukturę śledzenia, śledzić wystąpienia przepływu pracy. Infrastruktury programu WF śledzenia przezroczysty wykonuje Instrumentację Emituj rekordów odzwierciedlające zdarzenia klucza podczas wykonywania przepływu pracy. Ta funkcja jest dostępna domyślnie dla każdego [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] przepływu pracy. Zmiany nie są wymagane do [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] przepływu pracy dla śledzenia występuje. Jest to jedynie podejmowania decyzji o tym, jak dużo danych śledzenia, które chcesz otrzymywać. Podczas uruchamiania wystąpienia przepływu pracy, lub zakończeniu jego przetwarzanie śledzenia są emitowane rekordów. Śledzenie można również wyodrębnić odpowiednich firm dane skojarzone z zmienne przepływu pracy. Na przykład, jeśli przepływ pracy reprezentuje kolejność przetwarzania systemu, identyfikator zamówienia można wyodrębnić wraz z programem <xref:System.Activities.Tracking.TrackingRecord> obiektu. Ogólnie rzecz biorąc Włączanie śledzenia WF ułatwia diagnostyki lub danych analiz biznesowych można uzyskać dostępu do pochodzący z wykonania przepływu pracy.  
  
 Śledzenie składniki są równoważne usługi śledzenia w [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)]. W [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], została zwiększona wydajność i uproszczony model programowania dla funkcji śledzenia WF. Środowisko uruchomieniowe śledzenia instruments wystąpienia przepływu pracy do wysyłania zdarzeń związanych z cyklem życia przepływu pracy i działań przepływu pracy oraz zdarzeń niestandardowych.  
  
 Windows Server AppFabric umożliwia również monitorować wykonywania usług WCF i przepływ pracy. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Systemu Windows Server AppFabric monitorowania](http://go.microsoft.com/fwlink/?LinkId=201273) i [monitorowania aplikacji za pomocą programu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=201287)  
  
 Aby rozwiązać środowiska uruchomieniowego przepływu pracy, można włączyć śledzenie przepływu pracy diagnostyki. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Przepływu pracy śledzenia](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md).  
  
 Aby zrozumieć modelu programowania, podstawowymi składnikami infrastruktury śledzenia zostały omówione w tym temacie:  
  
-   <xref:System.Activities.Tracking.TrackingRecord>obiektów emitowanych przez środowisko uruchomieniowe przepływu pracy. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Śledzenie rekordów](../../../docs/framework/windows-workflow-foundation/tracking-records.md).  
  
-   <xref:System.Activities.Tracking.TrackingParticipant>obiekty subskrybować <xref:System.Activities.Tracking.TrackingRecord> obiektów. Uczestników śledzenia zawierają logikę przetwarzania ładunku z <xref:System.Activities.Tracking.TrackingRecord> obiektów (na przykład ich można zapisać do pliku). [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Uczestników śledzenia](../../../docs/framework/windows-workflow-foundation/tracking-participants.md).  
  
-   <xref:System.Activities.Tracking.TrackingProfile>obiekty filtrowanie rekordów śledzenia wyemitowanego z wystąpieniem przepływu pracy. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Śledzenia profile](../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
## <a name="workflow-tracking-infrastructure"></a>Infrastruktura śledzenia przepływu pracy  
 Infrastruktura śledzenia przepływu pracy wykonuje modelu publikowania i subskrybowania. Wystąpienie przepływu pracy jest wydawcą śledzenia rekordów, gdy subskrybenci rekordów śledzenia są rejestrowane jako rozszerzenia do przepływu pracy. Te rozszerzenia, które subskrybować <xref:System.Activities.Tracking.TrackingRecord> obiekty są nazywane uczestników śledzenia. Uczestników śledzenia są punkty rozszerzeń, które uzyskują dostęp do <xref:System.Activities.Tracking.TrackingRecord> obiekty i przetwarzanie ich w jakikolwiek sposób są one zapisywane w tym celu. Infrastruktura śledzenia umożliwia zastosowania filtru wychodzących rekordów śledzenia umożliwia uczestnika do subskrybowania podzestaw rekordów. Ten mechanizm filtrowania odbywa się za pośrednictwem śledzenia pliku profilu.  
  
 Widok wysokiego poziomu śledzenia infrastruktury przedstawiono na poniższej ilustracji.  
  
 ![Przepływ pracy śledzenia infrastruktury](../../../docs/framework/windows-workflow-foundation/media/wv.gif "WV")  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Rekordy śledzenia](../../../docs/framework/windows-workflow-foundation/tracking-records.md)  
 W tym artykule opisano rekordy śledzenia emitowane środowiska uruchomieniowego przepływu pracy.  
  
 [Profile śledzenia](../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
 W tym artykule omówiono, jak profile śledzenia są używane.  
  
 [Uczestnicy śledzenia](../../../docs/framework/windows-workflow-foundation/tracking-participants.md)  
 W tym artykule opisano sposób użycia uczestnika śledzenia dostarczane przez system lub tworzenie niestandardowych śledzenia uczestników.  
  
 [Konfigurowanie śledzenia dla przepływu pracy](../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)  
 Zawiera opis sposobu konfigurowania śledzenia dla przepływu pracy.  
  
 [Śledzenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md)  
 W tym artykule opisano dwa sposoby, aby włączyć śledzenie debugowania dla przepływu pracy.  
  
 [Określanie czasu trwania wykonania przepływu pracy za pomocą śledzenia](../../../docs/framework/windows-workflow-foundation/determining-workflow-execution-duration-using-tracing.md)  
 Informacje dotyczące używania komunikaty śledzenia, aby określić czas wykonywania przepływu pracy.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie SQL](../../../docs/framework/windows-workflow-foundation/samples/sql-tracking.md)
