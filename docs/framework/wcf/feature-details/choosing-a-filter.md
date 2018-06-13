---
title: Wybieranie filtra
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: 91b3802217a920ef3eeeccb5c4f85c66afee2430
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494130"
---
# <a name="choosing-a-filter"></a><span data-ttu-id="458a3-102">Wybieranie filtra</span><span class="sxs-lookup"><span data-stu-id="458a3-102">Choosing a Filter</span></span>
<span data-ttu-id="458a3-103">Podczas konfigurowania usługi routingu, należy wybrać filtry komunikatów i skonfigurować je do pozwalają zapewnić dokładne dopasowania przed wiadomości, które otrzymujesz.</span><span class="sxs-lookup"><span data-stu-id="458a3-103">When configuring the Routing Service, it is important to select correct message filters and configure them to allow you to make exact matches against the messages you receive.</span></span> <span data-ttu-id="458a3-104">Jeśli wybrane filtry są zbyt szerokie w ich odpowiedniki lub są niepoprawnie skonfigurowane, komunikaty są kierowane niepoprawnie.</span><span class="sxs-lookup"><span data-stu-id="458a3-104">If the filters you select are overly broad in their matches or are incorrectly configured, messages are routed incorrectly.</span></span> <span data-ttu-id="458a3-105">Jeśli filtry są zbyt restrykcyjne, nie masz żadnych prawidłowy trasy dostępne dla niektórych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="458a3-105">If the filters are too restrictive, you may not have any valid routes available for some of your messages.</span></span>  
  
## <a name="filter-types"></a><span data-ttu-id="458a3-106">Typy filtrów</span><span class="sxs-lookup"><span data-stu-id="458a3-106">Filter Types</span></span>  
 <span data-ttu-id="458a3-107">Wybierając filtry, które są używane przez usługi routingu, jest ważne, że rozumiesz sposób działania każdego filtru oraz jakie informacje są dostępne jako część wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="458a3-107">When selecting the filters that are used by the Routing Service, it is important that you understand how each filter works as well as what information is available as part of the incoming messages.</span></span> <span data-ttu-id="458a3-108">Na przykład jeśli wszystkie komunikaty są otrzymywane za pośrednictwem tego samego punktu końcowego, filtry adresów i EndpointName nie są przydatne ponieważ wszystkie komunikaty zgodne te filtry.</span><span class="sxs-lookup"><span data-stu-id="458a3-108">For instance, if all messages are received over the same endpoint, the Address and EndpointName filters are not useful because all messages match these filters.</span></span>  
  
### <a name="action"></a><span data-ttu-id="458a3-109">Akcja</span><span class="sxs-lookup"><span data-stu-id="458a3-109">Action</span></span>  
 <span data-ttu-id="458a3-110">Filtr akcji sprawdza <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="458a3-110">The Action filter inspects the <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> property.</span></span> <span data-ttu-id="458a3-111">Jeśli zawartość nagłówka Action w komunikacie jest zgodna z wartością danych filtru określonego w konfiguracji filtru, a następnie zwraca ten filtr `true`.</span><span class="sxs-lookup"><span data-stu-id="458a3-111">If the contents of the Action header in the message match the filter data value specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="458a3-112">W poniższym przykładzie zdefiniowano `FilterElement` używającą filtr akcji do dopasowania wiadomości z nagłówkiem akcji, która zawiera wartość "http://namespace/contract/operation/".</span><span class="sxs-lookup"><span data-stu-id="458a3-112">The following example defines a `FilterElement` that uses the Action filter to match messages with an action header that contains a value of "http://namespace/contract/operation/".</span></span>  
  
```xml  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />  
```  
  
```csharp  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
```  
  
 <span data-ttu-id="458a3-113">Można użyć tego filtru, gdy routing komunikatów, które zawierają unikatowy nagłówka Action.</span><span class="sxs-lookup"><span data-stu-id="458a3-113">This filter should be used when routing messages that contain a unique Action header.</span></span>  
  
