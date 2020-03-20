---
title: Wiele kontraktów
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: ed59803b867dfe7994aceea010aa656c53927a0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144347"
---
# <a name="multiple-contracts"></a>Wiele kontraktów
Przykład wielu kontraktów pokazuje, jak zaimplementować więcej niż jedną umowę w usłudze i jak skonfigurować punkty końcowe do komunikowania się z każdym z zaimplementowanych kontraktów. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Usługa została zmodyfikowana w celu zdefiniowania dwóch umów, `ICalculator` umowy i `ICalculatorSession` umowy.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Klasa usługi implementuje `ICalculator` zarówno `ICalculatorSession` i kontrakty. Ponieważ jedna z umów wymaga sesji, usługa <xref:System.ServiceModel.InstanceContextMode.PerSession> używa trybu wystąpienia, aby utrzymać stan przez cały okres istnienia sesji.  
  
 Konfiguracja usługi została zmodyfikowana w celu zdefiniowania dwóch punktów końcowych, aby udostępnić każdy kontrakt. Punkt `ICalculator` końcowy jest narażony na `basicHttpBinding`adres podstawowy przy użyciu pliku . Punkt `ICalculatorSession` końcowy jest narażony na adres podstawowy/sesję `bindingConfiguration` przy użyciu `BindingWithSession` `wsHttpBinding` atrybutu ustawionego na , jak pokazano w poniższej konfiguracji przykładowej.  
  
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
  
 Wygenerowany kod klienta zawiera teraz klasę `ICalculator` klienta dla `ICalculatorSession` oryginalnego kontraktu i nowego kontraktu. Konfiguracja klienta i kod zostały zmodyfikowane w celu komunikowania się z każdą umową w odpowiednim punkcie końcowym usługi.  
  
 Klient jest aplikacją konsoli systemu Windows (.exe). Usługa jest obsługiwana przez internetowe usługi informacyjne (IIS).  
  
 Okno konsoli klienta wyświetla operacje wysyłane do każdego z punktów końcowych, najpierw podstawowy punkt końcowy, a następnie bezpieczny punkt końcowy.  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
