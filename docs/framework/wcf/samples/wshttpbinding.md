---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: a78eac52095d3f647efdacc9104a75e46651f389
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596374"
---
# <a name="wshttpbinding"></a>WSHttpBinding
Ten przykład pokazuje, jak zaimplementować typową usługę i typowy klient przy użyciu Windows Communication Foundation (WCF). Ten przykład składa się z programu konsolowego klienta (Client. exe) i biblioteki usług hostowanej przez Internet Information Services (IIS). Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź. Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (Dodawanie, odejmowanie, mnożenie i dzielenie). Klient wykonuje synchroniczne żądania do danej operacji matematycznej, a usługa zwraca wynik. Aktywność klienta jest widoczna w oknie konsoli.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Ten przykład uwidacznia `ICalculator` kontrakt przy użyciu [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) . Konfiguracja tego powiązania została rozwinięta w pliku Web. config.  
  
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
  
 W elemencie Base `binding` `maxReceivedMessageSize` wartość umożliwia skonfigurowanie maksymalnego rozmiaru komunikatu przychodzącego (w bajtach). `hostNameComparisonMode`Wartość umożliwia skonfigurowanie, czy nazwa hosta jest brana pod uwagę podczas usuwania komunikatów do usługi. `messageEncoding`Wartość umożliwia skonfigurowanie, czy ma być używane kodowanie tekstu czy MTOM dla komunikatów. `textEncoding`Wartość umożliwia skonfigurowanie kodowania znaków dla komunikatów. `bypassProxyOnLocal`Wartość umożliwia skonfigurowanie, czy serwer proxy HTTP ma być używany do komunikacji lokalnej. `transactionFlow`Wartość określa, czy bieżąca transakcja jest przepływa (Jeśli skonfigurowano operację przepływu transakcji).  
  
 W [\<reliableSession>](../../configure-apps/file-schema/wcf/reliablesession.md) elemencie włączona wartość logiczna określa, czy są włączone niezawodne sesje. `ordered`Wartość określa, czy porządkowanie wiadomości jest zachowywane. `inactivityTimeout`Wartość określa, jak długo sesja może być bezczynna, zanim zostanie uszkodzona.  
  
 W programie [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `mode` wartość określa, który tryb zabezpieczeń ma być używany. W tym przykładzie zabezpieczenia komunikatów są używane, co oznacza, że [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) jest określony wewnątrz [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) .  
  
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
  
2. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