### <a name="endpointaddress"></a><span data-ttu-id="458a3-114">EndpointAddress</span><span class="sxs-lookup"><span data-stu-id="458a3-114">EndpointAddress</span></span>  
 <span data-ttu-id="458a3-115">Filtr EndpointAddress przeprowadzający EndpointAddress, odebranym komunikacie.</span><span class="sxs-lookup"><span data-stu-id="458a3-115">The EndpointAddress filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="458a3-116">Jeśli adres wiadomość dociera do dokładnie odpowiada adresowi filtru określonego w konfiguracji filtru, a następnie zwraca ten filtr `true`.</span><span class="sxs-lookup"><span data-stu-id="458a3-116">If the address that the message arrives at exactly matches the filter address specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="458a3-117">W poniższym przykładzie zdefiniowano `FilterElement` używającą filtr adresów do dopasowania komunikaty adresowane do "http://\<nazwa_hosta > / vdir/s.svc/b".</span><span class="sxs-lookup"><span data-stu-id="458a3-117">The following example defines a `FilterElement` that uses the Address filter to match any messages addressed to "http://\<hostname>/vdir/s.svc/b".</span></span>  
  
```xml  
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  <span data-ttu-id="458a3-118">Należy pamiętać, że część nazwy hosta adres może się różnić zależności od tego, czy klient używa w pełni kwalifikowaną nazwę domeny, nazwa NetBIOS, adres IP lub inną nazwę.</span><span class="sxs-lookup"><span data-stu-id="458a3-118">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="458a3-119">Ponieważ różne wartości mogą odwoływać się do tego samego hosta, domyślne zachowanie to porównanie jest nie używane część nazwy hosta adres podczas wykonywania dopasowań.</span><span class="sxs-lookup"><span data-stu-id="458a3-119">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>  
>   
>  <span data-ttu-id="458a3-120">To zachowanie można zmodyfikować w taki sposób, aby umożliwić porównania do oceny nazwy hosta podczas konfigurowania usługi routingu programowo.</span><span class="sxs-lookup"><span data-stu-id="458a3-120">This behavior can be modified to allow the comparison to evaluate the host name when configuring the Routing Service programmatically.</span></span>  
  
 <span data-ttu-id="458a3-121">Można użyć tego filtru, gdy wiadomości przychodzących są wysyłane na unikatowy adres.</span><span class="sxs-lookup"><span data-stu-id="458a3-121">This filter should be used when the incoming messages are addressed to a unique address.</span></span>  
  
### <a name="endpointaddressprefix"></a><span data-ttu-id="458a3-122">EndpointAddressPrefix</span><span class="sxs-lookup"><span data-stu-id="458a3-122">EndpointAddressPrefix</span></span>  
 <span data-ttu-id="458a3-123">Filtr EndpointAddressPrefix jest podobne do filtrów EndpointAddress.</span><span class="sxs-lookup"><span data-stu-id="458a3-123">The EndpointAddressPrefix filter is similar to the EndpointAddress filter.</span></span> <span data-ttu-id="458a3-124">Filtr EndpointAddressPrefix przeprowadzający EndpointAddress, odebranym komunikacie.</span><span class="sxs-lookup"><span data-stu-id="458a3-124">The EndpointAddressPrefix filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="458a3-125">Jednak filtr EndpointAddressPrefix działa jako symbolu wieloznacznego przez dopasowanie adresów, które zaczynają się od wartości określonej w konfiguracji filtru.</span><span class="sxs-lookup"><span data-stu-id="458a3-125">However the EndpointAddressPrefix filter acts as a wildcard by matching addresses that begin with the value specified in the filter configuration.</span></span> <span data-ttu-id="458a3-126">W poniższym przykładzie zdefiniowano `FilterElement` EndpointAddressPrefix filtr który używa w celu dopasowania komunikaty adresowane do "http://\<nazwa_hosta > / vdir \*".</span><span class="sxs-lookup"><span data-stu-id="458a3-126">The following example defines a `FilterElement` that uses the EndpointAddressPrefix filter to match any messages addressed to "http://\<hostname>/vdir\*".</span></span>  
  
```xml  
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />  
```  
  
```csharp  
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  <span data-ttu-id="458a3-127">Należy pamiętać, że część nazwy hosta adres może się różnić zależności od tego, czy klient używa w pełni kwalifikowaną nazwę domeny, nazwa NetBIOS, adres IP lub inną nazwę.</span><span class="sxs-lookup"><span data-stu-id="458a3-127">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="458a3-128">Ponieważ różne wartości mogą odwoływać się do tego samego hosta, domyślne zachowanie to porównanie jest nie używane część nazwy hosta adres podczas wykonywania dopasowań.</span><span class="sxs-lookup"><span data-stu-id="458a3-128">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>  
  
 <span data-ttu-id="458a3-129">Można użyć tego filtru, gdy routing wiadomości przychodzących, które mają Wspólny prefiks adresu.</span><span class="sxs-lookup"><span data-stu-id="458a3-129">This filter should be used when routing incoming messages that share a common address prefix.</span></span>  
  
