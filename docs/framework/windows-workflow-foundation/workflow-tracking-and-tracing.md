---
title: Kontrola i śledzenie przepływu pracy
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], tracking and tracing
ms.assetid: b965ded6-370a-483d-8790-f794f65b137e
ms.openlocfilehash: 9f887babec5c070eed2fb3c7e4d8d35cdfb3f488
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837483"
---
# <a name="workflow-tracking-and-tracing"></a>Kontrola i śledzenie przepływu pracy
Śledzenie przepływu pracy systemu Windows jest funkcją [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)], która umożliwia wgląd w wykonywanie przepływu pracy. Zapewnia infrastrukturę śledzenia do śledzenia wykonywania wystąpienia przepływu pracy. Infrastruktura śledzenia WF w sposób przezroczysty przydzieli przepływy pracy, aby emitować rekordy odzwierciedlające kluczowe zdarzenia podczas wykonywania. Ta funkcja jest domyślnie dostępna dla każdego [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]ego przepływu pracy. Aby śledzenie miało miejsce, nie trzeba wprowadzać żadnych zmian w przepływie pracy [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]. Jest to tylko kwestia decydowania o ilości danych śledzenia, które mają zostać odebrane. Gdy wystąpienie przepływu pracy zostanie rozpoczęte lub zostanie zakończone, jego rekordy śledzenia przetwarzania są emitowane. Śledzenie może również wyodrębnić dane biznesowe powiązane z zmiennymi przepływu pracy. Na przykład jeśli przepływ pracy reprezentuje system przetwarzania zamówień, można wyodrębnić identyfikator zamówienia wraz z obiektem <xref:System.Activities.Tracking.TrackingRecord>. Ogólnie rzecz biorąc, włączenie śledzenia WF ułatwia uzyskiwanie dostępu do danych diagnostycznych i analizy biznesowej z wykonywania przepływu pracy.  
  
 Te składniki śledzenia są równoważne usłudze śledzenia w programie WinFX. W [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]wydajność została ulepszona i model programowania uproszczony dla funkcji śledzenia WF. Funkcja śledzenia środowiska uruchomieniowego tworzy wystąpienie przepływu pracy, aby emitować zdarzenia związane z cyklem życia przepływu pracy, działaniami przepływu pracy i zdarzeniami niestandardowymi.  
  
 Sieć szkieletowa aplikacji systemu Windows Server umożliwia również monitorowanie wykonywania usług WCF i Workflow. Aby uzyskać więcej informacji, zobacz Monitorowanie i monitorowanie aplikacji [sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10)) [za pomocą programu Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))  
  
 Aby rozwiązać problem środowiska uruchomieniowego przepływu pracy, możesz włączyć śledzenie przepływu pracy diagnostyki. Aby uzyskać więcej informacji, zobacz [śledzenie przepływu pracy](workflow-tracing.md).  
  
 Aby zrozumieć model programowania, podstawowe składniki infrastruktury śledzenia zostały omówione w tym temacie:  
  
- <xref:System.Activities.Tracking.TrackingRecord> obiekty emitowane z środowiska uruchomieniowego przepływu pracy. Aby uzyskać więcej informacji, zobacz [śledzenie rekordów](tracking-records.md).  
  
- obiekty <xref:System.Activities.Tracking.TrackingParticipant> subskrybują obiekty <xref:System.Activities.Tracking.TrackingRecord>. Uczestnicy śledzenia mogą przetwarzać ładunek z obiektów <xref:System.Activities.Tracking.TrackingRecord> (na przykład mogli wybrać zapis w pliku). Aby uzyskać więcej informacji, zobacz [Śledzenie uczestników](tracking-participants.md).  
  
- <xref:System.Activities.Tracking.TrackingProfile> obiektów filtrowania rekordów śledzenia emitowanych z wystąpienia przepływu pracy. Aby uzyskać więcej informacji, zobacz [śledzenie profilów](tracking-profiles.md).  
  
## <a name="workflow-tracking-infrastructure"></a>Infrastruktura śledzenia przepływu pracy  
 Infrastruktura śledzenia przepływu pracy jest zgodna z modelem publikowania i subskrybowania. Wystąpienie przepływu pracy jest wydawcą rekordów śledzenia, podczas gdy Subskrybenci rekordów śledzenia są zarejestrowani jako rozszerzenia przepływu pracy. Te rozszerzenia, które subskrybują obiekty <xref:System.Activities.Tracking.TrackingRecord>, są nazywane uczestnikami śledzenia. Śledzenie uczestników to punkty rozszerzalności, które uzyskują dostęp <xref:System.Activities.Tracking.TrackingRecord> obiektów i przetwarzają je w dowolny sposób. Infrastruktura śledzenia umożliwia stosowanie filtru dla wychodzących rekordów śledzenia, aby umożliwić uczestnikowi subskrybowanie podzestawu rekordów. Ten mechanizm filtrowania jest realizowany za pomocą pliku profilu śledzenia.  
  
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
