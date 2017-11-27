---
title: "Wysyłanie i obsługa błędów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 57d522918d280c9a8a68fcd420b7216cc48216d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="sending-and-handling-faults"></a>Wysyłanie i obsługa błędów
W tym przykładzie przedstawiono sposób użycia <xref:System.ServiceModel.Activities.SendReply> i <xref:System.ServiceModel.Activities.ReceiveReply> wiadomości działań do wysyłania i odbierania oczekiwane i nieoczekiwane błędy. W tym scenariuszu pierwszy klient żąda powoduje błąd oczekiwanego, która została uwzględniona w jego <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> kolekcji. Następny kilka żądań klientów powoduje odbieranie nieoczekiwanych błędów, przed ostatnim żądanie zakończy się sukcesem.  
  
## <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z podwyższonym poziomem uprawnień, klikając prawym przyciskiem myszy [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikony, jak i wybierając **Uruchom jako administrator**.  
  
2.  Otwórz plik rozwiązania Faults.sln.  
  
3.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
4.  Uruchom projekt dla usługi.  
  
    1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `FaultService` projekt i wybierz **Ustaw jako projekt startowy**.  
  
    2.  Naciśnij klawisze CTRL + F5.  
  
5.  Otwórz inną kopię [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z podwyższonym poziomem uprawnień, klikając prawym przyciskiem myszy [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikony, jak i wybierając **Uruchom jako administrator**.  
  
6.  Otwórz plik rozwiązania Faults.sln.  
  
7.  Uruchamianie projektu klienta.  
  
    1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `FaultClient` projekt i wybierz **Ustaw jako projekt startowy**.  
  
    2.  Naciśnij klawisze CTRL + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`  
  
## <a name="see-also"></a>Zobacz też
