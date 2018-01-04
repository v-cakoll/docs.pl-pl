---
title: "Określanie czas wykonywania przepływu pracy za pomocą śledzenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f04ad0fd-edc7-4cbc-8979-356f2a1131c4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f2687d045db28974e99b2f2b6a3222924a520720
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="determining-workflow-execution-duration-using-tracing"></a>Określanie czas wykonywania przepływu pracy za pomocą śledzenia
W tym temacie pokazano, jak określić czas potrzebny pomyślnie zakończono, hostowanie Samoobsługowe przepływu pracy można wykonać za pomocą śledzenia przepływu pracy.  
  
### <a name="to-determine-workflow-application-execution-duration-by-using-workflow-tracing"></a>Aby określić czas wykonywania aplikacji przepływu pracy za pomocą śledzenia przepływu pracy  
  
1.  Otwórz [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  Wybierz **pliku**, **nowe**, **projektu**.  W obszarze **C#**, wybierz pozycję **przepływu pracy** węzła.  Wybierz **Aplikacja konsoli przepływu pracy** z listy szablonów.  Nazwa nowego projektu `WorkflowDurationTracing` i kliknij przycisk **OK**.  
  
2.  Otwórz Workflow1.xaml.  Przeciągnij <xref:System.Activities.Statements.Delay> działania na powierzchnię projektanta. Wartość 00:00:10 (dziesięć sekund) należy przypisać do właściwości Duration działania.  
  
3.  Otwórz Podgląd zdarzeń, klikając **Start**, **Uruchom**i wprowadzając `eventvwr.exe`.  
  
4.  Jeśli nie zostało włączone śledzenie przepływu pracy, rozwiń **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji serwera aplikacji** . Wybierz **widoku**, **wyświetlanie analityczne i debugowania dzienniki**. Kliknij prawym przyciskiem myszy **debugowania** i wybierz **Włącz dziennik**. Pozostaw otwarte Podgląd zdarzeń, tak aby po uruchomieniu przepływu pracy można wyświetlać danych śledzenia.  
  
5.  Uruchom aplikację przepływu pracy, naciskając klawisze CTRL + SHIFT + B.  
  
6.  W Podglądzie zdarzeń Znajdź ostatnie zdarzenie o identyfikatorze 1009 i komunikat podobny do następującego. Zanotuj czasie rejestrowania komunikatu.  
  
 **Działanie nadrzędne ", nazwa wyświetlana: '', identyfikator wystąpienia:" podrzędnych zaplanowanego działania "WorkflowDurationTracking.Workflow1", nazwa wyświetlana: "Workflow1", identyfikator wystąpienia: "1".**  
  
7.  Znajdź inne ostatnie zdarzenie o identyfikatorze 1001 i komunikat podobny do następującego.  Odejmowanie poprzedniej czas komunikatu z wartość zarejestrowane ten komunikat, aby określić czas wykonywania przepływu pracy, która powinna być około 10 sekund.  
  
 **Obiekt WorkflowInstance o identyfikatorze: "1bbac57b-3322-498e-9e27-8833fda3a5bf" zostało zakończone w stanie zamkniętym.**  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md)  
 [Windows Server AppFabric monitorowania](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorowanie aplikacji przy użyciu rozwiązania AppFabric](http://go.microsoft.com/fwlink/?LinkId=201275)
