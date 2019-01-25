---
title: Uproszczona konfiguracja usług WCF
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: c0d5f46e6ace71ad4732f8d387b3289b1d4105e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516372"
---
# <a name="simplified-configuration-for-wcf-services"></a>Uproszczona konfiguracja usług WCF
W tym przykładzie pokazano, jak zaimplementować i skonfigurować typowe usługi i klienta przy użyciu usługi Windows Communication Foundation (WCF). Te przykładowe dane stanowią podstawę dla wszystkich przykładów podstawową technologię.  
  
 Uproszczona konfiguracja w korzysta z tej usługi, który uwidacznia punkt końcowy w celu komunikowania się z usługą, [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]. Przed [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], punkt końcowy jest zazwyczaj definiowane w pliku konfiguracji (Web.config), jak pokazano w poniższym kodzie przykładu w konfiguracji.  
  
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
  
 W [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], `<service>` element jest opcjonalne. Jeśli usługi nie definiuje żadnych punktów końcowych, punkt końcowy dla każdego adresu podstawowego i zaimplementować kontrakt są dodawane do usługi. Adres podstawowy jest dołączany do nazwy kontraktu, aby ustalić punkt końcowy, a następnie powiązanie jest określana przez schemat adresów. Poniższy przykład kodu demonstruje pliku uproszczona konfiguracja. Zgodnie z konfiguracją, usługi mogą być wyświetlane w `http://localhost/servicemodelsamples/service.svc` przez klienta na tym samym komputerze. W przypadku klientów na komputerach zdalnych w celu uzyskania dostępu do usługi należy określić w pełni kwalifikowanej nazwy domeny zamiast nazwy localhost. Domyślnie usługa nie ujawnia metadanych. W efekcie usługa włącza <xref:System.ServiceModel.Description.ServiceMetadataBehavior> zachowanie.  
  
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
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Uruchom aplikację przykładową, wykonaj następujące czynności:  
  
    1.  Kliknij prawym przyciskiem myszy **usługi** projektu, a następnie wybierz **Ustaw jako projekt startowy**, naciśnij klawisz **kombinację klawiszy Ctrl + F5**.  
  
    2.  Poczekaj, aż dane wyjściowe konsoli z potwierdzenie, że usługa działa i uruchomiony.  
  
    3.  Kliknij prawym przyciskiem myszy **klienta** projektu, a następnie wybierz **Ustaw jako projekt startowy**, naciśnij klawisz **kombinację klawiszy Ctrl + F5**.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>Zobacz także
- [Przykładami dotyczącymi zarządzania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193960)
- [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)
