---
title: Buforowanie kanału z wysyłaniem
ms.date: 03/30/2017
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
ms.openlocfilehash: 619088def1f5e443a31244516655d75d1e25c9cb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503818"
---
# <a name="channel-caching-with-send"></a>Buforowanie kanału z wysyłaniem
<xref:System.ServiceModel.Activities.SendMessageChannelCache> Użytkownicy mogą mieć różne poziomy buforowania kanału <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.SendParametersContent> działań. Buforowanie poziomie wystąpienia jest domyślnie włączona, a w tym przykładzie przedstawiono następujące funkcje:  
  
1.  Udostępnij <xref:System.ServiceModel.Activities.SendMessageChannelCache> w domenie aplikacji.  
  
2.  Wyłącz buforowanie kanału.  
  
3.  Udostępnij <xref:System.ServiceModel.Activities.SendMessageChannelCache> wśród wystąpień przepływu pracy w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.ServiceModel.Activities.SendMessageChannelCache> rozszerzenie <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> i <xref:System.ServiceModel.Activities.SendReply> działań.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Załaduj projekt rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i skompiluj projekt.  
  
2.  Uruchom aplikację EchoWorkflowService wygenerowane w \EchoWorkflowService\bin\debug.  
  
3.  Uruchom aplikację EchoWorkflowClient wygenerowane w .\EchoWorkflowClient\bin\debug.  
  
4.  Klient wywołuje działanie usługi Echo i drukuje wyniki. Podczas drukowania wyniki naciśnij klawisz ENTER, aby zamknąć klienta i usługi.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`
