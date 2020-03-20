---
title: Migrowanie z programu .NET Remoting do programu WCF
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: 8dcc019017195fd55231fbea3493d4c53d500cb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183962"
---
# <a name="migrating-from-net-remoting-to-wcf"></a><span data-ttu-id="f570e-102">Migrowanie z programu .NET Remoting do programu WCF</span><span class="sxs-lookup"><span data-stu-id="f570e-102">Migrating from .NET Remoting to WCF</span></span>
<span data-ttu-id="f570e-103">W tym artykule opisano sposób migracji aplikacji, która używa programu .NET Remoting do używania programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f570e-103">This article describes how to migrate an application that uses .NET Remoting to use Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="f570e-104">Porównuje podobne pojęcia między tymi produktami, a następnie opisuje, jak wykonać kilka typowych scenariuszy komunikacji zdalnej w WCF.</span><span class="sxs-lookup"><span data-stu-id="f570e-104">It compares similar concepts between these products and then describes how to accomplish several common Remoting scenarios in WCF.</span></span>  
  
 <span data-ttu-id="f570e-105">.NET Remoting jest starszy produkt, który jest obsługiwany tylko dla zgodności z powrotem.</span><span class="sxs-lookup"><span data-stu-id="f570e-105">.NET Remoting is a legacy product that is supported only for backward compatibility.</span></span> <span data-ttu-id="f570e-106">Nie jest bezpieczny w środowiskach zaufania mieszanego, ponieważ nie może utrzymać oddzielnych poziomów zaufania między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="f570e-106">It is not secure across mixed-trust environments because it cannot maintain the separate trust levels between client and server.</span></span> <span data-ttu-id="f570e-107">Na przykład nigdy nie należy udostępniać punktu końcowego .NET Remoting do Internetu lub niezaufanych klientów.</span><span class="sxs-lookup"><span data-stu-id="f570e-107">For example, you should never expose a .NET Remoting endpoint to the Internet or to untrusted clients.</span></span> <span data-ttu-id="f570e-108">Firma Microsoft zaleca, aby istniejące aplikacje komunikacji zdalnej były migrowane do nowszych i bezpieczniejszych technologii.</span><span class="sxs-lookup"><span data-stu-id="f570e-108">We recommend existing Remoting applications be migrated to newer and more secure technologies.</span></span> <span data-ttu-id="f570e-109">Jeśli projekt aplikacji używa tylko protokołu HTTP i jest restful, zalecamy ASP.NET interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f570e-109">If the application’s design uses only HTTP and is RESTful, we recommend ASP.NET Web API.</span></span> <span data-ttu-id="f570e-110">Aby uzyskać więcej informacji, zobacz ASP.NET interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f570e-110">For more information, see ASP.NET Web API.</span></span> <span data-ttu-id="f570e-111">Jeśli aplikacja jest oparta na soap lub wymaga protokołów innych niż Http, takich jak TCP, zaleca się WCF.</span><span class="sxs-lookup"><span data-stu-id="f570e-111">If the application is based on SOAP or requires non-Http protocols such as TCP, we recommend WCF.</span></span>  

## <a name="comparing-net-remoting-to-wcf"></a><span data-ttu-id="f570e-112">Porównywanie komunikacji zdalnej .NET z WCF</span><span class="sxs-lookup"><span data-stu-id="f570e-112">Comparing .NET Remoting to WCF</span></span>  
 <span data-ttu-id="f570e-113">W tej sekcji porównuje podstawowe bloki konstrukcyjne .NET Remoting z ich odpowiednikami WCF.</span><span class="sxs-lookup"><span data-stu-id="f570e-113">This section compares the basic building blocks of .NET Remoting with their WCF equivalents.</span></span> <span data-ttu-id="f570e-114">Użyjemy tych bloków konstrukcyjnych później do utworzenia niektórych typowych scenariuszy klient-serwer w WCF.</span><span class="sxs-lookup"><span data-stu-id="f570e-114">We will use these building blocks later to create some common client-server scenarios in WCF.</span></span> <span data-ttu-id="f570e-115">Na poniższym wykresie podsumowano główne podobieństwa i różnice między .NET Remoting i WCF.</span><span class="sxs-lookup"><span data-stu-id="f570e-115">The following chart summarizes the main similarities and differences between .NET Remoting and WCF.</span></span>  
  
||<span data-ttu-id="f570e-116">Wywołaniem funkcji zdalnych .NET</span><span class="sxs-lookup"><span data-stu-id="f570e-116">.NET Remoting</span></span>|<span data-ttu-id="f570e-117">WCF</span><span class="sxs-lookup"><span data-stu-id="f570e-117">WCF</span></span>|  
|-|-------------------|---------|  
|<span data-ttu-id="f570e-118">Typ serwera</span><span class="sxs-lookup"><span data-stu-id="f570e-118">Server type</span></span>|<span data-ttu-id="f570e-119">Podklasa MarshalByRefObject</span><span class="sxs-lookup"><span data-stu-id="f570e-119">Subclass MarshalByRefObject</span></span>|<span data-ttu-id="f570e-120">Oznacz za pomocą atrybutu [ServiceContract]</span><span class="sxs-lookup"><span data-stu-id="f570e-120">Mark with [ServiceContract] attribute</span></span>|  
|<span data-ttu-id="f570e-121">Operacje serwisowe</span><span class="sxs-lookup"><span data-stu-id="f570e-121">Service operations</span></span>|<span data-ttu-id="f570e-122">Metody publiczne typu serwera</span><span class="sxs-lookup"><span data-stu-id="f570e-122">Public methods on server type</span></span>|<span data-ttu-id="f570e-123">Oznacz za pomocą atrybutu [OperationContract]</span><span class="sxs-lookup"><span data-stu-id="f570e-123">Mark with [OperationContract] attribute</span></span>|  
|<span data-ttu-id="f570e-124">Serializacja</span><span class="sxs-lookup"><span data-stu-id="f570e-124">Serialization</span></span>|<span data-ttu-id="f570e-125">ISerializable lub [Serializable]</span><span class="sxs-lookup"><span data-stu-id="f570e-125">ISerializable or [Serializable]</span></span>|<span data-ttu-id="f570e-126">DataContractSerializer lub XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="f570e-126">DataContractSerializer or XmlSerializer</span></span>|  
|<span data-ttu-id="f570e-127">Obiekty przekazywane</span><span class="sxs-lookup"><span data-stu-id="f570e-127">Objects passed</span></span>|<span data-ttu-id="f570e-128">Wartość według wartości lub odwołanie</span><span class="sxs-lookup"><span data-stu-id="f570e-128">By-value or by-reference</span></span>|<span data-ttu-id="f570e-129">Tylko wartość według wartości</span><span class="sxs-lookup"><span data-stu-id="f570e-129">By-value only</span></span>|  
|<span data-ttu-id="f570e-130">Błędy/wyjątki</span><span class="sxs-lookup"><span data-stu-id="f570e-130">Errors/exceptions</span></span>|<span data-ttu-id="f570e-131">Dowolny wyjątek, który można szeregizać</span><span class="sxs-lookup"><span data-stu-id="f570e-131">Any serializable exception</span></span>|<span data-ttu-id="f570e-132">> faultcontract\<TDetail</span><span class="sxs-lookup"><span data-stu-id="f570e-132">FaultContract\<TDetail></span></span>|  
|<span data-ttu-id="f570e-133">Obiekty serwera proxy klienta</span><span class="sxs-lookup"><span data-stu-id="f570e-133">Client proxy objects</span></span>|<span data-ttu-id="f570e-134">Silnie wpisane przezroczyste serwery proxy są tworzone automatycznie z MarshalByRefObjects</span><span class="sxs-lookup"><span data-stu-id="f570e-134">Strongly typed transparent proxies are created automatically from MarshalByRefObjects</span></span>|<span data-ttu-id="f570e-135">Silnie typizowane serwery proxy są generowane na\<żądanie przy użyciu kanału ChannelFactory TChannel></span><span class="sxs-lookup"><span data-stu-id="f570e-135">Strongly typed proxies are generated on-demand using ChannelFactory\<TChannel></span></span>|  
|<span data-ttu-id="f570e-136">Wymagana platforma</span><span class="sxs-lookup"><span data-stu-id="f570e-136">Platform required</span></span>|<span data-ttu-id="f570e-137">Zarówno klient, jak i serwer muszą używać systemu operacyjnego Microsoft I .NET</span><span class="sxs-lookup"><span data-stu-id="f570e-137">Both client and server must use Microsoft OS and .NET</span></span>|<span data-ttu-id="f570e-138">Wieloplatformowość</span><span class="sxs-lookup"><span data-stu-id="f570e-138">Cross-platform</span></span>|  
|<span data-ttu-id="f570e-139">Format wiadomości</span><span class="sxs-lookup"><span data-stu-id="f570e-139">Message format</span></span>|<span data-ttu-id="f570e-140">Private</span><span class="sxs-lookup"><span data-stu-id="f570e-140">Private</span></span>|<span data-ttu-id="f570e-141">Normy branżowe (SOAP, WS-\*, itp.)</span><span class="sxs-lookup"><span data-stu-id="f570e-141">Industry standards (SOAP, WS-\*, etc.)</span></span>|  
  
### <a name="server-implementation-comparison"></a><span data-ttu-id="f570e-142">Porównanie implementacji serwera</span><span class="sxs-lookup"><span data-stu-id="f570e-142">Server Implementation Comparison</span></span>  
  