### <a name="and"></a><span data-ttu-id="458a3-130">AND</span><span class="sxs-lookup"><span data-stu-id="458a3-130">AND</span></span>  
 <span data-ttu-id="458a3-131">Filtr i nie można bezpośrednio filtrować według wartości w wiadomości, ale umożliwia łączenie dwa filtry do utworzenia `AND` warunek, w których oba filtry muszą być zgodne wiadomości przed filtru i daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="458a3-131">The AND filter does not directly filter on a value within a message, but allows you to combine two other filters to create an `AND` condition where both filters must match the message before the AND filter evaluates to `true`.</span></span> <span data-ttu-id="458a3-132">Dzięki temu można tworzyć złożone filtry zgodne tylko jeśli wszystkie filtry podrzędnego są zgodne.</span><span class="sxs-lookup"><span data-stu-id="458a3-132">This allows you to create complex filters that only match if all the sub-filters match.</span></span> <span data-ttu-id="458a3-133">Poniższy przykład definiuje filtr adresów i filtr akcji, a następnie definiuje filtr i przetwarza wiadomość filtry adres i akcji.</span><span class="sxs-lookup"><span data-stu-id="458a3-133">The following example defines an address filter and an action filter, and then defines an AND filter that evaluates a message against both the address and action filters.</span></span> <span data-ttu-id="458a3-134">Jeśli zarówno adres i filtry akcji odpowiada, a następnie filtr i zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="458a3-134">If both the address and the action filters match, then the AND filter returns `true`.</span></span>  
  
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
  
 <span data-ttu-id="458a3-135">Można użyć tego filtru, gdy należy połączyć logiki wielu filtrów, aby określić, kiedy powinno się dopasowania.</span><span class="sxs-lookup"><span data-stu-id="458a3-135">This filter should be used when you must combine the logic from multiple filters to determine when a match should be made.</span></span> <span data-ttu-id="458a3-136">Na przykład jeśli masz wiele miejsc docelowych, które muszą odbierać tylko niektórych kombinacji akcji i komunikatów do określonego adresów służy filtru i połączyć niezbędne filtry akcji i adresu.</span><span class="sxs-lookup"><span data-stu-id="458a3-136">For example, if you have multiple destinations that must receive only certain combinations of actions and messages to particular addresses, you can use an AND filter to combine the necessary Action and Address filters.</span></span>  
  
### <a name="custom"></a><span data-ttu-id="458a3-137">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="458a3-137">Custom</span></span>  
 <span data-ttu-id="458a3-138">Wybierając typ filtru niestandardowego, należy podać wartość customtype — zawierający typ zestawu, który zawiera **MessageFilter** wdrożenia do użycia dla tego filtru.</span><span class="sxs-lookup"><span data-stu-id="458a3-138">When selecting the Custom filter type, you must provide a customType value that contains the type of the assembly that contains the **MessageFilter** implementation to be used for this filter.</span></span> <span data-ttu-id="458a3-139">Ponadto danych filtru musi zawierać wszystkie wartości, które filtr niestandardowy może wymagać w jej oceny wiadomości.</span><span class="sxs-lookup"><span data-stu-id="458a3-139">Additionally, filterData must contain any values that the custom filter may require in its evaluation of messages.</span></span> <span data-ttu-id="458a3-140">W poniższym przykładzie zdefiniowano `FilterElement` używającą `CustomAssembly.MyCustomMsgFilter` MessageFilter implementacji.</span><span class="sxs-lookup"><span data-stu-id="458a3-140">The following example defines a `FilterElement` that uses the `CustomAssembly.MyCustomMsgFilter` MessageFilter implementation.</span></span>  
  
```xml  
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />  
```  
  
