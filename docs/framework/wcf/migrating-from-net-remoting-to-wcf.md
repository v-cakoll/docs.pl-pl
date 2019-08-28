---
title: Migrowanie z programu .NET Remoting do programu WCF
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: c42255a14a23cb50f3fe8be434efab4af7361daa
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045854"
---
# <a name="migrating-from-net-remoting-to-wcf"></a><span data-ttu-id="7144e-102">Migrowanie z programu .NET Remoting do programu WCF</span><span class="sxs-lookup"><span data-stu-id="7144e-102">Migrating from .NET Remoting to WCF</span></span>
<span data-ttu-id="7144e-103">W tym artykule opisano sposób migracji aplikacji, która używa usług komunikacji zdalnej .NET do korzystania z Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7144e-103">This article describes how to migrate an application that uses .NET Remoting to use Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="7144e-104">Porównuje podobne koncepcje tych produktów, a następnie opisuje sposób wykonywania kilku typowych scenariuszy komunikacji zdalnej w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="7144e-104">It compares similar concepts between these products and then describes how to accomplish several common Remoting scenarios in WCF.</span></span>  
  
 <span data-ttu-id="7144e-105">Komunikacja zdalna .NET to starszy produkt, który jest obsługiwany tylko w celu zapewnienia zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="7144e-105">.NET Remoting is a legacy product that is supported only for backward compatibility.</span></span> <span data-ttu-id="7144e-106">Nie jest on zabezpieczony w środowiskach z zaufaniem mieszanym, ponieważ nie może zachować oddzielnych poziomów zaufania między klientem i serwerem.</span><span class="sxs-lookup"><span data-stu-id="7144e-106">It is not secure across mixed-trust environments because it cannot maintain the separate trust levels between client and server.</span></span> <span data-ttu-id="7144e-107">Na przykład nigdy nie należy ujawniać punktu końcowego komunikacji zdalnej platformy .NET z Internetem lub niezaufanym klientom.</span><span class="sxs-lookup"><span data-stu-id="7144e-107">For example, you should never expose a .NET Remoting endpoint to the Internet or to untrusted clients.</span></span> <span data-ttu-id="7144e-108">Zalecamy Migrowanie istniejących aplikacji zdalnych do nowszych i bardziej bezpiecznych technologii.</span><span class="sxs-lookup"><span data-stu-id="7144e-108">We recommend existing Remoting applications be migrated to newer and more secure technologies.</span></span> <span data-ttu-id="7144e-109">Jeśli projekt aplikacji używa tylko protokołu HTTP i jest RESTful, zalecamy ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="7144e-109">If the application’s design uses only HTTP and is RESTful, we recommend ASP.NET Web API.</span></span> <span data-ttu-id="7144e-110">Aby uzyskać więcej informacji, zobacz ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="7144e-110">For more information, see ASP.NET Web API.</span></span> <span data-ttu-id="7144e-111">Jeśli aplikacja jest oparta na protokole SOAP lub wymaga protokołów innych niż http, takich jak TCP, zalecamy korzystanie z programu WCF.</span><span class="sxs-lookup"><span data-stu-id="7144e-111">If the application is based on SOAP or requires non-Http protocols such as TCP, we recommend WCF.</span></span>  

## <a name="comparing-net-remoting-to-wcf"></a><span data-ttu-id="7144e-112">Porównanie komunikacji zdalnej .NET z usługą WCF</span><span class="sxs-lookup"><span data-stu-id="7144e-112">Comparing .NET Remoting to WCF</span></span>  
 <span data-ttu-id="7144e-113">Ta sekcja zawiera porównanie podstawowych bloków konstrukcyjnych komunikacji zdalnej .NET z ich odpowiednikami WCF.</span><span class="sxs-lookup"><span data-stu-id="7144e-113">This section compares the basic building blocks of .NET Remoting with their WCF equivalents.</span></span> <span data-ttu-id="7144e-114">Będziemy używać tych bloków konstrukcyjnych później, aby utworzyć niektóre typowe scenariusze serwera klienta w programie WCF. Poniższy wykres podsumowuje główne podobieństwa i różnice między usługami zdalnymi i WCF platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="7144e-114">We will use these building blocks later to create some common client-server scenarios in WCF.The following chart summarizes the main similarities and differences between .NET Remoting and WCF.</span></span>  
  
||<span data-ttu-id="7144e-115">Wywołaniem funkcji zdalnych .NET</span><span class="sxs-lookup"><span data-stu-id="7144e-115">.NET Remoting</span></span>|<span data-ttu-id="7144e-116">WCF</span><span class="sxs-lookup"><span data-stu-id="7144e-116">WCF</span></span>|  
|-|-------------------|---------|  
|<span data-ttu-id="7144e-117">Typ serwera</span><span class="sxs-lookup"><span data-stu-id="7144e-117">Server type</span></span>|<span data-ttu-id="7144e-118">MarshalByRefObject podklasy</span><span class="sxs-lookup"><span data-stu-id="7144e-118">Subclass MarshalByRefObject</span></span>|<span data-ttu-id="7144e-119">Oznacz przy użyciu atrybutu [ServiceContract]</span><span class="sxs-lookup"><span data-stu-id="7144e-119">Mark with [ServiceContract] attribute</span></span>|  
|<span data-ttu-id="7144e-120">Operacje usługi</span><span class="sxs-lookup"><span data-stu-id="7144e-120">Service operations</span></span>|<span data-ttu-id="7144e-121">Metody publiczne na serwerze typu</span><span class="sxs-lookup"><span data-stu-id="7144e-121">Public methods on server type</span></span>|<span data-ttu-id="7144e-122">Oznacz przy użyciu atrybutu [OperationContract]</span><span class="sxs-lookup"><span data-stu-id="7144e-122">Mark with [OperationContract] attribute</span></span>|  
|<span data-ttu-id="7144e-123">Serializacja</span><span class="sxs-lookup"><span data-stu-id="7144e-123">Serialization</span></span>|<span data-ttu-id="7144e-124">ISerializable lub [Serializable]</span><span class="sxs-lookup"><span data-stu-id="7144e-124">ISerializable or [Serializable]</span></span>|<span data-ttu-id="7144e-125">DataContractSerializer lub XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="7144e-125">DataContractSerializer or XmlSerializer</span></span>|  
|<span data-ttu-id="7144e-126">Obiekty zakończone</span><span class="sxs-lookup"><span data-stu-id="7144e-126">Objects passed</span></span>|<span data-ttu-id="7144e-127">Według wartości lub według odwołania</span><span class="sxs-lookup"><span data-stu-id="7144e-127">By-value or by-reference</span></span>|<span data-ttu-id="7144e-128">Tylko według wartości</span><span class="sxs-lookup"><span data-stu-id="7144e-128">By-value only</span></span>|  
|<span data-ttu-id="7144e-129">Błędy/wyjątki</span><span class="sxs-lookup"><span data-stu-id="7144e-129">Errors/exceptions</span></span>|<span data-ttu-id="7144e-130">Dowolny wyjątek możliwy do serializacji</span><span class="sxs-lookup"><span data-stu-id="7144e-130">Any serializable exception</span></span>|<span data-ttu-id="7144e-131">FaultContract\<TDetail></span><span class="sxs-lookup"><span data-stu-id="7144e-131">FaultContract\<TDetail></span></span>|  
|<span data-ttu-id="7144e-132">Obiekty serwera proxy klienta</span><span class="sxs-lookup"><span data-stu-id="7144e-132">Client proxy objects</span></span>|<span data-ttu-id="7144e-133">Przezroczyste obiekty pośredniczące o jednoznacznie określonym typie są tworzone automatycznie z MarshalByRefObjects</span><span class="sxs-lookup"><span data-stu-id="7144e-133">Strongly typed transparent proxies are created automatically from MarshalByRefObjects</span></span>|<span data-ttu-id="7144e-134">Serwery proxy o jednoznacznie określonym typie są generowane na żądanie przy\<użyciu elementu ChannelFactory TChannel ></span><span class="sxs-lookup"><span data-stu-id="7144e-134">Strongly typed proxies are generated on-demand using ChannelFactory\<TChannel></span></span>|  
|<span data-ttu-id="7144e-135">Wymagana platforma</span><span class="sxs-lookup"><span data-stu-id="7144e-135">Platform required</span></span>|<span data-ttu-id="7144e-136">Zarówno klient, jak i serwer muszą korzystać z systemów operacyjnych Microsoft i .NET</span><span class="sxs-lookup"><span data-stu-id="7144e-136">Both client and server must use Microsoft OS and .NET</span></span>|<span data-ttu-id="7144e-137">Wiele platform</span><span class="sxs-lookup"><span data-stu-id="7144e-137">Cross-platform</span></span>|  
|<span data-ttu-id="7144e-138">Format wiadomości</span><span class="sxs-lookup"><span data-stu-id="7144e-138">Message format</span></span>|<span data-ttu-id="7144e-139">Private</span><span class="sxs-lookup"><span data-stu-id="7144e-139">Private</span></span>|<span data-ttu-id="7144e-140">Standardy branżowe (SOAP, WS-\* itp.)</span><span class="sxs-lookup"><span data-stu-id="7144e-140">Industry standards (SOAP, WS-\*, etc.)</span></span>|  
  
