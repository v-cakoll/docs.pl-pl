---
title: 'Instrukcje: Używanie filtrów'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 6c357f2f410362d56fc931529a9fe731df0a477e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968767"
---
# <a name="how-to-use-filters"></a>Instrukcje: Używanie filtrów
W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia konfiguracji routingu korzystającej z wielu filtrów. W tym przykładzie komunikaty są kierowane do dwóch implementacji usługi kalkulatora, regularCalc i roundingCalc. Obie implementacje obsługują te same operacje; Jednak jedna usługa zaokrągla wszystkie obliczenia do najbliższej wartości całkowitej przed zwróceniem. Aplikacja kliencka musi być w stanie wskazać, czy ma być używana zaokrąglana wersja usługi. Jeśli preferencja usługi nie jest określona, komunikat jest równoważony między obiema usługami. Operacje udostępniane przez obie usługi są następujące:  
  
- Dodaj  
  
- Odjęt  
  
- Mnożenia  
  
- Mieszczon  
  
 Ponieważ obie usługi implementują te same operacje, nie można użyć filtru akcji, ponieważ akcja określona w komunikacie nie będzie unikatowa. Zamiast tego należy wykonać dodatkowe czynności, aby upewnić się, że komunikaty są kierowane do odpowiednich punktów końcowych.  
  
### <a name="determine-unique-data"></a>Określanie unikatowych danych  
  
1. Ponieważ oba implementacje usług obsługują te same operacje i są zasadniczo identyczne jak dane, które zwracają, dane podstawowe zawarte w komunikatach wysyłanych z aplikacji klienckich nie są wystarczająco unikatowe, aby umożliwić określenie sposobu kierowania żądając. Jeśli jednak aplikacja kliencka dodaje do wiadomości unikatową wartość nagłówka, można użyć tej wartości, aby określić sposób, w jaki komunikat powinien być kierowany.  
  
     W tym przykładzie, jeśli aplikacja kliencka wymaga przetworzenia komunikatu przez kalkulator zaokrąglenia, dodaje niestandardowy nagłówek przy użyciu następującego kodu:  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",   
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     Można teraz użyć filtru XPath do sprawdzenia komunikatów dla tego nagłówka i trasy komunikatów zawierających nagłówek do usługi roundCalc.  
  
2. Dodatkowo usługa routingu udostępnia dwa punkty końcowe usługi wirtualnej, które mogą być używane z filtrami EndpointName, EndpointAddress lub PrefixEndpointAddress w celu jednoznacznej trasy komunikatów przychodzących do określonej implementacji kalkulatora na podstawie punktu końcowego , do którego aplikacja kliencka przesyła żądanie.  
  
### <a name="define-endpoints"></a>Definiuj punkty końcowe  
  
1. Podczas definiowania punktów końcowych używanych przez usługę routingu należy najpierw określić kształt kanału używanego przez klientów i usługi. W tym scenariuszu zarówno usługi docelowe używają wzorca żądania-odpowiedzi, więc <xref:System.ServiceModel.Routing.IRequestReplyRouter> jest używany. W poniższym przykładzie zdefiniowano punkty końcowe usługi udostępniane przez usługę routingu.  
  
    ```xml  
    <services>  
          <service behaviorConfiguration="routingConfiguration"  
                   name="System.ServiceModel.Routing.RoutingService">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost/routingservice/router" />  
              </baseAddresses>  
            </host>  
            <!--Set up the inbound endpoints for the Routing Service-->  
            <!--first create the general router endpoint-->  
            <endpoint address="general"  
                      binding="wsHttpBinding"  
                      name="routerEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--create a virtual endpoint for the regular calculator service-->  
            <endpoint address="regular/calculator"  
                      binding="wsHttpBinding"  
                      name="calculatorEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--now create a virtual endpoint for the rounding calculator-->  
            <endpoint address="rounding/calculator"  
                      binding="wsHttpBinding"  
                      name="roundingEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
          </service>  
    </services>  
    ```  
  
     W przypadku tej konfiguracji usługa routingu ujawnia trzy oddzielne punkty końcowe. W zależności od opcji w czasie wykonywania aplikacja kliencka wysyła komunikaty do jednego z tych adresów. Komunikaty docierające do jednego z "wirtualnych" punktów końcowych usługi ("zaokrąglenie/Kalkulator" lub "regularne/Kalkulator") są przekazywane do odpowiedniej implementacji kalkulatora. Jeśli aplikacja kliencka nie wyśle żądania do określonego punktu końcowego, komunikat zostanie rozkierowany do ogólnego punktu końcowego. Niezależnie od wybranego punktu końcowego aplikacja kliencka może również dołączyć nagłówek niestandardowy, aby wskazać, że wiadomość powinna być przekazywana do implementacji kalkulatora zaokrąglenia.  
  
