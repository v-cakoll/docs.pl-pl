---
title: 'Instrukcje: Używanie filtrów'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 6b1e02563fcc32a0095e2bdb5e25d0853fc05e84
ms.sourcegitcommit: c66ba2df2d2ecfb214f85ee0687d298e4941c1a8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2018
ms.locfileid: "42752350"
---
# <a name="how-to-use-filters"></a>Instrukcje: Używanie filtrów
W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia konfiguracji routingu, który używa wielu filtrów. W tym przykładzie komunikaty są kierowane do dwie implementacje usługi Kalkulator, regularCalc i roundingCalc. Zarówno implementacje obsługują te same operacje; Jednak w jednej usłudze zaokrągla wszystkie obliczenia do najbliższej wartości całkowitej przed zwróceniem. Aplikacja kliencka musi być w stanie wskazać, czy ma być używany zaokrąglania wersję usługi; Jeśli brak preferencji Usługa bazy danych jest wyrażona wiadomość jest równoważone między obiema usługami. Operacje udostępniane przez obie te usługi są:  
  
-   Dodaj  
  
-   Odejmowanie  
  
-   Mnożenie  
  
-   Dzielenie  
  
 Ponieważ obie te usługi implementuje te same operacje, nie można użyć filtru akcji, ponieważ z akcją określoną w komunikacie nie jest unikatowa. Zamiast tego należy wykonać dodatkową pracę, aby upewnić się, że komunikaty są kierowane do odpowiednich punktów końcowych.  
  
### <a name="determine-unique-data"></a>Określić unikatowe dane  
  
1.  Ponieważ zarówno implementacji usługi obsługi tych samych operacji i są zasadniczo identyczne inne niż dane, które zwracają, podstawowy dane zawarte w wiadomości wysyłanych z aplikacji klienckich nie jest unikatowy, aby możliwe było określić, jak kierować żądanie. Ale jeśli aplikacja kliencka dodaje wartości nagłówka do wiadomości, następnie można użyć tej wartości można określić, jak powinny być kierowane wiadomości.  
  
     Na przykład jeśli aplikacja kliencka potrzebuje komunikat, który ma zostać przetworzony przez zaokrąglania Kalkulator, dodaje niestandardowego nagłówka przy użyciu następującego kodu:  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",   
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     Można teraz umożliwia sprawdzanie komunikatów dla tego pliku nagłówkowego filtr XPath i kierowanie komunikatów w postaci zawierający nagłówek usługą roundCalc.  
  
2.  Ponadto usługa routingu udostępnia dwa punkty końcowe usług wirtualnych, które mogą być używane z Nazwapunktukoncowego, EndpointAddress, lub PrefixEndpointAddress filtrów jednoznacznie kierowanie komunikatów przychodzących do implementacji określonego Kalkulator, oparta na punkcie końcowym do której aplikacja kliencka wysyła żądanie.  
  
### <a name="define-endpoints"></a>Punkty końcowe  
  
1.  Podczas definiowania punktów końcowych używanych przez usługę routingu, najpierw należy określić kształt kanał używany przez klientów i usług. W tym scenariuszu usług docelowych użyć wzorca "żądanie-odpowiedź", więc <xref:System.ServiceModel.Routing.IRequestReplyRouter> jest używany. W poniższym przykładzie zdefiniowano punktów końcowych usługi udostępniane przez usługę routingu.  
  
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
  
     W przypadku tej konfiguracji usługa routingu udostępnia trzy oddzielne punkty końcowe. W zależności od opcji środowiska wykonawczego aplikacja kliencka wysyła komunikaty do jednego z tych adresów. Komunikaty przychodzące w jednym z punktów końcowych usługi "wirtualne" ("zaokrąglania/Kalkulator" lub "zwykłych/Kalkulator") są przekazywane do odpowiedniej implementacji kalkulatora. Jeśli aplikacja kliencka nie wysyła żądanie do określonego punktu końcowego, komunikat jest skierowana do endpoint ogólne. Niezależnie od tego punktu końcowego wybrana aplikacja kliencka może też dołączyć niestandardowy nagłówek, aby wskazać, że komunikat powinien być przekazywany do zaokrąglenia implementacji kalkulatora.  
  
2.  W poniższym przykładzie zdefiniowano punktów końcowych klienta (docelowy), które usługa routingu kieruje komunikaty.  
  
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
  
     Te punkty końcowe są używane w tabeli filtru do wskazania docelowy punkt końcowy, który jest wysyłany komunikat w przypadku, gdy pasuje do określonego filtru.  
  
