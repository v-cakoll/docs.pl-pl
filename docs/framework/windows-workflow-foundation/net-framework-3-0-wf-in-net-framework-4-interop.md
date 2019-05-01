---
title: Używanie działań WF programu .NET Framework 3.0 w .NET Framework 4 przy użyciu działań Interop
ms.date: 03/30/2017
ms.assetid: 71f112ba-abb0-46f7-b05f-a5d2eb9d0c5c
ms.openlocfilehash: 33140ac85cd50140c0aa34d1986365fefc005c78
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934722"
---
# <a name="using-net-framework-30-wf-activities-in-net-framework-4-with-the-interop-activity"></a>Używanie działań WF programu .NET Framework 3.0 w .NET Framework 4 przy użyciu działań Interop
<xref:System.Activities.Statements.Interop> Działanie jest [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] działania (WF 4.5), który otacza [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] (WF 3.5) działania w ramach [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] przepływu pracy. Działanie WF 3 może być czynnością pojedynczego typu liść lub całe drzewo działań. Wykonanie (w tym unieważnienie i obsługa wyjątków) oraz trwałości [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] działanie występuje w kontekście [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] wystąpienia przepływu pracy, który jest wykonywany.  
  
> [!NOTE]
>  <xref:System.Activities.Statements.Interop> w przyborniku projektanta przepływu pracy nie ma działania, chyba że projekt przepływu pracy ma jego **platformę docelową** ustawienie **.NET Framework 4.5**.  
  
## <a name="criteria-for-using-a-wf-3-activity-with-an-interop-activity"></a>Kryteria WF 3 działanie przy użyciu działań Interop  
 Działania WF 3 pomyślnie wykonać w ramach <xref:System.Activities.Statements.Interop> działania muszą być spełnione następujące kryteria:  
  
- Działanie WF 3 musi pochodzić od klasy <xref:System.Workflow.ComponentModel.Activity?displayProperty=nameWithType>.  
  
- Działanie WF 3 musi być zadeklarowany jako `public` i nie może być `abstract`.  
  
- Działanie WF 3 musi mieć publicznego konstruktora domyślnego.  
  
