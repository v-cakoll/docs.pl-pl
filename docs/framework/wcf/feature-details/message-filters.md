---
title: Filtry komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], message filters
ms.assetid: cb33ba49-8b1f-4099-8acb-240404a46d9a
ms.openlocfilehash: a953dea9224d75907c593d87f06a0b0888f0af2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184660"
---
# <a name="message-filters"></a>Filtry komunikatów
Aby zaimplementować routing oparty na <xref:System.ServiceModel.Dispatcher.MessageFilter> zawartości, usługa routingu używa implementacji, które sprawdzają określone sekcje wiadomości, takie jak adres, nazwa punktu końcowego lub określona instrukcja XPath. Jeśli żaden z filtrów [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] wiadomości dostarczonych z potrzebami, można utworzyć filtr niestandardowy, tworząc nową implementację klasy podstawowej. <xref:System.ServiceModel.Dispatcher.MessageFilter>  
  
 Podczas konfigurowania usługi routingu należy zdefiniować elementy filtru (obiekty),<xref:System.ServiceModel.Routing.Configuration.FilterElement> które opisują typ **MessageFilter** i wszelkie dane pomocnicze wymagane do utworzenia filtru, takie jak określone wartości ciągu do wyszukania w wiadomości. Należy zauważyć, że tworzenie elementów filtru definiuje tylko poszczególne filtry wiadomości; aby użyć filtrów do oceny i rozsyłania<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>komunikatów, należy również zdefiniować tabelę filtrów ( ).  
  
 Każdy wpis w tabeli filtrów odwołuje się do elementu filtru i określa punkt końcowy klienta, do którego zostanie przekierowany komunikat, jeśli wiadomość jest zgodna z filtrem. Wpisy tabeli filtrów umożliwiają również określenie kolekcji<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>kopii zapasowych punktów końcowych ( ), która definiuje listę punktów końcowych, do których wiadomość będzie przesyłana w przypadku awarii transmisji podczas wysyłania do podstawowego punktu końcowego. Te punkty końcowe zostaną wypróbowane w określonej kolejności, dopóki jeden zakończy się pomyślnie.  
  
## <a name="message-filters"></a>Filtry komunikatów  
 Filtry wiadomości używane przez usługę routingu zapewniają typowe funkcje wyboru komunikatów, takie jak ocena nazwy punktu końcowego, do którego wysłano wiadomość, akcji SOAP lub prefiksu adresu lub adresu, do którego wiadomość została wysłana. Filtry można również łączyć `AND` z warunkiem, dzięki czemu wiadomości będą kierowane do punktu końcowego tylko wtedy, gdy wiadomość pasuje do obu filtrów. Można również utworzyć filtry niestandardowe, tworząc <xref:System.ServiceModel.Dispatcher.MessageFilter>własną implementację programu .  
  
 W poniższej <xref:System.ServiceModel.Routing.Configuration.FilterType> tabeli wymieniono używane przez usługę routingu, klasę, która <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> implementuje filtr określonych wiadomości i wymagane parametry.  
  