### <a name="define-filters"></a>Zdefiniuj filtry  
  
1.  Aby rozesłać komunikaty oparte na niestandardowy nagłówek "RoundingCalculator", który aplikacja kliencka dodaje do komunikatu, należy zdefiniować filtr, który używa kwerendy XPath Aby sprawdzić obecność tego pliku nagłówkowego. Ponieważ tego pliku nagłówkowego jest definiowana za pomocą niestandardowej przestrzeni nazw, należy również dodać wpis przestrzeni nazw, który definiuje prefiksem niestandardowej przestrzeni nazw "niestandardowy", który jest używany w zapytaniu XPath. W poniższym przykładzie zdefiniowano niezbędne sekcji routingu, przestrzeń nazw tabeli i filtr XPath.  
  
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
  
     To **MessageFilter** szuka RoundingCalculator nagłówka wiadomości, która zawiera wartość "zaokrąglania". Tego pliku nagłówkowego jest ustawionego przez klienta, aby wskazać, czy komunikat powinien być kierowane do usługi roundingCalc.  
  
    > [!NOTE]
    >  Prefiks przestrzeni nazw s12 jest zdefiniowana w przestrzeni nazw tabeli i reprezentuje obszar nazw "http://www.w3.org/2003/05/soap-envelope".  
  
2.  Należy także zdefiniować filtry, które poszukują komunikatów odebranych w dwóch punktach końcowych wirtualnej. Pierwszy wirtualnego punkt końcowy jest punktem końcowym "zwykłych/Kalkulator". Klient może wysyłać żądania do tego punktu końcowego, aby wskazać, czy komunikat powinien być kierowane do usługi regularCalc. Następująca konfiguracja definiuje filtr, który używa <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> ustalenie, jeśli wiadomość dotarła za pośrednictwem punktu końcowego o nazwie określonej w danych filtru.  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     Jeśli komunikat jest odbierany przez punkt końcowy usługi o nazwie "calculatorEndpoint", ten filtr daje w wyniku `true`.  
  
3.  Następnie zdefiniuj filtr, który wygląda dla wiadomości wysyłanych na adres roundingEndpoint. Klient może wysyłać żądania do tego punktu końcowego, aby wskazać, czy komunikat powinien być kierowane do usługi roundingCalc. Następująca konfiguracja definiuje filtr, który używa <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> ustalenie, jeśli wiadomość dotarła do endpoint "zaokrąglania/Kalkulator".  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     Gdy wiadomość zostaje odebrana w adres który rozpoczyna się od "http://localhost/routingservice/router/rounding/", a następnie daje w wyniku tego filtru **true**. Ponieważ adres bazowy używany przez tę konfigurację "http://localhost/routingservice/router"i jest pełny adres używany do komunikowania się z tym punktem końcowym adres określony dla roundingEndpoint jest "zaokrąglania/Kalkulator","http://localhost/routingservice/router/rounding/calculator", który pasuje do tego filtru.  
  
    > [!NOTE]
    >  Filtr PrefixEndpointAddress nie może oszacować nazwy hosta podczas wykonywania dopasowanie, ponieważ w jednym hoście mogą się odwoływać przy użyciu różnych nazw hostów, które mogą wszystkie prawidłowe metody odwoływania się do hosta z aplikacji klienckiej. Na przykład wszystkie poniższe może odnosić się do tego samego hosta:  
    >   
    > -   localhost  
    > -   127.0.0.1  
    > -   `www.contoso.com`  
    > -   ContosoWeb01  
  
4.  Ostatni filtr musi obsługiwać routing komunikaty przychodzące w punkcie końcowym ogólnego bez niestandardowego nagłówka. W tym scenariuszu komunikaty powinny alternatywne między usługami regularCalc i roundingCalc. Aby obsługiwać routing "działanie okrężne" tych wiadomości, użyj niestandardowy filtr, który umożliwia jedno wystąpienie filtru do dopasowania dla każdego komunikatu przetworzone.  Poniżej definiuje dwa wystąpienia RoundRobinMessageFilter, które są zgrupowane razem do wskazania, że powinien alternatywny między sobą.  
  
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
  
     W czasie wykonywania filtru tego typu przełącza między wszystkie wystąpienia zdefiniowany filtr tego typu, które są skonfigurowane jako tej samej grupie w jednej kolekcji. Powoduje to, że komunikaty przetwarzane przez ten filtr niestandardowy do alternatywnego między zwracanie `true` RoundRobinFilter1 i RoundRobinFilter2.  
  
