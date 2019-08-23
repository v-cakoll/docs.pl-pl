---
title: Filtry komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], message filters
ms.assetid: cb33ba49-8b1f-4099-8acb-240404a46d9a
ms.openlocfilehash: b8de58b6935ee59fc8c787dfcf7445afcd0774b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912699"
---
# <a name="message-filters"></a>Filtry komunikatów
W celu zaimplementowania routingu opartego na zawartości Usługa <xref:System.ServiceModel.Dispatcher.MessageFilter> routingu korzysta z implementacji, które sprawdzają konkretne sekcje komunikatu, takie jak adres, nazwa punktu końcowego lub określona instrukcja XPath. Jeśli żaden z filtrów [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] komunikatów nie spełnia wymagań, można utworzyć niestandardowy filtr, tworząc nową implementację klasy bazowej. <xref:System.ServiceModel.Dispatcher.MessageFilter>  
  
 Podczas konfigurowania usługi routingu należy zdefiniować elementy filtru (<xref:System.ServiceModel.Routing.Configuration.FilterElement> obiekty) opisujące typ **MessageFilter** i wszystkie dane pomocnicze wymagane do utworzenia filtru, takie jak określone wartości ciągu do wyszukania w komunikacie. . Należy pamiętać, że tworzenie elementów filtru definiuje tylko pojedyncze filtry komunikatów; Aby użyć filtrów do obliczenia i trasy komunikatów, należy również zdefiniować tabelę filtrów (<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>).  
  
 Każdy wpis w tabeli filtrów odwołuje się do elementu Filter i określa punkt końcowy klienta, do którego zostanie rozesłany komunikat, jeśli komunikat jest zgodny z filtrem. Wpisy tabeli filtru umożliwiają również określenie kolekcji punktów końcowych kopii zapasowych (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>), która definiuje listę punktów końcowych, do których zostanie przesłany komunikat w przypadku niepowodzenia transmisji podczas wysyłania do podstawowego punktu końcowego. Te punkty końcowe zostaną ponowione w kolejności określonej do momentu sukcesu jednego.  
  
## <a name="message-filters"></a>Filtry komunikatów  
 Filtry komunikatów używane przez usługę routingu zapewniają wspólną funkcję wyboru komunikatów, takie jak ocenianie nazwy punktu końcowego, do którego wysłano wiadomość, akcję protokołu SOAP lub adres lub prefiks adresu, do którego wiadomość została wysłana. Filtry można również dołączać z `AND` warunkiem, tak aby komunikaty były kierowane tylko do punktu końcowego, jeśli wiadomość pasuje do obu filtrów. Możesz również utworzyć niestandardowe filtry, tworząc własną implementację programu <xref:System.ServiceModel.Dispatcher.MessageFilter>.  
  
 W poniższej tabeli wymieniono <xref:System.ServiceModel.Routing.Configuration.FilterType> używane przez usługę routingu, klasę implementującą konkretny filtr komunikatów i wymagane <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> parametry.  
  
