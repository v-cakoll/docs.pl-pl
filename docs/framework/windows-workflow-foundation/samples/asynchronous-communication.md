---
title: Komunikacja asynchroniczna
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: 28b325a6bd870282577a2989b616628d52262deb
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711860"
---
# <a name="asynchronous-communication"></a>Komunikacja asynchroniczna
W tym przykładzie pokazano, jak komunikacja między dwiema różnymi usługami Windows Workflow Foundation (WF) odbywa się domyślnie asynchronicznie.  
  
## <a name="demonstrates"></a>Przedstawia  
 Asynchroniczna komunikacja między usługami [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  
  
## <a name="discussion"></a>Dyskusji  
 Ten przykład pokazuje, jak komunikacja między [!INCLUDE[wf1](../../../../includes/wf1-md.md)] aplikacjami odbywa się asynchronicznie przy użyciu działań dotyczących komunikatów dostarczonych przez .NET Framework.  
  
 Ten przykład składa się z trzech następujących projektów.  
  
 CreditCheckService  
 Ta usługa otrzymuje wynik kredytowy określonej osoby lub wartość elementu do pobrania, a następnie decyduje o tym, czy kredyt został udzielony.  
  
 RentalApprovalService  
 Ta usługa otrzymuje aplikację od osoby, która jest w trakcie pewnego kredytu. Ta usługa komunikuje się asynchronicznie z `CreditCheckService`, aby zdecydować, czy aplikacja kredytowa jest prawidłowa.  
  
 Klient  
 Klient komunikuje się synchronicznie z `RentalApprovalService`, aby dowiedzieć się, czy kredyt został zatwierdzony.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Kliknij prawym przyciskiem myszy rozwiązanie **AsynchronousCommunication** i wybierz polecenie **Właściwości**.  
  
2. W obszarze **wspólne właściwości**wybierz pozycję **projekt startowy**, a następnie wybierz opcję **wiele projektów startowych**.  
  
3. Przenieś **RentalApprovalService** do pierwszej pozycji na liście, a następnie **CreditCheckService**, po którym następuje **Klient**. Ustaw akcję **startową** dla wszystkich trzech projektów.  
  
4. Kliknij przycisk **OK**, a następnie naciśnij klawisz F5, aby uruchomić przykład.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
