---
title: Trwałe opóźnienie w XAMLX
ms.date: 03/30/2017
ms.assetid: efc38df4-2d34-453c-8e59-2c21d1307354
ms.openlocfilehash: 1eef9211c67d190ecb5f329c481fa2e3d1763353
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195192"
---
# <a name="durable-delay-in-xamlx"></a>Trwałe opóźnienie w XAMLX
Ten przykład pokazuje sposób użycia trwałe opóźnienie z opóźnieniem, która utrzymuje przepływu pracy na trwałe urządzenie podczas opóźnienie.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlx`  
  
## <a name="discussion"></a>Dyskusja  
 Przykładowy przepływ pracy zawiera dwa komunikaty do pliku lokalnego, oddzielonych opóźnienia. Po wyzwoleniu opóźnienie przepływu pracy jest zwalniana i oczekuje na 5 sekund magazynu wystąpień przepływu pracy ładowane w pamięci.  
  
 Plik .xamlx jest usługi przepływu pracy, który znajduje się w programie Visual Studio. Visual Studio używa Cassini, który używa usługi przepływu pracy do hosta przepływu pracy.  
  
 Oprócz hostowania przepływu pracy, hosta usługi przepływu pracy zarządza wystąpienia przepływu pracy, ładowanie i zwalnianie je. Aby uruchomić wystąpienie programu Windows Workflow Foundation (WF) definicji (na hosta usługi przepływu pracy), należy ustawić klienta, która wysyła komunikat do <xref:System.ServiceModel.Activities.Receive> działania w przepływie pracy. To <xref:System.ServiceModel.Activities.Receive> ma jego <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> właściwością `true`, dzięki czemu może utworzyć nowe wystąpienie przepływu pracy, po odebraniu wiadomości.  
  
 Podczas inicjowania zachowanie wystąpienia zwolnienie jest dodawany do pliku konfiguracji, który określa hosta usługi przepływu pracy w ramach której powinna zwolnić wystąpienia w trwałości sklepie najbardziej (baza danych). W tym przykładzie zwalnia wystąpienie natychmiast po zakończeniu przepływu pracy przechodzi bezczynności (w przypadku wyzwolenia opóźnienie).  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.  
  
2.  Przejdź do folderu DurableDelayXamlx\CS.  
  
3.  Uruchom plik Setup.cmd.  
  
4.  Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] jako administrator.  
  
5.  Otwórz plik rozwiązania DurableDelayXamlx.sln.  
  
6.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **właściwości**.  
  
7.  Wybierz **wiele projektów startowych** i ustaw oba projekty **Start**.  
  
8.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
9. Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
#### <a name="to-uninstall-this-sample"></a>Aby odinstalować tego przykładu  
  
1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.  
  
2.  Przejdź do folderu DurableDelayXamlx\CS.  
  
3.  Uruchom Cleanup.cmd.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlX`
