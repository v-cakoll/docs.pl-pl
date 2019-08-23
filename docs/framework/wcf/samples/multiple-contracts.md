---
title: Wiele kontraktów
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: 39970f9f0aefa46c3d064b39c9b35d195ef22843
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930363"
---
# <a name="multiple-contracts"></a>Wiele kontraktów
Przykład wielu kontraktów pokazuje, jak zaimplementować więcej niż jeden kontrakt w usłudze i jak skonfigurować punkty końcowe do komunikowania się z każdą z zaimplementowanych kontraktów. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Usługa została zmodyfikowana w celu zdefiniowania dwóch kontraktów `ICalculator` , kontraktu `ICalculatorSession` i kontraktu.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Klasa usługi implementuje zarówno `ICalculator` kontrakt, jak i. `ICalculatorSession` Ponieważ jeden z kontraktów wymaga sesji, usługa używa trybu wystąpienia, <xref:System.ServiceModel.InstanceContextMode.PerSession> aby zachować stan w okresie istnienia sesji.  
  
 Konfiguracja usługi została zmodyfikowana w celu zdefiniowania dwóch punktów końcowych, aby uwidocznić każdy kontrakt. Punkt końcowy jest uwidoczniony pod adresem podstawowym `basicHttpBinding`przy użyciu. `ICalculator` Punkt końcowy jest uwidaczniany w BaseAddress/sesji `wsHttpBinding` przy użyciu `bindingConfiguration` atrybutu z ustawionym na `BindingWithSession`, jak pokazano w poniższej konfiguracji przykładowej. `ICalculatorSession`  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- ICalculator endpoint is exposed using BasicBinding at the base  
       address provided by host:   
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- ICalculatorSession endpoint is exposed using BindingWithSession  
       at {baseaddress}/session:  
       http://localhost/servicemodelsamples/service.svc/session -->  
  <endpoint address="session"  
            binding="wsHttpBinding"  
            bindingConfiguration="BindingWithSession"   
           contract="Microsoft.ServiceModel.Samples.ICalculatorSession" />  
  ...  
</service>  
```  
  
 Wygenerowany kod klienta zawiera teraz klasę klienta zarówno dla oryginalnego `ICalculator` kontraktu, jak i nowego `ICalculatorSession` kontraktu. Konfiguracja i kod klienta zostały zmodyfikowane w celu komunikowania się z każdą umową w odpowiednim punkcie końcowym usługi.  
  
 Klient jest aplikacją dla systemu Windows (exe). Usługa jest hostowana przez Internet Information Services (IIS).  
  
 W oknie konsoli klienta są wyświetlane operacje wysyłane do poszczególnych punktów końcowych, pierwszy punkt końcowy podstawowego, a następnie bezpieczny punkt końcowy.  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
