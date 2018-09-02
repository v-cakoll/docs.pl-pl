---
title: Podstawowe użycia sposoby i ReceiveParameters działań
ms.date: 03/30/2017
ms.assetid: 1b6b1681-3d41-403f-bfe2-3f600f24aa8c
ms.openlocfilehash: c13999ad1571a6413e30e801b6c642000f8e4654
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467698"
---
# <a name="basic-usage-of-sendparameters-and-receiveparameters-activities"></a>Podstawowe użycia sposoby i ReceiveParameters działań
W tym przykładzie przedstawiono użycie <xref:System.ServiceModel.Activities.SendParametersContent> i <xref:System.ServiceModel.Activities.ReceiveParametersContent> działań. Usługa udostępnia jedna operacja, która przyjmuje argument ciąg i zwraca dane wejściowe do klienta. Przykład przedstawia sposób ustawiania parametrów dla tych działań dotyczących komunikatów.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\SendReceiveParameters`  
  
#### <a name="using-this-sample"></a>Za pomocą tego przykładu  
  
1.  Załaduj projekt rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i skompiluj projekt.  
  
2.  Pierwszym uruchomieniu aplikacji EchoWorkflowService wygenerowane w \EchoWorkflowService\bin\debug [katalog podstawowy rozwiązania].  
  
3.  Po drugie Uruchom aplikację EchoWorkflowClient, wygenerowane w \EchoWorkflowClient\bin\debug [katalog podstawowy rozwiązania].  
  
4.  Klient wywołuje działanie usługi Echo i drukuje wyniki. Po zakończeniu naciśnij klawisz ENTER, aby zamknąć klienta, a następnie usługi.