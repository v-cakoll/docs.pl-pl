---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: 5a2d190fe7dfd5305b47da0e6e67de822cfd695b
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424456"
---
# <a name="wshttpbinding"></a>WSHttpBinding
Ten przykład pokazuje, jak zaimplementować typową usługę i typowy klient przy użyciu Windows Communication Foundation (WCF). Ten przykład składa się z programu konsolowego klienta (Client. exe) i biblioteki usług hostowanej przez Internet Information Services (IIS). Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź. Kontrakt jest definiowany przez interfejs `ICalculator`, który udostępnia operacje matematyczne (Dodawanie, odejmowanie, mnożenie i dzielenie). Klient wykonuje synchroniczne żądania do danej operacji matematycznej, a usługa zwraca wynik. Aktywność klienta jest widoczna w oknie konsoli.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Ten przykład uwidacznia kontrakt `ICalculator` przy użyciu [\<WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Konfiguracja tego powiązania została rozwinięta w pliku Web. config.  
  
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
  
 W podstawowym elemencie `binding` wartość `maxReceivedMessageSize` umożliwia skonfigurowanie maksymalnego rozmiaru komunikatu przychodzącego (w bajtach). Wartość `hostNameComparisonMode` umożliwia skonfigurowanie, czy nazwa hosta jest brana pod uwagę podczas usuwania komunikatów do usługi. Wartość `messageEncoding` umożliwia skonfigurowanie, czy ma być używane kodowanie tekstu czy MTOM dla komunikatów. Wartość `textEncoding` umożliwia skonfigurowanie kodowania znaków dla komunikatów. Wartość `bypassProxyOnLocal` pozwala określić, czy serwer proxy HTTP ma być używany do komunikacji lokalnej. Wartość `transactionFlow` określa, czy bieżąca transakcja jest przepływa (jeśli operacja jest skonfigurowana dla przepływu transakcji).  
  
 W elemencie [\<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) wartość logiczna enabled określa, czy są włączone niezawodne sesje. Wartość `ordered` określa, czy porządkowanie wiadomości jest zachowywane. Wartość `inactivityTimeout` określa, jak długo sesja może być bezczynna, zanim zostanie uszkodzona.  
  
 Na [> zabezpieczeń\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)wartość `mode` służy do konfigurowania trybu zabezpieczeń, który ma być używany. W tym przykładzie zabezpieczenia komunikatów są używane, co oznacza, że [\<> komunikatów](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) jest określony w [> zabezpieczeń\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).  
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
