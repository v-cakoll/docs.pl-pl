---
title: 'Porady: Używanie filtrów'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 2c8c5519d31d1d57c1c568599964b97043f806a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496354"
---
# <a name="how-to-use-filters"></a>Porady: Używanie filtrów
W tym temacie przedstawiono podstawowe czynności wymagane do utworzenia konfiguracji routingu, która używa wielu filtrów. W tym przykładzie wiadomości są kierowane do dwóch implementacji usługi Kalkulator, regularCalc i roundingCalc. Zarówno implementacje obsługują te same operacje; Jednak jedna usługa zaokrągla wszystkich obliczeń do najbliższej liczby całkowitej wartości przed zwróceniem. Aplikacja kliencka musi mieć możliwość wskazuje, czy należy użyć wersji zaokrąglania usługi; Jeśli wyrażono ma preferencji usługi wiadomość jest równoważone między dwie usługi. Operacje udostępnianych przez obie te usługi są:  
  
-   Dodaj  
  
-   Odejmowanie  
  
-   Mnożenia  
  
-   Podziel  
  
 Ponieważ obie te usługi zaimplementować te same operacje, można użyć filtru akcji, ponieważ z akcją określoną w komunikacie nie jest unikatowa. Zamiast tego należy wykonać dodatkowe czynności, aby upewnić się, że komunikaty są kierowane do odpowiednich punktów końcowych.  
  
### <a name="determine-unique-data"></a>Określić unikatowe dane  
  
1.  Ponieważ obu implementacji usługi obsługi tych samych operacji i są zasadniczo identyczne inne niż dane, które zwracają, podstawowe dane zawarte w wiadomości wysyłane przez aplikacje klienckie nie jest unikatowa, co pozwala określić sposób kierowania żądanie. Ale jeśli aplikacja kliencka dodaje wartości nagłówka do wiadomości, następnie można użyć tej wartości można określić, jak powinny być kierowane wiadomości.  
  
     Na przykład jeśli aplikacja kliencka musi komunikat, który ma zostać przetworzone przez zaokrąglania Kalkulator on dodaje niestandardowy nagłówek przy użyciu następującego kodu:  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",   
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     Można teraz filtr XPath umożliwia inspekcję komunikatów dla tego nagłówka i kierowania wiadomości zawierające nagłówka z usługą roundCalc.  
  
2.  Ponadto usługa routingu udostępnia dwa punkty końcowe usług wirtualnych, które mogą być używane z EndpointName, EndpointAddress, lub PrefixEndpointAddress filtrów jednoznacznie kierowania wiadomości przychodzących implementacji określonego Kalkulator oparte na punkt końcowy do którego aplikacja kliencka przesyła żądanie.  
  
### <a name="define-endpoints"></a>Punkty końcowe  
  
1.  Podczas definiowania punktów końcowych używanych przez usługi routingu, należy najpierw określić kształtu kanału używany przez klientów i usług. W tym scenariuszu usług docelowych Użyj wzorca "żądanie-odpowiedź", więc <xref:System.ServiceModel.Routing.IRequestReplyRouter> jest używany. W poniższym przykładzie zdefiniowano punktów końcowych usługi udostępniane przez usługi routingu.  
  
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
  
     W tej konfiguracji usługa routingu udostępnia trzy oddzielne punkty końcowe. W zależności od opcji czasu wykonywania aplikacji klient wysyła komunikaty do jednego z tych adresów. Komunikaty przychodzące w jednym z punktów końcowych usługi "wirtualne" ("zaokrąglania/Kalkulator" lub "regular/Kalkulator") są przekazywane do odpowiedniej implementacji Kalkulator. Jeśli aplikacja kliencka nie wysyłać żądania do danego punktu końcowego, wiadomość jest skierowana do ogólne punktu końcowego. Niezależnie od wybranego punktu końcowego aplikacji klienckiej mogą też dołączyć niestandardowy nagłówek, aby wskazać, że wiadomość jest przekazywany do zaokrąglania implementacji Kalkulator.  
  
2.  W poniższym przykładzie zdefiniowano punktów końcowych klienta (docelowy), które usługa routingu kieruje komunikaty do.  
  
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
  
     Te punkty końcowe są używane w tabeli filtrów wskazująca docelowego punktu końcowego, który komunikat jest wysyłany do, gdy są one zgodne określonego filtru.  
  
