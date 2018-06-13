---
title: Uproszczona konfiguracja usług WCF
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 80e2ac83ec0e07176d6afe6d34c63fb4d8e836d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502267"
---
# <a name="simplified-configuration-for-wcf-services"></a>Uproszczona konfiguracja usług WCF
W tym przykładzie pokazano, jak wdrożyć i skonfigurować typowe usługi i klienta przy użyciu usługi Windows Communication Foundation (WCF). W tym przykładzie stanowi podstawę dla wszystkich innych przykładów podstawową technologię.  
  
 Uproszczona konfiguracja w korzysta z tej usługi, który udostępnia punktu końcowego w celu komunikowania się z usługą, [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]. Przed [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], punkt końcowy jest zazwyczaj definiowane w pliku konfiguracyjnym (Web.config), jak pokazano w poniższym kodzie konfiguracji przykład.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright ©) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Samples.GettingStarted.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <endpoint address="" binding="basicHttpBinding" contract="ICalculator"/>  
        <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 W [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], `<service>` element jest opcjonalny. Jeśli usługi nie definiuje żadnych punktów końcowych, dla każdego adresu podstawowego i zaimplementowana kontraktu punktu końcowego są dodawane do usługi. Adres podstawowy jest dołączany do nazwy kontraktu, aby ustalić punktu końcowego i powiązania jest określany przez schemat adresów. W poniższym przykładzie przedstawiono plik konfiguracji uproszczone. Zgodnie z konfiguracją, usługi mogą być wyświetlane w http://localhost/servicemodelsamples/service.svc przez klienta na tym samym komputerze. Dla klientów na komputerach zdalnych do uzyskania dostępu do usługi należy określić w pełni kwalifikowanej nazwy domeny zamiast nazwy localhost. Domyślnie usługa nie uwidacznia metadanych. W efekcie usługa włącza <xref:System.ServiceModel.Description.ServiceMetadataBehavior> zachowanie.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright © Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Uruchom próbkę, wykonaj następujące czynności:  
  
    1.  Kliknij prawym przyciskiem myszy **usługi** projekt i wybierz **Ustaw jako projekt startowy**, naciśnij klawisz **Ctrl + F5**.  
  
    2.  Poczekaj na dane wyjściowe konsoli potwierdzenie, że usługa działa i uruchomiona.  
  
    3.  Kliknij prawym przyciskiem myszy **klienta** projekt i wybierz **Ustaw jako projekt startowy**, naciśnij klawisz **Ctrl + F5**.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady zarządzania AppFabric](http://go.microsoft.com/fwlink/?LinkId=193960)  
 [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)
