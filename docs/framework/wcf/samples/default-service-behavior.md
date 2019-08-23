---
title: Domyślne zachowanie usługi
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 31c6e0b8bf2b058fbefa76f48ade39ba8e7def69
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961769"
---
# <a name="default-service-behavior"></a>Domyślne zachowanie usługi
Ten przykład pokazuje, jak można skonfigurować ustawienia zachowania usługi. Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontrakt usługi. Ten przykład jawnie definiuje zachowania usługi i zachowania operacji przy użyciu <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutów <xref:System.ServiceModel.OperationBehaviorAttribute> i. Można skonfigurować zachowania w plikach konfiguracyjnych lub w sposób niezależny w kodzie (jak pokazano w tym przykładzie).  
  
 W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Klasa usługi określa zachowania z <xref:System.ServiceModel.ServiceBehaviorAttribute> i, <xref:System.ServiceModel.OperationBehaviorAttribute> jak pokazano w poniższym przykładzie kodu. Wszystkie określone wartości są wartościami domyślnymi.  
  
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
  
 Zachowania usługi są określane przy użyciu <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu. W poniższej tabeli opisano niektóre z tych zachowań.  
  
|Zachowanie usługi|Opis|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|Automatycznie zamyka sesję na żądanie klienta.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|Określa tryb współbieżności dla każdego wystąpienia usługi.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|Określa tryb kontekstu wystąpienia.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|Określa, czy należy użyć podanego kontekstu synchronizacji, jeśli został ustawiony. Użyj tego, jeśli chcesz kontrolować, czy należy używać `WindowsFormsSynchronizationContext` w Windows Forms aplikacji.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|Określa, czy ogólne Nieobsłużone wyjątki wykonywania mają być konwertowane do `Fault<string>` i wysyłane jako komunikat o błędzie.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|Określa poziom izolacji dla transakcji.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|Określa, czy nieoczekiwane nagłówki komunikatów powodują wystąpienie błędu.|  
  
 Zachowania operacji są określane przy użyciu <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutu. W poniższej tabeli opisano niektóre z tych zachowań.  
  
|Zachowanie operacji|Opis|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|Określa, czy zakończenie operacji usługi zatwierdza bieżącą transakcję.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|Określa, czy operacja usługi jest rejestrowana w transakcji przepływającej przez klienta.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|Określa, czy operacja usługi personifikuje tożsamość obiektu wywołującego.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|Określa, czy wystąpienia usługi są odtwarzane na początku, czy na końcu wywołania operacji usługi.|  
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Opóźnienie między wywołaniami to wynik wywołań `System.Threading.Thread.Sleep()` wykonanych w operacjach usługi. Pozostałe przykłady zachowania wyjaśniają te zachowania bardziej szczegółowo. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
