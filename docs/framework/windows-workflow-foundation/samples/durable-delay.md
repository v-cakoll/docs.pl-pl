---
title: "Trwałe opóźnienia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 220ec240-b958-430c-81ff-b734a6aa97ae
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a7023d7548db99d511ae18ad4d52b9a8168c4243
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="durable-delay"></a>Trwałe opóźnienia
W tym przykładzie przedstawiono sposób użycia trwałe opóźnienia, czyli opóźnienie będzie się powtarzał przepływu pracy na urządzeniu trwałe podczas opóźnienie. Przykładowy przepływ pracy zawiera dwa komunikaty do konsoli, oddzielonych opóźnienia. Po wyzwoleniu opóźnienie przepływu pracy jest zwalniany i oczekuje na 5 sekund w magazynie wystąpień przepływu pracy przed ładowane w pamięci.  
  
## <a name="workflow-details"></a>Szczegóły przepływu pracy  
 Hosta usługi przepływu pracy obsługuje przepływu pracy i wystąpienia przepływu pracy przez ładowanie i zwalnianie nimi zarządza. Aby uruchomić wystąpienie definicji przepływu pracy, próbki ustawia serwer proxy, który wysyła komunikat do <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy. <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> Właściwość jest ustawiona na `true`, włączenie go w celu utworzenia nowego wystąpienia przepływu pracy po otrzymaniu komunikatu.  
  
 Poniższa lista zawiera szczegóły dotyczące konfiguracji przez hosta usługi przepływu pracy podczas inicjowania.  
  
1.  Tworzy hosta usługi przy użyciu adresu (adresem http://localhost: 8080/klienta).  
  
2.  Tworzy punkt końcowy w celu umożliwienia komunikacji z hosta usługi <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy.  
  
3.  Skonfigurowanie magazynu wystąpienia SQL.  
  
4.  Dodaje zachowanie wystąpienia zwolnienie określa warunki, w których hosta usługi przepływu pracy należy zwolnić wystąpienia przepływu pracy w magazynie trwałości SQL. Dla tego przykładu zwalnia wystąpienie natychmiast po przepływu pracy przechodzi bezczynności (po wyzwoleniu opóźnienia).  
  
5.  Tworzy serwera proxy, który wysyła komunikat do <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Konfigurowanie bazy danych trwałości.  
  
    1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.  
  
    2.  Przejdź do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] katalogu (C:\Windows\Microsoft.NET\Framework\v4. X\\).  
  
    3.  Edytuj plik WorkflowManagementService.exe.config i dodaj następujące parametry połączenia w <`database`> elementu.  
  
        ```xml  
        <database connectionString="Data Source=localhost\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True;Asynchronous Processing=True" />  
        ```  
  
    4.  Przejdź do katalogu DurableDelay\CS.  
  
    5.  Uruchom Setup.cmd.  
  
2.  Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] przy użyciu podwyższonym poziomem uprawnień, klikając prawym przyciskiem myszy [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikony, jak i wybierając **Uruchom jako administrator**.  
  
3.  Otwórz plik rozwiązania Delay.sln.  
  
4.  Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.  
  
5.  Naciśnij klawisze CTRL + F5, aby uruchomić rozwiązanie.  
  
#### <a name="to-uninstall-this-sample"></a>Aby odinstalować tego przykładu  
  
1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.  
  
2.  Przejdź do katalogu DurableDelay\CS.  
  
3.  Uruchom Cleanup.cmd.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelay`  
  
## <a name="see-also"></a>Zobacz też
