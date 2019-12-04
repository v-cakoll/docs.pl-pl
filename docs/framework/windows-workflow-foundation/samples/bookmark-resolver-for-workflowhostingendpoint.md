---
title: Program rozpoznawania zakładek dla WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: 99371cc64ca2790bec383b4ab5dca280d4bb9659
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716763"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a>Program rozpoznawania zakładek dla WorkflowHostingEndpoint
W tym przykładzie pokazano, jak można użyć <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> z <xref:System.ServiceModel.Activities.WorkflowServiceHost> do tworzenia wystąpień przepływu pracy.  
  
## <a name="demonstrates"></a>Przedstawia  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Dyskusji  
 Ten przykład używa <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> do tworzenia wystąpień przepływu pracy hostowanych przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jest punktem rozszerzalności dla <xref:System.ServiceModel.Activities.WorkflowServiceHost>, którego można użyć w następujących scenariuszach:  
  
- Tworzenie nowych wystąpień przepływu pracy.  
  
- Wznawianie zakładek w wystąpieniu przepływu pracy hostowanym w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
 W dołączonym przykładowym punkcie końcowym jest udostępniany kontrakt, który zapewnia operacje tworzenia przepływu pracy i zwraca identyfikator wystąpienia lub tworzy wystąpienie o określonym IDENTYFIKATORze. Przykładowa aplikacja konsolowa tworzy wystąpienie <xref:System.ServiceModel.Activities.WorkflowServiceHost> z definicją przepływu pracy i dodaje `CreationEndpoint` do hosta. Następnie wywołuje operację `Create` w punkcie końcowym, aby utworzyć nowe wystąpienie przepływu pracy.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Skompiluj rozwiązanie.  
  
2. Uruchom aplikację. W konsoli `CreationEndpoint` zostanie wyświetlony komunikat zawierający identyfikator wystąpienia podczas tworzenia wystąpienia przepływu pracy. Komunikat "Hello world!" jest drukowana przez wystąpienie przepływu pracy.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
