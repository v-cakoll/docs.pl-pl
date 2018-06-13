---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: d76ec0292ea6f8143e641b771daeac8975e91b02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33505443"
---
# <a name="wshttpbinding"></a>WSHttpBinding
W tym przykładzie pokazano, jak do zaimplementowania typowych usługi i typowego klienta za pomocą usługi Windows Communication Foundation (WCF). W tym przykładzie składa się z konsoli programu klienckiego (client.exe) i biblioteki usługi hostowanej przez Internetowe usługi informacyjne (IIS). Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź. Kontrakt jest definiowana za pomocą `ICalculator` interfejsu, który udostępnia operacji matematycznych (Dodawanie, odjąć mnożenia i dzielenia). Klient wysyła żądań synchronicznych operacji matematycznych danego i odpowiedzi usługi z wynikiem. Aktywność klienta jest widoczna w oknie konsoli.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Ten przykład przedstawia `ICalculator` kontraktu przy użyciu [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). W pliku Web.config została rozszerzona konfiguracji tego powiązania.  
  
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
  
 Na podstawie `binding` elementu `maxReceivedMessageSize` wartość można skonfigurować maksymalny rozmiar wiadomości przychodzącej (w bajtach). `hostNameComparisonMode` Wartość umożliwia skonfigurowanie, czy nazwa hosta jest uznawany za podczas usuwania Multipleksowanie komunikaty do usługi. `messageEncoding` Wartość umożliwia skonfigurowanie, czy ma być używany tekst lub MTOM kodowania dla wiadomości. `textEncoding` Wartość umożliwia konfigurowanie kodowanie znaków dla wiadomości. `bypassProxyOnLocal` Wartość umożliwia skonfigurowanie, czy używany serwer proxy HTTP do lokalnej komunikacji. `transactionFlow` Wartość określa, czy bieżąca transakcja jest umieszczane (Jeśli operacja jest skonfigurowana dla przepływu transakcji).  
  
 Na [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) elementu włączone wartość logiczna określa, czy włączono niezawodnej sesji. `ordered` Wartość określa, czy komunikat kolejność jest zachowywana. `inactivityTimeout` Wartość określa, jak długo sesja może być bezczynne przed jest błędny.  
  
 Na [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), `mode` wartość konfiguruje tryb zabezpieczeń, którym powinien być używany. W tym przykładzie zabezpieczeń wiadomości jest używany, która jest dlaczego [ \<wiadomości >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) określono wewnątrz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).  
  
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
