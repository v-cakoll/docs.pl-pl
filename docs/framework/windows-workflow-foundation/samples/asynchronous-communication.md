---
title: Komunikacja asynchroniczna
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: e1bc63b5d3178b8e98350dedd8eb0791e0e35589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142879"
---
# <a name="asynchronous-communication"></a>Komunikacja asynchroniczna
W tym przykładzie pokazano, jak komunikacja między dwoma różnymi usługami Windows Workflow Foundation (WF) jest domyślnie wykonywana asynchronicznie.  
  
## <a name="demonstrates"></a>Demonstracje  
 Komunikacja asynchronizacjowa między usługami. [!INCLUDE[wf1](../../../../includes/wf1-md.md)]  
  
## <a name="discussion"></a>Dyskusji  
 W tym przykładzie [!INCLUDE[wf1](../../../../includes/wf1-md.md)] pokazano, jak komunikacja między aplikacjami odbywa się asynchronicznie przy użyciu działań obsługi wiadomości dostarczonych przez program .NET Framework.  
  
 Ten przykład składa się z następujących trzech projektów.  
  
 Usługa CreditCheckService  
 Usługa ta otrzymuje ocenę kredytową konkretnej osoby lub wartość przedmiotu do nabycia, a następnie decyduje, czy kredyt jest przyznawany osobie.  
  
 RentalApprovalService (Usługa zdatna do wypożyczania)  
 Usługa ta otrzymuje wniosek od osoby, która potrzebuje jakiegoś kredytu. Ta usługa komunikuje się asynchronicznie `CreditCheckService` z, aby zdecydować, czy wniosek o kredyt jest prawidłowy.  
  
 Klient  
 Klient komunikuje się synchronicznie `RentalApprovalService` z, aby wiedzieć, czy kredyt został zatwierdzony.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Kliknij prawym przyciskiem myszy rozwiązanie **komunikacji asynchroniiowej** i wybierz polecenie **Właściwości**.  
  
2. W **obszarze Właściwości wspólne**wybierz pozycję Projekt **uruchamiania**i wybierz pozycję Wiele projektów **uruchamiania**.  
  
3. Przenieś **RentalApprovalService** na pierwszą pozycję na liście, a następnie **CreditCheckService**, a następnie **klient**. Ustaw akcję **Start** dla wszystkich trzech projektów.  
  
4. Kliknij **przycisk OK**i naciśnij klawisz F5, aby uruchomić próbkę.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
