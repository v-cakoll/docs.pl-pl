---
title: Sesja niezawodna WS
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: 8898dfedc6ba7deceb5a6e6856b7c7e6ad79d047
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143502"
---
# <a name="ws-reliable-session"></a>Sesja niezawodna WS
W tym przykładzie pokazano użycie niezawodnych sesji. Niezawodne sesje zapewniają obsługę niezawodnych wiadomości i sesji. Niezawodne wiadomości ponawia komunikację w przypadku awarii i umożliwia zapewnienie dostarczania, takie jak najaśledzenie wiadomości w kolejności. Sesje utrzymują stan dla klientów między wywołaniami. Przykład implementuje sesje do utrzymania stanu klienta i określa gwarancje dostarczania w kolejności.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 Ten przykład jest oparty na [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md) który implementuje usługę kalkulatora. Niezawodne funkcje sesji są włączone i konfigurowane w plikach konfiguracyjnych aplikacji dla klienta i usługi.  
  
 W tym przykładzie usługa jest hostowana w internetowych usługach informacyjnych (IIS), a klient jest aplikacją konsoli (.exe).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W próbce `wsHttpBinding`użyto pliku . Powiązanie jest określone w plikach konfiguracyjnych dla klienta i usługi. Typ powiązania jest określony w atrybucie elementu punktu końcowego, `binding` jak pokazano w poniższej konfiguracji przykładowej.  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Punkt końcowy zawiera `bindingConfiguration` atrybut, który odwołuje się do konfiguracji powiązania o nazwie "Binding1". Konfiguracja wiązania umożliwia niezawodne `enabled` sesje, ustawiając atrybut [ \<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) do `true`. Gwarancje dostawy dla zamówionych sesji są kontrolowane `true` `false`przez ustawienie zamówionego atrybutu na lub . Wartość domyślna to `true`.  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 Klasa implementacji usługi <xref:System.ServiceModel.InstanceContextMode.PerSession> implementuje instancing do obsługi wystąpienia klasy oddzielne dla każdego klienta, jak pokazano w poniższym przykładowym kodzie.  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Zainstaluj ASP.NET 4.0 za pomocą następującego polecenia.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
