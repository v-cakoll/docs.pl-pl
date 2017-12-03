---
title: "Za pomocą działania WF programu .NET Framework 3.0 w programie .NET Framework 4 z działania Interop"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71f112ba-abb0-46f7-b05f-a5d2eb9d0c5c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 51f11beb474758f16c6de0c47444e0467cac8bec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="using-net-framework-30-wf-activities-in-net-framework-4-with-the-interop-activity"></a>Za pomocą działania WF programu .NET Framework 3.0 w programie .NET Framework 4 z działania Interop
<xref:System.Activities.Statements.Interop> Działanie jest [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] działania (WF 4.5), który opakowuje [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] (WF 3.5) działania w ramach [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] przepływu pracy. Działanie WF 3 może być działanie jednego typu liść lub całe drzewo działań. Wykonanie (w tym anulowania i obsługa wyjątków) i trwałość [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] działanie występuje w kontekście [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] wystąpienia przepływu pracy, który jest wykonywany.  
  
> [!NOTE]
>  <xref:System.Activities.Statements.Interop> Przybornika projektanta przepływów pracy nie ma działania, chyba że ma projektu przepływu pracy jego **platformy docelowej** ustawienie **.NET Framework 4.5**.  
  
## <a name="criteria-for-using-a-wf-3-activity-with-an-interop-activity"></a>Kryteria WF 3 działania z działania Interop  
 Dla działania WF 3 pomyślnie wykonać w ramach <xref:System.Activities.Statements.Interop> działania, muszą być spełnione następujące kryteria:  
  
-   Działanie WF 3 musi pochodzić od <xref:System.Workflow.ComponentModel.Activity?displayProperty=nameWithType>.  
  
-   Działanie WF 3 musi być zadeklarowany jako `public` i nie może być `abstract`.  
  
-   Działanie WF 3 musi mieć publicznego konstruktora domyślnego.  
  
-   Ze względu na ograniczenia w interfejsie typy, które <xref:System.Activities.Statements.Interop> działania może obsługiwać, <xref:System.Workflow.Activities.HandleExternalEventActivity> i <xref:System.Workflow.Activities.CallExternalMethodActivity> nie może być używane bezpośrednio, ale pochodnych działania utworzone za pomocą narzędzia działanie komunikacji przepływu pracy (WCA.exe) może służyć. Zobacz [narzędzia programu Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkId=178889) szczegółowe informacje.  
  
## <a name="configuring-a-wf-3-activity-within-an-interop-activity"></a>Konfigurowanie WF 3 działania w ramach działania Interop  
 Aby skonfigurować i przekazywania danych do i z działania WF 3, granicy współdziałanie, właściwości działania WF 3 i właściwości metadanych są dostępne w <xref:System.Activities.Statements.Interop> działania. Właściwości metadanych działania WF 3 (takich jak <xref:System.Workflow.ComponentModel.Activity.Name%2A>) są udostępniane za pośrednictwem <xref:System.Activities.Statements.Interop.ActivityMetaProperties%2A> kolekcji. Jest to kolekcja par nazwa wartość używane do definiowania wartości dla właściwości metadanych działania WF 3. Właściwość metadanych jest obsługiwana przez właściwości zależności, dla którego właściwością <xref:System.Workflow.ComponentModel.DependencyPropertyOptions.Metadata> flaga jest ustawiona.  
  
 Właściwości działania WF 3 dostępnych za pośrednictwem <xref:System.Activities.Statements.Interop.ActivityProperties%2A> kolekcji. Jest to zestaw par nazwa wartość, gdzie każda wartość <xref:System.Activities.Argument> obiekt używany do definiowania właściwości działania WF 3 argumenty. Ponieważ nie można wywnioskować kierunek właściwości działania WF 3, dla każdej właściwości jest wyświetlana jako <xref:System.Activities.InArgument> / <xref:System.Activities.OutArgument> pary. W zależności od użycia działania właściwości, można zapewnić <xref:System.Activities.InArgument> wpisu, <xref:System.Activities.OutArgument> wpis lub oba. Oczekiwano nazwy z <xref:System.Activities.InArgument> wpis w kolekcji jest nazwa właściwości, zgodnie z definicją w działaniu WF 3. Oczekiwano nazwy z <xref:System.Activities.OutArgument> wpis w kolekcji jest złączeniem nazwy właściwości oraz ciąg "Out".  
  