|Typ filtru|Opis|Filtrowanie danych znaczenie|Przykładowy filtr|  
|------------------|-----------------|-------------------------|--------------------|  
|Akcja|<xref:System.ServiceModel.Dispatcher.ActionMessageFilter> Używa klasy do dopasowywania komunikatów zawierających określoną akcję.|Akcja do filtrowania.|\<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation" />|  
|Elemencie|Używa klasy, z <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  aby dopasowaćkomunikatyzawierająceokreślonyadres.`true` <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>|Adres do filtrowania (w nagłówku do).|\<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b"  />|  
|EndpointAddressPrefix|Używa klasy, z <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  aby dopasowaćkomunikatyzawierająceokreślonyprefiksadresu.`true` <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>|Adres do filtrowania przy użyciu najdłuższych pasujących prefiksów.|\<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/" />|  
|Oraz|<xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> Używa klasy, która zawsze oblicza oba warunki przed zwróceniem.|Danych filtru nie jest używany; Zamiast tego Filter1 i Filter2 mają nazwy odpowiednich filtrów komunikatów (również w tabeli), które powinny być **i**Ed razem.|\<filter name="and1" filterType="And" filter1="address1" filter2="action1" />|  
|Celnej|Typ zdefiniowany przez użytkownika, który rozszerza <xref:System.ServiceModel.Dispatcher.MessageFilter> klasę i ma konstruktora pobierającego ciąg.|Atrybut CustomType jest w pełni kwalifikowaną nazwą typu klasy do utworzenia; Danych filtru jest ciągiem, który ma zostać przekazany do konstruktora podczas tworzenia filtru.|\<filter name="custom1" filterType="Custom" customType="CustomAssembly.CustomMsgFilter, CustomAssembly" filterData="Custom Data" />|  
|EndpointName|<xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> Używa klasy w celu dopasowania komunikatów na podstawie nazwy punktu końcowego usługi, w którym dotarły.|Nazwa punktu końcowego usługi, na przykład: "serviceEndpoint1".  Powinien to być jeden z punktów końcowych uwidocznionych w usłudze routingu.|\<filter name="stock1" filterType="Endpoint" filterData="SvcEndpoint" />|  
|MatchAll|<xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> Używa klasy. Ten filtr dopasowuje wszystkie przychodzące komunikaty.|Danych filtru nie jest używany. Ten filtr będzie zawsze pasować do wszystkich komunikatów.|\<filter name="matchAll1" filterType="MatchAll" />|  
|XPath|<xref:System.ServiceModel.Dispatcher.XPathMessageFilter> Używa klasy do dopasowania określonych zapytań XPath w komunikacie.|Zapytanie XPath, które ma być używane podczas dopasowywania komunikatów.|\<filter name="XPath1" filterType="XPath" filterData="//ns:element" />|  
  
 W poniższym przykładzie zdefiniowano wpisy filtru, które używają filtrów XPath, EndpointName i PrefixEndpointAddress. Ten przykład ilustruje także użycie filtru niestandardowego dla wpisów RoundRobinFilter1 i RoundRobinFilter2.  
  
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
> Po prostu Definiowanie filtru nie powoduje, że komunikaty są oceniane względem filtru. Filtr należy dodać do tabeli filtrów, która jest następnie skojarzona z punktem końcowym usługi udostępnianym przez usługę routingu.  
  
### <a name="namespace-table"></a>Tabela przestrzeni nazw  
 W przypadku korzystania z filtru XPath dane filtru zawierające zapytanie XPath mogą stać się bardzo duże ze względu na użycie przestrzeni nazw. Aby rozwiązać ten problem, usługa routingu zapewnia możliwość definiowania własnych prefiksów przestrzeni nazw za pomocą tabeli przestrzeni nazw.  
  
 Tabela przestrzeni nazw to kolekcja <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> obiektów, która definiuje prefiksy przestrzeni nazw dla wspólnych przestrzeni nazw, które mogą być używane w XPath. Poniżej znajdują się domyślne przestrzenie nazw i prefiksy przestrzeni nazw, które są zawarte w tabeli przestrzeni nazw.  
  
|Prefiks|Przestrzeń nazw|  
|------------|---------------|  
|s11|`http://schemas.xmlsoap.org/soap/envelope`|  
|s12|`http://www.w3.org/2003/05/soap-envelope`|  
|wsaAugust2004|`http://schemas.xmlsoap.org/ws/2004/08/addressing`|  
|wsa10|`http://www.w3.org/2005/08/addressing`|  
|sm|`http://schemas.microsoft.com/serviceModel/2004/05/xpathfunctions`|  
|tempuri|`http://tempuri.org`|  
|ser|`http://schemas.microsoft.com/2003/10/Serialization`|  
  
 Jeśli wiesz, że w zapytaniach XPath będziesz używać konkretnej przestrzeni nazw, możesz dodać ją do tabeli przestrzeni nazw wraz z unikatowym prefiksem przestrzeni nazw i użyć prefiksu w dowolnym zapytaniu XPath zamiast w całej przestrzeni nazw. Poniższy przykład definiuje prefiks "Custom" dla przestrzeni nazw `"http://my.custom.namespace"`, który jest następnie używany w zapytaniu XPath zawartym w danych filtru.  
  
```xml  
<namespaceTable>  
     <add prefix="custom" namespace="http://my.custom.namespace/"/>  
</namespaceTable>  
<filters>  
     <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
</filters>  
```  
  
