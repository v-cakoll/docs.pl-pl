---
title: Filtry komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], message filters
ms.assetid: cb33ba49-8b1f-4099-8acb-240404a46d9a
ms.openlocfilehash: fc4656a76894eb3a844bc9f2187847fd9eff0ffe
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48839108"
---
# <a name="message-filters"></a>Filtry komunikatów
Aby zaimplementować, routingu opartego na zawartości, usługa routingu korzysta z <xref:System.ServiceModel.Dispatcher.MessageFilter> implementacji, które sprawdzanie określonych sekcji wiadomości, takich jak adres, nazwę punktu końcowego lub określonych instrukcji języka XPath. Jeśli żaden z filtry komunikatów za pomocą [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] własnych potrzeb, możesz utworzyć niestandardowy filtr, tworząc nową metodę implementacji elementu bazowego <xref:System.ServiceModel.Dispatcher.MessageFilter> klasy.  
  
 Podczas konfigurowania usługi routingu, należy zdefiniować elementy filtru (<xref:System.ServiceModel.Routing.Configuration.FilterElement> obiektów) opisują typ **MessageFilter** i wszystkie pomocnicze dane wymagane do utworzenia filtru, takie jak wartości określonego ciągu wyszukiwania dla wiadomości. Należy pamiętać, że tylko tworzenie elementów filtr definiuje filtry jednego komunikatu. Aby używać filtrów do oceny i kierowanie komunikatów w postaci należy także zdefiniować tabelę filtru (<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>).  
  
 Każdy wpis w tabeli filtr odwołuje się element filtru i określa punkt końcowy klienta, który komunikat będą kierowane do komunikatu jest zgodny z filtrem. Filtr wpisów tabeli pozwalają również na Określ kolekcję punktów końcowych kopii zapasowej (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>), który definiuje listę punktów końcowych, które wiadomość zostanie przesłana do awarii transmisji podczas wysyłania do podstawowego punktu końcowego. Te punkty końcowe zostaną sprawdzone w kolejności określonej, aż któraś się powiedzie.  
  
## <a name="message-filters"></a>Filtry komunikatów  
 Filtry komunikatów używane przez usługę Routing zawierają typowe funkcje wybór wiadomości, takie jak nazwa punktu końcowego, który wiadomość została wysłana do Akcja SOAP lub adresu lub prefiksu adresu, który została wysłana wiadomość do oceny. Filtry można również łączyć z `AND` warunku, dzięki czemu komunikaty tylko będą kierowane do punktu końcowego, jeśli oba filtry dopasuje komunikat o stanie. Można również utworzyć niestandardowe filtry, tworząc własną implementację <xref:System.ServiceModel.Dispatcher.MessageFilter>.  
  
 W poniższej tabeli wymieniono <xref:System.ServiceModel.Routing.Configuration.FilterType> używane przez usługę Routing klasy, która implementuje filtr szczegółowy komunikat o błędzie i wymagane <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> parametrów.  
  
|Typ filtru|Opis|Filtruj dane znaczenia|Przykład filtru|  
|------------------|-----------------|-------------------------|--------------------|  
|Akcja|Używa <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> klasę wiadomości zawierające określonej akcji.|Akcja do filtrowania.|\<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation" />|  
|EndpointAddress|Używa <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> klasy, za pomocą <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` do dopasowania komunikaty zawierające określonego adresu.|Adres do filtrowania (w nagłówku To).|\<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b"  />|  
|EndpointAddressPrefix|Używa <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> klasy, za pomocą <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` do dopasowania komunikaty zawierające prefiksu określonego adresu.|Adres do filtrowania przy użyciu najdłuższy zgodny prefiks.|\<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/" />|  
|i|Używa <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> klasę, która zawsze ocenia oba warunki przed zwróceniem.|danych filtru nie jest używany; Zamiast tego Filtr1 i filtr2 mają nazwy odpowiednie filtry komunikatów (również w tabeli), które powinny być **i**ed razem.|\<filter name="and1" filterType="And" filter1="address1" filter2="action1" />|  
|Niestandardowe|Typ zdefiniowany przez użytkownika, która rozszerza <xref:System.ServiceModel.Dispatcher.MessageFilter> klasy i ma konstruktora biorąc ciągu.|Atrybut customtype — jest w pełni kwalifikowana nazwa typu klasy, aby utworzyć; danych filtru jest parametry do przekazania do konstruktora, podczas tworzenia filtru.|\<filter name="custom1" filterType="Custom" customType="CustomAssembly.CustomMsgFilter, CustomAssembly" filterData="Custom Data" />|  
|EndpointName|Używa <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> klasę wiadomości na podstawie nazwy przybyły na punktu końcowego usługi.|Nazwa punktu końcowego usługi, na przykład: "serviceEndpoint1".  Powinno to być jeden z punktów końcowych dostępne w usłudze Routing.|\<filter name="stock1" filterType="Endpoint" filterData="SvcEndpoint" />|  
|MatchAll|Używa <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> klasy. Ten filtr dopasowuje wartość do wszystkich nadchodzących wiadomości.|danych filtru nie jest używana. Ten filtr będzie zawsze zgodna wszystkie komunikaty.|\<filter name="matchAll1" filterType="MatchAll" />|  
|XPath|Używa <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> klasy w celu dopasowania określonej kwerendy XPath w komunikacie.|Zapytanie XPath do użycia podczas dopasowywania komunikatów.|\<filter name="XPath1" filterType="XPath" filterData="//ns:element" />|  
  
 W poniższym przykładzie zdefiniowano wpisy filtrów, korzystających z XPath, Nazwapunktukoncowego i PrefixEndpointAddress filtry wiadomości. W przykładzie pokazano również przy użyciu niestandardowego filtru dla wpisów RoundRobinFilter1 i RoundRobinFilter2.  
  
