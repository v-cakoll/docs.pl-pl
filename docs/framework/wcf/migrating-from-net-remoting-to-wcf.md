---
title: Migrowanie z programu .NET Remoting do programu WCF
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: 91cbfa33c6645fbc0a8d9b513e3a59799114a710
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200101"
---
# <a name="migrating-from-net-remoting-to-wcf"></a><span data-ttu-id="7cba9-102">Migrowanie z programu .NET Remoting do programu WCF</span><span class="sxs-lookup"><span data-stu-id="7cba9-102">Migrating from .NET Remoting to WCF</span></span>
<span data-ttu-id="7cba9-103">W tym artykule opisano sposób migrowania aplikacji korzystającej z wywołaniem funkcji zdalnych .NET do użycia usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7cba9-103">This article describes how to migrate an application that uses .NET Remoting to use Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="7cba9-104">Jego porównuje podobne pojęcia między tymi produktami, a następnie w tym artykule opisano sposób wykonywania kilku typowych scenariuszy komunikacji zdalnej programu WCF.</span><span class="sxs-lookup"><span data-stu-id="7cba9-104">It compares similar concepts between these products and then describes how to accomplish several common Remoting scenarios in WCF.</span></span>  
  
 <span data-ttu-id="7cba9-105">Wywołaniem funkcji zdalnych .NET jest starszy produkt, który jest obsługiwany tylko w przypadku zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="7cba9-105">.NET Remoting is a legacy product that is supported only for backward compatibility.</span></span> <span data-ttu-id="7cba9-106">Nie jest bezpieczny w środowiskach mieszanych zaufania, ponieważ nie można zachować, poziomy zaufania oddzielne między klientem i serwerem.</span><span class="sxs-lookup"><span data-stu-id="7cba9-106">It is not secure across mixed-trust environments because it cannot maintain the separate trust levels between client and server.</span></span> <span data-ttu-id="7cba9-107">Na przykład nigdy nie powinny ujawniać punkt końcowy wywołaniem funkcji zdalnych .NET do Internetu lub niezaufanego klientami.</span><span class="sxs-lookup"><span data-stu-id="7cba9-107">For example, you should never expose a .NET Remoting endpoint to the Internet or to untrusted clients.</span></span> <span data-ttu-id="7cba9-108">Firma Microsoft zaleca Remoting istniejące aplikacje można migrować do nowszych i bardziej bezpieczne technologii.</span><span class="sxs-lookup"><span data-stu-id="7cba9-108">We recommend existing Remoting applications be migrated to newer and more secure technologies.</span></span> <span data-ttu-id="7cba9-109">Jeśli projekt aplikacji używa tylko protokołu HTTP i jest zgodne ze specyfikacją REST, firma Microsoft zaleca interfejsu API sieci Web platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7cba9-109">If the application’s design uses only HTTP and is RESTful, we recommend ASP.NET Web API.</span></span> <span data-ttu-id="7cba9-110">Aby uzyskać więcej informacji zobacz interfejs API sieci Web platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7cba9-110">For more information, see ASP.NET Web API.</span></span> <span data-ttu-id="7cba9-111">Jeśli aplikacja jest oparta na SOAP lub wymaga protokołów innych niż Http, takich jak TCP, firma Microsoft zaleca WCF.</span><span class="sxs-lookup"><span data-stu-id="7cba9-111">If the application is based on SOAP or requires non-Http protocols such as TCP, we recommend WCF.</span></span>  

## <a name="comparing-net-remoting-to-wcf"></a><span data-ttu-id="7cba9-112">Porównywanie .NET Remoting do programu WCF</span><span class="sxs-lookup"><span data-stu-id="7cba9-112">Comparing .NET Remoting to WCF</span></span>  
 <span data-ttu-id="7cba9-113">W tej sekcji przedstawiono porównanie podstawowych bloków konstrukcyjnych wywołaniem funkcji zdalnych .NET przy użyciu ich odpowiedników WCF.</span><span class="sxs-lookup"><span data-stu-id="7cba9-113">This section compares the basic building blocks of .NET Remoting with their WCF equivalents.</span></span> <span data-ttu-id="7cba9-114">Firma Microsoft użyje tych bloków konstrukcyjnych później utworzyć kilka typowych scenariuszy, klient serwer programu WCF. Poniższy wykres zawiera podsumowanie głównych podobieństwa i różnice między wywołaniem funkcji zdalnych .NET i usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="7cba9-114">We will use these building blocks later to create some common client-server scenarios in WCF.The following chart summarizes the main similarities and differences between .NET Remoting and WCF.</span></span>  
  
||<span data-ttu-id="7cba9-115">Wywołaniem funkcji zdalnych .NET</span><span class="sxs-lookup"><span data-stu-id="7cba9-115">.NET Remoting</span></span>|<span data-ttu-id="7cba9-116">WCF</span><span class="sxs-lookup"><span data-stu-id="7cba9-116">WCF</span></span>|  
|-|-------------------|---------|  
|<span data-ttu-id="7cba9-117">Typ serwera</span><span class="sxs-lookup"><span data-stu-id="7cba9-117">Server type</span></span>|<span data-ttu-id="7cba9-118">Podklasy MarshalByRefObject</span><span class="sxs-lookup"><span data-stu-id="7cba9-118">Subclass MarshalByRefObject</span></span>|<span data-ttu-id="7cba9-119">Oznacz za pomocą atrybutu [ServiceContract]</span><span class="sxs-lookup"><span data-stu-id="7cba9-119">Mark with [ServiceContract] attribute</span></span>|  
|<span data-ttu-id="7cba9-120">Operacje usługi</span><span class="sxs-lookup"><span data-stu-id="7cba9-120">Service operations</span></span>|<span data-ttu-id="7cba9-121">Metody publiczne na typ serwera</span><span class="sxs-lookup"><span data-stu-id="7cba9-121">Public methods on server type</span></span>|<span data-ttu-id="7cba9-122">Oznacz za pomocą atrybutu [elementu OperationContract]</span><span class="sxs-lookup"><span data-stu-id="7cba9-122">Mark with [OperationContract] attribute</span></span>|  
|<span data-ttu-id="7cba9-123">Serializacja</span><span class="sxs-lookup"><span data-stu-id="7cba9-123">Serialization</span></span>|<span data-ttu-id="7cba9-124">Typ iSerializable lub [Serializable]</span><span class="sxs-lookup"><span data-stu-id="7cba9-124">ISerializable or [Serializable]</span></span>|<span data-ttu-id="7cba9-125">DataContractSerializer, lub elementu XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="7cba9-125">DataContractSerializer or XmlSerializer</span></span>|  
|<span data-ttu-id="7cba9-126">Obiekty przekazany</span><span class="sxs-lookup"><span data-stu-id="7cba9-126">Objects passed</span></span>|<span data-ttu-id="7cba9-127">Przez wartość lub przez odwołanie</span><span class="sxs-lookup"><span data-stu-id="7cba9-127">By-value or by-reference</span></span>|<span data-ttu-id="7cba9-128">Przez wartość tylko</span><span class="sxs-lookup"><span data-stu-id="7cba9-128">By-value only</span></span>|  
|<span data-ttu-id="7cba9-129">Błędy/wyjątków</span><span class="sxs-lookup"><span data-stu-id="7cba9-129">Errors/exceptions</span></span>|<span data-ttu-id="7cba9-130">Każdy wyjątek, możliwy do serializacji</span><span class="sxs-lookup"><span data-stu-id="7cba9-130">Any serializable exception</span></span>|<span data-ttu-id="7cba9-131">FaultContract\<TDetail></span><span class="sxs-lookup"><span data-stu-id="7cba9-131">FaultContract\<TDetail></span></span>|  
|<span data-ttu-id="7cba9-132">Obiekty serwera proxy klienta</span><span class="sxs-lookup"><span data-stu-id="7cba9-132">Client proxy objects</span></span>|<span data-ttu-id="7cba9-133">Silnie typizowane przezroczystych obiektów proxy są tworzone automatycznie na podstawie MarshalByRefObjects</span><span class="sxs-lookup"><span data-stu-id="7cba9-133">Strongly typed transparent proxies are created automatically from MarshalByRefObjects</span></span>|<span data-ttu-id="7cba9-134">Silnie typizowane serwery proxy są generowane na żądanie przy użyciu elementu ChannelFactory\<TChannel ></span><span class="sxs-lookup"><span data-stu-id="7cba9-134">Strongly typed proxies are generated on-demand using ChannelFactory\<TChannel></span></span>|  
|<span data-ttu-id="7cba9-135">Platforma wymagane</span><span class="sxs-lookup"><span data-stu-id="7cba9-135">Platform required</span></span>|<span data-ttu-id="7cba9-136">Zarówno klient, jak i serwera, należy użyć OS firmy Microsoft i platformy .NET</span><span class="sxs-lookup"><span data-stu-id="7cba9-136">Both client and server must use Microsoft OS and .NET</span></span>|<span data-ttu-id="7cba9-137">Dla wielu platform</span><span class="sxs-lookup"><span data-stu-id="7cba9-137">Cross-platform</span></span>|  
|<span data-ttu-id="7cba9-138">Format komunikatu</span><span class="sxs-lookup"><span data-stu-id="7cba9-138">Message format</span></span>|<span data-ttu-id="7cba9-139">Private</span><span class="sxs-lookup"><span data-stu-id="7cba9-139">Private</span></span>|<span data-ttu-id="7cba9-140">Standardy branżowe (protokołu SOAP, WS-\*, itp.)</span><span class="sxs-lookup"><span data-stu-id="7cba9-140">Industry standards (SOAP, WS-\*, etc.)</span></span>|  
  
