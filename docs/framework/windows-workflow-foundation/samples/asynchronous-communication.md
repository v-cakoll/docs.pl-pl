---
title: Komunikacji asynchronicznej
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: 9eafeab89aefb181ae016dc0219f9155d9bd2a25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515163"
---
# <a name="asynchronous-communication"></a>Komunikacji asynchronicznej
W przykładzie pokazano, jak komunikację między dwóch różnych usług Windows Workflow Foundation (WF) jest wykonywane asynchronicznie domyślnie.  
  
## <a name="demonstrates"></a>Demonstracje  
 Asynchroniczną komunikację między [!INCLUDE[wf1](../../../../includes/wf1-md.md)] usług.  
  
## <a name="discussion"></a>Omówienie  
 W tym przykładzie pokazano sposób komunikacji między [!INCLUDE[wf1](../../../../includes/wf1-md.md)] aplikacji jest wykonywane asynchronicznie za pomocą działania obsługi komunikatów dostarczonych przez .NET Framework.  
  
 W tym przykładzie składa się z następujących trzech projektach.  
  
 CreditCheckService  
 Ta usługa odbiera wynik środki danej osoby lub wartość elementu uzyskanie, a następnie decyduje o tym, czy środków znajduje się z osobą.  
  
 RentalApprovalService  
 Ta usługa odbiera aplikacji od osoby, która wymaga certyfikat. Ta usługa komunikuje asynchronicznie `CreditCheckService` zdecydować, czy aplikacja kredytowej jest prawidłowy.  
  
 Klient  
 Klient komunikuje się synchronicznie z `RentalApprovalService` wiedzieć, czy jest zatwierdzona środków.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Kliknij prawym przyciskiem myszy **AsynchronousCommunication** rozwiązania i wybierz **właściwości**.  
  
2.  W **wspólne właściwości**, wybierz pozycję **projekt startowy**i wybierz **wiele projektów startowych**.  
  
3.  Przenieś **RentalApprovalService** na pierwszą pozycję na liście, a następnie **CreditCheckService**, a następnie **klienta**. Ustaw **Start** akcji we wszystkich trzech projektach.  
  
4.  Kliknij przycisk **OK**, i naciśnij klawisz F5, aby uruchomić przykład.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
