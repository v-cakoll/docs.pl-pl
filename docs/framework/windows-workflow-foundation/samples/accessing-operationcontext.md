---
title: Uzyskiwanie dostępu do elementu OperationContext
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: 83f3a6cacd3ee86050f65a886d446ab8da7d3690
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094712"
---
# <a name="accessing-operationcontext"></a>Uzyskiwanie dostępu do elementu OperationContext
W tym przykładzie pokazano, jak działania obsługi komunikatów (<xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.Send>) mogą być używane z niestandardowym działaniem zakresu w celu uzyskania dostępu do <xref:System.ServiceModel.OperationContext.Current%2A> i dołączania lub pobierania niestandardowego nagłówka wiadomości w wiadomości wychodzącej lub przychodzącej.  
  
## <a name="demonstrates"></a>Przedstawia  
 Działania dotyczące komunikatów, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.  
  
## <a name="discussion"></a>Dyskusji  
 Ten przykład pokazuje, jak używać punktów rozszerzalności (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) w działaniach obsługi komunikatów w celu uzyskania dostępu do <xref:System.ServiceModel.OperationContext.Current%2A>. Wywołania zwrotne są rejestrowane w czasie wykonywania przepływu pracy jako implementacja <xref:System.Activities.IExecutionProperty>, która jest pobierana przez działania związane z obsługą komunikatów po wykonaniu. Wszystkie działania związane z obsługą komunikatów w tym samym zakresie, w których zaimplementowano <xref:System.Activities.IExecutionProperty>. W szczególności, w tym przykładzie używa niestandardowego działania zakresu, aby wymusić zachowanie wywołania zwrotnego. <xref:System.ServiceModel.Activities.ISendMessageCallback> jest używana w przepływie pracy klienta w celu uwzględnienia <xref:System.Activities.WorkflowApplication.Id%2A> przepływu pracy jako <xref:System.ServiceModel.Channels.MessageHeader>wychodzącego. Ten nagłówek jest następnie wybierany w usłudze przy użyciu <xref:System.ServiceModel.Activities.IReceiveMessageCallback> i wartość nagłówka jest drukowana do konsoli.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Ten przykład uwidacznia usługę przepływu pracy za pomocą punktów końcowych HTTP. Aby uruchomić ten przykład, należy dodać odpowiednie listy ACL adresów URL (zobacz [Konfigurowanie protokołu HTTP i https](../../wcf/feature-details/configuring-http-and-https.md) w celu uzyskania szczegółowych informacji), uruchamiając program Visual Studio jako administrator lub wykonując następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień, aby dodać odpowiednie listy ACL. Upewnij się, że Twoja domena i nazwa użytkownika zostały zastąpione.  
  
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
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
