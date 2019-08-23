---
title: Używanie działań WF programu .NET Framework 3.0 w .NET Framework 4 przy użyciu działań Interop
ms.date: 03/30/2017
ms.assetid: 71f112ba-abb0-46f7-b05f-a5d2eb9d0c5c
ms.openlocfilehash: 3e7382b25e68c1b01bd11e015b9864ae32f25f9b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965955"
---
# <a name="using-net-framework-30-wf-activities-in-net-framework-4-with-the-interop-activity"></a>Używanie działań WF programu .NET Framework 3.0 w .NET Framework 4 przy użyciu działań Interop
Działanie to działanie (WF 4,5), [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] które otacza działanie (WF3,5)wramachprzepływupracy.[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Interop> Działanie WF 3 może być jednym działaniem typu liść lub całym drzewem działań. Wykonanie (włącznie z anulowaniem i obsługą wyjątków) i trwałość [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] działania występuje w kontekście [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] wykonywanego wystąpienia przepływu pracy.  
  
> [!NOTE]
> Działanie nie pojawia się w przyborniku projektanta przepływów pracy, chyba że projekt przepływu pracy ma ustawione ustawienie **platformy docelowej** na **.NET Framework 4,5.** <xref:System.Activities.Statements.Interop>  
  
## <a name="criteria-for-using-a-wf-3-activity-with-an-interop-activity"></a>Kryteria używania działania WF 3 z działaniem międzyoperacyjnym  
 Aby działanie WF 3 zostało pomyślnie wykonane w ramach <xref:System.Activities.Statements.Interop> działania, muszą zostać spełnione następujące kryteria:  
  
- Działanie WF 3 musi pochodzić od <xref:System.Workflow.ComponentModel.Activity?displayProperty=nameWithType>.  
  
- Działanie WF 3 musi być zadeklarowane jako `public` i nie może `abstract`być.  
  
- Działanie WF 3 musi mieć publiczny Konstruktor bez parametrów.  
  
- Ze względu na ograniczenia w typach interfejsów, <xref:System.Activities.Statements.Interop> które działanie może obsługiwać <xref:System.Workflow.Activities.HandleExternalEventActivity> , <xref:System.Workflow.Activities.CallExternalMethodActivity> i nie mogą być używane bezpośrednio, ale można użyć działań pochodnych utworzonych za pomocą narzędzia działania komunikacyjnego przepływu pracy (WCA. exe). Zobacz [narzędzia Windows Workflow Foundation](https://go.microsoft.com/fwlink/?LinkId=178889) , aby uzyskać szczegółowe informacje.  
  
## <a name="configuring-a-wf-3-activity-within-an-interop-activity"></a>Konfigurowanie działania WF 3 w działaniu międzyoperacyjnym  
 Aby skonfigurować i przekazać dane do działania WF 3 i z niego, w granicach międzyoperacyjnych, właściwości i właściwości metadanych działania WF 3 są uwidaczniane przez <xref:System.Activities.Statements.Interop> działanie. Właściwości metadanych działania WF 3 (takie jak <xref:System.Workflow.ComponentModel.Activity.Name%2A>) są udostępniane <xref:System.Activities.Statements.Interop.ActivityMetaProperties%2A> za pomocą kolekcji. Jest to kolekcja par nazwa-wartość służąca do definiowania wartości właściwości metadanych działania WF 3. Właściwość metadanych jest właściwością utworzoną przez właściwość zależności, dla której <xref:System.Workflow.ComponentModel.DependencyPropertyOptions.Metadata> ustawiono flagę.  
  
 Właściwości działania WF 3 są udostępniane za pomocą <xref:System.Activities.Statements.Interop.ActivityProperties%2A> kolekcji. Jest to zestaw par nazwa-wartość, gdzie każda wartość jest <xref:System.Activities.Argument> obiektem, służącym do definiowania argumentów dla właściwości działania WF 3. Ponieważ nie można wywnioskować kierunku właściwości działania WF 3, Każda właściwość jest podano jako <xref:System.Activities.InArgument> / <xref:System.Activities.OutArgument> para. W zależności od użycia działania właściwości można podać <xref:System.Activities.InArgument> wpis <xref:System.Activities.OutArgument> , wpis lub oba te elementy. Oczekiwana nazwa <xref:System.Activities.InArgument> wpisu w kolekcji jest nazwą właściwości, zgodnie z definicją w działaniu WF 3. Oczekiwana nazwa <xref:System.Activities.OutArgument> wpisu w kolekcji jest połączeniem nazwy właściwości i ciągu "out".  
  
## <a name="limitations-of-using-a-wf-3-activity-within-an-interop-activity"></a>Ograniczenia dotyczące używania działania WF 3 w działaniu międzyoperacyjnym  
 Działania związane z systemem WF 3 nie mogą być bezpośrednio opakowane w <xref:System.Activities.Statements.Interop> działaniu. W przypadku niektórych działań związanych z WF 3 <xref:System.Workflow.Activities.DelayActivity>, takich jak, jest to spowodowane analogicznym działaniem WF 4,5. Jest to spowodowane tym, że funkcjonalność działania nie jest obsługiwana. W przepływach pracy opakowanych przez <xref:System.Activities.Statements.Interop> działanie może być używanych wiele działań systemu WF 3, które podlegają następującym ograniczeniom:  
  
1. <xref:System.ServiceModel.Activities.Send>i <xref:System.ServiceModel.Activities.Receive> nie można używać go <xref:System.Activities.Statements.Interop> w działaniu.  
  
2. <xref:System.Workflow.Activities.WebServiceInputActivity>, <xref:System.Workflow.Activities.WebServiceOutputActivity>i <xref:System.Workflow.Activities.WebServiceFaultActivity> niemogąbyćużywane<xref:System.Activities.Statements.Interop> w ramach działania.  
  
3. <xref:System.Workflow.Activities.InvokeWorkflowActivity>nie można użyć w ramach <xref:System.Activities.Statements.Interop> działania.  
  
4. <xref:System.Workflow.ComponentModel.SuspendActivity>nie można użyć w ramach <xref:System.Activities.Statements.Interop> działania.  
  
5. Działań związanych z kompensacją nie można używać w <xref:System.Activities.Statements.Interop> ramach działania.  
  
 Istnieją również pewne specyficzne dla zachowań informacje dotyczące korzystania z działań WF 3 w ramach <xref:System.Activities.Statements.Interop> działania:  
  
1. Działania WF 3 zawarte w <xref:System.Activities.Statements.Interop> działaniu są inicjowane <xref:System.Activities.Statements.Interop> podczas wykonywania działania. W programie WF 4,5 nie istnieje faza inicjowania wystąpienia przepływu pracy przed jego wykonaniem.  
  
2. Środowisko uruchomieniowe WF 4,5 nie jest punktem kontrolnym stanu wystąpienia przepływu pracy po rozpoczęciu transakcji, niezależnie od tego, gdzie rozpoczyna się transakcja <xref:System.Activities.Statements.Interop> (wewnątrz lub na zewnątrz działania).  
  
3. Rekordy śledzenia WF 3 dla działań w ramach <xref:System.Activities.Statements.Interop> działania są udostępniane dla uczestników programu WF 4,5 śledzenie <xref:System.Activities.Tracking.InteropTrackingRecord> jako obiekty. <xref:System.Activities.Tracking.InteropTrackingRecord>jest pochodną <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
4. Działanie niestandardowe WF 3 umożliwia dostęp do danych za pomocą kolejek przepływu pracy w środowisku międzyoperacyjnym w taki sam sposób, jak w przypadku środowiska uruchomieniowego przepływu pracy WF 3. Nie są wymagane żadne zmiany kodu działania niestandardowego. Na hoście dane są przekolejkowane do kolejki przepływu pracy programu WF 3 przez wznowienie <xref:System.Activities.Bookmark>. Nazwa zakładki jest ciągiem w postaci <xref:System.IComparable> nazwy kolejki przepływu pracy.
