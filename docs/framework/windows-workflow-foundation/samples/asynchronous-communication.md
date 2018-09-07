---
title: Komunikacji asynchronicznej
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: e85f7efb0de1326ceb5091c305b20f34809eab57
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44047090"
---
# <a name="asynchronous-communication"></a>Komunikacji asynchronicznej
Niniejszy przykład pokazuje, jak komunikacja między dwoma różnymi usługami Windows Workflow Foundation (WF) są wykonywane asynchronicznie domyślnie.  
  
## <a name="demonstrates"></a>Demonstracje  
 Komunikacji asynchronicznej między [!INCLUDE[wf1](../../../../includes/wf1-md.md)] usług.  
  
## <a name="discussion"></a>Dyskusja  
 Ten przykład pokazuje, jak komunikacja między [!INCLUDE[wf1](../../../../includes/wf1-md.md)] aplikacje są wykonywane asynchronicznie przy użyciu działań dotyczących komunikatów dostarczane przez program .NET Framework.  
  
 W tym przykładzie składa się z następujących trzech projektach.  
  
 CreditCheckService  
 Ta usługa odbiera wynik środki konkretnej osoby lub wartość elementu można uzyskać i następnie decyduje, czy kredytu znajduje się z osobą.  
  
 RentalApprovalService  
 Ta usługa odbiera aplikacji z osoba będąca wymagające niektóre środki. Ta usługa komunikuje asynchronicznie `CreditCheckService` zdecydować, czy wniosku o kredyt jest prawidłowa.  
  
 Klient  
 Klient komunikuje się synchronicznie przy użyciu `RentalApprovalService` wiedzieć, czy jest zatwierdzony środków.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Kliknij prawym przyciskiem myszy **AsynchronousCommunication** rozwiązań i wybierz pozycję **właściwości**.  
  
2.  W **wspólne właściwości**, wybierz opcję **projekt startowy**i wybierz **wiele projektów startowych**.  
  
3.  Przenieś **RentalApprovalService** na pierwszą pozycję na liście, a następnie **CreditCheckService**, a następnie **klienta**. Ustaw **Start** akcję na wszystkich trzech projektach.  
  
4.  Kliknij przycisk **OK**, i naciśnij klawisz F5, aby uruchomić próbki.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
