---
title: "Podstawowe sposoby użycia SendParameters i ReceiveParameters działania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b6b1681-3d41-403f-bfe2-3f600f24aa8c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 501aead51a96d483a55602c737613e1d9066b74c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="basic-usage-of-sendparameters-and-receiveparameters-activities"></a>Podstawowe sposoby użycia SendParameters i ReceiveParameters działania
W tym przykładzie pokazano sposób użycia <xref:System.ServiceModel.Activities.SendParametersContent> i <xref:System.ServiceModel.Activities.ReceiveParametersContent> działań. Usługa przedstawia jedną operację, która przyjmuje argument będący ciągiem i zwraca dane wejściowe do klienta. Przykład pokazuje, jak do ustawiania parametrów dla tych działań komunikacji.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\SendReceiveParameters`  
  
#### <a name="using-this-sample"></a>Za pomocą tego przykładu  
  
1.  Załadowanie projektu rozwiązania w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i skompilować projekt.  
  
2.  Najpierw uruchom aplikację EchoWorkflowService wygenerowanych w \EchoWorkflowService\bin\debug [katalogu podstawowego rozwiązania].  
  
3.  Po drugie Uruchom aplikację EchoWorkflowClient wygenerowanych w \EchoWorkflowClient\bin\debug [katalogu podstawowego rozwiązania].  
  
4.  Klient wywołuje operację Echo i wyświetla wyniki. Po zakończeniu naciśnij klawisz ENTER, aby zamknąć klienta, a następnie usługi.