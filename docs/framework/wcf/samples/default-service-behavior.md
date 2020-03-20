---
title: Domyślne zachowanie usługi
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 798231cbfddf17dd63a61f3e2a07a6490289e56f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183750"
---
# <a name="default-service-behavior"></a>Domyślne zachowanie usługi
W tym przykładzie pokazano, jak można skonfigurować ustawienia zachowania usługi. Próbka jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), `ICalculator` który implementuje umowy serwisowej. Ten przykład jawnie definiuje zachowania usługi i <xref:System.ServiceModel.ServiceBehaviorAttribute> zachowania <xref:System.ServiceModel.OperationBehaviorAttribute> operacji przy użyciu i atrybutów. Można skonfigurować zachowania w plikach konfiguracyjnych lub w trybie pilnym w kodzie (jak pokazuje ten przykład).  
  
 W tym przykładzie klient jest aplikacją konsoli (.exe), a usługa jest obsługiwana przez internetowe usługi informacyjne (IIS).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Klasa usługi określa zachowania z <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> jak pokazano w poniższym przykładzie kodu. Wszystkie określone wartości są wartościami domyślnymi.  
  
```csharp
[ServiceBehavior(  
    AutomaticSessionShutdown=true,  
    ConcurrencyMode=ConcurrencyMode.Single,  
    InstanceContextMode=InstanceContextMode.PerSession,  
    IncludeExceptionDetailInFaults=false,  
    UseSynchronizationContext=true,  
    ValidateMustUnderstand=true)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(  
        TransactionAutoComplete=true,  
        TransactionScopeRequired=false,  
        Impersonation=ImpersonationOption.NotAllowed)]  
    public double Add(double n1, double n2)  
    {  
        System.Threading.Thread.Sleep(1600);  
        return n1 + n2;  
    }  
    ...  
}  
```  
  
 Zachowania usługi są określone <xref:System.ServiceModel.ServiceBehaviorAttribute> za pomocą atrybutu. W poniższej tabeli opisano niektóre z tych zachowań.  
  
|Zachowanie usługi|Opis|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|Automatycznie zamyka sesję na żądanie klienta.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|Określa tryb współbieżności dla każdego wystąpienia usługi.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|Określa tryb kontekstu wystąpienia.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|Określa, czy należy użyć podanego kontekstu synchronizacji, jeśli jest ustawiony. Użyj tego, aby kontrolować, czy `WindowsFormsSynchronizationContext` w aplikacjach Windows Forms ma być używana aplikacja Windows Forms.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|Określa, czy ogólne nieobsługiwać wyjątki wykonywania `Fault<string>` mają być konwertowane na a i wysyłane jako komunikat o błędzie.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|Określa poziom izolacji dla transakcji.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|Określa, czy nieoczekiwane nagłówki wiadomości powodują stan błędu.|  
  
 Zachowania operacji są określane <xref:System.ServiceModel.OperationBehaviorAttribute> przy użyciu atrybutu. W poniższej tabeli opisano niektóre z tych zachowań.  
  
|Zachowanie operacji|Opis|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|Określa, czy zakończenie operacji usługi zatwierdza bieżącą transakcję.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|Określa, czy operacja usługi rejestruje się w transakcji przepływanych przez klienta.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|Określa, czy operacja usługi personifikuje tożsamość wywołującego.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|Określa, czy wystąpienia usługi są odtwo cenach odtworzyć na początku lub na końcu wywołania operacji usługi.|  
  
 Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Opóźnienie między wywołaniami jest wynikiem `System.Threading.Thread.Sleep()` wywołań w operacjach usługi. Pozostałe przykłady zachowania wyjaśnić te zachowania bardziej szczegółowo. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