### <a name="server-implementation-comparison"></a><span data-ttu-id="7cba9-141">Porównanie wdrożenia serwera</span><span class="sxs-lookup"><span data-stu-id="7cba9-141">Server Implementation Comparison</span></span>  
  
#### <a name="creating-a-server-in-net-remoting"></a><span data-ttu-id="7cba9-142">Tworzenie serwera w wywołaniem funkcji zdalnych .NET</span><span class="sxs-lookup"><span data-stu-id="7cba9-142">Creating a Server in .NET Remoting</span></span>  
 <span data-ttu-id="7cba9-143">Typy serwerów wywołaniem funkcji zdalnych .NET musi pochodzić od elementu MarshalByRefObject i definiowania metod, które klient może wywołać, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="7cba9-143">.NET Remoting server types must derive from MarshalByRefObject and define methods the client can call, like the following:</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="7cba9-144">Metody publiczne ten typ serwera stanie zamówienia publicznego dostępne dla klientów.</span><span class="sxs-lookup"><span data-stu-id="7cba9-144">The public methods of this server type become the public contract available to clients.</span></span>  <span data-ttu-id="7cba9-145">Brak oddzielenie interfejsu publicznego serwera i jego wdrożenie — jeden typ obsługuje obie.</span><span class="sxs-lookup"><span data-stu-id="7cba9-145">There is no separation between the server’s public interface and its implementation – one type handles both.</span></span>  
  
 <span data-ttu-id="7cba9-146">Po zdefiniowaniu typ serwera może on dostępne dla klientów, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7cba9-146">Once the server type has been defined, it can be made available to clients, like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="7cba9-147">Istnieje wiele sposobów, aby udostępnić typ usług zdalnych jako serwer, w tym za pomocą plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7cba9-147">There are many ways to make the Remoting type available as a server, including using configuration files.</span></span> <span data-ttu-id="7cba9-148">Jest to tylko jeden przykład.</span><span class="sxs-lookup"><span data-stu-id="7cba9-148">This is just one example.</span></span>  
  
#### <a name="creating-a-server-in-wcf"></a><span data-ttu-id="7cba9-149">Tworzenie serwera w programie WCF</span><span class="sxs-lookup"><span data-stu-id="7cba9-149">Creating a Server in WCF</span></span>  
 <span data-ttu-id="7cba9-150">Równoważne etapem WCF związane z utworzeniem dwa typy — publiczny "Umowa serwisowa" i wykonanie.</span><span class="sxs-lookup"><span data-stu-id="7cba9-150">The equivalent step in WCF involves creating two types -- the public "service contract" and the concrete implementation.</span></span> <span data-ttu-id="7cba9-151">Pierwszy jest zadeklarowany jako interfejs oznaczone atrybutem [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="7cba9-151">The first is declared as an interface marked with [ServiceContract].</span></span> <span data-ttu-id="7cba9-152">Metody dostępne dla klientów są oznaczone za pomocą elementu [OperationContract]:</span><span class="sxs-lookup"><span data-stu-id="7cba9-152">Methods available to clients are marked with [OperationContract]:</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="7cba9-153">Implementacja serwera jest zdefiniowana w osobnej klasy konkretnych, takich jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7cba9-153">The server’s implementation is defined in a separate concrete class, like in the following example:</span></span>  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="7cba9-154">Po zdefiniowaniu typu serwera WCF mogą być udostępniane klientom, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7cba9-154">Once these types have been defined, the WCF server can be made available to clients, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
Uri baseAddress = new Uri("net.tcp://localhost:8000/wcfserver");  
  
using (ServiceHost serviceHost = new ServiceHost(typeof(WCFServer), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(IWCFServer), binding, baseAddress);  
    serviceHost.Open();  
  
    Console.WriteLine(String.Format("The WCF server is ready at {0}.",  
                                    baseAddress));  
    Console.WriteLine("Press <ENTER> to terminate service...");  
    Console.WriteLine();  
    Console.ReadLine();  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="7cba9-155">TCP jest używany w obu przykładach, aby były jak najbardziej podobna.</span><span class="sxs-lookup"><span data-stu-id="7cba9-155">TCP is used in both examples to keep them as similar as possible.</span></span> <span data-ttu-id="7cba9-156">Zapoznaj się z przewodników scenariusza w dalszej części tego tematu, przykłady przy użyciu protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cba9-156">Refer to the scenario walk-throughs later in this topic for examples using HTTP.</span></span>  
  
 <span data-ttu-id="7cba9-157">Istnieje wiele sposobów konfigurowania oraz obsługi usług WCF.</span><span class="sxs-lookup"><span data-stu-id="7cba9-157">There are many ways to configure and to host WCF services.</span></span> <span data-ttu-id="7cba9-158">Jest to tylko jeden przykład, znane jako "może być samodzielnie hostowane".</span><span class="sxs-lookup"><span data-stu-id="7cba9-158">This is just one example, known as "self-hosted".</span></span> <span data-ttu-id="7cba9-159">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="7cba9-159">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="7cba9-160">Instrukcje: definiowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="7cba9-160">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)  
  
-   [<span data-ttu-id="7cba9-161">Konfigurowanie usług za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7cba9-161">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
  
-   [<span data-ttu-id="7cba9-162">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="7cba9-162">Hosting Services</span></span>](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a><span data-ttu-id="7cba9-163">Porównanie wdrożenia klienta</span><span class="sxs-lookup"><span data-stu-id="7cba9-163">Client Implementation Comparison</span></span>  
  
#### <a name="creating-a-client-in-net-remoting"></a><span data-ttu-id="7cba9-164">Tworzenie klienta w wywołaniem funkcji zdalnych .NET</span><span class="sxs-lookup"><span data-stu-id="7cba9-164">Creating a Client in .NET Remoting</span></span>  
 <span data-ttu-id="7cba9-165">Gdy obiekt serwera wywołaniem funkcji zdalnych .NET został udostępniony, mogą być używane przez klientów, takie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7cba9-165">Once a .NET Remoting server object has been made available, it can be consumed by clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine(String.Format("Customer {0} {1} received.",   
                                 customer.FirstName, customer.LastName));  
```  
  
 <span data-ttu-id="7cba9-166">Wystąpienie RemotingServer zwróciło Activator.GetObject() jest nazywany "przezroczystym serwerem proxy."</span><span class="sxs-lookup"><span data-stu-id="7cba9-166">The RemotingServer instance returned from Activator.GetObject() is known as a "transparent proxy."</span></span> <span data-ttu-id="7cba9-167">Implementuje publicznego interfejsu API dla typu RemotingServer na komputerze klienckim, ale wszystkie metody wywołania obiektu serwera uruchomionego w inny proces lub komputera.</span><span class="sxs-lookup"><span data-stu-id="7cba9-167">It implements the public API for the RemotingServer type on the client, but all the methods call the server object running in a different process or machine.</span></span>  
  
#### <a name="creating-a-client-in-wcf"></a><span data-ttu-id="7cba9-168">Tworzenie klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="7cba9-168">Creating a Client in WCF</span></span>  
 <span data-ttu-id="7cba9-169">Równoważne etapem WCF polega na tym, za pomocą fabryki kanałów, aby jawnie utworzyć serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="7cba9-169">The equivalent step in WCF involves using a channel factory to create the proxy explicitly.</span></span> <span data-ttu-id="7cba9-170">Podobnie jak obsługa zdalna obiekt serwera proxy może służyć do wywołania operacji na serwerze, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7cba9-170">Like Remoting, the proxy object can be used to invoke operations on the server, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
String url = "net.tcp://localhost:8000/wcfserver";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<IWCFServer> channelFactory =   
    new ChannelFactory<IWCFServer>(binding, address);  
IWCFServer server = channelFactory.CreateChannel();  
  
Customer customer = server.GetCustomer(42);  
Console.WriteLine(String.Format("  Customer {0} {1} received.",  
                    customer.FirstName, customer.LastName));  
```  
  
 <span data-ttu-id="7cba9-171">Ten przykład przedstawia, programowanie na poziomie kanału, ponieważ jest najbardziej podobne do komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="7cba9-171">This example shows programming at the channel level because it is most similar to the Remoting example.</span></span> <span data-ttu-id="7cba9-172">Dostępne jest również **Dodaj odwołanie do usługi** podejście w programie Visual Studio generuje kod, aby uprościć programowanie klienta.</span><span class="sxs-lookup"><span data-stu-id="7cba9-172">Also available is the **Add Service Reference** approach in Visual Studio that generates code to simplify client programming.</span></span> <span data-ttu-id="7cba9-173">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="7cba9-173">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="7cba9-174">Programowanie na poziomie kanału klienta</span><span class="sxs-lookup"><span data-stu-id="7cba9-174">Client Channel-Level Programming</span></span>](./extending/client-channel-level-programming.md)  
  