|Typ filtru|Opis|Znaczenie danych filtrowania|Przykładowy filtr|  
|------------------|-----------------|-------------------------|--------------------|  
|Akcja|Używa klasy, <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> aby dopasować wiadomości zawierające określoną akcję.|Akcja do filtrowania.|\<nazwa filtra="action1" filterType="Action" filterData="http://namespace/contract/operation" />|  
|Endpointaddress|Używa <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> klasy, z <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` dopasowywania wiadomości zawierających określony adres.|Adres do filtrowania (w nagłówku Do).|\<nazwa filtra="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />|  
|Poprawka do adresów końcowych|Używa <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> klasy, z <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` dopasowywania wiadomości zawierających prefiks określonego adresu.|Adres do filtrowania przy użyciu najdłuższego dopasowania prefiksu.|\<nazwa filtra="prefiks1" filterType="EndpointAddressPrefix"http://host/filterData=" " />|  
|And|Używa <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> klasy, która zawsze ocenia oba warunki przed zwróceniem.|filterData nie jest używany; zamiast filter1 i filter2 mają nazwy odpowiednich filtrów wiadomości (również w tabeli), które powinny być **i**ed razem.|\<nazwa filtra="and1" filterType="And" filter1="address1" filter2="action1" />|  
|Niestandardowy|Typ zdefiniowany przez użytkownika, <xref:System.ServiceModel.Dispatcher.MessageFilter> który rozszerza klasę i ma konstruktora biorący ciąg.|Atrybut customType jest w pełni kwalifikowaną nazwą typu klasy do utworzenia; filterData jest ciągiem, który należy przekazać konstruktorowi podczas tworzenia filtru.|\<nazwa filtra="custom1" filterType="Custom" customType="CustomAssembly.CustomMsgFilter, CustomAssembly" filterData="Dane niestandardowe" />|  
|Nazwa punktu końcowego|Używa klasy, <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> aby dopasować komunikaty na podstawie nazwy punktu końcowego usługi, na których dotarli.|Nazwa punktu końcowego usługi, na przykład: "serviceEndpoint1".  Powinien to być jeden z punktów końcowych ujawnionych w usłudze routingu.|\<nazwa filtra="stock1" filterType="Endpoint" filterData="SvcEndpoint" />|  
|MatchAll|Używa <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> klasy. Ten filtr jest zgodny ze wszystkimi przychodzącymi wiadomościami.|filterData nie jest używany. Ten filtr będzie zawsze pasować do wszystkich wiadomości.|\<nazwa filtra="matchAll1" filterType="MatchAll" />|  
|XPath|Używa klasy, <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> aby dopasować określone zapytania XPath w wiadomości.|XPath kwerendy do użycia podczas dopasowywania wiadomości.|\<nazwa filtra="XPath1" filterType="XPath" filterData="/ns:element" />|  
  
 Poniższy przykład definiuje wpisy filtru, które używają filtrów wiadomości XPath, EndpointName i PrefixEndpointAddress. W tym przykładzie pokazano również przy użyciu filtru niestandardowego dla wpisów RoundRobinFilter1 i RoundRobinFilter2.  
  
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
> Samo zdefiniowanie filtru nie powoduje, że wiadomości mają być oceniane względem filtru. Filtr musi zostać dodany do tabeli filtrów, która jest następnie skojarzona z punktem końcowym usługi udostępniane przez usługę routingu.  
  
### <a name="namespace-table"></a>Tabela obszaru nazw  
 Podczas korzystania z filtru XPath, dane filtru, który zawiera kwerendę XPath może stać się bardzo duże ze względu na użycie obszarów nazw. Aby złagodzić ten problem, usługa routingu umożliwia zdefiniowanie własnych prefiksów obszaru nazw przy użyciu tabeli obszaru nazw.  
  
 Tabela obszaru nazw jest <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> zbiorem obiektów, które definiują prefiksy obszaru nazw dla wspólnych obszarów nazw, które mogą być używane w XPath. Poniżej przedstawiono domyślne przestrzenie nazw i prefiksy obszaru nazw zawarte w tabeli obszaru nazw.  
  
|Prefiks|Przestrzeń nazw|  
|------------|---------------|  
|s11|`http://schemas.xmlsoap.org/soap/envelope`|  
|s12|`http://www.w3.org/2003/05/soap-envelope`|  
|wsa Sierpnia2004|`http://schemas.xmlsoap.org/ws/2004/08/addressing`|  
|wsa10|`http://www.w3.org/2005/08/addressing`|  
|sm|`http://schemas.microsoft.com/serviceModel/2004/05/xpathfunctions`|  
|tempuri ( tempuri )|`http://tempuri.org`|  
|ser (ser)|`http://schemas.microsoft.com/2003/10/Serialization`|  
  
 Gdy wiadomo, że będzie używany określony obszar nazw w kwerendach XPath, można dodać go do tabeli obszaru nazw wraz z unikatowym prefiksem obszaru nazw i użyć prefiksu w dowolnej kwerendzie XPath zamiast pełnego obszaru nazw. Poniższy przykład definiuje prefiks "niestandardowy" `"http://my.custom.namespace"`dla obszaru nazw , który jest następnie używany w kwerendzie XPath zawarte w filterData.  
  
```xml  
<namespaceTable>  
     <add prefix="custom" namespace="http://my.custom.namespace/"/>  
</namespaceTable>  
<filters>  
     <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
</filters>  
```  
  