```xml  
<filters>  
     <filter name="XPathFilter" filterType="XPath"   
             filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
     <filter name="EndpointNameFilter" filterType="EndpointName"   
             filterData="calculatorEndpoint"/>  
     <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"   
             filterData="http://localhost/routingservice/router/rounding/"/>  
     <filter name="RoundRobinFilter1" filterType="Custom"   
             customType="RoutingServiceFilters.RoundRobinMessageFilter,   
             RoutingService" filterData="group1"/>  
     <filter name="RoundRobinFilter2" filterType="Custom"   
             customType="RoutingServiceFilters.RoundRobinMessageFilter,   
             RoutingService" filterData="group1"/>  
</filters>  
```  
  
> [!NOTE]
>  Po prostu zdefiniowanie filtru nie powoduje wiadomości, które ma zostać obliczone dla filtru. Filtr muszą zostać dodane do tabeli filtr, który jest skojarzony z punktem końcowym usługi udostępniane przez usługę routingu.  
  
### <a name="namespace-table"></a>Tabela Namespace  
 Korzystając z filtr XPath, dane filtru, który zawiera zapytanie XPath może stać się bardzo duże, ze względu na użycie przestrzeni nazw. Złagodzić ten problem usługa routingu umożliwia definiowanie własnych prefiksy przestrzeni nazw przy użyciu tabeli przestrzeni nazw.  
  
 Tabela nazw jest kolekcją <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> obiektów, które określa prefiksy przestrzeni nazw dla popularnych przestrzeni nazw, który może służyć w wyrażenie XPath. Poniżej przedstawiono domyślne obszary nazw i przestrzeni nazw prefiksy, które są zawarte w tabeli przestrzeni nazw.  
  
|Prefiks|Przestrzeń nazw|  
|------------|---------------|  
|s11|`http://schemas.xmlsoap.org/soap/envelope`|  
|s12|`http://www.w3.org/2003/05/soap-envelope`|  
|wsaAugust2004|`http://schemas.xmlsoap.org/ws/2004/08/addressing`|  
|wsa10|`http://www.w3.org/2005/08/addressing`|  
|sm|`http://schemas.microsoft.com/serviceModel/2004/05/xpathfunctions`|  
|tempuri|`http://tempuri.org`|  
|ser|`http://schemas.microsoft.com/2003/10/Serialization`|  
  
 Gdy wiadomo, że będziesz używać określonych przestrzeni nazw w zapytaniach XPath, możesz dodać go do tabeli przestrzeni nazw, wraz z prefiksem unikatową przestrzeń nazw i Użyj prefiksu w każdym zapytaniu XPath zamiast pełnego przestrzeni nazw. W poniższym przykładzie zdefiniowano prefiksu "niestandardowe" dla przestrzeni nazw `"http://my.custom.namespace"`, który jest następnie używany w zapytaniu XPath zawarte w danych filtru.  
  
```xml  
<namespaceTable>  
     <add prefix="custom" namespace="http://my.custom.namespace/"/>  
</namespaceTable>  
<filters>  
     <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
</filters>  
```  
  
## <a name="filter-tables"></a>Filtrowanie tabel  
 Gdy każdy element filtr definiuje logiczne porównanie, które mogą być stosowane do wiadomości, tabelę filtru zawiera skojarzenia między elementem filtru i docelowy punkt końcowy klienta. Tabela filtru jest nazywany kolekcją <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> obiekty, które określają skojarzenie między filtru, punktu końcowego podstawowego docelowego i listę alternatywne punkty końcowe kopii zapasowej. Wpisów tabeli filtru umożliwiają również określić opcjonalne priorytet dla każdego warunku filtru. Poniższy przykład definiuje dwa filtry, a następnie definiuje tabelę filtru, który kojarzy każdy filtr z docelowy punkt końcowy.  
  