```csharp  
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");  
```  
  
 <span data-ttu-id="458a3-141">Jeśli zachodzi potrzeba wykonania niestandardowej logiki pasującego przed komunikat, który nie pasuje do żadnego filtry wyposażone [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], należy utworzyć niestandardowy filtr, który jest implementacją **MessageFilter** klasy.</span><span class="sxs-lookup"><span data-stu-id="458a3-141">If you need to perform custom matching logic against a message that is not covered by the filters provided with [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], you must create a custom filter that is an implementation of the **MessageFilter** class.</span></span> <span data-ttu-id="458a3-142">Na przykład można utworzyć niestandardowy filtr, który porównuje pola w komunikat przychodzący z listą znane wartości podanej w filtrze jako konfiguracja lub skróty elementu określonego komunikatu i następnie sprawdza tę wartość, aby określić, czy filtr należy zwrócić `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="458a3-142">For example, you might create a custom filter that compares a field in the incoming message against a list of known values given to the filter as configuration, or that hashes a particular message element and then examines that value to determine whether the filter should return `true` or `false`.</span></span>  
  
### <a name="endpointname"></a><span data-ttu-id="458a3-143">EndpointName</span><span class="sxs-lookup"><span data-stu-id="458a3-143">EndpointName</span></span>  
 <span data-ttu-id="458a3-144">Filtr EndpointName sprawdza nazwę punktu końcowego, który odebrał wiadomość.</span><span class="sxs-lookup"><span data-stu-id="458a3-144">The EndpointName filter inspects the name of the endpoint that received the message.</span></span> <span data-ttu-id="458a3-145">W poniższym przykładzie zdefiniowano `FilterElement` używającą filtru EndpointName do wyznaczania tras wiadomościom odebranych na "SvcEndpoint".</span><span class="sxs-lookup"><span data-stu-id="458a3-145">The following example defines a `FilterElement` that uses the EndpointName filter to route messages received on the "SvcEndpoint".</span></span>  
  
```xml  
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />  
```  
  
```csharp  
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");  
```  
  
 <span data-ttu-id="458a3-146">Ten filtr jest przydatne, gdy więcej niż jeden punkt końcowy usługi o nazwie udostępnia usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="458a3-146">This filter is useful when the Routing Service exposes more than one named service endpoint.</span></span> <span data-ttu-id="458a3-147">Na przykład może narazić dwa punkty końcowe, które usługa routingu używana do odbierania wiadomości. jeden służy Priorytet klientów, którzy wymagają w czasie rzeczywistym, przetwarzanie wiadomości, podczas innych punktów końcowych odbiera komunikaty, które nie są czasu liter.</span><span class="sxs-lookup"><span data-stu-id="458a3-147">For example, you might expose two endpoints that the Routing Service uses to receive messages; one is used by priority customers who require real-time processing of their messages, while the other endpoint receives messages that are not time sensitive.</span></span>  
  
 <span data-ttu-id="458a3-148">Często za pomocą pełnego adresu dopasowany do określenia punktu końcowego, których wiadomość została odebrana, zamiast nazwy określonych punktów końcowych jest wygodne skrótu klawiaturowego, który jest często mniej podatna, szczególnie w przypadku konfigurowania usługi routingu przy użyciu konfiguracji plik (gdzie nazw punktu końcowego są wymaganego atrybutu).</span><span class="sxs-lookup"><span data-stu-id="458a3-148">While you can often use full address matching to determine which endpoint a message was received on, using the defined endpoint name instead is a convenient shortcut that is often less error prone, especially when configuring a Routing Service using a configuration file (where endpoint names are a required attribute).</span></span>  
  
### <a name="matchall"></a><span data-ttu-id="458a3-149">MatchAll</span><span class="sxs-lookup"><span data-stu-id="458a3-149">MatchAll</span></span>  
 <span data-ttu-id="458a3-150">Filtr MatchAll pasuje dowolnego odebranego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="458a3-150">The MatchAll filter matches any received message.</span></span> <span data-ttu-id="458a3-151">Jest on przydatny, gdy wszystkie odebrane wiadomości musi zawsze kierować do określonego punktu końcowego, takie jak usługa rejestrowania, który przechowuje kopię wszystkich odbieranych komunikatach.</span><span class="sxs-lookup"><span data-stu-id="458a3-151">It is useful if you must always route all received messages to a specific endpoint, such as a logging service that stores a copy of all received messages.</span></span> <span data-ttu-id="458a3-152">W poniższym przykładzie zdefiniowano `FilterElement` używającą MatchAll filtru.</span><span class="sxs-lookup"><span data-stu-id="458a3-152">The following example defines a `FilterElement` that uses the MatchAll filter.</span></span>  
  
```xml  
<filter name="matchAll1" filterType="MatchAll" />  
```  
  
```csharp  
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();  
```  
  
### <a name="xpath"></a><span data-ttu-id="458a3-153">XPath</span><span class="sxs-lookup"><span data-stu-id="458a3-153">XPath</span></span>  
 <span data-ttu-id="458a3-154">Filtr XPath umożliwia określenie Kwerenda XPath, która służy do sprawdzenia elementu określonego w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="458a3-154">The XPath filter allows you to specify an XPath query that is used to inspect a specific element within the message.</span></span> <span data-ttu-id="458a3-155">Filtrowanie XPath jest zaawansowanych opcji filtrowania, która umożliwia bezpośrednio sprawdzić każdy wpis adresowanego XML w komunikacie; jednak wymaga posiadania określonych informacji na temat struktury wiadomości, które są odbierane.</span><span class="sxs-lookup"><span data-stu-id="458a3-155">XPath filtering is a powerful filtering option that allows you to directly inspect any XML addressable entry within the message; however it requires that you have specific knowledge of the structure of the messages that you are receiving.</span></span> <span data-ttu-id="458a3-156">W poniższym przykładzie zdefiniowano `FilterElement` używającą filtr XPath do zbadania komunikatu dla elementu o nazwie "element" w przestrzeni nazw odwołuje się prefiks przestrzeni nazw "ns".</span><span class="sxs-lookup"><span data-stu-id="458a3-156">The following example defines a `FilterElement` that uses the XPath filter to inspect the message for an element named "element" within the namespace referenced by the "ns" namespace prefix.</span></span>  
  
```xml  
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />  
```  
  
```csharp  
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");  
```  
  
 <span data-ttu-id="458a3-157">Ten filtr jest przydatne, jeśli wiadomo, że wiadomości, które otrzymujesz zawiera określoną wartość.</span><span class="sxs-lookup"><span data-stu-id="458a3-157">This filter is useful if you know that the messages you are receiving contain a specific value.</span></span> <span data-ttu-id="458a3-158">Na przykład jeśli wiadomo, że komunikaty adresowane do nowszej wersji usługi zawiera unikatową wartość niestandardowego nagłówka znajdują się dwie wersje tej samej usługi, należy utworzyć filtr, który używa języka XPath można przejść do tego nagłówka i porównuje prez wartość Enterprise w nagłówku do innego podane w konfiguracji filtru do określenia, czy pasuje do filtru.</span><span class="sxs-lookup"><span data-stu-id="458a3-158">For example, if you are hosting two versions of the same service and you know that messages addressed to the newer version of the service contain a unique value in a custom header, you can create a filter that uses XPath to navigate to this header and compares the value present in the header to another given in the filter configuration to determine if the filter matches.</span></span>  
  
 <span data-ttu-id="458a3-159">Ponieważ kwerendy XPath często zawierają unikatowy przestrzeni nazw, które są często długie lub wartości ciągu złożonych, filtr XPath umożliwia użycie tabeli przestrzeni nazw do definiowania prefiksy unikatowy dla obszary nazw.</span><span class="sxs-lookup"><span data-stu-id="458a3-159">Because XPath queries often contain unique namespaces, which are often lengthy or complex string values, the XPath filter allows you to use the namespace table to define unique prefixes for your namespaces.</span></span> <span data-ttu-id="458a3-160">Aby uzyskać więcej informacji o tabeli przestrzeni nazw, zobacz [filtry komunikatów](../../../../docs/framework/wcf/feature-details/message-filters.md).</span><span class="sxs-lookup"><span data-stu-id="458a3-160">For more information about the namespace table, see [Message Filters](../../../../docs/framework/wcf/feature-details/message-filters.md).</span></span>  
  
 <span data-ttu-id="458a3-161">Aby uzyskać więcej informacji na temat opracowywania kwerendy XPath, zobacz [składni języka XPath](http://go.microsoft.com/fwlink/?LinkId=164592).</span><span class="sxs-lookup"><span data-stu-id="458a3-161">For more information about designing XPath queries, see [XPath Syntax](http://go.microsoft.com/fwlink/?LinkId=164592).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="458a3-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="458a3-162">See Also</span></span>  
 [<span data-ttu-id="458a3-163">Filtry komunikatów</span><span class="sxs-lookup"><span data-stu-id="458a3-163">Message Filters</span></span>](../../../../docs/framework/wcf/feature-details/message-filters.md)  
 [<span data-ttu-id="458a3-164">Instrukcje: używanie filtrów</span><span class="sxs-lookup"><span data-stu-id="458a3-164">How To: Use Filters</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
