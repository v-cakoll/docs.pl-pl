---
title: Kontrola i śledzenie przepływu pracy
description: Śledzenie przepływu pracy systemu Windows jest funkcją .NET Framework 4.6.1, która zapewnia infrastrukturę śledzenia do śledzenia wykonywania wystąpienia przepływu pracy.
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], tracking and tracing
ms.assetid: b965ded6-370a-483d-8790-f794f65b137e
ms.openlocfilehash: f88ff68a361bf3882d75bc2d5fb21903fd283a4d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421296"
---
# <a name="workflow-tracking-and-tracing"></a>Kontrola i śledzenie przepływu pracy
Śledzenie przepływu pracy systemu Windows to [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Funkcja przeznaczona do zapewnienia wglądu w wykonywanie przepływu pracy. Zapewnia infrastrukturę śledzenia do śledzenia wykonywania wystąpienia przepływu pracy. Infrastruktura śledzenia WF w sposób przezroczysty przydzieli przepływy pracy, aby emitować rekordy odzwierciedlające kluczowe zdarzenia podczas wykonywania. Ta funkcja jest domyślnie dostępna dla każdego [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] przepływu pracy. Nie są wymagane żadne zmiany, aby można było wykonać [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Śledzenie w przepływie pracy. Jest to tylko kwestia decydowania o ilości danych śledzenia, które mają zostać odebrane. Gdy wystąpienie przepływu pracy zostanie rozpoczęte lub zostanie zakończone, jego rekordy śledzenia przetwarzania są emitowane. Śledzenie może również wyodrębnić dane biznesowe powiązane z zmiennymi przepływu pracy. Na przykład, jeśli przepływ pracy reprezentuje system przetwarzania zamówień, można wyodrębnić identyfikator zamówienia wraz z <xref:System.Activities.Tracking.TrackingRecord> obiektem. Ogólnie rzecz biorąc, włączenie śledzenia WF ułatwia uzyskiwanie dostępu do danych diagnostycznych i analizy biznesowej z wykonywania przepływu pracy.  
  
 Te składniki śledzenia są równoważne usłudze śledzenia w programie WinFX. W programie [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] wydajność została ulepszona i model programowania uproszczony dla funkcji śledzenia WF. Funkcja śledzenia środowiska uruchomieniowego tworzy wystąpienie przepływu pracy, aby emitować zdarzenia związane z cyklem życia przepływu pracy, działaniami przepływu pracy i zdarzeniami niestandardowymi.  
  
 Sieć szkieletowa aplikacji systemu Windows Server umożliwia również monitorowanie wykonywania usług WCF i Workflow. Aby uzyskać więcej informacji, zobacz Monitorowanie i monitorowanie aplikacji [sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10)) [za pomocą programu Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))  
  
 Aby rozwiązać problem środowiska uruchomieniowego przepływu pracy, możesz włączyć śledzenie przepływu pracy diagnostyki. Aby uzyskać więcej informacji, zobacz [śledzenie przepływu pracy](workflow-tracing.md).  
  
 Aby zrozumieć model programowania, podstawowe składniki infrastruktury śledzenia zostały omówione w tym temacie:  
  
- <xref:System.Activities.Tracking.TrackingRecord>obiekty emitowane z środowiska uruchomieniowego przepływu pracy. Aby uzyskać więcej informacji, zobacz [śledzenie rekordów](tracking-records.md).  
  
- <xref:System.Activities.Tracking.TrackingParticipant>obiekty subskrybują <xref:System.Activities.Tracking.TrackingRecord> obiekty. Uczestnicy śledzenia zawierają logikę do przetwarzania ładunku z <xref:System.Activities.Tracking.TrackingRecord> obiektów (na przykład mogą zdecydować się na zapisanie w pliku). Aby uzyskać więcej informacji, zobacz [Śledzenie uczestników](tracking-participants.md).  
  
- <xref:System.Activities.Tracking.TrackingProfile>Filtrowanie obiektów rekordów śledzenia z wystąpienia przepływu pracy. Aby uzyskać więcej informacji, zobacz [śledzenie profilów](tracking-profiles.md).  
  
## <a name="workflow-tracking-infrastructure"></a>Infrastruktura śledzenia przepływu pracy  
 Infrastruktura śledzenia przepływu pracy jest zgodna z modelem publikowania i subskrybowania. Wystąpienie przepływu pracy jest wydawcą rekordów śledzenia, podczas gdy Subskrybenci rekordów śledzenia są zarejestrowani jako rozszerzenia przepływu pracy. Te rozszerzenia, które subskrybują <xref:System.Activities.Tracking.TrackingRecord> obiekty, są nazywane uczestnikami śledzenia. Śledzenie uczestników to punkty rozszerzalności, które uzyskują dostęp do <xref:System.Activities.Tracking.TrackingRecord> obiektów i przetwarzają je w dowolny sposób. Infrastruktura śledzenia umożliwia stosowanie filtru dla wychodzących rekordów śledzenia, aby umożliwić uczestnikowi subskrybowanie podzestawu rekordów. Ten mechanizm filtrowania jest realizowany za pomocą pliku profilu śledzenia.  
  
 Na poniższej ilustracji przedstawiono widok wysokiego poziomu infrastruktury śledzenia:  
  
 ![Zrzut ekranu przedstawiający infrastrukturę śledzenia przepływu pracy.](./media/workflow-tracking-and-tracing/workflow-tracking-infrastructure.gif "WV")  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Rekordy śledzenia](tracking-records.md)  
 Opisuje rekordy śledzenia, które są emitowane przez środowisko uruchomieniowe przepływu pracy.  
  
 [Profile śledzenia](tracking-profiles.md)  
 W tym artykule omówiono sposób używania profilów śledzenia.  
  
 [Uczestnicy śledzenia](tracking-participants.md)  
 Opisuje sposób użycia uczestnika śledzenia systemu lub tworzenia niestandardowych uczestników śledzenia.  
  
 [Konfigurowanie śledzenia dla przepływu pracy](configuring-tracking-for-a-workflow.md)  
 Opisuje sposób konfigurowania śledzenia dla przepływu pracy.  
  
 [Śledzenie przepływu pracy](workflow-tracing.md)  
 Opisuje dwa sposoby włączania śledzenia debugowania dla przepływu pracy.  
  
## <a name="see-also"></a>Zobacz także

- [Śledzenie SQL](./samples/sql-tracking.md)
