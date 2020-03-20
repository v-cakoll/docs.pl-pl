---
title: 'Instrukcje: używanie filtrów'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: f99c2af623dacac3ebe46422815a7f42e2a4df2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184816"
---
# <a name="how-to-use-filters"></a>Instrukcje: używanie filtrów
W tym temacie opisano podstawowe kroki wymagane do utworzenia konfiguracji routingu, która używa wielu filtrów. W tym przykładzie wiadomości są kierowane do dwóch implementacji usługi kalkulatora, regularCalc i roundingCalc. Obie implementacje obsługują te same operacje; jednak jedna usługa zaokrągla wszystkie obliczenia do najbliższej wartości całkowitej przed zwróceniem. Aplikacja kliencka musi być w stanie wskazać, czy ma być używana wersja zaokrąglania usługi; jeśli nie preferencje usługi jest wyrażona, a następnie komunikat jest równoważenie obciążenia między dwiema usługami. Operacje udostępniane przez obie usługi są następujące:  
  
- Dodaj  
  
- Odejmowanie  
  
- Mnożenie  
  
- Dzielenie  
  
 Ponieważ obie usługi implementują te same operacje, nie można użyć filtru Akcja, ponieważ akcja określona w komunikacie nie będzie unikatowa. Zamiast tego należy wykonać dodatkową pracę, aby upewnić się, że wiadomości są kierowane do odpowiednich punktów końcowych.  
  
### <a name="determine-unique-data"></a>Określanie unikatowych danych  
  
1. Ponieważ obie implementacje usługi obsługują te same operacje i są zasadniczo identyczne inne niż dane, które zwracają, dane podstawowe zawarte w wiadomościach wysyłanych z aplikacji klienckich nie są wystarczająco unikatowe, aby umożliwić określenie sposobu rozsyłania Żądanie. Ale jeśli aplikacja kliencka dodaje unikatową wartość nagłówka do wiadomości, można użyć tej wartości, aby określić, jak wiadomość powinna być kierowana.  
  
     W tym przykładzie, jeśli aplikacja kliencka wymaga, aby komunikat został przetworzony przez kalkulator zaokrąglania, dodaje niestandardowy nagłówek przy użyciu następującego kodu:  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     Teraz można użyć filtru XPath do sprawdzania wiadomości dla tego nagłówka i wysyłać komunikaty zawierające nagłówek do usługi roundCalc.  
  
2. Ponadto usługa routingu udostępnia dwa wirtualne punkty końcowe usługi, które mogą być używane z filtrami EndpointName, EndpointAddress lub PrefixEndpointAddress, aby jednoznacznie kierować przychodzące wiadomości do określonej implementacji kalkulatora na podstawie punktu końcowego wniosek, do którego wniosek składa wniosek.  
  
### <a name="define-endpoints"></a>Definiowanie punktów końcowych  
  
1. Podczas definiowania punktów końcowych używanych przez usługę routingu, należy najpierw określić kształt kanału używanego przez klientów i usług. W tym scenariuszu usługi docelowe używają wzorca <xref:System.ServiceModel.Routing.IRequestReplyRouter> żądanie odpowiedź, więc jest używany. Poniższy przykład definiuje punkty końcowe usługi udostępniane przez usługę routingu.  
  
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
  
     W tej konfiguracji usługa routingu udostępnia trzy oddzielne punkty końcowe. W zależności od wyborów w czasie wykonywania aplikacja kliencka wysyła komunikaty do jednego z tych adresów. Wiadomości docierające do jednego z "wirtualnych" punktów końcowych usługi ("zaokrąglanie/kalkulator" lub "zwykły/kalkulator") są przekazywane do odpowiedniej implementacji kalkulatora. Jeśli aplikacja kliencka nie wysyła żądania do określonego punktu końcowego, komunikat jest adresowany do ogólnego punktu końcowego. Niezależnie od wybranego punktu końcowego aplikacja kliencka może również dołączyć niestandardowy nagłówek, aby wskazać, że wiadomość powinna być przekazycona do implementacji kalkulatora zaokrąglania.  
  
2. Poniższy przykład definiuje klienta (miejsce docelowe) punkty końcowe, do których usługa routingu kieruje wiadomości do.  
  
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
  
     Te punkty końcowe są używane w tabeli filtrów, aby wskazać docelowy punkt końcowy, do którego jest wysyłana wiadomość, gdy pasuje do określonego filtru.  
  