### <a name="define-filters"></a>Zdefiniuj filtry  
  
1.  Aby rozesłać komunikaty oparte na niestandardowy nagłówek "RoundingCalculator", który aplikacja kliencka dodaje do wiadomości, zdefiniuj filtr, który używa zapytanie XPath do sprawdzenia obecności tego nagłówka. Ponieważ ten nagłówek jest definiowana za pomocą niestandardowej przestrzeni nazw, należy również dodać wpis przestrzeni nazw, który definiuje prefiksem niestandardowej przestrzeni nazw "custom", który jest używany w zapytaniu XPath. W poniższym przykładzie zdefiniowano niezbędne sekcji routingu, przestrzeni nazw tabeli i filtr XPath.  
  
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
  
     To **MessageFilter** szuka RoundingCalculator nagłówka wiadomości, która zawiera wartość "zaokrąglania". Ten nagłówek jest ustawionego przez klienta, aby wskazać, że komunikat powinny być kierowane do usługi roundingCalc.  
  
    > [!NOTE]
    >  Prefiks przestrzeni nazw s12 jest zdefiniowana w tabeli nazw i reprezentuje przestrzeni nazw "http://www.w3.org/2003/05/soap-envelope".  
  
2.  Należy również zdefiniować filtry mające poszukaj komunikatów odebranych na dwa punkty końcowe wirtualnego. Pierwszy wirtualnego punkt końcowy jest punktem końcowym "regular/kalkulatora". Klient może wysyłać żądania do tego punktu końcowego, aby wskazać, że komunikat powinny być kierowane do usługi regularCalc. Następująca konfiguracja definiuje filtr, który używa <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> ustalenie, czy odebrania wiadomości za pośrednictwem punktu końcowego o podanej nazwie w danych filtru.  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     Jeśli wiadomość zostanie odebrana przez punkt końcowy usługi o nazwie "calculatorEndpoint", filtr daje w wyniku `true`.  
  
3.  Następnie określ filtr, który wygląda komunikaty wysyłane na adres roundingEndpoint. Klient może wysyłać żądania do tego punktu końcowego, aby wskazać, że komunikat powinny być kierowane do usługi roundingCalc. Następująca konfiguracja definiuje filtr, który używa <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> ustalenie, czy wiadomość dotarła do punktu końcowego "zaokrąglania/kalkulatora".  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     Jeśli wiadomość zostanie odebrana na adres, który rozpoczyna się od ciągu "http://localhost/routingservice/router/rounding/" daje w wyniku tego filtru, a następnie **true**. Ponieważ jest adres podstawowy używany przez tę konfigurację "http://localhost/routingservice/router"i jest pełny adres używany do komunikacji z tym punktem końcowym adres podany dla roundingEndpoint jest "zaokrąglania/Kalkulator","http://localhost/routingservice/router/rounding/calculator", który spełni warunki tego filtru.  
  
    > [!NOTE]
    >  Filtr PrefixEndpointAddress nie może oszacować nazwy hosta podczas wykonywania dopasowania, ponieważ w jednym hoście można odwoływać się przy użyciu różnych nazw hostów, które może wszystkie mieć prawidłowe metody odwoływania się do hosta z aplikacji klienta. Na przykład następujące czynności mogą odwoływać się do tego samego hosta:  
    >   
    >  -   localhost  
    > -   127.0.0.1  
    > -   www.contoso.com  
    > -   ContosoWeb01  
  
4.  Ostatni filtr musi obsługiwać routing komunikaty przychodzące w punkcie końcowym w ogólne bez nagłówek niestandardowy. W tym scenariuszu wiadomości powinna alternatywny między usługami regularCalc i roundingCalc. Aby obsługiwać routing "działanie okrężne" tych wiadomości, należy używać niestandardowego filtru umożliwiający jedno wystąpienie filtru do dopasowania dla każdego komunikatu przetworzone.  Poniższy schemat określa dwa wystąpienia RoundRobinMessageFilter, które są zgrupowane aby wskazać, że należy alternatywny między sobą.  
  
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
  
     W czasie wykonywania ten typ filtru przełącza między wszystkich wystąpień zdefiniowany filtr tego typu, które są skonfigurowane jako tej samej grupie w jednej kolekcji. Powoduje to, że komunikaty przetwarzane przez ten niestandardowy filtr, aby przełącza między zwracanie `true` RoundRobinFilter1 i RoundRobinFilter2.  
  