-   [<span data-ttu-id="7cba9-175">Porady: Dodawanie, aktualizowanie lub usuwanie odwołań usługi</span><span class="sxs-lookup"><span data-stu-id="7cba9-175">How to: Add, Update, or Remove a Service Reference</span></span>](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a><span data-ttu-id="7cba9-176">Sposób użycia serializacji</span><span class="sxs-lookup"><span data-stu-id="7cba9-176">Serialization Usage</span></span>  
 <span data-ttu-id="7cba9-177">Wywołaniem funkcji zdalnych .NET i usługi WCF umożliwia wysyłanie obiektów między klientem i serwerem serializacji, ale różnią się w tych ważnymi względami:</span><span class="sxs-lookup"><span data-stu-id="7cba9-177">Both .NET Remoting and WCF use serialization to send objects between client and server, but they differ in these important ways:</span></span>  
  
1.  <span data-ttu-id="7cba9-178">Konwencje i różnych serializatory one służy do wskazywania, co do serializacji.</span><span class="sxs-lookup"><span data-stu-id="7cba9-178">They use different serializers and conventions to indicate what to serialize.</span></span>  
  
2.  <span data-ttu-id="7cba9-179">Wywołaniem funkcji zdalnych .NET obsługuje serializacji "przez odwołanie", który umożliwia dostęp metody lub właściwości w jednej warstwy na wykonanie kodu na inne warstwy, która jest w granicach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7cba9-179">.NET Remoting supports "by reference" serialization that allows method or property access on one tier to execute code on the other tier, which is across security boundaries.</span></span> <span data-ttu-id="7cba9-180">Ta funkcja udostępnia luk w zabezpieczeniach i jest jednym z głównych powodów dlaczego punkty końcowe komunikacji zdalnej nigdy nie powinny zostać ujawnione klientom niezaufanych.</span><span class="sxs-lookup"><span data-stu-id="7cba9-180">This capability exposes security vulnerabilities and is one of the main reasons why Remoting endpoints should never be exposed to untrusted clients.</span></span>  
  
3.  <span data-ttu-id="7cba9-181">Serializacja używana przez wywołaniem funkcji zdalnych uniezależnienia (jawnie wykluczone, jak nie można serializować) i WCF serializacji jest zoptymalizowany pod kątem (wyraźnie oznaczyć elementów członkowskich, które można serializować).</span><span class="sxs-lookup"><span data-stu-id="7cba9-181">Serialization used by Remoting is opt-out (explicitly exclude what not to serialize) and WCF serialization is opt-in (explicitly mark which members to serialize).</span></span>  
  
#### <a name="serialization-in-net-remoting"></a><span data-ttu-id="7cba9-182">Serializacja w wywołaniem funkcji zdalnych .NET</span><span class="sxs-lookup"><span data-stu-id="7cba9-182">Serialization in .NET Remoting</span></span>  
 <span data-ttu-id="7cba9-183">Wywołaniem funkcji zdalnych .NET obsługuje dwie metody serializacji i deserializacji obiektów między klientem i serwerem:</span><span class="sxs-lookup"><span data-stu-id="7cba9-183">.NET Remoting supports two ways to serialize and deserialize objects between the client and server:</span></span>  
  
-   <span data-ttu-id="7cba9-184">*Według wartości* — wartości obiektu są serializowane w granicach warstwy i nowego wystąpienia tego obiektu jest tworzony w innej warstwie.</span><span class="sxs-lookup"><span data-stu-id="7cba9-184">*By value* – the values of the object are serialized across tier boundaries, and a new instance of that object is created on the other tier.</span></span> <span data-ttu-id="7cba9-185">Wszelkie wywołania metody lub właściwości tego nowego wystąpienia wykonanie tylko lokalnie i nie ma wpływu na oryginalny obiekt lub warstwy.</span><span class="sxs-lookup"><span data-stu-id="7cba9-185">Any calls to methods or properties of that new instance execute only locally and do not affect the original object or tier.</span></span>  
  
-   <span data-ttu-id="7cba9-186">*Przez odwołanie* — specjalnego "odwołanie do obiektu" jest serializowane jako granice warstwy.</span><span class="sxs-lookup"><span data-stu-id="7cba9-186">*By reference* – a special "object reference" is serialized across tier boundaries.</span></span> <span data-ttu-id="7cba9-187">Gdy jednej warstwy korzysta z metody lub właściwości tego obiektu, komunikuje się do oryginalnego obiektu, oryginalnym warstwy.</span><span class="sxs-lookup"><span data-stu-id="7cba9-187">When one tier interacts with methods or properties of that object, it communicates back to the original object on the original tier.</span></span> <span data-ttu-id="7cba9-188">Obiekty-reference może przepływać w dowolnym kierunku — od serwera do klienta lub od klienta do serwera.</span><span class="sxs-lookup"><span data-stu-id="7cba9-188">By-reference objects can flow in either direction – server to client, or client to server.</span></span>  
  
 <span data-ttu-id="7cba9-189">Typy i wartości w komunikacji zdalnej są oznaczone atrybutem [Serializable] lub zaimplementować ISerializable, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7cba9-189">By-value types in Remoting are marked with the [Serializable] attribute or implement ISerializable, like in the following example:</span></span>  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="7cba9-190">Typy niebędące odwołaniami pochodzi od klasy MarshalByRefObject, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7cba9-190">By-reference types derive from the MarshalByRefObject class, like in the following example:</span></span>  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="7cba9-191">Jest to bardzo ważne umożliwić poznanie skutków obiektów przez odwołanie w komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="7cba9-191">It is extremely important to understand the implications of Remoting’s by-reference objects.</span></span> <span data-ttu-id="7cba9-192">Jeśli każda warstwa (klienta lub serwera) wysyła obiekt przez odwołanie do innych warstwy, wszystkie wywołania metody wykonywania ponownie na warstwa będąca właścicielem obiektu.</span><span class="sxs-lookup"><span data-stu-id="7cba9-192">If either tier (client or server) sends a by-reference object to the other tier, all method calls execute back on the tier owning the object.</span></span> <span data-ttu-id="7cba9-193">Na przykład klient, wywoływanie metod na obiekcie przez odwołanie, zwrócony przez serwer będzie wykonanie kodu na serwerze.</span><span class="sxs-lookup"><span data-stu-id="7cba9-193">For example, a client calling methods on a by-reference object returned by the server will execute code on the server.</span></span> <span data-ttu-id="7cba9-194">Podobnie serwera, wywoływanie metod na obiekcie przez odwołanie, dostarczonych przez klienta będzie wykonywać kod ponownie na kliencie.</span><span class="sxs-lookup"><span data-stu-id="7cba9-194">Similarly, a server calling methods on a by-reference object provided by the client will execute code back on the client.</span></span> <span data-ttu-id="7cba9-195">Z tego powodu korzystanie z wywołaniem funkcji zdalnych .NET jest zalecane tylko w obrębie środowiska, w pełni zaufane.</span><span class="sxs-lookup"><span data-stu-id="7cba9-195">For this reason, the use of .NET Remoting is recommended only within fully-trusted environments.</span></span> <span data-ttu-id="7cba9-196">Udostępnianie publicznym punktem końcowym wywołaniem funkcji zdalnych .NET do niezaufani Klienci spowoduje, że serwer usług zdalnych narażony na ataki.</span><span class="sxs-lookup"><span data-stu-id="7cba9-196">Exposing a public .NET Remoting endpoint to untrusted clients will make a Remoting server vulnerable to attack.</span></span>  
  
#### <a name="serialization-in-wcf"></a><span data-ttu-id="7cba9-197">Serializacja w programie WCF</span><span class="sxs-lookup"><span data-stu-id="7cba9-197">Serialization in WCF</span></span>  
 <span data-ttu-id="7cba9-198">Usługi WCF obsługuje tylko przez wartość serializacji.</span><span class="sxs-lookup"><span data-stu-id="7cba9-198">WCF supports only by-value serialization.</span></span> <span data-ttu-id="7cba9-199">Najbardziej typowym sposobem definiowania typu do wymiany między klientem a serwerem jest podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7cba9-199">The most common way to define a type to exchange between client and server is like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="7cba9-200">Atrybut [DataContract] określa tego typu jako jeden, który może być serializacji i deserializacji między klientem i serwerem.</span><span class="sxs-lookup"><span data-stu-id="7cba9-200">The [DataContract] attribute identifies this type as one that can be serialized and deserialized between client and server.</span></span> <span data-ttu-id="7cba9-201">Atrybut [DataMember] identyfikuje poszczególne właściwości lub pól do serializacji.</span><span class="sxs-lookup"><span data-stu-id="7cba9-201">The [DataMember] attribute identifies the individual properties or fields to serialize.</span></span>  
  
 <span data-ttu-id="7cba9-202">Gdy WCF wysyła obiekt w warstwach, serializuje tylko wartości i tworzy nowe wystąpienie obiektu w innej warstwie.</span><span class="sxs-lookup"><span data-stu-id="7cba9-202">When WCF sends an object across tiers, it serializes only the values and creates a new instance of the object on the other tier.</span></span> <span data-ttu-id="7cba9-203">Wszystkie interakcje z wartościami obiektu występują tylko lokalnie — nie komunikują się z warstwą zrobić obiektów przez odwołanie wywołaniem funkcji zdalnych .NET.</span><span class="sxs-lookup"><span data-stu-id="7cba9-203">Any interactions with the values of the object occur only locally – they do not communicate with the other tier the way .NET Remoting by-reference objects do.</span></span> <span data-ttu-id="7cba9-204">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="7cba9-204">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="7cba9-205">Serializacja i deserializacja</span><span class="sxs-lookup"><span data-stu-id="7cba9-205">Serialization and Deserialization</span></span>](./feature-details/serialization-and-deserialization.md)  
  
