---
title: Używanie działań WF programu .NET Framework 3.0 w .NET Framework 4 przy użyciu działań Interop
ms.date: 03/30/2017
ms.assetid: 71f112ba-abb0-46f7-b05f-a5d2eb9d0c5c
ms.openlocfilehash: de0a0474f0a996ce8c781064f56c03b483ca1bb9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283196"
---
# <a name="using-net-framework-30-wf-activities-in-net-framework-4-with-the-interop-activity"></a>Używanie działań WF programu .NET Framework 3.0 w .NET Framework 4 przy użyciu działań Interop
Działanie <xref:System.Activities.Statements.Interop> to działanie [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] (WF 4,5), które otacza działanie .NET Framework 3,5 (WF 3,5) w ramach przepływu pracy [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]. Działanie WF 3 może być jednym działaniem typu liść lub całym drzewem działań. Wykonanie (w tym operacje anulowania i obsługi wyjątków) i trwałość działania .NET Framework 3,5 odbywa się w kontekście wykonywania [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]go wystąpienia przepływu pracy.  
  
> [!NOTE]
> Działanie <xref:System.Activities.Statements.Interop> nie jest wyświetlane w przyborniku projektanta przepływów pracy, chyba że dla projektu przepływu pracy ustawiono ustawienie **platformy docelowej** **.NET Framework 4,5**.  
  
## <a name="criteria-for-using-a-wf-3-activity-with-an-interop-activity"></a>Kryteria używania działania WF 3 z działaniem międzyoperacyjnym  
 Aby działanie WF 3 zostało pomyślnie wykonane w ramach działania <xref:System.Activities.Statements.Interop>, muszą zostać spełnione następujące kryteria:  
  
- Działanie WF 3 musi pochodzić od <xref:System.Workflow.ComponentModel.Activity?displayProperty=nameWithType>.  
  
- Działanie WF 3 musi być zadeklarowane jako `public` i nie może być `abstract`.  
  
- Działanie WF 3 musi mieć publiczny Konstruktor bez parametrów.  
  
