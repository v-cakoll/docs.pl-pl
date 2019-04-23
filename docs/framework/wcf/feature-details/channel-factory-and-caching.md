---
title: Fabryka kanałów i buforowanie
ms.date: 03/30/2017
ms.assetid: 954f030e-091c-4c0e-a7a2-10f9a6b1f529
ms.openlocfilehash: 3914ba74337bd959558348c191a897c79a32da52
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59106460"
---
# <a name="channel-factory-and-caching"></a><span data-ttu-id="8e688-102">Fabryka kanałów i buforowanie</span><span class="sxs-lookup"><span data-stu-id="8e688-102">Channel Factory and Caching</span></span>
<span data-ttu-id="8e688-103">Aplikacje klienta WCF <xref:System.ServiceModel.ChannelFactory%601> klasy, aby utworzyć kanał komunikacji z usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="8e688-103">WCF client applications use the <xref:System.ServiceModel.ChannelFactory%601> class to create a communication channel with a WCF service.</span></span>  <span data-ttu-id="8e688-104">Tworzenie <xref:System.ServiceModel.ChannelFactory%601> wystąpień powoduje pewne nadmiarowe obciążenie, ponieważ obejmuje ona następujące operacje:</span><span class="sxs-lookup"><span data-stu-id="8e688-104">Creating <xref:System.ServiceModel.ChannelFactory%601> instances incurs some overhead because it involves the following operations:</span></span>  
  
-   <span data-ttu-id="8e688-105">Konstruowanie <xref:System.ServiceModel.Description.ContractDescription> drzewa</span><span class="sxs-lookup"><span data-stu-id="8e688-105">Constructing the <xref:System.ServiceModel.Description.ContractDescription> tree</span></span>  
  
-   <span data-ttu-id="8e688-106">Odzwierciedlenie wszystkich wymaganych typów CLR</span><span class="sxs-lookup"><span data-stu-id="8e688-106">Reflecting all of the required CLR types</span></span>  
  
-   <span data-ttu-id="8e688-107">Konstruowanie stosu kanału</span><span class="sxs-lookup"><span data-stu-id="8e688-107">Constructing the channel stack</span></span>  
  
-   <span data-ttu-id="8e688-108">Usuwanie zasobów</span><span class="sxs-lookup"><span data-stu-id="8e688-108">Disposing of resources</span></span>  
  
 <span data-ttu-id="8e688-109">Aby zminimalizować ten narzut, WCF może buforować fabryki kanałów, korzystając z serwera proxy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="8e688-109">To help minimize this overhead, WCF can cache channel factories when you are using a WCF client proxy.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="8e688-110">Masz bezpośrednią kontrolę nad tworzenie fabryki kanałów, gdy używasz <xref:System.ServiceModel.ChannelFactory%601> klasy bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="8e688-110">You have direct control over channel factory creation when you use the <xref:System.ServiceModel.ChannelFactory%601> class directly.</span></span>  
  
 <span data-ttu-id="8e688-111">Proxy klienta WCF wygenerowane z [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) są uzyskiwane z <xref:System.ServiceModel.ClientBase%601>.</span><span class="sxs-lookup"><span data-stu-id="8e688-111">WCF client proxies generated with [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) are derived from <xref:System.ServiceModel.ClientBase%601>.</span></span> <span data-ttu-id="8e688-112"><xref:System.ServiceModel.ClientBase%601> Definiuje statycznego <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> właściwość, która definiuje zachowanie pamięci podręcznej fabryki kanału.</span><span class="sxs-lookup"><span data-stu-id="8e688-112"><xref:System.ServiceModel.ClientBase%601> defines a static <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property that defines channel factory caching behavior.</span></span> <span data-ttu-id="8e688-113">Ustawienia pamięci podręcznej są wykonywane dla określonego typu.</span><span class="sxs-lookup"><span data-stu-id="8e688-113">Cache settings are made for a specific type.</span></span> <span data-ttu-id="8e688-114">Na przykład ustawienie `ClientBase<ITest>.CacheSettings` jedną z wartości zdefiniowanych poniżej wpłynie tylko tych proxy/element ClientBase typu `ITest`.</span><span class="sxs-lookup"><span data-stu-id="8e688-114">For example, setting  `ClientBase<ITest>.CacheSettings` to one of the values defined below will affect only those proxy/ClientBase of type `ITest`.</span></span> <span data-ttu-id="8e688-115">Ustawienie pamięci podręcznej dla określonego <xref:System.ServiceModel.ClientBase%601> jest niezmienny zaraz po utworzeniu pierwszego wystąpienia serwera proxy/element ClientBase.</span><span class="sxs-lookup"><span data-stu-id="8e688-115">The cache setting for a particular <xref:System.ServiceModel.ClientBase%601> is immutable as soon as the first proxy/ClientBase instance is created.</span></span>  
  
