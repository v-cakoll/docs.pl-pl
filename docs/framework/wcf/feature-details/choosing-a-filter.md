---
title: Wybieranie filtra
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 973a70fdb655ab069d6ecdafd0e017324720e57a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="choosing-a-filter"></a>Wybieranie filtra
Podczas konfigurowania usługi routingu, należy wybrać filtry komunikatów i skonfigurować je do pozwalają zapewnić dokładne dopasowania przed wiadomości, które otrzymujesz. Jeśli wybrane filtry są zbyt szerokie w ich odpowiedniki lub są niepoprawnie skonfigurowane, komunikaty są kierowane niepoprawnie. Jeśli filtry są zbyt restrykcyjne, nie masz żadnych prawidłowy trasy dostępne dla niektórych wiadomości.  
  
## <a name="filter-types"></a>Typy filtrów  
 Wybierając filtry, które są używane przez usługi routingu, jest ważne, że rozumiesz sposób działania każdego filtru oraz jakie informacje są dostępne jako część wiadomości przychodzących. Na przykład jeśli wszystkie komunikaty są otrzymywane za pośrednictwem tego samego punktu końcowego, filtry adresów i EndpointName nie są przydatne ponieważ wszystkie komunikaty zgodne te filtry.  
  
### <a name="action"></a>Akcja  
 Filtr akcji sprawdza <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> właściwości. Jeśli zawartość nagłówka Action w komunikacie jest zgodna z wartością danych filtru określonego w konfiguracji filtru, a następnie zwraca ten filtr `true`. W poniższym przykładzie zdefiniowano `FilterElement` używającą filtr akcji do dopasowania wiadomości z nagłówkiem akcji, która zawiera wartość "http://namespace/contract/operation/".  
  
```xml  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />  
```  
  
```csharp  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
```  
  
 Można użyć tego filtru, gdy routing komunikatów, które zawierają unikatowy nagłówka Action.  
  
### <a name="endpointaddress"></a>EndpointAddress  
 Filtr EndpointAddress przeprowadzający EndpointAddress, odebranym komunikacie. Jeśli adres wiadomość dociera do dokładnie odpowiada adresowi filtru określonego w konfiguracji filtru, a następnie zwraca ten filtr `true`. W poniższym przykładzie zdefiniowano `FilterElement` używającą filtr adresów do dopasowania komunikaty adresowane do "http://\<nazwa_hosta > / vdir/s.svc/b".  
  
```xml  
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  Należy pamiętać, że część nazwy hosta adres może się różnić zależności od tego, czy klient używa w pełni kwalifikowaną nazwę domeny, nazwa NetBIOS, adres IP lub inną nazwę. Ponieważ różne wartości mogą odwoływać się do tego samego hosta, domyślne zachowanie to porównanie jest nie używane część nazwy hosta adres podczas wykonywania dopasowań.  
>   
>  To zachowanie można zmodyfikować w taki sposób, aby umożliwić porównania do oceny nazwy hosta podczas konfigurowania usługi routingu programowo.  
  
 Można użyć tego filtru, gdy wiadomości przychodzących są wysyłane na unikatowy adres.  
  
### <a name="endpointaddressprefix"></a>EndpointAddressPrefix  
 Filtr EndpointAddressPrefix jest podobne do filtrów EndpointAddress. Filtr EndpointAddressPrefix przeprowadzający EndpointAddress, odebranym komunikacie. Jednak filtr EndpointAddressPrefix działa jako symbolu wieloznacznego przez dopasowanie adresów, które zaczynają się od wartości określonej w konfiguracji filtru. W poniższym przykładzie zdefiniowano `FilterElement` EndpointAddressPrefix filtr który używa w celu dopasowania komunikaty adresowane do "http://\<nazwa_hosta > / vdir *".  
  
```xml  
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />  
```  
  
```csharp  
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  Należy pamiętać, że część nazwy hosta adres może się różnić zależności od tego, czy klient używa w pełni kwalifikowaną nazwę domeny, nazwa NetBIOS, adres IP lub inną nazwę. Ponieważ różne wartości mogą odwoływać się do tego samego hosta, domyślne zachowanie to porównanie jest nie używane część nazwy hosta adres podczas wykonywania dopasowań.  
  
 Można użyć tego filtru, gdy routing wiadomości przychodzących, które mają Wspólny prefiks adresu.  
  
### <a name="and"></a>AND  
 Filtr i nie można bezpośrednio filtrować według wartości w wiadomości, ale umożliwia łączenie dwa filtry do utworzenia `AND` warunek, w których oba filtry muszą być zgodne wiadomości przed filtru i daje w wyniku `true`. Dzięki temu można tworzyć złożone filtry zgodne tylko jeśli wszystkie filtry podrzędnego są zgodne. Poniższy przykład definiuje filtr adresów i filtr akcji, a następnie definiuje filtr i przetwarza wiadomość filtry adres i akcji. Jeśli zarówno adres i filtry akcji odpowiada, a następnie filtr i zwraca `true`.  
  
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
  
 Można użyć tego filtru, gdy należy połączyć logiki wielu filtrów, aby określić, kiedy powinno się dopasowania. Na przykład jeśli masz wiele miejsc docelowych, które muszą odbierać tylko niektórych kombinacji akcji i komunikatów do określonego adresów służy filtru i połączyć niezbędne filtry akcji i adresu.  
  