- Ze względu na ograniczenia w typach interfejsów obsługiwanych przez działanie <xref:System.Activities.Statements.Interop>, <xref:System.Workflow.Activities.HandleExternalEventActivity> i <xref:System.Workflow.Activities.CallExternalMethodActivity> nie mogą być używane bezpośrednio, ale można użyć działań pochodnych utworzonych za pomocą narzędzia działania komunikacyjnego przepływu pracy (WCA. exe). Zobacz [narzędzia Windows Workflow Foundation](https://go.microsoft.com/fwlink/?LinkId=178889) , aby uzyskać szczegółowe informacje.  
  
## <a name="configuring-a-wf-3-activity-within-an-interop-activity"></a>Konfigurowanie działania WF 3 w działaniu międzyoperacyjnym  
 Aby skonfigurować i przekazać dane do działania programu WF 3 i z niego z niej, w granicach międzyoperacyjnych właściwości działania WF 3 i właściwości metadanych są uwidaczniane przez działanie <xref:System.Activities.Statements.Interop>. Właściwości metadanych działania WF 3 (takie jak <xref:System.Workflow.ComponentModel.Activity.Name%2A>) są uwidaczniane przez kolekcję <xref:System.Activities.Statements.Interop.ActivityMetaProperties%2A>. Jest to kolekcja par nazwa-wartość służąca do definiowania wartości właściwości metadanych działania WF 3. Właściwość metadanych jest właściwością utworzoną przez właściwość zależności, dla której ustawiono flagę <xref:System.Workflow.ComponentModel.DependencyPropertyOptions.Metadata>.  
  
 Właściwości działania WF 3 są udostępniane za pomocą kolekcji <xref:System.Activities.Statements.Interop.ActivityProperties%2A>. Jest to zestaw par nazwa-wartość, gdzie każda wartość jest obiektem <xref:System.Activities.Argument> używanym do definiowania argumentów dla właściwości działania WF 3. Ponieważ nie można wywnioskować kierunku właściwości działania WF 3, Każda właściwość jest podano jako para <xref:System.Activities.InArgument>/<xref:System.Activities.OutArgument>. W zależności od użycia właściwości można podać wpis <xref:System.Activities.InArgument>, wpis <xref:System.Activities.OutArgument> lub oba te elementy. Oczekiwana Nazwa wpisu <xref:System.Activities.InArgument> w kolekcji jest nazwą właściwości, zgodnie z definicją w działaniu WF 3. Oczekiwana Nazwa wpisu <xref:System.Activities.OutArgument> w kolekcji jest połączeniem nazwy właściwości i ciągu "out".  
  
## <a name="limitations-of-using-a-wf-3-activity-within-an-interop-activity"></a>Ograniczenia dotyczące używania działania WF 3 w działaniu międzyoperacyjnym  
 Działania związane z systemem WF 3 nie mogą być bezpośrednio opakowane w działanie <xref:System.Activities.Statements.Interop>. W przypadku niektórych działań WF 3, takich jak <xref:System.Workflow.Activities.DelayActivity>, dzieje się tak, ponieważ istnieje analogiczne działanie WF 4,5. Jest to spowodowane tym, że funkcjonalność działania nie jest obsługiwana. W przepływach pracy opakowanych przez działanie <xref:System.Activities.Statements.Interop> mogą być używane wiele działań systemu WF 3, które podlegają następującym ograniczeniom:  
  
1. <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Receive> nie mogą być używane w działaniu <xref:System.Activities.Statements.Interop>.  
  
2. <xref:System.Workflow.Activities.WebServiceInputActivity>, <xref:System.Workflow.Activities.WebServiceOutputActivity>i <xref:System.Workflow.Activities.WebServiceFaultActivity> nie mogą być używane w ramach działania <xref:System.Activities.Statements.Interop>.  
  
3. nie można użyć <xref:System.Workflow.Activities.InvokeWorkflowActivity> w działaniu <xref:System.Activities.Statements.Interop>.  
  
4. nie można użyć <xref:System.Workflow.ComponentModel.SuspendActivity> w działaniu <xref:System.Activities.Statements.Interop>.  
  
5. Działań związanych z kompensacją nie można używać w ramach działania <xref:System.Activities.Statements.Interop>.  
  
 Istnieją również pewne specyficzne dla zachowań informacje dotyczące korzystania z działań WF 3 w ramach działania <xref:System.Activities.Statements.Interop>:  
  
1. Działania WF 3 zawarte w działaniu <xref:System.Activities.Statements.Interop> są inicjowane, gdy działanie <xref:System.Activities.Statements.Interop> zostanie wykonane. W programie WF 4,5 nie istnieje faza inicjowania wystąpienia przepływu pracy przed jego wykonaniem.  
  
2. Środowisko uruchomieniowe WF 4,5 nie jest punktem kontrolnym stanu wystąpienia przepływu pracy po rozpoczęciu transakcji, niezależnie od tego, gdzie rozpoczyna się transakcja (wewnątrz lub na zewnątrz działania <xref:System.Activities.Statements.Interop>).  
  
3. Rekordy śledzenia WF 3 dla działań w ramach działania <xref:System.Activities.Statements.Interop> są udostępniane dla uczestników śledzenia WF 4,5 jako obiektów <xref:System.Activities.Tracking.InteropTrackingRecord>. <xref:System.Activities.Tracking.InteropTrackingRecord> jest pochodną <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
4. Działanie niestandardowe WF 3 umożliwia dostęp do danych za pomocą kolejek przepływu pracy w środowisku międzyoperacyjnym w taki sam sposób, jak w przypadku środowiska uruchomieniowego przepływu pracy WF 3. Nie są wymagane żadne zmiany kodu działania niestandardowego. Na hoście dane są przekolejkowane do kolejki przepływu pracy programu WF 3 przez wznowienie <xref:System.Activities.Bookmark>. Nazwa zakładki to ciąg w postaci ciągu nazwy kolejki przepływu pracy <xref:System.IComparable>.