-   [<span data-ttu-id="7cba9-206">Serializacja w Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="7cba9-206">Serialization in Windows Communication Foundation</span></span>](https://msdn.microsoft.com/magazine/cc163569.aspx)  
  
### <a name="exception-handling-capabilities"></a><span data-ttu-id="7cba9-207">Możliwości obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="7cba9-207">Exception Handling Capabilities</span></span>  
  
#### <a name="exceptions-in-net-remoting"></a><span data-ttu-id="7cba9-208">Wyjątki w wywołaniem funkcji zdalnych .NET</span><span class="sxs-lookup"><span data-stu-id="7cba9-208">Exceptions in .NET Remoting</span></span>  
 <span data-ttu-id="7cba9-209">Wyjątki zgłaszane przez serwer usług zdalnych są serializowane, wysłane do klienta, a następnie generowany lokalnie na komputerze klienckim, podobnie jak inne wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7cba9-209">Exceptions thrown by a Remoting server are serialized, sent to the client, and thrown locally on the client like any other exception.</span></span> <span data-ttu-id="7cba9-210">Niestandardowe wyjątki mogą być tworzone przez podrzędnych classing typ wyjątku i oznaczenie go przy użyciu [Serializable].</span><span class="sxs-lookup"><span data-stu-id="7cba9-210">Custom exceptions can be created by sub-classing the Exception type and marking it with [Serializable].</span></span>   <span data-ttu-id="7cba9-211">Większość wyjątków framework są już oznaczone w ten sposób, dzięki czemu większość zostanie wygenerowany przez serwer, serializowany i zgłoszony ponownie na kliencie.</span><span class="sxs-lookup"><span data-stu-id="7cba9-211">Most framework exceptions are already marked in this way, allowing most to be thrown by the server, serialized, and re-thrown on the client.</span></span> <span data-ttu-id="7cba9-212">Chociaż ten projekt jest wygodne podczas tworzenia aplikacji, informacji po stronie serwera może przypadkowo ujawnione klienta.</span><span class="sxs-lookup"><span data-stu-id="7cba9-212">Though this design is convenient during development, server-side information can inadvertently be disclosed to the client.</span></span> <span data-ttu-id="7cba9-213">Jest to jedna z wielu powodów, które wywołaniem funkcji zdalnych należy używać tylko w pełni zaufanym środowisku.</span><span class="sxs-lookup"><span data-stu-id="7cba9-213">This is one of many reasons Remoting should be used only in fully-trusted environments.</span></span>  
  
#### <a name="exceptions-and-faults-in-wcf"></a><span data-ttu-id="7cba9-214">Wyjątki i błędy w programie WCF</span><span class="sxs-lookup"><span data-stu-id="7cba9-214">Exceptions and Faults in WCF</span></span>  
 <span data-ttu-id="7cba9-215">Usługi WCF nie zezwala na typy dowolnego wyjątków, które mają być zwracane przez serwer do klienta, ponieważ mogłoby doprowadzić do ujawnienia informacji przypadkowego.</span><span class="sxs-lookup"><span data-stu-id="7cba9-215">WCF does not allow arbitrary exception types to be returned from the server to the client because it could lead to inadvertent information disclosure.</span></span> <span data-ttu-id="7cba9-216">Jeśli operacja usługi zgłasza nieoczekiwany wyjątek, powoduje ogólnego przeznaczenia FaultException — zostanie wygenerowany na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="7cba9-216">If a service operation throws an unexpected exception, it causes a general purpose FaultException to be thrown on the client.</span></span> <span data-ttu-id="7cba9-217">Dlaczego lub którym wystąpił problem, i dla niektórych aplikacji jest to wystarczające tego wyjątku nie zawiera żadnych informacji.</span><span class="sxs-lookup"><span data-stu-id="7cba9-217">This exception does not carry any information why or where the problem occurred, and for some applications this is sufficient.</span></span> <span data-ttu-id="7cba9-218">Aplikacje, które muszą komunikować się bogatsze informacje o błędzie do zrobienia klienta to definiując kontrakt błędu.</span><span class="sxs-lookup"><span data-stu-id="7cba9-218">Applications that need to communicate richer error information to the client do this by defining a fault contract.</span></span>  
  
 <span data-ttu-id="7cba9-219">Aby to zrobić, należy najpierw utworzyć typ [DataContract], żeby informacje o błędzie.</span><span class="sxs-lookup"><span data-stu-id="7cba9-219">To do this, first create a [DataContract] type to carry the fault information.</span></span>  
  
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
  
 <span data-ttu-id="7cba9-220">Określ kontrakt błędu dla każdej operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="7cba9-220">Specify the fault contract to use for each service operation.</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="7cba9-221">Serwer raportów warunki błędów, zgłaszając FaultException —.</span><span class="sxs-lookup"><span data-stu-id="7cba9-221">The server reports error conditions by throwing a FaultException.</span></span>  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 <span data-ttu-id="7cba9-222">I zawsze wtedy, gdy klient wysyła żądanie do serwera, może to przechwycić błędy jako wyjątki normalny.</span><span class="sxs-lookup"><span data-stu-id="7cba9-222">And whenever the client makes a request to the server, it can catch faults as normal exceptions.</span></span>  
  
```csharp
try  
{  
    Customer customer = server.GetCustomer(-1);  
}  
catch (FaultException<CustomerServiceFault> fault)  
{  
    Console.WriteLine(String.Format("Fault received: {0}",  
    fault.Detail.ErrorMessage));  
}  
```  
  
 <span data-ttu-id="7cba9-223">Aby uzyskać więcej informacji na temat umów błędów, zobacz <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="7cba9-223">For more information about fault contracts, see <xref:System.ServiceModel.FaultException>.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="7cba9-224">Zagadnienia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="7cba9-224">Security Considerations</span></span>  
  
#### <a name="security-in-net-remoting"></a><span data-ttu-id="7cba9-225">Zabezpieczenia w wywołaniem funkcji zdalnych .NET</span><span class="sxs-lookup"><span data-stu-id="7cba9-225">Security in .NET Remoting</span></span>  
 <span data-ttu-id="7cba9-226">Niektórych kanałów wywołaniem funkcji zdalnych .NET obsługuje funkcje zabezpieczeń, takie jak uwierzytelnianie i szyfrowanie w warstwie kanału (IPC i TCP).</span><span class="sxs-lookup"><span data-stu-id="7cba9-226">Some .NET Remoting channels support security features such as authentication and encryption at the channel layer (IPC and TCP).</span></span> <span data-ttu-id="7cba9-227">Kanał HTTP opiera się na Internet Information Services (IIS) dla uwierzytelniania i szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="7cba9-227">The HTTP channel relies on Internet Information Services (IIS) for both authentication and encryption.</span></span> <span data-ttu-id="7cba9-228">Pomimo tej obsługi możesz należy wziąć pod uwagę wywołaniem funkcji zdalnych .NET protokołu komunikacyjnego niebezpieczne i używać go tylko w obrębie środowiska, w pełni zaufane.</span><span class="sxs-lookup"><span data-stu-id="7cba9-228">Despite this support, you should consider .NET Remoting an unsecure communication protocol and use it only within fully-trusted environments.</span></span> <span data-ttu-id="7cba9-229">Nigdy nie ujawniają publicznym punktem końcowym komunikacji zdalnej do Internetu lub niezaufanego klientów.</span><span class="sxs-lookup"><span data-stu-id="7cba9-229">Never expose a public Remoting endpoint to the Internet or untrusted clients.</span></span>  
  
#### <a name="security-in-wcf"></a><span data-ttu-id="7cba9-230">Zabezpieczenia w programie WCF</span><span class="sxs-lookup"><span data-stu-id="7cba9-230">Security in WCF</span></span>  
 <span data-ttu-id="7cba9-231">Usługi WCF został opracowany z myślą o bezpieczeństwie, w części adresu rodzaje luk w zabezpieczeniach w wywołaniem funkcji zdalnych .NET.</span><span class="sxs-lookup"><span data-stu-id="7cba9-231">WCF was designed with security in mind, in part to address the kinds of vulnerabilities found in .NET Remoting.</span></span> <span data-ttu-id="7cba9-232">Usługi WCF oferuje zabezpieczenia na poziomie transportu i komunikat i oferuje wiele opcji uwierzytelniania, autoryzacji, szyfrowania i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="7cba9-232">WCF offers security at both the transport and message level, and offers many options for authentication, authorization, encryption, and so on.</span></span> <span data-ttu-id="7cba9-233">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="7cba9-233">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="7cba9-234">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="7cba9-234">Security</span></span>](./feature-details/security.md)  
  
