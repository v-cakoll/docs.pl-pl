---
title: Wybieranie filtra
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: 377d4f5c221ad37acf954b1dafc8712a388122ff
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196131"
---
# <a name="choosing-a-filter"></a>Wybieranie filtra
Podczas konfigurowania usługi routingu, należy wybrać filtry komunikatów i ich konfigurowania pod kątem umożliwiają dokładne dopasowania przed komunikatami, które otrzymujesz. Jeśli filtry, które możesz wybrać są zbyt szerokie w swoich dopasowań lub są niepoprawnie skonfigurowane, komunikaty są kierowane niepoprawnie. Jeśli filtry są zbyt restrykcyjne, możesz nie mieć dostępnych tras prawidłowy dla niektórych komunikatów.  
  
## <a name="filter-types"></a>Filtruj typy  
 Wybierając filtry, które są używane przez usługę routingu, to zrozumieć, jak działa każdy filtr oraz jakie informacje są dostępne jako część komunikatów przychodzących. Na przykład jeśli wszystkie komunikaty są odbierane za pośrednictwem tego samego punktu końcowego, filtry adresów i Nazwapunktukoncowego nie są przydatne ponieważ wszystkie wiadomości pasuje do tych filtrów.  
  
### <a name="action"></a>Akcja  
 Filtr akcji sprawdza <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> właściwości. Jeśli zawartość nagłówka akcji w wiadomości pasuje do filtru wartości danych, który jest określony w konfiguracji filtru, a następnie zwraca ten filtr `true`. W poniższym przykładzie zdefiniowano `FilterElement` , używa filtru akcji w celu dopasowania komunikatów za pomocą nagłówek akcji, która zawiera wartość `http://namespace/contract/operation/`.
  
```xml  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />  
```  
  
```csharp  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
```  
  
 Ten filtr powinien służyć routing komunikatów, które zawierają unikatowy nagłówek akcji.  
  
### <a name="endpointaddress"></a>EndpointAddress  
 Filtr EndpointAddress bada EndpointAddress, odebranym komunikacie. Jeśli adres, który komunikat dociera do dokładnie odpowiada filtru adresu określonego w konfiguracji filtru, a następnie zwraca ten filtr `true`. W poniższym przykładzie zdefiniowano `FilterElement` , używa filtru adresów w celu dopasowania wszelkie komunikaty adresowane do "http://\<nazwa hosta > / vdir/s.svc/b".  
  
```xml  
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  Należy zauważyć, że część nazwy hosta adresu mogą się różnić zależnie od tego, czy klient używa w pełni kwalifikowaną nazwę domeny, nazwa NetBIOS, adres IP lub innej nazwy. Ponieważ różne wartości mogą odwoływać się do tego samego hosta, domyślne zachowanie dla tego porównania jest nieużywanie część nazwy hosta adres podczas przeprowadzania dopasowań.  
>   
>  To zachowanie można zmodyfikować w taki sposób, aby zezwolić na porównania do wzięcia pod uwagę nazwy hosta podczas programowe Konfigurowanie usługi routingu.  
  
 Ten filtr powinien służyć komunikaty przychodzące są adresowane do unikatowy adres.  
  
### <a name="endpointaddressprefix"></a>EndpointAddressPrefix  
 Filtr EndpointAddressPrefix jest podobny do filtrowania EndpointAddress. Filtr EndpointAddressPrefix bada EndpointAddress, odebranym komunikacie. Jednak filtrów EndpointAddressPrefix działa jako symbolu wieloznacznego, dopasowując adresy, które zaczynają się od wartości określonej w konfiguracji filtru. W poniższym przykładzie zdefiniowano `FilterElement` EndpointAddressPrefix filtr który używa w celu dopasowania wszelkie komunikaty adresowane do `http://<hostname>/vdir*`.  
  
```xml  
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />  
```  
  