2. W poniższym przykładzie zdefiniowano punkty końcowe klienta (miejsce docelowe), do których usługa routingu kieruje komunikaty.  
  
    ```xml  
    <client>  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
    </client>  
    ```  
  
     Te punkty końcowe są używane w tabeli filtrów, aby wskazać docelowy punkt końcowy, do którego komunikat jest wysyłany, gdy jest zgodny z określonym filtrem.  
  
### <a name="define-filters"></a>Definiuj filtry  
  
1. Aby przesłać komunikaty na podstawie niestandardowego nagłówka "RoundingCalculator", który aplikacja kliencka dodaje do wiadomości, zdefiniuj filtr, który używa zapytania XPath do sprawdzenia obecności tego nagłówka. Ponieważ ten nagłówek jest definiowany przy użyciu niestandardowej przestrzeni nazw, należy również dodać wpis przestrzeni nazw, który definiuje niestandardowy prefiks przestrzeni nazw "Custom", który jest używany w zapytaniu XPath. W poniższym przykładzie zdefiniowano niezbędną sekcję routingu, tabelę przestrzeni nazw oraz filtr XPath.  
  
    ```xml  
    <routing>  
          <!-- use the namespace table element to define a prefix for our custom namespace-->  
          <namespaceTable>  
            <add prefix="custom" namespace="http://my.custom.namespace/"/>  
          </namespaceTable>  
          <filters>  
            <!--define the different message filters-->  
            <!--define an xpath message filter to look for the custom header coming from the client-->  
            <filter name="XPathFilter" filterType="XPath"   
                    filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
          </filters>  
    </routing>  
    ```  
  
     Ta **MessageFilter** szuka nagłówka RoundingCalculator w komunikacie zawierającym wartość "rounding". Ten nagłówek jest ustawiany przez klienta w celu wskazania, że komunikat powinien być kierowany do usługi roundingCalc.  
  
    > [!NOTE]
    > Prefiks przestrzeni nazw S12 jest definiowany domyślnie w tabeli przestrzeni nazw i reprezentuje przestrzeń nazw `http://www.w3.org/2003/05/soap-envelope`.
  
2. Należy również zdefiniować filtry, które szukają komunikatów odebranych w dwóch wirtualnych punktach końcowych. Pierwszy wirtualny punkt końcowy to punkt końcowy "Regular/Kalkulator". Klient może wysyłać żądania do tego punktu końcowego, aby wskazać, że komunikat powinien być kierowany do usługi regularCalc. Poniższa konfiguracja definiuje filtr, który używa <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> do określenia, czy komunikat dotarł do punktu końcowego o nazwie określonej w danych filtru.  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     Jeśli komunikat jest odbierany przez punkt końcowy usługi o nazwie "calculatorEndpoint", ten filtr szacuje `true`wartość.  
  
