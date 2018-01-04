---
title: "Filtry komunikatów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: routing [WCF], message filters
ms.assetid: cb33ba49-8b1f-4099-8acb-240404a46d9a
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd5019668e865d2fea835b450d992d45b5273ed7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="message-filters"></a>Filtry komunikatów
Do wdrożenia na podstawie zawartości routingu, usługa routingu używa <xref:System.ServiceModel.Dispatcher.MessageFilter> implementacje sprawdzić określonych sekcji wiadomości, takie jak adres, nazwa punktu końcowego lub określonych instrukcji XPath. Jeśli żaden komunikat filtrów nie podany z [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] spełnia Twoich potrzeb, można utworzyć niestandardowy filtr przez utworzenie nowego wdrożenia podstawy <xref:System.ServiceModel.Dispatcher.MessageFilter> klasy.  
  
 Podczas konfigurowania usługi routingu, należy zdefiniować filtr elementy (<xref:System.ServiceModel.Routing.Configuration.FilterElement> obiektów) opisują typ **MessageFilter** i obsługi dane wymagane do utworzenia filtru, takie jak wartości określonego ciągu wyszukiwania dla wiadomości. Należy pamiętać, że tylko tworzenie elementów filtr definiuje filtry poszczególnych komunikatów. Aby użyć filtrów w celu oceny i trasy wiadomości musi także definiować tabelę filtru (<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>).  
  
 Każdy wpis w tabeli filtru odwołuje się do elementu filtru i umożliwia określenie punktu końcowego klienta, który wiadomości będą kierowane do Jeśli komunikat jest zgodny z filtrem. Wpisy tabeli filtrów pozwalają również określić kolekcję punktów końcowych kopii zapasowej (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>), który definiuje listę punktów końcowych, które wiadomości zostaną przekazane w przypadku niepowodzenia przesyłania przy wysyłaniu do podstawowego punktu końcowego. Te punkty końcowe zostaną sprawdzone w kolejności określonej aż do znalezienia właściwego konta.  
  
## <a name="message-filters"></a>Filtry komunikatów  
 Filtry komunikatów używane przez usługę Routing Podaj typowe funkcje wybór wiadomości, takie jak nazwa punktu końcowego, że wiadomość została wysłana do akcji SOAP lub adres lub prefiks adresu, który wiadomość została wysłana do oceny. Filtry można również łączyć z `AND` warunek, dzięki czemu wiadomości tylko będą kierowane do punktu końcowego, jeśli komunikat jest zgodny zarówno filtrów. Można również utworzyć filtry niestandardowe, tworząc własne wykonania <xref:System.ServiceModel.Dispatcher.MessageFilter>.  
  
 W poniższej tabeli wymieniono <xref:System.ServiceModel.Routing.Configuration.FilterType> używane przez usługę Routing klasy, która implementuje filtr określonego komunikatu i wymaganych <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> parametrów.  
  