#### <a name="creating-a-server-in-net-remoting"></a><span data-ttu-id="f570e-143">Tworzenie serwera w systemie remoting .NET</span><span class="sxs-lookup"><span data-stu-id="f570e-143">Creating a Server in .NET Remoting</span></span>  
 <span data-ttu-id="f570e-144">.NET Typy serwerów remoting musi pochodzić z MarshalByRefObject i zdefiniować metody, które klient może wywołać, jak poniżej:</span><span class="sxs-lookup"><span data-stu-id="f570e-144">.NET Remoting server types must derive from MarshalByRefObject and define methods the client can call, like the following:</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="f570e-145">Publiczne metody tego typu serwera stają się kontraktem publicznym dostępnym dla klientów.</span><span class="sxs-lookup"><span data-stu-id="f570e-145">The public methods of this server type become the public contract available to clients.</span></span>  <span data-ttu-id="f570e-146">Nie ma separacji między interfejsem publicznym serwera i jego implementacji — jeden typ obsługuje zarówno.</span><span class="sxs-lookup"><span data-stu-id="f570e-146">There is no separation between the server’s public interface and its implementation – one type handles both.</span></span>  
  
 <span data-ttu-id="f570e-147">Po zdefiniowaniu typu serwera można go udostępnić klientom, na przykład w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f570e-147">Once the server type has been defined, it can be made available to clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel(8080);  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingConfiguration.RegisterWellKnownServiceType(  
    typeof(RemotingServer),
    "RemotingServer",
    WellKnownObjectMode.Singleton);  
Console.WriteLine("RemotingServer is running.  Press ENTER to terminate...");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="f570e-148">Istnieje wiele sposobów, aby udostępnić typ komunikacji zdalnej jako serwer, w tym przy użyciu plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f570e-148">There are many ways to make the Remoting type available as a server, including using configuration files.</span></span> <span data-ttu-id="f570e-149">To tylko jeden z przykładów.</span><span class="sxs-lookup"><span data-stu-id="f570e-149">This is just one example.</span></span>  
  
