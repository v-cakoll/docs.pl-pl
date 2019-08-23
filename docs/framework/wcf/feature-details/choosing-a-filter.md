---
title: Wybieranie filtra
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: 73901ff312722605cceff2a0448511b0055fc120
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935023"
---
# <a name="choosing-a-filter"></a>Wybieranie filtra
Podczas konfigurowania usługi routingu ważne jest, aby wybrać poprawne filtry komunikatów i skonfigurować je w taki sposób, aby umożliwiały dokładne dopasowanie do odbieranych komunikatów. Jeśli wybrane filtry są zbyt szerokie w dopasowaniach lub są nieprawidłowo skonfigurowane, komunikaty są kierowane nieprawidłowo. Jeśli filtry są zbyt restrykcyjne, może nie mieć dostępnych prawidłowych tras dla niektórych komunikatów.  
  
## <a name="filter-types"></a>Typy filtrów  
 Podczas wybierania filtrów, które są używane przez usługę routingu, ważne jest, aby zrozumieć, jak działa każdy filtr, a także jakie informacje są dostępne w ramach komunikatów przychodzących. Na przykład, jeśli wszystkie komunikaty są odbierane w tym samym punkcie końcowym, filtry adresu i punktu końcowego nie są przydatne, ponieważ wszystkie komunikaty pasują do tych filtrów.  
  
### <a name="action"></a>Akcja  
 Filtr akcji sprawdza <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> właściwość. Jeśli zawartość nagłówka akcji w komunikacie jest zgodna z wartością Filtruj dane określoną w konfiguracji filtru, ten filtr zwraca wartość `true`. W poniższym przykładzie zdefiniowano `FilterElement` , który używa filtru akcji, aby dopasować komunikaty z nagłówkiem akcji, który zawiera `http://namespace/contract/operation/`wartość.
  
```xml  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />  
```  
  
```csharp  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
```  
  
 Ten filtr powinien być używany podczas routingu komunikatów, które zawierają unikatowy nagłówek akcji.  
  
### <a name="endpointaddress"></a>Elemencie  
 Filtr EndpointAddress sprawdza wartość elementu EndpointAddress, w którym wiadomość została odebrana. Jeśli adres odebrany przez komunikat dokładnie pasuje do adresu filtru określonego w konfiguracji filtru, ten filtr zwraca wartość `true`. W poniższym przykładzie zdefiniowano `FilterElement` , który używa filtru adresów w celu dopasowania wszelkich komunikatów skierowanych do\<"http://hostname >/vdir/s.svc/b".  
  
```xml  
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
> Należy pamiętać, że nazwa hosta część adresu może się różnić w zależności od tego, czy klient korzysta z w pełni kwalifikowanej nazwy domeny, nazwy NetBIOS, adresu IP czy innej nazwy. Ponieważ różne wartości mogą odwoływać się do tego samego hosta, zachowanie domyślne dla tego porównania ma nie używać części nazwy hosta w przypadku wykonywania dopasowań.  
>   
>  Takie zachowanie można zmodyfikować tak, aby umożliwić porównanie do oszacowania nazwy hosta podczas programistycznego konfigurowania usługi routingu.  
  
 Ten filtr powinien być używany, gdy wiadomości przychodzące są rozkierowane na unikatowy adres.  
  
### <a name="endpointaddressprefix"></a>EndpointAddressPrefix  
 Filtr EndpointAddressPrefix jest podobny do filtru EndpointAddress. Filtr EndpointAddressPrefix sprawdza wartość EndpointAddress, w której wiadomość została odebrana. Jednak filtr EndpointAddressPrefix działa jako symbol wieloznaczny przez dopasowanie adresów zaczynających się od wartości określonej w konfiguracji filtru. W poniższym przykładzie zdefiniowano `FilterElement` , który używa filtru EndpointAddressPrefix do dopasowania wszelkich komunikatów skierowanych `http://<hostname>/vdir*`do.  
  
```xml  
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />  
```  
  
