---
title: Wybieranie filtra
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: f634363a3f8b69b38fd4d313c42de4d742d94acc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514196"
---
# <a name="choosing-a-filter"></a><span data-ttu-id="c7058-102">Wybieranie filtra</span><span class="sxs-lookup"><span data-stu-id="c7058-102">Choosing a Filter</span></span>
<span data-ttu-id="c7058-103">Podczas konfigurowania usługi routingu, należy wybrać filtry komunikatów i ich konfigurowania pod kątem umożliwiają dokładne dopasowania przed komunikatami, które otrzymujesz.</span><span class="sxs-lookup"><span data-stu-id="c7058-103">When configuring the Routing Service, it is important to select correct message filters and configure them to allow you to make exact matches against the messages you receive.</span></span> <span data-ttu-id="c7058-104">Jeśli filtry, które możesz wybrać są zbyt szerokie w swoich dopasowań lub są niepoprawnie skonfigurowane, komunikaty są kierowane niepoprawnie.</span><span class="sxs-lookup"><span data-stu-id="c7058-104">If the filters you select are overly broad in their matches or are incorrectly configured, messages are routed incorrectly.</span></span> <span data-ttu-id="c7058-105">Jeśli filtry są zbyt restrykcyjne, możesz nie mieć dostępnych tras prawidłowy dla niektórych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="c7058-105">If the filters are too restrictive, you may not have any valid routes available for some of your messages.</span></span>  
  
## <a name="filter-types"></a><span data-ttu-id="c7058-106">Filtruj typy</span><span class="sxs-lookup"><span data-stu-id="c7058-106">Filter Types</span></span>  
 <span data-ttu-id="c7058-107">Wybierając filtry, które są używane przez usługę routingu, to zrozumieć, jak działa każdy filtr oraz jakie informacje są dostępne jako część komunikatów przychodzących.</span><span class="sxs-lookup"><span data-stu-id="c7058-107">When selecting the filters that are used by the Routing Service, it is important that you understand how each filter works as well as what information is available as part of the incoming messages.</span></span> <span data-ttu-id="c7058-108">Na przykład jeśli wszystkie komunikaty są odbierane za pośrednictwem tego samego punktu końcowego, filtry adresów i Nazwapunktukoncowego nie są przydatne ponieważ wszystkie wiadomości pasuje do tych filtrów.</span><span class="sxs-lookup"><span data-stu-id="c7058-108">For instance, if all messages are received over the same endpoint, the Address and EndpointName filters are not useful because all messages match these filters.</span></span>  
  
### <a name="action"></a><span data-ttu-id="c7058-109">Akcja</span><span class="sxs-lookup"><span data-stu-id="c7058-109">Action</span></span>  
 <span data-ttu-id="c7058-110">Filtr akcji sprawdza <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c7058-110">The Action filter inspects the <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> property.</span></span> <span data-ttu-id="c7058-111">Jeśli zawartość nagłówka akcji w wiadomości pasuje do filtru wartości danych, który jest określony w konfiguracji filtru, a następnie zwraca ten filtr `true`.</span><span class="sxs-lookup"><span data-stu-id="c7058-111">If the contents of the Action header in the message match the filter data value specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="c7058-112">W poniższym przykładzie zdefiniowano `FilterElement` , używa filtru akcji w celu dopasowania komunikatów za pomocą nagłówek akcji, która zawiera wartość `http://namespace/contract/operation/`.</span><span class="sxs-lookup"><span data-stu-id="c7058-112">The following example defines a `FilterElement` that uses the Action filter to match messages with an action header that contains a value of `http://namespace/contract/operation/`.</span></span>
  
```xml  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />  
```  
  
```csharp  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
```  
  
 <span data-ttu-id="c7058-113">Ten filtr powinien służyć routing komunikatów, które zawierają unikatowy nagłówek akcji.</span><span class="sxs-lookup"><span data-stu-id="c7058-113">This filter should be used when routing messages that contain a unique Action header.</span></span>  
  
