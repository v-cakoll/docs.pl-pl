---
title: Fabryka kanałów i buforowanie
ms.date: 03/30/2017
ms.assetid: 954f030e-091c-4c0e-a7a2-10f9a6b1f529
ms.openlocfilehash: 98b77071204e2c2f98609e6c5bb1ca84a896dd58
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040200"
---
# <a name="channel-factory-and-caching"></a><span data-ttu-id="0e96a-102">Fabryka kanałów i buforowanie</span><span class="sxs-lookup"><span data-stu-id="0e96a-102">Channel Factory and Caching</span></span>

<span data-ttu-id="0e96a-103">Aplikacje klienckie programu WCF używają <xref:System.ServiceModel.ChannelFactory%601> klasy do tworzenia kanału komunikacyjnego z usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="0e96a-103">WCF client applications use the <xref:System.ServiceModel.ChannelFactory%601> class to create a communication channel with a WCF service.</span></span>  <span data-ttu-id="0e96a-104">Tworzenie <xref:System.ServiceModel.ChannelFactory%601> wystąpień wiąże się z pewnym obciążeniem, ponieważ obejmuje następujące operacje:</span><span class="sxs-lookup"><span data-stu-id="0e96a-104">Creating <xref:System.ServiceModel.ChannelFactory%601> instances incurs some overhead because it involves the following operations:</span></span>

- <span data-ttu-id="0e96a-105">Konstruowanie <xref:System.ServiceModel.Description.ContractDescription> drzewa</span><span class="sxs-lookup"><span data-stu-id="0e96a-105">Constructing the <xref:System.ServiceModel.Description.ContractDescription> tree</span></span>

- <span data-ttu-id="0e96a-106">Odzwierciedlanie wszystkich wymaganych typów CLR</span><span class="sxs-lookup"><span data-stu-id="0e96a-106">Reflecting all of the required CLR types</span></span>

- <span data-ttu-id="0e96a-107">Konstruowanie stosu kanału</span><span class="sxs-lookup"><span data-stu-id="0e96a-107">Constructing the channel stack</span></span>

- <span data-ttu-id="0e96a-108">Usuwanie zasobów</span><span class="sxs-lookup"><span data-stu-id="0e96a-108">Disposing of resources</span></span>

<span data-ttu-id="0e96a-109">Aby zminimalizować obciążenie, usługa WCF może buforować fabryki kanałów w przypadku korzystania z serwera proxy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="0e96a-109">To help minimize this overhead, WCF can cache channel factories when you are using a WCF client proxy.</span></span>

> [!TIP]
> <span data-ttu-id="0e96a-110">Użytkownik ma bezpośrednią kontrolę nad tworzeniem fabryki kanałów w przypadku bezpośredniego <xref:System.ServiceModel.ChannelFactory%601> używania klasy.</span><span class="sxs-lookup"><span data-stu-id="0e96a-110">You have direct control over channel factory creation when you use the <xref:System.ServiceModel.ChannelFactory%601> class directly.</span></span>

