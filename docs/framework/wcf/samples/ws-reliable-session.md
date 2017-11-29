---
title: Sesja niezawodna WS
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
caps.latest.revision: "30"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ec04c91237516bcf535963c2d5ff7b0584c52be2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ws-reliable-session"></a>Sesja niezawodna WS
W przykładzie pokazano użycie niezawodnej sesji. Niezawodne sesje zapewniają obsługę niezawodna obsługa komunikatów i sesje. Niezawodna obsługa komunikatów ponowi próbę komunikacji w przypadku niepowodzenia i umożliwia gwarancje dostarczenia, należy określić, takich jak otrzymanie wiadomości w kolejności. Sesje przechowywania stanu dla klientów między wywołaniami. Próbka implementuje sesji do przechowywania stanu klienta i określa gwarancje dostarczenia w kolejności.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi Kalkulator. Funkcje niezawodnej sesji są włączone i skonfigurowane w plikach konfiguracji aplikacji dla klienta i usługi.  
  
 W tym przykładzie usługa jest obsługiwana w Internet Information Services (IIS) i klient jest aplikacji konsoli (.exe).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W przykładzie użyto `wsHttpBinding`. Powiązanie jest określona w plikach konfiguracji klienta i usługi. Typ powiązania jest określony w elemencie endpoint `binding` atrybutu, jak pokazano w poniższych Przykładowa konfiguracja.  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Zawiera punkt końcowy `bindingConfiguration` atrybut, który odwołuje się do konfiguracji powiązania o nazwie "Binding1." Konfiguracja powiązania umożliwia niezawodnej sesji przez ustawienie `enabled` atrybutu [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) do `true`. Gwarancje dostarczenia uporządkowanej sesji są kontrolowane przez ustawienie atrybutu uporządkowane na `true` lub `false`. Wartość domyślna to `true`.  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 Implementuje klasy implementacji usługi <xref:System.ServiceModel.InstanceContextMode.PerSession> wystąpień do obsługi wystąpienia klasy osobne dla każdego klienta, jak pokazano w poniższym kodzie próbki.  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```  
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też