### <a name="endpointaddress"></a><span data-ttu-id="c7058-114">EndpointAddress</span><span class="sxs-lookup"><span data-stu-id="c7058-114">EndpointAddress</span></span>  
 <span data-ttu-id="c7058-115">Filtr EndpointAddress bada EndpointAddress, odebranym komunikacie.</span><span class="sxs-lookup"><span data-stu-id="c7058-115">The EndpointAddress filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="c7058-116">Jeśli adres, który komunikat dociera do dokładnie odpowiada filtru adresu określonego w konfiguracji filtru, a następnie zwraca ten filtr `true`.</span><span class="sxs-lookup"><span data-stu-id="c7058-116">If the address that the message arrives at exactly matches the filter address specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="c7058-117">W poniższym przykładzie zdefiniowano `FilterElement` , używa filtru adresów w celu dopasowania wszelkie komunikaty adresowane do "http://\<nazwa hosta > / vdir/s.svc/b".</span><span class="sxs-lookup"><span data-stu-id="c7058-117">The following example defines a `FilterElement` that uses the Address filter to match any messages addressed to "http://\<hostname>/vdir/s.svc/b".</span></span>  
  
```xml  
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  <span data-ttu-id="c7058-118">Należy zauważyć, że część nazwy hosta adresu mogą się różnić zależnie od tego, czy klient używa w pełni kwalifikowaną nazwę domeny, nazwa NetBIOS, adres IP lub innej nazwy.</span><span class="sxs-lookup"><span data-stu-id="c7058-118">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="c7058-119">Ponieważ różne wartości mogą odwoływać się do tego samego hosta, domyślne zachowanie dla tego porównania jest nieużywanie część nazwy hosta adres podczas przeprowadzania dopasowań.</span><span class="sxs-lookup"><span data-stu-id="c7058-119">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>  
>   
>  <span data-ttu-id="c7058-120">To zachowanie można zmodyfikować w taki sposób, aby zezwolić na porównania do wzięcia pod uwagę nazwy hosta podczas programowe Konfigurowanie usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="c7058-120">This behavior can be modified to allow the comparison to evaluate the host name when configuring the Routing Service programmatically.</span></span>  
  
 <span data-ttu-id="c7058-121">Ten filtr powinien służyć komunikaty przychodzące są adresowane do unikatowy adres.</span><span class="sxs-lookup"><span data-stu-id="c7058-121">This filter should be used when the incoming messages are addressed to a unique address.</span></span>  
  
### <a name="endpointaddressprefix"></a><span data-ttu-id="c7058-122">EndpointAddressPrefix</span><span class="sxs-lookup"><span data-stu-id="c7058-122">EndpointAddressPrefix</span></span>  
 <span data-ttu-id="c7058-123">Filtr EndpointAddressPrefix jest podobny do filtrowania EndpointAddress.</span><span class="sxs-lookup"><span data-stu-id="c7058-123">The EndpointAddressPrefix filter is similar to the EndpointAddress filter.</span></span> <span data-ttu-id="c7058-124">Filtr EndpointAddressPrefix bada EndpointAddress, odebranym komunikacie.</span><span class="sxs-lookup"><span data-stu-id="c7058-124">The EndpointAddressPrefix filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="c7058-125">Jednak filtrów EndpointAddressPrefix działa jako symbolu wieloznacznego, dopasowując adresy, które zaczynają się od wartości określonej w konfiguracji filtru.</span><span class="sxs-lookup"><span data-stu-id="c7058-125">However the EndpointAddressPrefix filter acts as a wildcard by matching addresses that begin with the value specified in the filter configuration.</span></span> <span data-ttu-id="c7058-126">W poniższym przykładzie zdefiniowano `FilterElement` EndpointAddressPrefix filtr który używa w celu dopasowania wszelkie komunikaty adresowane do `http://<hostname>/vdir*`.</span><span class="sxs-lookup"><span data-stu-id="c7058-126">The following example defines a `FilterElement` that uses the EndpointAddressPrefix filter to match any messages addressed to `http://<hostname>/vdir*`.</span></span>  
  
```xml  
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />  
```  
  
