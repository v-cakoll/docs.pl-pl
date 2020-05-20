---
title: Omówienie programu Windows Workflow
description: W tym artykule opisano przepływy pracy programu Workflow Foundation, które są modelami opisującymi procesy w świecie rzeczywistym.
ms.date: 03/30/2017
ms.assetid: fc44adbe-1412-49ae-81af-0298be44aae6
ms.openlocfilehash: ec1a00b37abe2cb842735fb98e1c113a97943758
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421478"
---
# <a name="windows-workflow-overview"></a>Omówienie programu Windows Workflow
Przepływ pracy to zbiór jednostek elementów o nazwie *działania* , które są przechowywane jako model, który opisuje proces rzeczywisty. Przepływy pracy umożliwiają opisywanie kolejności wykonywania i zależności zależnych od elementów pracy krótko-lub długotrwałej. Ta praca przechodzi przez model od początku do końca, a działania mogą być wykonywane przez osoby lub funkcje systemowe.  
  
## <a name="workflow-run-time-engine"></a>Aparat czasu wykonywania przepływu pracy  
 Każde uruchomione wystąpienie przepływu pracy jest tworzone i utrzymywane przez przetwarzany przez proces aparat czasu wykonywania, który współdziała z procesem hosta za pomocą jednego z następujących elementów:  
  
- A <xref:System.Activities.WorkflowInvoker> , który wywołuje przepływ pracy jako metodę.  
  
- A <xref:System.Activities.WorkflowApplication> dla jawnej kontroli nad wykonywaniem pojedynczego wystąpienia przepływu pracy.  
  
- A w <xref:System.ServiceModel.WorkflowServiceHost> przypadku interakcji opartych na komunikatach w scenariuszach obejmujących wiele wystąpień.  
  
 Każda z tych klas otacza podstawowe środowisko uruchomieniowe działania reprezentowane jako <xref:System.Activities.ActivityInstance> odpowiedzialne za wykonywanie działania. Może istnieć kilka <xref:System.Activities.ActivityInstance> obiektów w domenie aplikacji uruchomionych współbieżnie.  
  
 Każdy z powyższych trzech obiektów interakcji hosta jest tworzony na podstawie drzewa działań, zwanego programem przepływu pracy. Korzystając z tych typów lub niestandardowego hosta, który zawija <xref:System.Activities.ActivityInstance> , przepływy pracy mogą być wykonywane wewnątrz dowolnego procesu systemu Windows, w tym aplikacji konsolowych, aplikacji opartych na formularzach, usług systemu Windows, witryn sieci Web ASP.NET oraz usług Windows Communication Foundation (WCF).  
  
 ![Składniki przepływu pracy w procesie hosta](./media/44c79d1d-178b-4487-87ed-3e33015a3842.gif "44c79d1d-178b-4487-87ed-3e33015a3842")  
Składniki przepływu pracy w procesie hosta  
  
## <a name="interaction-between-workflow-components"></a>Interakcja między składnikami przepływu pracy  
 Na poniższym diagramie pokazano, jak składniki przepływu pracy współdziałają ze sobą.  
  
 ![Diagram przedstawiający sposób działania składników przepływu pracy.](./media/overview/workflow-component-interatction.gif)  
  
 Na powyższym diagramie <xref:System.Activities.WorkflowInvoker.Invoke%2A> Metoda <xref:System.Activities.WorkflowInvoker> klasy jest używana do wywołania kilku wystąpień przepływu pracy. <xref:System.Activities.WorkflowInvoker>służy do obsługi uproszczonych przepływów pracy, które nie wymagają zarządzania z hosta; przepływy pracy, które wymagają zarządzania z hosta (takie jak <xref:System.Activities.Bookmark> wznowienie), muszą być wykonywane przy użyciu <xref:System.Activities.WorkflowApplication.Run%2A> zamiast tego. Nie jest wymagane oczekiwanie na ukończenie jednego wystąpienia przepływu pracy przed wywołaniem innego elementu; aparat środowiska uruchomieniowego obsługuje jednoczesne uruchamianie wielu wystąpień przepływu pracy.  Wywoływane przepływy pracy są następujące:  
  
- <xref:System.Activities.Statements.Sequence>Działanie zawierające <xref:System.Activities.Statements.WriteLine> działanie podrzędne. <xref:System.Activities.Variable>Działanie elementu nadrzędnego jest powiązane z <xref:System.Activities.InArgument> działaniem podrzędnym. Aby uzyskać więcej informacji na temat zmiennych, argumentów i powiązań, zobacz [zmienne i argumenty](variables-and-arguments.md).  
  
- Działanie niestandardowe o nazwie `ReadLine` . <xref:System.Activities.OutArgument> `ReadLine` Działanie jest zwracane do metody wywołującej <xref:System.Activities.WorkflowInvoker.Invoke%2A> .  
  
- Działanie niestandardowe, które pochodzi od <xref:System.Activities.CodeActivity> klasy abstrakcyjnej. <xref:System.Activities.CodeActivity>Może uzyskać dostęp do funkcji czasu wykonywania (takich jak śledzenie i właściwości) przy użyciu <xref:System.Activities.CodeActivityContext> , który jest dostępny jako parametr <xref:System.Activities.CodeActivity.Execute%2A> metody. Aby uzyskać więcej informacji na temat tych funkcji w czasie wykonywania, zobacz [śledzenie przepływu pracy i](workflow-tracking-and-tracing.md) [właściwości wykonywania przepływu pracy](workflow-execution-properties.md).  
  
## <a name="see-also"></a>Zobacz także

- [BizTalk Server 2006 czy WF? Wybieranie odpowiedniego narzędzia przepływu pracy dla projektu](https://docs.microsoft.com/previous-versions/dotnet/articles/cc303238(v=msdn.10))