3. Następnie zdefiniuj filtr, który szuka komunikatów wysyłanych na adres roundingEndpoint. Klient może wysyłać żądania do tego punktu końcowego, aby wskazać, że komunikat powinien być kierowany do usługi roundingCalc. Poniższa konfiguracja definiuje filtr, który używa w <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> celu ustalenia, czy wiadomość dotarła do punktu końcowego "zaokrąglenie/kalkulatora".  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     Jeśli otrzymasz komunikat o adresie zaczynającym `http://localhost/routingservice/router/rounding/` się od, ten filtr zwróci **wartość true**. Ponieważ adres podstawowy używany przez tę konfigurację jest `http://localhost/routingservice/router` i adresem określonym dla roundingEndpoint jest "zaokrąglenie/Kalkulator", pełny adres używany do komunikacji z tym punktem końcowym jest `http://localhost/routingservice/router/rounding/calculator`zgodny z tym filtrem.  
  
    > [!NOTE]
    > Filtr PrefixEndpointAddress nie oblicza nazwy hosta podczas dopasowywania, ponieważ pojedynczy host może być określony przy użyciu różnych nazw hostów, które mogą być prawidłowymi sposobami odwoływania się do hosta z aplikacji klienckiej. Na przykład wszystkie następujące elementy mogą odnosić się do tego samego hosta:  
    >   
    > - localhost  
    > - 127.0.0.1  
    > - `www.contoso.com`  
    > - ContosoWeb01  
  
4. Filtr końcowy musi obsługiwać Routing komunikatów, które docierają do ogólnego punktu końcowego bez niestandardowego nagłówka. W tym scenariuszu komunikaty powinny być zastępowane przez usługi regularCalc i roundingCalc. Aby zapewnić obsługę routingu "Round Robin" tych komunikatów, należy użyć filtru niestandardowego, który umożliwia dopasowanie jednego wystąpienia filtru dla każdego przetworzonego komunikatu.  Poniżej zdefiniowano dwa wystąpienia RoundRobinMessageFilter, które są pogrupowane w celu wskazania, że powinny one być różne od siebie.  
  
    ```xml  
    <!-- Set up the custom message filters.  In this example,   
         we'll use the example round robin message filter,   
         which alternates between the references-->  
    <filter name="RoundRobinFilter1" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    <filter name="RoundRobinFilter2" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    ```  
  
     W czasie wykonywania ten filtr typu alternatywy między wszystkimi zdefiniowanymi wystąpieniami filtru tego typu, które są skonfigurowane jako ta sama Grupa w jednej kolekcji. Powoduje to `true` `RoundRobinFilter1` , że komunikaty przetwarzane przez ten filtr niestandardowy do alternatywy między `RoundRobinFilter2`zwracanymi a i.  
  
### <a name="define-filter-tables"></a>Definiowanie tabel filtrów  
  
1. Aby skojarzyć filtry z określonymi punktami końcowymi klienta, należy umieścić je w tabeli filtrów. W tym przykładowym scenariuszu są używane również ustawienia priorytetu filtru, które jest ustawieniem opcjonalnym umożliwiającym wskazanie kolejności przetwarzania filtrów. Jeśli nie określono priorytetu filtru, wszystkie filtry są oceniane jednocześnie.  
  
    > [!NOTE]
    > Chociaż określenie priorytetu filtru pozwala kontrolować kolejność przetwarzania filtrów, może niekorzystnie wpłynąć na wydajność usługi routingu. Jeśli to możliwe, Utwórz logikę filtru, aby użycie priorytetów filtru nie jest wymagane.  
  
     Poniższy schemat definiuje tabelę filtrów i dodaje element "obiekt XPathFilter" zdefiniowany wcześniej do tabeli o priorytecie 2. Ten wpis określa również, że jeśli `XPathFilter` dopasowuje komunikat, komunikat zostanie rozesłany `roundingCalcEndpoint`do.  
  
    ```xml  
    <routing>  
    ...      <filters>  
    ...      </filters>  
          <filterTables>  
            <table name="filterTable1">  
              <entries>  
                <!--add the filters to the message filter table-->  
                <!--first look for the custom header, and if we find it,  
                    send the message to the rounding calc endpoint-->  
                <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
              </entries>  
            </table>  
          <filterTables>  
    </routing>  
    ```  
  
     Podczas określania priorytetu filtru najpierw są oceniane filtry o najwyższym priorytecie. Jeśli co najmniej jeden filtr o określonym poziomie priorytetu jest zgodny, nie będą oceniane żadne filtry o niższych poziomach. W tym scenariuszu wartość 2 to najwyższy określony priorytet i jest to jedyna pozycja filtru na tym poziomie.  
  
