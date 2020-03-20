---
title: Uproszczona konfiguracja usług WCF
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: f3c4df5ae3fe5426c8b26142807f16b60db001c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183353"
---
# <a name="simplified-configuration-for-wcf-services"></a>Uproszczona konfiguracja usług WCF
W tym przykładzie pokazano, jak zaimplementować i skonfigurować typową usługę i klienta przy użyciu programu Windows Communication Foundation (WCF). Ta próbka jest podstawą dla wszystkich innych próbek technologii podstawowej.  
  
 Ta usługa, która udostępnia punkt końcowy do komunikowania się z usługą, używa uproszczonej konfiguracji w programie .NET Framework 4. Przed programem .NET Framework 4 punkt końcowy jest zazwyczaj definiowany w pliku konfiguracyjnym (Web.config), jak pokazano w poniższym przykładowym kodzie konfiguracji.  
  
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
  
 W .NET Framework 4 `<service>` element jest opcjonalny. Gdy usługa nie definiuje żadnych punktów końcowych, punkt końcowy dla każdego adresu podstawowego i umowy zaimplementowane są dodawane do usługi. Adres podstawowy jest dołączany do nazwy kontraktu w celu określenia punktu końcowego, a powiązanie jest określane przez schemat adresów. Poniższy przykład kodu pokazuje uproszczony plik konfiguracji. Zgodnie z konfiguracją, usługa jest `http://localhost/servicemodelsamples/service.svc` dostępna dla klienta na tym samym komputerze. Aby klienci na komputerach zdalnych mogli uzyskać dostęp do usługi, zamiast hosta lokalnego należy określić w pełni kwalifikowaną nazwę domeny. Usługa domyślnie nie udostępnia metadanych. W związku z tym <xref:System.ServiceModel.Description.ServiceMetadataBehavior> usługa włącza zachowanie.  
  
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
  
### <a name="to-use-this-sample"></a>Aby użyć tej próbki  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Uruchom próbkę, wykonując następujące kroki:  
  
    1. Kliknij prawym przyciskiem myszy projekt **usługi** i wybierz pozycję **Ustaw jako projekt startowy,** a następnie naciśnij **klawisze Ctrl+F5**.  
  
    2. Poczekaj na wyjście konsoli potwierdzające, że usługa jest uruchomiona.  
  
    3. Kliknij prawym przyciskiem myszy projekt **klienta** i wybierz polecenie **Ustaw jako projekt startowy,** a następnie naciśnij **klawisze Ctrl+F5**.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>Zobacz też

- [Przykłady zarządzania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))
- [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)
