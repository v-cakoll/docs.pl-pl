---
title: Uproszczona konfiguracja usług WCF
description: Dowiedz się, jak zaimplementować i skonfigurować typową usługę i klienta przy użyciu programu WCF. Usługa komunikuje się za pomocą punktu końcowego określonego w pliku konfiguracji.
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 46a0c878b29de34219413a508799ddaddf507dd8
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246223"
---
# <a name="simplified-configuration-for-wcf-services"></a>Uproszczona konfiguracja usług WCF
Ten przykład pokazuje, jak zaimplementować i skonfigurować typową usługę i klienta przy użyciu Windows Communication Foundation (WCF). Ten przykład jest podstawą dla wszystkich innych podstawowych przykładów technologii.  
  
 Ta usługa, która udostępnia punkt końcowy do komunikacji z usługą, używa uproszczonej konfiguracji w .NET Framework 4. Przed .NET Framework 4 punkt końcowy jest zwykle definiowany w pliku konfiguracji (Web.config), jak pokazano w poniższym przykładowym kodzie konfiguracyjnym.  
  
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
  
 W .NET Framework 4 `<service>` element jest opcjonalny. Gdy usługa nie definiuje żadnych punktów końcowych, do usługi są dodawane punkty końcowe dla każdego adresu podstawowego i zaimplementowanego kontraktu. Adres podstawowy jest dołączany do nazwy kontraktu w celu określenia punktu końcowego i powiązania jest określany przez schemat adresu. Poniższy przykład kodu demonstruje uproszczony plik konfiguracji. Zgodnie z konfiguracją usługa może być dostępna `http://localhost/servicemodelsamples/service.svc` przez klienta programu na tym samym komputerze. Aby klienci na komputerach zdalnych mogli uzyskać dostęp do usługi, należy określić w pełni kwalifikowaną nazwę domeny zamiast hosta lokalnego. Usługa domyślnie nie uwidacznia metadanych. W związku z tym usługa włącza <xref:System.ServiceModel.Description.ServiceMetadataBehavior> zachowanie.  
  
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
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
3. Uruchom przykład, wykonując następujące czynności:  
  
    1. Kliknij prawym przyciskiem myszy projekt **usługi** i wybierz pozycję **Ustaw jako projekt startowy**, a następnie naciśnij **klawisze CTRL + F5**.  
  
    2. Poczekaj, aż dane wyjściowe konsoli potwierdzają, że usługa jest uruchomiona.  
  
    3. Kliknij prawym przyciskiem myszy projekt **klienta** i wybierz pozycję **Ustaw jako projekt startowy**, a następnie naciśnij **klawisze CTRL + F5**.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>Zobacz też

- [Przykłady zarządzania dla oprogramowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))
- [Uproszczona konfiguracja](../simplified-configuration.md)
