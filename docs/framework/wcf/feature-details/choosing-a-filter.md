---
title: Wybieranie filtra
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: 908e905b4196409b00abccccae03436640cbe986
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045977"
---
# <a name="choosing-a-filter"></a><span data-ttu-id="5b947-102">Wybieranie filtra</span><span class="sxs-lookup"><span data-stu-id="5b947-102">Choosing a Filter</span></span>
<span data-ttu-id="5b947-103">Podczas konfigurowania usługi routingu ważne jest, aby wybrać poprawne filtry komunikatów i skonfigurować je w taki sposób, aby umożliwiały dokładne dopasowanie do odbieranych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="5b947-103">When configuring the Routing Service, it is important to select correct message filters and configure them to allow you to make exact matches against the messages you receive.</span></span> <span data-ttu-id="5b947-104">Jeśli wybrane filtry są zbyt szerokie w dopasowaniach lub są nieprawidłowo skonfigurowane, komunikaty są kierowane nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="5b947-104">If the filters you select are overly broad in their matches or are incorrectly configured, messages are routed incorrectly.</span></span> <span data-ttu-id="5b947-105">Jeśli filtry są zbyt restrykcyjne, może nie mieć dostępnych prawidłowych tras dla niektórych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="5b947-105">If the filters are too restrictive, you may not have any valid routes available for some of your messages.</span></span>

## <a name="filter-types"></a><span data-ttu-id="5b947-106">Typy filtrów</span><span class="sxs-lookup"><span data-stu-id="5b947-106">Filter Types</span></span>

<span data-ttu-id="5b947-107">Podczas wybierania filtrów, które są używane przez usługę routingu, ważne jest, aby zrozumieć, jak działa każdy filtr, a także jakie informacje są dostępne w ramach komunikatów przychodzących.</span><span class="sxs-lookup"><span data-stu-id="5b947-107">When selecting the filters that are used by the Routing Service, it is important that you understand how each filter works as well as what information is available as part of the incoming messages.</span></span> <span data-ttu-id="5b947-108">Na przykład, jeśli wszystkie komunikaty są odbierane w tym samym punkcie końcowym, filtry adresu i punktu końcowego nie są przydatne, ponieważ wszystkie komunikaty pasują do tych filtrów.</span><span class="sxs-lookup"><span data-stu-id="5b947-108">For instance, if all messages are received over the same endpoint, the Address and EndpointName filters are not useful because all messages match these filters.</span></span>

### <a name="action"></a><span data-ttu-id="5b947-109">Akcja</span><span class="sxs-lookup"><span data-stu-id="5b947-109">Action</span></span>

<span data-ttu-id="5b947-110">Filtr akcji sprawdza <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="5b947-110">The Action filter inspects the <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> property.</span></span> <span data-ttu-id="5b947-111">Jeśli zawartość nagłówka akcji w komunikacie jest zgodna z wartością Filtruj dane określoną w konfiguracji filtru, ten filtr zwraca wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="5b947-111">If the contents of the Action header in the message match the filter data value specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="5b947-112">W poniższym przykładzie zdefiniowano `FilterElement` , który używa filtru akcji, aby dopasować komunikaty z nagłówkiem akcji, który zawiera `http://namespace/contract/operation/`wartość.</span><span class="sxs-lookup"><span data-stu-id="5b947-112">The following example defines a `FilterElement` that uses the Action filter to match messages with an action header that contains a value of `http://namespace/contract/operation/`.</span></span>

```xml
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />
```

```csharp
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });
```

<span data-ttu-id="5b947-113">Ten filtr powinien być używany podczas routingu komunikatów, które zawierają unikatowy nagłówek akcji.</span><span class="sxs-lookup"><span data-stu-id="5b947-113">This filter should be used when routing messages that contain a unique Action header.</span></span>

### <a name="endpointaddress"></a><span data-ttu-id="5b947-114">Elemencie</span><span class="sxs-lookup"><span data-stu-id="5b947-114">EndpointAddress</span></span>

