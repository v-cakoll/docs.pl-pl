---
title: 'Instrukcje: migrowanie zarządzanego kodu DCOM do WCF'
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 42edce63856b629511faeb165362da18ea3cecad
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833631"
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a><span data-ttu-id="8fedf-102">Instrukcje: migrowanie zarządzanego kodu DCOM do WCF</span><span class="sxs-lookup"><span data-stu-id="8fedf-102">How to: Migrate Managed-Code DCOM to WCF</span></span>
<span data-ttu-id="8fedf-103">Windows Communication Foundation (WCF) to zalecany i bezpieczny wybór dla rozproszonych Component Object Model (DCOM) dla wywołań kodu zarządzanego między serwerami i klientami w środowisku rozproszonym.</span><span class="sxs-lookup"><span data-stu-id="8fedf-103">Windows Communication Foundation (WCF) is the recommended and secure choice over Distributed Component Object Model (DCOM) for managed code calls between servers and clients in a distributed environment.</span></span> <span data-ttu-id="8fedf-104">W tym artykule przedstawiono sposób migrowania kodu z modelu DCOM do usługi WCF w następujących scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="8fedf-104">This article shows how you to migrate code from DCOM to WCF for the following scenarios.</span></span>  
  
- <span data-ttu-id="8fedf-105">Usługa zdalna zwraca obiekt przez wartość do klienta</span><span class="sxs-lookup"><span data-stu-id="8fedf-105">The remote service returns an object by-value to the client</span></span>  
  
- <span data-ttu-id="8fedf-106">Klient wysyła obiekt według wartości do usługi zdalnej.</span><span class="sxs-lookup"><span data-stu-id="8fedf-106">The client sends an object by-value to the remote service</span></span>  
  
