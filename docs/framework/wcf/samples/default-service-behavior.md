---
title: "Domyślne zachowanie usługi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 57d534a1af16790aa6c3477629f0d4b6e2604179
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="default-service-behavior"></a>Domyślne zachowanie usługi
W przykładzie pokazano, jak można skonfigurować ustawienia zachowania usługi. Próbki jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontraktu usługi. W tym przykładzie jawnie definiuje zachowania usługi i zachowania operację przy użyciu <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutów. Zachowania można skonfigurować w plikach konfiguracji lub imperatively w kodzie (jak pokazano w przykładzie).  
  
 W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana przez Internet Information Services (IIS).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Klasa usługi określa zachowania z <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> jak pokazano w poniższym przykładzie kodu. Wszystkie wartości są ustawienia domyślne.  
  
```  
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
  
 Zachowania usług są określane za pomocą <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu. W poniższej tabeli opisano niektóre z tych zachowań.  
  
|Zachowanie usługi|Opis|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|Automatycznie zamknięty sesji w żądaniu klienta.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|Określa tryb współbieżności dla każdego wystąpienia usługi.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|Określa tryb kontekstu wystąpienia.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|Określa, czy używać kontekstu synchronizacji podany, jeśli jest on ustawiony. Użyj go, jeśli chcesz określić, czy używać `WindowsFormsSynchronizationContext` w aplikacjach formularzy systemu Windows.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|Określa, czy Wyjątki ogólne nieobsłużonego są do przekonwertowania na `Fault<string>` i wysłany jako komunikat o błędzie.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|Określa poziom izolacji transakcji.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|Określa, czy nagłówki nieoczekiwany komunikat spowodować wystąpienie stanu błędu.|  
  
 Operacja zachowania są określane przy użyciu <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutu. W poniższej tabeli opisano niektóre z tych zachowań.  
  
|Zachowanie działania|Opis|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|Określa, czy zakończenie operacji usługi zatwierdza bieżącej transakcji.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|Określa, czy operacja usługi powoduje zarejestrowanie w transakcji przepływ klienta.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|Określa, czy operacja usługi personifikuje tożsamości obiektu wywołującego.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|Określa, czy wystąpienie usługi są odtwarzania początek lub koniec wywołania operacji usługi.|  
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Opóźnienie między wywołaniami jest wynikiem wywołania `System.Threading.Thread.Sleep()` w operacji usługi. Pozostałe przykłady zachowanie opisano te zachowania bardziej szczegółowo. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
  
## <a name="see-also"></a>Zobacz też
