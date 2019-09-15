---
title: Uzyskiwanie dostępu do elementu OperationContext
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: dea990e275125dc1cd2255b88e506d363c3ac78e
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989390"
---
# <a name="accessing-operationcontext"></a>Uzyskiwanie dostępu do elementu OperationContext
W tym przykładzie pokazano, jak działania obsługi<xref:System.ServiceModel.Activities.Receive> komunikatów <xref:System.ServiceModel.Activities.Send>(i) mogą być używane z niestandardowym działaniem zakresu w celu uzyskania dostępu <xref:System.ServiceModel.OperationContext.Current%2A> do niestandardowego nagłówka komunikatu i dołączenia go lub pobrania go w wiadomości wychodzącej lub przychodzącej.  
  
## <a name="demonstrates"></a>Demonstracje  
 Działania dotyczące komunikatów <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>,.  
  
## <a name="discussion"></a>Dyskusji  
 Ten przykład pokazuje, jak używać punktów rozszerzalności<xref:System.ServiceModel.Activities.ISendMessageCallback>( <xref:System.ServiceModel.Activities.IReceiveMessageCallback>)) w działaniach związanych z <xref:System.ServiceModel.OperationContext.Current%2A>przesyłaniem komunikatów do programu. Wywołania zwrotne są rejestrowane w środowisku uruchomieniowym przepływu pracy jako implementacja <xref:System.Activities.IExecutionProperty> programu, która jest pobierana przez działania związane z obsługą komunikatów po wykonaniu. Ma to zastosowanie do wszelkich działań związanych z obsługą komunikatów w tym samym zakresie co ta <xref:System.Activities.IExecutionProperty> implementacja. W szczególności, w tym przykładzie używa niestandardowego działania zakresu, aby wymusić zachowanie wywołania zwrotnego. Jest używany w przepływie pracy klienta w celu uwzględnienia <xref:System.Activities.WorkflowApplication.Id%2A> przepływu pracy jako wychodzącego <xref:System.ServiceModel.Channels.MessageHeader>. <xref:System.ServiceModel.Activities.ISendMessageCallback> Ten nagłówek jest następnie wybierany w usłudze przy użyciu <xref:System.ServiceModel.Activities.IReceiveMessageCallback> i wartość nagłówka jest drukowana do konsoli programu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Ten przykład uwidacznia usługę przepływu pracy za pomocą punktów końcowych HTTP. Aby uruchomić ten przykład, należy dodać odpowiednie listy ACL adresów URL (zobacz [Konfigurowanie protokołu HTTP i https](https://go.microsoft.com/fwlink/?LinkId=70353) w celu uzyskania szczegółowych informacji), uruchamiając program Visual Studio jako administrator lub wykonując następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień, aby dodać odpowiednie listy ACL. Upewnij się, że Twoja domena i nazwa użytkownika zostały zastąpione.  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. Po dodaniu list ACL adresów URL wykonaj następujące czynności.  
  
    1. Skompiluj rozwiązanie.  
  
    2. Aby ustawić wiele projektów uruchomieniowych, kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie **Ustaw projekty startowe**.  
  
    3. Dodaj **usługę** i **klienta** (w tej kolejności) jako wiele projektów początkowych.  
  
    4. Uruchom aplikację. W konsoli klienta zostanie uruchomiony przepływ pracy dwa razy, a w oknie usługi zostanie wyświetlony identyfikator wystąpienia tych przepływów pracy.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