### <a name="server-implementation-comparison"></a><span data-ttu-id="7144e-141">Porównanie implementacji serwera</span><span class="sxs-lookup"><span data-stu-id="7144e-141">Server Implementation Comparison</span></span>  
  
#### <a name="creating-a-server-in-net-remoting"></a><span data-ttu-id="7144e-142">Tworzenie serwera w usłudze komunikacja zdalna .NET</span><span class="sxs-lookup"><span data-stu-id="7144e-142">Creating a Server in .NET Remoting</span></span>  
 <span data-ttu-id="7144e-143">Typy serwerów komunikacji zdalnej platformy .NET muszą pochodzić od MarshalByRefObject i definiować metody, które klient może wywołać, tak jak w przypadku następujących:</span><span class="sxs-lookup"><span data-stu-id="7144e-143">.NET Remoting server types must derive from MarshalByRefObject and define methods the client can call, like the following:</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="7144e-144">Publiczne metody tego typu serwera stają się kontraktem publicznym dostępnym dla klientów.</span><span class="sxs-lookup"><span data-stu-id="7144e-144">The public methods of this server type become the public contract available to clients.</span></span>  <span data-ttu-id="7144e-145">Nie ma rozdzielania między interfejsem publicznym serwera a jego implementacją — jeden typ obsługuje obie.</span><span class="sxs-lookup"><span data-stu-id="7144e-145">There is no separation between the server’s public interface and its implementation – one type handles both.</span></span>  
  
 <span data-ttu-id="7144e-146">Po zdefiniowaniu typu serwera można go udostępnić klientom, tak jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7144e-146">Once the server type has been defined, it can be made available to clients, like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="7144e-147">Istnieje wiele sposobów zapewnienia, że typ komunikacji zdalnej jest dostępny jako serwer, w tym przy użyciu plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="7144e-147">There are many ways to make the Remoting type available as a server, including using configuration files.</span></span> <span data-ttu-id="7144e-148">Jest to tylko jeden przykład.</span><span class="sxs-lookup"><span data-stu-id="7144e-148">This is just one example.</span></span>  
  
#### <a name="creating-a-server-in-wcf"></a><span data-ttu-id="7144e-149">Tworzenie serwera w programie WCF</span><span class="sxs-lookup"><span data-stu-id="7144e-149">Creating a Server in WCF</span></span>  
 <span data-ttu-id="7144e-150">Odpowiedni krok w programie WCF obejmuje tworzenie dwóch typów — publicznego "kontraktu usług" i konkretnej implementacji.</span><span class="sxs-lookup"><span data-stu-id="7144e-150">The equivalent step in WCF involves creating two types -- the public "service contract" and the concrete implementation.</span></span> <span data-ttu-id="7144e-151">Pierwszy jest zadeklarowany jako interfejs oznaczony przy użyciu [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="7144e-151">The first is declared as an interface marked with [ServiceContract].</span></span> <span data-ttu-id="7144e-152">Metody dostępne dla klientów są oznaczone atrybutem [OperationContract]:</span><span class="sxs-lookup"><span data-stu-id="7144e-152">Methods available to clients are marked with [OperationContract]:</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="7144e-153">Implementacja serwera jest definiowana w oddzielnym konkretnym klasie, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7144e-153">The server’s implementation is defined in a separate concrete class, like in the following example:</span></span>  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="7144e-154">Po zdefiniowaniu tych typów serwer WCF można udostępnić klientom, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7144e-154">Once these types have been defined, the WCF server can be made available to clients, like in the following example:</span></span>  
  
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
> <span data-ttu-id="7144e-155">Protokół TCP jest używany w obu przykładach, aby zachować je tak jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="7144e-155">TCP is used in both examples to keep them as similar as possible.</span></span> <span data-ttu-id="7144e-156">Zapoznaj się z tematami dotyczącymi scenariusza w dalszej części tego tematu, aby poznać przykłady użycia protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="7144e-156">Refer to the scenario walk-throughs later in this topic for examples using HTTP.</span></span>  
  
 <span data-ttu-id="7144e-157">Istnieje wiele sposobów konfigurowania i hostowania usług WCF.</span><span class="sxs-lookup"><span data-stu-id="7144e-157">There are many ways to configure and to host WCF services.</span></span> <span data-ttu-id="7144e-158">Jest to tylko jeden przykład, znany jako "samodzielny".</span><span class="sxs-lookup"><span data-stu-id="7144e-158">This is just one example, known as "self-hosted".</span></span> <span data-ttu-id="7144e-159">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="7144e-159">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="7144e-160">Instrukcje: Definiowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="7144e-160">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)  
  