## <a name="filter-tables"></a>Filtruj tabele  
 Chociaż każdy element filtru definiuje logiczne porównanie, które można zastosować do komunikatu, tabela filtrów zawiera skojarzenie między elementem Filter i docelowym punktem końcowym klienta. Tabela filtrów to nazwana kolekcja <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> obiektów, która definiuje skojarzenie między filtrem, głównym punktem końcowym i listą alternatywnych punktów końcowych kopii zapasowych. Wpisy tabeli filtru umożliwiają również określenie opcjonalnego priorytetu dla każdego warunku filtru. W poniższym przykładzie zdefiniowano dwa filtry, a następnie zdefiniowano tabelę filtru, która kojarzy każdy filtr z docelowym punktem końcowym.  
  
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
 Domyślnie wszystkie wpisy w tabeli filtrów są oceniane jednocześnie, a oceniany komunikat jest kierowany do punktów końcowych skojarzonych z każdym pasującym wpisem filtru. W przypadku obliczenia `true`wielu filtrów, a komunikat jest jednokierunkowy lub dupleksowy, komunikat jest multiemisją dla punktów końcowych dla wszystkich zgodnych filtrów. Komunikaty żądanie-odpowiedź nie mogą być multiemisją, ponieważ do klienta można zwrócić tylko jedną odpowiedź.  
  
 Bardziej złożoną logikę routingu można zaimplementować przez określenie poziomów priorytetów dla każdego filtru; Usługa routingu najpierw szacuje wszystkie filtry na najwyższym poziomie priorytetu. Jeśli komunikat jest zgodny z filtrem tego poziomu, nie są przetwarzane żadne filtry o niższym priorytecie. Na przykład przychodzące komunikaty jednokierunkowe są najpierw oceniane względem wszystkich filtrów o priorytecie 2. Komunikat nie jest zgodny z żadnym filtrem na tym poziomie priorytetu, dlatego następny komunikat jest porównywany z filtrami o priorytecie 1. Dwa filtry o priorytecie 1 pasują do komunikatu, ponieważ jest to komunikat jednokierunkowy, który jest kierowany do obu docelowych punktów końcowych.  Ponieważ znaleziono dopasowanie między filtrami o priorytecie 1, nie są oceniane żadne filtry o priorytecie 0.  
  
> [!NOTE]
> Jeśli priorytet nie zostanie określony, zostanie użyty domyślny priorytet 0.  
  
 W poniższym przykładzie zdefiniowano tabelę filtru, która określa priorytety 2, 1 i 0 dla filtrów, do których odwołuje się tabela.  
  
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
  
 W poprzednim przykładzie, jeśli komunikat jest zgodny z obiekt XPathFilter, zostanie on rozesłany do roundingCalcEndpoint i żadne dalsze filtry w tabeli nie zostaną ocenione, ponieważ wszystkie inne filtry mają niższy priorytet. Jeśli jednak wiadomość nie jest zgodna z obiekt XPathFilter, zostanie ona oceniona względem wszystkich filtrów o następnym niższym priorytecie, EndpointNameFilter i PrefixAddressFilter.  
  
> [!NOTE]
> Jeśli to możliwe, użyj filtrów wyłącznych zamiast określania priorytetu, ponieważ Ocena priorytetów może spowodować spadek wydajności.  
  
### <a name="backup-lists"></a>Listy kopii zapasowych  
 Każdy filtr w tabeli filtrów może opcjonalnie określić listę kopii zapasowych, która jest nazwaną kolekcją punktów końcowych (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>). Ta kolekcja zawiera uporządkowaną listę punktów końcowych, do których zostanie przesłany komunikat w przypadku <xref:System.ServiceModel.CommunicationException> wysyłania do podstawowego punktu końcowego określonego w. <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A> W poniższym przykładzie zdefiniowano listę kopii zapasowych o nazwie "backupServiceEndpoints", która zawiera dwa punkty końcowe.  
  
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
  
 W poprzednim przykładzie, Jeśli wysyłanie do podstawowego punktu końcowego nie powiedzie się, usługa routingu podejmie próbę wysłania do każdego punktu końcowego w sekwencji, które są wyświetlane, po raz pierwszy wysyła do backupServiceQueue, a następnie wysyła do alternateServiceQueue, jeśli Wysyłanie do backupServiceQueue nie powiodło się. Jeśli wszystkie punkty końcowe kopii zapasowej zakończą się niepowodzeniem, zwracany jest błąd.