```csharp  
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  <span data-ttu-id="c7058-127">Należy zauważyć, że część nazwy hosta adresu mogą się różnić zależnie od tego, czy klient używa w pełni kwalifikowaną nazwę domeny, nazwa NetBIOS, adres IP lub innej nazwy.</span><span class="sxs-lookup"><span data-stu-id="c7058-127">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="c7058-128">Ponieważ różne wartości mogą odwoływać się do tego samego hosta, domyślne zachowanie dla tego porównania jest nieużywanie część nazwy hosta adres podczas przeprowadzania dopasowań.</span><span class="sxs-lookup"><span data-stu-id="c7058-128">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>  
  
 <span data-ttu-id="c7058-129">Ten filtr powinien służyć routing wiadomości przychodzących, które współużytkują Wspólny prefiks adresu.</span><span class="sxs-lookup"><span data-stu-id="c7058-129">This filter should be used when routing incoming messages that share a common address prefix.</span></span>  
  
### <a name="and"></a><span data-ttu-id="c7058-130">AND</span><span class="sxs-lookup"><span data-stu-id="c7058-130">AND</span></span>  
 <span data-ttu-id="c7058-131">Filtr i nie filtruje bezpośrednio na podstawie wartości w wiadomości, ale pozwala połączyć dwa filtry do utworzenia `AND` warunku, gdzie oba filtry muszą być zgodne komunikatu przed filtru i daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="c7058-131">The AND filter does not directly filter on a value within a message, but allows you to combine two other filters to create an `AND` condition where both filters must match the message before the AND filter evaluates to `true`.</span></span> <span data-ttu-id="c7058-132">Dzięki temu można tworzyć złożone filtry, które dopasowanie tylko wtedy, gdy wszystkie podrzędne filtry zgodne.</span><span class="sxs-lookup"><span data-stu-id="c7058-132">This allows you to create complex filters that only match if all the sub-filters match.</span></span> <span data-ttu-id="c7058-133">Poniższy przykład definiuje filtry adresów i akcji, a następnie definiuje filtr i przetwarza wiadomość filtry adres i akcji.</span><span class="sxs-lookup"><span data-stu-id="c7058-133">The following example defines an address filter and an action filter, and then defines an AND filter that evaluates a message against both the address and action filters.</span></span> <span data-ttu-id="c7058-134">Jeśli zarówno adres, jak i filtry akcji są zgodne, a następnie filtr i zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="c7058-134">If both the address and the action filters match, then the AND filter returns `true`.</span></span>  
  
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
  
 <span data-ttu-id="c7058-135">Ten filtr powinien służyć należy połączyć Logic Apps z wielu filtrów, aby określić, kiedy powinno się dopasowania.</span><span class="sxs-lookup"><span data-stu-id="c7058-135">This filter should be used when you must combine the logic from multiple filters to determine when a match should be made.</span></span> <span data-ttu-id="c7058-136">Na przykład w przypadku wielu miejsc docelowych, które muszą odbierać tylko niektóre kombinacje akcji i komunikaty do konkretnego adresów służy filtru i połączyć niezbędne filtry akcji i od adresów.</span><span class="sxs-lookup"><span data-stu-id="c7058-136">For example, if you have multiple destinations that must receive only certain combinations of actions and messages to particular addresses, you can use an AND filter to combine the necessary Action and Address filters.</span></span>  
  
### <a name="custom"></a><span data-ttu-id="c7058-137">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="c7058-137">Custom</span></span>  
 <span data-ttu-id="c7058-138">Podczas wybierania typu filtr niestandardowy, należy podać wartość customtype —, zawierający typ zestawu, który zawiera **MessageFilter** wdrożenia ma być używany dla tego filtru.</span><span class="sxs-lookup"><span data-stu-id="c7058-138">When selecting the Custom filter type, you must provide a customType value that contains the type of the assembly that contains the **MessageFilter** implementation to be used for this filter.</span></span> <span data-ttu-id="c7058-139">Ponadto danych filtru musi zawierać dowolnych wartości, które filtr niestandardowy może wymagać jej oceny wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c7058-139">Additionally, filterData must contain any values that the custom filter may require in its evaluation of messages.</span></span> <span data-ttu-id="c7058-140">W poniższym przykładzie zdefiniowano `FilterElement` , który używa `CustomAssembly.MyCustomMsgFilter` MessageFilter implementacji.</span><span class="sxs-lookup"><span data-stu-id="c7058-140">The following example defines a `FilterElement` that uses the `CustomAssembly.MyCustomMsgFilter` MessageFilter implementation.</span></span>  
  
```xml  
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />  
```  
  
```csharp  
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");  
```  
  
 <span data-ttu-id="c7058-141">Jeśli zachodzi potrzeba wykonania niestandardowej logiki pasującego przed komunikatami, które nie jest objęta filtry dostarczane z [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], należy utworzyć filtr niestandardowy, który jest implementacją **MessageFilter** klasy.</span><span class="sxs-lookup"><span data-stu-id="c7058-141">If you need to perform custom matching logic against a message that is not covered by the filters provided with [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], you must create a custom filter that is an implementation of the **MessageFilter** class.</span></span> <span data-ttu-id="c7058-142">Na przykład utworzyć filtr niestandardowy, który porównuje pola w przychodzącej wiadomości z listą znane wartości do filtrowania konfiguracji lub wyznacza wartość skrótu elementu określoną wiadomość i następnie sprawdza, czy ta wartość, aby określić, czy filtr powinna zostać zwrócona `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="c7058-142">For example, you might create a custom filter that compares a field in the incoming message against a list of known values given to the filter as configuration, or that hashes a particular message element and then examines that value to determine whether the filter should return `true` or `false`.</span></span>  
  
### <a name="endpointname"></a><span data-ttu-id="c7058-143">EndpointName</span><span class="sxs-lookup"><span data-stu-id="c7058-143">EndpointName</span></span>  
 <span data-ttu-id="c7058-144">Filtr Nazwapunktukoncowego sprawdza nazwę punktu końcowego, który otrzymał komunikat.</span><span class="sxs-lookup"><span data-stu-id="c7058-144">The EndpointName filter inspects the name of the endpoint that received the message.</span></span> <span data-ttu-id="c7058-145">W poniższym przykładzie zdefiniowano `FilterElement` używającej Nazwapunktukoncowego filtru w celu przesyłania wiadomości odebrane w "SvcEndpoint".</span><span class="sxs-lookup"><span data-stu-id="c7058-145">The following example defines a `FilterElement` that uses the EndpointName filter to route messages received on the "SvcEndpoint".</span></span>  
  
```xml  
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />  
```  
  
```csharp  
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");  
```  
  
 <span data-ttu-id="c7058-146">Ten filtr jest przydatny, gdy usługa routingu udostępnia więcej niż jeden punkt końcowy usługi o nazwie.</span><span class="sxs-lookup"><span data-stu-id="c7058-146">This filter is useful when the Routing Service exposes more than one named service endpoint.</span></span> <span data-ttu-id="c7058-147">Na przykład można uwidocznić dwa punkty końcowe używane usługa routingu do odbierania wiadomości. jeden jest używany przez klientom priorytet, którzy potrzebują, przetwarzanie ich komunikatów, podczas inny punkt końcowy w czasie rzeczywistym odbiera komunikaty, które nie są czasu liter.</span><span class="sxs-lookup"><span data-stu-id="c7058-147">For example, you might expose two endpoints that the Routing Service uses to receive messages; one is used by priority customers who require real-time processing of their messages, while the other endpoint receives messages that are not time sensitive.</span></span>  
  
 <span data-ttu-id="c7058-148">Często możesz użyć pełnego adresu dopasowania, aby ustalić którym punktem końcowym wiadomość została odebrana, zamiast wybranej nazwy punktu końcowego zdefiniowana jest wygodny skrót, który jest często mniej podatne, błąd, szczególnie w przypadku konfigurowania usługi routingu przy użyciu konfiguracji plik (gdzie nazwy punktów końcowych są wymaganego atrybutu).</span><span class="sxs-lookup"><span data-stu-id="c7058-148">While you can often use full address matching to determine which endpoint a message was received on, using the defined endpoint name instead is a convenient shortcut that is often less error prone, especially when configuring a Routing Service using a configuration file (where endpoint names are a required attribute).</span></span>  
  
### <a name="matchall"></a><span data-ttu-id="c7058-149">MatchAll</span><span class="sxs-lookup"><span data-stu-id="c7058-149">MatchAll</span></span>  
 <span data-ttu-id="c7058-150">Filtr MatchAll pasuje do dowolnego odebranego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="c7058-150">The MatchAll filter matches any received message.</span></span> <span data-ttu-id="c7058-151">Jest to przydatne, jeśli wszystkie odebrane wiadomości musi zawsze kierować do określonego punktu końcowego, takie jak usługa rejestrowania, która przechowuje kopię wszystkich odebranych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="c7058-151">It is useful if you must always route all received messages to a specific endpoint, such as a logging service that stores a copy of all received messages.</span></span> <span data-ttu-id="c7058-152">W poniższym przykładzie zdefiniowano `FilterElement` korzystającą z filtrem MatchAll.</span><span class="sxs-lookup"><span data-stu-id="c7058-152">The following example defines a `FilterElement` that uses the MatchAll filter.</span></span>  
  
```xml  
<filter name="matchAll1" filterType="MatchAll" />  
```  
  
```csharp  
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();  
```  
  