<span data-ttu-id="5b947-115">Filtr EndpointAddress sprawdza wartość elementu EndpointAddress, w którym wiadomość została odebrana.</span><span class="sxs-lookup"><span data-stu-id="5b947-115">The EndpointAddress filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="5b947-116">Jeśli adres odebrany przez komunikat dokładnie pasuje do adresu filtru określonego w konfiguracji filtru, ten filtr zwraca wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="5b947-116">If the address that the message arrives at exactly matches the filter address specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="5b947-117">W poniższym przykładzie zdefiniowano `FilterElement` , który używa filtru adresów w celu dopasowania wszelkich komunikatów skierowanych do\<"http://hostname >/vdir/s.svc/b".</span><span class="sxs-lookup"><span data-stu-id="5b947-117">The following example defines a `FilterElement` that uses the Address filter to match any messages addressed to "http://\<hostname>/vdir/s.svc/b".</span></span>

```xml
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />
```

```csharp
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
```

> [!NOTE]
> <span data-ttu-id="5b947-118">Należy pamiętać, że nazwa hosta część adresu może się różnić w zależności od tego, czy klient korzysta z w pełni kwalifikowanej nazwy domeny, nazwy NetBIOS, adresu IP czy innej nazwy.</span><span class="sxs-lookup"><span data-stu-id="5b947-118">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="5b947-119">Ponieważ różne wartości mogą odwoływać się do tego samego hosta, zachowanie domyślne dla tego porównania ma nie używać części nazwy hosta w przypadku wykonywania dopasowań.</span><span class="sxs-lookup"><span data-stu-id="5b947-119">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>
>
> <span data-ttu-id="5b947-120">Takie zachowanie można zmodyfikować tak, aby umożliwić porównanie do oszacowania nazwy hosta podczas programistycznego konfigurowania usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="5b947-120">This behavior can be modified to allow the comparison to evaluate the host name when configuring the Routing Service programmatically.</span></span>

<span data-ttu-id="5b947-121">Ten filtr powinien być używany, gdy wiadomości przychodzące są rozkierowane na unikatowy adres.</span><span class="sxs-lookup"><span data-stu-id="5b947-121">This filter should be used when the incoming messages are addressed to a unique address.</span></span>

### <a name="endpointaddressprefix"></a><span data-ttu-id="5b947-122">EndpointAddressPrefix</span><span class="sxs-lookup"><span data-stu-id="5b947-122">EndpointAddressPrefix</span></span>

<span data-ttu-id="5b947-123">Filtr EndpointAddressPrefix jest podobny do filtru EndpointAddress.</span><span class="sxs-lookup"><span data-stu-id="5b947-123">The EndpointAddressPrefix filter is similar to the EndpointAddress filter.</span></span> <span data-ttu-id="5b947-124">Filtr EndpointAddressPrefix sprawdza wartość EndpointAddress, w której wiadomość została odebrana.</span><span class="sxs-lookup"><span data-stu-id="5b947-124">The EndpointAddressPrefix filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="5b947-125">Jednak filtr EndpointAddressPrefix działa jako symbol wieloznaczny przez dopasowanie adresów zaczynających się od wartości określonej w konfiguracji filtru.</span><span class="sxs-lookup"><span data-stu-id="5b947-125">However the EndpointAddressPrefix filter acts as a wildcard by matching addresses that begin with the value specified in the filter configuration.</span></span> <span data-ttu-id="5b947-126">W poniższym przykładzie zdefiniowano `FilterElement` , który używa filtru EndpointAddressPrefix do dopasowania wszelkich komunikatów skierowanych `http://<hostname>/vdir*`do.</span><span class="sxs-lookup"><span data-stu-id="5b947-126">The following example defines a `FilterElement` that uses the EndpointAddressPrefix filter to match any messages addressed to `http://<hostname>/vdir*`.</span></span>

```xml
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />
```

```csharp
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
```

> [!NOTE]
> <span data-ttu-id="5b947-127">Należy pamiętać, że nazwa hosta część adresu może się różnić w zależności od tego, czy klient korzysta z w pełni kwalifikowanej nazwy domeny, nazwy NetBIOS, adresu IP czy innej nazwy.</span><span class="sxs-lookup"><span data-stu-id="5b947-127">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="5b947-128">Ponieważ różne wartości mogą odwoływać się do tego samego hosta, zachowanie domyślne dla tego porównania ma nie używać części nazwy hosta w przypadku wykonywania dopasowań.</span><span class="sxs-lookup"><span data-stu-id="5b947-128">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>

