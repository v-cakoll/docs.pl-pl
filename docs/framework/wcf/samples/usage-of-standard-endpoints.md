---
title: "Użycie standardowych punktów końcowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 85dda1619fe3a77c4716806de2467cb96287b2f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="usage-of-standard-endpoints"></a>Użycie standardowych punktów końcowych
W tym przykładzie przedstawiono sposób użycia standardowych punktów końcowych w plikach konfiguracji usługi. Standardowy punkt końcowy umożliwia użytkownikowi uprościć definicje punktu końcowego za pomocą jednej właściwości do opisywania address, binding i contract kombinacji z dodatkowe właściwości skojarzone z nim. W tym przykładzie przedstawiono sposób definiowania i implementować niestandardowe standardowy punkt końcowy oraz do definiowania właściwości specyficzne dla punktu końcowego.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Punkty końcowe usługi można określić podając trzy parametry: adres i powiązanie i kontraktu. Inne parametry, które mogą być dostarczane obejmują konfigurację zachowania, nagłówki, identyfikatora URI nasłuchiwania i tak dalej. W niektórych przypadkach, dowolne lub wszystkie adresy powiązania i kontrakty mają wartości, których nie można zmienić. Z tego powodu jest możliwe użycie standardowych punktów końcowych. Niektóre z tych punktów końcowych przykładami punkty końcowe wymiany metadanych i odnajdywania. Standardowe punkty końcowe także zwiększają jego użyteczność, zezwalając konfiguracji punktów końcowych usługi bez konieczności zawierają informacje o charakterze stałym lub utworzyć własne standardowych punktów końcowych, na przykład aby poprawić użyteczność, podając uzasadnione zestaw domyślnych wartości i w związku z tym zmniejszenie szczegółowości plików konfiguracji.  
  
 Ten przykład zawiera dwa projekty: usługi, który definiuje dwa standardowe punkty końcowe i klienta, który komunikuje się z usługą. Sposób standardowych punktów końcowych zdefiniowanych w pliku konfiguracji usługi jest Pokaż w poniższym przykładzie.  
  
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
  
 Pierwszy punkt końcowy zdefiniowany dla usługi jest rodzaju `customEndpoint`, którego definicja będzie widoczne w `<standardEndpoints>` sekcji, w którym właściwość `property` znajduje się wartość `true`. Jest to punkt końcowy dostosować za pomocą nowej właściwości. Odpowiada drugiego punktu końcowego na punkt końcowy metadanych, w którym są ustalone wartości address, binding i contract.  
  
 Aby zdefiniować element standardowego punktu końcowego, klasy, która jest pochodną `StandardEndpointElement` musi zostać utworzony. W przypadku tej próbki `CustomEndpointElement` zdefiniowano klasy, jak pokazano w poniższym przykładzie.  
  
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
  
 W `CreateServiceEndpoint` funkcji `CustomEndpoint` tworzony jest obiekt. W poniższym przykładzie przedstawiono definicję.  
  
```  
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
  
 Aby wykonać komunikacji między usługą i klienta, odwołania do usługi jest tworzony w klienta do usługi. Gdy próbki jest wbudowana i wykonywane, wykonuje usługa i klient komunikuje się z nim. Należy pamiętać, że odwołania do usługi powinien być aktualizowane za każdym razem, gdy niektóre zmiany w usłudze.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik StandardEndpoints.sln.  
  
2.  Włącz wiele projektów mogła się uruchomić.  
  
    1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie standardowych punktów końcowych, a następnie wybierz **właściwości**.  
  
    2.  W **wspólne właściwości**, wybierz pozycję **projekt startowy**, a następnie kliknij przycisk **wiele projektów startowych**.  
  
    3.  Projekt usługi na początku listy, są przenoszone wraz z **akcji** ustawioną **Start**.  
  
    4.  Przenieś projektu klienta po projektu usługi również z **akcji** ustawioną **Start**.  
  
         To ustawienie określa, że projekt klienta jest wykonywane po projektu usługi.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisz F5.  
  
> [!NOTE]
>  Jeśli te kroki nie działają, następnie upewnij się, że środowiska nie został prawidłowo skonfigurowany, wykonując następujące kroki.  
>   
>  1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
> 2.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
> 3.  Aby uruchomić przykład w jednym lub wielu konfiguracji komputera, postępuj zgodnie z instrukcjami [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`  
  
## <a name="see-also"></a>Zobacz też