## <a name="specifying-caching-behavior"></a><span data-ttu-id="8e688-116">Określanie zachowania buforowania</span><span class="sxs-lookup"><span data-stu-id="8e688-116">Specifying Caching Behavior</span></span>  
 <span data-ttu-id="8e688-117">Zachowanie buforowania jest określany przez ustawienie <xref:System.ServiceModel.ClientBase%601.CacheSetting> właściwość na jedną z następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="8e688-117">Caching behavior is specified by setting the <xref:System.ServiceModel.ClientBase%601.CacheSetting> property to one of the following values.</span></span>  
  
|<span data-ttu-id="8e688-118">Ustawienie wartości w pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="8e688-118">Cache Setting Value</span></span>|<span data-ttu-id="8e688-119">Opis</span><span class="sxs-lookup"><span data-stu-id="8e688-119">Description</span></span>|  
|-------------------------|-----------------|  
|<xref:System.ServiceModel.CacheSetting.AlwaysOn>|<span data-ttu-id="8e688-120">Wszystkie wystąpienia elementu <xref:System.ServiceModel.ClientBase%601> w domenie aplikacji mogą brać udział w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="8e688-120">All instances of <xref:System.ServiceModel.ClientBase%601> within the app-domain can participate in caching.</span></span> <span data-ttu-id="8e688-121">Deweloper ustalono, że nie nie skutki dla bezpieczeństwa negatywnie do buforowania.</span><span class="sxs-lookup"><span data-stu-id="8e688-121">The developer has determined that there are no adverse security implications to caching.</span></span> <span data-ttu-id="8e688-122">Pamięć podręczna będzie nie można wyłączyć nawet wtedy, gdy "istotnymi dla zabezpieczeń" właściwości <xref:System.ServiceModel.ClientBase%601> są dostępne.</span><span class="sxs-lookup"><span data-stu-id="8e688-122">Caching will not be turned off even if "security-sensitive" properties on <xref:System.ServiceModel.ClientBase%601> are accessed.</span></span> <span data-ttu-id="8e688-123">Właściwości "istotnymi dla zabezpieczeń" <xref:System.ServiceModel.ClientBase%601> są <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> i <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e688-123">The "security-sensitive" properties of <xref:System.ServiceModel.ClientBase%601> are <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> and <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span></span>|  
|<xref:System.ServiceModel.CacheSetting.Default>|<span data-ttu-id="8e688-124">Tylko wystąpienia <xref:System.ServiceModel.ClientBase%601> utworzone na podstawie punktów końcowych zdefiniowanych w konfiguracji, pliki uczestniczyć w pamięci podręcznej w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8e688-124">Only instances of <xref:System.ServiceModel.ClientBase%601> created from endpoints defined in configuration files participate in caching within the app-domain.</span></span> <span data-ttu-id="8e688-125">Wszystkie wystąpienia <xref:System.ServiceModel.ClientBase%601> utworzony programowo w ramach tej domeny aplikacji nie będzie uczestniczyć w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="8e688-125">Any instances of <xref:System.ServiceModel.ClientBase%601> created programmatically within that app-domain will not participate in caching.</span></span> <span data-ttu-id="8e688-126">Ponadto pamięć podręczna zostanie wyłączony dla wystąpienia programu <xref:System.ServiceModel.ClientBase%601> po żadnej z jej właściwości "istotnymi dla zabezpieczeń" jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="8e688-126">Also, caching will be disabled for an instance of <xref:System.ServiceModel.ClientBase%601> once any of its "security-sensitive" properties is accessed.</span></span>|  
|<xref:System.ServiceModel.CacheSetting.AlwaysOff>|<span data-ttu-id="8e688-127">Buforowanie jest wyłączone dla wszystkich wystąpień <xref:System.ServiceModel.ClientBase%601> określonego typu w ramach aplikacji domeny w danym.</span><span class="sxs-lookup"><span data-stu-id="8e688-127">Caching is turned off for all instances of <xref:System.ServiceModel.ClientBase%601> of a particular type within the app-domain in question.</span></span>|  
  
 <span data-ttu-id="8e688-128">Poniższe fragmenty kodu przedstawiają sposób użycia <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8e688-128">The following code snippets illustrate how to use the <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property.</span></span>  
  