### <a name="define-filters"></a>Definiowanie filtrów  
  
1. Aby rozsyłać wiadomości na podstawie niestandardowego nagłówka "Zaokrąglanie obliczania", który aplikacja kliencka dodaje do wiadomości, zdefiniuj filtr, który używa kwerendy XPath do sprawdzenia obecności tego nagłówka. Ponieważ ten nagłówek jest zdefiniowany przy użyciu niestandardowego obszaru nazw, należy również dodać wpis obszaru nazw, który definiuje niestandardowy prefiks obszaru nazw "niestandardowy", który jest używany w kwerendzie XPath. Poniższy przykład definiuje niezbędną sekcję routingu, tabelę obszaru nazw i filtr XPath.  
  
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
  
     Ten **messagefilter** szuka zaokrąglaniawejszy nagłówek w wiadomości, która zawiera wartość "zaokrąglania". Ten nagłówek jest ustawiany przez klienta, aby wskazać, że wiadomość powinna być kierowana do usługi zaokrąglaniaCalc.  
  
    > [!NOTE]
    > Prefiks obszaru nazw s12 jest zdefiniowany domyślnie w tabeli obszaru nazw i reprezentuje obszar nazw `http://www.w3.org/2003/05/soap-envelope`.
  
2. Należy również zdefiniować filtry, które szukają wiadomości odebranych w dwóch wirtualnych punktach końcowych. Pierwszym wirtualnym punktem końcowym jest punkt końcowy "zwykły/kalkulator". Klient może wysyłać żądania do tego punktu końcowego, aby wskazać, że wiadomość powinna być kierowana do usługi regularCalc. Poniższa konfiguracja definiuje filtr, <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> który używa do określenia, czy wiadomość dotarła przez punkt końcowy o nazwie określonej w filterData.  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     Jeśli komunikat zostanie odebrany przez punkt końcowy usługi o nazwie "calculatorEndpoint", ten filtr ocenia wartość `true`.  
  
3. Następnie zdefiniuj filtr, który wyszukuje wiadomości wysłane na adres zaokrągleniaEndpoint. Klient może wysyłać żądania do tego punktu końcowego, aby wskazać, że wiadomość powinna być kierowana do usługi zaokrąglaniaCalc. Poniższa konfiguracja definiuje filtr, <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> który używa do określenia, czy wiadomość dotarła do punktu końcowego "zaokrąglania/kalkulatora".  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     Jeśli wiadomość zostanie odebrana pod `http://localhost/routingservice/router/rounding/` adresem, który zaczyna się od tego, filtr ten jest oceniany jako **true**. Ponieważ adres podstawowy używany przez `http://localhost/routingservice/router` tę konfigurację jest i adres określony dla zaokrągleniaEndpoint jest "zaokrąglanie/kalkulator", pełny adres używany do komunikowania się z tym punktem końcowym jest `http://localhost/routingservice/router/rounding/calculator`, który pasuje do tego filtru.  
  
    > [!NOTE]
    > Filtr PrefixEndpointAddress nie ocenia nazwy hosta podczas wykonywania dopasowania, ponieważ można odwoływać się do pojedynczego hosta przy użyciu różnych nazw hostów, które mogą być prawidłowymi sposobami odwoływania się do hosta z aplikacji klienckiej. Na przykład wszystkie następujące mogą odwoływać się do tego samego hosta:  
    >
    > - localhost  
    > - 127.0.0.1  
    > - `www.contoso.com`  
    > - Sieć ContosoWeb01  
  
4. Filtr końcowy musi obsługiwać routingu wiadomości, które docierają do ogólnego punktu końcowego bez nagłówka niestandardowego. W tym scenariuszu komunikaty powinny naprzemiennie między regularCalc i roundingSedy. Aby obsługiwać routing "okrężny" tych wiadomości, użyj filtru niestandardowego, który umożliwia dopasowywanie jednego wystąpienia filtru dla każdej przetworzonej wiadomości.  Poniżej definiuje dwa wystąpienia RoundRobinMessageFilter, które są zgrupowane razem, aby wskazać, że powinny one naprzemiennie między sobą.  
  
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
  
     W czasie wykonywania ten typ filtru przełącza się między wszystkimi zdefiniowanymi wystąpieniami filtru tego typu, które są skonfigurowane jako ta sama grupa w jedną kolekcję. Powoduje to, że wiadomości przetwarzane przez ten `true` `RoundRobinFilter1` filtr `RoundRobinFilter2`niestandardowy zmieniają się między zwracaniem dla i .  
  