### <a name="xpath"></a><span data-ttu-id="c7058-153">XPath</span><span class="sxs-lookup"><span data-stu-id="c7058-153">XPath</span></span>  
 <span data-ttu-id="c7058-154">Filtr XPath można określić zapytanie XPath, używanej do inspekcji określonego elementu w wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c7058-154">The XPath filter allows you to specify an XPath query that is used to inspect a specific element within the message.</span></span> <span data-ttu-id="c7058-155">Filtrowanie XPath jest zaawansowanych opcji filtrowania, która umożliwia inspekcję bezpośrednio żadnego wpisu adresowalnych XML wiadomości; jednak wymaga, że masz szczególnej wiedzy na temat struktury wiadomości, które są odbierane.</span><span class="sxs-lookup"><span data-stu-id="c7058-155">XPath filtering is a powerful filtering option that allows you to directly inspect any XML addressable entry within the message; however it requires that you have specific knowledge of the structure of the messages that you are receiving.</span></span> <span data-ttu-id="c7058-156">W poniższym przykładzie zdefiniowano `FilterElement` używającą filtr XPath do wglądu do wiadomości dla elementu o nazwie "element" w przestrzeni nazw, odwołuje się prefiks przestrzeni nazw "ns".</span><span class="sxs-lookup"><span data-stu-id="c7058-156">The following example defines a `FilterElement` that uses the XPath filter to inspect the message for an element named "element" within the namespace referenced by the "ns" namespace prefix.</span></span>  
  
```xml  
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />  
```  
  
```csharp  
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");  
```  
  
 <span data-ttu-id="c7058-157">Ten filtr jest przydatny, jeśli wiesz, że wiadomości, które otrzymujesz zawiera określoną wartość.</span><span class="sxs-lookup"><span data-stu-id="c7058-157">This filter is useful if you know that the messages you are receiving contain a specific value.</span></span> <span data-ttu-id="c7058-158">Na przykład jeśli są hostowane dwie wersje tej samej usłudze i dowiedzieć się, że komunikaty adresowane do nowszej wersji usługi zawiera unikatową wartość niestandardowego nagłówka, możesz utworzyć filtr, który używa XPath, aby przejść do tego pliku nagłówkowego i porównuje prez wartość ENT w nagłówku do innego podane w konfiguracji filtru, aby określić, jeśli filtr dopasowuje wartość.</span><span class="sxs-lookup"><span data-stu-id="c7058-158">For example, if you are hosting two versions of the same service and you know that messages addressed to the newer version of the service contain a unique value in a custom header, you can create a filter that uses XPath to navigate to this header and compares the value present in the header to another given in the filter configuration to determine if the filter matches.</span></span>  
  
 <span data-ttu-id="c7058-159">Ponieważ kwerendy XPath często zawierają unikatowy przestrzeni nazw, które są często długi lub wartości ciągu złożonego, filtr XPath pozwala zdefiniować unikatowy prefiksów dla usługi przestrzenie nazw przy użyciu tabeli przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c7058-159">Because XPath queries often contain unique namespaces, which are often lengthy or complex string values, the XPath filter allows you to use the namespace table to define unique prefixes for your namespaces.</span></span> <span data-ttu-id="c7058-160">Aby uzyskać więcej informacji o tabeli przestrzeni nazw, zobacz [filtry komunikatów](../../../../docs/framework/wcf/feature-details/message-filters.md).</span><span class="sxs-lookup"><span data-stu-id="c7058-160">For more information about the namespace table, see [Message Filters](../../../../docs/framework/wcf/feature-details/message-filters.md).</span></span>  
  
 <span data-ttu-id="c7058-161">Aby uzyskać więcej informacji na temat projektowania zapytania XPath, zobacz [składni XPath](https://go.microsoft.com/fwlink/?LinkId=164592).</span><span class="sxs-lookup"><span data-stu-id="c7058-161">For more information about designing XPath queries, see [XPath Syntax](https://go.microsoft.com/fwlink/?LinkId=164592).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7058-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7058-162">See also</span></span>
- [<span data-ttu-id="c7058-163">Filtry komunikatów</span><span class="sxs-lookup"><span data-stu-id="c7058-163">Message Filters</span></span>](../../../../docs/framework/wcf/feature-details/message-filters.md)
- [<span data-ttu-id="c7058-164">Instrukcje: Użyj filtrów</span><span class="sxs-lookup"><span data-stu-id="c7058-164">How To: Use Filters</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
