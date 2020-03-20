---
title: Uzyskiwanie dostępu do elementu OperationContext
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: 5a2731c7918c216221b0adcafd5c804e80f36dfb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182860"
---
# <a name="accessing-operationcontext"></a>Uzyskiwanie dostępu do elementu OperationContext
W tym przykładzie pokazano,<xref:System.ServiceModel.Activities.Receive> jak <xref:System.ServiceModel.Activities.Send>działania obsługi wiadomości ( i <xref:System.ServiceModel.OperationContext.Current%2A> ) mogą być używane z działaniem zakresu niestandardowego, aby uzyskać dostęp do i dołączyć lub pobrać niestandardowy nagłówek wiadomości w wiadomości wychodzącej lub przychodzącej.  
  
## <a name="demonstrates"></a>Demonstracje  
 Działania związane <xref:System.ServiceModel.Activities.ISendMessageCallback>z <xref:System.ServiceModel.Activities.IReceiveMessageCallback>komunikacją informacyjną, , .  
  
## <a name="discussion"></a>Dyskusji  
 W tym przykładzie pokazano, jak<xref:System.ServiceModel.Activities.ISendMessageCallback> <xref:System.ServiceModel.Activities.IReceiveMessageCallback>używać punktów rozszerzalności ( <xref:System.ServiceModel.OperationContext.Current%2A>) ) w działaniach obsługi wiadomości, aby uzyskać dostęp . Wywołania zwrotne są rejestrowane w środowisku wykonawczym przepływu pracy jako <xref:System.Activities.IExecutionProperty> implementacja, która jest pobierana przez działania obsługi wiadomości po wykonaniu. Wpływa na wszelkie działania obsługi <xref:System.Activities.IExecutionProperty> wiadomości w tym samym zakresie, co ta implementacja. W szczególności w tym przykładzie używa działania zakresu niestandardowego, aby wymusić zachowanie wywołania zwrotnego. Jest <xref:System.ServiceModel.Activities.ISendMessageCallback> używany w przepływie pracy klienta, aby <xref:System.Activities.WorkflowApplication.Id%2A> uwzględnić <xref:System.ServiceModel.Channels.MessageHeader>przepływ pracy jako wychodzące . Ten nagłówek jest następnie pobierany <xref:System.ServiceModel.Activities.IReceiveMessageCallback> w usłudze przy użyciu i wartość nagłówka jest drukowana na konsoli.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. W tym przykładzie udostępnia usługę przepływu pracy przy użyciu punktów końcowych HTTP. Aby uruchomić ten przykład, należy dodać odpowiednie listy ACL adresów URL (zobacz [Konfigurowanie protokołu HTTP i HTTPS](../../wcf/feature-details/configuring-http-and-https.md) w celu uzyskania szczegółowych informacji), uruchamiając program Visual Studio jako administrator lub wykonując następujące polecenie z podwyższonym poziomem uprawnień, aby dodać odpowiednie listy ACL. Upewnij się, że twoja domena i nazwa użytkownika są podstawione.  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. Po dodaniu list ACL url należy wykonać następujące czynności.  
  
    1. Skompiluj rozwiązanie.  
  
    2. Ustaw wiele projektów start-upów, klikając prawym przyciskiem myszy rozwiązanie i wybierając **pozycję Ustaw projekty startowe**.  
  
    3. Dodaj **usługę** i **klienta** (w tej kolejności) jako wiele projektów startowych.  
  
    4. Uruchom aplikację. Konsola klienta pokazuje przepływ pracy uruchomiony dwa razy, a okno Usługa pokazuje identyfikator wystąpienia tych przepływów pracy.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
