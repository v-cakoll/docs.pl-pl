---
title: Wznowienie zakładki WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: d393a26dd29624765e01b139e818de8a41f73e06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182740"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a>Wznowienie zakładki WorkflowHostingEndpoint
W tym przykładzie <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> pokazano, <xref:System.ServiceModel.Activities.WorkflowServiceHost> jak można używać do tworzenia wystąpień przepływu pracy.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>Dyskusji  
 W tym przykładzie <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> użyto do utworzenia <xref:System.ServiceModel.Activities.WorkflowServiceHost>wystąpienia przepływu pracy hostowanego przy użyciu programu . <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>jest punktem rozszerzalności, który <xref:System.ServiceModel.Activities.WorkflowServiceHost> może być używany w następujących scenariuszach:  
  
- Tworzenie nowych wystąpień przepływu pracy.  
  
- Wznowienie zakładek w wystąpieniu przepływu pracy hostowanym w pliku <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
 Przykładowy punkt końcowy, który jest uwzględniony udostępnia kontrakt, który udostępnia operacje, aby utworzyć przepływ pracy i zwrócić identyfikator wystąpienia lub utworzyć wystąpienie o określonym identyfikatorze. Przykładowa aplikacja konsoli <xref:System.ServiceModel.Activities.WorkflowServiceHost> tworzy wystąpienie z podstawową `CreationEndpoint` definicją przepływu pracy i dodaje do hosta. Następnie wywołuje `Create` operację w punkcie końcowym, aby utworzyć nowe wystąpienie przepływu pracy.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Skompiluj rozwiązanie.  
  
2. Uruchom aplikację. Konsola `CreationEndpoint` wyświetla komunikat zawierający identyfikator wystąpienia podczas tworzenia wystąpienia przepływu pracy. Wiadomość "Hello World!" jest drukowany przez przepływ pracy po pomyślnym wznowieniu zakładki.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