2. Zdefiniowano wpisy filtru, aby sprawdzić, czy wiadomość została odebrana w określonym punkcie końcowym przez sprawdzenie nazwy punktu końcowego lub prefiksu adresu. Poniższe wpisy umożliwiają dodanie obu tych wpisów filtru do tabeli filtrów i skojarzenie ich z docelowym miejscem końcowym, do którego zostanie rozesłany komunikat. Te filtry mają ustawiony priorytet 1, aby wskazać, że powinny być uruchamiane tylko wtedy, gdy poprzedni filtr XPath nie jest zgodny z komunikatem.  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     Ponieważ te filtry mają priorytet filtru 1, będą oceniane tylko wtedy, gdy filtr na poziomie priorytetu 2 nie jest zgodny z komunikatem. Ponadto, ponieważ oba filtry mają taki sam poziom priorytetu, będą oceniane jednocześnie. Ponieważ oba filtry wykluczają się wzajemnie, możliwe jest tylko jedno lub drugie, aby dopasować komunikat.  
  
3. Jeśli komunikat nie jest zgodny z żadnym z poprzednich filtrów, komunikat został odebrany za pomocą punktu końcowego usługi ogólnej i nie zawierał informacji nagłówka wskazujących, gdzie należy je przekierować. Te komunikaty mają być obsługiwane przez filtr niestandardowy, który równoważy obciążenie między obiema usługami kalkulatora. Poniższy przykład ilustruje sposób dodawania wpisów filtru do tabeli filtrów; Każdy filtr jest skojarzony z jednym z dwóch docelowych punktów końcowych.  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     Ponieważ te wpisy określają priorytet 0, będą oceniane tylko wtedy, gdy żaden filtr o wyższym priorytecie nie jest zgodny z komunikatem. Ponadto, ponieważ oba mają ten sam priorytet, są one oceniane jednocześnie.  
  
     Jak wspomniano wcześniej, filtr niestandardowy używany przez te definicje filtru oblicza tylko jedną lub drugą `true` wartość dla każdego odebranego komunikatu. Ponieważ tylko dwa filtry są zdefiniowane przy użyciu tego filtru, z tym samym ustawieniem określonej grupy, efektem jest to, że usługa routingu jest alternatywna dla wysyłania do regularCalcEndpoint i RoundingCalcEndpoint.  
  
4. Aby można było oszacować komunikaty względem filtrów, tabela filtrów musi być najpierw skojarzona z punktami końcowymi usługi, które będą używane do odbierania komunikatów.  W poniższym przykładzie pokazano, jak skojarzyć tabelę routingu z punktami końcowymi usługi przy użyciu zachowania routingu:  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się kompletna lista plików konfiguracyjnych.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--first create the general router endpoint-->  
        <endpoint address="general"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--create a virtual endpoint for the regular calculator service-->  
        <endpoint address="regular/calculator"  
                  binding="wsHttpBinding"  
                  name="calculatorEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--now create a virtual endpoint for the rounding calculator-->  
        <endpoint address="rounding/calculator"  
                  binding="wsHttpBinding"  
                  name="roundingEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoints-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the custom header coming from the client-->  
        <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
  
        <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
        <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
  
        <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
        <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress" filterData="http://localhost/routingservice/router/rounding/"/>  
  
        <!--Set up the custom message filters.  In this example, we'll use the example round robin message filter, which alternates between the references-->  
        <filter name="RoundRobinFilter1" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
        <filter name="RoundRobinFilter2" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
      </filters>  
      <filterTables>  
        <table name="filterTable1">  
          <entries>  
            <!--add the filters to the message filter table-->  
            <!--first look for the custom header, and if we find it, send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
  
            <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
            <!--we determine this through the endpoint name, or through the address prefix-->  
            <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
            <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
  
            <!--if none of the other filters have matched, this message showed up on the default router endpoint, with no custom header-->  
            <!--round robin these requests between the two services-->  
            <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
            <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
          </entries>  
        </table>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Usługi routingu](../../../../docs/framework/wcf/samples/routing-services.md)