#### <a name="creating-a-server-in-wcf"></a><span data-ttu-id="f570e-150">Tworzenie serwera w WCF</span><span class="sxs-lookup"><span data-stu-id="f570e-150">Creating a Server in WCF</span></span>  
 <span data-ttu-id="f570e-151">Równoważny krok w WCF polega na utworzeniu dwóch typów - publicznego "umowy o świadczenie usług" i konkretnej implementacji.</span><span class="sxs-lookup"><span data-stu-id="f570e-151">The equivalent step in WCF involves creating two types -- the public "service contract" and the concrete implementation.</span></span> <span data-ttu-id="f570e-152">Pierwszy jest zadeklarowany jako interfejs oznaczony jako [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="f570e-152">The first is declared as an interface marked with [ServiceContract].</span></span> <span data-ttu-id="f570e-153">Metody dostępne dla klientów są oznaczone symbolem [OperationContract]:</span><span class="sxs-lookup"><span data-stu-id="f570e-153">Methods available to clients are marked with [OperationContract]:</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="f570e-154">Implementacja serwera jest zdefiniowana w osobnej konkretnej klasie, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f570e-154">The server’s implementation is defined in a separate concrete class, like in the following example:</span></span>  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="f570e-155">Po zdefiniowaniu tych typów serwer WCF może być udostępniony klientom, na przykład w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f570e-155">Once these types have been defined, the WCF server can be made available to clients, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
Uri baseAddress = new Uri("net.tcp://localhost:8000/wcfserver");  
  
using (ServiceHost serviceHost = new ServiceHost(typeof(WCFServer), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(IWCFServer), binding, baseAddress);  
    serviceHost.Open();  
  
    Console.WriteLine($"The WCF server is ready at {baseAddress}.");
    Console.WriteLine("Press <ENTER> to terminate service...");  
    Console.WriteLine();  
    Console.ReadLine();  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="f570e-156">Protokół TCP jest używany w obu przykładach, aby zachować je tak podobne, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="f570e-156">TCP is used in both examples to keep them as similar as possible.</span></span> <span data-ttu-id="f570e-157">Zapoznaj się z for-ów scenariusz w dalszej części tego tematu na przykłady przy użyciu protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f570e-157">Refer to the scenario walk-throughs later in this topic for examples using HTTP.</span></span>  
  
 <span data-ttu-id="f570e-158">Istnieje wiele sposobów konfigurowania i hostować usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="f570e-158">There are many ways to configure and to host WCF services.</span></span> <span data-ttu-id="f570e-159">Jest to tylko jeden z przykładów, znany jako "self-hosted".</span><span class="sxs-lookup"><span data-stu-id="f570e-159">This is just one example, known as "self-hosted".</span></span> <span data-ttu-id="f570e-160">Aby uzyskać więcej informacji, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="f570e-160">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="f570e-161">Instrukcje: definiowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="f570e-161">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)  
  
- [<span data-ttu-id="f570e-162">Konfigurowanie usług za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f570e-162">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
  
- [<span data-ttu-id="f570e-163">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="f570e-163">Hosting Services</span></span>](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a><span data-ttu-id="f570e-164">Porównanie implementacji klienta</span><span class="sxs-lookup"><span data-stu-id="f570e-164">Client Implementation Comparison</span></span>  
  
#### <a name="creating-a-client-in-net-remoting"></a><span data-ttu-id="f570e-165">Tworzenie klienta w sieci .NET Remoting</span><span class="sxs-lookup"><span data-stu-id="f570e-165">Creating a Client in .NET Remoting</span></span>  
 <span data-ttu-id="f570e-166">Po udostępnieniu obiektu serwera remotingu .NET może on być zużywany przez klientów, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f570e-166">Once a .NET Remoting server object has been made available, it can be consumed by clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 <span data-ttu-id="f570e-167">RemotingServer wystąpienie zwrócone z Activator.GetObject() jest znany jako "przezroczysty serwer proxy."</span><span class="sxs-lookup"><span data-stu-id="f570e-167">The RemotingServer instance returned from Activator.GetObject() is known as a "transparent proxy."</span></span> <span data-ttu-id="f570e-168">Implementuje publiczny interfejs API dla typu RemotingServer na kliencie, ale wszystkie metody wywołać obiekt serwera uruchomiony w innym procesie lub komputerze.</span><span class="sxs-lookup"><span data-stu-id="f570e-168">It implements the public API for the RemotingServer type on the client, but all the methods call the server object running in a different process or machine.</span></span>  
  
#### <a name="creating-a-client-in-wcf"></a><span data-ttu-id="f570e-169">Tworzenie klienta w WCF</span><span class="sxs-lookup"><span data-stu-id="f570e-169">Creating a Client in WCF</span></span>  
 <span data-ttu-id="f570e-170">Równoważny krok w WCF polega na użyciu fabryki kanałów, aby utworzyć serwer proxy jawnie.</span><span class="sxs-lookup"><span data-stu-id="f570e-170">The equivalent step in WCF involves using a channel factory to create the proxy explicitly.</span></span> <span data-ttu-id="f570e-171">Podobnie jak funkcja komunikacji zdalnej, obiekt proxy może służyć do wywoływania operacji na serwerze, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f570e-171">Like Remoting, the proxy object can be used to invoke operations on the server, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
String url = "net.tcp://localhost:8000/wcfserver";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<IWCFServer> channelFactory =
    new ChannelFactory<IWCFServer>(binding, address);  
IWCFServer server = channelFactory.CreateChannel();  
  
Customer customer = server.GetCustomer(42);  
Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 <span data-ttu-id="f570e-172">W tym przykładzie pokazano programowania na poziomie kanału, ponieważ jest najbardziej podobny do przykładu komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="f570e-172">This example shows programming at the channel level because it is most similar to the Remoting example.</span></span> <span data-ttu-id="f570e-173">Dostępne jest również **podejście Dodaj odwołanie do usługi** w programie Visual Studio, które generuje kod w celu uproszczenia programowania klienta.</span><span class="sxs-lookup"><span data-stu-id="f570e-173">Also available is the **Add Service Reference** approach in Visual Studio that generates code to simplify client programming.</span></span> <span data-ttu-id="f570e-174">Aby uzyskać więcej informacji, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="f570e-174">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="f570e-175">Programowanie na poziomie kanału klienta</span><span class="sxs-lookup"><span data-stu-id="f570e-175">Client Channel-Level Programming</span></span>](./extending/client-channel-level-programming.md)  
  
- [<span data-ttu-id="f570e-176">Jak: Dodawanie, aktualizowanie lub usuwanie odwołania do usługi</span><span class="sxs-lookup"><span data-stu-id="f570e-176">How to: Add, Update, or Remove a Service Reference</span></span>](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a><span data-ttu-id="f570e-177">Użycie serializacji</span><span class="sxs-lookup"><span data-stu-id="f570e-177">Serialization Usage</span></span>  
 <span data-ttu-id="f570e-178">Zarówno .NET Remoting i WCF używać serializacji do wysyłania obiektów między klientem a serwerem, ale różnią się one w tych ważnych sposobów:</span><span class="sxs-lookup"><span data-stu-id="f570e-178">Both .NET Remoting and WCF use serialization to send objects between client and server, but they differ in these important ways:</span></span>  
  
1. <span data-ttu-id="f570e-179">Używają różnych serializatorów i konwencji, aby wskazać, co do serializacji.</span><span class="sxs-lookup"><span data-stu-id="f570e-179">They use different serializers and conventions to indicate what to serialize.</span></span>  
  
2. <span data-ttu-id="f570e-180">.NET Remoting obsługuje serializacji "przez odwołanie", która umożliwia dostęp do metody lub właściwości w jednej warstwie do wykonania kodu w drugiej warstwie, która znajduje się poza granicami zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f570e-180">.NET Remoting supports "by reference" serialization that allows method or property access on one tier to execute code on the other tier, which is across security boundaries.</span></span> <span data-ttu-id="f570e-181">Ta funkcja uwidacznia luki w zabezpieczeniach i jest jednym z głównych powodów, dla których punkty końcowe komunikacji zdalnej nigdy nie powinny być narażone na niezaufanych klientów.</span><span class="sxs-lookup"><span data-stu-id="f570e-181">This capability exposes security vulnerabilities and is one of the main reasons why Remoting endpoints should never be exposed to untrusted clients.</span></span>  
  
3. <span data-ttu-id="f570e-182">Serializacja używana przez remoting jest opt-out (jawnie wykluczyć, co nie serializacji) i WCF serializacji jest opt-in (jawnie oznaczyć, które elementy członkowskie do serializacji).</span><span class="sxs-lookup"><span data-stu-id="f570e-182">Serialization used by Remoting is opt-out (explicitly exclude what not to serialize) and WCF serialization is opt-in (explicitly mark which members to serialize).</span></span>  
  
#### <a name="serialization-in-net-remoting"></a><span data-ttu-id="f570e-183">Serializacja w .NET Remoting</span><span class="sxs-lookup"><span data-stu-id="f570e-183">Serialization in .NET Remoting</span></span>  
 <span data-ttu-id="f570e-184">Funkcja .NET Remoting obsługuje dwa sposoby serializacji i deserializacji obiektów między klientem a serwerem:</span><span class="sxs-lookup"><span data-stu-id="f570e-184">.NET Remoting supports two ways to serialize and deserialize objects between the client and server:</span></span>  
  
- <span data-ttu-id="f570e-185">*Według wartości* — wartości obiektu są serializowane między granicami warstwy, a nowe wystąpienie tego obiektu jest tworzone w innej warstwie.</span><span class="sxs-lookup"><span data-stu-id="f570e-185">*By value* – the values of the object are serialized across tier boundaries, and a new instance of that object is created on the other tier.</span></span> <span data-ttu-id="f570e-186">Wszelkie wywołania metod lub właściwości tego nowego wystąpienia są wykonywane tylko lokalnie i nie mają wpływu na oryginalny obiekt lub warstwę.</span><span class="sxs-lookup"><span data-stu-id="f570e-186">Any calls to methods or properties of that new instance execute only locally and do not affect the original object or tier.</span></span>  
  
- <span data-ttu-id="f570e-187">*Przez odwołanie* — specjalne "odwołanie do obiektu" jest serializowane w granicach warstwy.</span><span class="sxs-lookup"><span data-stu-id="f570e-187">*By reference* – a special "object reference" is serialized across tier boundaries.</span></span> <span data-ttu-id="f570e-188">Gdy jedna warstwa współdziała z metodami lub właściwościami tego obiektu, komunikuje się z powrotem do oryginalnego obiektu w oryginalnej warstwie.</span><span class="sxs-lookup"><span data-stu-id="f570e-188">When one tier interacts with methods or properties of that object, it communicates back to the original object on the original tier.</span></span> <span data-ttu-id="f570e-189">Obiekty według odwołania mogą przepływać w każdym kierunku — serwer do klienta lub klient do serwera.</span><span class="sxs-lookup"><span data-stu-id="f570e-189">By-reference objects can flow in either direction – server to client, or client to server.</span></span>  
  
 <span data-ttu-id="f570e-190">Typy według wartości w remoting są oznaczone atrybutem [Serializable] lub implementują ISerializable, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f570e-190">By-value types in Remoting are marked with the [Serializable] attribute or implement ISerializable, like in the following example:</span></span>  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="f570e-191">Typy według odwołań pochodzą z MarshalByRefObject klasy, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f570e-191">By-reference types derive from the MarshalByRefObject class, like in the following example:</span></span>  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="f570e-192">Jest niezwykle ważne, aby zrozumieć implikacje remoting przez odniesienia obiektów.</span><span class="sxs-lookup"><span data-stu-id="f570e-192">It is extremely important to understand the implications of Remoting’s by-reference objects.</span></span> <span data-ttu-id="f570e-193">Jeśli warstwa (klient lub serwer) wysyła obiekt według odwołania do innej warstwy, wszystkie wywołania metody są wykonywane z powrotem w warstwie posiadającej obiekt.</span><span class="sxs-lookup"><span data-stu-id="f570e-193">If either tier (client or server) sends a by-reference object to the other tier, all method calls execute back on the tier owning the object.</span></span> <span data-ttu-id="f570e-194">Na przykład metody wywołujące klienta na obiekcie odwołania zwróconego przez serwer będą wykonywać kod na serwerze.</span><span class="sxs-lookup"><span data-stu-id="f570e-194">For example, a client calling methods on a by-reference object returned by the server will execute code on the server.</span></span> <span data-ttu-id="f570e-195">Podobnie metody wywoływania serwera na obiektie według odwołania dostarczonych przez klienta wykona kod z powrotem na kliencie.</span><span class="sxs-lookup"><span data-stu-id="f570e-195">Similarly, a server calling methods on a by-reference object provided by the client will execute code back on the client.</span></span> <span data-ttu-id="f570e-196">Z tego powodu użycie funkcji .NET Remoting jest zalecane tylko w w pełni zaufanych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="f570e-196">For this reason, the use of .NET Remoting is recommended only within fully-trusted environments.</span></span> <span data-ttu-id="f570e-197">Uwidacznianie publicznego punktu końcowego komunikacji zdalnej .NET na niezaufanych klientach spowoduje, że serwer komunikacji zdalnej będzie narażony na ataki.</span><span class="sxs-lookup"><span data-stu-id="f570e-197">Exposing a public .NET Remoting endpoint to untrusted clients will make a Remoting server vulnerable to attack.</span></span>  
  
#### <a name="serialization-in-wcf"></a><span data-ttu-id="f570e-198">Serializacja w WCF</span><span class="sxs-lookup"><span data-stu-id="f570e-198">Serialization in WCF</span></span>  
 <span data-ttu-id="f570e-199">WCF obsługuje tylko przez wartość serializacji.</span><span class="sxs-lookup"><span data-stu-id="f570e-199">WCF supports only by-value serialization.</span></span> <span data-ttu-id="f570e-200">Najczęstszym sposobem definiowania typu do wymiany między klientem a serwerem jest jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f570e-200">The most common way to define a type to exchange between client and server is like in the following example:</span></span>  
  
```csharp
[DataContract]  
public class WCFCustomer  
{  
    [DataMember]  
    public string FirstName { get; set; }  
  
    [DataMember]  
    public string LastName { get; set; }  
  
    [DataMember]  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="f570e-201">Atrybut [DataContract] identyfikuje ten typ jako taki, który może być serializowany i deserializowany między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="f570e-201">The [DataContract] attribute identifies this type as one that can be serialized and deserialized between client and server.</span></span> <span data-ttu-id="f570e-202">Atrybut [DataMember] identyfikuje poszczególne właściwości lub pola do serializacji.</span><span class="sxs-lookup"><span data-stu-id="f570e-202">The [DataMember] attribute identifies the individual properties or fields to serialize.</span></span>  
  
 <span data-ttu-id="f570e-203">Gdy WCF wysyła obiekt między warstwami, serializuje tylko wartości i tworzy nowe wystąpienie obiektu w innej warstwie.</span><span class="sxs-lookup"><span data-stu-id="f570e-203">When WCF sends an object across tiers, it serializes only the values and creates a new instance of the object on the other tier.</span></span> <span data-ttu-id="f570e-204">Wszelkie interakcje z wartościami obiektu występują tylko lokalnie — nie komunikują się z drugą warstwą sposób .NET Remoting przez odwołanie obiektów zrobić.</span><span class="sxs-lookup"><span data-stu-id="f570e-204">Any interactions with the values of the object occur only locally – they do not communicate with the other tier the way .NET Remoting by-reference objects do.</span></span> <span data-ttu-id="f570e-205">Aby uzyskać więcej informacji, zobacz [Serializacja i deserializacja](./feature-details/serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="f570e-205">For more information, see [Serialization and Deserialization](./feature-details/serialization-and-deserialization.md).</span></span>  
  
### <a name="exception-handling-capabilities"></a><span data-ttu-id="f570e-206">Możliwości obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="f570e-206">Exception Handling Capabilities</span></span>  
  
#### <a name="exceptions-in-net-remoting"></a><span data-ttu-id="f570e-207">Wyjątki w obszarze .NET Remoting</span><span class="sxs-lookup"><span data-stu-id="f570e-207">Exceptions in .NET Remoting</span></span>  
 <span data-ttu-id="f570e-208">Wyjątki generowane przez serwer komunikacji zdalnej są serializowane, wysyłane do klienta i generowane lokalnie na kliencie, jak każdy inny wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f570e-208">Exceptions thrown by a Remoting server are serialized, sent to the client, and thrown locally on the client like any other exception.</span></span> <span data-ttu-id="f570e-209">Wyjątki niestandardowe można utworzyć, klasyfikując typ wyjątku i oznaczając go za pomocą [Serializable].</span><span class="sxs-lookup"><span data-stu-id="f570e-209">Custom exceptions can be created by sub-classing the Exception type and marking it with [Serializable].</span></span>   <span data-ttu-id="f570e-210">Większość wyjątków framework są już oznaczone w ten sposób, dzięki czemu większość być generowane przez serwer, serializowane i ponownie generowane na kliencie.</span><span class="sxs-lookup"><span data-stu-id="f570e-210">Most framework exceptions are already marked in this way, allowing most to be thrown by the server, serialized, and re-thrown on the client.</span></span> <span data-ttu-id="f570e-211">Chociaż ten projekt jest wygodny podczas tworzenia, informacje po stronie serwera mogą przypadkowo zostać ujawnione klientowi.</span><span class="sxs-lookup"><span data-stu-id="f570e-211">Though this design is convenient during development, server-side information can inadvertently be disclosed to the client.</span></span> <span data-ttu-id="f570e-212">Jest to jeden z wielu powodów, dla których program komunikacji zdalnej powinien być używany tylko w w pełni zaufanych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="f570e-212">This is one of many reasons Remoting should be used only in fully-trusted environments.</span></span>  
  
#### <a name="exceptions-and-faults-in-wcf"></a><span data-ttu-id="f570e-213">Wyjątki i usterki w WCF</span><span class="sxs-lookup"><span data-stu-id="f570e-213">Exceptions and Faults in WCF</span></span>  
 <span data-ttu-id="f570e-214">WCF nie zezwala na arbitralne typy wyjątków mają być zwracane z serwera do klienta, ponieważ może to prowadzić do niezamierzonego ujawnienia informacji.</span><span class="sxs-lookup"><span data-stu-id="f570e-214">WCF does not allow arbitrary exception types to be returned from the server to the client because it could lead to inadvertent information disclosure.</span></span> <span data-ttu-id="f570e-215">Jeśli operacja usługi zgłasza nieoczekiwany wyjątek, powoduje, że ogólne przeznaczenie FaultException do rzuconego na klienta.</span><span class="sxs-lookup"><span data-stu-id="f570e-215">If a service operation throws an unexpected exception, it causes a general purpose FaultException to be thrown on the client.</span></span> <span data-ttu-id="f570e-216">Ten wyjątek nie zawiera żadnych informacji, dlaczego i gdzie wystąpił problem, a dla niektórych aplikacji jest to wystarczające.</span><span class="sxs-lookup"><span data-stu-id="f570e-216">This exception does not carry any information why or where the problem occurred, and for some applications this is sufficient.</span></span> <span data-ttu-id="f570e-217">Aplikacje, które muszą komunikować się z klientem bogatsze informacje o błędach, robią to, definiując kontrakt o usterki.</span><span class="sxs-lookup"><span data-stu-id="f570e-217">Applications that need to communicate richer error information to the client do this by defining a fault contract.</span></span>  
  
 <span data-ttu-id="f570e-218">Aby to zrobić, należy najpierw utworzyć typ [DataContract] do przenoszenia informacji o usterce.</span><span class="sxs-lookup"><span data-stu-id="f570e-218">To do this, first create a [DataContract] type to carry the fault information.</span></span>  
  
```csharp
[DataContract]  
public class CustomerServiceFault  
{  
    [DataMember]  
    public string ErrorMessage { get; set; }  
  
    [DataMember]  
    public int CustomerId {get;set;}  
}  
```  
  
 <span data-ttu-id="f570e-219">Określ kontrakt błędów do użycia dla każdej operacji serwisu.</span><span class="sxs-lookup"><span data-stu-id="f570e-219">Specify the fault contract to use for each service operation.</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="f570e-220">Serwer zgłasza warunki błędu, rzucając FaultException.</span><span class="sxs-lookup"><span data-stu-id="f570e-220">The server reports error conditions by throwing a FaultException.</span></span>  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {
        CustomerId = customerId,
        ErrorMessage = "Illegal customer Id"
    });  
```  
  
 <span data-ttu-id="f570e-221">I za każdym razem, gdy klient wysyła żądanie do serwera, może przechwytywać błędy jako normalne wyjątki.</span><span class="sxs-lookup"><span data-stu-id="f570e-221">And whenever the client makes a request to the server, it can catch faults as normal exceptions.</span></span>  
  
```csharp
try  
{  
    Customer customer = server.GetCustomer(-1);  
}  
catch (FaultException<CustomerServiceFault> fault)  
{  
    Console.WriteLine($"Fault received: {fault.Detail.ErrorMessage}");
}  
```  
  
 <span data-ttu-id="f570e-222">Aby uzyskać więcej informacji <xref:System.ServiceModel.FaultException>na temat kontraktów usterek, zobacz .</span><span class="sxs-lookup"><span data-stu-id="f570e-222">For more information about fault contracts, see <xref:System.ServiceModel.FaultException>.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="f570e-223">Zagadnienia związane z zabezpieczeniami</span><span class="sxs-lookup"><span data-stu-id="f570e-223">Security Considerations</span></span>  
  
#### <a name="security-in-net-remoting"></a><span data-ttu-id="f570e-224">Zabezpieczenia w komunikacji zdalnej .NET</span><span class="sxs-lookup"><span data-stu-id="f570e-224">Security in .NET Remoting</span></span>  
 <span data-ttu-id="f570e-225">Niektóre kanały komunikacji zdalnej platformy .NET obsługują funkcje zabezpieczeń, takie jak uwierzytelnianie i szyfrowanie w warstwie kanału (IPC i TCP).</span><span class="sxs-lookup"><span data-stu-id="f570e-225">Some .NET Remoting channels support security features such as authentication and encryption at the channel layer (IPC and TCP).</span></span> <span data-ttu-id="f570e-226">Kanał HTTP opiera się na internetowych usługach informacyjnych (IIS) zarówno do uwierzytelniania, jak i szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="f570e-226">The HTTP channel relies on Internet Information Services (IIS) for both authentication and encryption.</span></span> <span data-ttu-id="f570e-227">Pomimo tej pomocy należy rozważyć .NET Remoting niezabezpieczony protokół komunikacyjny i używać go tylko w w pełni zaufanych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="f570e-227">Despite this support, you should consider .NET Remoting an unsecure communication protocol and use it only within fully-trusted environments.</span></span> <span data-ttu-id="f570e-228">Nigdy nie udostępniaj publicznego punktu końcowego komunikacji zdalnej w Internecie lub niezaufanych klientów.</span><span class="sxs-lookup"><span data-stu-id="f570e-228">Never expose a public Remoting endpoint to the Internet or untrusted clients.</span></span>  
  
#### <a name="security-in-wcf"></a><span data-ttu-id="f570e-229">Zabezpieczenia w programie WCF</span><span class="sxs-lookup"><span data-stu-id="f570e-229">Security in WCF</span></span>  
 <span data-ttu-id="f570e-230">WCF został zaprojektowany z myślą o bezpieczeństwie, częściowo w celu wyeliminowania rodzajów luk znalezionych w .NET Remoting.</span><span class="sxs-lookup"><span data-stu-id="f570e-230">WCF was designed with security in mind, in part to address the kinds of vulnerabilities found in .NET Remoting.</span></span> <span data-ttu-id="f570e-231">WCF oferuje zabezpieczenia na poziomie transportu i wiadomości i oferuje wiele opcji uwierzytelniania, autoryzacji, szyfrowania i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="f570e-231">WCF offers security at both the transport and message level, and offers many options for authentication, authorization, encryption, and so on.</span></span> <span data-ttu-id="f570e-232">Aby uzyskać więcej informacji, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="f570e-232">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="f570e-233">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="f570e-233">Security</span></span>](./feature-details/security.md)  
  
- [<span data-ttu-id="f570e-234">Wskazówki dotyczące zabezpieczeń WCF</span><span class="sxs-lookup"><span data-stu-id="f570e-234">WCF Security Guidance</span></span>](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a><span data-ttu-id="f570e-235">Migracja do WCF</span><span class="sxs-lookup"><span data-stu-id="f570e-235">Migrating to WCF</span></span>  
  
### <a name="why-migrate-from-remoting-to-wcf"></a><span data-ttu-id="f570e-236">Dlaczego migracji z komunikacji zdalnej do WCF?</span><span class="sxs-lookup"><span data-stu-id="f570e-236">Why Migrate from Remoting to WCF?</span></span>  
  
- <span data-ttu-id="f570e-237">**.NET Remoting jest produktem starszej wersji.**</span><span class="sxs-lookup"><span data-stu-id="f570e-237">**.NET Remoting is a legacy product.**</span></span> <span data-ttu-id="f570e-238">Jak opisano w [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), jest uważany za produkt starszej wersji i nie jest zalecany do nowego rozwoju.</span><span class="sxs-lookup"><span data-stu-id="f570e-238">As described in [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), it is considered a legacy product and is not recommended for new development.</span></span> <span data-ttu-id="f570e-239">WCF lub ASP.NET web API są zalecane dla nowych i istniejących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f570e-239">WCF or ASP.NET Web API are recommended for new and existing applications.</span></span>  
  
- <span data-ttu-id="f570e-240">**WCF używa standardów międzyplatformowych.**</span><span class="sxs-lookup"><span data-stu-id="f570e-240">**WCF uses cross-platform standards.**</span></span> <span data-ttu-id="f570e-241">WCF został zaprojektowany z myślą o interoperacyjności między platformami i obsługuje wiele standardów branżowych (SOAP, WS-Security, WS-Trust itp.).</span><span class="sxs-lookup"><span data-stu-id="f570e-241">WCF was designed with cross-platform interoperability in mind and supports many industry standards (SOAP, WS-Security, WS-Trust, etc.).</span></span> <span data-ttu-id="f570e-242">Usługa WCF może współpracować z klientami działającymi w systemach operacyjnych innych niż Windows.</span><span class="sxs-lookup"><span data-stu-id="f570e-242">A WCF service can interoperate with clients running on operating systems other than Windows.</span></span> <span data-ttu-id="f570e-243">Komunikacji zdalnej został zaprojektowany przede wszystkim dla środowisk, w których zarówno serwer, jak i aplikacje klienckie są uruchamiane przy użyciu programu .NET Framework w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="f570e-243">Remoting was designed primarily for environments where both the server and client applications run using .NET Framework on a Windows operating system.</span></span>
  
- <span data-ttu-id="f570e-244">**WCF ma wbudowane zabezpieczenia.**</span><span class="sxs-lookup"><span data-stu-id="f570e-244">**WCF has built-in security.**</span></span> <span data-ttu-id="f570e-245">WCF został zaprojektowany z myślą o bezpieczeństwie i oferuje wiele opcji uwierzytelniania, bezpieczeństwa na poziomie transportu, zabezpieczeń na poziomie wiadomości itp. Komunikacji zdalnej został zaprojektowany, aby ułatwić aplikacjom współdziałanie, ale nie został zaprojektowany, aby być bezpieczne w środowiskach niezaufanych.</span><span class="sxs-lookup"><span data-stu-id="f570e-245">WCF was designed with security in mind and offers many options for authentication, transport level security, message level security, etc. Remoting was designed to make it easy for applications to interoperate but was not designed to be secure in non-trusted environments.</span></span> <span data-ttu-id="f570e-246">WCF został zaprojektowany do pracy w środowiskach zaufanych i niezaufanych.</span><span class="sxs-lookup"><span data-stu-id="f570e-246">WCF was designed to work in both trusted and non-trusted environments.</span></span>  
  
### <a name="migration-recommendations"></a><span data-ttu-id="f570e-247">Zalecenia dotyczące migracji</span><span class="sxs-lookup"><span data-stu-id="f570e-247">Migration Recommendations</span></span>  
 <span data-ttu-id="f570e-248">Poniżej przedstawiono zalecane kroki migracji z .NET Remoting do WCF:</span><span class="sxs-lookup"><span data-stu-id="f570e-248">The following are the recommended steps to migrate from .NET Remoting to WCF:</span></span>  
  
- <span data-ttu-id="f570e-249">**Utwórz umowę serwisową.**</span><span class="sxs-lookup"><span data-stu-id="f570e-249">**Create the service contract.**</span></span> <span data-ttu-id="f570e-250">Zdefiniuj typy interfejsów usługi i oznacz je atrybutem [ServiceContract]. Oznacz wszystkie metody, które klienci będą mogli wywołać za pomocą [OperationContract].</span><span class="sxs-lookup"><span data-stu-id="f570e-250">Define your service interface types, and mark them with the [ServiceContract] attribute.Mark all the methods the clients will be allowed to call with [OperationContract].</span></span>  
  
- <span data-ttu-id="f570e-251">**Utwórz kontrakt na dane.**</span><span class="sxs-lookup"><span data-stu-id="f570e-251">**Create the data contract.**</span></span> <span data-ttu-id="f570e-252">Zdefiniuj typy danych, które będą wymieniane między serwerem a klientem, i oznacz je atrybutem [DataContract].</span><span class="sxs-lookup"><span data-stu-id="f570e-252">Define the data types that will be exchanged between server and client, and mark them with the [DataContract] attribute.</span></span> <span data-ttu-id="f570e-253">Zaznacz wszystkie pola i właściwości, których klient będzie mógł używać z programem [DataMember].</span><span class="sxs-lookup"><span data-stu-id="f570e-253">Mark all the fields and properties the client will be allowed to use with [DataMember].</span></span>  
  
- <span data-ttu-id="f570e-254">**Utwórz kontrakt na usterkę (opcjonalnie).**</span><span class="sxs-lookup"><span data-stu-id="f570e-254">**Create the fault contract (optional).**</span></span> <span data-ttu-id="f570e-255">Utwórz typy, które będą wymieniane między serwerem a klientem po napotkaniu błędów.</span><span class="sxs-lookup"><span data-stu-id="f570e-255">Create the types that will be exchanged between server and client when errors are encountered.</span></span> <span data-ttu-id="f570e-256">Oznacz te typy za pomocą [DataContract] i [DataMember], aby były serializowalne.</span><span class="sxs-lookup"><span data-stu-id="f570e-256">Mark these types with [DataContract] and [DataMember] to make them serializable.</span></span> <span data-ttu-id="f570e-257">Dla wszystkich operacji usługi oznaczone jako [OperationContract], również oznaczyć je z [FaultContract], aby wskazać, które błędy mogą zwracać.</span><span class="sxs-lookup"><span data-stu-id="f570e-257">For all service operations you marked with [OperationContract], also mark them with [FaultContract] to indicate which errors they may return.</span></span>  
  
- <span data-ttu-id="f570e-258">**Konfigurowanie i hostowania usługi.**</span><span class="sxs-lookup"><span data-stu-id="f570e-258">**Configure and host the service.**</span></span> <span data-ttu-id="f570e-259">Po utworzeniu umowy serwisowej następnym krokiem jest skonfigurowanie powiązania, aby udostępnić usługę w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="f570e-259">Once the service contract has been created, the next step is to configure a binding to expose the service at an endpoint.</span></span> <span data-ttu-id="f570e-260">Aby uzyskać więcej informacji, zobacz [Punkty końcowe: Adresy, Powiązania i Kontrakty](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="f570e-260">For more information, see [Endpoints: Addresses, Bindings, and Contracts](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span></span>  
  
 <span data-ttu-id="f570e-261">Po migracji aplikacji komunikacji zdalnej do WCF, nadal ważne jest, aby usunąć zależności na .NET Komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="f570e-261">Once a Remoting application has been migrated to WCF, it is still important to remove dependencies on .NET Remoting.</span></span> <span data-ttu-id="f570e-262">Gwarantuje to, że wszelkie luki w zabezpieczeniach są usuwane z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f570e-262">This ensures that any Remoting vulnerabilities are removed from the application.</span></span> <span data-ttu-id="f570e-263">Te kroki obejmują następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f570e-263">These steps include the following:</span></span>  
  
- <span data-ttu-id="f570e-264">**Zaprzestanie używania MarshalByRefObject.**</span><span class="sxs-lookup"><span data-stu-id="f570e-264">**Discontinue use of MarshalByRefObject.**</span></span> <span data-ttu-id="f570e-265">Typu MarshalByRefObject istnieje tylko dla komunikacji zdalnej i nie jest używany przez WCF.</span><span class="sxs-lookup"><span data-stu-id="f570e-265">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="f570e-266">Wszystkie typy aplikacji, które podklasy MarshalByRefObject powinny zostać usunięte lub zmienione.</span><span class="sxs-lookup"><span data-stu-id="f570e-266">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span>  
  
- <span data-ttu-id="f570e-267">**Zaprzestać używania [Serializable] i ISerializable.**</span><span class="sxs-lookup"><span data-stu-id="f570e-267">**Discontinue use of [Serializable] and ISerializable.**</span></span> <span data-ttu-id="f570e-268">Atrybut [Serializable] i interfejs ISerializable zostały pierwotnie zaprojektowane do serializacji typów w zaufanych środowiskach i są używane przez program Remoting.</span><span class="sxs-lookup"><span data-stu-id="f570e-268">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="f570e-269">Serializacja WCF zależy od typów oznaczonych jako [DataContract] i [DataMember].</span><span class="sxs-lookup"><span data-stu-id="f570e-269">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="f570e-270">Typy danych używane przez aplikację powinny być modyfikowane w celu użycia [DataContract] i nie używać funkcji ISerializable lub [Serializable].</span><span class="sxs-lookup"><span data-stu-id="f570e-270">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span>  
  
### <a name="migration-scenarios"></a><span data-ttu-id="f570e-271">Scenariusze migracji</span><span class="sxs-lookup"><span data-stu-id="f570e-271">Migration Scenarios</span></span>  
 <span data-ttu-id="f570e-272">Teraz zobaczmy, jak wykonać następujące typowe scenariusze komunikacji zdalnej w WCF:</span><span class="sxs-lookup"><span data-stu-id="f570e-272">Now let’s see how to accomplish the following common Remoting scenarios in WCF:</span></span>  
  
1. <span data-ttu-id="f570e-273">Serwer zwraca klientowi wartość po wartości obiektu</span><span class="sxs-lookup"><span data-stu-id="f570e-273">Server returns an object by-value to the client</span></span>  
  
2. <span data-ttu-id="f570e-274">Serwer zwraca obiekt przez odwołanie do klienta</span><span class="sxs-lookup"><span data-stu-id="f570e-274">Server returns an object by-reference to the client</span></span>  
  
3. <span data-ttu-id="f570e-275">Klient wysyła obiekt według wartości do serwera</span><span class="sxs-lookup"><span data-stu-id="f570e-275">Client sends an object by-value to the server</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f570e-276">Wysyłanie obiektu przez odwołanie od klienta do serwera nie jest dozwolone w WCF.</span><span class="sxs-lookup"><span data-stu-id="f570e-276">Sending an object by-reference from the client to the server is not allowed in WCF.</span></span>  
  
 <span data-ttu-id="f570e-277">Podczas odczytywania tych scenariuszy, załóżmy, że nasze interfejsy linii bazowej dla .NET Komunikacji zdalnej wyglądają jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f570e-277">When reading through these scenarios, assume our baseline interfaces for .NET Remoting look like the following example.</span></span> <span data-ttu-id="f570e-278">Implementacja .NET Remoting nie jest w tym miejscu ważne, ponieważ chcemy zilustrować tylko sposób używania WCF do implementowania równoważnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="f570e-278">The .NET Remoting implementation is not important here because we want to illustrate only how to use WCF to implement equivalent functionality.</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    // Demonstrates server returning object by-value  
    public Customer GetCustomer(int customerId) {…}  
  
    // Demonstrates server returning object by-reference  
    public CustomerReference GetCustomerReference(int customerId) {…}  
  
    // Demonstrates client passing object to server by-value  
    public bool UpdateCustomer(Customer customer) {…}  
}  
```  
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a><span data-ttu-id="f570e-279">Scenariusz 1.</span><span class="sxs-lookup"><span data-stu-id="f570e-279">Scenario 1: Service Returns an Object by Value</span></span>  
 <span data-ttu-id="f570e-280">W tym scenariuszu pokazano serwer zwraca obiekt do klienta według wartości.</span><span class="sxs-lookup"><span data-stu-id="f570e-280">This scenario demonstrates a server returning an object to the client by value.</span></span> <span data-ttu-id="f570e-281">WCF zawsze zwraca obiekty z serwera według wartości, więc następujące kroki po prostu opisują sposób tworzenia normalnej usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="f570e-281">WCF always returns objects from the server by value, so the following steps simply describe how to build a normal WCF service.</span></span>  
  
1. <span data-ttu-id="f570e-282">Rozpocznij od zdefiniowania interfejsu publicznego dla usługi WCF i oznacz go atrybutem [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="f570e-282">Start by defining a public interface for the WCF service and mark it with the [ServiceContract] attribute.</span></span> <span data-ttu-id="f570e-283">Używamy [OperationContract] do identyfikowania metod po stronie serwera, które nasz klient wywoła.</span><span class="sxs-lookup"><span data-stu-id="f570e-283">We use [OperationContract] to identify the server-side methods our client will call.</span></span>  
  
   ```csharp
   [ServiceContract]  
   public interface ICustomerService  
   {  
       [OperationContract]  
       Customer GetCustomer(int customerId);  
  
       [OperationContract]  
       bool UpdateCustomer(Customer customer);  
   }  
   ```  
  
2. <span data-ttu-id="f570e-284">Następnym krokiem jest utworzenie kontraktu danych dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f570e-284">The next step is to create the data contract for this service.</span></span> <span data-ttu-id="f570e-285">Robimy to, tworząc klasy (nie interfejsy) oznaczone atrybutem [DataContract].</span><span class="sxs-lookup"><span data-stu-id="f570e-285">We do this by creating classes (not interfaces) marked with the [DataContract] attribute.</span></span> <span data-ttu-id="f570e-286">Poszczególne właściwości lub pola, które chcemy być widoczne zarówno dla klienta, jak i dla serwera, są oznaczone symbolem [DataMember].</span><span class="sxs-lookup"><span data-stu-id="f570e-286">The individual properties or fields we want visible to both client and server are marked with [DataMember].</span></span> <span data-ttu-id="f570e-287">Jeśli chcemy, aby typy pochodne były dozwolone, musimy użyć [KnownType] atrybut do ich identyfikacji.</span><span class="sxs-lookup"><span data-stu-id="f570e-287">If we want derived types to be allowed, we must use the [KnownType] attribute to identify them.</span></span> <span data-ttu-id="f570e-288">Jedynymi typami WCF pozwoli być serializowane lub deserialized dla tej usługi są te w interfejsie usługi i tych "znanych typów".</span><span class="sxs-lookup"><span data-stu-id="f570e-288">The only types WCF will allow to be serialized or deserialized for this service are those in the service interface and these "known types".</span></span> <span data-ttu-id="f570e-289">Próba wymiany dowolnego innego typu, który nie znajduje się na tej liście, zostanie odrzucona.</span><span class="sxs-lookup"><span data-stu-id="f570e-289">Attempting to exchange any other type not in this list will be rejected.</span></span>  
  
   ```csharp
   [DataContract]  
   [KnownType(typeof(PremiumCustomer))]  
   public class Customer  
   {  
       [DataMember]  
       public string FirstName { get; set; }  
  
       [DataMember]  
       public string LastName { get; set; }  
  
       [DataMember]  
       public int CustomerId { get; set; }  
   }  
  
   [DataContract]  
   public class PremiumCustomer : Customer
   {  
       [DataMember]  
       public int AccountId { get; set; }  
   }  
   ```  
  
3. <span data-ttu-id="f570e-290">Następnie zapewniamy implementację interfejsu usługi.</span><span class="sxs-lookup"><span data-stu-id="f570e-290">Next, we provide the implementation for the service interface.</span></span>  
  
   ```csharp  
   public class CustomerService : ICustomerService  
   {  
       public Customer GetCustomer(int customerId)  
       {  
           // read from database  
       }  
  
       public bool UpdateCustomer(Customer customer)  
       {  
           // write to database  
       }  
   }  
   ```  
  
4. <span data-ttu-id="f570e-291">Aby uruchomić usługę WCF, musimy zadeklarować punkt końcowy, który udostępnia tego interfejsu usługi przy określonym adresie URL przy użyciu określonego powiązania WCF.</span><span class="sxs-lookup"><span data-stu-id="f570e-291">To run the WCF service, we need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="f570e-292">Zazwyczaj odbywa się to przez dodanie następujących sekcji do pliku web.config projektu serwera.</span><span class="sxs-lookup"><span data-stu-id="f570e-292">This is typically done by adding the following sections to the server project’s web.config file.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
5. <span data-ttu-id="f570e-293">Usługę WCF można następnie uruchomić z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="f570e-293">The WCF service can then be started with the following code:</span></span>  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     <span data-ttu-id="f570e-294">Po uruchomieniu tego ServiceHost używa pliku web.config do ustanowienia właściwej umowy, powiązania i punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f570e-294">When this ServiceHost is started, it uses the web.config file to establish the proper contract, binding and endpoint.</span></span> <span data-ttu-id="f570e-295">Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [Konfigurowanie usług przy użyciu plików konfiguracyjnych](./configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="f570e-295">For more information about configuration files, see [Configuring Services Using Configuration Files](./configuring-services-using-configuration-files.md).</span></span> <span data-ttu-id="f570e-296">Ten styl uruchamiania serwera jest znany jako własny hosting.</span><span class="sxs-lookup"><span data-stu-id="f570e-296">This style of starting the server is known as self-hosting.</span></span> <span data-ttu-id="f570e-297">Aby dowiedzieć się więcej o innych możliwościach obsługi usług WCF, zobacz [Usługi hostingowe](./hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="f570e-297">To learn more about other choices for hosting WCF services, see [Hosting Services](./hosting-services.md).</span></span>  
  
6. <span data-ttu-id="f570e-298">App.config projektu klienta musi zadeklarować pasujące informacje o powiązaniach dla punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="f570e-298">The client project’s app.config must declare matching binding information for the service’s endpoint.</span></span> <span data-ttu-id="f570e-299">Najprostszym sposobem, aby to zrobić w programie Visual Studio jest użycie **Dodaj service reference**, który automatycznie zaktualizuje plik app.config.</span><span class="sxs-lookup"><span data-stu-id="f570e-299">The easiest way to do this in Visual Studio is to use **Add Service Reference**, which will automatically update the app.config file.</span></span> <span data-ttu-id="f570e-300">Alternatywnie te same zmiany można dodać ręcznie.</span><span class="sxs-lookup"><span data-stu-id="f570e-300">Alternatively, these same changes can be added manually.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="f570e-301">Aby uzyskać więcej informacji na temat **używania dodatku odwołania do usługi,** zobacz [Jak: Dodawanie, aktualizowanie lub usuwanie odwołania do usługi](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span><span class="sxs-lookup"><span data-stu-id="f570e-301">For more information about using **Add Service Reference**, see [How to: Add, Update, or Remove a Service Reference](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span></span>  
  
7. <span data-ttu-id="f570e-302">Teraz możemy wywołać usługę WCF z klienta.</span><span class="sxs-lookup"><span data-stu-id="f570e-302">Now we can call the WCF service from the client.</span></span> <span data-ttu-id="f570e-303">Robimy to, tworząc fabrykę kanałów dla tej usługi, prosząc ją o kanał i bezpośrednio wywołując metodę, którą chcemy na tym kanale.</span><span class="sxs-lookup"><span data-stu-id="f570e-303">We do this by creating a channel factory for that service, asking it for a channel, and directly calling the method we want on that channel.</span></span> <span data-ttu-id="f570e-304">Możemy to zrobić, ponieważ kanał implementuje interfejs usługi i obsługuje podstawową logikę żądania/odpowiedzi dla nas.</span><span class="sxs-lookup"><span data-stu-id="f570e-304">We can do this because the channel implements the service’s interface and handles the underlying request/reply logic for us.</span></span> <span data-ttu-id="f570e-305">Zwracana wartość z tego wywołania metody jest deserializowanej kopii odpowiedzi serwera.</span><span class="sxs-lookup"><span data-stu-id="f570e-305">The return value from that method call is the deserialized copy of the server’s response.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 <span data-ttu-id="f570e-306">Obiekty zwracane przez WCF z serwera do klienta są zawsze według wartości.</span><span class="sxs-lookup"><span data-stu-id="f570e-306">Objects returned by WCF from the server to the client are always by value.</span></span> <span data-ttu-id="f570e-307">Obiekty są deserializowane kopie danych wysyłanych przez serwer.</span><span class="sxs-lookup"><span data-stu-id="f570e-307">The objects are deserialized copies of the data sent by the server.</span></span> <span data-ttu-id="f570e-308">Klient może wywołać metody na tych kopiach lokalnych bez żadnego niebezpieczeństwa wywoływania kodu serwera za pomocą wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="f570e-308">The client can call methods on these local copies without any danger of invoking server code through callbacks.</span></span>  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a><span data-ttu-id="f570e-309">Scenariusz 2: Serwer zwraca obiekt według odwołania</span><span class="sxs-lookup"><span data-stu-id="f570e-309">Scenario 2: Server Returns an Object By Reference</span></span>  
 <span data-ttu-id="f570e-310">W tym scenariuszu pokazano serwer dostarczanie obiektu do klienta przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f570e-310">This scenario demonstrates the server providing an object to the client by reference.</span></span> <span data-ttu-id="f570e-311">W .NET Remoting jest obsługiwany automatycznie dla dowolnego typu pochodzącego z MarshalByRefObject, który jest serializowany przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f570e-311">In .NET Remoting, this is handled automatically for any type derived from MarshalByRefObject, which is serialized by-reference.</span></span> <span data-ttu-id="f570e-312">Przykładem tego scenariusza jest umożliwienie wielu klientom mieć niezależne sesyjne obiekty po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="f570e-312">An example of this scenario is allowing multiple clients to have independent sessionful server-side objects.</span></span> <span data-ttu-id="f570e-313">Jak wcześniej wspomniano, obiekty zwracane przez usługę WCF są zawsze według wartości, więc nie ma bezpośredniego odpowiednika obiektu przez odwołanie, ale jest <xref:System.ServiceModel.EndpointAddress10> możliwe, aby osiągnąć coś podobnego do semantyki przez odwołanie za pomocą obiektu.</span><span class="sxs-lookup"><span data-stu-id="f570e-313">As previously mentioned, objects returned by a WCF service are always by value, so there is no direct equivalent of a by-reference object, but it is possible to achieve something similar to by-reference semantics using an <xref:System.ServiceModel.EndpointAddress10> object.</span></span> <span data-ttu-id="f570e-314">Jest to obiekt według wartości, który może być używany przez klienta do uzyskania sesyjnego obiektu po odwołań na serwerze.</span><span class="sxs-lookup"><span data-stu-id="f570e-314">This is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span> <span data-ttu-id="f570e-315">Dzięki temu scenariusz posiadania wielu klientów z niezależnymi obiektami po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="f570e-315">This enables the scenario of having multiple clients with independent sessionful server-side objects.</span></span>  
  
1. <span data-ttu-id="f570e-316">Po pierwsze musimy zdefiniować kontrakt serwisowy WCF, który odpowiada samego obiektu sessionful.</span><span class="sxs-lookup"><span data-stu-id="f570e-316">First, we need to define a WCF service contract that corresponds to the sessionful object itself.</span></span>  
  
   ```csharp
   [ServiceContract(SessionMode = SessionMode.Allowed)]  
       public interface ISessionBoundObject  
       {  
           [OperationContract]  
           string GetCurrentValue();  
  
           [OperationContract]  
           void SetCurrentValue(string value);  
       }  
   ```  
  
    > [!TIP]
    > <span data-ttu-id="f570e-317">Należy zauważyć, że obiekt sessionful jest oznaczony jako [ServiceContract], co czyni go normalnym interfejsem usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="f570e-317">Notice that the sessionful object is marked with [ServiceContract], making it a normal WCF service interface.</span></span> <span data-ttu-id="f570e-318">Ustawienie SessionMode właściwość wskazuje, że będzie to usługa sesyjna.</span><span class="sxs-lookup"><span data-stu-id="f570e-318">Setting the SessionMode property indicates it will be a sessionful service.</span></span> <span data-ttu-id="f570e-319">W WCF sesji jest sposobem korelowania wielu komunikatów wysyłanych między dwoma punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="f570e-319">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span> <span data-ttu-id="f570e-320">Oznacza to, że gdy klient uzyskuje połączenie z tą usługą, zostanie ustanowiona sesja między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="f570e-320">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span> <span data-ttu-id="f570e-321">Klient użyje pojedynczego unikatowego wystąpienia obiektu po stronie serwera dla wszystkich jego interakcji w ramach tej pojedynczej sesji.</span><span class="sxs-lookup"><span data-stu-id="f570e-321">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span>  
  
2. <span data-ttu-id="f570e-322">Następnie musimy zapewnić implementację tego interfejsu usługi.</span><span class="sxs-lookup"><span data-stu-id="f570e-322">Next, we need to provide the implementation of this service interface.</span></span> <span data-ttu-id="f570e-323">Oznaczając go za pomocą [ServiceBehavior] i ustawiając InstanceContextMode, informujemy WCF, że chcemy użyć unikatowego wystąpienia tego typu dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="f570e-323">By denoting it with [ServiceBehavior] and setting the InstanceContextMode, we tell WCF we want to use a unique instance of this type for an each session.</span></span>  
  
   ```csharp
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
       public class MySessionBoundObject : ISessionBoundObject  
       {  
           private string _value;  
  
           public string GetCurrentValue()  
           {  
               return _value;  
           }  
  
           public void SetCurrentValue(string val)  
           {  
               _value = val;  
           }  
  
       }  
   ```  
  
3. <span data-ttu-id="f570e-324">Teraz potrzebujemy sposobu, aby uzyskać wystąpienie tego obiektu sesji.</span><span class="sxs-lookup"><span data-stu-id="f570e-324">Now we need a way to obtain an instance of this sessionful object.</span></span> <span data-ttu-id="f570e-325">Robimy to, tworząc inny interfejs usługi WCF, który zwraca Obiekt EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="f570e-325">We do this by creating another WCF service interface that returns an EndpointAddress10 object.</span></span> <span data-ttu-id="f570e-326">Jest to serializable formie punktu końcowego, który klient może użyć do utworzenia obiektu sessionful.</span><span class="sxs-lookup"><span data-stu-id="f570e-326">This is a serializable form of an endpoint that the client can use to create the sessionful object.</span></span>  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     <span data-ttu-id="f570e-327">I wdrażamy tę usługę WCF:</span><span class="sxs-lookup"><span data-stu-id="f570e-327">And we implement this WCF service:</span></span>  
  
   ```csharp
   public class SessionBoundFactory : ISessionBoundFactory  
       {  
           public static ChannelFactory<ISessionBoundObject> _factory =
               new ChannelFactory<ISessionBoundObject>("sessionbound");  

           public SessionBoundFactory()  
           {  
           }  
  
           public EndpointAddress10 GetInstanceAddress()  
           {  
               IClientChannel channel = (IClientChannel)_factory.CreateChannel();  
               return EndpointAddress10.FromEndpointAddress(channel.RemoteAddress);  
           }  
       }  
   ```  
  
     <span data-ttu-id="f570e-328">Ta implementacja utrzymuje fabrykę pojedynczego kanału do tworzenia obiektów sesji.</span><span class="sxs-lookup"><span data-stu-id="f570e-328">This implementation maintains a singleton channel factory to create sessionful objects.</span></span> <span data-ttu-id="f570e-329">Gdy getInstanceAddress() jest wywoływana, tworzy kanał i tworzy EndpointAddress10 obiektu, który skutecznie wskazuje na adres zdalny skojarzony z tym kanałem.</span><span class="sxs-lookup"><span data-stu-id="f570e-329">When GetInstanceAddress() is called, it creates a channel and creates an EndpointAddress10 object that effectively points to the remote address associated with this channel.</span></span> <span data-ttu-id="f570e-330">EndpointAddress10 jest po prostu typem danych, który może być zwracany do wartości klienta według wartości.</span><span class="sxs-lookup"><span data-stu-id="f570e-330">EndpointAddress10 is simply a data type that can be returned to the client by-value.</span></span>  
  
4. <span data-ttu-id="f570e-331">Musimy zmodyfikować plik konfiguracyjny serwera, wykonując następujące dwie czynności, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f570e-331">We need to modify the server’s configuration file by doing the following two things as shown in the example below:</span></span>  
  
    1. <span data-ttu-id="f570e-332">Zadeklaruj sekcję \<> klienta, która opisuje punkt końcowy dla obiektu sesji.</span><span class="sxs-lookup"><span data-stu-id="f570e-332">Declare a \<client> section that describes the endpoint for the sessionful object.</span></span> <span data-ttu-id="f570e-333">Jest to konieczne, ponieważ serwer działa również jako klient w tej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="f570e-333">This is necessary because the server also acts as a client in this situation.</span></span>  
  
    2. <span data-ttu-id="f570e-334">Zadeklaruj punkty końcowe dla obiektu fabrycznego i sesyjnego.</span><span class="sxs-lookup"><span data-stu-id="f570e-334">Declare endpoints for the factory and sessionful object.</span></span> <span data-ttu-id="f570e-335">Jest to konieczne, aby umożliwić klientowi komunikować się z punktami końcowymi usługi, aby uzyskać EndpointAddress10 i utworzyć kanał sessionful.</span><span class="sxs-lookup"><span data-stu-id="f570e-335">This is necessary to allow the client to communicate with the service endpoints to acquire the EndpointAddress10 and to create the sessionful channel.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
         <client>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
        </client>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
          <service name="Server.MySessionBoundObject">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundObject"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundObject" />  
          </service>  
          <service name="Server.SessionBoundFactory">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundFactory"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundFactory" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="f570e-336">A następnie możemy uruchomić te usługi:</span><span class="sxs-lookup"><span data-stu-id="f570e-336">And then we can start these services:</span></span>  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. <span data-ttu-id="f570e-337">Konfigurujemy klienta, deklarując te same punkty końcowe w pliku app.config projektu.</span><span class="sxs-lookup"><span data-stu-id="f570e-337">We configure the client by declaring these same endpoints in its project’s app.config file.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
          <endpoint name="factory"  
                    address="net.tcp://localhost:8081/SessionBoundFactory"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundFactory"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
6. <span data-ttu-id="f570e-338">Aby utworzyć i używać tego obiektu sesyjnego, klient musi wykonać następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="f570e-338">In order to create and use this sessionful object, the client must do the following steps:</span></span>  
  
    1. <span data-ttu-id="f570e-339">Utwórz kanał do usługi ISessionBoundFactory.</span><span class="sxs-lookup"><span data-stu-id="f570e-339">Create a channel to the ISessionBoundFactory service.</span></span>  
  
    2. <span data-ttu-id="f570e-340">Użyj tego kanału, aby wywołać tę usługę, aby uzyskać EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="f570e-340">Use that channel to invoke that service to obtain an EndpointAddress10.</span></span>  
  
    3. <span data-ttu-id="f570e-341">EndpointAddress10 służy do tworzenia kanału w celu uzyskania obiektu sesji.</span><span class="sxs-lookup"><span data-stu-id="f570e-341">Use the EndpointAddress10 to create a channel to obtain a sessionful object.</span></span>  
  
    4. <span data-ttu-id="f570e-342">Interakcja z sessionful obiektu, aby zademonstrować, że pozostaje to samo wystąpienie w wielu wywołaniach.</span><span class="sxs-lookup"><span data-stu-id="f570e-342">Interact with the sessionful object to demonstrate it remains the same instance across multiple calls.</span></span>  
  
   ```csharp
   ChannelFactory<ISessionBoundFactory> channelFactory =
       new ChannelFactory<ISessionBoundFactory>("factory");  
   ISessionBoundFactory sessionFactory = channelFactory.CreateChannel();  
  
   EndpointAddress10 address1 = sessionFactory.GetInstanceAddress();  
   EndpointAddress10 address2 = sessionFactory.GetInstanceAddress();  
  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory1 =
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),
                                               address1.ToEndpointAddress());  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory2 =
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),
                                               address2.ToEndpointAddress());  
  
   ISessionBoundObject sessionInstance1 = sessionObjectFactory1.CreateChannel();  
   ISessionBoundObject sessionInstance2 = sessionObjectFactory2.CreateChannel();  
  
   sessionInstance1.SetCurrentValue("Hello");  
   sessionInstance2.SetCurrentValue("World");  
  
   if (sessionInstance1.GetCurrentValue() == "Hello" &&  
       sessionInstance2.GetCurrentValue() == "World")  
   {  
       Console.WriteLine("sessionful server object works as expected");  
   }  
   ```  
  
 <span data-ttu-id="f570e-343">WCF zawsze zwraca obiekty według wartości, ale jest możliwe do obsługi odpowiednika semantyki odwołania za pomocą EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="f570e-343">WCF always returns objects by value, but it is possible to support the equivalent of by-reference semantics through the use of EndpointAddress10.</span></span> <span data-ttu-id="f570e-344">Dzięki temu klient żądać sesyjne wystąpienie usługi WCF, po czym można wchodzić w interakcje z nim, jak każda inna usługa WCF.</span><span class="sxs-lookup"><span data-stu-id="f570e-344">This permits the client to request a sessionful WCF service instance, after which it can interact with it like any other WCF service.</span></span>  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a><span data-ttu-id="f570e-345">Scenariusz 3: Klient wysyła serwer jako wystąpienie według wartości</span><span class="sxs-lookup"><span data-stu-id="f570e-345">Scenario 3: Client Sends Server a By-Value Instance</span></span>  
 <span data-ttu-id="f570e-346">W tym scenariuszu pokazano klienta wysyłania wystąpienia obiektu nieizbowy do serwera według wartości.</span><span class="sxs-lookup"><span data-stu-id="f570e-346">This scenario demonstrates the client sending a non-primitive object instance to the server by value.</span></span> <span data-ttu-id="f570e-347">Ponieważ WCF wysyła tylko obiekty według wartości, w tym scenariuszu pokazuje normalne użycie WCF.</span><span class="sxs-lookup"><span data-stu-id="f570e-347">Because WCF only sends objects by value, this scenario demonstrates normal WCF usage.</span></span>  
  
1. <span data-ttu-id="f570e-348">Użyj tej samej usługi WCF ze scenariusza 1.</span><span class="sxs-lookup"><span data-stu-id="f570e-348">Use the same WCF Service from Scenario 1.</span></span>  
  
2. <span data-ttu-id="f570e-349">Użyj klienta, aby utworzyć nowy obiekt według wartości (Klient), utworzyć kanał do komunikowania się z usługą ICustomerService i wysłać obiekt do niego.</span><span class="sxs-lookup"><span data-stu-id="f570e-349">Use the client to create a new by-value object (Customer), create a channel to communicate with the ICustomerService service, and send the object to it.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   PremiumCustomer customer = new PremiumCustomer {
   FirstName = "Bob",
   LastName = "Jones",
   CustomerId = 43,
   AccountId = 99};  
   bool success = service.UpdateCustomer(customer);  
   Console.WriteLine($"  Server returned {success}.");
   ```  
  
     <span data-ttu-id="f570e-350">Obiekt klienta zostanie szeregizowany i wysłany do serwera, gdzie jest deserializowany do nowej kopii tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f570e-350">The customer object will be serialized, and sent to the server, where it is deserialized into a new copy of that object.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f570e-351">Ten kod ilustruje również wysyłanie typu pochodnego (PremiumCustomer).</span><span class="sxs-lookup"><span data-stu-id="f570e-351">This code also illustrates sending a derived type (PremiumCustomer).</span></span> <span data-ttu-id="f570e-352">Interfejs usługi oczekuje Customer obiektu, ale [KnownType] atrybut w Customer klasy wskazane PremiumCustomer był również dozwolone.</span><span class="sxs-lookup"><span data-stu-id="f570e-352">The service interface expects a Customer object, but the [KnownType] attribute on the Customer class indicated PremiumCustomer was also allowed.</span></span> <span data-ttu-id="f570e-353">WCF zakończy się niepowodzeniem wszelkie próby serializacji lub deserializacji dowolnego innego typu za pośrednictwem tego interfejsu usługi.</span><span class="sxs-lookup"><span data-stu-id="f570e-353">WCF will fail any attempt to serialize or deserialize any other type through this service interface.</span></span>  
  
 <span data-ttu-id="f570e-354">Normalna wymiana danych WCF jest według wartości.</span><span class="sxs-lookup"><span data-stu-id="f570e-354">Normal WCF exchanges of data are by value.</span></span> <span data-ttu-id="f570e-355">Gwarantuje to, że wywoływanie metod na jednym z tych obiektów danych wykonuje tylko lokalnie — nie będzie wywoływać kodu w innej warstwie.</span><span class="sxs-lookup"><span data-stu-id="f570e-355">This guarantees that invoking methods on one of these data objects executes only locally – it will not invoke code on the other tier.</span></span> <span data-ttu-id="f570e-356">Chociaż jest możliwe, aby osiągnąć coś jak obiekty odwołania zwracane *z* serwera, nie jest możliwe dla klienta, aby przekazać obiekt by-reference *do* serwera.</span><span class="sxs-lookup"><span data-stu-id="f570e-356">While it is possible to achieve something like by-reference objects returned *from* the server, it is not possible for a client to pass a by-reference object *to* the server.</span></span> <span data-ttu-id="f570e-357">Scenariusz, który wymaga konwersacji tam iz powrotem między klientem a serwerem można osiągnąć w WCF przy użyciu usługi dupleksu.</span><span class="sxs-lookup"><span data-stu-id="f570e-357">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span> <span data-ttu-id="f570e-358">Aby uzyskać więcej informacji, zobacz [Usługi dupleksu](./feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="f570e-358">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="f570e-359">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="f570e-359">Summary</span></span>  
 <span data-ttu-id="f570e-360">.NET Remoting to struktura komunikacji przeznaczona do użycia tylko w w pełni zaufanych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="f570e-360">.NET Remoting is a communication framework intended to be used only within fully-trusted environments.</span></span> <span data-ttu-id="f570e-361">Jest to produkt starszej wersji i obsługiwany tylko w celu zapewnienia zgodności z powrotem.</span><span class="sxs-lookup"><span data-stu-id="f570e-361">It is a legacy product and supported only for backward compatibility.</span></span> <span data-ttu-id="f570e-362">Nie należy używać do tworzenia nowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f570e-362">It should not be used to build new applications.</span></span> <span data-ttu-id="f570e-363">Z drugiej strony WCF został zaprojektowany z myślą o bezpieczeństwie i jest zalecany dla nowych i istniejących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f570e-363">Conversely, WCF was designed with security in mind and is recommended for new and existing applications.</span></span> <span data-ttu-id="f570e-364">Firma Microsoft zaleca migrację istniejących aplikacji komunikacji zdalnej w celu użycia interfejsu WCF lub ASP.NET interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f570e-364">Microsoft recommends that existing Remoting applications be migrated to use WCF or ASP.NET Web API instead.</span></span>
