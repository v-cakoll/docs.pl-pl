---
title: Uzyskiwanie dostępu do elementu OperationContext
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: c104ceb22117d7cc53050a6513a4aea58fdff8c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62005605"
---
# <a name="accessing-operationcontext"></a>Uzyskiwanie dostępu do elementu OperationContext
W tym przykładzie przedstawiono sposób działania dotyczące komunikatów (<xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.Send>) może służyć za pomocą działania niestandardowego zakresu dostępu do <xref:System.ServiceModel.OperationContext.Current%2A> i dołączyć lub pobrać nagłówek niestandardowy komunikat w wiadomości wychodzące lub przychodzące.  
  
## <a name="demonstrates"></a>Demonstracje  
 Wiadomości działania, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.  
  
## <a name="discussion"></a>Dyskusja  
 W tym przykładzie pokazano, jak punkty rozszerzeń (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) w działań dotyczących komunikatów w celu uzyskania dostępu do <xref:System.ServiceModel.OperationContext.Current%2A>. Wywołania zwrotne są zarejestrowane w ramach środowiska wykonawczego przepływów pracy jako implementacja <xref:System.Activities.IExecutionProperty> , zostaje pobrana przez działań dotyczących komunikatów podczas wykonywania. Wszelkie działania obsługi komunikatów w tym samym zakresie co <xref:System.Activities.IExecutionProperty> dotyczy wdrożenia. W szczególności w tym przykładzie używa działania niestandardowy zakres, aby wymusić zachowanie wywołania zwrotnego. <xref:System.ServiceModel.Activities.ISendMessageCallback> Jest używana w przepływie pracy klienta do włączenia przepływu pracy <xref:System.Activities.WorkflowApplication.Id%2A> jako wychodzący <xref:System.ServiceModel.Channels.MessageHeader>. Tego pliku nagłówkowego jest następnie pobierana za pomocą usługi <xref:System.ServiceModel.Activities.IReceiveMessageCallback> i wartość nagłówka są drukowane do konsoli.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Ten przykład przedstawia usługi przepływu pracy za pomocą punktów końcowych HTTP. Można dodać do uruchomienia tego przykładowego, odpowiednie listy ACL adresu URL (zobacz [Konfigurowanie protokołów HTTP i HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) szczegóły), albo przez uruchomienie programu Visual Studio jako Administrator, wykonując następujące polecenie w wierszu podwyższonym poziomem uprawnień, aby dodać odpowiednie listy ACL. Upewnij się, Twoja domena i nazwa użytkownika są zastępowane.  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. Po dodaniu listy ACL adresu URL, wykonaj następujące kroki.  
  
    1. Skompiluj rozwiązanie.  
  
    2. Ustawianie wielu projektów uruchamiania, kliknij prawym przyciskiem myszy rozwiązanie i wybierając **Ustaw projekty startowe**.  
  
    3. Dodaj **usługi** i **klienta** (w tej kolejności) jako wiele projektów uruchamiania.  
  
    4. Uruchom aplikację. W konsoli klienta pokazuje przepływu pracy korzystającego z dwa razy i przedział czasu usługi zawiera identyfikator wystąpienia tych przepływów pracy.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
