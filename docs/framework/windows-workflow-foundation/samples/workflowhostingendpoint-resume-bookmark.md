---
title: Wznowienie zakładki WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: 83065a0034303dcbc83f846ba455f71e954fdb54
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037764"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a>Wznowienie zakładki WorkflowHostingEndpoint
W tym przykładzie pokazano, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jak można użyć programu <xref:System.ServiceModel.Activities.WorkflowServiceHost> z programem w celu utworzenia wystąpień przepływu pracy.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Dyskusji  
 W <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> tym przykładzie użyto do utworzenia wystąpienia przepływu pracy hostowanego <xref:System.ServiceModel.Activities.WorkflowServiceHost>za pomocą. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>jest punktem <xref:System.ServiceModel.Activities.WorkflowServiceHost> rozszerzalności, który może być używany w następujących scenariuszach:  
  
- Tworzenie nowych wystąpień przepływu pracy.  
  
- Wznawianie zakładek w wystąpieniu przepływu pracy hostowanym w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
 W dołączonym przykładowym punkcie końcowym jest udostępniany kontrakt zawierający operacje umożliwiające utworzenie przepływu pracy i zwrócenie identyfikatora wystąpienia lub utworzenie wystąpienia o określonym IDENTYFIKATORze. Przykładowa aplikacja konsolowa tworzy <xref:System.ServiceModel.Activities.WorkflowServiceHost> wystąpienie z podstawową definicją przepływu pracy i `CreationEndpoint` dodaje do hosta. Następnie wywołuje `Create` operację w punkcie końcowym, aby utworzyć nowe wystąpienie przepływu pracy.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Skompiluj rozwiązanie.  
  
2. Uruchom aplikację. W `CreationEndpoint` konsoli programu jest wyświetlany komunikat z identyfikatorem wystąpienia podczas tworzenia wystąpienia przepływu pracy. Komunikat "Hello world!" jest drukowany przez przepływ pracy w przypadku pomyślnego wznowienia zakładki.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