## <a name="filter-tables"></a>Tabele filtrów  
 Podczas gdy każdy element filtru definiuje logiczne porównanie, które można zastosować do wiadomości, tabela filtrów zapewnia skojarzenie między elementem filtru a docelowym punktem końcowym klienta docelowego. Tabela filtrów <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> to nazwana kolekcja obiektów, które definiują skojarzenie między filtrem, podstawowym docelowym punktem końcowym i listą alternatywnych punktów końcowych kopii zapasowej. Wpisy tabeli filtrów umożliwiają również określenie opcjonalnego priorytetu dla każdego warunku filtru. Poniższy przykład definiuje dwa filtry, a następnie definiuje tabelę filtrów, która kojarzy każdy filtr z docelowym punktem końcowym.  
  
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
 Domyślnie wszystkie wpisy w tabeli filtrów są oceniane jednocześnie, a oceniana wiadomość jest kierowana do punktu końcowego skojarzonego z każdym pasującym wpisem filtru. Jeśli wiele filtrów `true`ocenić do , a wiadomość jest jednokierunkowa lub dupleks, wiadomość jest multiemisji do punktów końcowych dla wszystkich pasujących filtrów. Wiadomości żądania odpowiedzi nie mogą być multiemisji, ponieważ tylko jedna odpowiedź może być zwrócona do klienta.  
  
 Bardziej złożoną logikę routingu można zaimplementować, określając poziomy priorytetów dla każdego filtru; Usługa routingu najpierw ocenia wszystkie filtry na najwyższym poziomie priorytetu. Jeśli wiadomość pasuje do filtru tego poziomu, nie są przetwarzane filtry o niższym priorytecie. Na przykład przychodząca wiadomość jednokierunkowa jest najpierw oceniana dla wszystkich filtrów o priorytecie 2. Wiadomość nie pasuje do żadnego filtru na tym poziomie priorytetu, więc dalej wiadomość jest porównywana z filtrami o priorytecie 1. Dwa filtry priorytetu 1 są zgodne z wiadomością, a ponieważ jest to komunikat jednokierunkowy, jest on kierowany do obu docelowych punktów końcowych.  Ponieważ znaleziono dopasowanie wśród filtrów priorytetu 1, nie są oceniane filtry o priorytecie 0.  
  
> [!NOTE]
> Jeśli nie określono priorytetu, używany jest domyślny priorytet 0.  
  
 Poniższy przykład definiuje tabelę filtrów, która określa priorytety 2, 1 i 0 dla filtrów, do których odwołuje się tabela.  
  
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
  
 W poprzednim przykładzie, jeśli komunikat pasuje do XPathFilter, zostanie on skierowany do zaokrągleniaCalcEndpoint i nie dalsze filtry w tabeli będą oceniane, ponieważ wszystkie inne filtry mają niższy priorytet. Jeśli jednak komunikat nie jest zgodny z filtrem XPathFilter, zostanie on oceniony względem wszystkich filtrów następnego niższego priorytetu, EndpointNameFilter i PrefixAddressFilter.  
  
> [!NOTE]
> Jeśli to możliwe, należy użyć wyłącznych filtrów zamiast określania priorytetu, ponieważ ocena priorytetu może spowodować spadek wydajności.  
  
### <a name="backup-lists"></a>Listy kopii zapasowych  
 Każdy filtr w tabeli filtrów może opcjonalnie określić listę kopii<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>zapasowych, która jest nazwaną kolekcją punktów końcowych ( ). Ta kolekcja zawiera uporządkowaną listę punktów końcowych, do których wiadomość zostanie <xref:System.ServiceModel.CommunicationException> przekazana w przypadku wysłania <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A>do podstawowego punktu końcowego określonego w programie . Poniższy przykład definiuje listę kopii zapasowych o nazwie "backupServiceEndpoints", która zawiera dwa punkty końcowe.  
  
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
  
 W poprzednim przykładzie, jeśli wysłanie do podstawowego punktu końcowego "Miejsce docelowe" zakończy się niepowodzeniem, usługa routingu spróbuje wysłać do każdego punktu końcowego w kolejności, w jakiej są wyświetlane, najpierw wysyłając do backupServiceQueue, a następnie wysyłając do alternateServiceQueue, jeśli send do backupServiceQueue kończy się niepowodzeniem. Jeśli wszystkie punkty końcowe kopii zapasowej nie powiedzie się, zwracany jest błąd.