<span data-ttu-id="5b947-129">Ten filtr powinien być używany podczas routingu przychodzących komunikatów, które współużytkują wspólny prefiks adresu.</span><span class="sxs-lookup"><span data-stu-id="5b947-129">This filter should be used when routing incoming messages that share a common address prefix.</span></span>

### <a name="and"></a><span data-ttu-id="5b947-130">AND</span><span class="sxs-lookup"><span data-stu-id="5b947-130">AND</span></span>

<span data-ttu-id="5b947-131">Filtr i nie bezpośrednio filtruje wartość w komunikacie, ale umożliwia połączenie dwóch innych filtrów w celu utworzenia `AND` warunku, w którym oba filtry muszą być zgodne z komunikatem, zanim filtr i zwróci wartość. `true`</span><span class="sxs-lookup"><span data-stu-id="5b947-131">The AND filter does not directly filter on a value within a message, but allows you to combine two other filters to create an `AND` condition where both filters must match the message before the AND filter evaluates to `true`.</span></span> <span data-ttu-id="5b947-132">Dzięki temu można tworzyć złożone filtry, które pasują tylko wtedy, gdy wszystkie filtry podrzędne pasują do siebie.</span><span class="sxs-lookup"><span data-stu-id="5b947-132">This allows you to create complex filters that only match if all the sub-filters match.</span></span> <span data-ttu-id="5b947-133">Poniższy przykład definiuje filtr adresów i filtr akcji, a następnie definiuje filtr i, który szacuje komunikat w odniesieniu do filtrów adresu i akcji.</span><span class="sxs-lookup"><span data-stu-id="5b947-133">The following example defines an address filter and an action filter, and then defines an AND filter that evaluates a message against both the address and action filters.</span></span> <span data-ttu-id="5b947-134">Jeśli adres i filtry akcji pasują do siebie, filtr i zwraca wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="5b947-134">If both the address and the action filters match, then the AND filter returns `true`.</span></span>

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

<span data-ttu-id="5b947-135">Ten filtr powinien być używany, gdy konieczne jest połączenie logiki z wielu filtrów, aby określić, kiedy należy wykonać dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="5b947-135">This filter should be used when you must combine the logic from multiple filters to determine when a match should be made.</span></span> <span data-ttu-id="5b947-136">Na przykład jeśli masz wiele miejsc docelowych, które muszą odbierać tylko niektóre kombinacje akcji i komunikatów do określonych adresów, możesz użyć filtru i, aby połączyć wymagane filtry akcji i adresów.</span><span class="sxs-lookup"><span data-stu-id="5b947-136">For example, if you have multiple destinations that must receive only certain combinations of actions and messages to particular addresses, you can use an AND filter to combine the necessary Action and Address filters.</span></span>

### <a name="custom"></a><span data-ttu-id="5b947-137">Celnej</span><span class="sxs-lookup"><span data-stu-id="5b947-137">Custom</span></span>

<span data-ttu-id="5b947-138">Wybierając typ filtru niestandardowego, należy podać wartość CustomType, która zawiera typ zestawu, który zawiera implementację **MessageFilter** , która ma być używana dla tego filtru.</span><span class="sxs-lookup"><span data-stu-id="5b947-138">When selecting the Custom filter type, you must provide a customType value that contains the type of the assembly that contains the **MessageFilter** implementation to be used for this filter.</span></span> <span data-ttu-id="5b947-139">Ponadto danych filtru musi zawierać wszystkie wartości, które mogą być wymagane przez filtr niestandardowy w ocenie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="5b947-139">Additionally, filterData must contain any values that the custom filter may require in its evaluation of messages.</span></span> <span data-ttu-id="5b947-140">W poniższym przykładzie zdefiniowano `FilterElement` , który `CustomAssembly.MyCustomMsgFilter` używa implementacji MessageFilter.</span><span class="sxs-lookup"><span data-stu-id="5b947-140">The following example defines a `FilterElement` that uses the `CustomAssembly.MyCustomMsgFilter` MessageFilter implementation.</span></span>

```xml
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />
```

```csharp
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");
```