### <a name="define-filter-tables"></a>Definiowanie tabel filtru  
  
1.  Aby skojarzyć z filtrami z punktów końcowych klienta właściwy, trzeba je umieścić w tabeli filtru. Ten przykładowy scenariusz używa także ustawienia priorytetu filtr, który jest ustawienie opcjonalne, które można określić kolejność, w jakiej są przetwarzane filtrów. Jeśli żaden priorytet filtru zostanie określony, wszystkie filtry są obliczane jednocześnie.  
  
    > [!NOTE]
    >  Podczas określania priorytetu filtr umożliwia pozwala kontrolować kolejność, w której filtry są przetwarzane, jego może niekorzystnie wpłynąć na wydajność usługi routingu. Jeśli to możliwe, należy utworzyć logikę filtrowania tak, aby korzystanie z priorytetów filtru nie jest wymagana.  
  
     Poniżej definiuje tabelę filtru i dodaje "Obiekt XPathFilter" wcześniej zdefiniowaną w tabeli o priorytecie 2. Ten wpis określa również, że jeśli obiekt "XPathFilter" pasuje do komunikatu, komunikat będą kierowane do "roundingCalcEndpoint"  
  
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
  
     Podczas określania priorytetu filtru, najwyższy priorytet filtry są obliczane jako pierwsze. Jeśli co najmniej jeden filtr na poziomie określonym priorytecie są zgodne, zostanie ono ocenione żadnych filtrów na niższych poziomach priorytetu. W tym scenariuszu 2 ma najwyższy priorytet, które są określone i jest to jedyny wpis filtru na tym poziomie.  
  
2.  Wpisy filtrów zdefiniowano należy sprawdzać, gdy wiadomość zostaje odebrana w określonym punkcie końcowym, sprawdzając nazwę punktu końcowego lub prefiks adresu. Następujące wpisy Dodaj oba te wpisy filtru do tabeli filtru i skojarzyć je z docelowych punktów końcowych, które wiadomości będą kierowane do. Te filtry są ustawione na priorytet 1 w celu wskazania, że mogą uruchamiać tylko jeśli poprzednie filtr XPath nie był zgodny komunikat.  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     Ponieważ te filtry mają priorytet filtru 1, ich będzie być oceniany tylko jeśli filtr na poziomie priorytetu 2 nie jest zgodny komunikat. Ponadto ponieważ oba filtry mają ten sam poziom priorytetu one zostaną ocenione jednocześnie. Ponieważ zarówno filtry wykluczają się wzajemnie, jest możliwe tylko jedna lub druga do dopasowania komunikatu.  
  
3.  Jeśli komunikat nie pasuje do żadnego z poprzednim filtrom, komunikat zostało odebrane za pośrednictwem punktu końcowego Usługa ogólna i zawarte nie informacje nagłówka, która wskazuje, gdzie w celu kierowania go. Te komunikaty są mają być obsługiwane przez filtr niestandardowy, który równoważy ich między usługami dwóch kalkulatora. Poniższy przykład pokazuje, jak dodać wpisy filtr do filtru tabeli; Każdy filtr jest skojarzony z jedną z dwóch docelowych punktów końcowych.  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     Ponieważ te wpisy określić priorytet 0, ich będzie być oceniany tylko jeśli żaden filtr o wyższym priorytecie jest zgodny komunikat. Ponadto ponieważ oba mają ten sam priorytet, ocenia się je jednocześnie.  
  
     Jak wspomniano wcześniej, filtr niestandardowy używany przez te definicje filtrów oblicza tylko jeden lub inne, `true` dla każdego komunikatu odebranego. Ponieważ tylko dwa filtry są definiowane za pomocą tego samego ustawienia w określonej grupie za pomocą tego filtru, powoduje, że usługa routingu przełącza między wysłaniem regularCalcEndpoint i RoundingCalcEndpoint.  
  
4.  Do analizowania wiadomości te filtry, tabelę filtru najpierw należy skojarzyć z punktami końcowymi usługi, które będą używane do odbierania komunikatów.  Poniższy przykład pokazuje jak skojarzyć tabeli routingu za pomocą punktów końcowych usługi za pomocą zachowania routingu:  
  
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
