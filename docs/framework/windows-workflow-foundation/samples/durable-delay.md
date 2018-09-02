---
title: Trwałe opóźnienie
ms.date: 03/30/2017
ms.assetid: 220ec240-b958-430c-81ff-b734a6aa97ae
ms.openlocfilehash: 2a7692e28d60232913ae5d11a90025e59664c0e5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406579"
---
# <a name="durable-delay"></a>Trwałe opóźnienie
Ten przykład pokazuje sposób użycia trwałe opóźnienie z opóźnieniem, która utrzymuje przepływu pracy na trwałe urządzenie podczas opóźnienie. Przykładowy przepływ pracy zawiera dwa komunikaty wyjściowe do konsoli, które są oddzielone opóźnienia. Po wyzwoleniu opóźnienie przepływu pracy jest zwalniana i oczekuje na 5 sekund magazynu wystąpień przepływu pracy ładowane w pamięci.  
  
## <a name="workflow-details"></a>Szczegóły przepływu pracy  
 Hosta usługi przepływu pracy obsługuje przepływu pracy i wystąpienia przepływu pracy, ładowanie i zwalnianie nimi zarządza. Aby uruchomić wystąpienie definicji przepływu pracy, próbki zestawów serwera proxy, który wysyła wiadomość do <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy. <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> Właściwość jest ustawiona na `true`, dzięki czemu może utworzyć nowe wystąpienie przepływu pracy, po odebraniu wiadomości.  
  
 Poniżej przedstawiono szczegółową listę konfiguracji przez hosta usługi przepływu pracy podczas inicjowania.  
  
1.  Tworzy hosta usługi przy użyciu adresu (http://localhost:8080/Client).  
  
2.  Tworzy punkt końcowy na hoście usługi, aby umożliwić komunikację z <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy.  
  
3.  Konfiguruje magazyn wystąpienia programu SQL.  
  
4.  Dodaje zachowanie wystąpienia unload, który określa warunki, w których hosta usługi przepływu pracy należy zwolnić wystąpienia przepływu pracy w magazynie stanów trwałych programu SQL. W tym przykładzie zwalnia wystąpienie natychmiast po zakończeniu przepływu pracy przechodzi bezczynności (w przypadku wyzwolenia opóźnienie).  
  
5.  Tworzy serwer proxy, który wysyła wiadomość do <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Konfigurowanie bazy danych trwałości.  
  
    1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.  
  
    2.  Przejdź do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] katalogu (C:\Windows\Microsoft.NET\Framework\v4. X\\).  
  
    3.  Edytuj plik WorkflowManagementService.exe.config i dodaj następujące parametry połączenia w ramach <`database`> element.  
  
        ```xml  
        <database connectionString="Data Source=localhost\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True;Asynchronous Processing=True" />  
        ```  
  
    4.  Przejdź do katalogu DurableDelay\CS.  
  
    5.  Uruchom plik Setup.cmd.  
  
2.  Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] przy użyciu podniesionych uprawnień, klikając prawym przyciskiem myszy [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonę i wybierając polecenie **Uruchom jako administrator**.  
  
3.  Otwórz plik rozwiązania Delay.sln.  
  
4.  Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.  
  
5.  Naciśnij klawisze CTRL + F5, aby uruchomić rozwiązanie.  
  
#### <a name="to-uninstall-this-sample"></a>Aby odinstalować tego przykładu  
  
1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.  
  
2.  Przejdź do katalogu DurableDelay\CS.  
  
3.  Uruchom Cleanup.cmd.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelay`