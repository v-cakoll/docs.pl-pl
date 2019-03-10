---
title: Przepływ pracy i śledzenie
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], tracking and tracing
ms.assetid: b965ded6-370a-483d-8790-f794f65b137e
ms.openlocfilehash: 298791fc43d976e339c42c45a8fd30c25d73bdb9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708018"
---
# <a name="workflow-tracking-and-tracing"></a>Przepływ pracy i śledzenie
Śledzenie przepływu pracy Windows jest [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] funkcja przeznaczona do zapewniają widoczność wykonywania przepływu pracy. Zapewnia to Infrastruktura śledzenia do śledzenia wykonywania wystąpienia przepływu pracy. Infrastruktura śledzenia WF w sposób niewidoczny dla użytkownika instruments przepływu pracy, aby emitować rekordów odzwierciedlający kluczy zdarzeń podczas wykonywania. Ta funkcja jest domyślnie dostępny dla dowolnego [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] przepływu pracy. Żadne zmiany nie są wymagane do [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] przepływu pracy dla śledzenia wystąpienia. Jest to kwestia podejmowania decyzji o tym jak dużo danych śledzenia, które chcesz otrzymywać. Gdy wystąpienie przepływu pracy rozpoczyna się lub kończy, jego przetwarzania śledzenia są emitowane rekordów. Śledzenie również można wyodrębnić business odpowiednie dane skojarzone z zmienne przepływu pracy. Na przykład, jeśli przepływ pracy reprezentuje kolejność przetwarzania systemu, identyfikator zamówienia wyodrębniania wraz z <xref:System.Activities.Tracking.TrackingRecord> obiektu. Ogólnie rzecz biorąc włączania WF śledzenia umożliwia diagnostyki lub danymi analiz biznesowych były dostępne z wykonywania przepływu pracy.  
  
 Śledzenie składniki są odpowiednikiem usługi śledzenia w [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)]. W [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], zwiększona wydajność i uproszczony model programowania na potrzeby funkcja śledzenia programu WF. Środowisko uruchomieniowe śledzenia instruments wystąpienia przepływu pracy, aby emitować zdarzenia związane z cyklem życia przepływu pracy, działania przepływu pracy i zdarzeń niestandardowych.  
  
 AppFabric w systemie Windows Server umożliwia także monitorowanie wykonania usług WCF i przepływ pracy. Aby uzyskać więcej informacji, zobacz [monitorowanie sieci szkieletowej aplikacji systemu Windows Server](https://go.microsoft.com/fwlink/?LinkId=201273) i [monitorowania aplikacji za pomocą programu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=201287)  
  
 Aby rozwiązać problemy środowiska wykonawczego przepływów pracy, można włączyć śledzenie przepływu pracy diagnostyki. Aby uzyskać więcej informacji, zobacz [śledzenie przepływu pracy](workflow-tracing.md).  
  
 Aby poznać model programowania, podstawowymi składnikami infrastruktury śledzenia zostały omówione w tym temacie:  
  
-   <xref:System.Activities.Tracking.TrackingRecord> obiekty emitowane przez środowisko wykonawcze przepływów pracy. Aby uzyskać więcej informacji, zobacz [rekordów śledzenia](tracking-records.md).  
  
-   <xref:System.Activities.Tracking.TrackingParticipant> Subskrybuj obiektów <xref:System.Activities.Tracking.TrackingRecord> obiektów. Uczestnicy śledzenia zawiera logikę do przetwarzania ładunku z <xref:System.Activities.Tracking.TrackingRecord> obiektów (na przykład ich można wybrać do zapisu do pliku). Aby uzyskać więcej informacji, zobacz [uczestników śledzenia](tracking-participants.md).  
  
-   <xref:System.Activities.Tracking.TrackingProfile> Obiekty filtrowania rekordów śledzenia emitowane z wystąpienia przepływu pracy. Aby uzyskać więcej informacji, zobacz [profile śledzenia](tracking-profiles.md).  
  
## <a name="workflow-tracking-infrastructure"></a>Infrastruktura śledzenia przepływu pracy  
 Infrastruktura śledzenia przepływu pracy następuje paradygmatu publikowania i subskrybowania. Wystąpienie przepływu pracy, jest wydawcą śledzenia rekordów, podczas gdy subskrybenci rekordów śledzenia są rejestrowane jako rozszerzenia do przepływu pracy. Te rozszerzenia, które subskrybują <xref:System.Activities.Tracking.TrackingRecord> obiekty są nazywane śledzenia uczestników. Śledzenie uczestników są punkty rozszerzeń, które uzyskują dostęp <xref:System.Activities.Tracking.TrackingRecord> obiektów i przetworzyć je w jakikolwiek sposób, że są one zapisywane w tym celu. Infrastruktura śledzenia umożliwia stosowanie filtru na wychodzące rekordów śledzenia, aby umożliwić uczestnika do subskrybowania podzestaw rekordów. Ten mechanizm filtrowania odbywa się za pomocą śledzenia plik profilu.  
  
 Widok wysokiego poziomu Infrastruktura śledzenia jest wyświetlany na poniższej ilustracji.  
  
 ![Infrastruktura śledzenia przepływu pracy](./media/wv.gif "WV")  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Rekordy śledzenia](tracking-records.md)  
 W tym artykule opisano rekordów śledzenia emitowane przez środowisko wykonawcze przepływów pracy.  
  
 [Profile śledzenia](tracking-profiles.md)  
 W tym artykule omówiono, jak są używane profile śledzenia.  
  
 [Uczestnicy śledzenia](tracking-participants.md)  
 Opisuje sposób używania uczestnika śledzenia dostarczane przez system lub jak utworzyć niestandardowe śledzenia uczestników.  
  
 [Konfigurowanie śledzenia dla przepływu pracy](configuring-tracking-for-a-workflow.md)  
 W tym artykule opisano sposób konfigurowania śledzenia dla przepływu pracy.  
  
 [Śledzenie przepływu pracy](workflow-tracing.md)  
 W tym artykule opisano dwa sposoby, aby włączyć śledzenie debugowania dla przepływu pracy.  
  
## <a name="see-also"></a>Zobacz także
- [Śledzenie SQL](./samples/sql-tracking.md)