### <a name="define-filter-tables"></a>Definiowanie tabel filtrów  
  
1. Aby skojarzyć filtry z określonymi punktami końcowymi klienta, należy umieścić je w tabeli filtrów. W tym przykładzie scenariusza użyto również ustawień priorytetu filtru, które jest ustawieniem opcjonalnym, które umożliwia wskazanie kolejności przetwarzania filtrów. Jeśli nie określono priorytetu filtru, wszystkie filtry są oceniane jednocześnie.  
  
    > [!NOTE]
    > Podczas określania priorytetu filtru pozwala kontrolować kolejność, w jakiej filtry są przetwarzane, może to niekorzystnie wpłynąć na wydajność usługi routingu. Jeśli to możliwe, skonstruuj logikę filtru, aby użycie priorytetów filtru nie było wymagane.  
  
     Poniżej definiuje tabelę filtrów i dodaje "XPathFilter" zdefiniowane wcześniej do tabeli o priorytecie 2. Ten wpis określa również, `XPathFilter` że jeśli wiadomość jest zgodna z `roundingCalcEndpoint`komunikatem, zostanie przekierowana do pliku .  
  
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
  
     Podczas określania priorytetu filtru filtry o najwyższym priorytecie są oceniane jako pierwsze. Jeśli jeden lub więcej filtrów na określonym poziomie priorytetu pasuje, nie filtry na niższych poziomach priorytetu będą oceniane. W tym scenariuszu 2 jest najwyższy priorytet określony i jest to tylko wpis filtru na tym poziomie.  
  
2. Wpisy filtru zostały zdefiniowane, aby sprawdzić, czy wiadomość jest odbierana w określonym punkcie końcowym, sprawdzając nazwę punktu końcowego lub prefiks adresu. Następujące wpisy dodać oba te wpisy filtru do tabeli filtru i skojarzyć je z docelowymi punktami końcowymi, do których zostanie skierowana wiadomość. Filtry te są ustawione na priorytet 1, aby wskazać, że powinny działać tylko wtedy, gdy poprzedni filtr XPath nie pasuje do wiadomości.  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     Ponieważ te filtry mają priorytet filtru 1, będą one oceniane tylko wtedy, gdy filtr na poziomie priorytetu 2 nie pasuje do wiadomości. Ponadto, ponieważ oba filtry mają ten sam poziom priorytetu będą oceniane jednocześnie. Ponieważ oba filtry wzajemnie się wykluczają, jest możliwe tylko jeden lub drugi, aby dopasować wiadomość.  
  
3. Jeśli wiadomość nie pasuje do żadnego z poprzednich filtrów, wiadomość została odebrana za pośrednictwem punktu końcowego usługi ogólnej i nie zawierała żadnych informacji nagłówka wskazujących, gdzie ją rozsyłać. Te komunikaty mają być obsługiwane przez filtr niestandardowy, który równoważy je między dwiema usługami kalkulatora. W poniższym przykładzie pokazano, jak dodać wpisy filtru do tabeli filtrów; każdy filtr jest skojarzony z jednym z dwóch docelowych punktów końcowych.  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     Ponieważ te wpisy określają priorytet 0, będą one oceniane tylko wtedy, gdy żaden filtr o wyższym priorytecie nie pasuje do wiadomości. Ponadto, ponieważ oba są tego samego priorytetu, są one oceniane jednocześnie.  
  
     Jak wspomniano wcześniej, filtr niestandardowy używany przez te definicje filtrów `true` ocenia tylko jeden lub drugi, jak dla każdej odebranej wiadomości. Ponieważ tylko dwa filtry są zdefiniowane przy użyciu tego filtru, z tym samym ustawieniem określonej grupy, efekt jest, że usługa routingu przełącza się między wysyłaniem do regularCalcEndpoint i RoundingCalcEndpoint.  
  
4. Aby ocenić komunikaty względem filtrów, tabela filtrów musi być najpierw skojarzona z punktami końcowymi usługi, które będą używane do odbierania wiadomości.  W poniższym przykładzie pokazano, jak skojarzyć tabelę routingu z punktami końcowymi usługi przy użyciu zachowania routingu:  
  
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
 Poniżej znajduje się pełna lista pliku konfiguracyjnego.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Usługi routingu](../../../../docs/framework/wcf/samples/routing-services.md)