|Typ filtru|Opis|Znaczenie danych filtru|Przykład filtru|  
|------------------|-----------------|-------------------------|--------------------|  
|Akcja|Używa <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> klasę wiadomości zawierające określonej akcji.|Akcja filtrowania na.|\<Nazwa filtru = "action1" filterType = danych filtru "Akcja" = "http://namespace/contract/operation" / >|  
|EndpointAddress|Używa <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> klasy, z <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` odpowiadające wiadomości zawierające określonego adresu.|Adres do filtrowania po (w nagłówku do).|\<Nazwa filtru = "address1" filterType = danych filtru "EndpointAddress" = "http://host/vdir/s.svc/b" / >|  
|EndpointAddressPrefix|Używa <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> klasy, z <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` odpowiadające wiadomości zawierające prefiksu określonego adresu.|Adres do filtrowania przy użyciu najdłuższe dopasowanie prefiksów.|\<Nazwa filtru = "prefix1" filterType = danych filtru "EndpointAddressPrefix" = "http://host/" / >|  
|I|Używa <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> klasy, która zawsze ocenia oba warunki przed zwróceniem.|danych filtru nie jest używany; Zamiast tego Filtr1 i filtr2 mają nazwy odpowiedniego komunikatu filtrów (również w tabeli), które powinny być **i**ed razem.|\<Nazwa filtru = filterType "and1" = "I" Filtr1 = filtr2 "address1" = "action1" / >|  
|Niestandardowe|Zdefiniowane przez użytkownika typu, rozszerzający <xref:System.ServiceModel.Dispatcher.MessageFilter> klasy i ma konstruktor przyjmujący ciąg.|Customtype — atrybut jest typu w pełni kwalifikowaną nazwę klasy w celu utworzenia; danych filtru jest parametry do przekazania do konstruktora podczas tworzenia filtru.|\<Nazwa filtru = filterType "custom1" = "Custom" customType="CustomAssembly.CustomMsgFilter, CustomAssembly" danych filtru = "Dane niestandardowe" / >|  
|EndpointName|Używa <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> klasę wiadomości na podstawie nazwy przybyły na punktu końcowego usługi.|Nazwa punktu końcowego usługi, na przykład: "serviceEndpoint1".  Powinno to być jeden z punktów końcowych, narażone na usługi routingu.|\<Nazwa filtru = "stock1" filterType = danych filtru "Punktu końcowego" = "SvcEndpoint" / >|  
|MatchAll|Używa <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> klasy. Ten filtr dopasowuje wszystkie komunikaty o nadchodzących.|danych filtru nie jest używany. Ten filtr będzie zawsze zgodna wszystkie komunikaty.|\<Nazwa filtru = filterType "matchAll1" = "MatchAll" / >|  
|XPath|Używa <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> klasy do dopasowania określonej kwerendy XPath w komunikacie.|Zapytanie XPath do użycia podczas dopasowywania komunikatów.|\<Nazwa filtru = "XPath1" filterType = danych filtru "XPath" = "//ns:element" / >|  
  
 W poniższym przykładzie zdefiniowano filtru wpisów, które należy używać filtrów wiadomości XPath, EndpointName i PrefixEndpointAddress. W przykładzie pokazano także przy użyciu niestandardowego filtru dla wpisów RoundRobinFilter1 i RoundRobinFilter2.  
  
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
>  Po prostu Definiowanie filtru nie powoduje wiadomości ma zostać obliczone dla filtru. Filtr musi zostać dodany do tabeli filtr, który jest następnie skojarzone z punktem końcowym usługi udostępniane przez usługi routingu.  
  
### <a name="namespace-table"></a>Namespace tabeli  
 Podczas korzystania z filtrów XPath, dane filtr zawiera zapytanie XPath może stać się bardzo dużą z powodu używania przestrzeni nazw. Aby rozwiązanie tego problemu usługa routingu udostępnia możliwość definiowania własnych prefiksy przestrzeni nazw przy użyciu tabeli nazw.  
  
 Tabela nazw jest kolekcją <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> obiektów, które definiuje prefiksy przestrzeni nazw dla typowych przestrzenie nazw, które mogą być używane w elemencie XPath. Poniżej przedstawiono domyślne obszary nazw i przestrzeni nazw prefiksów, które znajdują się w tabeli nazw.  
  
|Prefiks|Przestrzeń nazw|  
|------------|---------------|  
|S11|http://schemas.xmlsoap.org/SOAP/Envelope|  
|S12|http://www.w3.org/2003/05/SOAP-Envelope|  
|wsaAugust2004|http://schemas.xmlsoap.org/ws/2004/08/Addressing|  
|wsa10|http://www.w3.org/2005/08/Addressing|  
|SM|http://schemas.microsoft.com/ServiceModel/2004/05/xpathfunctions|  
|tempuri|http://tempuri.org|  
|ser|http://schemas.microsoft.com/2003/10/serialization|  
  
 Gdy wiesz, że będziesz używać określonego obszaru nazw zapytania XPath, można dodać go do tabeli przestrzeni nazw, wraz z prefiksem unikatową przestrzeń nazw i Użyj prefiksu w każde zapytanie XPath zamiast pełnej przestrzeni nazw. W poniższym przykładzie zdefiniowano prefiksu "niestandardowe" w przestrzeni nazw "http://my.custom.namespace", który jest następnie używany w zapytaniu XPath zawarte w danych filtru.  
  
```xml  
<namespaceTable>  
     <add prefix="custom" namespace="http://my.custom.namespace/"/>  
</namespaceTable>  
<filters>  
     <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
</filters>  
```  
  
