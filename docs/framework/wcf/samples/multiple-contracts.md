---
title: Wiele kontraktów
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: 040ab9b80e9567139ca4588e3ddf83b8f43f2d76
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565984"
---
# <a name="multiple-contracts"></a>Wiele kontraktów
Wiele kontraktów w przykładzie pokazano, jak zaimplementować więcej niż jednego kontraktu usługi i sposobie konfigurowania punktów końcowych do komunikowania się z każdym zaimplementowane kontrakty. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Usługa została zmodyfikowana, aby zdefiniować dwa kontrakty `ICalculator` kontraktu i `ICalculatorSession` kontraktu.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Klasa usługi implementuje interfejsy `ICalculator` i `ICalculatorSession` umów. Jedną z umów wymagają sesję, dlatego usługa używa <xref:System.ServiceModel.InstanceContextMode.PerSession> tryb wystąpienia, aby utrzymywać stan przez cały okres istnienia sesji.  
  
 Konfiguracja usługi została zmodyfikowana, aby zdefiniować dwa punkty końcowe do udostępnienia każdej umowy. `ICalculator` Punkt końcowy jest uwidaczniany na adres bazowy przy użyciu `basicHttpBinding`. `ICalculatorSession` Punkt końcowy jest uwidaczniany w baseaddress/sesji przy użyciu `wsHttpBinding` z `bindingConfiguration` ustawioną wartość atrybutu `BindingWithSession`, jak pokazano na poniższym Przykładowa konfiguracja.  
  
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
  
 Wygenerowanego kodu klienta zawiera teraz klasę klienta dla zarówno oryginał `ICalculator` kontraktu i nowym `ICalculatorSession` kontraktu. Konfiguracja klienta i kod zostały zmodyfikowane w celu komunikowania się z każdej umowy w punkcie końcowym odpowiednią usługę.  
  
 Klient jest aplikacji konsoli systemu windows (.exe). Usługa jest hostowana przez Internetowe usługi informacyjne (IIS).  
  
 W oknie konsoli klienta wyświetlane operacje wysyłane do każdego z punktów końcowych, najpierw podstawowego punktu końcowego, następuje bezpiecznego punktu końcowego.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
  
## <a name="see-also"></a>Zobacz też
