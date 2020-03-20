---
title: Program rozpoznawania zakładek dla WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: 113e6e52214d482dcd733bbd07ef2aab9f1b8c3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142813"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a>Program rozpoznawania zakładek dla WorkflowHostingEndpoint
W tym przykładzie <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> pokazano, <xref:System.ServiceModel.Activities.WorkflowServiceHost> jak można używać do tworzenia wystąpień przepływu pracy.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Dyskusji  
 W tym przykładzie użyto do <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> utworzenia <xref:System.ServiceModel.Activities.WorkflowServiceHost>wystąpień przepływu pracy hostowanych przy użyciu programu . <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>jest punktem rozszerzalności, który <xref:System.ServiceModel.Activities.WorkflowServiceHost> może być używany w następujących scenariuszach:  
  
- Tworzenie nowych wystąpień przepływu pracy.  
  
- Wznowienie zakładek w wystąpieniu przepływu pracy <xref:System.ServiceModel.Activities.WorkflowServiceHost>hostowanym w pliku .  
  
 Przykładowy punkt końcowy, który jest uwzględniony udostępnia kontrakt, który udostępnia operacje w celu utworzenia przepływu pracy i zwraca identyfikator wystąpienia lub tworzy wystąpienie o określonym identyfikatorze. Przykładowa aplikacja konsoli <xref:System.ServiceModel.Activities.WorkflowServiceHost> tworzy wystąpienie z definicją przepływu pracy i dodaje `CreationEndpoint` do hosta. Następnie wywołuje `Create` operację w punkcie końcowym, aby utworzyć nowe wystąpienie przepływu pracy.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Skompiluj rozwiązanie.  
  
2. Uruchom aplikację. Konsola `CreationEndpoint` wyświetla komunikat zawierający identyfikator wystąpienia podczas tworzenia wystąpienia przepływu pracy. Wiadomość "Hello World!" jest drukowany przez wystąpienie przepływu pracy.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
