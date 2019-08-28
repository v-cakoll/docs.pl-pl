---
title: Uproszczona konfiguracja usług WCF
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 57aa92eb0a2978ab463c368ed70fb298cc5fb90d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038859"
---
# <a name="simplified-configuration-for-wcf-services"></a>Uproszczona konfiguracja usług WCF
Ten przykład pokazuje, jak zaimplementować i skonfigurować typową usługę i klienta przy użyciu Windows Communication Foundation (WCF). Ten przykład jest podstawą dla wszystkich innych podstawowych przykładów technologii.  
  
 Ta usługa, która udostępnia punkt końcowy do komunikacji z usługą, używa uproszczonej konfiguracji w programie [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]. W systemach starszych niż ,punktkońcowyjestzwykledefiniowanywplikukonfiguracji(Web.config),jakpokazanowponiższymprzykładowymkodziekonfiguracyjnym.[!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]  
  
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
  
 W programie [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]elementjestopcjonalny `<service>` . Gdy usługa nie definiuje żadnych punktów końcowych, do usługi są dodawane punkty końcowe dla każdego adresu podstawowego i zaimplementowanego kontraktu. Adres podstawowy jest dołączany do nazwy kontraktu w celu określenia punktu końcowego i powiązania jest określany przez schemat adresu. Poniższy przykład kodu demonstruje uproszczony plik konfiguracji. Zgodnie z konfiguracją usługa może być dostępna `http://localhost/servicemodelsamples/service.svc` przez klienta programu na tym samym komputerze. Aby klienci na komputerach zdalnych mogli uzyskać dostęp do usługi, należy określić w pełni kwalifikowaną nazwę domeny zamiast hosta lokalnego. Usługa domyślnie nie uwidacznia metadanych. W związku z tym usługa włącza <xref:System.ServiceModel.Description.ServiceMetadataBehavior> zachowanie.  
  
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
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Uruchom przykład, wykonując następujące czynności:  
  
    1. Kliknij prawym przyciskiem myszy projekt **usługi** i wybierz pozycję **Ustaw jako projekt startowy**, a następnie naciśnij **klawisze CTRL + F5**.  
  
    2. Poczekaj, aż dane wyjściowe konsoli potwierdzają, że usługa jest uruchomiona.  
  
    3. Kliknij prawym przyciskiem myszy projekt **klienta** i wybierz pozycję **Ustaw jako projekt startowy**, a następnie naciśnij **klawisze CTRL + F5**.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady zarządzania dla oprogramowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193960)
- [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)