## <a name="filter-tables"></a>Tabele filtru  
 Podczas każdego elementu filtr definiuje logicznej porównanie, które mogą być stosowane do wiadomości, tabeli filtru zawiera skojarzenie elementu filtr docelowy punkt końcowy klienta. Tabela Filtr jest nazwanej kolekcji <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> obiekty, które określają skojarzenie między filtru, punkt końcowy miejsce docelowe głównej i listę alternatywnej kopii zapasowej punktów końcowych. Wpisy tabeli filtrów pozwalają również określić opcjonalny priorytet dla każdego warunku filtru. W poniższym przykładzie definiuje dwa filtry i następnie definiuje tabeli filtrów, które kojarzy każdego filtru z docelowym punktem końcowym.  
  
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
 Domyślnie wszystkie wpisy w tabeli filtru są oceniane jednocześnie, a komunikat oceniane jest kierowany do punktów końcowych skojarzonych z każdego pasującego wpisu filtru. Jeśli mają wiele filtrów `true`i wiadomość jest jednokierunkowa lub dupleks, wiadomość jest multiemisji do punktów końcowych dla wszystkie filtry zgodne. Komunikaty żądanie odpowiedź nie może być multiemisji, ponieważ tylko jedną odpowiedź może być zwracany do klienta.  
  
 Bardziej złożonej logiki routingu może być zaimplementowany przez określenie priorytetów dla każdego filtru; Usługa routingu najpierw sprawdza wszystkie filtry na najwyższym poziomie priorytetu. Jeśli komunikat jest zgodny z filtrem tego poziomu, są przetwarzane żadnych filtrów o niższym priorytecie. Na przykład przychodzącego komunikatu jednokierunkowego najpierw jest porównywany wszystkie filtry o priorytecie 2. Komunikat nie pasuje do żadnego filtru na tym poziomie priorytetu, więc obok komunikatu jest porównywana filtry o priorytecie 1. Dwa filtry o priorytecie 1 zgodny komunikat, a ponieważ jest on komunikat jednokierunkowy jest kierowany do punktów końcowych zarówno docelowego.  Ponieważ między filtry o priorytecie 1 znaleziono dopasowania, są oceniane żadnych filtrów priorytet 0.  
  
> [!NOTE]
>  Jeśli jest określony żaden priorytet, jest używany domyślny priorytet 0.  
  
 W poniższym przykładzie zdefiniowano filtru tabeli, która określa priorytety 2, 1 i 0 dla filtrów odwołuje się do tabeli.  
  
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
  
 W poprzednim przykładzie Jeśli obiekt XPathFilter dopasuje komunikat o stanie, zostaną przesłane roundingCalcEndpoint i żadne dodatkowe filtry w tabeli zostanie obliczone, ponieważ wszystkie pozostałe filtry o niższym priorytecie. Jednak jeśli komunikat jest niezgodny obiekt XPathFilter następnie jest szacowana wszystkie filtry dalej niższego priorytetu, EndpointNameFilter i PrefixAddressFilter.  
  
> [!NOTE]
>  Jeśli to możliwe, należy używać filtrów wyłącznego zamiast określania priorytet, ponieważ obliczanie priorytetu może spowodować obniżenie wydajności.  
  
### <a name="backup-lists"></a>Listy kopii zapasowej  
 Każdy filtr w tabeli filtrów można opcjonalnie określić listy kopii zapasowych, który jest nazywany kolekcją punktów końcowych (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>). Ta kolekcja zawiera uporządkowaną listę punktów końcowych, które wiadomości zostaną przekazane w przypadku <xref:System.ServiceModel.CommunicationException> przy wysyłaniu do podstawowy punkt końcowy określony w <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A>. W poniższym przykładzie zdefiniowano listy kopii zapasowych o nazwie "backupServiceEndpoints", który zawiera dwa punkty końcowe.  
  
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
  
 W poprzednim przykładzie, jeśli wysyłania do podstawowego punktu końcowego "Miejsce docelowe" zakończy się niepowodzeniem, usługa routingu spróbuje wysyłane do każdego punktu końcowego w sekwencji, są one wyświetlane, najpierw wysyłane do backupServiceQueue i następnie wysyłanie do alternateServiceQueue, jeśli Wyślij do backupServiceQueue kończy się niepowodzeniem. Jeśli wszystkie punkty końcowe kopii zapasowej zakończą się niepowodzeniem, zostanie zwrócony błąd.
