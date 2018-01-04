---
title: "Kanał buforowania, wysyłania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b12ebe4cc15629125627253200a95b1f8353bbc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="channel-caching-with-send"></a>Kanał buforowania, wysyłania
<xref:System.ServiceModel.Activities.SendMessageChannelCache> , Użytkownicy mogą mieć różne poziomy buforowania, kanał <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.SendParametersContent> działań. Buforowanie na poziomie wystąpienia jest domyślnie włączona i w tym przykładzie przedstawiono następujące funkcje:  
  
1.  Udział <xref:System.ServiceModel.Activities.SendMessageChannelCache> w domenie aplikacji.  
  
2.  Wyłącz buforowanie kanału.  
  
3.  Udział <xref:System.ServiceModel.Activities.SendMessageChannelCache> między wystąpienia przepływu pracy w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.ServiceModel.Activities.SendMessageChannelCache>rozszerzenie, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> i <xref:System.ServiceModel.Activities.SendReply> działań.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Załadowanie projektu rozwiązania w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i skompilować projekt.  
  
2.  Uruchom aplikację EchoWorkflowService wygenerowanych w \EchoWorkflowService\bin\debug.  
  
3.  Uruchom aplikację EchoWorkflowClient wygenerowanych w .\EchoWorkflowClient\bin\debug.  
  
4.  Klient wywołuje operację Echo usługi i wyświetla wyniki. Podczas drukowania wyników naciśnij klawisz ENTER, aby zamknąć klienta i usługi.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`