```csharp  
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
> Należy pamiętać, że nazwa hosta część adresu może się różnić w zależności od tego, czy klient korzysta z w pełni kwalifikowanej nazwy domeny, nazwy NetBIOS, adresu IP czy innej nazwy. Ponieważ różne wartości mogą odwoływać się do tego samego hosta, zachowanie domyślne dla tego porównania ma nie używać części nazwy hosta w przypadku wykonywania dopasowań.  
  
 Ten filtr powinien być używany podczas routingu przychodzących komunikatów, które współużytkują wspólny prefiks adresu.  
  
### <a name="and"></a>AND  
 Filtr i nie bezpośrednio filtruje wartość w komunikacie, ale umożliwia połączenie dwóch innych filtrów w celu utworzenia `AND` warunku, w którym oba filtry muszą być zgodne z komunikatem, zanim filtr i zwróci wartość. `true` Dzięki temu można tworzyć złożone filtry, które pasują tylko wtedy, gdy wszystkie filtry podrzędne pasują do siebie. Poniższy przykład definiuje filtr adresów i filtr akcji, a następnie definiuje filtr i, który szacuje komunikat w odniesieniu do filtrów adresu i akcji. Jeśli adres i filtry akcji pasują do siebie, filtr i zwraca wartość `true`.  
  
```xml  
<filter name="address1" filterType="AddressPrefix" filterData="http://host/vdir"/>  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/"/>  
<filter name="and1" filterType="And" filter1="address1" filter2="action1" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
StrictAndMessageFilter and1=new StrictAndMessageFilter(address1, action1);  
```  
  
 Ten filtr powinien być używany, gdy konieczne jest połączenie logiki z wielu filtrów, aby określić, kiedy należy wykonać dopasowanie. Na przykład jeśli masz wiele miejsc docelowych, które muszą odbierać tylko niektóre kombinacje akcji i komunikatów do określonych adresów, możesz użyć filtru i, aby połączyć wymagane filtry akcji i adresów.  
  
### <a name="custom"></a>Celnej  
 Wybierając typ filtru niestandardowego, należy podać wartość CustomType, która zawiera typ zestawu, który zawiera implementację **MessageFilter** , która ma być używana dla tego filtru. Ponadto danych filtru musi zawierać wszystkie wartości, które mogą być wymagane przez filtr niestandardowy w ocenie komunikatów. W poniższym przykładzie zdefiniowano `FilterElement` , który `CustomAssembly.MyCustomMsgFilter` używa implementacji MessageFilter.  
  
```xml  
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />  
```  
  
```csharp  
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");  
```  
  
 Jeśli musisz wykonać niestandardową logikę dopasowywania względem komunikatu, który nie jest objęty przez filtry [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]dostarczone z, musisz utworzyć filtr niestandardowy, który jest implementacją klasy **MessageFilter** . Można na przykład utworzyć filtr niestandardowy, który porównuje pole w komunikacie przychodzącym z listą znanych wartości przyznanych filtrowi jako konfigurację lub które miesza określony element komunikatu, a następnie sprawdza tę wartość, aby określić, czy filtr powinna zwracać `true` lub `false`.  
  
### <a name="endpointname"></a>EndpointName  
 Filtr EndpointName sprawdza nazwę punktu końcowego, który odebrał komunikat. W poniższym przykładzie zdefiniowano `FilterElement` , który używa filtru EndpointName do przesyłania komunikatów odebranych w "SvcEndpoint".  
  
```xml  
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />  
```  
  
```csharp  
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");  
```  
  
 Ten filtr jest przydatny, gdy usługa routingu ujawnia więcej niż jeden nazwany punkt końcowy usługi. Można na przykład uwidocznić dwa punkty końcowe używane przez usługę routingu do odbierania komunikatów. jeden z nich jest używany przez klientów priorytetowych, którzy wymagają przetwarzania komunikatów w czasie rzeczywistym, podczas gdy drugi punkt końcowy otrzymuje komunikaty, które nie są zależne od czasu.  
  
 Mimo że w celu określenia punktu końcowego, w którym wiadomość została odebrana, używana jest pełna nazwa punktu końcowego, jest to wygodny skrót, który jest często mniej podatny na błędy, szczególnie w przypadku konfigurowania usługi routingu przy użyciu konfiguracji plik (gdzie nazwy punktów końcowych są wymaganym atrybutem).  
  
### <a name="matchall"></a>MatchAll  
 Filtr MatchAll jest zgodny z odebranymi komunikatami. Jest to przydatne, jeśli konieczne jest zawsze kierowanie wszystkich odebranych komunikatów do określonego punktu końcowego, takich jak usługa rejestrowania przechowująca kopię wszystkich odebranych komunikatów. W poniższym przykładzie zdefiniowano `FilterElement` , który używa filtru MatchAll.  
  
```xml  
<filter name="matchAll1" filterType="MatchAll" />  
```  
  
```csharp  
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();  
```  
  
### <a name="xpath"></a>XPath  
 Filtr XPath umożliwia określenie zapytania XPath, które jest używane do inspekcji określonego elementu w komunikacie. Filtrowanie XPath to zaawansowana opcja filtrowania, która umożliwia bezpośrednie sprawdzenie dowolnego wpisu z adresami XML w wiadomości. jednak wymaga to konkretnej znajomości struktury otrzymywanych komunikatów. W poniższym przykładzie zdefiniowano `FilterElement` , który używa filtru XPath do sprawdzenia komunikatu dla elementu o nazwie "element" w przestrzeni nazw, do którego odwołuje się prefiks przestrzeni nazw "NS".  
  
```xml  
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />  
```  
  
```csharp  
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");  
```  
  
 Ten filtr jest przydatny, Jeśli wiesz, że odebrane komunikaty zawierają konkretną wartość. Na przykład, Jeśli przechowujesz dwie wersje tej samej usługi i wiesz, że komunikaty rozkierowane do nowszej wersji usługi zawierają unikatową wartość w niestandardowym nagłówku, możesz utworzyć filtr, który używa XPath, aby przejść do tego nagłówka i porównać wartość zaliczkową. w nagłówku do innego podanego w konfiguracji filtru, aby określić, czy filtr jest zgodny.  
  
 Ponieważ zapytania XPath często zawierają unikatowe przestrzenie nazw, które często mają długość lub złożone wartości ciągu, filtr XPath umożliwia użycie tabeli przestrzeni nazw w celu zdefiniowania unikatowych prefiksów przestrzeni nazw. Aby uzyskać więcej informacji na temat tabeli przestrzeni nazw, zobacz [filtry komunikatów](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
 Aby uzyskać więcej informacji na temat projektowania zapytań XPath, zobacz [składnia XPath](https://go.microsoft.com/fwlink/?LinkId=164592).  
  
## <a name="see-also"></a>Zobacz także

- [Filtry komunikatów](../../../../docs/framework/wcf/feature-details/message-filters.md)
- [Instrukcje: Używanie filtrów](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
