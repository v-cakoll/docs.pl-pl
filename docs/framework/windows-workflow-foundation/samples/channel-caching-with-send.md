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
ms.openlocfilehash: 7f8a11397fe161edad6f726c1d6df9ed09dad54a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
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
