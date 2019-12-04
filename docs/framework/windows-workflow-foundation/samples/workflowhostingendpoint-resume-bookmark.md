---
title: Wznowienie zakładki WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: 3b3c7d40a70e797960837c82e2f5a08b2814e17f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710965"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a>Wznowienie zakładki WorkflowHostingEndpoint
W tym przykładzie pokazano, jak można użyć <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> z <xref:System.ServiceModel.Activities.WorkflowServiceHost> do tworzenia wystąpień przepływu pracy.  
  
## <a name="demonstrates"></a>Przedstawia  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Dyskusji  
 W tym przykładzie użyto <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, aby utworzyć wystąpienie przepływu pracy hostowane przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jest punktem rozszerzalności dla <xref:System.ServiceModel.Activities.WorkflowServiceHost>, którego można użyć w następujących scenariuszach:  
  
- Tworzenie nowych wystąpień przepływu pracy.  
  
- Wznawianie zakładek w wystąpieniu przepływu pracy hostowanym w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
 W dołączonym przykładowym punkcie końcowym jest udostępniany kontrakt zawierający operacje umożliwiające utworzenie przepływu pracy i zwrócenie identyfikatora wystąpienia lub utworzenie wystąpienia o określonym IDENTYFIKATORze. Przykładowa aplikacja konsolowa tworzy wystąpienie <xref:System.ServiceModel.Activities.WorkflowServiceHost> z podstawową definicją przepływu pracy i dodaje `CreationEndpoint` do hosta. Następnie wywołuje operację `Create` w punkcie końcowym, aby utworzyć nowe wystąpienie przepływu pracy.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Skompiluj rozwiązanie.  
  
2. Uruchom aplikację. W konsoli `CreationEndpoint` zostanie wyświetlony komunikat zawierający identyfikator wystąpienia podczas tworzenia wystąpienia przepływu pracy. Komunikat "Hello world!" jest drukowany przez przepływ pracy w przypadku pomyślnego wznowienia zakładki.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
