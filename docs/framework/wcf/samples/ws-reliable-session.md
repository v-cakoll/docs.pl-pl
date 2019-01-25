---
title: Sesja niezawodna WS
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: 660fb9a7f60bc95a5039cdf3bad098c330ac969e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682684"
---
# <a name="ws-reliable-session"></a>Sesja niezawodna WS
Niniejszy przykład pokazuje użycie niezawodnej sesji. Sesje niezawodnej obsługi niezawodna obsługa komunikatów i sesji. Niezawodna obsługa komunikatów ponawia próbę komunikacji w przypadku niepowodzenia i umożliwia gwarancje dostarczenia, należy określić, takich jak otrzymanie wiadomości w kolejności. Sesje zarządzania stanem dla klientów między wywołaniami. Przykład implementuje sesje dotyczące utrzymania Stan klienta i określa gwarancje dostarczenia w określonej kolejności.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi kalkulatora. Funkcje niezawodnej sesji są włączone i skonfigurowane w plikach konfiguracji aplikacji dla klienta i usługi.  
  
 W tym przykładzie usługa jest hostowana w Internet Information Services (IIS), a klient to aplikacja konsoli (.exe).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 W przykładzie użyto `wsHttpBinding`. Powiązanie jest określona w plikach konfiguracyjnych dla klienta i usługi. Typ powiązania jest określony w elemencie punktu końcowego `binding` atrybutu, jak pokazano w poniższym Przykładowa konfiguracja.  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Punkt końcowy zawiera `bindingConfiguration` atrybut, który odwołuje się do konfiguracji powiązania o nazwie "Binding1." Konfiguracja powiązania umożliwia niezawodne sesje, ustawiając `enabled` atrybutu [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) do `true`. Gwarancje dostarczenia sesjach uporządkowanym są kontrolowane przez ustawienie atrybutu uporządkowane na `true` lub `false`. Wartość domyślna to `true`.  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 Klasa implementuje implementacji usługi <xref:System.ServiceModel.InstanceContextMode.PerSession> wystąpień do obsługi wystąpienia osobnej klasy dla każdego klienta, jak pokazano w poniższym przykładowym kodzie.  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, używając następującego polecenia.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz także