```xml  
<routing>  
     <filters>  
       <filter name="AddAction" filterType="Action" filterData="Add" />  
       <filter name="SubtractAction" filterType="Action" filterData="Subtract" />  
     </filters>  
     <filterTables>  
       <table name="routingTable1">  
         <filters>  
           <add filterName="AddAction" endpointName="Addition" />  
           <add filterName="SubtractAction" endpointName="Subtraction" />  
         </filters>  
       </table>  
     </filterTables>      
</routing>  
```  
  
### <a name="filter-evaluation-priority"></a>Priorytet oceny filtru  
 Domyślnie wszystkie wpisy w tabeli filtru są oceniane jednocześnie, a komunikat Trwa obliczanie jest kierowany do punkty końcowe: skojarzone z każdego zgodnego wpisu filtru. Jeśli mają wiele filtrów `true`i wiadomości jest jednokierunkowa lub dupleks się komunikat multiemisji do punktów końcowych dla wszystkich zgodnych filtrów. Komunikaty "żądanie-odpowiedź" nie może być multiemisji, ponieważ mogą być zwracane tylko jedną odpowiedź do klienta.  
  
 Można zaimplementować bardziej złożonej logiki routingu, określając poziomy priorytetów dla każdego filtru; Usługa routingu najpierw sprawdza wszystkie filtry na najwyższym poziomie priorytetu. Jeśli komunikat dopasowana do filtru tego poziomu, żadnych filtrów o niższym priorytecie będą przetwarzane. Na przykład jednokierunkowej wiadomości przychodzące najpierw zostaną ocenione względem wszystkich filtrów o priorytecie 2. Komunikatu nie pasuje do żadnego filtru na tym poziomie priorytetu więc obok komunikatu jest porównywana z priorytetem 1 filtrów. Dwa filtry priorytet 1 zgodny komunikat, a ponieważ komunikat jednokierunkowy jest kierowany do obu docelowych punktów końcowych.  Ponieważ między filtrami o priorytecie 1 zostało znalezione dopasowanie, są obliczane żadnych filtrów priorytet 0.  
  
> [!NOTE]
>  Jeśli nie określono priorytetu, jest używany domyślny priorytet 0.  
  
 W poniższym przykładzie zdefiniowano tabelę filtru, który określa priorytety 2, 1 i 0 dla filtrów, do których odwołuje się w tabeli.  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="XPathFilter" endpointName="roundingCalcEndpoint"   
               priority="2"/>  
          <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint"   
               priority="1"/>  
          <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint"   
               priority="1"/>  
          <add filterName="MatchAllMessageFilter" endpointName="defaultCalcEndpoint"   
               priority="0"/>  
     </filterTable>  
</filterTables>  
```  
  
 W poprzednim przykładzie Jeśli obiekt XPathFilter dopasuje komunikat o stanie, będą kierowane roundingCalcEndpoint i żadne dodatkowe filtry w tabeli zostaną ocenione, ponieważ wszystkie pozostałe filtry są o niższym priorytecie. Jednak jeśli komunikat jest niezgodny obiekt XPathFilter go następnie ocenia się ze wszystkimi filtrami dalej niższego priorytetu, EndpointNameFilter i PrefixAddressFilter.  
  
> [!NOTE]
>  Jeśli to możliwe, należy użyć filtrów wyłączne zamiast określania priorytet, ponieważ obliczanie priorytetu może spowodować obniżenie wydajności.  
  
### <a name="backup-lists"></a>Listy kopii zapasowej  
 Każdy filtr w tabeli filtru można opcjonalnie określić listy kopii zapasowych, który jest nazywany kolekcją punktów końcowych (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>). Ta kolekcja zawiera uporządkowaną listę punktów końcowych, które wiadomości zostaną przekazane w przypadku powstania <xref:System.ServiceModel.CommunicationException> podczas wysyłania do podstawowego punktu końcowego określonego w <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A>. W poniższym przykładzie zdefiniowano listy kopii zapasowych o nazwie "backupServiceEndpoints", który zawiera dwa punkty końcowe.  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="MatchAllFilter1" endpointName="Destination" backupList="backupEndpointList"/>  
     </filterTable>  
</filterTables>  
<backupLists>  
     <backupList name="backupEndpointList">  
          <add endpointName="backupServiceQueue" />  
          <add endpointName="alternateServiceQueue" />  
     </backupList>  
</backupLists>  
```  
  
 W poprzednim przykładzie, jeśli wysłanie do podstawowego punktu końcowego "Miejsce docelowe" zakończy się niepowodzeniem, usługa routingu spróbuje wysyłane do każdego punktu końcowego w kolejności, w jakiej występują na liście, wysyłce backupServiceQueue i następnie wysłanie do alternateServiceQueue, jeśli Wyślij do backupServiceQueue kończy się niepowodzeniem. Jeśli wszystkie punkty końcowe kopii zapasowej zakończy się niepowodzeniem, zwracany jest błąd.
