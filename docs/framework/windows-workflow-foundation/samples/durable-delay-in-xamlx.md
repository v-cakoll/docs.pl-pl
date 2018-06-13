---
title: Trwałe opóźnienia w XAMLX
ms.date: 03/30/2017
ms.assetid: efc38df4-2d34-453c-8e59-2c21d1307354
ms.openlocfilehash: 1b0e418e382c20350a61a36164265c1693925e11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516308"
---
# <a name="durable-delay-in-xamlx"></a>Trwałe opóźnienia w XAMLX
W tym przykładzie przedstawiono sposób użycia trwałe opóźnienia, czyli opóźnienie będzie się powtarzał przepływu pracy na urządzeniu trwałe podczas opóźnienie.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlx`  
  
## <a name="discussion"></a>Omówienie  
 Przykładowy przepływ pracy zawiera dwa komunikaty do pliku lokalnego, oddzielonych opóźnienia. Po wyzwoleniu opóźnienie przepływu pracy jest zwalniany i oczekuje na 5 sekund w magazynie wystąpień przepływu pracy przed ładowane w pamięci.  
  
 Plik .xamlx jest usługi przepływu pracy, który znajduje się w programie Visual Studio. Visual Studio będzie korzystać Cassini, który korzysta z hosta do hosta usługi przepływu pracy przepływu pracy.  
  
 Oprócz obsługuje przepływ pracy, hosta usługi przepływu pracy zarządza wystąpienia przepływu pracy, ładowanie i zwalnianie je. Aby uruchomić wystąpienie definicji Windows Workflow Foundation (WF) (na hosta usługi przepływu pracy), należy ustawić klienta, który wysyła komunikat do <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy. To <xref:System.ServiceModel.Activities.Receive> ma jego <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> ustawioną właściwość `true`, włączenie go w celu utworzenia nowego wystąpienia przepływu pracy po otrzymaniu komunikatu.  
  
 Podczas inicjowania zwolnienie zachowanie wystąpienia są dodawane do pliku konfiguracji, która określa hosta usługi przepływu pracy, pod którym powinna zwolnić wystąpienie w magazynie trwałości (baza danych). Dla tego przykładu zwalnia wystąpienie natychmiast po przepływu pracy przechodzi bezczynności (po wyzwoleniu opóźnienia).  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.  
  
2.  Przejdź do folderu DurableDelayXamlx\CS.  
  
3.  Uruchom Setup.cmd.  
  
4.  Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] jako administrator.  
  
5.  Otwórz plik rozwiązania DurableDelayXamlx.sln.  
  
6.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **właściwości**.  
  
7.  Wybierz **wiele projektów startowych** ustawiono oba projekty **Start**.  
  
8.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
9. Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
#### <a name="to-uninstall-this-sample"></a>Aby odinstalować tego przykładu  
  
1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.  
  
2.  Przejdź do folderu DurableDelayXamlx\CS.  
  
3.  Uruchom Cleanup.cmd.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlX`