<span data-ttu-id="0e96a-111">Serwery proxy klienta WCF generowane za pomocą [Narzędzia do przesyłania metadanych programu ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pochodzą od <xref:System.ServiceModel.ClientBase%601>.</span><span class="sxs-lookup"><span data-stu-id="0e96a-111">WCF client proxies generated with [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) are derived from <xref:System.ServiceModel.ClientBase%601>.</span></span> <span data-ttu-id="0e96a-112"><xref:System.ServiceModel.ClientBase%601>definiuje Właściwość statyczną <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> , która definiuje zachowanie buforowania fabryki kanałów.</span><span class="sxs-lookup"><span data-stu-id="0e96a-112"><xref:System.ServiceModel.ClientBase%601> defines a static <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property that defines channel factory caching behavior.</span></span> <span data-ttu-id="0e96a-113">Ustawienia pamięci podręcznej dla określonego typu.</span><span class="sxs-lookup"><span data-stu-id="0e96a-113">Cache settings are made for a specific type.</span></span> <span data-ttu-id="0e96a-114">Na przykład ustawienie `ClientBase<ITest>.CacheSettings` jednej z wartości zdefiniowanych poniżej będzie miało wpływ tylko na te dane typu `ITest`proxy/ClientBase.</span><span class="sxs-lookup"><span data-stu-id="0e96a-114">For example, setting  `ClientBase<ITest>.CacheSettings` to one of the values defined below will affect only those proxy/ClientBase of type `ITest`.</span></span> <span data-ttu-id="0e96a-115">Ustawienie pamięci podręcznej dla <xref:System.ServiceModel.ClientBase%601> konkretnego elementu jest niezmienne, gdy tylko zostanie utworzony pierwszy wystąpienie serwera proxy/elementu ClientBase.</span><span class="sxs-lookup"><span data-stu-id="0e96a-115">The cache setting for a particular <xref:System.ServiceModel.ClientBase%601> is immutable as soon as the first proxy/ClientBase instance is created.</span></span>

## <a name="specifying-caching-behavior"></a><span data-ttu-id="0e96a-116">Określanie zachowania buforowania</span><span class="sxs-lookup"><span data-stu-id="0e96a-116">Specifying Caching Behavior</span></span>

<span data-ttu-id="0e96a-117">Zachowanie buforowania jest określone przez ustawienie <xref:System.ServiceModel.ClientBase%601.CacheSetting> właściwości na jedną z następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="0e96a-117">Caching behavior is specified by setting the <xref:System.ServiceModel.ClientBase%601.CacheSetting> property to one of the following values.</span></span>

|<span data-ttu-id="0e96a-118">Wartość ustawienia pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="0e96a-118">Cache Setting Value</span></span>|<span data-ttu-id="0e96a-119">Opis</span><span class="sxs-lookup"><span data-stu-id="0e96a-119">Description</span></span>|
|-------------------------|-----------------|
|<xref:System.ServiceModel.CacheSetting.AlwaysOn>|<span data-ttu-id="0e96a-120">Wszystkie wystąpienia <xref:System.ServiceModel.ClientBase%601> w domenie aplikacji mogą brać udział w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="0e96a-120">All instances of <xref:System.ServiceModel.ClientBase%601> within the app-domain can participate in caching.</span></span> <span data-ttu-id="0e96a-121">Deweloper stwierdził, że nie ma żadnych niepożądanych implikacji w zabezpieczeniach do buforowania.</span><span class="sxs-lookup"><span data-stu-id="0e96a-121">The developer has determined that there are no adverse security implications to caching.</span></span> <span data-ttu-id="0e96a-122">Buforowanie nie zostanie wyłączone, nawet jeśli są dostępne właściwości "poufne dla <xref:System.ServiceModel.ClientBase%601> zabezpieczeń".</span><span class="sxs-lookup"><span data-stu-id="0e96a-122">Caching will not be turned off even if "security-sensitive" properties on <xref:System.ServiceModel.ClientBase%601> are accessed.</span></span> <span data-ttu-id="0e96a-123">Właściwości "z <xref:System.ServiceModel.ClientBase%601> uwzględnieniem zabezpieczeń" są <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> i <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span><span class="sxs-lookup"><span data-stu-id="0e96a-123">The "security-sensitive" properties of <xref:System.ServiceModel.ClientBase%601> are <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> and <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span></span>|
|<xref:System.ServiceModel.CacheSetting.Default>|<span data-ttu-id="0e96a-124">Tylko wystąpienia <xref:System.ServiceModel.ClientBase%601> utworzone z punktów końcowych zdefiniowanych w plikach konfiguracji uczestniczą w pamięci podręcznej w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0e96a-124">Only instances of <xref:System.ServiceModel.ClientBase%601> created from endpoints defined in configuration files participate in caching within the app-domain.</span></span> <span data-ttu-id="0e96a-125">Wszystkie wystąpienia <xref:System.ServiceModel.ClientBase%601> utworzone programowo w tej domenie aplikacji nie będą uczestniczyły w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="0e96a-125">Any instances of <xref:System.ServiceModel.ClientBase%601> created programmatically within that app-domain will not participate in caching.</span></span> <span data-ttu-id="0e96a-126">Ponadto buforowanie zostanie wyłączone dla wystąpienia <xref:System.ServiceModel.ClientBase%601> po uzyskaniu dostępu do wszystkich właściwości "z uwzględnieniem zabezpieczeń".</span><span class="sxs-lookup"><span data-stu-id="0e96a-126">Also, caching will be disabled for an instance of <xref:System.ServiceModel.ClientBase%601> once any of its "security-sensitive" properties is accessed.</span></span>|
|<xref:System.ServiceModel.CacheSetting.AlwaysOff>|<span data-ttu-id="0e96a-127">Buforowanie jest wyłączone dla wszystkich wystąpień <xref:System.ServiceModel.ClientBase%601> określonego typu w danej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0e96a-127">Caching is turned off for all instances of <xref:System.ServiceModel.ClientBase%601> of a particular type within the app-domain in question.</span></span>|

<span data-ttu-id="0e96a-128">Poniższe fragmenty kodu ilustrują sposób użycia <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0e96a-128">The following code snippets illustrate how to use the <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property.</span></span>

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

<span data-ttu-id="0e96a-129">W powyższym kodzie wszystkie wystąpienia programu `TestClient` będą używały tej samej fabryki kanałów.</span><span class="sxs-lookup"><span data-stu-id="0e96a-129">In the above code, all instances of `TestClient` will use the same channel factory.</span></span>

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

<span data-ttu-id="0e96a-130">W powyższym przykładzie wszystkie wystąpienia `TestClient` mogą korzystać z tej samej fabryki kanałów, z wyjątkiem #4 wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="0e96a-130">In the example above, all instances of `TestClient` would use the same channel factory except instance #4.</span></span> <span data-ttu-id="0e96a-131">Wystąpienie #4 będzie używać fabryki kanałów, która została utworzona w celu użycia.</span><span class="sxs-lookup"><span data-stu-id="0e96a-131">Instance #4 would use a channel factory that is created specifically for its use.</span></span> <span data-ttu-id="0e96a-132">To ustawienie będzie działało w scenariuszach, w których konkretny punkt końcowy wymaga różnych ustawień zabezpieczeń z innych punktów końcowych tego samego typu fabryki kanału (w `ITest`tym przypadku).</span><span class="sxs-lookup"><span data-stu-id="0e96a-132">This setting would work for scenarios where a particular endpoint needs different security settings from the other endpoints of the same channel factory type (in this case `ITest`).</span></span>

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

<span data-ttu-id="0e96a-133">W powyższym przykładzie wszystkie wystąpienia `TestClient` byłyby używają różnych fabryk kanałów.</span><span class="sxs-lookup"><span data-stu-id="0e96a-133">In the example above, all instances of `TestClient` would use different channel factories.</span></span> <span data-ttu-id="0e96a-134">Jest to przydatne, gdy każdy punkt końcowy ma inne wymagania dotyczące zabezpieczeń i nie ma sensu buforowania.</span><span class="sxs-lookup"><span data-stu-id="0e96a-134">This is useful when each endpoint has different security requirements and it makes no sense to cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="0e96a-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e96a-135">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601>
- [<span data-ttu-id="0e96a-136">Kompilowanie klientów</span><span class="sxs-lookup"><span data-stu-id="0e96a-136">Building Clients</span></span>](../../../../docs/framework/wcf/building-clients.md)
- [<span data-ttu-id="0e96a-137">Klienci</span><span class="sxs-lookup"><span data-stu-id="0e96a-137">Clients</span></span>](../../../../docs/framework/wcf/feature-details/clients.md)
- [<span data-ttu-id="0e96a-138">Uzyskiwanie dostępu do usług za pomocą klienta WCF</span><span class="sxs-lookup"><span data-stu-id="0e96a-138">Accessing Services Using a WCF Client</span></span>](../../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="0e96a-139">Instrukcje: Korzystanie z elementu ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="0e96a-139">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