<span data-ttu-id="5b947-141">Jeśli musisz wykonać niestandardową logikę dopasowywania względem komunikatu, który nie jest objęty przez filtry [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]dostarczone z, musisz utworzyć filtr niestandardowy, który jest implementacją klasy **MessageFilter** .</span><span class="sxs-lookup"><span data-stu-id="5b947-141">If you need to perform custom matching logic against a message that is not covered by the filters provided with [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], you must create a custom filter that is an implementation of the **MessageFilter** class.</span></span> <span data-ttu-id="5b947-142">Można na przykład utworzyć filtr niestandardowy, który porównuje pole w komunikacie przychodzącym z listą znanych wartości przyznanych filtrowi jako konfigurację lub które miesza określony element komunikatu, a następnie sprawdza tę wartość, aby określić, czy filtr powinna zwracać `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="5b947-142">For example, you might create a custom filter that compares a field in the incoming message against a list of known values given to the filter as configuration, or that hashes a particular message element and then examines that value to determine whether the filter should return `true` or `false`.</span></span>

### <a name="endpointname"></a><span data-ttu-id="5b947-143">EndpointName</span><span class="sxs-lookup"><span data-stu-id="5b947-143">EndpointName</span></span>

<span data-ttu-id="5b947-144">Filtr EndpointName sprawdza nazwę punktu końcowego, który odebrał komunikat.</span><span class="sxs-lookup"><span data-stu-id="5b947-144">The EndpointName filter inspects the name of the endpoint that received the message.</span></span> <span data-ttu-id="5b947-145">W poniższym przykładzie zdefiniowano `FilterElement` , który używa filtru EndpointName do przesyłania komunikatów odebranych w "SvcEndpoint".</span><span class="sxs-lookup"><span data-stu-id="5b947-145">The following example defines a `FilterElement` that uses the EndpointName filter to route messages received on the "SvcEndpoint".</span></span>

```xml
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />
```

```csharp
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");
```

<span data-ttu-id="5b947-146">Ten filtr jest przydatny, gdy usługa routingu ujawnia więcej niż jeden nazwany punkt końcowy usługi.</span><span class="sxs-lookup"><span data-stu-id="5b947-146">This filter is useful when the Routing Service exposes more than one named service endpoint.</span></span> <span data-ttu-id="5b947-147">Można na przykład uwidocznić dwa punkty końcowe używane przez usługę routingu do odbierania komunikatów. jeden z nich jest używany przez klientów priorytetowych, którzy wymagają przetwarzania komunikatów w czasie rzeczywistym, podczas gdy drugi punkt końcowy otrzymuje komunikaty, które nie są zależne od czasu.</span><span class="sxs-lookup"><span data-stu-id="5b947-147">For example, you might expose two endpoints that the Routing Service uses to receive messages; one is used by priority customers who require real-time processing of their messages, while the other endpoint receives messages that are not time sensitive.</span></span>

<span data-ttu-id="5b947-148">Mimo że w celu określenia punktu końcowego, w którym wiadomość została odebrana, używana jest pełna nazwa punktu końcowego, jest to wygodny skrót, który jest często mniej podatny na błędy, szczególnie w przypadku konfigurowania usługi routingu przy użyciu konfiguracji plik (gdzie nazwy punktów końcowych są wymaganym atrybutem).</span><span class="sxs-lookup"><span data-stu-id="5b947-148">While you can often use full address matching to determine which endpoint a message was received on, using the defined endpoint name instead is a convenient shortcut that is often less error prone, especially when configuring a Routing Service using a configuration file (where endpoint names are a required attribute).</span></span>

### <a name="matchall"></a><span data-ttu-id="5b947-149">MatchAll</span><span class="sxs-lookup"><span data-stu-id="5b947-149">MatchAll</span></span>

<span data-ttu-id="5b947-150">Filtr MatchAll jest zgodny z odebranymi komunikatami.</span><span class="sxs-lookup"><span data-stu-id="5b947-150">The MatchAll filter matches any received message.</span></span> <span data-ttu-id="5b947-151">Jest to przydatne, jeśli konieczne jest zawsze kierowanie wszystkich odebranych komunikatów do określonego punktu końcowego, takich jak usługa rejestrowania przechowująca kopię wszystkich odebranych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="5b947-151">It is useful if you must always route all received messages to a specific endpoint, such as a logging service that stores a copy of all received messages.</span></span> <span data-ttu-id="5b947-152">W poniższym przykładzie zdefiniowano `FilterElement` , który używa filtru MatchAll.</span><span class="sxs-lookup"><span data-stu-id="5b947-152">The following example defines a `FilterElement` that uses the MatchAll filter.</span></span>

```xml
<filter name="matchAll1" filterType="MatchAll" />
```

```csharp
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();
```

### <a name="xpath"></a><span data-ttu-id="5b947-153">XPath</span><span class="sxs-lookup"><span data-stu-id="5b947-153">XPath</span></span>

<span data-ttu-id="5b947-154">Filtr XPath umożliwia określenie zapytania XPath, które jest używane do inspekcji określonego elementu w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="5b947-154">The XPath filter allows you to specify an XPath query that is used to inspect a specific element within the message.</span></span> <span data-ttu-id="5b947-155">Filtrowanie XPath to zaawansowana opcja filtrowania, która umożliwia bezpośrednie sprawdzenie dowolnego wpisu z adresami XML w wiadomości. jednak wymaga to konkretnej znajomości struktury otrzymywanych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="5b947-155">XPath filtering is a powerful filtering option that allows you to directly inspect any XML addressable entry within the message; however it requires that you have specific knowledge of the structure of the messages that you are receiving.</span></span> <span data-ttu-id="5b947-156">W poniższym przykładzie zdefiniowano `FilterElement` , który używa filtru XPath do sprawdzenia komunikatu dla elementu o nazwie "element" w przestrzeni nazw, do którego odwołuje się prefiks przestrzeni nazw "NS".</span><span class="sxs-lookup"><span data-stu-id="5b947-156">The following example defines a `FilterElement` that uses the XPath filter to inspect the message for an element named "element" within the namespace referenced by the "ns" namespace prefix.</span></span>

```xml
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />
```

```csharp
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");
```

<span data-ttu-id="5b947-157">Ten filtr jest przydatny, Jeśli wiesz, że odebrane komunikaty zawierają konkretną wartość.</span><span class="sxs-lookup"><span data-stu-id="5b947-157">This filter is useful if you know that the messages you are receiving contain a specific value.</span></span> <span data-ttu-id="5b947-158">Na przykład, Jeśli przechowujesz dwie wersje tej samej usługi i wiesz, że komunikaty rozkierowane do nowszej wersji usługi zawierają unikatową wartość w niestandardowym nagłówku, możesz utworzyć filtr, który używa XPath, aby przejść do tego nagłówka i porównać wartość zaliczkową. w nagłówku do innego podanego w konfiguracji filtru, aby określić, czy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="5b947-158">For example, if you are hosting two versions of the same service and you know that messages addressed to the newer version of the service contain a unique value in a custom header, you can create a filter that uses XPath to navigate to this header and compares the value present in the header to another given in the filter configuration to determine if the filter matches.</span></span>

<span data-ttu-id="5b947-159">Ponieważ zapytania XPath często zawierają unikatowe przestrzenie nazw, które często mają długość lub złożone wartości ciągu, filtr XPath umożliwia użycie tabeli przestrzeni nazw w celu zdefiniowania unikatowych prefiksów przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5b947-159">Because XPath queries often contain unique namespaces, which are often lengthy or complex string values, the XPath filter allows you to use the namespace table to define unique prefixes for your namespaces.</span></span> <span data-ttu-id="5b947-160">Aby uzyskać więcej informacji na temat tabeli przestrzeni nazw, zobacz [filtry komunikatów](../../../../docs/framework/wcf/feature-details/message-filters.md).</span><span class="sxs-lookup"><span data-stu-id="5b947-160">For more information about the namespace table, see [Message Filters](../../../../docs/framework/wcf/feature-details/message-filters.md).</span></span>

<span data-ttu-id="5b947-161">Aby uzyskać więcej informacji na temat projektowania zapytań XPath, zobacz [składnia XPath](https://go.microsoft.com/fwlink/?LinkId=164592).</span><span class="sxs-lookup"><span data-stu-id="5b947-161">For more information about designing XPath queries, see [XPath Syntax](https://go.microsoft.com/fwlink/?LinkId=164592).</span></span>

## <a name="see-also"></a><span data-ttu-id="5b947-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b947-162">See also</span></span>

- [<span data-ttu-id="5b947-163">Filtry komunikatów</span><span class="sxs-lookup"><span data-stu-id="5b947-163">Message Filters</span></span>](../../../../docs/framework/wcf/feature-details/message-filters.md)
- [<span data-ttu-id="5b947-164">Instrukcje: Używanie filtrów</span><span class="sxs-lookup"><span data-stu-id="5b947-164">How To: Use Filters</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