### <a name="define-filter-tables"></a>Zdefiniuj filtr tabel  
  
1.  Aby skojarzyć filtrów z punktami końcowymi określonego klienta, należy umieścić je w tabeli filtrów. Ten przykładowy scenariusz używa również filtru ustawienia priorytetu, która jest ustawienie opcjonalne, które można określić kolejność, w jakiej są przetwarzane filtrów. Jeśli jest określony żaden priorytet filtru, wszystkie filtry, które są oceniane jednocześnie.  
  
    > [!NOTE]
    >  Podczas określania priorytet filtru umożliwia można kontrolować kolejność, w których filtry są przetwarzane go może niekorzystnie wpłynąć na wydajność usługi routingu. Jeśli to możliwe, należy utworzyć filtr logiki tak, aby korzystanie z priorytetów filtru nie jest wymagana.  
  
     Następujące definiuje tabeli filtrów i dodaje "Obiekt XPathFilter" zdefiniowanego wcześniej do tabeli o priorytecie 2. Ten wpis określa, że jeśli obiekt "XPathFilter" pasuje do komunikatu, komunikat będą kierowane do "roundingCalcEndpoint"  
  
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
  
     Podczas określania priorytet filtru, najpierw są oceniane filtry najwyższy priorytet. Jeśli co najmniej jeden filtr na poziomie określonym priorytecie są zgodne, zostanie obliczone żadnych filtrów na niższych poziomach priorytet. W tym scenariuszu 2 jest najwyższy priorytet określone i to tylko wpisu filtru na tym poziomie.  
  
2.  Wpisy filtrów zostały zdefiniowane Aby sprawdzić, czy wiadomość zostanie odebrana w określonym punkcie końcowym, sprawdzając nazwę punktu końcowego lub prefiks adresu. Następujące pozycje Dodaj oba te wpisy filtru do tabeli filtrów i skojarzyć je z punktów końcowych docelowego, które wiadomości będą kierowane do. Te filtry są ustawione na o priorytecie 1, aby wskazać, że ich powinien uruchamiać tylko jeśli poprzedni filtr XPath nie jest zgodny komunikat.  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     Ponieważ te filtry mają priorytet filtru 1, ich tylko ocenia się filtru na poziomie priorytetu 2 jest niezgodna z komunikatu. Ponadto ponieważ oba filtry mają ten sam poziom priorytetu one będą oceniane jednocześnie. Ponieważ obu filtrów wzajemnie się wykluczają, jest możliwe tylko jednego lub drugiego odpowiadające wiadomości.  
  
3.  Jeśli wiadomość nie pasuje do żadnego z poprzednich filtrów, wiadomość została odebrana za pośrednictwem punktu końcowego usługi ogólnej i zawarte żadne informacje nagłówka, która wskazuje, gdzie go rozesłać. Komunikaty te są mają być obsługiwane przez filtr niestandardowy, obciążenia, która równoważy ich między usługami dwóch Kalkulator. W poniższym przykładzie pokazano, jak dodać filtr wpisów do tabeli filtru; Każdy filtr jest skojarzony z jednym z docelowym dwa punkty końcowe.  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     Ponieważ te wpisy Określ priorytet 0, one tylko ocenia się Jeśli żaden filtr o wyższym priorytecie zgodny komunikat. Ponadto ponieważ zarówno z takim samym priorytecie, są one oceniane jednocześnie.  
  
     Jak wspomniano wcześniej, filtr niestandardowy używany przez te definicje filtrów ocenia tylko jedną lub inne, `true` dla każdego komunikatu Odebrano. Ponieważ tylko dwa filtry są zdefiniowane przy użyciu tego filtru, to samo ustawienie określonej grupy, powoduje, że usługa routingu przełącza między wysłaniem regularCalcEndpoint i RoundingCalcEndpoint.  
  
4.  Aby ocenić komunikaty te filtry, tabeli filtrów najpierw musi być skojarzony z punktów końcowych usługi, które będą używane do odbierania wiadomości.  W poniższym przykładzie pokazano, jak skojarzyć tabeli routingu z punktów końcowych usługi przy użyciu routingu zachowanie:  
  
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
 Poniżej znajduje się pełna lista pliku konfiguracji.  
  
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
 [Usługi routingu](../../../../docs/framework/wcf/samples/routing-services.md)
