---
title: Użycie standardowych punktów końcowych
ms.date: 03/30/2017
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
ms.openlocfilehash: 2b210bfe683669aeebf54a1701f07d492e6abdb4
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715345"
---
# <a name="usage-of-standard-endpoints"></a>Użycie standardowych punktów końcowych

Ten przykład pokazuje, jak używać standardowych punktów końcowych w plikach konfiguracji usługi. Standardowy punkt końcowy umożliwia użytkownikowi uproszczenie definicji punktów końcowych przy użyciu pojedynczej właściwości do opisywania kombinacji adresu, powiązania i kontraktu z dodatkowymi skojarzonymi właściwościami. Ten przykład ilustruje sposób definiowania i implementowania niestandardowego standardowego punktu końcowego oraz sposobu definiowania określonych właściwości w punkcie końcowym.

## <a name="sample-details"></a>Przykładowe szczegóły

Punkty końcowe usługi można określić, dostarczając trzy parametry: Address, Binding i Contract. Inne parametry, które można podać, obejmują konfigurację zachowań, nagłówki, identyfikator URI nasłuchiwania i tak dalej. W niektórych przypadkach wszystkie lub wszystkie adresy, powiązania i kontrakty mają wartości, których nie można zmienić. Z tego powodu można używać standardowych punktów końcowych. Niektóre przykłady takich punktów końcowych obejmują punkty końcowe wymiany metadanych i punkty końcowe odnajdywania. Standardowe punkty końcowe również zwiększają użyteczność, umożliwiając Konfigurowanie punktów końcowych usługi bez konieczności dostarczania informacji o stałym charakterze lub do tworzenia własnych standardowych punktów końcowych, na przykład w celu poprawy użyteczności przez dostarczanie rozsądnego zestawu domyślnego wartości, co zmniejsza poziom szczegółowości plików konfiguracji.

Ten przykład składa się z dwóch projektów: usługi, która definiuje dwa standardowe punkty końcowe i klienta, który komunikuje się z usługą. W poniższym przykładzie pokazano sposób definiowania standardowych punktów końcowych dla usługi w pliku konfiguracji.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <extensions>
      <endpointExtensions>
        <add name="customEndpoint" type="Microsoft.Samples.StandardEndpoints.CustomEndpointCollectionElement, service" />
      </endpointExtensions>
    </extensions>
    <services>
      <service name="Microsoft.Samples.StandardEndpoints.CalculatorService">
        <endpoint address="http://localhost:8000/Samples/Service.svc/customEndpoint" contract="Microsoft.Samples.StandardEndpoints.ICalculator" kind="customEndpoint" />
        <endpoint kind="mexEndpoint" />
      </service>
    </services>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="True"/>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <standardEndpoints>
      <customEndpoint>
        <standardEndpoint property="True" />
      </customEndpoint>
    </standardEndpoints>
  </system.serviceModel>
</configuration>
```

Pierwszy punkt końcowy zdefiniowany dla usługi jest typu `customEndpoint`, którego definicja może być widoczna w sekcji `<standardEndpoints>`, w której Właściwość `property` ma daną wartość `true`. Jest to przypadek punktu końcowego dostosowany do nowej właściwości. Drugi punkt końcowy odpowiada punktowi końcowemu metadanych, w którym są naprawione wartości adresu, powiązania i kontraktu.

Aby zdefiniować standardowy element punktu końcowego, należy utworzyć klasę, która dziedziczy z `StandardEndpointElement`. W przypadku tego przykładu Klasa `CustomEndpointElement` została zdefiniowana, jak pokazano w poniższym przykładzie.

```csharp
public class CustomEndpointElement : StandardEndpointElement
{
    public bool Property
    {
        get { return (bool)base["property"]; }
        set { base["property"] = value; }
    }

    protected override ConfigurationPropertyCollection Properties
    {
        get
        {
            ConfigurationPropertyCollection properties = base.Properties;
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));
            return properties;
        }
    }

    protected override Type EndpointType
    {
        get { return typeof(CustomEndpoint); }
    }

    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)
    {
        return new CustomEndpoint();
    }

    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)
    {
    }

    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)
    {
    }
}
```

W funkcji `CreateServiceEndpoint` tworzony jest obiekt `CustomEndpoint`. Jego definicja jest pokazana w poniższym przykładzie:

```csharp
public class CustomEndpoint : ServiceEndpoint
{
    public CustomEndpoint()
        : this(string.Empty)
    {
    }

    public CustomEndpoint(string address)
        : this(address, ContractDescription.GetContract(typeof(ICalculator)))
    {
    }

    public CustomEndpoint(string address, ContractDescription contract)
        : base(contract)
    {
        this.Binding = new BasicHttpBinding();
        this.IsSystemEndpoint = false;
    }

    public bool Property
    {
        get;
        set;
    }
}
```

 W celu przeprowadzenia komunikacji między usługą a klientem do usługi jest tworzone odwołanie do usługi. Po skompilowaniu i wykonaniu przykładu usługa jest wykonywana i klient komunikuje się z nią. Należy pamiętać, że odwołanie do usługi powinno być aktualizowane za każdym razem, gdy w usłudze wprowadzono pewne zmiany.

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Za pomocą programu Visual Studio 2012 Otwórz plik StandardEndpoints. sln.

2. Włącz uruchamianie wielu projektów.

    1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy standardowe rozwiązanie punktów końcowych, a następnie wybierz polecenie **Właściwości**.

    2. W obszarze **wspólne właściwości**wybierz pozycję **projekt startowy**, a następnie kliknij pozycję **wiele projektów startowych**.

    3. Przenieś projekt usługi na początek listy z **akcją** ustawioną na wartość **Rozpocznij**.

    4. Przenieś projekt klienta po projekcie usługi, również z **akcją** ustawioną na wartość **Uruchom**.

         Oznacza to, że projekt klienta jest wykonywany po projekcie usługi.

3. Aby uruchomić rozwiązanie, naciśnij klawisz F5.

> [!NOTE]
> Jeśli te kroki nie działają, upewnij się, że środowisko zostało prawidłowo skonfigurowane, wykonując następujące czynności:
>
> 1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).
> 2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).
> 3. Aby uruchomić przykład w jednej lub wielu konfiguracjach komputera, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`