-   [<span data-ttu-id="7cba9-235">Wskazówki dotyczące zabezpieczeń programu WCF</span><span class="sxs-lookup"><span data-stu-id="7cba9-235">WCF Security Guidance</span></span>](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a><span data-ttu-id="7cba9-236">Migrowanie do programu WCF</span><span class="sxs-lookup"><span data-stu-id="7cba9-236">Migrating to WCF</span></span>  
  
### <a name="why-migrate-from-remoting-to-wcf"></a><span data-ttu-id="7cba9-237">Dlaczego warto przeprowadzić migrację z Remoting do programu WCF?</span><span class="sxs-lookup"><span data-stu-id="7cba9-237">Why Migrate from Remoting to WCF?</span></span>  
  
-   <span data-ttu-id="7cba9-238">**Wywołaniem funkcji zdalnych .NET jest starszy produkt.**</span><span class="sxs-lookup"><span data-stu-id="7cba9-238">**.NET Remoting is a legacy product.**</span></span> <span data-ttu-id="7cba9-239">Zgodnie z opisem w [wywołaniem funkcji zdalnych .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), są traktowane jako starszy produkt i nie jest zalecane w przypadku nowych wdrożeń.</span><span class="sxs-lookup"><span data-stu-id="7cba9-239">As described in [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), it is considered a legacy product and is not recommended for new development.</span></span> <span data-ttu-id="7cba9-240">Usługi WCF lub Web API platformy ASP.NET są zalecane w przypadku nowych i istniejących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7cba9-240">WCF or ASP.NET Web API are recommended for new and existing applications.</span></span>  
  
-   <span data-ttu-id="7cba9-241">**Usługi WCF używa standardów dla wielu platform.**</span><span class="sxs-lookup"><span data-stu-id="7cba9-241">**WCF uses cross-platform standards.**</span></span> <span data-ttu-id="7cba9-242">Program WCF zaprojektowano pod kątem współdziałania dla wielu platform, należy pamiętać i obsługuje wiele standardów branżowych (protokołu SOAP, WS-Security WS-Trust, itp.).</span><span class="sxs-lookup"><span data-stu-id="7cba9-242">WCF was designed with cross-platform interoperability in mind and supports many industry standards (SOAP, WS-Security, WS-Trust, etc.).</span></span> <span data-ttu-id="7cba9-243">Usługa WCF może współpracować z klientami, działających w systemach operacyjnych innych niż Windows.</span><span class="sxs-lookup"><span data-stu-id="7cba9-243">A WCF service can interoperate with clients running on operating systems other than Windows.</span></span> <span data-ttu-id="7cba9-244">Komunikacja zdalna została zaprojektowana głównie dla środowisk, w którym serwer i klient aplikacje są uruchamiane przy użyciu programu .NET framework w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="7cba9-244">Remoting was designed primarily for environments where both the server and client applications run using the .NET framework on a Windows operating system.</span></span>  
  
-   <span data-ttu-id="7cba9-245">**Usługi WCF ma wbudowane zabezpieczenia.**</span><span class="sxs-lookup"><span data-stu-id="7cba9-245">**WCF has built-in security.**</span></span> <span data-ttu-id="7cba9-246">Usługi WCF została zaprojektowana z myślą o bezpieczeństwie i oferuje wiele opcji uwierzytelniania, zabezpieczenia na poziomie transportu, zabezpieczenia na poziomie komunikatu itp. Komunikacja zdalna zaprojektowano tak, aby ułatwić aplikacji pod kątem współdziałania, ale nie był projektowany do zabezpieczenia w środowiskach innych niż zaufane.</span><span class="sxs-lookup"><span data-stu-id="7cba9-246">WCF was designed with security in mind and offers many options for authentication, transport level security, message level security, etc. Remoting was designed to make it easy for applications to interoperate but was not designed to be secure in non-trusted environments.</span></span> <span data-ttu-id="7cba9-247">Usługi WCF był projektowany do pracy w środowiskach zaufanej i niezaufanej.</span><span class="sxs-lookup"><span data-stu-id="7cba9-247">WCF was designed to work in both trusted and non-trusted environments.</span></span>  
  
### <a name="migration-recommendations"></a><span data-ttu-id="7cba9-248">Zalecenia dotyczące migracji</span><span class="sxs-lookup"><span data-stu-id="7cba9-248">Migration Recommendations</span></span>  
 <span data-ttu-id="7cba9-249">Poniżej przedstawiono zalecane kroki, aby migrować z programu .NET Remoting do programu WCF:</span><span class="sxs-lookup"><span data-stu-id="7cba9-249">The following are the recommended steps to migrate from .NET Remoting to WCF:</span></span>  
  
-   <span data-ttu-id="7cba9-250">**Tworzenie kontraktu usługi.**</span><span class="sxs-lookup"><span data-stu-id="7cba9-250">**Create the service contract.**</span></span> <span data-ttu-id="7cba9-251">Definiowanie typów interfejsu użytkownika usługi i oznacz je za pomocą atrybutu [ServiceContract]. Oznacz wszystkie metody, których klienci będą mogły wywołać za pomocą elementu [OperationContract].</span><span class="sxs-lookup"><span data-stu-id="7cba9-251">Define your service interface types, and mark them with the [ServiceContract] attribute.Mark all the methods the clients will be allowed to call with [OperationContract].</span></span>  
  
-   <span data-ttu-id="7cba9-252">**Tworzenie kontraktu danych.**</span><span class="sxs-lookup"><span data-stu-id="7cba9-252">**Create the data contract.**</span></span> <span data-ttu-id="7cba9-253">Definiowanie typów danych, które będą wymieniane między serwerem a klientem i oznacz je za pomocą atrybutu [DataContract].</span><span class="sxs-lookup"><span data-stu-id="7cba9-253">Define the data types that will be exchanged between server and client, and mark them with the [DataContract] attribute.</span></span> <span data-ttu-id="7cba9-254">Oznacz wszystkie pola i właściwości klienta zostaną dozwolone za pomocą [DataMember].</span><span class="sxs-lookup"><span data-stu-id="7cba9-254">Mark all the fields and properties the client will be allowed to use with [DataMember].</span></span>  
  
-   <span data-ttu-id="7cba9-255">**Utworzyć kontrakt błędu (opcjonalnie).**</span><span class="sxs-lookup"><span data-stu-id="7cba9-255">**Create the fault contract (optional).**</span></span> <span data-ttu-id="7cba9-256">Tworzenie typów, które będą wymieniane między serwerem a klientem, gdy wystąpią błędy.</span><span class="sxs-lookup"><span data-stu-id="7cba9-256">Create the types that will be exchanged between server and client when errors are encountered.</span></span> <span data-ttu-id="7cba9-257">Należy oznaczyć te typy z [DataContract] i [DataMember] były możliwe do serializacji.</span><span class="sxs-lookup"><span data-stu-id="7cba9-257">Mark these types with [DataContract] and [DataMember] to make them serializable.</span></span> <span data-ttu-id="7cba9-258">Dla wszystkich operacji usługi, które zostały oznaczone za pomocą elementu [OperationContract] również oznacz je za pomocą [FaultContract] do sygnalizowania błędów, które zwracają może.</span><span class="sxs-lookup"><span data-stu-id="7cba9-258">For all service operations you marked with [OperationContract], also mark them with [FaultContract] to indicate which errors they may return.</span></span>  
  
-   <span data-ttu-id="7cba9-259">**Skonfiguruj i obsługi usługi.**</span><span class="sxs-lookup"><span data-stu-id="7cba9-259">**Configure and host the service.**</span></span> <span data-ttu-id="7cba9-260">Po utworzeniu kontraktu usługi, następnym krokiem jest skonfigurować powiązanie, aby udostępnić usługę w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="7cba9-260">Once the service contract has been created, the next step is to configure a binding to expose the service at an endpoint.</span></span> <span data-ttu-id="7cba9-261">Aby uzyskać więcej informacji, zobacz [punkty końcowe: adresy, powiązania i kontrakty](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="7cba9-261">For more information, see [Endpoints: Addresses, Bindings, and Contracts](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span></span>  
  
 <span data-ttu-id="7cba9-262">Po migracji aplikacji usług zdalnych do programu WCF jest nadal ważne usunąć zależności między wywołaniem funkcji zdalnych .NET.</span><span class="sxs-lookup"><span data-stu-id="7cba9-262">Once a Remoting application has been migrated to WCF, it is still important to remove dependencies on .NET Remoting.</span></span> <span data-ttu-id="7cba9-263">Daje to gwarancję, że wszystkie luki w zabezpieczeniach z wywołaniem funkcji zdalnych są usuwane z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7cba9-263">This ensures that any Remoting vulnerabilities are removed from the application.</span></span> <span data-ttu-id="7cba9-264">Kroki te obejmują następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="7cba9-264">These steps include the following:</span></span>  
  
-   <span data-ttu-id="7cba9-265">**Przestać korzystać ze MarshalByRefObject.**</span><span class="sxs-lookup"><span data-stu-id="7cba9-265">**Discontinue use of MarshalByRefObject.**</span></span> <span data-ttu-id="7cba9-266">Typ elementu MarshalByRefObject istnieje tylko dla niego komunikację zdalną i nie jest używany przez architekturę WCF.</span><span class="sxs-lookup"><span data-stu-id="7cba9-266">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="7cba9-267">Wszystkie typy aplikacji, które podrzędnych klasy MarshalByRefObject powinny być usunięte lub zmienione.</span><span class="sxs-lookup"><span data-stu-id="7cba9-267">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span> <span data-ttu-id="7cba9-268">Typ elementu MarshalByRefObject istnieje tylko dla niego komunikację zdalną i nie jest używany przez architekturę WCF.</span><span class="sxs-lookup"><span data-stu-id="7cba9-268">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="7cba9-269">Wszystkie typy aplikacji, które podrzędnych klasy MarshalByRefObject powinny być usunięte lub zmienione.</span><span class="sxs-lookup"><span data-stu-id="7cba9-269">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span>  
  
-   <span data-ttu-id="7cba9-270">**Zaprzestanie użytkowania [Serializable] i interfejs ISerializable.**</span><span class="sxs-lookup"><span data-stu-id="7cba9-270">**Discontinue use of [Serializable] and ISerializable.**</span></span> <span data-ttu-id="7cba9-271">Atrybut [Serializable] i interfejs ISerializable zostały pierwotnie zaprojektowane do serializacji typów w środowiskach zaufanych i są one używane przez komunikację zdalną.</span><span class="sxs-lookup"><span data-stu-id="7cba9-271">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="7cba9-272">Serializacja WCF opiera się na typy, które są oznaczone [DataContract] i [DataMember].</span><span class="sxs-lookup"><span data-stu-id="7cba9-272">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="7cba9-273">Powinien być modyfikowany typów danych używanych przez aplikację, aby użyć [DataContract] i nie należy używać interfejsu ISerializable lub [Serializable].</span><span class="sxs-lookup"><span data-stu-id="7cba9-273">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span> <span data-ttu-id="7cba9-274">Atrybut [Serializable] i interfejs ISerializable zostały pierwotnie zaprojektowane do serializacji typów w środowiskach zaufanych i są one używane przez komunikację zdalną.</span><span class="sxs-lookup"><span data-stu-id="7cba9-274">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="7cba9-275">Serializacja WCF opiera się na typy, które są oznaczone [DataContract] i [DataMember].</span><span class="sxs-lookup"><span data-stu-id="7cba9-275">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="7cba9-276">Powinien być modyfikowany typów danych używanych przez aplikację, aby użyć [DataContract] i nie należy używać interfejsu ISerializable lub [Serializable].</span><span class="sxs-lookup"><span data-stu-id="7cba9-276">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span>  
  
### <a name="migration-scenarios"></a><span data-ttu-id="7cba9-277">Scenariusze migracji</span><span class="sxs-lookup"><span data-stu-id="7cba9-277">Migration Scenarios</span></span>  
 <span data-ttu-id="7cba9-278">Teraz zobaczmy, jak wykonywać następujące typowe scenariusze komunikacji zdalnej programu WCF:</span><span class="sxs-lookup"><span data-stu-id="7cba9-278">Now let’s see how to accomplish the following common Remoting scenarios in WCF:</span></span>  
  
1.  <span data-ttu-id="7cba9-279">Serwer zwraca obiekt przez wartość do klienta</span><span class="sxs-lookup"><span data-stu-id="7cba9-279">Server returns an object by-value to the client</span></span>  
  
2.  <span data-ttu-id="7cba9-280">Serwer zwraca obiekt przez odwołanie do klienta</span><span class="sxs-lookup"><span data-stu-id="7cba9-280">Server returns an object by-reference to the client</span></span>  
  
3.  <span data-ttu-id="7cba9-281">Klient wysyła obiekt przez wartość do serwera</span><span class="sxs-lookup"><span data-stu-id="7cba9-281">Client sends an object by-value to the server</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7cba9-282">Wysyłanie przez — odwołanie do obiektu z klienta do serwera w programie WCF jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="7cba9-282">Sending an object by-reference from the client to the server is not allowed in WCF.</span></span>  
  
 <span data-ttu-id="7cba9-283">Podczas odczytywania za pośrednictwem tych scenariuszy, zakłada się, że nasze interfejsy punktu odniesienia dla wywołaniem funkcji zdalnych .NET wyglądać jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7cba9-283">When reading through these scenarios, assume our baseline interfaces for .NET Remoting look like the following example.</span></span> <span data-ttu-id="7cba9-284">Implementacja wywołaniem funkcji zdalnych .NET nie jest ważna w tym miejscu, ponieważ chcemy zilustrować, lecz jak używać usługi WCF do zaimplementowania równoważne funkcje.</span><span class="sxs-lookup"><span data-stu-id="7cba9-284">The .NET Remoting implementation is not important here because we want to illustrate only how to use WCF to implement equivalent functionality.</span></span>  
  
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
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a><span data-ttu-id="7cba9-285">Scenariusz 1: Usługa zwraca obiekt przez wartość</span><span class="sxs-lookup"><span data-stu-id="7cba9-285">Scenario 1: Service Returns an Object by Value</span></span>  
 <span data-ttu-id="7cba9-286">Ten scenariusz pokazuje serwera zwrócenie obiektu, do klienta przez wartość.</span><span class="sxs-lookup"><span data-stu-id="7cba9-286">This scenario demonstrates a server returning an object to the client by value.</span></span> <span data-ttu-id="7cba9-287">Usługi WCF zawsze zwraca obiekty z serwera według wartości, więc w poniższych krokach opisano tylko sposób budowania normalne usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="7cba9-287">WCF always returns objects from the server by value, so the following steps simply describe how to build a normal WCF service.</span></span>  
  
1.  <span data-ttu-id="7cba9-288">Rozpocznij od zdefiniowania interfejsu publicznego dla usługi WCF i oznacz ją atrybutem [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="7cba9-288">Start by defining a public interface for the WCF service and mark it with the [ServiceContract] attribute.</span></span> <span data-ttu-id="7cba9-289">[Elementu OperationContract] są używane do identyfikowania metod po stronie serwera, który wywoła naszych klientów.</span><span class="sxs-lookup"><span data-stu-id="7cba9-289">We use [OperationContract] to identify the server-side methods our client will call.</span></span>  
  
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
  
2.  <span data-ttu-id="7cba9-290">Następnym krokiem jest tworzenie kontraktu danych dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="7cba9-290">The next step is to create the data contract for this service.</span></span> <span data-ttu-id="7cba9-291">Możemy to zrobić przez utworzenie klas (nie interfejsy) oznaczona przez atrybut [DataContract].</span><span class="sxs-lookup"><span data-stu-id="7cba9-291">We do this by creating classes (not interfaces) marked with the [DataContract] attribute.</span></span> <span data-ttu-id="7cba9-292">Indywidualne właściwości lub pola, które chcemy, aby widoczne dla klienta i serwera są oznaczone [DataMember].</span><span class="sxs-lookup"><span data-stu-id="7cba9-292">The individual properties or fields we want visible to both client and server are marked with [DataMember].</span></span> <span data-ttu-id="7cba9-293">Jeśli chcemy, aby typy pochodne, które mają być dozwolone, będziemy Użyj atrybutu [element KnownType] umożliwiający ich zidentyfikowanie.</span><span class="sxs-lookup"><span data-stu-id="7cba9-293">If we want derived types to be allowed, we must use the [KnownType] attribute to identify them.</span></span> <span data-ttu-id="7cba9-294">Jedyne typy WCF pozwoli serializowany lub deserializowany dla tej usługi są w interfejsie usługi i te "znane typy".</span><span class="sxs-lookup"><span data-stu-id="7cba9-294">The only types WCF will allow to be serialized or deserialized for this service are those in the service interface and these "known types".</span></span> <span data-ttu-id="7cba9-295">Podjęto próbę wymiany innego typu, nie ma na tej liście będą odrzucane.</span><span class="sxs-lookup"><span data-stu-id="7cba9-295">Attempting to exchange any other type not in this list will be rejected.</span></span>  
  
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
  
3.  <span data-ttu-id="7cba9-296">Następnie firma Microsoft oferuje implementację interfejsu usługi.</span><span class="sxs-lookup"><span data-stu-id="7cba9-296">Next, we provide the implementation for the service interface.</span></span>  
  
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
  
4.  <span data-ttu-id="7cba9-297">Aby uruchomić usługę WCF, należy zadeklarować punktu końcowego uwidocznionego interfejsu usług pod określonym adresem URL używa określonego powiązania WCF.</span><span class="sxs-lookup"><span data-stu-id="7cba9-297">To run the WCF service, we need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="7cba9-298">Zazwyczaj jest to wykonywane, dodając poniższe sekcje w pliku web.config projektu serwera.</span><span class="sxs-lookup"><span data-stu-id="7cba9-298">This is typically done by adding the following sections to the server project’s web.config file.</span></span>  
  
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
  
5.  <span data-ttu-id="7cba9-299">Następnie można uruchomić usługi WCF z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="7cba9-299">The WCF service can then be started with the following code:</span></span>  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     <span data-ttu-id="7cba9-300">Po uruchomieniu tego elementu ServiceHost, używa pliku web.config można ustanowić prawidłowego kontraktu, powiązania i punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="7cba9-300">When this ServiceHost is started, it uses the web.config file to establish the proper contract, binding and endpoint.</span></span> <span data-ttu-id="7cba9-301">Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [Konfigurowanie usług za pomocą plików konfiguracji](./configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="7cba9-301">For more information about configuration files, see [Configuring Services Using Configuration Files](./configuring-services-using-configuration-files.md).</span></span> <span data-ttu-id="7cba9-302">Uruchamianie serwera ten styl jest określany jako hostingu samodzielnego.</span><span class="sxs-lookup"><span data-stu-id="7cba9-302">This style of starting the server is known as self-hosting.</span></span> <span data-ttu-id="7cba9-303">Aby dowiedzieć się więcej na temat innych opcji do hostowania usług WCF, zobacz [usług obsługującego](./hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="7cba9-303">To learn more about other choices for hosting WCF services, see [Hosting Services](./hosting-services.md).</span></span>  
  
6.  <span data-ttu-id="7cba9-304">Projekt klienta w pliku app.config, należy zadeklarować pasujące informacje o powiązaniu dla punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="7cba9-304">The client project’s app.config must declare matching binding information for the service’s endpoint.</span></span> <span data-ttu-id="7cba9-305">Najprostszym sposobem, aby to zrobić w programie Visual Studio jest użycie **Dodaj odwołanie do usługi**, który automatycznie aktualizuje plik app.config.</span><span class="sxs-lookup"><span data-stu-id="7cba9-305">The easiest way to do this in Visual Studio is to use **Add Service Reference**, which will automatically update the app.config file.</span></span> <span data-ttu-id="7cba9-306">Te same zmiany można również dodać ręcznie.</span><span class="sxs-lookup"><span data-stu-id="7cba9-306">Alternatively, these same changes can be added manually.</span></span>  
  
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
  
     <span data-ttu-id="7cba9-307">Aby uzyskać więcej informacji o korzystaniu z **Dodaj odwołanie do usługi**, zobacz [porady: Dodawanie, aktualizowanie lub usuwanie odwołań usługi](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span><span class="sxs-lookup"><span data-stu-id="7cba9-307">For more information about using **Add Service Reference**, see [How to: Add, Update, or Remove a Service Reference](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span></span>  
  
7.  <span data-ttu-id="7cba9-308">Teraz możemy wywołać usługi WCF z klienta.</span><span class="sxs-lookup"><span data-stu-id="7cba9-308">Now we can call the WCF service from the client.</span></span> <span data-ttu-id="7cba9-309">Możemy to zrobić, tworząc fabryki kanałów dla tej usługi, o kanału i bezpośrednio wywołać metodę, którą chcemy, aby w tym kanale.</span><span class="sxs-lookup"><span data-stu-id="7cba9-309">We do this by creating a channel factory for that service, asking it for a channel, and directly calling the method we want on that channel.</span></span> <span data-ttu-id="7cba9-310">Możemy to zrobić, ponieważ implementuje interfejs usługi w kanale i obsługuje podstawowej logiki żądanie/nietypizowana odpowiedź dla nas.</span><span class="sxs-lookup"><span data-stu-id="7cba9-310">We can do this because the channel implements the service’s interface and handles the underlying request/reply logic for us.</span></span> <span data-ttu-id="7cba9-311">Wartość zwrócona przez wywołanie tej metody jest zdeserializowany kopię odpowiedź serwera.</span><span class="sxs-lookup"><span data-stu-id="7cba9-311">The return value from that method call is the deserialized copy of the server’s response.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine(String.Format("  Customer {0} {1} received.",  
           customer.FirstName, customer.LastName));  
   ```  
  
 <span data-ttu-id="7cba9-312">Obiekty zwrócone przez architekturę WCF z serwera do klienta są zawsze przez wartość.</span><span class="sxs-lookup"><span data-stu-id="7cba9-312">Objects returned by WCF from the server to the client are always by value.</span></span> <span data-ttu-id="7cba9-313">Obiekty są zdeserializowany kopie danych wysłanych przez serwer.</span><span class="sxs-lookup"><span data-stu-id="7cba9-313">The objects are deserialized copies of the data sent by the server.</span></span> <span data-ttu-id="7cba9-314">Klient może wywoływać metody te kopiami lokalnymi bez zagrożenia wywoływania kod serwera za pomocą wywołania zwrotne.</span><span class="sxs-lookup"><span data-stu-id="7cba9-314">The client can call methods on these local copies without any danger of invoking server code through callbacks.</span></span>  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a><span data-ttu-id="7cba9-315">Scenariusz 2: Serwer zwraca obiekt przez odwołanie</span><span class="sxs-lookup"><span data-stu-id="7cba9-315">Scenario 2: Server Returns an Object By Reference</span></span>  
 <span data-ttu-id="7cba9-316">Ten scenariusz pokazuje serwera, podając obiekt do klienta przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="7cba9-316">This scenario demonstrates the server providing an object to the client by reference.</span></span> <span data-ttu-id="7cba9-317">W wywołaniem funkcji zdalnych .NET, to odbywa się automatycznie dla wszystkich typów pochodnych MarshalByRefObject, który jest serializowany przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="7cba9-317">In .NET Remoting, this is handled automatically for any type derived from MarshalByRefObject, which is serialized by-reference.</span></span> <span data-ttu-id="7cba9-318">Przykładem tego scenariusza jest zezwolenie klientom wiele niezależnych sesji obiektów po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="7cba9-318">An example of this scenario is allowing multiple clients to have independent sessionful server-side objects.</span></span> <span data-ttu-id="7cba9-319">Jak wcześniej wspomniano, obiekty zwrócone przez usługę WCF zawsze według wartości, więc ma bezpośredniego odpowiednika obiektu przez odwołanie, ale można osiągnąć podobny do przy użyciu semantyki przez odwołanie <xref:System.ServiceModel.EndpointAddress10> obiektu.</span><span class="sxs-lookup"><span data-stu-id="7cba9-319">As previously mentioned, objects returned by a WCF service are always by value, so there is no direct equivalent of a by-reference object, but it is possible to achieve something similar to by-reference semantics using an <xref:System.ServiceModel.EndpointAddress10> object.</span></span> <span data-ttu-id="7cba9-320">Jest to obiekt możliwy do serializacji według wartości, który może służyć przez klienta do uzyskiwania obiektu sesji przez odwołanie, na serwerze.</span><span class="sxs-lookup"><span data-stu-id="7cba9-320">This is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span> <span data-ttu-id="7cba9-321">Dzięki temu scenariusz posiadanie wielu klientów obiektami niezależnie od sesji po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="7cba9-321">This enables the scenario of having multiple clients with independent sessionful server-side objects.</span></span>  
  
1.  <span data-ttu-id="7cba9-322">Najpierw musimy definiowanie kontraktu usługi WCF, która odnosi się do samego obiektu sesji.</span><span class="sxs-lookup"><span data-stu-id="7cba9-322">First, we need to define a WCF service contract that corresponds to the sessionful object itself.</span></span>  
  
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
    >  <span data-ttu-id="7cba9-323">Zwróć uwagę, że obiekt sesji jest oznaczona atrybutem [ServiceContract], dzięki czemu normalne interfejsu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="7cba9-323">Notice that the sessionful object is marked with [ServiceContract], making it a normal WCF service interface.</span></span> <span data-ttu-id="7cba9-324">Ustawienie SessionMode właściwość wskazuje, że będzie on sesji usługi.</span><span class="sxs-lookup"><span data-stu-id="7cba9-324">Setting the SessionMode property indicates it will be a sessionful service.</span></span> <span data-ttu-id="7cba9-325">W programie WCF sesja jest sposób korelacji wielu komunikatów przesyłanych między dwoma punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="7cba9-325">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span> <span data-ttu-id="7cba9-326">Oznacza to, że gdy klient uzyskuje połączenie z tą usługą, sesji zostanie nawiązane między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="7cba9-326">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span> <span data-ttu-id="7cba9-327">Klient użyje jednego unikatowego wystąpienia obiektu po stronie serwera dla wszystkich jego interakcji w ramach tej jednej sesji.</span><span class="sxs-lookup"><span data-stu-id="7cba9-327">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span>  
  
2.  <span data-ttu-id="7cba9-328">Następnie należy udostępnić implementację tego interfejsu usługi.</span><span class="sxs-lookup"><span data-stu-id="7cba9-328">Next, we need to provide the implementation of this service interface.</span></span> <span data-ttu-id="7cba9-329">Oznaczającą, za pomocą [ServiceBehavior] i ustawiając właściwość InstanceContextMode, o WCF że chcemy użyć unikatowego wystąpienia tego typu dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="7cba9-329">By denoting it with [ServiceBehavior] and setting the InstanceContextMode, we tell WCF we want to use a unique instance of this type for an each session.</span></span>  
  
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
  
3.  <span data-ttu-id="7cba9-330">Teraz musimy sposobem uzyskania wystąpienie tego obiektu sesji.</span><span class="sxs-lookup"><span data-stu-id="7cba9-330">Now we need a way to obtain an instance of this sessionful object.</span></span> <span data-ttu-id="7cba9-331">Możemy to zrobić, tworząc inny interfejs usługi WCF, która zwraca obiekt EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="7cba9-331">We do this by creating another WCF service interface that returns an EndpointAddress10 object.</span></span> <span data-ttu-id="7cba9-332">Jest to format możliwy do serializacji punktu końcowego, który klient może używać do utworzenia obiektu sesji.</span><span class="sxs-lookup"><span data-stu-id="7cba9-332">This is a serializable form of an endpoint that the client can use to create the sessionful object.</span></span>  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     <span data-ttu-id="7cba9-333">I firma Microsoft zaimplementowania tej usługi WCF:</span><span class="sxs-lookup"><span data-stu-id="7cba9-333">And we implement this WCF service:</span></span>  
  
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
  
     <span data-ttu-id="7cba9-334">Ta implementacja obsługuje pojedyncze fabryki kanałów, aby utworzyć obiekty sesji.</span><span class="sxs-lookup"><span data-stu-id="7cba9-334">This implementation maintains a singleton channel factory to create sessionful objects.</span></span> <span data-ttu-id="7cba9-335">Po wywołaniu GetInstanceAddress() tworzy kanał i tworzy obiekt EndpointAddress10 skutecznie wskazujący zdalny adres skojarzony z tym kanałem.</span><span class="sxs-lookup"><span data-stu-id="7cba9-335">When GetInstanceAddress() is called, it creates a channel and creates an EndpointAddress10 object that effectively points to the remote address associated with this channel.</span></span> <span data-ttu-id="7cba9-336">EndpointAddress10 jest po prostu typu danych, które mogą być zwrócone do klienta przez wartość.</span><span class="sxs-lookup"><span data-stu-id="7cba9-336">EndpointAddress10 is simply a data type that can be returned to the client by-value.</span></span>  
  
4.  <span data-ttu-id="7cba9-337">Należy zmodyfikować plik konfiguracji serwera, wykonując następujące dwie czynności, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7cba9-337">We need to modify the server’s configuration file by doing the following two things as shown in the example below:</span></span>  
  
    1.  <span data-ttu-id="7cba9-338">Zadeklaruj \<klienta > sekcji, która opisuje punktu końcowego dla obiektu sesji.</span><span class="sxs-lookup"><span data-stu-id="7cba9-338">Declare a \<client> section that describes the endpoint for the sessionful object.</span></span> <span data-ttu-id="7cba9-339">Jest to konieczne, ponieważ serwer działa również jako klient w tej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="7cba9-339">This is necessary because the server also acts as a client in this situation.</span></span>  
  
    2.  <span data-ttu-id="7cba9-340">Zadeklaruj punktów końcowych dla obiektu ustawień fabrycznych i sessionful.</span><span class="sxs-lookup"><span data-stu-id="7cba9-340">Declare endpoints for the factory and sessionful object.</span></span> <span data-ttu-id="7cba9-341">Jest to konieczne umożliwić klientowi komunikowanie się z punktami końcowymi usługi do uzyskania EndpointAddress10 i tworzenia kanału sesji.</span><span class="sxs-lookup"><span data-stu-id="7cba9-341">This is necessary to allow the client to communicate with the service endpoints to acquire the EndpointAddress10 and to create the sessionful channel.</span></span>  
  
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
  
     <span data-ttu-id="7cba9-342">A następnie Zaczniemy tych usług:</span><span class="sxs-lookup"><span data-stu-id="7cba9-342">And then we can start these services:</span></span>  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5.  <span data-ttu-id="7cba9-343">Możemy skonfigurować klienta przez zadeklarowanie te tymi samymi punktami końcowymi w pliku app.config jego projektu.</span><span class="sxs-lookup"><span data-stu-id="7cba9-343">We configure the client by declaring these same endpoints in its project’s app.config file.</span></span>  
  
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
  
6.  <span data-ttu-id="7cba9-344">Aby można było utworzyć i używać tego obiektu sesji, klient musi wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="7cba9-344">In order to create and use this sessionful object, the client must do the following steps:</span></span>  
  
    1.  <span data-ttu-id="7cba9-345">Utwórz kanał w usłudze ISessionBoundFactory.</span><span class="sxs-lookup"><span data-stu-id="7cba9-345">Create a channel to the ISessionBoundFactory service.</span></span>  
  
    2.  <span data-ttu-id="7cba9-346">Do wywołania tej usługi w celu uzyskania EndpointAddress10 przy użyciu tego kanału.</span><span class="sxs-lookup"><span data-stu-id="7cba9-346">Use that channel to invoke that service to obtain an EndpointAddress10.</span></span>  
  
    3.  <span data-ttu-id="7cba9-347">Próba utworzenia kanału do uzyskiwania obiektu sesji, należy użyć EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="7cba9-347">Use the EndpointAddress10 to create a channel to obtain a sessionful object.</span></span>  
  
    4.  <span data-ttu-id="7cba9-348">Wchodzić w interakcje z obiektem sesji wykazanie, że będzie tego samego wystąpienia w wielu wywołań.</span><span class="sxs-lookup"><span data-stu-id="7cba9-348">Interact with the sessionful object to demonstrate it remains the same instance across multiple calls.</span></span>  
  
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
  
 <span data-ttu-id="7cba9-349">Usługi WCF zawsze zwraca obiekty według wartości, ale istnieje możliwość obsługi wielokrotność semantyki przez odwołanie za pomocą EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="7cba9-349">WCF always returns objects by value, but it is possible to support the equivalent of by-reference semantics through the use of EndpointAddress10.</span></span> <span data-ttu-id="7cba9-350">Umożliwia klientowi żądanie sesji wystąpienie usługi WCF, po upływie którego go mogą wchodzić w interakcje z nią podobnie jak inne usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="7cba9-350">This permits the client to request a sessionful WCF service instance, after which it can interact with it like any other WCF service.</span></span>  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a><span data-ttu-id="7cba9-351">Scenariusz 3: Klient wysyła serwer wystąpienie przez wartość</span><span class="sxs-lookup"><span data-stu-id="7cba9-351">Scenario 3: Client Sends Server a By-Value Instance</span></span>  
 <span data-ttu-id="7cba9-352">Ten scenariusz pokazuje klienta wysyłania wystąpienia obiektu niepodstawowe do serwera przez wartość.</span><span class="sxs-lookup"><span data-stu-id="7cba9-352">This scenario demonstrates the client sending a non-primitive object instance to the server by value.</span></span> <span data-ttu-id="7cba9-353">Ponieważ WCF wysyła tylko obiektów według wartości, w tym scenariuszu pokazano normalnego użycia usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="7cba9-353">Because WCF only sends objects by value, this scenario demonstrates normal WCF usage.</span></span>  
  
1.  <span data-ttu-id="7cba9-354">Użyj tej samej usługi WCF z scenariusz 1.</span><span class="sxs-lookup"><span data-stu-id="7cba9-354">Use the same WCF Service from Scenario 1.</span></span>  
  
2.  <span data-ttu-id="7cba9-355">Aby utworzyć nowy obiekt przez wartość (klienta), utworzenia kanału do komunikacji z usługą ICustomerService i wysyłać obiekt, korzystając z klienta.</span><span class="sxs-lookup"><span data-stu-id="7cba9-355">Use the client to create a new by-value object (Customer), create a channel to communicate with the ICustomerService service, and send the object to it.</span></span>  
  
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
   Console.WriteLine(String.Format("  Server returned {0}.", success));  
   ```  
  
     <span data-ttu-id="7cba9-356">Obiekt klienta będą serializowane i wysyłane do serwera, gdzie jest ona przeprowadzona deserializacja nową kopię tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="7cba9-356">The customer object will be serialized, and sent to the server, where it is deserialized into a new copy of that object.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7cba9-357">Ten kod ilustruje także wysyłanie typu pochodnego (PremiumCustomer).</span><span class="sxs-lookup"><span data-stu-id="7cba9-357">This code also illustrates sending a derived type (PremiumCustomer).</span></span> <span data-ttu-id="7cba9-358">Interfejs usługi oczekuje obiektu klienta, ale atrybut [element KnownType] w klasie klienta wskazał PremiumCustomer również był dozwolony.</span><span class="sxs-lookup"><span data-stu-id="7cba9-358">The service interface expects a Customer object, but the [KnownType] attribute on the Customer class indicated PremiumCustomer was also allowed.</span></span> <span data-ttu-id="7cba9-359">Usługi WCF zakończy się niepowodzeniem próby serializacji lub deserializacji dowolny inny typ za pomocą tego interfejsu usługi.</span><span class="sxs-lookup"><span data-stu-id="7cba9-359">WCF will fail any attempt to serialize or deserialize any other type through this service interface.</span></span>  
  
 <span data-ttu-id="7cba9-360">Normalny WCF wymiany danych są według wartości.</span><span class="sxs-lookup"><span data-stu-id="7cba9-360">Normal WCF exchanges of data are by value.</span></span> <span data-ttu-id="7cba9-361">Gwarantuje to, że wywoływanie metod na jednym z tych obiektów danych wykonuje tylko lokalnie — nie wywoła kodu w innej warstwie.</span><span class="sxs-lookup"><span data-stu-id="7cba9-361">This guarantees that invoking methods on one of these data objects executes only locally – it will not invoke code on the other tier.</span></span> <span data-ttu-id="7cba9-362">Choć jest możliwe osiągnąć podobny zwracanych obiektów przez odwołanie *z* server, nie jest możliwe dla klienta do przekazania obiektu przez odwołanie *do* serwera.</span><span class="sxs-lookup"><span data-stu-id="7cba9-362">While it is possible to achieve something like by-reference objects returned *from* the server, it is not possible for a client to pass a by-reference object *to* the server.</span></span> <span data-ttu-id="7cba9-363">Scenariusz, który wymaga konwersacji i z powrotem między klientem i serwerem można osiągnąć programu WCF za pomocą usługi duplex.</span><span class="sxs-lookup"><span data-stu-id="7cba9-363">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span> <span data-ttu-id="7cba9-364">Aby uzyskać więcej informacji, zobacz [usługi dwukierunkowe](./feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="7cba9-364">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="7cba9-365">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="7cba9-365">Summary</span></span>  
 <span data-ttu-id="7cba9-366">Wywołaniem funkcji zdalnych .NET to platforma komunikacji, może być używany tylko w obrębie środowiska, w pełni zaufane.</span><span class="sxs-lookup"><span data-stu-id="7cba9-366">.NET Remoting is a communication framework intended to be used only within fully-trusted environments.</span></span> <span data-ttu-id="7cba9-367">Jest starszy produkt i obsługiwany tylko w przypadku zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="7cba9-367">It is a legacy product and supported only for backward compatibility.</span></span> <span data-ttu-id="7cba9-368">Nie można stosować do tworzenia nowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7cba9-368">It should not be used to build new applications.</span></span> <span data-ttu-id="7cba9-369">Z drugiej strony WCF została zaprojektowana z myślą o bezpieczeństwie i jest zalecane w przypadku nowych i istniejących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7cba9-369">Conversely, WCF was designed with security in mind and is recommended for new and existing applications.</span></span> <span data-ttu-id="7cba9-370">Firma Microsoft zaleca, aby istniejący aplikacji usług zdalnych można migrować zamiast tego użyć WCF lub Web API platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7cba9-370">Microsoft recommends that existing Remoting applications be migrated to use WCF or ASP.NET Web API instead.</span></span>