### <a name="custom"></a>Niestandardowe  
 Wybierając typ filtru niestandardowego, należy podać wartość customtype — zawierający typ zestawu, który zawiera **MessageFilter** wdrożenia do użycia dla tego filtru. Ponadto danych filtru musi zawierać wszystkie wartości, które filtr niestandardowy może wymagać w jej oceny wiadomości. W poniższym przykładzie zdefiniowano `FilterElement` używającą `CustomAssembly.MyCustomMsgFilter` MessageFilter implementacji.  
  
```xml  
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />  
```  
  
```csharp  
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");  
```  
  
 Jeśli zachodzi potrzeba wykonania niestandardowej logiki pasującego przed komunikat, który nie pasuje do żadnego filtry wyposażone [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], należy utworzyć niestandardowy filtr, który jest implementacją **MessageFilter** klasy. Na przykład można utworzyć niestandardowy filtr, który porównuje pola w komunikat przychodzący z listą znane wartości podanej w filtrze jako konfiguracja lub skróty elementu określonego komunikatu i następnie sprawdza tę wartość, aby określić, czy filtr należy zwrócić `true` lub `false`.  
  
### <a name="endpointname"></a>EndpointName  
 Filtr EndpointName sprawdza nazwę punktu końcowego, który odebrał wiadomość. W poniższym przykładzie zdefiniowano `FilterElement` używającą filtru EndpointName do wyznaczania tras wiadomościom odebranych na "SvcEndpoint".  
  
```xml  
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />  
```  
  
```csharp  
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");  
```  
  
 Ten filtr jest przydatne, gdy więcej niż jeden punkt końcowy usługi o nazwie udostępnia usługi routingu. Na przykład może narazić dwa punkty końcowe, które usługa routingu używana do odbierania wiadomości. jeden służy Priorytet klientów, którzy wymagają w czasie rzeczywistym, przetwarzanie wiadomości, podczas innych punktów końcowych odbiera komunikaty, które nie są czasu liter.  
  
 Często za pomocą pełnego adresu dopasowany do określenia punktu końcowego, których wiadomość została odebrana, zamiast nazwy określonych punktów końcowych jest wygodne skrótu klawiaturowego, który jest często mniej podatna, szczególnie w przypadku konfigurowania usługi routingu przy użyciu konfiguracji plik (gdzie nazw punktu końcowego są wymaganego atrybutu).  
  
### <a name="matchall"></a>MatchAll  
 Filtr MatchAll pasuje dowolnego odebranego komunikatu. Jest on przydatny, gdy wszystkie odebrane wiadomości musi zawsze kierować do określonego punktu końcowego, takie jak usługa rejestrowania, który przechowuje kopię wszystkich odbieranych komunikatach. W poniższym przykładzie zdefiniowano `FilterElement` używającą MatchAll filtru.  
  
```xml  
<filter name="matchAll1" filterType="MatchAll" />  
```  
  
```csharp  
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();  
```  
  
### <a name="xpath"></a>XPath  
 Filtr XPath umożliwia określenie Kwerenda XPath, która służy do sprawdzenia elementu określonego w komunikacie. Filtrowanie XPath jest zaawansowanych opcji filtrowania, która umożliwia bezpośrednio sprawdzić każdy wpis adresowanego XML w komunikacie; jednak wymaga posiadania określonych informacji na temat struktury wiadomości, które są odbierane. W poniższym przykładzie zdefiniowano `FilterElement` używającą filtr XPath do zbadania komunikatu dla elementu o nazwie "element" w przestrzeni nazw odwołuje się prefiks przestrzeni nazw "ns".  
  
```xml  
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />  
```  
  
```csharp  
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");  
```  
  
 Ten filtr jest przydatne, jeśli wiadomo, że wiadomości, które otrzymujesz zawiera określoną wartość. Na przykład jeśli wiadomo, że komunikaty adresowane do nowszej wersji usługi zawiera unikatową wartość niestandardowego nagłówka znajdują się dwie wersje tej samej usługi, należy utworzyć filtr, który używa języka XPath można przejść do tego nagłówka i porównuje prez wartość Enterprise w nagłówku do innego podane w konfiguracji filtru do określenia, czy pasuje do filtru.  
  
 Ponieważ kwerendy XPath często zawierają unikatowy przestrzeni nazw, które są często długie lub wartości ciągu złożonych, filtr XPath umożliwia użycie tabeli przestrzeni nazw do definiowania prefiksy unikatowy dla obszary nazw. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]w tabeli nazw, zobacz [filtry komunikatów](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Projektowanie kwerendy XPath, zobacz [składni języka XPath](http://go.microsoft.com/fwlink/?LinkId=164592).  
  
## <a name="see-also"></a>Zobacz też  
 [Filtry komunikatów](../../../../docs/framework/wcf/feature-details/message-filters.md)  
 [Porady: Używanie filtrów](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