```csharp  
class Program   
{   
   static void Main(string[] args)   
   {   
      ClientBase<ITest>.CacheSettings = CacheSettings.AlwaysOn;   
      foreach (string msg in messages)   
      {   
         using (TestClient proxy = new TestClient (new BasicHttpBinding(), new EndpointAddress(address)))   
         {   
            // ...  
            proxy.Test(msg);   
            // ...  
         }   
      }   
   }   
}  
// Generated by SvcUtil.exe     
public partial class TestClient : System.ServiceModel.ClientBase, ITest { }  
```  
  
 <span data-ttu-id="8e688-129">W kodzie powyżej, wszystkie wystąpienia elementu `TestClient` użyje tych samych fabryki kanałów.</span><span class="sxs-lookup"><span data-stu-id="8e688-129">In the above code, all instances of `TestClient` will use the same channel factory.</span></span>  
  
```csharp  
class Program   
{   
   static void Main(string[] args)   
   {   
      ClientBase.CacheSettings = CacheSettings.Default;   
      int i = 1;   
      foreach (string msg in messages)   
      {   
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))   
         {   
            if (i == 4)   
            {   
               ServiceEndpoint endpoint = proxy.Endpoint;   
               ... // use endpoint in some way   
            }   
            proxy.Test(msg);   
         }   
         i++;   
   }   
}   
  
// Generated by SvcUtil.exe     
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}  
```  
  
 <span data-ttu-id="8e688-130">W przykładzie powyżej, wszystkie wystąpienia elementu `TestClient` użyje tych samych fabryki kanałów, z wyjątkiem wystąpienia #4.</span><span class="sxs-lookup"><span data-stu-id="8e688-130">In the example above, all instances of `TestClient` would use the same channel factory except instance #4.</span></span> <span data-ttu-id="8e688-131">Wystąpienie #4 użyje fabryki kanałów, który jest tworzony w szczególności w ramach jego użycia.</span><span class="sxs-lookup"><span data-stu-id="8e688-131">Instance #4 would use a channel factory that is created specifically for its use.</span></span> <span data-ttu-id="8e688-132">To ustawienie będzie działać dla scenariuszy, w których danego punktu końcowego wymaga różnych typach ustawień zabezpieczeń z innych punktów końcowych tego samego typu fabryki kanału (w tym przypadku `ITest`).</span><span class="sxs-lookup"><span data-stu-id="8e688-132">This setting would work for scenarios where a particular endpoint needs different security settings from the other endpoints of the same channel factory type (in this case `ITest`).</span></span>  
  
```csharp  
class Program   
{   
   static void Main(string[] args)   
   {   
      ClientBase.CacheSettings = CacheSettings.AlwaysOff;   
      foreach (string msg in messages)   
      {   
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))   
         {   
            proxy.Test(msg);   
         }           
      }   
   }  
}  
  
// Generated by SvcUtil.exe   
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}  
```  
  
 <span data-ttu-id="8e688-133">W przykładzie powyżej, wszystkie wystąpienia elementu `TestClient` użyć różnych kanałów fabryk.</span><span class="sxs-lookup"><span data-stu-id="8e688-133">In the example above, all instances of `TestClient` would use different channel factories.</span></span> <span data-ttu-id="8e688-134">Jest to przydatne, gdy każdy punkt końcowy ma inne wymagania dotyczące zabezpieczeń i nie ma sensu do pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="8e688-134">This is useful when each endpoint has different security requirements and it makes no sense to cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e688-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e688-135">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601>
- [<span data-ttu-id="8e688-136">Kompilowanie klientów</span><span class="sxs-lookup"><span data-stu-id="8e688-136">Building Clients</span></span>](../../../../docs/framework/wcf/building-clients.md)
- [<span data-ttu-id="8e688-137">Klienci</span><span class="sxs-lookup"><span data-stu-id="8e688-137">Clients</span></span>](../../../../docs/framework/wcf/feature-details/clients.md)
- [<span data-ttu-id="8e688-138">Uzyskiwanie dostępu do usług za pomocą klienta WCF</span><span class="sxs-lookup"><span data-stu-id="8e688-138">Accessing Services Using a WCF Client</span></span>](../../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="8e688-139">Instrukcje: Używanie elementu ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="8e688-139">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
