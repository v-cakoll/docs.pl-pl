---
title: Użycie standardowych punktów końcowych
ms.date: 03/30/2017
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
ms.openlocfilehash: 4ef0714acad12db1414e34fbb476b4ae7d1d9fb2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006341"
---
# <a name="usage-of-standard-endpoints"></a>Użycie standardowych punktów końcowych

W tym przykładzie pokazano, jak używać standardowych punktów końcowych w plikach konfiguracji usługi. Standardowy punkt końcowy umożliwia użytkownikowi Uprość definicji punktów końcowych przy użyciu pojedynczej właściwości do opisania za pomocą dodatkowych właściwości skojarzone z jego adres, powiązania i umowy. Niniejszy przykład pokazuje, jak definiować ani implementować niestandardowe standardowy punkt końcowy oraz jak zdefiniować konkretne właściwości w punkcie końcowym.

## <a name="sample-details"></a>Przykład szczegółów

Punkty końcowe usługi można określić, podając trzy parametry: adres i powiązanie i umowy. Inne parametry, które mogą być dostarczane obejmują konfigurację zachowania, nagłówki, identyfikatora URI nasłuchiwania i tak dalej. W niektórych przypadkach, dowolne lub wszystkie adresy powiązania i kontrakty mają wartości, których nie można zmienić. Z tego powodu jest możliwe użycie standardowych punktów końcowych. Przykłady takich punktów końcowych to punkty końcowe wymiany metadanych i odnajdywania. Standardowe punkty końcowe również zwiększyć użyteczność, umożliwiając konfiguracji punktów końcowych usługi bez konieczności zawierają informacje o charakterze stałej lub utworzyć własne standardowych punktów końcowych, na przykład aby zwiększyć użyteczność, podając uzasadnione zestaw domyślnych wartości i zmniejszając w ten sposób poziom szczegółowości plików konfiguracyjnych.

Ten przykład obejmuje dwa projekty: usługa, która definiuje dwa standardowe punkty końcowe i klienta, który komunikuje się z usługą. Sposób zdefiniowanych standardowych punktów końcowych usługi w pliku konfiguracji jest show w poniższym przykładzie.

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

Pierwszy punkt końcowy zdefiniowany dla usługi jest rodzaju `customEndpoint`, którego definicja będzie widoczne w `<standardEndpoints>` sekcji, w którym właściwość `property` jest podana wartość `true`. Dotyczy to dostosować za pomocą nowej właściwości punktu końcowego. Drugi punkt końcowy odnosi się do punktu końcowego metadanych, w którym są stałe wartości dla adresu, powiązania i umowy.

Aby zdefiniować element standardowy punkt końcowy, klasa, która pochodzi od klasy `StandardEndpointElement` musi zostać utworzona. W przypadku ten przykład `CustomEndpointElement` klasy została zdefiniowana, jak pokazano w poniższym przykładzie.

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

W `CreateServiceEndpoint` funkcji `CustomEndpoint` obiekt zostanie utworzony. W poniższym przykładzie pokazano definicję:

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

 Aby wykonać komunikacji między usługą i klienta, odwołanie do usługi jest tworzony w klienta do usługi. Gdy próbki są kompilowane i wykonywany, usługa była wykonywana, a klient komunikuje się z nim. Należy zauważyć, że odwołanie do usługi mają być aktualizowane za każdym razem, gdy niektóre zmiany w usłudze.

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Za pomocą programu Visual Studio 2012, otwórz plik StandardEndpoints.sln.

2. Włączanie wielu projektów do uruchomienia.

    1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie standardowych punktów końcowych, a następnie wybierz **właściwości**.

    2. W **wspólne właściwości**, wybierz opcję **projekt startowy**, a następnie kliknij przycisk **wiele projektów startowych**.

    3. Przenieś projektu usługi na początku listy, za pomocą **akcji** równa **Start**.

    4. Przejściem projekt klienta po projektu usługi również **akcji** równa **Start**.

         To ustawienie określa, że projekt klienta jest wykonywane po projektu usługi.

3. Aby uruchomić rozwiązanie, naciśnij klawisz F5.

> [!NOTE]
> Jeśli te kroki nie zadziałają, należy sprawdzić, czy środowiska prawidłowo skonfigurowano, wykonując następujące czynności:
>
> 1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).
> 2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](building-the-samples.md).
> 3. Do uruchomienia przykładu w jednej lub wielu konfiguracji komputera, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`
