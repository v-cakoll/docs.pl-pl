---
title: Program rozpoznawania zakładek dla WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: 017c5f959ed109ffe9b5e5c4bf2b9de9d04fdcdb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964941"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a>Program rozpoznawania zakładek dla WorkflowHostingEndpoint
W tym przykładzie pokazano, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jak można użyć programu <xref:System.ServiceModel.Activities.WorkflowServiceHost> z programem w celu utworzenia wystąpień przepływu pracy.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Dyskusji  
 Ten przykład używa <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> do tworzenia wystąpień przepływu pracy hostowanych <xref:System.ServiceModel.Activities.WorkflowServiceHost>za pomocą. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>jest punktem <xref:System.ServiceModel.Activities.WorkflowServiceHost> rozszerzalności, który może być używany w następujących scenariuszach:  
  
- Tworzenie nowych wystąpień przepływu pracy.  
  
- Wznawianie zakładek w wystąpieniu przepływu pracy <xref:System.ServiceModel.Activities.WorkflowServiceHost>hostowanym w.  
  
 W dołączonym przykładowym punkcie końcowym jest udostępniany kontrakt, który zapewnia operacje tworzenia przepływu pracy i zwraca identyfikator wystąpienia lub tworzy wystąpienie o określonym IDENTYFIKATORze. Przykładowa aplikacja konsolowa tworzy <xref:System.ServiceModel.Activities.WorkflowServiceHost> wystąpienie z definicją przepływu pracy i `CreationEndpoint` dodaje do hosta. Następnie wywołuje `Create` operację w punkcie końcowym, aby utworzyć nowe wystąpienie przepływu pracy.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Skompiluj rozwiązanie.  
  
2. Uruchom aplikację. W `CreationEndpoint` konsoli programu jest wyświetlany komunikat z identyfikatorem wystąpienia podczas tworzenia wystąpienia przepływu pracy. Komunikat "Hello world!" jest drukowana przez wystąpienie przepływu pracy.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