- <span data-ttu-id="8fedf-107">Usługa zdalna zwraca obiekt przez odwołanie do klienta</span><span class="sxs-lookup"><span data-stu-id="8fedf-107">The remote service returns an object by-reference to the client</span></span>  
  
 <span data-ttu-id="8fedf-108">Ze względów bezpieczeństwa wysyłanie obiektu przez odwołanie z klienta do usługi nie jest dozwolone w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="8fedf-108">For security reasons, sending an object by-reference from the client to the service is not allowed in WCF.</span></span> <span data-ttu-id="8fedf-109">Scenariusz, który wymaga konwersacji między klientem a serwerem można osiągnąć w programie WCF przy użyciu usługi dupleksowej.</span><span class="sxs-lookup"><span data-stu-id="8fedf-109">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span>  <span data-ttu-id="8fedf-110">Aby uzyskać więcej informacji na temat usług dupleksowych, zobacz [usługi dupleksowe](../wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="8fedf-110">For more information about duplex services, see [Duplex Services](../wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="8fedf-111">Aby uzyskać więcej informacji na temat tworzenia usług i klientów programu WCF dla tych usług, zobacz [podstawowe programowanie WCF](../wcf/basic-wcf-programming.md), [projektowanie i implementowanie usług](../wcf/designing-and-implementing-services.md)oraz [Kompilowanie klientów](../wcf/building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="8fedf-111">For more details about creating WCF services and clients for those services, see [Basic WCF Programming](../wcf/basic-wcf-programming.md), [Designing and Implementing Services](../wcf/designing-and-implementing-services.md), and [Building Clients](../wcf/building-clients.md).</span></span>  
  
## <a name="dcom-example-code"></a><span data-ttu-id="8fedf-112">Przykładowy kod DCOM</span><span class="sxs-lookup"><span data-stu-id="8fedf-112">DCOM example code</span></span>  
 <span data-ttu-id="8fedf-113">W tych scenariuszach interfejsy DCOM, które są zilustrowane przy użyciu programu WCF, mają następującą strukturę:</span><span class="sxs-lookup"><span data-stu-id="8fedf-113">For these scenarios, the DCOM interfaces that are illustrated using WCF have the following structure:</span></span>  
  
```csharp  
[ComVisible(true)]  
[Guid("AA9C4CDB-55EA-4413-90D2-843F1A49E6E6")]  
public interface IRemoteService  
{  
   Customer GetObjectByValue();  
   IRemoteObject GetObjectByReference();  
   void SendObjectByValue(Customer customer);  
}  
  
[ComVisible(true)]  
[Guid("A12C98DE-B6A1-463D-8C24-81E4BBC4351B")]  
public interface IRemoteObject  
{  
}  
  
public class Customer  
{  
}  
```  
  
## <a name="the-service-returns-an-object-by-value"></a><span data-ttu-id="8fedf-114">Usługa zwraca obiekt według wartości</span><span class="sxs-lookup"><span data-stu-id="8fedf-114">The service returns an object by-value</span></span>  
 <span data-ttu-id="8fedf-115">W tym scenariuszu należy wykonać wywołanie do usługi i Metoda ta zwraca obiekt, który jest przesyłany przez wartość z serwera do klienta.</span><span class="sxs-lookup"><span data-stu-id="8fedf-115">For this scenario, you make a call to a service and it method returns an object, which is passed by-value from the server to the client.</span></span> <span data-ttu-id="8fedf-116">Ten scenariusz reprezentuje następujące wywołanie COM:</span><span class="sxs-lookup"><span data-stu-id="8fedf-116">This scenario represents the following COM call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 <span data-ttu-id="8fedf-117">W tym scenariuszu klient otrzymuje deserializowaną kopię obiektu z usługi zdalnej.</span><span class="sxs-lookup"><span data-stu-id="8fedf-117">In this scenario, the client receives a deserialized copy of an object from the remote service.</span></span> <span data-ttu-id="8fedf-118">Klient może korzystać z tej kopii lokalnej bez wywołania zwrotnego do usługi.</span><span class="sxs-lookup"><span data-stu-id="8fedf-118">The client can interact with this local copy without calling back to the service.</span></span>  <span data-ttu-id="8fedf-119">Innymi słowy klient ma gwarancję, że usługa nie będzie uczestniczyć w żaden sposób w przypadku wywołania metod w kopii lokalnej.</span><span class="sxs-lookup"><span data-stu-id="8fedf-119">In other words, the client is guaranteed the service will not be involved in any way when methods on the local copy are called.</span></span> <span data-ttu-id="8fedf-120">Program WCF zawsze zwraca obiekty z usługi według wartości, dlatego w poniższych krokach opisano tworzenie zwykłej usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="8fedf-120">WCF always returns objects from the service by value, so the following steps describe creating a regular WCF service.</span></span>  
  
### <a name="step-1-define-the-wcf-service-interface"></a><span data-ttu-id="8fedf-121">Krok 1. Definiowanie interfejsu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="8fedf-121">Step 1: Define the WCF service interface</span></span>  
 <span data-ttu-id="8fedf-122">Zdefiniuj interfejs publiczny dla usługi WCF i oznacz go przy użyciu atrybutu [<xref:System.ServiceModel.ServiceContractAttribute>].</span><span class="sxs-lookup"><span data-stu-id="8fedf-122">Define a public interface for the WCF service and mark it with the [<xref:System.ServiceModel.ServiceContractAttribute>] attribute.</span></span>  <span data-ttu-id="8fedf-123">Oznacz metody, które chcesz uwidocznić klientom z atrybutem [<xref:System.ServiceModel.OperationContractAttribute>].</span><span class="sxs-lookup"><span data-stu-id="8fedf-123">Mark the methods you want to expose to clients with the [<xref:System.ServiceModel.OperationContractAttribute>] attribute.</span></span> <span data-ttu-id="8fedf-124">Poniższy przykład pokazuje, jak używać tych atrybutów do identyfikowania interfejsów po stronie serwera i metod interfejsu, które klient może wywoływać.</span><span class="sxs-lookup"><span data-stu-id="8fedf-124">The following example shows using these attributes to identify the server-side interface and interface methods a client can call.</span></span> <span data-ttu-id="8fedf-125">Metoda użyta w tym scenariuszu jest pogrubienie.</span><span class="sxs-lookup"><span data-stu-id="8fedf-125">The method used for this scenario is shown in bold.</span></span>  
  
```csharp  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Web;   
. . .  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]  
    void StoreCustomer(Customer customer);  
  
    [OperationContract]     Customer GetCustomer(string firstName, string lastName);   
  
}  
```  
  
### <a name="step-2-define-the-data-contract"></a><span data-ttu-id="8fedf-126">Krok 2. Definiowanie kontraktu danych</span><span class="sxs-lookup"><span data-stu-id="8fedf-126">Step 2: Define the data contract</span></span>  
 <span data-ttu-id="8fedf-127">Następnie należy utworzyć kontrakt danych dla usługi, która będzie opisywać, w jaki sposób dane będą wymieniane między usługą i jej klientami.</span><span class="sxs-lookup"><span data-stu-id="8fedf-127">Next you should create a data contract for the service, which will describe how the data will be exchanged between the service and its clients.</span></span>  <span data-ttu-id="8fedf-128">Klasy opisane w kontrakcie danych powinny być oznaczone atrybutem [<xref:System.Runtime.Serialization.DataContractAttribute>].</span><span class="sxs-lookup"><span data-stu-id="8fedf-128">Classes described in the data contract should be marked with the [<xref:System.Runtime.Serialization.DataContractAttribute>] attribute.</span></span> <span data-ttu-id="8fedf-129">Poszczególne właściwości lub pola, które mają być widoczne zarówno dla klienta, jak i serwera, powinny być oznaczone atrybutem [<xref:System.Runtime.Serialization.DataMemberAttribute>].</span><span class="sxs-lookup"><span data-stu-id="8fedf-129">The individual properties or fields you want visible to both client and server should be marked with the [<xref:System.Runtime.Serialization.DataMemberAttribute>] attribute.</span></span> <span data-ttu-id="8fedf-130">Jeśli chcesz, aby typy pochodne od klasy w kontrakcie danych były dozwolone, należy je zidentyfikować przy użyciu atrybutu [<xref:System.Runtime.Serialization.KnownTypeAttribute>].</span><span class="sxs-lookup"><span data-stu-id="8fedf-130">If you want types derived from a class in the data contract to be allowed, you must identify them with the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute.</span></span> <span data-ttu-id="8fedf-131">Funkcja WCF będzie serializować lub deserializować typy w interfejsie usługi i typach identyfikowanych jako znane typy.</span><span class="sxs-lookup"><span data-stu-id="8fedf-131">WCF will only serialize or deserialize types in the service interface and types identified as known types.</span></span> <span data-ttu-id="8fedf-132">Jeśli spróbujesz użyć typu, który nie jest typem znanym, wystąpi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8fedf-132">If you attempt to use a type that is not a known type, an exception will occur.</span></span>  
  
 <span data-ttu-id="8fedf-133">Aby uzyskać więcej informacji na temat umów dotyczących danych, zobacz [Kontrakty danych](../wcf/samples/data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="8fedf-133">For more information about data contracts, see [Data Contracts](../wcf/samples/data-contracts.md).</span></span>  
  
```csharp  
[DataContract]  
[KnownType(typeof(PremiumCustomer))]  
public class Customer  
{  
    [DataMember]  
    public string Firstname;  
    [DataMember]  
    public string Lastname;  
    [DataMember]  
    public Address DefaultDeliveryAddress;  
    [DataMember]  
    public Address DefaultBillingAddress;  
}  
 [DataContract]  
public class PremiumCustomer : Customer  
{  
    [DataMember]  
    public int AccountID;  
}  
  
 [DataContract]  
public class Address  
{  
    [DataMember]  
    public string Street;  
    [DataMember]  
    public string Zipcode;  
    [DataMember]  
    public string City;  
    [DataMember]  
    public string State;  
    [DataMember]  
    public string Country;  
}  
```  
  
### <a name="step-3-implement-the-wcf-service"></a><span data-ttu-id="8fedf-134">Krok 3. Implementowanie usługi WCF</span><span class="sxs-lookup"><span data-stu-id="8fedf-134">Step 3: Implement the WCF service</span></span>  
 <span data-ttu-id="8fedf-135">Następnie należy zaimplementować klasę usługi WCF implementującą interfejs zdefiniowany w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="8fedf-135">Next, you should implement the WCF service class that implements the interface you defined in the previous step.</span></span>  
  
```csharp  
public class CustomerService: ICustomerManager    
{  
    public void StoreCustomer(Customer customer)  
    {  
        // write to a database  
    }  
    public Customer GetCustomer(string firstName, string lastName)  
    {  
        // read from a database  
    }  
}  
```  
  
### <a name="step-4-configure-the-service-and-the-client"></a><span data-ttu-id="8fedf-136">Krok 4. Konfigurowanie usługi i klienta</span><span class="sxs-lookup"><span data-stu-id="8fedf-136">Step 4: Configure the service and the client</span></span>  
 <span data-ttu-id="8fedf-137">Aby uruchomić usługę WCF, należy zadeklarować punkt końcowy, który uwidacznia ten interfejs usługi w określonym adresie URL przy użyciu określonego powiązania WCF.</span><span class="sxs-lookup"><span data-stu-id="8fedf-137">To run a WCF service, you need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="8fedf-138">Powiązanie określa informacje o transportach, kodowaniu i protokole dla klientów i serwera do komunikacji.</span><span class="sxs-lookup"><span data-stu-id="8fedf-138">A binding specifies the transport, encoding and protocol details for the clients and server to communicate.</span></span> <span data-ttu-id="8fedf-139">Zazwyczaj można dodawać powiązania do pliku konfiguracji projektu usługi (Web. config).</span><span class="sxs-lookup"><span data-stu-id="8fedf-139">You typically add bindings to the service project’s configuration file (web.config).</span></span> <span data-ttu-id="8fedf-140">Poniżej przedstawiono wpis powiązania dla przykładowej usługi:</span><span class="sxs-lookup"><span data-stu-id="8fedf-140">The following shows a binding entry for the example service:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Server.CustomerService">  
        <endpoint address="http://localhost:8083/CustomerManager"   
                  binding="basicHttpBinding"  
                  contract="Shared.ICustomerManager" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="8fedf-141">Następnie należy skonfigurować klienta tak, aby pasował do informacji o powiązaniu określonych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="8fedf-141">Next, you need to configure the client to match the binding information specified by the service.</span></span> <span data-ttu-id="8fedf-142">Aby to zrobić, Dodaj następujący plik do pliku konfiguracji aplikacji klienta (App. config).</span><span class="sxs-lookup"><span data-stu-id="8fedf-142">To do so, add the following to the client’s application configuration (app.config) file.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="customermanager"   
                address="http://localhost:8083/CustomerManager"   
                binding="basicHttpBinding"   
                contract="Shared.ICustomerManager"/>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="step-5-run-the-service"></a><span data-ttu-id="8fedf-143">Krok 5. uruchomienie usługi</span><span class="sxs-lookup"><span data-stu-id="8fedf-143">Step 5: Run the service</span></span>  
 <span data-ttu-id="8fedf-144">Na koniec możesz go hostować w aplikacji konsolowej, dodając następujące wiersze do aplikacji usługi i uruchamiając aplikację.</span><span class="sxs-lookup"><span data-stu-id="8fedf-144">Finally, you can self-host it in a console application by adding the following lines to the service app, and starting the app.</span></span> <span data-ttu-id="8fedf-145">Aby uzyskać więcej informacji na temat innych sposobów hostowania aplikacji usługi WCF, [usług hostingowych](../wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="8fedf-145">For more information about other ways to host a WCF service application, [Hosting Services](../wcf/hosting-services.md).</span></span>  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a><span data-ttu-id="8fedf-146">Krok 6. Wywoływanie usługi z klienta</span><span class="sxs-lookup"><span data-stu-id="8fedf-146">Step 6: Call the service from the client</span></span>  
 <span data-ttu-id="8fedf-147">Aby wywołać usługę od klienta, należy utworzyć fabrykę kanałów dla usługi i zażądać kanału, co umożliwi bezpośrednie wywoływanie metody `GetCustomer` bezpośrednio od klienta.</span><span class="sxs-lookup"><span data-stu-id="8fedf-147">To call the service from the client, you need to create a channel factory for the service, and request a channel, which will enable you to directly call the `GetCustomer` method directly from the client.</span></span> <span data-ttu-id="8fedf-148">Kanał implementuje interfejs usługi i obsługuje podstawową logikę żądania/odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8fedf-148">The channel implements the service’s interface and handles the underlying request/reply logic for you.</span></span>  <span data-ttu-id="8fedf-149">Wartością zwracaną z tego wywołania metody jest deserializowana kopia odpowiedzi usługi.</span><span class="sxs-lookup"><span data-stu-id="8fedf-149">The return value from that method call is the deserialized copy of the service response.</span></span>  
  
```csharp  
ChannelFactory<ICustomerManager> factory =   
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a><span data-ttu-id="8fedf-150">Klient wysyła do serwera obiekt przez wartość</span><span class="sxs-lookup"><span data-stu-id="8fedf-150">The client sends a by-value object to the server</span></span>  
 <span data-ttu-id="8fedf-151">W tym scenariuszu klient wysyła do serwera obiekt, według wartości.</span><span class="sxs-lookup"><span data-stu-id="8fedf-151">In this scenario, the client sends an object to the server, by-value.</span></span> <span data-ttu-id="8fedf-152">Oznacza to, że serwer otrzyma deserializowaną kopię obiektu.</span><span class="sxs-lookup"><span data-stu-id="8fedf-152">This means that the server will receive a deserialized copy of the object.</span></span>  <span data-ttu-id="8fedf-153">Serwer może wywoływać metody w tej kopii i zagwarantować, że nie ma wywołania zwrotnego w kodzie klienta.</span><span class="sxs-lookup"><span data-stu-id="8fedf-153">The server can call methods on that copy and be guaranteed there is no callback into client code.</span></span> <span data-ttu-id="8fedf-154">Jak wspomniano wcześniej, normalne wymiany danych WCF są według wartości.</span><span class="sxs-lookup"><span data-stu-id="8fedf-154">As mentioned previously, normal WCF exchanges of data are by-value.</span></span>  <span data-ttu-id="8fedf-155">Gwarantuje to, że wywoływanie metod na jednym z tych obiektów jest wykonywane tylko lokalnie — nie wywoła kodu na kliencie.</span><span class="sxs-lookup"><span data-stu-id="8fedf-155">This guarantees that calling methods on one of these objects executes locally only – it will not invoke code on the client.</span></span>  
  
 <span data-ttu-id="8fedf-156">Ten scenariusz reprezentuje następujące wywołanie metody COM:</span><span class="sxs-lookup"><span data-stu-id="8fedf-156">This scenario represents the following COM method call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 <span data-ttu-id="8fedf-157">Ten scenariusz używa tego samego interfejsu usługi i kontraktu danych, jak pokazano w pierwszym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8fedf-157">This scenario uses the same service interface and data contract as shown in the first example.</span></span> <span data-ttu-id="8fedf-158">Ponadto klient i usługa zostaną skonfigurowane w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="8fedf-158">In addition, the client and service will be configured in the same way.</span></span> <span data-ttu-id="8fedf-159">W tym przykładzie tworzony jest kanał służący do wysyłania obiektu i uruchamiania w ten sam sposób.</span><span class="sxs-lookup"><span data-stu-id="8fedf-159">In this example, a channel is created to send the object and run the same way.</span></span> <span data-ttu-id="8fedf-160">Jednak w tym przykładzie utworzysz klienta, który wywoła usługę, przekazując obiekt według wartości.</span><span class="sxs-lookup"><span data-stu-id="8fedf-160">However, for this example, you will create a client that calls the service, passing an object by-value.</span></span> <span data-ttu-id="8fedf-161">Metoda usługi, która będzie wywoływana przez klienta w kontrakcie usługi, jest pogrubienie:</span><span class="sxs-lookup"><span data-stu-id="8fedf-161">The service method the client will call in the service contract is shown in bold:</span></span>  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a><span data-ttu-id="8fedf-162">Dodawanie kodu do klienta wysyłającego obiekt przez wartość</span><span class="sxs-lookup"><span data-stu-id="8fedf-162">Add code to the client that sends a by-value object</span></span>  
 <span data-ttu-id="8fedf-163">Poniższy kod pokazuje, jak klient tworzy nowy obiekt klienta według wartości, tworzy kanał do komunikacji z usługą `ICustomerManager` i wysyła do niego obiekt klienta.</span><span class="sxs-lookup"><span data-stu-id="8fedf-163">The following code shows how the client creates a new by-value customer object, creates a channel to communicate with the `ICustomerManager` service, and sends the customer object to it.</span></span>  
  
 <span data-ttu-id="8fedf-164">Obiekt klienta zostanie Zserializowany i wysłany do usługi, w którym zostanie odszeregowany przez usługę w nowej kopii tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="8fedf-164">The customer object will be serialized, and sent to the service, where it is deserialized by the service into a new copy of that object.</span></span>  <span data-ttu-id="8fedf-165">Wszystkie metody wywołania usługi na tym obiekcie będą wykonywane tylko lokalnie na serwerze.</span><span class="sxs-lookup"><span data-stu-id="8fedf-165">Any methods the service calls on this object will execute only locally on the server.</span></span> <span data-ttu-id="8fedf-166">Należy zauważyć, że ten kod ilustruje wysyłanie typu pochodnego (`PremiumCustomer`).</span><span class="sxs-lookup"><span data-stu-id="8fedf-166">It’s important to note that this code illustrates sending a derived type (`PremiumCustomer`).</span></span>  <span data-ttu-id="8fedf-167">Kontrakt usługi oczekuje obiektu `Customer`, ale kontrakt danych usługi używa atrybutu [<xref:System.Runtime.Serialization.KnownTypeAttribute>], aby wskazać, że `PremiumCustomer` jest również dozwolone.</span><span class="sxs-lookup"><span data-stu-id="8fedf-167">The service contract expects a `Customer` object, but the service data contract uses the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute to indicate that `PremiumCustomer` is also allowed.</span></span>  <span data-ttu-id="8fedf-168">Funkcja WCF nie będzie podejmować próby serializacji lub deserializacji dowolnego innego typu za pośrednictwem tego interfejsu usługi.</span><span class="sxs-lookup"><span data-stu-id="8fedf-168">WCF will fail attempts to serialize or deserialize any other type via this service interface.</span></span>  
  
```csharp  
PremiumCustomer customer = new PremiumCustomer();  
customer.Firstname = "John";  
customer.Lastname = "Doe";  
customer.DefaultBillingAddress = new Address();  
customer.DefaultBillingAddress.Street = "One Microsoft Way";  
customer.DefaultDeliveryAddress = customer.DefaultBillingAddress;  
customer.AccountID = 42;  
  
ChannelFactory<ICustomerManager> factory =  
   new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager customerManager = factory.CreateChannel();  
customerManager.StoreCustomer(customer);  
```  
  
## <a name="the-service-returns-an-object-by-reference"></a><span data-ttu-id="8fedf-169">Usługa zwraca obiekt przez odwołanie</span><span class="sxs-lookup"><span data-stu-id="8fedf-169">The service returns an object by reference</span></span>  
 <span data-ttu-id="8fedf-170">W tym scenariuszu aplikacja kliencka wysyła wywołanie do usługi zdalnej, a metoda zwraca obiekt, który jest przesyłany przez odwołanie z usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="8fedf-170">For this scenario, the client app makes a call to the remote service and the method returns an object, which is passed by reference from the service to the client.</span></span>  
  
 <span data-ttu-id="8fedf-171">Jak wspomniano wcześniej, usługi WCF zawsze zwracają obiekt według wartości.</span><span class="sxs-lookup"><span data-stu-id="8fedf-171">As mentioned previously, WCF services always return object by value.</span></span>  <span data-ttu-id="8fedf-172">Można jednak osiągnąć podobny wynik przy użyciu klasy <xref:System.ServiceModel.EndpointAddress10>.</span><span class="sxs-lookup"><span data-stu-id="8fedf-172">However, you can achieve a similar result by using the <xref:System.ServiceModel.EndpointAddress10> class.</span></span>  <span data-ttu-id="8fedf-173">@No__t-0 to obiekt możliwy do serializacji przez wartość, który może być używany przez klienta w celu uzyskania na serwerze sesji na podstawie obiektu odniesienia.</span><span class="sxs-lookup"><span data-stu-id="8fedf-173">The <xref:System.ServiceModel.EndpointAddress10> is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span>  
  
 <span data-ttu-id="8fedf-174">Zachowanie obiektu przez odwołanie w programie WCF przedstawionym w tym scenariuszu różni się od modelu DCOM.</span><span class="sxs-lookup"><span data-stu-id="8fedf-174">The behavior of the by-reference object in WCF shown in this scenario is different than DCOM.</span></span>  <span data-ttu-id="8fedf-175">W modelu DCOM serwer może bezpośrednio zwrócić do klienta obiekt przez odwołanie, a klient może wywołać metody tego obiektu, które są wykonywane na serwerze.</span><span class="sxs-lookup"><span data-stu-id="8fedf-175">In DCOM, the server can return a by-reference object to the client directly, and the client can call that object’s methods, which execute on the server.</span></span>  <span data-ttu-id="8fedf-176">W programie WCF jednak zwracany obiekt jest zawsze przez wartość.</span><span class="sxs-lookup"><span data-stu-id="8fedf-176">In WCF, however, the object returned is always by-value.</span></span>  <span data-ttu-id="8fedf-177">Klient musi wykonać ten obiekt przez wartość, reprezentowany przez <xref:System.ServiceModel.EndpointAddress10> i użyć go do utworzenia własnej sesji na obiekt-odwołanie.</span><span class="sxs-lookup"><span data-stu-id="8fedf-177">The client must take that by-value object, represented by <xref:System.ServiceModel.EndpointAddress10> and use it to create its own sessionful by-reference object.</span></span>  <span data-ttu-id="8fedf-178">Metoda kliencka wywołuje na serwerze. Innymi słowy, ten obiekt odwołujący się do programu WCF to normalna usługa WCF, która jest skonfigurowana do sesji.</span><span class="sxs-lookup"><span data-stu-id="8fedf-178">The client method calls on the sessionful object execute on the server.In other words, this by-reference object in WCF is a normal WCF service that is configured to be sessionful.</span></span>  
  
 <span data-ttu-id="8fedf-179">W programie WCF sesja jest sposobem skorelowania wielu wiadomości przesyłanych między dwoma punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="8fedf-179">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span>  <span data-ttu-id="8fedf-180">Oznacza to, że gdy klient uzyska połączenie z tą usługą, zostanie ustanowiona sesja między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="8fedf-180">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span>  <span data-ttu-id="8fedf-181">Klient będzie używać jednego unikatowego wystąpienia obiektu po stronie serwera dla wszystkich jego interakcji w ramach jednej sesji.</span><span class="sxs-lookup"><span data-stu-id="8fedf-181">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span> <span data-ttu-id="8fedf-182">Umowy WCF dotyczące sesji są podobne do wzorców żądań i odpowiedzi sieciowych zorientowanych na połączenia.</span><span class="sxs-lookup"><span data-stu-id="8fedf-182">Sessionful WCF contracts are similar to connection-oriented network request/response patterns.</span></span>  
  
 <span data-ttu-id="8fedf-183">Ten scenariusz jest reprezentowany przez poniższą metodę DCOM.</span><span class="sxs-lookup"><span data-stu-id="8fedf-183">This scenario is represented by the following DCOM method.</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a><span data-ttu-id="8fedf-184">Krok 1. Definiowanie sesji interfejsu i implementacji usługi WCF</span><span class="sxs-lookup"><span data-stu-id="8fedf-184">Step 1: Define the Sessionful WCF service interface and implementation</span></span>  
 <span data-ttu-id="8fedf-185">Najpierw Zdefiniuj interfejs usługi WCF, który zawiera obiekt session.</span><span class="sxs-lookup"><span data-stu-id="8fedf-185">First, define a WCF service interface that contains the sessionful object.</span></span>  
  
 <span data-ttu-id="8fedf-186">W tym kodzie obiekt sesji jest oznaczony atrybutem `ServiceContract`, który identyfikuje go jako zwykły interfejs usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="8fedf-186">In this code, the sessionful object is marked with the `ServiceContract` attribute, which identifies it as a regular WCF service interface.</span></span>  <span data-ttu-id="8fedf-187">Ponadto Właściwość <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> ma ustawioną wartość wskazującą, że będzie to usługa sesji.</span><span class="sxs-lookup"><span data-stu-id="8fedf-187">In addition, the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> property is set to indicate it will be a sessionful service.</span></span>  
  
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
  
 <span data-ttu-id="8fedf-188">Poniższy kod przedstawia implementację usługi.</span><span class="sxs-lookup"><span data-stu-id="8fedf-188">The following code shows the service implementation.</span></span>  
  
 <span data-ttu-id="8fedf-189">Usługa jest oznaczona atrybutem [ServiceBehavior], a jej Właściwość InstanceContextmode ma wartość InstanceContextmode. PerSessions, aby wskazać, że dla każdej sesji należy utworzyć unikatowe wystąpienie tego typu.</span><span class="sxs-lookup"><span data-stu-id="8fedf-189">The service is marked with the [ServiceBehavior] attribute, and its InstanceContextMode property set to InstanceContextMode.PerSessions to indicate that a unique instance of this type should be created for each session.</span></span>  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a><span data-ttu-id="8fedf-190">Krok 2. Definiowanie usługi fabryki WCF dla obiektu sesji</span><span class="sxs-lookup"><span data-stu-id="8fedf-190">Step 2: Define the WCF factory service for the sessionful object</span></span>  
 <span data-ttu-id="8fedf-191">Usługa, która tworzy obiekt sesji, musi być zdefiniowana i zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="8fedf-191">The service that creates the sessionful object must be defined and implemented.</span></span> <span data-ttu-id="8fedf-192">Poniższy kod pokazuje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="8fedf-192">The following code shows how to do this.</span></span> <span data-ttu-id="8fedf-193">Ten kod tworzy kolejną usługę WCF, która zwraca obiekt <xref:System.ServiceModel.EndpointAddress10>.</span><span class="sxs-lookup"><span data-stu-id="8fedf-193">This code creates another WCF service that returns an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  <span data-ttu-id="8fedf-194">Jest to możliwy do serializacji formularz punktu końcowego, którego można użyć do utworzenia obiektu z pełnymi sesjami.</span><span class="sxs-lookup"><span data-stu-id="8fedf-194">This is a serializable form of an endpoint the can use to create the session-full object.</span></span>  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 <span data-ttu-id="8fedf-195">Poniżej przedstawiono implementację tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8fedf-195">The following is the implementation of this service.</span></span> <span data-ttu-id="8fedf-196">Ta implementacja obsługuje pojedyncze fabryki kanałów do tworzenia obiektów sesji.</span><span class="sxs-lookup"><span data-stu-id="8fedf-196">This implementation maintains a singleton channel factory to create sessionful objects.</span></span>  <span data-ttu-id="8fedf-197">Po wywołaniu `GetInstanceAddress` tworzy kanał i tworzy obiekt <xref:System.ServiceModel.EndpointAddress10>, który wskazuje na adres zdalny skojarzony z tym kanałem.</span><span class="sxs-lookup"><span data-stu-id="8fedf-197">When `GetInstanceAddress` is called, it creates a channel and creates an <xref:System.ServiceModel.EndpointAddress10> object that points to the remote address associated with this channel.</span></span>   <span data-ttu-id="8fedf-198"><xref:System.ServiceModel.EndpointAddress10> to typ danych, który może być zwracany do klienta przez wartość.</span><span class="sxs-lookup"><span data-stu-id="8fedf-198"><xref:System.ServiceModel.EndpointAddress10> is a data type that can be returned to the client by-value.</span></span>
  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a><span data-ttu-id="8fedf-199">Krok 3. Konfigurowanie i uruchamianie usług WCF</span><span class="sxs-lookup"><span data-stu-id="8fedf-199">Step 3: Configure and start the WCF services</span></span>  
 <span data-ttu-id="8fedf-200">Aby hostować te usługi, należy wprowadzić następujące dodatki do pliku konfiguracji serwera (Web. config).</span><span class="sxs-lookup"><span data-stu-id="8fedf-200">To host these services, you will need to make the following additions to the server’s configuration file (web.config).</span></span>  
  
1. <span data-ttu-id="8fedf-201">Dodaj sekcję `<client>` opisującą punkt końcowy dla obiektu sesji.</span><span class="sxs-lookup"><span data-stu-id="8fedf-201">Add a `<client>` section that describes the endpoint for the sessionful object.</span></span>  <span data-ttu-id="8fedf-202">W tym scenariuszu serwer działa również jako klient i musi być skonfigurowany, aby go włączyć.</span><span class="sxs-lookup"><span data-stu-id="8fedf-202">In this scenario, the server also acts as a client and must be configured to enable this.</span></span>  
  
2. <span data-ttu-id="8fedf-203">W sekcji `<services>` Zadeklaruj punkty końcowe usługi dla obiektu fabryki i sesji.</span><span class="sxs-lookup"><span data-stu-id="8fedf-203">In the `<services>` section, declare service endpoints for the factory and sessionful object.</span></span>  <span data-ttu-id="8fedf-204">Dzięki temu Klient może komunikować się z punktami końcowymi usługi, uzyskać <xref:System.ServiceModel.EndpointAddress10> i utworzyć kanał sesji.</span><span class="sxs-lookup"><span data-stu-id="8fedf-204">This enables the client to communicate with the service endpoints, acquire the <xref:System.ServiceModel.EndpointAddress10> and create the sessionful channel.</span></span>  
  
 <span data-ttu-id="8fedf-205">Poniżej przedstawiono przykładowy plik konfiguracji z następującymi ustawieniami:</span><span class="sxs-lookup"><span data-stu-id="8fedf-205">The following is an example configuration file with these settings:</span></span>  
  
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
  
 <span data-ttu-id="8fedf-206">Dodaj następujące wiersze do aplikacji konsolowej, do samodzielnego hostowania usługi i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="8fedf-206">Add the following lines to a console application, to self-host the service, and start the app.</span></span>  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a><span data-ttu-id="8fedf-207">Krok 4. Konfigurowanie klienta i wywoływanie usługi</span><span class="sxs-lookup"><span data-stu-id="8fedf-207">Step 4: Configure the client and call the service</span></span>  
 <span data-ttu-id="8fedf-208">Skonfiguruj klienta programu do komunikacji z usługami WCF, wprowadzając następujące wpisy w pliku konfiguracyjnym aplikacji projektu (App. config).</span><span class="sxs-lookup"><span data-stu-id="8fedf-208">Configure the client to communicate with the WCF services by making the following entries in the project’s application configuration file (app.config).</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
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
  
 <span data-ttu-id="8fedf-209">Aby wywołać usługę, Dodaj kod do klienta, aby wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="8fedf-209">To call the service, add the code to the client to do the following:</span></span>  
  
1. <span data-ttu-id="8fedf-210">Utwórz kanał dla usługi `ISessionBoundFactory`.</span><span class="sxs-lookup"><span data-stu-id="8fedf-210">Create a channel to the `ISessionBoundFactory` service.</span></span>  
  
2. <span data-ttu-id="8fedf-211">Użyj kanału, aby wywołać usługę `ISessionBoundFactory` i uzyskać obiekt <xref:System.ServiceModel.EndpointAddress10>.</span><span class="sxs-lookup"><span data-stu-id="8fedf-211">Use the channel to invoke the `ISessionBoundFactory` service an obtain an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  
  
3. <span data-ttu-id="8fedf-212">Użyj <xref:System.ServiceModel.EndpointAddress10>, aby utworzyć kanał do uzyskania obiektu sesji.</span><span class="sxs-lookup"><span data-stu-id="8fedf-212">Use the <xref:System.ServiceModel.EndpointAddress10> to create a channel to obtain a sessionful object.</span></span>  
  
4. <span data-ttu-id="8fedf-213">Wywołaj metody `SetCurrentValue` i `GetCurrentValue`, aby pokazać, że to samo wystąpienie obiektu jest używane w wielu wywołaniach.</span><span class="sxs-lookup"><span data-stu-id="8fedf-213">Call the `SetCurrentValue` and `GetCurrentValue` methods to demonstrate it remains the same object instance is used across multiple calls.</span></span>  
  
```csharp  
ChannelFactory<ISessionBoundFactory> factory =  
        new ChannelFactory<ISessionBoundFactory>("factory");  
  
ISessionBoundFactory sessionBoundFactory = factory.CreateChannel();  
  
EndpointAddress10 address = sessionBoundFactory.GetInstanceAddress();  
  
ChannelFactory<ISessionBoundObject> sessionBoundObjectFactory =  
    new ChannelFactory<ISessionBoundObject>(  
        new NetTcpBinding(),  
        address.ToEndpointAddress());  
  
ISessionBoundObject sessionBoundObject =  
        sessionBoundObjectFactory.CreateChannel();  
  
sessionBoundObject.SetCurrentValue("Hello");  
if (sessionBoundObject.GetCurrentValue() == "Hello")  
{  
    Console.WriteLine("Session-full instance management works as expected");  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="8fedf-214">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8fedf-214">See also</span></span>

- [<span data-ttu-id="8fedf-215">Podstawy programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="8fedf-215">Basic WCF Programming</span></span>](../wcf/basic-wcf-programming.md)
- [<span data-ttu-id="8fedf-216">Projektowanie i implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="8fedf-216">Designing and Implementing Services</span></span>](../wcf/designing-and-implementing-services.md)
- [<span data-ttu-id="8fedf-217">Kompilowanie klientów</span><span class="sxs-lookup"><span data-stu-id="8fedf-217">Building Clients</span></span>](../wcf/building-clients.md)
- [<span data-ttu-id="8fedf-218">Usługi dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="8fedf-218">Duplex Services</span></span>](../wcf/feature-details/duplex-services.md)