- [<span data-ttu-id="7144e-161">Konfigurowanie usług za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7144e-161">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
  
- [<span data-ttu-id="7144e-162">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="7144e-162">Hosting Services</span></span>](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a><span data-ttu-id="7144e-163">Porównanie implementacji klienta</span><span class="sxs-lookup"><span data-stu-id="7144e-163">Client Implementation Comparison</span></span>  
  
#### <a name="creating-a-client-in-net-remoting"></a><span data-ttu-id="7144e-164">Tworzenie klienta w usłudze komunikacja zdalna .NET</span><span class="sxs-lookup"><span data-stu-id="7144e-164">Creating a Client in .NET Remoting</span></span>  
 <span data-ttu-id="7144e-165">Po udostępnieniu obiektu serwera komunikacji zdalnej platformy .NET może on być używany przez klientów, taki jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7144e-165">Once a .NET Remoting server object has been made available, it can be consumed by clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 <span data-ttu-id="7144e-166">Wystąpienie RemotingServer zwróciło element aktywator. GetObject () jest znany jako "przezroczysty serwer proxy".</span><span class="sxs-lookup"><span data-stu-id="7144e-166">The RemotingServer instance returned from Activator.GetObject() is known as a "transparent proxy."</span></span> <span data-ttu-id="7144e-167">Implementuje on publiczny interfejs API dla typu RemotingServer na kliencie, ale wszystkie metody wywołują obiekt serwera uruchomiony w innym procesie lub na maszynie.</span><span class="sxs-lookup"><span data-stu-id="7144e-167">It implements the public API for the RemotingServer type on the client, but all the methods call the server object running in a different process or machine.</span></span>  
  
#### <a name="creating-a-client-in-wcf"></a><span data-ttu-id="7144e-168">Tworzenie klienta w programie WCF</span><span class="sxs-lookup"><span data-stu-id="7144e-168">Creating a Client in WCF</span></span>  
 <span data-ttu-id="7144e-169">Odpowiedni krok w programie WCF polega na użyciu fabryki kanałów w celu jawnego utworzenia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="7144e-169">The equivalent step in WCF involves using a channel factory to create the proxy explicitly.</span></span> <span data-ttu-id="7144e-170">Podobnie jak w przypadku komunikacji zdalnej, obiekt serwera proxy może służyć do wywoływania operacji na serwerze, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7144e-170">Like Remoting, the proxy object can be used to invoke operations on the server, like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="7144e-171">W tym przykładzie przedstawiono Programowanie na poziomie kanału, ponieważ jest ono najbardziej podobne do przykładu komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="7144e-171">This example shows programming at the channel level because it is most similar to the Remoting example.</span></span> <span data-ttu-id="7144e-172">Dostępna jest również Metoda **Dodaj odwołanie do usługi** w programie Visual Studio, która generuje kod upraszczający programowanie klientów.</span><span class="sxs-lookup"><span data-stu-id="7144e-172">Also available is the **Add Service Reference** approach in Visual Studio that generates code to simplify client programming.</span></span> <span data-ttu-id="7144e-173">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="7144e-173">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="7144e-174">Programowanie na poziomie kanału klienta</span><span class="sxs-lookup"><span data-stu-id="7144e-174">Client Channel-Level Programming</span></span>](./extending/client-channel-level-programming.md)  
  
- [<span data-ttu-id="7144e-175">Instrukcje: Dodawanie, aktualizowanie lub usuwanie odwołania do usługi</span><span class="sxs-lookup"><span data-stu-id="7144e-175">How to: Add, Update, or Remove a Service Reference</span></span>](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a><span data-ttu-id="7144e-176">Użycie serializacji</span><span class="sxs-lookup"><span data-stu-id="7144e-176">Serialization Usage</span></span>  
 <span data-ttu-id="7144e-177">Zarówno komunikacja zdalna .NET, jak i WCF używają serializacji do przesyłania obiektów między klientem a serwerem, ale różnią się następującymi sposobami:</span><span class="sxs-lookup"><span data-stu-id="7144e-177">Both .NET Remoting and WCF use serialization to send objects between client and server, but they differ in these important ways:</span></span>  
  
1. <span data-ttu-id="7144e-178">Wykorzystują różne serializatory i konwencje w celu wskazania, co należy serializować.</span><span class="sxs-lookup"><span data-stu-id="7144e-178">They use different serializers and conventions to indicate what to serialize.</span></span>  
  
2. <span data-ttu-id="7144e-179">Komunikacja zdalna platformy .NET obsługuje serializację "przywoływane", który umożliwia dostęp do metody lub właściwości w jednej warstwie w celu wykonywania kodu w innej warstwie, która znajduje się w granicach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7144e-179">.NET Remoting supports "by reference" serialization that allows method or property access on one tier to execute code on the other tier, which is across security boundaries.</span></span> <span data-ttu-id="7144e-180">Ta funkcja udostępnia luki w zabezpieczeniach i jest jednym z głównych powodów, dla których punkty końcowe komunikacji zdalnej nigdy nie mają być ujawniane niezaufanym klientom.</span><span class="sxs-lookup"><span data-stu-id="7144e-180">This capability exposes security vulnerabilities and is one of the main reasons why Remoting endpoints should never be exposed to untrusted clients.</span></span>  
  
3. <span data-ttu-id="7144e-181">Serializacja używana przez funkcję komunikacji zdalnej jest niezależna (jawnie wyklucza to, co nie jest serializowane) i Serializacja WCF jest niezależna (jawnie Oznacz członków do serializacji).</span><span class="sxs-lookup"><span data-stu-id="7144e-181">Serialization used by Remoting is opt-out (explicitly exclude what not to serialize) and WCF serialization is opt-in (explicitly mark which members to serialize).</span></span>  
  
#### <a name="serialization-in-net-remoting"></a><span data-ttu-id="7144e-182">Serializacja w komunikacji zdalnej .NET</span><span class="sxs-lookup"><span data-stu-id="7144e-182">Serialization in .NET Remoting</span></span>  
 <span data-ttu-id="7144e-183">Komunikacja zdalna platformy .NET obsługuje dwa sposoby serializacji i deserializacji obiektów między klientem a serwerem:</span><span class="sxs-lookup"><span data-stu-id="7144e-183">.NET Remoting supports two ways to serialize and deserialize objects between the client and server:</span></span>  
  
- <span data-ttu-id="7144e-184">*Według wartości* — wartości obiektu są serializowane w granicach warstwy, a nowe wystąpienie tego obiektu jest tworzone w innej warstwie.</span><span class="sxs-lookup"><span data-stu-id="7144e-184">*By value* – the values of the object are serialized across tier boundaries, and a new instance of that object is created on the other tier.</span></span> <span data-ttu-id="7144e-185">Wszystkie wywołania metod lub właściwości tego nowego wystąpienia są wykonywane tylko lokalnie i nie wpływają na oryginalny obiekt lub warstwę.</span><span class="sxs-lookup"><span data-stu-id="7144e-185">Any calls to methods or properties of that new instance execute only locally and do not affect the original object or tier.</span></span>  
  
- <span data-ttu-id="7144e-186">*Według odwołania* — specjalne "odwołanie do obiektu" jest serializowane między granicami warstwy.</span><span class="sxs-lookup"><span data-stu-id="7144e-186">*By reference* – a special "object reference" is serialized across tier boundaries.</span></span> <span data-ttu-id="7144e-187">Gdy jedna warstwa współdziała z metodami lub właściwościami tego obiektu, komunikuje się z powrotem do oryginalnego obiektu w oryginalnej warstwie.</span><span class="sxs-lookup"><span data-stu-id="7144e-187">When one tier interacts with methods or properties of that object, it communicates back to the original object on the original tier.</span></span> <span data-ttu-id="7144e-188">Obiekty przez odwołanie mogą przepływać w dowolnym kierunku — serwer do klienta lub z klientem do serwera.</span><span class="sxs-lookup"><span data-stu-id="7144e-188">By-reference objects can flow in either direction – server to client, or client to server.</span></span>  
  
 <span data-ttu-id="7144e-189">Typy według wartości w ramach usług zdalnych są oznaczone atrybutem [Serializable] lub implementuje interfejs ISerializable, tak jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7144e-189">By-value types in Remoting are marked with the [Serializable] attribute or implement ISerializable, like in the following example:</span></span>  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="7144e-190">Typy odwołań pochodnych pochodzą od klasy MarshalByRefObject, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7144e-190">By-reference types derive from the MarshalByRefObject class, like in the following example:</span></span>  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="7144e-191">Niezwykle ważne jest, aby zrozumieć konsekwencje dotyczące obiektów odwołujących się do komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="7144e-191">It is extremely important to understand the implications of Remoting’s by-reference objects.</span></span> <span data-ttu-id="7144e-192">Jeśli jedna z warstw (klienta lub serwera) wysyła obiekt przez odwołanie do innej warstwy, wszystkie wywołania metod są wykonywane z powrotem do warstwy będącej właścicielem obiektu.</span><span class="sxs-lookup"><span data-stu-id="7144e-192">If either tier (client or server) sends a by-reference object to the other tier, all method calls execute back on the tier owning the object.</span></span> <span data-ttu-id="7144e-193">Na przykład wywoływanie metod przez klienta na obiektach przez odwołanie przez serwer spowoduje wykonanie kodu na serwerze.</span><span class="sxs-lookup"><span data-stu-id="7144e-193">For example, a client calling methods on a by-reference object returned by the server will execute code on the server.</span></span> <span data-ttu-id="7144e-194">Podobnie serwer wywołujący metody dla obiektu przez odwołanie dostarczone przez klienta spowoduje wykonanie kodu z powrotem na kliencie.</span><span class="sxs-lookup"><span data-stu-id="7144e-194">Similarly, a server calling methods on a by-reference object provided by the client will execute code back on the client.</span></span> <span data-ttu-id="7144e-195">Z tego powodu zaleca się używanie komunikacji zdalnej platformy .NET tylko w środowiskach w pełni zaufanych.</span><span class="sxs-lookup"><span data-stu-id="7144e-195">For this reason, the use of .NET Remoting is recommended only within fully-trusted environments.</span></span> <span data-ttu-id="7144e-196">Ujawnienie publicznego punktu końcowego komunikacji zdalnej .NET do niezaufanych klientów spowoduje, że serwer komunikacji zdalnej będzie narażony na ataki.</span><span class="sxs-lookup"><span data-stu-id="7144e-196">Exposing a public .NET Remoting endpoint to untrusted clients will make a Remoting server vulnerable to attack.</span></span>  
  
#### <a name="serialization-in-wcf"></a><span data-ttu-id="7144e-197">Serializacja w programie WCF</span><span class="sxs-lookup"><span data-stu-id="7144e-197">Serialization in WCF</span></span>  
 <span data-ttu-id="7144e-198">WCF obsługuje tylko serializacji według wartości.</span><span class="sxs-lookup"><span data-stu-id="7144e-198">WCF supports only by-value serialization.</span></span> <span data-ttu-id="7144e-199">Najbardziej typowym sposobem zdefiniowania typu do wymiany między klientem a serwerem jest jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7144e-199">The most common way to define a type to exchange between client and server is like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="7144e-200">Atrybut [DataContract] identyfikuje ten typ jako taki, który może być serializowany i deserializowany między klientem i serwerem.</span><span class="sxs-lookup"><span data-stu-id="7144e-200">The [DataContract] attribute identifies this type as one that can be serialized and deserialized between client and server.</span></span> <span data-ttu-id="7144e-201">Atrybut [DataMember] identyfikuje poszczególne właściwości lub pola do serializacji.</span><span class="sxs-lookup"><span data-stu-id="7144e-201">The [DataMember] attribute identifies the individual properties or fields to serialize.</span></span>  
  
 <span data-ttu-id="7144e-202">Gdy WCF wysyła obiekt między warstwami, serializować tylko wartości i tworzy nowe wystąpienie obiektu na drugiej warstwie.</span><span class="sxs-lookup"><span data-stu-id="7144e-202">When WCF sends an object across tiers, it serializes only the values and creates a new instance of the object on the other tier.</span></span> <span data-ttu-id="7144e-203">Wszystkie interakcje z wartościami obiektu są wykonywane tylko lokalnie — nie komunikują się z drugą warstwą, tak jak obiekty referencyjne komunikacji zdalnej przez platformę .NET.</span><span class="sxs-lookup"><span data-stu-id="7144e-203">Any interactions with the values of the object occur only locally – they do not communicate with the other tier the way .NET Remoting by-reference objects do.</span></span> <span data-ttu-id="7144e-204">Aby uzyskać więcej informacji, zobacz [serializacji i deserializacji](./feature-details/serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="7144e-204">For more information, see [Serialization and Deserialization](./feature-details/serialization-and-deserialization.md).</span></span>  
  
### <a name="exception-handling-capabilities"></a><span data-ttu-id="7144e-205">Możliwości obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="7144e-205">Exception Handling Capabilities</span></span>  
  
#### <a name="exceptions-in-net-remoting"></a><span data-ttu-id="7144e-206">Wyjątki w komunikacji zdalnej .NET</span><span class="sxs-lookup"><span data-stu-id="7144e-206">Exceptions in .NET Remoting</span></span>  
 <span data-ttu-id="7144e-207">Wyjątki zgłoszone przez serwer usług zdalnych są serializowane, wysyłane do klienta i zgłaszane lokalnie na kliencie, podobnie jak każdy inny wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7144e-207">Exceptions thrown by a Remoting server are serialized, sent to the client, and thrown locally on the client like any other exception.</span></span> <span data-ttu-id="7144e-208">Wyjątki niestandardowe można utworzyć przez podklasę typu wyjątku i oznaczenie go przy użyciu [Serializable].</span><span class="sxs-lookup"><span data-stu-id="7144e-208">Custom exceptions can be created by sub-classing the Exception type and marking it with [Serializable].</span></span>   <span data-ttu-id="7144e-209">Większość wyjątków Framework została już oznaczona w ten sposób, co pozwala na to, aby większość zgłaszać serwerowi, serializować i ponownie wygenerowane na kliencie.</span><span class="sxs-lookup"><span data-stu-id="7144e-209">Most framework exceptions are already marked in this way, allowing most to be thrown by the server, serialized, and re-thrown on the client.</span></span> <span data-ttu-id="7144e-210">Chociaż ten projekt jest wygodny podczas programowania, informacje po stronie serwera mogą zostać przypadkowo ujawnione dla klienta.</span><span class="sxs-lookup"><span data-stu-id="7144e-210">Though this design is convenient during development, server-side information can inadvertently be disclosed to the client.</span></span> <span data-ttu-id="7144e-211">Jest to jedna z wielu powodów, dla których komunikacja zdalna powinna być używana tylko w w pełni zaufanych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="7144e-211">This is one of many reasons Remoting should be used only in fully-trusted environments.</span></span>  
  
#### <a name="exceptions-and-faults-in-wcf"></a><span data-ttu-id="7144e-212">Wyjątki i błędy w programie WCF</span><span class="sxs-lookup"><span data-stu-id="7144e-212">Exceptions and Faults in WCF</span></span>  
 <span data-ttu-id="7144e-213">Funkcja WCF nie zezwala na Zwracanie żadnych typów wyjątków z serwera do klienta, ponieważ może to prowadzić do przypadkowego ujawnienia informacji.</span><span class="sxs-lookup"><span data-stu-id="7144e-213">WCF does not allow arbitrary exception types to be returned from the server to the client because it could lead to inadvertent information disclosure.</span></span> <span data-ttu-id="7144e-214">Jeśli operacja usługi zgłasza nieoczekiwany wyjątek, spowoduje to, że na kliencie zostanie zgłoszony błąd ogólnego przeznaczeniaexception.</span><span class="sxs-lookup"><span data-stu-id="7144e-214">If a service operation throws an unexpected exception, it causes a general purpose FaultException to be thrown on the client.</span></span> <span data-ttu-id="7144e-215">Ten wyjątek nie zawiera żadnych informacji o tym, dlaczego wystąpił problem, i w przypadku niektórych aplikacji, które są wystarczające.</span><span class="sxs-lookup"><span data-stu-id="7144e-215">This exception does not carry any information why or where the problem occurred, and for some applications this is sufficient.</span></span> <span data-ttu-id="7144e-216">Aplikacje, które muszą przekazać bogatsze informacje o błędzie do klienta, można to zrobić, definiując umowę o błędzie.</span><span class="sxs-lookup"><span data-stu-id="7144e-216">Applications that need to communicate richer error information to the client do this by defining a fault contract.</span></span>  
  
 <span data-ttu-id="7144e-217">W tym celu należy najpierw utworzyć typ [DataContract], aby przenieść informacje o błędzie.</span><span class="sxs-lookup"><span data-stu-id="7144e-217">To do this, first create a [DataContract] type to carry the fault information.</span></span>  
  
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
  
 <span data-ttu-id="7144e-218">Określ kontrakt błędu, który ma być używany dla każdej operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="7144e-218">Specify the fault contract to use for each service operation.</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="7144e-219">Serwer zgłasza warunki błędów, zgłaszając wyjątek FaultException.</span><span class="sxs-lookup"><span data-stu-id="7144e-219">The server reports error conditions by throwing a FaultException.</span></span>  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 <span data-ttu-id="7144e-220">Gdy klient wysyła żądanie do serwera, może przechwytywać błędy jako normalne wyjątki.</span><span class="sxs-lookup"><span data-stu-id="7144e-220">And whenever the client makes a request to the server, it can catch faults as normal exceptions.</span></span>  
  
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
  
 <span data-ttu-id="7144e-221">Aby uzyskać więcej informacji na temat umów dotyczących <xref:System.ServiceModel.FaultException>błędów, zobacz.</span><span class="sxs-lookup"><span data-stu-id="7144e-221">For more information about fault contracts, see <xref:System.ServiceModel.FaultException>.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="7144e-222">Zagadnienia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="7144e-222">Security Considerations</span></span>  
  
#### <a name="security-in-net-remoting"></a><span data-ttu-id="7144e-223">Zabezpieczenia w komunikacji zdalnej .NET</span><span class="sxs-lookup"><span data-stu-id="7144e-223">Security in .NET Remoting</span></span>  
 <span data-ttu-id="7144e-224">Niektóre kanały komunikacji zdalnej .NET obsługują funkcje zabezpieczeń, takie jak uwierzytelnianie i szyfrowanie, w warstwie kanału (IPC i TCP).</span><span class="sxs-lookup"><span data-stu-id="7144e-224">Some .NET Remoting channels support security features such as authentication and encryption at the channel layer (IPC and TCP).</span></span> <span data-ttu-id="7144e-225">Kanał HTTP opiera się na Internet Information Services (IIS) do uwierzytelniania i szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="7144e-225">The HTTP channel relies on Internet Information Services (IIS) for both authentication and encryption.</span></span> <span data-ttu-id="7144e-226">Pomimo tego wsparcia należy rozważyć użycie przez program .NET zdalnej protokołu komunikacyjnego i używanie go tylko w środowiskach w pełni zaufanych.</span><span class="sxs-lookup"><span data-stu-id="7144e-226">Despite this support, you should consider .NET Remoting an unsecure communication protocol and use it only within fully-trusted environments.</span></span> <span data-ttu-id="7144e-227">Nigdy nie ujawniaj publicznego punktu końcowego komunikacji zdalnej dla Internetu lub niezaufanych klientów.</span><span class="sxs-lookup"><span data-stu-id="7144e-227">Never expose a public Remoting endpoint to the Internet or untrusted clients.</span></span>  
  
#### <a name="security-in-wcf"></a><span data-ttu-id="7144e-228">Zabezpieczenia w programie WCF</span><span class="sxs-lookup"><span data-stu-id="7144e-228">Security in WCF</span></span>  
 <span data-ttu-id="7144e-229">Funkcja WCF została zaprojektowana z myślą o bezpieczeństwie, w części dotyczącej rodzaju luk w zabezpieczeniach platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="7144e-229">WCF was designed with security in mind, in part to address the kinds of vulnerabilities found in .NET Remoting.</span></span> <span data-ttu-id="7144e-230">Usługa WCF oferuje zabezpieczenia zarówno na poziomie transportu, jak i komunikatów, a ponadto oferuje wiele opcji uwierzytelniania, autoryzacji, szyfrowania i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="7144e-230">WCF offers security at both the transport and message level, and offers many options for authentication, authorization, encryption, and so on.</span></span> <span data-ttu-id="7144e-231">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="7144e-231">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="7144e-232">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="7144e-232">Security</span></span>](./feature-details/security.md)  
  
- [<span data-ttu-id="7144e-233">Wskazówki dotyczące zabezpieczeń programu WCF</span><span class="sxs-lookup"><span data-stu-id="7144e-233">WCF Security Guidance</span></span>](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a><span data-ttu-id="7144e-234">Migrowanie do programu WCF</span><span class="sxs-lookup"><span data-stu-id="7144e-234">Migrating to WCF</span></span>  
  
### <a name="why-migrate-from-remoting-to-wcf"></a><span data-ttu-id="7144e-235">Dlaczego należy przeprowadzić migrację z usług zdalnych do WCF?</span><span class="sxs-lookup"><span data-stu-id="7144e-235">Why Migrate from Remoting to WCF?</span></span>  
  
- <span data-ttu-id="7144e-236">**Komunikacja zdalna .NET to starszy produkt.**</span><span class="sxs-lookup"><span data-stu-id="7144e-236">**.NET Remoting is a legacy product.**</span></span> <span data-ttu-id="7144e-237">Zgodnie z opisem w [komunikacji zdalnej .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), jest uznawany za starszy produkt i nie jest zalecany w przypadku nowych rozwiązań programistycznych.</span><span class="sxs-lookup"><span data-stu-id="7144e-237">As described in [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), it is considered a legacy product and is not recommended for new development.</span></span> <span data-ttu-id="7144e-238">W przypadku nowych i istniejących aplikacji zaleca się używanie interfejsu API sieci Web WCF lub ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7144e-238">WCF or ASP.NET Web API are recommended for new and existing applications.</span></span>  
  
- <span data-ttu-id="7144e-239">**Funkcja WCF stosuje standardy dla wielu platform.**</span><span class="sxs-lookup"><span data-stu-id="7144e-239">**WCF uses cross-platform standards.**</span></span> <span data-ttu-id="7144e-240">Program WCF został zaprojektowany z myślą o współdziałaniu między platformami i obsługuje wiele standardów branżowych (SOAP, WS-Security, WS-Trust itp.).</span><span class="sxs-lookup"><span data-stu-id="7144e-240">WCF was designed with cross-platform interoperability in mind and supports many industry standards (SOAP, WS-Security, WS-Trust, etc.).</span></span> <span data-ttu-id="7144e-241">Usługa WCF może współpracować z klientami uruchomionymi w systemach operacyjnych innych niż Windows.</span><span class="sxs-lookup"><span data-stu-id="7144e-241">A WCF service can interoperate with clients running on operating systems other than Windows.</span></span> <span data-ttu-id="7144e-242">Komunikacja zdalna została zaprojektowana głównie dla środowisk, w których zarówno serwer, jak i aplikacje klienckie działają przy użyciu programu .NET Framework w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="7144e-242">Remoting was designed primarily for environments where both the server and client applications run using the .NET framework on a Windows operating system.</span></span>  
  
- <span data-ttu-id="7144e-243">**Funkcja WCF ma wbudowane zabezpieczenia.**</span><span class="sxs-lookup"><span data-stu-id="7144e-243">**WCF has built-in security.**</span></span> <span data-ttu-id="7144e-244">Funkcja WCF została zaprojektowana z myślą o bezpieczeństwie i oferuje wiele opcji uwierzytelniania, zabezpieczeń na poziomie transportu, zabezpieczeń na poziomie komunikatów itp. Komunikacja zdalna została zaprojektowana w celu ułatwienia współpracy aplikacji, ale nie została zaprojektowana w taki sposób, aby była zabezpieczona w środowiskach niezaufanych.</span><span class="sxs-lookup"><span data-stu-id="7144e-244">WCF was designed with security in mind and offers many options for authentication, transport level security, message level security, etc. Remoting was designed to make it easy for applications to interoperate but was not designed to be secure in non-trusted environments.</span></span> <span data-ttu-id="7144e-245">Funkcja WCF została zaprojektowana tak, aby działała zarówno w środowiskach zaufanych, jak i niezaufanych.</span><span class="sxs-lookup"><span data-stu-id="7144e-245">WCF was designed to work in both trusted and non-trusted environments.</span></span>  
  
### <a name="migration-recommendations"></a><span data-ttu-id="7144e-246">Zalecenia dotyczące migracji</span><span class="sxs-lookup"><span data-stu-id="7144e-246">Migration Recommendations</span></span>  
 <span data-ttu-id="7144e-247">Poniżej przedstawiono zalecane kroki migracji z komunikacji zdalnej platformy .NET do programu WCF:</span><span class="sxs-lookup"><span data-stu-id="7144e-247">The following are the recommended steps to migrate from .NET Remoting to WCF:</span></span>  
  
- <span data-ttu-id="7144e-248">**Utwórz kontrakt usługi.**</span><span class="sxs-lookup"><span data-stu-id="7144e-248">**Create the service contract.**</span></span> <span data-ttu-id="7144e-249">Zdefiniuj typy interfejsów usługi i oznacz je atrybutem [ServiceContract]. Oznacz wszystkie metody, które będą mogły być wywoływane przez klientów [OperationContract].</span><span class="sxs-lookup"><span data-stu-id="7144e-249">Define your service interface types, and mark them with the [ServiceContract] attribute.Mark all the methods the clients will be allowed to call with [OperationContract].</span></span>  
  
- <span data-ttu-id="7144e-250">**Utwórz kontrakt danych.**</span><span class="sxs-lookup"><span data-stu-id="7144e-250">**Create the data contract.**</span></span> <span data-ttu-id="7144e-251">Zdefiniuj typy danych, które będą wymieniane między serwerem a klientem i oznacz je atrybutem [DataContract].</span><span class="sxs-lookup"><span data-stu-id="7144e-251">Define the data types that will be exchanged between server and client, and mark them with the [DataContract] attribute.</span></span> <span data-ttu-id="7144e-252">Oznacz wszystkie pola i właściwości, których klient będzie mógł używać z [DataMember].</span><span class="sxs-lookup"><span data-stu-id="7144e-252">Mark all the fields and properties the client will be allowed to use with [DataMember].</span></span>  
  
- <span data-ttu-id="7144e-253">**Utwórz kontrakt błędu (opcjonalnie).**</span><span class="sxs-lookup"><span data-stu-id="7144e-253">**Create the fault contract (optional).**</span></span> <span data-ttu-id="7144e-254">Utwórz typy, które będą wymieniane między serwerem a klientem po napotkaniu błędów.</span><span class="sxs-lookup"><span data-stu-id="7144e-254">Create the types that will be exchanged between server and client when errors are encountered.</span></span> <span data-ttu-id="7144e-255">Oznacz te typy elementami [DataContract] i [DataMember], aby je serializować.</span><span class="sxs-lookup"><span data-stu-id="7144e-255">Mark these types with [DataContract] and [DataMember] to make them serializable.</span></span> <span data-ttu-id="7144e-256">Dla wszystkich operacji usługi, które zostały oznaczone za pomocą elementu [OperationContract], należy również oznaczyć je jako [FaultContract], aby wskazać, które błędy mogą zostać zwrócone.</span><span class="sxs-lookup"><span data-stu-id="7144e-256">For all service operations you marked with [OperationContract], also mark them with [FaultContract] to indicate which errors they may return.</span></span>  
  
- <span data-ttu-id="7144e-257">**Skonfigurowanie i Hostowanie usługi.**</span><span class="sxs-lookup"><span data-stu-id="7144e-257">**Configure and host the service.**</span></span> <span data-ttu-id="7144e-258">Po utworzeniu kontraktu usługi następnym krokiem jest skonfigurowanie powiązania, aby uwidocznić usługę w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="7144e-258">Once the service contract has been created, the next step is to configure a binding to expose the service at an endpoint.</span></span> <span data-ttu-id="7144e-259">Aby uzyskać więcej informacji, [Zobacz punkty końcowe: Adresy, powiązania i kontrakty](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="7144e-259">For more information, see [Endpoints: Addresses, Bindings, and Contracts](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span></span>  
  
 <span data-ttu-id="7144e-260">Po przeprowadzeniu migracji aplikacji zdalnej do programu WCF nadal trzeba usunąć zależności dotyczące komunikacji zdalnej platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="7144e-260">Once a Remoting application has been migrated to WCF, it is still important to remove dependencies on .NET Remoting.</span></span> <span data-ttu-id="7144e-261">Dzięki temu wszystkie luki w zabezpieczeniach zdalnych zostaną usunięte z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7144e-261">This ensures that any Remoting vulnerabilities are removed from the application.</span></span> <span data-ttu-id="7144e-262">Następujące kroki obejmują:</span><span class="sxs-lookup"><span data-stu-id="7144e-262">These steps include the following:</span></span>  
  
- <span data-ttu-id="7144e-263">**Zaprzestanie korzystania z MarshalByRefObject.**</span><span class="sxs-lookup"><span data-stu-id="7144e-263">**Discontinue use of MarshalByRefObject.**</span></span> <span data-ttu-id="7144e-264">Typ MarshalByRefObject istnieje tylko w przypadku komunikacji zdalnej i nie jest używany przez WCF.</span><span class="sxs-lookup"><span data-stu-id="7144e-264">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="7144e-265">Wszystkie typy aplikacji, które podklasy MarshalByRefObject należy usunąć lub zmienić.</span><span class="sxs-lookup"><span data-stu-id="7144e-265">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span>  
  
- <span data-ttu-id="7144e-266">**Zaprzestanie używania [Serializable] i ISerializable.**</span><span class="sxs-lookup"><span data-stu-id="7144e-266">**Discontinue use of [Serializable] and ISerializable.**</span></span> <span data-ttu-id="7144e-267">Atrybut [Serializable] i interfejs ISerializable zostały pierwotnie zaprojektowane do serializacji typów w zaufanych środowiskach i są używane przez funkcję komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="7144e-267">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="7144e-268">Serializacja WCF opiera się na typach oznaczonych za pomocą elementu [DataContract] i [DataMember].</span><span class="sxs-lookup"><span data-stu-id="7144e-268">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="7144e-269">Typy danych używane przez aplikację należy zmodyfikować tak, aby używały elementu [DataContract], a nie do użycia interfejsu ISerializable lub [Serializable].</span><span class="sxs-lookup"><span data-stu-id="7144e-269">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span>  
  
### <a name="migration-scenarios"></a><span data-ttu-id="7144e-270">Scenariusze migracji</span><span class="sxs-lookup"><span data-stu-id="7144e-270">Migration Scenarios</span></span>  
 <span data-ttu-id="7144e-271">Teraz zobaczmy, jak wykonywać następujące typowe scenariusze komunikacji zdalnej w programie WCF:</span><span class="sxs-lookup"><span data-stu-id="7144e-271">Now let’s see how to accomplish the following common Remoting scenarios in WCF:</span></span>  
  
1. <span data-ttu-id="7144e-272">Serwer zwraca obiekt przez wartość do klienta</span><span class="sxs-lookup"><span data-stu-id="7144e-272">Server returns an object by-value to the client</span></span>  
  
2. <span data-ttu-id="7144e-273">Serwer zwraca obiekt przez odwołanie do klienta</span><span class="sxs-lookup"><span data-stu-id="7144e-273">Server returns an object by-reference to the client</span></span>  
  
3. <span data-ttu-id="7144e-274">Klient wysyła obiekt według wartości do serwera</span><span class="sxs-lookup"><span data-stu-id="7144e-274">Client sends an object by-value to the server</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7144e-275">Wysyłanie obiektu przez odwołanie z klienta do serwera nie jest dozwolone w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="7144e-275">Sending an object by-reference from the client to the server is not allowed in WCF.</span></span>  
  
 <span data-ttu-id="7144e-276">Podczas czytania w tych scenariuszach Załóżmy, że nasze interfejsy bazowe dla komunikacji zdalnej platformy .NET wyglądają jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7144e-276">When reading through these scenarios, assume our baseline interfaces for .NET Remoting look like the following example.</span></span> <span data-ttu-id="7144e-277">Implementacja komunikacji zdalnej platformy .NET nie jest ważna w tym miejscu, ponieważ chcemy zilustrować, jak używać programu WCF do implementowania równoważnej funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="7144e-277">The .NET Remoting implementation is not important here because we want to illustrate only how to use WCF to implement equivalent functionality.</span></span>  
  
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
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a><span data-ttu-id="7144e-278">Scenariusz 1: Usługa zwraca obiekt przez wartość</span><span class="sxs-lookup"><span data-stu-id="7144e-278">Scenario 1: Service Returns an Object by Value</span></span>  
 <span data-ttu-id="7144e-279">W tym scenariuszu zademonstrowano serwer zwracający obiekt do klienta przez wartość.</span><span class="sxs-lookup"><span data-stu-id="7144e-279">This scenario demonstrates a server returning an object to the client by value.</span></span> <span data-ttu-id="7144e-280">Program WCF zawsze zwraca obiekty z serwera według wartości, dlatego w następujących krokach opisano sposób tworzenia normalnej usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="7144e-280">WCF always returns objects from the server by value, so the following steps simply describe how to build a normal WCF service.</span></span>  
  
1. <span data-ttu-id="7144e-281">Zacznij od zdefiniowania interfejsu publicznego dla usługi WCF i oznacz go atrybutem [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="7144e-281">Start by defining a public interface for the WCF service and mark it with the [ServiceContract] attribute.</span></span> <span data-ttu-id="7144e-282">Używamy [OperationContract], aby identyfikować metody po stronie serwera, które będą wywoływane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="7144e-282">We use [OperationContract] to identify the server-side methods our client will call.</span></span>  
  
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
  
2. <span data-ttu-id="7144e-283">Następnym krokiem jest utworzenie kontraktu danych dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="7144e-283">The next step is to create the data contract for this service.</span></span> <span data-ttu-id="7144e-284">W tym celu należy utworzyć klasy (nie interfejsy) oznaczone za pomocą atrybutu [DataContract].</span><span class="sxs-lookup"><span data-stu-id="7144e-284">We do this by creating classes (not interfaces) marked with the [DataContract] attribute.</span></span> <span data-ttu-id="7144e-285">Poszczególne właściwości lub pola, które mają być widoczne dla klienta i serwera, są oznaczone za pomocą [DataMember].</span><span class="sxs-lookup"><span data-stu-id="7144e-285">The individual properties or fields we want visible to both client and server are marked with [DataMember].</span></span> <span data-ttu-id="7144e-286">Jeśli chcemy, aby typy pochodne były dozwolone, należy użyć atrybutu [KnownType], aby je zidentyfikować.</span><span class="sxs-lookup"><span data-stu-id="7144e-286">If we want derived types to be allowed, we must use the [KnownType] attribute to identify them.</span></span> <span data-ttu-id="7144e-287">Jedyne typy WCF umożliwią serializacji lub deserializacji dla tej usługi są te w interfejsie usługi i tych "znanych typach".</span><span class="sxs-lookup"><span data-stu-id="7144e-287">The only types WCF will allow to be serialized or deserialized for this service are those in the service interface and these "known types".</span></span> <span data-ttu-id="7144e-288">Próba wymiany dowolnego innego typu, którego nie ma na liście, zostanie odrzucona.</span><span class="sxs-lookup"><span data-stu-id="7144e-288">Attempting to exchange any other type not in this list will be rejected.</span></span>  
  
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
  
3. <span data-ttu-id="7144e-289">Następnie udostępnimy implementację interfejsu usługi.</span><span class="sxs-lookup"><span data-stu-id="7144e-289">Next, we provide the implementation for the service interface.</span></span>  
  
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
  
4. <span data-ttu-id="7144e-290">Aby uruchomić usługę WCF, musimy zadeklarować punkt końcowy, który ujawnia ten interfejs usługi w określonym adresie URL przy użyciu określonego powiązania WCF.</span><span class="sxs-lookup"><span data-stu-id="7144e-290">To run the WCF service, we need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="7144e-291">Zwykle jest to wykonywane przez dodanie poniższych sekcji do pliku Web. config projektu serwera.</span><span class="sxs-lookup"><span data-stu-id="7144e-291">This is typically done by adding the following sections to the server project’s web.config file.</span></span>  
  
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
  
5. <span data-ttu-id="7144e-292">Następnie można uruchomić usługę WCF przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="7144e-292">The WCF service can then be started with the following code:</span></span>  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     <span data-ttu-id="7144e-293">Po uruchomieniu tego elementu ServiceHost używa on pliku Web. config w celu ustanowienia właściwego kontraktu, powiązania i punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="7144e-293">When this ServiceHost is started, it uses the web.config file to establish the proper contract, binding and endpoint.</span></span> <span data-ttu-id="7144e-294">Aby uzyskać więcej informacji na temat plików konfiguracji, zobacz [Konfigurowanie usług przy użyciu plików konfiguracji](./configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="7144e-294">For more information about configuration files, see [Configuring Services Using Configuration Files](./configuring-services-using-configuration-files.md).</span></span> <span data-ttu-id="7144e-295">Ten styl uruchamiania serwera jest znany jako samohosting.</span><span class="sxs-lookup"><span data-stu-id="7144e-295">This style of starting the server is known as self-hosting.</span></span> <span data-ttu-id="7144e-296">Aby dowiedzieć się więcej o innych opcjach hostingu usług WCF, zobacz [usługi hostingu](./hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="7144e-296">To learn more about other choices for hosting WCF services, see [Hosting Services](./hosting-services.md).</span></span>  
  
6. <span data-ttu-id="7144e-297">Plik App. config projektu klienta musi deklarować pasujące informacje o powiązaniu dla punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="7144e-297">The client project’s app.config must declare matching binding information for the service’s endpoint.</span></span> <span data-ttu-id="7144e-298">Najprostszym sposobem wykonania tej czynności w programie Visual Studio jest użycie **Dodaj odwołanie do usługi**, która spowoduje automatyczne zaktualizowanie pliku App. config.</span><span class="sxs-lookup"><span data-stu-id="7144e-298">The easiest way to do this in Visual Studio is to use **Add Service Reference**, which will automatically update the app.config file.</span></span> <span data-ttu-id="7144e-299">Alternatywnie te same zmiany można dodać ręcznie.</span><span class="sxs-lookup"><span data-stu-id="7144e-299">Alternatively, these same changes can be added manually.</span></span>  
  
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
  
     <span data-ttu-id="7144e-300">Aby uzyskać więcej informacji okorzystaniu z [Dodaj odwołanie do usługi, zobacz How to: Dodaj, zaktualizuj lub usuń odwołanie](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)do usługi.</span><span class="sxs-lookup"><span data-stu-id="7144e-300">For more information about using **Add Service Reference**, see [How to: Add, Update, or Remove a Service Reference](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span></span>  
  
7. <span data-ttu-id="7144e-301">Teraz możemy wywołać usługę WCF od klienta.</span><span class="sxs-lookup"><span data-stu-id="7144e-301">Now we can call the WCF service from the client.</span></span> <span data-ttu-id="7144e-302">Możemy to zrobić, tworząc fabrykę kanałów dla tej usługi, zwracając ją na kanał i bezpośrednio wywołując metodę, którą chcemy w tym kanale.</span><span class="sxs-lookup"><span data-stu-id="7144e-302">We do this by creating a channel factory for that service, asking it for a channel, and directly calling the method we want on that channel.</span></span> <span data-ttu-id="7144e-303">Można to zrobić, ponieważ kanał implementuje interfejs usługi i obsługuje podstawową logikę żądania/odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="7144e-303">We can do this because the channel implements the service’s interface and handles the underlying request/reply logic for us.</span></span> <span data-ttu-id="7144e-304">Wartością zwracaną z tego wywołania metody jest deserializowana kopia odpowiedzi serwera.</span><span class="sxs-lookup"><span data-stu-id="7144e-304">The return value from that method call is the deserialized copy of the server’s response.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 <span data-ttu-id="7144e-305">Obiekty zwracane przez WCF z serwera do klienta są zawsze przez wartość.</span><span class="sxs-lookup"><span data-stu-id="7144e-305">Objects returned by WCF from the server to the client are always by value.</span></span> <span data-ttu-id="7144e-306">Obiekty są deserializowanymi kopiami danych wysyłanych przez serwer.</span><span class="sxs-lookup"><span data-stu-id="7144e-306">The objects are deserialized copies of the data sent by the server.</span></span> <span data-ttu-id="7144e-307">Klient może wywoływać metody dla tych kopii lokalnych bez jakichkolwiek zagrożeń związanych z wywoływaniem kodu serwera za pomocą wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="7144e-307">The client can call methods on these local copies without any danger of invoking server code through callbacks.</span></span>  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a><span data-ttu-id="7144e-308">Scenariusz 2: Serwer zwraca obiekt przez odwołanie</span><span class="sxs-lookup"><span data-stu-id="7144e-308">Scenario 2: Server Returns an Object By Reference</span></span>  
 <span data-ttu-id="7144e-309">W tym scenariuszu pokazano serwer dostarczający obiekt do klienta przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="7144e-309">This scenario demonstrates the server providing an object to the client by reference.</span></span> <span data-ttu-id="7144e-310">W przypadku komunikacji zdalnej .NET jest to obsługiwane automatycznie dla dowolnego typu pochodnego od MarshalByRefObject, który jest serializowany przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="7144e-310">In .NET Remoting, this is handled automatically for any type derived from MarshalByRefObject, which is serialized by-reference.</span></span> <span data-ttu-id="7144e-311">Przykładem tego scenariusza jest umożliwienie wielu klientom niezależnych obiektów po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="7144e-311">An example of this scenario is allowing multiple clients to have independent sessionful server-side objects.</span></span> <span data-ttu-id="7144e-312">Jak wspomniano wcześniej, obiekty zwrócone przez usługę WCF są zawsze przez wartość, więc nie istnieje bezpośredni odpowiednik obiektu przez odwołanie, ale możliwe jest osiągnięcie czegoś podobnego do semantyki odniesienia przy użyciu <xref:System.ServiceModel.EndpointAddress10> obiektu.</span><span class="sxs-lookup"><span data-stu-id="7144e-312">As previously mentioned, objects returned by a WCF service are always by value, so there is no direct equivalent of a by-reference object, but it is possible to achieve something similar to by-reference semantics using an <xref:System.ServiceModel.EndpointAddress10> object.</span></span> <span data-ttu-id="7144e-313">Jest to obiekt możliwy do serializacji przez wartość, który może być używany przez klienta w celu uzyskania na serwerze sesji na podstawie obiektu referencyjnego.</span><span class="sxs-lookup"><span data-stu-id="7144e-313">This is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span> <span data-ttu-id="7144e-314">Dzięki temu scenariusz ma wiele klientów z niezależnymi obiektami po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="7144e-314">This enables the scenario of having multiple clients with independent sessionful server-side objects.</span></span>  
  
1. <span data-ttu-id="7144e-315">Najpierw należy zdefiniować kontrakt usługi WCF, który odpowiada obiektowi sesji.</span><span class="sxs-lookup"><span data-stu-id="7144e-315">First, we need to define a WCF service contract that corresponds to the sessionful object itself.</span></span>  
  
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
    > <span data-ttu-id="7144e-316">Zwróć uwagę, że obiekt sesji jest oznaczony za pomocą elementu [ServiceContract], co sprawia, że jest to normalny interfejs usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="7144e-316">Notice that the sessionful object is marked with [ServiceContract], making it a normal WCF service interface.</span></span> <span data-ttu-id="7144e-317">Ustawienie właściwości SessionMode wskazuje, że będzie ona usługą sesji.</span><span class="sxs-lookup"><span data-stu-id="7144e-317">Setting the SessionMode property indicates it will be a sessionful service.</span></span> <span data-ttu-id="7144e-318">W programie WCF sesja jest sposobem skorelowania wielu wiadomości przesyłanych między dwoma punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="7144e-318">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span> <span data-ttu-id="7144e-319">Oznacza to, że gdy klient uzyska połączenie z tą usługą, zostanie ustanowiona sesja między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="7144e-319">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span> <span data-ttu-id="7144e-320">Klient będzie używać jednego unikatowego wystąpienia obiektu po stronie serwera dla wszystkich jego interakcji w ramach jednej sesji.</span><span class="sxs-lookup"><span data-stu-id="7144e-320">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span>  
  
2. <span data-ttu-id="7144e-321">Następnie musimy wprowadzić implementację tego interfejsu usługi.</span><span class="sxs-lookup"><span data-stu-id="7144e-321">Next, we need to provide the implementation of this service interface.</span></span> <span data-ttu-id="7144e-322">Wskazując, że za pomocą [ServiceBehavior] i ustawiając właściwość InstanceContextmode, będziemy informować, że firma Microsoft chce użyć unikatowego wystąpienia tego typu dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="7144e-322">By denoting it with [ServiceBehavior] and setting the InstanceContextMode, we tell WCF we want to use a unique instance of this type for an each session.</span></span>  
  
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
  
3. <span data-ttu-id="7144e-323">Teraz potrzebujemy metody uzyskania wystąpienia tego obiektu sesji.</span><span class="sxs-lookup"><span data-stu-id="7144e-323">Now we need a way to obtain an instance of this sessionful object.</span></span> <span data-ttu-id="7144e-324">W tym celu należy utworzyć inny interfejs usługi WCF, który zwraca obiekt EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="7144e-324">We do this by creating another WCF service interface that returns an EndpointAddress10 object.</span></span> <span data-ttu-id="7144e-325">Jest to możliwy do serializacji formularz punktu końcowego, którego może użyć klient do utworzenia obiektu sesji.</span><span class="sxs-lookup"><span data-stu-id="7144e-325">This is a serializable form of an endpoint that the client can use to create the sessionful object.</span></span>  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     <span data-ttu-id="7144e-326">I implementujemy tę usługę WCF:</span><span class="sxs-lookup"><span data-stu-id="7144e-326">And we implement this WCF service:</span></span>  
  
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
  
     <span data-ttu-id="7144e-327">Ta implementacja obsługuje pojedyncze fabryki kanałów do tworzenia obiektów sesji.</span><span class="sxs-lookup"><span data-stu-id="7144e-327">This implementation maintains a singleton channel factory to create sessionful objects.</span></span> <span data-ttu-id="7144e-328">Gdy wywoływana jest GetInstanceAddress (), tworzy kanał i tworzy obiekt EndpointAddress10, który efektywnie wskazuje adres zdalny skojarzony z tym kanałem.</span><span class="sxs-lookup"><span data-stu-id="7144e-328">When GetInstanceAddress() is called, it creates a channel and creates an EndpointAddress10 object that effectively points to the remote address associated with this channel.</span></span> <span data-ttu-id="7144e-329">EndpointAddress10 jest po prostu typem danych, który może być zwracany do klienta przez wartość.</span><span class="sxs-lookup"><span data-stu-id="7144e-329">EndpointAddress10 is simply a data type that can be returned to the client by-value.</span></span>  
  
4. <span data-ttu-id="7144e-330">Musimy zmodyfikować plik konfiguracji serwera, wykonując następujące dwie czynności, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7144e-330">We need to modify the server’s configuration file by doing the following two things as shown in the example below:</span></span>  
  
    1. <span data-ttu-id="7144e-331">Zadeklaruj sekcję > klienta opisującą punkt końcowy dla obiektu sesji. \<</span><span class="sxs-lookup"><span data-stu-id="7144e-331">Declare a \<client> section that describes the endpoint for the sessionful object.</span></span> <span data-ttu-id="7144e-332">Jest to konieczne, ponieważ serwer działa również jako klient w takiej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="7144e-332">This is necessary because the server also acts as a client in this situation.</span></span>  
  
    2. <span data-ttu-id="7144e-333">Zadeklaruj punkty końcowe dla obiektu fabryki i sesji.</span><span class="sxs-lookup"><span data-stu-id="7144e-333">Declare endpoints for the factory and sessionful object.</span></span> <span data-ttu-id="7144e-334">Jest to konieczne, aby umożliwić klientowi komunikowanie się z punktami końcowymi usługi w celu uzyskania EndpointAddress10 i utworzenia kanału sesji.</span><span class="sxs-lookup"><span data-stu-id="7144e-334">This is necessary to allow the client to communicate with the service endpoints to acquire the EndpointAddress10 and to create the sessionful channel.</span></span>  
  
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
  
     <span data-ttu-id="7144e-335">A następnie możemy uruchomić następujące usługi:</span><span class="sxs-lookup"><span data-stu-id="7144e-335">And then we can start these services:</span></span>  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. <span data-ttu-id="7144e-336">Skonfigurujemy klienta, deklarując te same punkty końcowe w pliku App. config projektu.</span><span class="sxs-lookup"><span data-stu-id="7144e-336">We configure the client by declaring these same endpoints in its project’s app.config file.</span></span>  
  
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
  
6. <span data-ttu-id="7144e-337">Aby można było utworzyć ten obiekt sesji i używać go, klient musi wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="7144e-337">In order to create and use this sessionful object, the client must do the following steps:</span></span>  
  
    1. <span data-ttu-id="7144e-338">Utwórz kanał usługi ISessionBoundFactory.</span><span class="sxs-lookup"><span data-stu-id="7144e-338">Create a channel to the ISessionBoundFactory service.</span></span>  
  
    2. <span data-ttu-id="7144e-339">Użyj tego kanału do wywołania tej usługi w celu uzyskania EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="7144e-339">Use that channel to invoke that service to obtain an EndpointAddress10.</span></span>  
  
    3. <span data-ttu-id="7144e-340">Użyj EndpointAddress10, aby utworzyć kanał, aby uzyskać obiekt sesji.</span><span class="sxs-lookup"><span data-stu-id="7144e-340">Use the EndpointAddress10 to create a channel to obtain a sessionful object.</span></span>  
  
    4. <span data-ttu-id="7144e-341">Pracuj z obiektem Session, aby pokazać, że pozostaje w tym samym wystąpieniu w wielu wywołaniach.</span><span class="sxs-lookup"><span data-stu-id="7144e-341">Interact with the sessionful object to demonstrate it remains the same instance across multiple calls.</span></span>  
  
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
  
 <span data-ttu-id="7144e-342">Funkcja WCF zawsze zwraca obiekty według wartości, ale istnieje możliwość obsługi równoważnej semantyki przez odwołanie za pomocą EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="7144e-342">WCF always returns objects by value, but it is possible to support the equivalent of by-reference semantics through the use of EndpointAddress10.</span></span> <span data-ttu-id="7144e-343">Pozwala to klientowi na zażądanie wystąpienia usługi WCF, po którym może ona współistnieć z nim, podobnie jak w przypadku każdej innej usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="7144e-343">This permits the client to request a sessionful WCF service instance, after which it can interact with it like any other WCF service.</span></span>  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a><span data-ttu-id="7144e-344">Scenariusz 3: Klient wysyła serwer a wystąpienie przez wartość</span><span class="sxs-lookup"><span data-stu-id="7144e-344">Scenario 3: Client Sends Server a By-Value Instance</span></span>  
 <span data-ttu-id="7144e-345">W tym scenariuszu przedstawiono klienta wysyłającego wystąpienie obiektu niepierwotnego do serwera przez wartość.</span><span class="sxs-lookup"><span data-stu-id="7144e-345">This scenario demonstrates the client sending a non-primitive object instance to the server by value.</span></span> <span data-ttu-id="7144e-346">Ponieważ WCF wysyła tylko obiekty według wartości, w tym scenariuszu pokazano normalne użycie programu WCF.</span><span class="sxs-lookup"><span data-stu-id="7144e-346">Because WCF only sends objects by value, this scenario demonstrates normal WCF usage.</span></span>  
  
1. <span data-ttu-id="7144e-347">Użyj tej samej usługi WCF w scenariuszu 1.</span><span class="sxs-lookup"><span data-stu-id="7144e-347">Use the same WCF Service from Scenario 1.</span></span>  
  
2. <span data-ttu-id="7144e-348">Użyj klienta programu, aby utworzyć nowy obiekt według wartości (klienta), utworzyć kanał do komunikacji z usługą ICustomerService i wysłać do niego obiekt.</span><span class="sxs-lookup"><span data-stu-id="7144e-348">Use the client to create a new by-value object (Customer), create a channel to communicate with the ICustomerService service, and send the object to it.</span></span>  
  
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
  
     <span data-ttu-id="7144e-349">Obiekt klienta zostanie Zserializowany i wysłany do serwera, gdzie zostaje rozszeregowany do nowej kopii tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="7144e-349">The customer object will be serialized, and sent to the server, where it is deserialized into a new copy of that object.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7144e-350">Ten kod ilustruje również wysyłanie typu pochodnego (PremiumCustomer).</span><span class="sxs-lookup"><span data-stu-id="7144e-350">This code also illustrates sending a derived type (PremiumCustomer).</span></span> <span data-ttu-id="7144e-351">Interfejs usługi oczekuje obiektu klienta, ale atrybut [KnownType] w klasie Customer wskazujący PremiumCustomer był również dozwolony.</span><span class="sxs-lookup"><span data-stu-id="7144e-351">The service interface expects a Customer object, but the [KnownType] attribute on the Customer class indicated PremiumCustomer was also allowed.</span></span> <span data-ttu-id="7144e-352">W przypadku programu WCF próba serializacji lub deserializacji dowolnego innego typu za poorednictwem tego interfejsu usługi jest niemożliwa.</span><span class="sxs-lookup"><span data-stu-id="7144e-352">WCF will fail any attempt to serialize or deserialize any other type through this service interface.</span></span>  
  
 <span data-ttu-id="7144e-353">Normalne wymianę danych WCF są według wartości.</span><span class="sxs-lookup"><span data-stu-id="7144e-353">Normal WCF exchanges of data are by value.</span></span> <span data-ttu-id="7144e-354">Gwarantuje to, że wywoływanie metod na jednym z tych obiektów danych jest wykonywane tylko lokalnie — nie wywoła kodu w drugiej warstwie.</span><span class="sxs-lookup"><span data-stu-id="7144e-354">This guarantees that invoking methods on one of these data objects executes only locally – it will not invoke code on the other tier.</span></span> <span data-ttu-id="7144e-355">Chociaż możliwe jest osiągnięcie obiektów, takich jak obiekty referencyjne, zwracanych *z* serwera, nie jest możliwe, aby klient przeszedł obiekt przez odwołanie *do* serwera.</span><span class="sxs-lookup"><span data-stu-id="7144e-355">While it is possible to achieve something like by-reference objects returned *from* the server, it is not possible for a client to pass a by-reference object *to* the server.</span></span> <span data-ttu-id="7144e-356">Scenariusz, który wymaga konwersacji między klientem a serwerem można osiągnąć w programie WCF przy użyciu usługi dupleksowej.</span><span class="sxs-lookup"><span data-stu-id="7144e-356">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span> <span data-ttu-id="7144e-357">Aby uzyskać więcej informacji, zobacz [usługi dupleksowe](./feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="7144e-357">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="7144e-358">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="7144e-358">Summary</span></span>  
 <span data-ttu-id="7144e-359">Komunikacja zdalna .NET to struktura komunikacji przeznaczona do użycia tylko w środowiskach w pełni zaufanych.</span><span class="sxs-lookup"><span data-stu-id="7144e-359">.NET Remoting is a communication framework intended to be used only within fully-trusted environments.</span></span> <span data-ttu-id="7144e-360">Jest to starszy produkt i jest obsługiwany tylko w celu zapewnienia zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="7144e-360">It is a legacy product and supported only for backward compatibility.</span></span> <span data-ttu-id="7144e-361">Nie należy używać go do kompilowania nowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7144e-361">It should not be used to build new applications.</span></span> <span data-ttu-id="7144e-362">Z kolei platforma WCF została zaprojektowana z myślą o bezpieczeństwie i jest zalecana w przypadku nowych i istniejących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7144e-362">Conversely, WCF was designed with security in mind and is recommended for new and existing applications.</span></span> <span data-ttu-id="7144e-363">Firma Microsoft zaleca, aby w zamian przeprowadzić migrację istniejących aplikacji zdalnych do korzystania z interfejsu API sieci Web WCF lub ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7144e-363">Microsoft recommends that existing Remoting applications be migrated to use WCF or ASP.NET Web API instead.</span></span>
