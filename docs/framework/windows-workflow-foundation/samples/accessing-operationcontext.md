---
title: Uzyskiwanie dostępu do elementu OperationContext
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: cefbc3b10114b427518e640809462eedb131d695
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="accessing-operationcontext"></a>Uzyskiwanie dostępu do elementu OperationContext
W tym przykładzie przedstawiono sposób działania dotyczące komunikatów (<xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.Send>) można użyć z działaniem niestandardowy zakres dostępu do <xref:System.ServiceModel.OperationContext.Current%2A> i dołączyć lub pobrać nagłówek niestandardowy komunikat w wiadomości wychodzące lub przychodzące.  
  
## <a name="demonstrates"></a>Demonstracje  
 Działania, do obsługi komunikatów <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.  
  
## <a name="discussion"></a>Omówienie  
 Ten przykład przedstawia sposób użycia punkty rozszerzeń (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) w działaniach obsługi dostępu do <xref:System.ServiceModel.OperationContext.Current%2A>. Wywołania zwrotne są zarejestrowane w ramach środowiska uruchomieniowego przepływu pracy jako implementacja <xref:System.Activities.IExecutionProperty> która zostaje pobrana przez działania obsługi komunikatów na wykonanie. Wszystkie działania obsługi komunikatów w tym samym zakresie co <xref:System.Activities.IExecutionProperty> dotyczy implementacji. W szczególności w przykładzie użyto działania niestandardowy zakres, aby wymusić zachowanie wywołania zwrotnego. <xref:System.ServiceModel.Activities.ISendMessageCallback> Jest używana w przepływie pracy klienta do włączenia przepływu pracy <xref:System.Activities.WorkflowApplication.Id%2A> jako wychodzące <xref:System.ServiceModel.Channels.MessageHeader>. Ten nagłówek jest następnie pobrane przy użyciu usługi <xref:System.ServiceModel.Activities.IReceiveMessageCallback> i wartość nagłówka jest drukowany w konsoli.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Ten przykład przedstawia usługi przepływu pracy przy użyciu punktów końcowych HTTP. Można dodać do uruchomienia, to przykładowa, odpowiednich list ACL adresu URL (zobacz [Konfigurowanie protokołów HTTP i HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) szczegółowe informacje), uruchamiając program Visual Studio jako Administrator lub, wykonując następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień, aby dodać odpowiednich list ACL. Upewnij się, czy użytkownika domena i nazwa użytkownika są zastępowane.  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  Po dodaniu listy ACL adresu URL, wykonaj następujące kroki.  
  
    1.  Skompiluj rozwiązanie.  
  
    2.  Ustawianie wielu projektów uruchamiania prawym przyciskiem myszy rozwiązanie i wybierając **Ustaw projekty startowe**.  
  
    3.  Dodaj **usługi** i **klienta** (w tej kolejności) jako wiele projektów rozruchu.  
  
    4.  Uruchom aplikację. W konsoli klienta zawiera przepływu pracy korzystającego z dwa razy i okno usługi zawiera identyfikator wystąpienia tych przepływów pracy.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
