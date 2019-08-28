---
title: Sesja niezawodna WS
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: cc5afdeeeea2601eb22be316302aeacee570e5f7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045381"
---
# <a name="ws-reliable-session"></a>Sesja niezawodna WS
Ten przykład pokazuje użycie niezawodnych sesji. Niezawodne sesje zapewniają obsługę niezawodnej obsługi komunikatów i sesji. Niezawodna ponowna próba komunikacji przy niepowodzeń i pozwala określić gwarancje dostarczania, takie jak wysyłanie komunikatów. Sesje utrzymują stan dla klientów między wywołaniami. Przykład implementuje sesje do obsługi stanu klienta i określa gwarancje dostarczania w kolejności.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) , który implementuje usługę kalkulatora. Funkcje niezawodnej sesji są włączane i konfigurowane w plikach konfiguracji aplikacji dla klienta i usługi.  
  
 W tym przykładzie usługa jest hostowana w Internet Information Services (IIS), a klient jest aplikacją konsolową (. exe).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Przykład używa `wsHttpBinding`. Powiązanie jest określone w plikach konfiguracji zarówno dla klienta, jak i usługi. Typ powiązania jest określony w `binding` atrybucie elementu punktu końcowego, jak pokazano w poniższej konfiguracji przykładowej.  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Punkt końcowy zawiera `bindingConfiguration` atrybut odwołujący się do konfiguracji powiązania o nazwie "Binding1". Konfiguracja powiązania umożliwia niezawodne sesje przez ustawienie `enabled` atrybutu [ \<> ReliableSession](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) na. `true` Gwarancje dostarczania dla uporządkowanych sesji są kontrolowane przez ustawienie atrybutu uporządkowane `true` na `false`lub. Wartość domyślna to `true`.  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 Klasa implementacji usługi implementuje <xref:System.ServiceModel.InstanceContextMode.PerSession> Tworzenie wystąpień dla każdego klienta, jak pokazano w poniższym przykładowym kodzie.  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