```csharp  
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  Należy zauważyć, że część nazwy hosta adresu mogą się różnić zależnie od tego, czy klient używa w pełni kwalifikowaną nazwę domeny, nazwa NetBIOS, adres IP lub innej nazwy. Ponieważ różne wartości mogą odwoływać się do tego samego hosta, domyślne zachowanie dla tego porównania jest nieużywanie część nazwy hosta adres podczas przeprowadzania dopasowań.  
  
 Ten filtr powinien służyć routing wiadomości przychodzących, które współużytkują Wspólny prefiks adresu.  
  
### <a name="and"></a>AND  
 Filtr i nie filtruje bezpośrednio na podstawie wartości w wiadomości, ale pozwala połączyć dwa filtry do utworzenia `AND` warunku, gdzie oba filtry muszą być zgodne komunikatu przed filtru i daje w wyniku `true`. Dzięki temu można tworzyć złożone filtry, które dopasowanie tylko wtedy, gdy wszystkie podrzędne filtry zgodne. Poniższy przykład definiuje filtry adresów i akcji, a następnie definiuje filtr i przetwarza wiadomość filtry adres i akcji. Jeśli zarówno adres, jak i filtry akcji są zgodne, a następnie filtr i zwraca `true`.  
  
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
  
 Ten filtr powinien służyć należy połączyć Logic Apps z wielu filtrów, aby określić, kiedy powinno się dopasowania. Na przykład w przypadku wielu miejsc docelowych, które muszą odbierać tylko niektóre kombinacje akcji i komunikaty do konkretnego adresów służy filtru i połączyć niezbędne filtry akcji i od adresów.  
  
### <a name="custom"></a>Niestandardowe  
 Podczas wybierania typu filtr niestandardowy, należy podać wartość customtype —, zawierający typ zestawu, który zawiera **MessageFilter** wdrożenia ma być używany dla tego filtru. Ponadto danych filtru musi zawierać dowolnych wartości, które filtr niestandardowy może wymagać jej oceny wiadomości. W poniższym przykładzie zdefiniowano `FilterElement` , który używa `CustomAssembly.MyCustomMsgFilter` MessageFilter implementacji.  
  
```xml  
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />  
```  
  
```csharp  
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");  
```  
  
 Jeśli zachodzi potrzeba wykonania niestandardowej logiki pasującego przed komunikatami, które nie jest objęta filtry dostarczane z [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], należy utworzyć filtr niestandardowy, który jest implementacją **MessageFilter** klasy. Na przykład utworzyć filtr niestandardowy, który porównuje pola w przychodzącej wiadomości z listą znane wartości do filtrowania konfiguracji lub wyznacza wartość skrótu elementu określoną wiadomość i następnie sprawdza, czy ta wartość, aby określić, czy filtr powinna zostać zwrócona `true` lub `false`.  
  
### <a name="endpointname"></a>EndpointName  
 Filtr Nazwapunktukoncowego sprawdza nazwę punktu końcowego, który otrzymał komunikat. W poniższym przykładzie zdefiniowano `FilterElement` używającej Nazwapunktukoncowego filtru w celu przesyłania wiadomości odebrane w "SvcEndpoint".  
  
```xml  
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />  
```  
  
```csharp  
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");  
```  
  
 Ten filtr jest przydatny, gdy usługa routingu udostępnia więcej niż jeden punkt końcowy usługi o nazwie. Na przykład można uwidocznić dwa punkty końcowe używane usługa routingu do odbierania wiadomości. jeden jest używany przez klientom priorytet, którzy potrzebują, przetwarzanie ich komunikatów, podczas inny punkt końcowy w czasie rzeczywistym odbiera komunikaty, które nie są czasu liter.  
  
 Często możesz użyć pełnego adresu dopasowania, aby ustalić którym punktem końcowym wiadomość została odebrana, zamiast wybranej nazwy punktu końcowego zdefiniowana jest wygodny skrót, który jest często mniej podatne, błąd, szczególnie w przypadku konfigurowania usługi routingu przy użyciu konfiguracji plik (gdzie nazwy punktów końcowych są wymaganego atrybutu).  
  
### <a name="matchall"></a>MatchAll  
 Filtr MatchAll pasuje do dowolnego odebranego komunikatu. Jest to przydatne, jeśli wszystkie odebrane wiadomości musi zawsze kierować do określonego punktu końcowego, takie jak usługa rejestrowania, która przechowuje kopię wszystkich odebranych komunikatów. W poniższym przykładzie zdefiniowano `FilterElement` korzystającą z filtrem MatchAll.  
  
```xml  
<filter name="matchAll1" filterType="MatchAll" />  
```  
  
```csharp  
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();  
```  
  
### <a name="xpath"></a>XPath  
 Filtr XPath można określić zapytanie XPath, używanej do inspekcji określonego elementu w wiadomości. Filtrowanie XPath jest zaawansowanych opcji filtrowania, która umożliwia inspekcję bezpośrednio żadnego wpisu adresowalnych XML wiadomości; jednak wymaga, że masz szczególnej wiedzy na temat struktury wiadomości, które są odbierane. W poniższym przykładzie zdefiniowano `FilterElement` używającą filtr XPath do wglądu do wiadomości dla elementu o nazwie "element" w przestrzeni nazw, odwołuje się prefiks przestrzeni nazw "ns".  
  
```xml  
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />  
```  
  
```csharp  
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");  
```  
  
 Ten filtr jest przydatny, jeśli wiesz, że wiadomości, które otrzymujesz zawiera określoną wartość. Na przykład jeśli są hostowane dwie wersje tej samej usłudze i dowiedzieć się, że komunikaty adresowane do nowszej wersji usługi zawiera unikatową wartość niestandardowego nagłówka, możesz utworzyć filtr, który używa XPath, aby przejść do tego pliku nagłówkowego i porównuje prez wartość ENT w nagłówku do innego podane w konfiguracji filtru, aby określić, jeśli filtr dopasowuje wartość.  
  
 Ponieważ kwerendy XPath często zawierają unikatowy przestrzeni nazw, które są często długi lub wartości ciągu złożonego, filtr XPath pozwala zdefiniować unikatowy prefiksów dla usługi przestrzenie nazw przy użyciu tabeli przestrzeni nazw. Aby uzyskać więcej informacji o tabeli przestrzeni nazw, zobacz [filtry komunikatów](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
 Aby uzyskać więcej informacji na temat projektowania zapytania XPath, zobacz [składni XPath](https://go.microsoft.com/fwlink/?LinkId=164592).  
  
## <a name="see-also"></a>Zobacz też  
 [Filtry komunikatów](../../../../docs/framework/wcf/feature-details/message-filters.md)  
 [Instrukcje: używanie filtrów](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
