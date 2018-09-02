---
title: Wysyłanie i obsługa błędów
ms.date: 03/30/2017
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
ms.openlocfilehash: 896f209e7daeeab2bb33c1fde15298aae96c8776
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406661"
---
# <a name="sending-and-handling-faults"></a>Wysyłanie i obsługa błędów
W tym przykładzie przedstawiono sposób użycia <xref:System.ServiceModel.Activities.SendReply> i <xref:System.ServiceModel.Activities.ReceiveReply> wiadomości działania do wysyłania i odbierania oczekiwane i nieoczekiwane błędy. W tym scenariuszu pierwszy klient żąda wyniki w oczekiwanym domenach błędów, która została uwzględniona w jego <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> kolekcji. Dalej kilka żądań klientów doprowadzić do odbierania nieoczekiwane błędy przed ostatnim żądanie zakończy się pomyślnie.  
  
## <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z podwyższonym poziomem uprawnień, klikając prawym przyciskiem myszy [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonę i wybierając polecenie **Uruchom jako administrator**.  
  
2.  Otwórz plik rozwiązania Faults.sln.  
  
3.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
4.  Uruchamianie projektu usługi.  
  
    1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `FaultService` projektu, a następnie wybierz **Ustaw jako projekt startowy**.  
  
    2.  Naciśnij kombinację klawiszy CTRL + F5.  
  
5.  Otwórz inną kopię [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z podwyższonym poziomem uprawnień, klikając prawym przyciskiem myszy [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonę i wybierając polecenie **Uruchom jako administrator**.  
  
6.  Otwórz plik rozwiązania Faults.sln.  
  
7.  Uruchom projekt klienta.  
  
    1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `FaultClient` projektu, a następnie wybierz **Ustaw jako projekt startowy**.  
  
    2.  Naciśnij kombinację klawiszy CTRL + F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`