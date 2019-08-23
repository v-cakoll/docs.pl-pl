---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: 5d76cb2e4d9f3173c1eb3fda45e1f1c65efeadde
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959821"
---
# <a name="wshttpbinding"></a>WSHttpBinding
Ten przykład pokazuje, jak zaimplementować typową usługę i typowy klient przy użyciu Windows Communication Foundation (WCF). Ten przykład składa się z programu konsolowego klienta (Client. exe) i biblioteki usług hostowanej przez Internet Information Services (IIS). Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź. Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (Dodawanie, odejmowanie, mnożenie i dzielenie). Klient wykonuje synchroniczne żądania do danej operacji matematycznej, a usługa zwraca wynik. Aktywność klienta jest widoczna w oknie konsoli.  
  
> [!IMPORTANT]
>  Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Ten przykład uwidacznia `ICalculator` kontrakt [ \<przy użyciu > WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Konfiguracja tego powiązania została rozwinięta w pliku Web. config.  
  
```xml
<bindings>  
  <wsHttpBinding>  
    <!--The following is the expanded configuration section for a-->  
    <!--WSHttpBinding. Each property is configured with the default-->   
    <!--value. See the ReliableSession, TransactionFlow, -->  
    <!--TransportSecurity, and MessageSecurity samples in the WS -->  
    <!--directory to learn how to configure these features. -->  
    <binding name="Binding1"  
              bypassProxyOnLocal="false"   
              transactionFlow="false"   
              hostNameComparisonMode="StrongWildcard"  
              maxBufferPoolSize="524288"   
              maxReceivedMessageSize="65536"  
              messageEncoding="Text"   
              textEncoding="utf-8"   
              useDefaultWebProxy="true"  
              allowCookies="false">  
      <reliableSession ordered="true"   
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Message">  
        <message clientCredentialType="Windows"   
                 negotiateServiceCredential="true"  
                 algorithmSuite="Default"   
                 establishSecurityContext="true" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 W elemencie `binding` `maxReceivedMessageSize` Base wartość umożliwia skonfigurowanie maksymalnego rozmiaru komunikatu przychodzącego (w bajtach). `hostNameComparisonMode` Wartość umożliwia skonfigurowanie, czy nazwa hosta jest brana pod uwagę podczas usuwania komunikatów do usługi. `messageEncoding` Wartość umożliwia skonfigurowanie, czy ma być używane kodowanie tekstu czy MTOM dla komunikatów. `textEncoding` Wartość umożliwia skonfigurowanie kodowania znaków dla komunikatów. `bypassProxyOnLocal` Wartość umożliwia skonfigurowanie, czy serwer proxy HTTP ma być używany do komunikacji lokalnej. `transactionFlow` Wartość określa, czy bieżąca transakcja jest przepływa (Jeśli skonfigurowano operację przepływu transakcji).  
  
 W elemencie ReliableSession > wartość włączone wartości logicznej określa, czy są włączone niezawodne sesje. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) Wartość `ordered` określa, czy porządkowanie wiadomości jest zachowywane. `inactivityTimeout` Wartość określa, jak długo sesja może być bezczynna, zanim zostanie uszkodzona.  
  
 Na > `mode` zabezpieczenia służy do konfigurowania trybu zabezpieczeń, który ma być używany. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) W tym przykładzie zabezpieczenia komunikatów są używane, co oznacza, że [ \<komunikat >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)jest określony wewnątrz > zabezpieczeń.  
  
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