## <a name="limitations-of-using-a-wf-3-activity-within-an-interop-activity"></a>Ograniczenia używania WF 3 działania w ramach działania Interop  
 Działania WF 3 dostarczane przez system nie może być bezpośrednio ujęte w <xref:System.Activities.Statements.Interop> działania. W przypadku niektórych działań WF 3 takich jak <xref:System.Workflow.Activities.DelayActivity>, ponieważ jest analogiczna działania WF 4.5. Dla innych osób wynika to funkcja działania nie jest obsługiwana. Wiele działań WF 3 dostarczane przez system może być używana w przepływach pracy za <xref:System.Activities.Statements.Interop> działania może ulec następujące ograniczenia:  
  
1.  <xref:System.ServiceModel.Activities.Send>i <xref:System.ServiceModel.Activities.Receive> nie można używać w <xref:System.Activities.Statements.Interop> działania.  
  
2.  <xref:System.Workflow.Activities.WebServiceInputActivity>, <xref:System.Workflow.Activities.WebServiceOutputActivity>, i <xref:System.Workflow.Activities.WebServiceFaultActivity> nie można używać wewnątrz <xref:System.Activities.Statements.Interop> działania.  
  
3.  <xref:System.Workflow.Activities.InvokeWorkflowActivity>Nie można używać wewnątrz <xref:System.Activities.Statements.Interop> działania.  
  
4.  <xref:System.Workflow.ComponentModel.SuspendActivity>Nie można używać wewnątrz <xref:System.Activities.Statements.Interop> działania.  
  
5.  Działania związane z kompensacji nie można używać wewnątrz <xref:System.Activities.Statements.Interop> działania.  
  
 Dostępne są także niektóre szczegóły zachowania informacje dotyczące używania działań WF 3 w ramach <xref:System.Activities.Statements.Interop> działania:  
  
1.  WF 3 działań zawartych w <xref:System.Activities.Statements.Interop> działania są kiedy zainicjowana <xref:System.Activities.Statements.Interop> wykonaniu działania. W WF 4.5 nie ma żadnych faza inicjowania wystąpienia przepływu pracy przed jego wykonywania.  
  
2.  Środowisko uruchomieniowe WF 4.5 nie nie punkt kontrolny stanu wystąpienia przepływu pracy, gdy rozpoczyna transakcją, niezależnie od tego, w którym rozpoczyna się tej transakcji (wewnątrz lub poza <xref:System.Activities.Statements.Interop> działania).  
  
3.  Rekordy 3 śledzenia WF dla działań w ramach <xref:System.Activities.Statements.Interop> działania są dostarczane do uczestników śledzenia WF 4.5 jako <xref:System.Activities.Tracking.InteropTrackingRecord> obiektów. <xref:System.Activities.Tracking.InteropTrackingRecord>jest pochodną elementu <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
4.  Niestandardowe działanie WF 3 można uzyskać dostępu do danych za pomocą kolejek przepływu pracy w środowisku współdziałanie w taki sam sposób jak w ramach środowiska uruchomieniowego przepływu pracy WF 3. Zmiany kodu niestandardowego działania, nie są wymagane. Na hoście, dane są dodawane do kolejki do kolejki przepływu pracy WF 3 za wznawianie <xref:System.Activities.Bookmark>. Nazwa zakładki jest formę ciągu <xref:System.IComparable> Nazwa kolejki przepływu pracy.  
  
## <a name="see-also"></a>Zobacz też  
 [Przy użyciu platformy .NET Framework 3.0 lub .NET Framework 3.5 działania w przepływie pracy .NET Framework 4.5](../../../docs/framework/windows-workflow-foundation/samples/using-a-net-3-0-or-net-3-5-activity-in-a-net-4-5-workflow.md)