- Ze względu na ograniczenia w interfejsie typy, które <xref:System.Activities.Statements.Interop> działanie może obsługiwać, <xref:System.Workflow.Activities.HandleExternalEventActivity> i <xref:System.Workflow.Activities.CallExternalMethodActivity> nie może być używany bezpośrednio, ale pochodnych działań utworzonych za pomocą narzędzia działania komunikacji przepływu pracy (WCA.exe) może służyć. Zobacz [narzędzia programu Windows Workflow Foundation](https://go.microsoft.com/fwlink/?LinkId=178889) Aby uzyskać szczegółowe informacje.  
  
## <a name="configuring-a-wf-3-activity-within-an-interop-activity"></a>Konfigurowanie WF 3 działania w ramach działań Interop  
 Aby skonfigurować i przekazać dane do i z działania programu WF 3, wewnątrz międzyoperacyjnej granicy, właściwości i metadanych właściwości działania WF 3 są udostępniane przez <xref:System.Activities.Statements.Interop> działania. Działanie WF 3 właściwości metadanych (takie jak <xref:System.Workflow.ComponentModel.Activity.Name%2A>) są udostępniane za pośrednictwem <xref:System.Activities.Statements.Interop.ActivityMetaProperties%2A> kolekcji. Jest to kolekcja par nazwa wartość używanych do definiowania wartości dla właściwości metadanych działanie WF 3. Właściwość metadanych jest wspierana przez właściwość zależności, dla którego właściwość <xref:System.Workflow.ComponentModel.DependencyPropertyOptions.Metadata> flaga jest ustawiona.  
  
 Właściwości działania WF 3 są udostępniane za pośrednictwem <xref:System.Activities.Statements.Interop.ActivityProperties%2A> kolekcji. Jest to zestaw par nazwa wartość, gdzie każda wartość jest <xref:System.Activities.Argument> obiekt, używany do definiowania argumenty dla właściwości działania WF 3. Ponieważ nie można wywnioskować kierunek właściwości działania WF 3, dla każdej właściwości jest wyświetlana jako <xref:System.Activities.InArgument> / <xref:System.Activities.OutArgument> pary. Minimalnie działania właściwości, możesz chcieć zapewnić <xref:System.Activities.InArgument> wpisu <xref:System.Activities.OutArgument> wpisu lub obu. Oczekiwano nazwy z <xref:System.Activities.InArgument> wpis w kolekcji jest nazwa właściwości, zgodnie z definicją w działaniu WF 3. Oczekiwano nazwy z <xref:System.Activities.OutArgument> wpis w kolekcji jest łączenie nazwy właściwości i parametrów "Out".  
  
## <a name="limitations-of-using-a-wf-3-activity-within-an-interop-activity"></a>Ograniczenia przy użyciu WF 3 działania w ramach działań Interop  
 Działania WF 3 dostarczane przez system nie może być bezpośrednio ujęte w <xref:System.Activities.Statements.Interop> działania. W przypadku niektórych działań WF 3 takich jak <xref:System.Workflow.Activities.DelayActivity>, jest to spowodowane jest analogiczne działanie WF 4.5. Dla innych użytkowników jest to spowodowane funkcjonalność działania nie jest obsługiwana. Wiele działań WF 3 dostarczane przez system mogą być używane w przepływach pracy opakowane przez <xref:System.Activities.Statements.Interop> działania podlegają następującym ograniczeniom:  
  
1. <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Receive> nie można używać w <xref:System.Activities.Statements.Interop> działania.  
  
2. <xref:System.Workflow.Activities.WebServiceInputActivity>, <xref:System.Workflow.Activities.WebServiceOutputActivity>, i <xref:System.Workflow.Activities.WebServiceFaultActivity> nie można używać wewnątrz <xref:System.Activities.Statements.Interop> działania.  
  
3. <xref:System.Workflow.Activities.InvokeWorkflowActivity> Nie można używać wewnątrz <xref:System.Activities.Statements.Interop> działania.  
  
4. <xref:System.Workflow.ComponentModel.SuspendActivity> Nie można używać wewnątrz <xref:System.Activities.Statements.Interop> działania.  
  
5. Działań dotyczących wynagrodzenie, nie można używać wewnątrz <xref:System.Activities.Statements.Interop> działania.  
  
 Dostępne są także niektóre zachowania charakterystyki informacje dotyczące używania działań WF 3 w ramach <xref:System.Activities.Statements.Interop> działania:  
  
1. WF 3 działań zawartych w <xref:System.Activities.Statements.Interop> działania są inicjowane, gdy <xref:System.Activities.Statements.Interop> jest wykonywane działanie. W programie WF 4.5 ma nie fazy inicjowania dla wystąpienia przepływu pracy, przed jej wykonanie.  
  
2. Środowisko uruchomieniowe programu WF 4.5 jest nie punktu kontrolnego stanu wystąpienia przepływu pracy, po rozpoczęciu transakcji, niezależnie od tego, gdzie rozpoczyna się w tej transakcji (wewnątrz lub poza <xref:System.Activities.Statements.Interop> działanie).  
  
3. Rekordy śledzenia 3 WF działań w ramach <xref:System.Activities.Statements.Interop> działania zostały udostępnione firmie WF 4.5 śledzenia uczestników jako <xref:System.Activities.Tracking.InteropTrackingRecord> obiektów. <xref:System.Activities.Tracking.InteropTrackingRecord> jest pochodną z <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
4. Niestandardowe działanie WF 3 mogą uzyskać dostęp do danych przy użyciu funkcji kolejek przepływu pracy w środowisku współdziałanie w taki sam sposób jak w ramach środowiska uruchomieniowego przepływu pracy WF 3. Wymagane są bez zmian w kodzie działań niestandardowych. Na tym hoście danych polega na umieszczonych w kolejce do kolejki przepływu pracy WF 3 wznawianie <xref:System.Activities.Bookmark>. Nazwa zakładki jest to forma ciągu <xref:System.IComparable> Nazwa kolejki przepływu pracy.
