---
title: Omówienie programu Windows Workflow
ms.date: 03/30/2017
ms.assetid: fc44adbe-1412-49ae-81af-0298be44aae6
ms.openlocfilehash: ada5ec75d130c9c518c5129db6c12b61c3acbf45
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802534"
---
# <a name="windows-workflow-overview"></a>Omówienie programu Windows Workflow
Przepływ pracy to zbiór jednostek elementów o nazwie *działania* , które są przechowywane jako model, który opisuje proces rzeczywisty. Przepływy pracy umożliwiają opisywanie kolejności wykonywania i zależności zależnych od elementów pracy krótko-lub długotrwałej. Ta praca przechodzi przez model od początku do końca, a działania mogą być wykonywane przez osoby lub funkcje systemowe.  
  
## <a name="workflow-run-time-engine"></a>Aparat czasu wykonywania przepływu pracy  
 Każde uruchomione wystąpienie przepływu pracy jest tworzone i utrzymywane przez przetwarzany przez proces aparat czasu wykonywania, który współdziała z procesem hosta za pomocą jednego z następujących elementów:  
  
- <xref:System.Activities.WorkflowInvoker>, który wywołuje przepływ pracy jako metodę.  
  
- <xref:System.Activities.WorkflowApplication> dla jawnej kontroli nad wykonywaniem pojedynczego wystąpienia przepływu pracy.  
  
- <xref:System.ServiceModel.WorkflowServiceHost> dla interakcji opartych na komunikatach w scenariuszach obejmujących wiele wystąpień.  
  
 Każda z tych klas otacza podstawowe środowisko uruchomieniowe działania reprezentowane jako <xref:System.Activities.ActivityInstance> odpowiedzialne za wykonywanie działania. Może istnieć kilka <xref:System.Activities.ActivityInstance> obiektów w domenie aplikacji uruchomionych współbieżnie.  
  
 Każdy z powyższych trzech obiektów interakcji hosta jest tworzony na podstawie drzewa działań, zwanego programem przepływu pracy. Korzystając z tych typów lub niestandardowego hosta, który zawija <xref:System.Activities.ActivityInstance>, przepływy pracy mogą być wykonywane w dowolnym procesie systemu Windows, w tym aplikacje konsolowe, aplikacje oparte na formularzach, usługi systemu Windows, witryny sieci Web ASP.NET oraz usługi Windows Communication Foundation (WCF).  
  
 ![Składniki przepływu pracy w procesie hosta](./media/44c79d1d-178b-4487-87ed-3e33015a3842.gif "44c79d1d-178b-4487-87ed-3e33015a3842")  
Składniki przepływu pracy w procesie hosta  
  
## <a name="interaction-between-workflow-components"></a>Interakcja między składnikami przepływu pracy  
 Na poniższym diagramie pokazano, jak składniki przepływu pracy współdziałają ze sobą.  
  
 ![Diagram przedstawiający sposób działania składników przepływu pracy.](./media/overview/workflow-component-interatction.gif)  
  
 Na powyższym diagramie Metoda <xref:System.Activities.WorkflowInvoker.Invoke%2A> klasy <xref:System.Activities.WorkflowInvoker> służy do wywoływania kilku wystąpień przepływu pracy. <xref:System.Activities.WorkflowInvoker> jest używany w przypadku lekkich przepływów pracy, które nie wymagają zarządzania z hosta; przepływy pracy, które wymagają zarządzania z hosta (takie jak <xref:System.Activities.Bookmark> wznawiania), muszą być wykonywane przy użyciu <xref:System.Activities.WorkflowApplication.Run%2A> zamiast tego. Nie jest wymagane oczekiwanie na ukończenie jednego wystąpienia przepływu pracy przed wywołaniem innego elementu; aparat środowiska uruchomieniowego obsługuje jednoczesne uruchamianie wielu wystąpień przepływu pracy.  Wywoływane przepływy pracy są następujące:  
  
- Działanie <xref:System.Activities.Statements.Sequence>, które zawiera <xref:System.Activities.Statements.WriteLine> działania podrzędnego. <xref:System.Activities.Variable> działania nadrzędnego jest powiązany z <xref:System.Activities.InArgument> działania podrzędnego. Aby uzyskać więcej informacji na temat zmiennych, argumentów i powiązań, zobacz [zmienne i argumenty](variables-and-arguments.md).  
  
- Działanie niestandardowe o nazwie `ReadLine`. <xref:System.Activities.OutArgument> działania `ReadLine` są zwracane do metody wywoływania <xref:System.Activities.WorkflowInvoker.Invoke%2A>.  
  
- Działanie niestandardowe, które pochodzi od klasy abstrakcyjnej <xref:System.Activities.CodeActivity>. <xref:System.Activities.CodeActivity> może uzyskać dostęp do funkcji czasu wykonywania (takich jak śledzenie i właściwości) przy użyciu <xref:System.Activities.CodeActivityContext>, który jest dostępny jako parametr metody <xref:System.Activities.CodeActivity.Execute%2A>. Aby uzyskać więcej informacji na temat tych funkcji w czasie wykonywania, zobacz [śledzenie przepływu pracy i](workflow-tracking-and-tracing.md) [właściwości wykonywania przepływu pracy](workflow-execution-properties.md).  
  
## <a name="see-also"></a>Zobacz także

- [BizTalk Server 2006 czy WF? Wybieranie odpowiedniego narzędzia przepływu pracy dla projektu](https://docs.microsoft.com/previous-versions/dotnet/articles/cc303238(v=msdn.10))
