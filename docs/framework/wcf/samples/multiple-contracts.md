---
title: "Wiele kontraktów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfd9446edc176e3d4cb014db578990971128707c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="multiple-contracts"></a>Wiele kontraktów
Przykład wielu umów przedstawiono sposoby zaimplementować więcej niż jeden kontrakt na usługę oraz sposobu konfigurowania punktów końcowych do komunikowania się z każdym zaimplementowanych kontraktów. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Usługa została zmodyfikowana, aby zdefiniować dwa kontrakty `ICalculator` kontraktu i `ICalculatorSession` kontraktu.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Klasa usługi implementuje zarówno `ICalculator` i `ICalculatorSession` umów. Wymaga jednego umów sesji, dlatego usługa używa <xref:System.ServiceModel.InstanceContextMode.PerSession> tryb wystąpienia, aby zachować stan okresu istnienia sesji.  
  
 Konfiguracja usługi została zmodyfikowana, aby zdefiniować dwa punkty końcowe do udostępnienia każdej umowy. `ICalculator` Punktu końcowego jest uwidaczniany za pomocą adresu podstawowego `basicHttpBinding`. `ICalculatorSession` Punktu końcowego jest uwidaczniany za pomocą baseaddress/sesji `wsHttpBinding` z `bindingConfiguration` ustawić atrybutu `BindingWithSession`, jak pokazano w poniższych Przykładowa konfiguracja.  
  
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
  
 Kod wygenerowanego klienta zawiera teraz klasę klienta dla obu oryginalnej `ICalculator` kontraktu i nowych `ICalculatorSession` kontraktu. Konfiguracja klienta i kod został zmodyfikowany w celu komunikowania się z każdej umowy w punkcie końcowym odpowiednią usługę.  
  
 Klient jest aplikacji konsoli systemu windows (.exe). Usługa jest obsługiwana przez Internet Information Services (IIS).  
  
 Okno konsoli klienta Wyświetla operacje wysyłane do każdego z punktów końcowych, najpierw podstawowy punkt końcowy, następuje bezpiecznego punktu końcowego.  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
  
## <a name="see-also"></a>Zobacz też
