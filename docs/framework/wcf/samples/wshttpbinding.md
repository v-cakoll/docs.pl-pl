---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: c54cbf1fe881ef2ce5dffb0bc0c6dac4049135b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143372"
---
# <a name="wshttpbinding"></a>WSHttpBinding
W tym przykładzie pokazano, jak zaimplementować typową usługę i typowego klienta przy użyciu programu Windows Communication Foundation (WCF). Ten przykład składa się z programu konsoli klienta (client.exe) i biblioteki usług hostowanych przez internetowe usługi informacyjne (IIS). Usługa implementuje kontrakt, który definiuje wzorzec komunikacji żądanie odpowiedź. Kontrakt jest definiowany `ICalculator` przez interfejs, który udostępnia operacje matematyczne (dodawanie, odejmowanie, mnożenie i dzielenie). Klient sprawia, że synchroniczne żądania do danej operacji matematycznej i odpowiedzi usługi z wynikiem. Aktywność klienta jest widoczna w oknie konsoli.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Ten przykład udostępnia `ICalculator` kontrakt przy użyciu [ \<>wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Konfiguracja tego powiązania została rozwinięta w pliku Web.config.  
  
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
  
 W elemencie podstawowym `binding` `maxReceivedMessageSize` wartość umożliwia skonfigurowanie maksymalnego rozmiaru wiadomości przychodzącej (w bajtach). Wartość `hostNameComparisonMode` umożliwia skonfigurowanie, czy nazwa hosta jest brana pod uwagę podczas od multipleksowania komunikatów do usługi. Wartość `messageEncoding` umożliwia skonfigurowanie, czy do używania kodowania tekstu lub MTOM dla wiadomości. Wartość `textEncoding` umożliwia skonfigurowanie kodowania znaków dla wiadomości. Wartość `bypassProxyOnLocal` umożliwia skonfigurowanie, czy ma być używany serwer proxy HTTP do komunikacji lokalnej. Wartość `transactionFlow` konfiguruje, czy bieżąca transakcja jest przepływa (jeśli operacja jest skonfigurowana dla przepływu transakcji).  
  
 W [ \<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) element włączone wartości logicznej konfiguruje, czy niezawodne sesje są włączone. Wartość `ordered` konfiguruje, czy kolejność wiadomości jest zachowywana. Wartość `inactivityTimeout` konfiguruje, jak długo sesja może być bezczynna przed błędem.  
  
 W [ \<>zabezpieczeń ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `mode` wartość konfiguruje, który tryb zabezpieczeń powinien być używany. W tym przykładzie używane są zabezpieczenia wiadomości, dlatego [ \<>wiadomości](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) jest określony wewnątrz [ \<>zabezpieczeń ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).  
  
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
