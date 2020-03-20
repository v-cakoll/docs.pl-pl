---
title: 'Instrukcje: migrowanie zarządzanego kodu DCOM do WCF'
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
ms.openlocfilehash: 2576e88c25ae381e90ec7d613efb648048145b3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181392"
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a><span data-ttu-id="f68c2-102">Instrukcje: migrowanie zarządzanego kodu DCOM do WCF</span><span class="sxs-lookup"><span data-stu-id="f68c2-102">How to: Migrate Managed-Code DCOM to WCF</span></span>
<span data-ttu-id="f68c2-103">Windows Communication Foundation (WCF) jest zalecanym i bezpiecznym wyborem w stosunku do modelu DCOM (Distributed Component Object Model) dla wywołań kodu zarządzanego między serwerami i klientami w środowisku rozproszonym.</span><span class="sxs-lookup"><span data-stu-id="f68c2-103">Windows Communication Foundation (WCF) is the recommended and secure choice over Distributed Component Object Model (DCOM) for managed code calls between servers and clients in a distributed environment.</span></span> <span data-ttu-id="f68c2-104">W tym artykule pokazano, jak przeprowadzić migrację kodu z dcom do WCF dla następujących scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="f68c2-104">This article shows how you to migrate code from DCOM to WCF for the following scenarios.</span></span>  
  
- <span data-ttu-id="f68c2-105">Usługa zdalna zwraca klientowi wartość po wartości obiektu</span><span class="sxs-lookup"><span data-stu-id="f68c2-105">The remote service returns an object by-value to the client</span></span>  
  
- <span data-ttu-id="f68c2-106">Klient wysyła obiekt według wartości do usługi zdalnej</span><span class="sxs-lookup"><span data-stu-id="f68c2-106">The client sends an object by-value to the remote service</span></span>  
  
- <span data-ttu-id="f68c2-107">Usługa zdalna zwraca obiekt przez odwołanie do klienta</span><span class="sxs-lookup"><span data-stu-id="f68c2-107">The remote service returns an object by-reference to the client</span></span>  
  
 <span data-ttu-id="f68c2-108">Ze względów bezpieczeństwa wysyłanie obiektu przez odwołanie od klienta do usługi nie jest dozwolone w WCF.</span><span class="sxs-lookup"><span data-stu-id="f68c2-108">For security reasons, sending an object by-reference from the client to the service is not allowed in WCF.</span></span> <span data-ttu-id="f68c2-109">Scenariusz, który wymaga konwersacji tam iz powrotem między klientem a serwerem można osiągnąć w WCF przy użyciu usługi dupleksu.</span><span class="sxs-lookup"><span data-stu-id="f68c2-109">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span>  <span data-ttu-id="f68c2-110">Aby uzyskać więcej informacji na temat usług dupleksu, zobacz [Usługi dupleksu](../wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="f68c2-110">For more information about duplex services, see [Duplex Services](../wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="f68c2-111">Aby uzyskać więcej informacji na temat tworzenia usług WCF i klientów dla tych usług, zobacz [Podstawowe programowanie WCF,](../wcf/basic-wcf-programming.md) [projektowanie i wdrażanie usług](../wcf/designing-and-implementing-services.md)oraz budowanie [klientów](../wcf/building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="f68c2-111">For more details about creating WCF services and clients for those services, see [Basic WCF Programming](../wcf/basic-wcf-programming.md), [Designing and Implementing Services](../wcf/designing-and-implementing-services.md), and [Building Clients](../wcf/building-clients.md).</span></span>  
  
## <a name="dcom-example-code"></a><span data-ttu-id="f68c2-112">Przykładowy kod DCOM</span><span class="sxs-lookup"><span data-stu-id="f68c2-112">DCOM example code</span></span>  
 <span data-ttu-id="f68c2-113">W tych scenariuszach interfejsy DCOM, które są zilustrowane przy użyciu WCF mają następującą strukturę:</span><span class="sxs-lookup"><span data-stu-id="f68c2-113">For these scenarios, the DCOM interfaces that are illustrated using WCF have the following structure:</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-value"></a><span data-ttu-id="f68c2-114">Usługa zwraca obiekt według wartości</span><span class="sxs-lookup"><span data-stu-id="f68c2-114">The service returns an object by-value</span></span>  
 <span data-ttu-id="f68c2-115">W tym scenariuszu należy wywołać usługę i metoda zwraca obiekt, który jest przekazywany przez wartość z serwera do klienta.</span><span class="sxs-lookup"><span data-stu-id="f68c2-115">For this scenario, you make a call to a service and it method returns an object, which is passed by-value from the server to the client.</span></span> <span data-ttu-id="f68c2-116">W tym scenariuszu przedstawiono następujące wywołanie COM:</span><span class="sxs-lookup"><span data-stu-id="f68c2-116">This scenario represents the following COM call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 <span data-ttu-id="f68c2-117">W tym scenariuszu klient odbiera deserializowane kopię obiektu z usługi zdalnej.</span><span class="sxs-lookup"><span data-stu-id="f68c2-117">In this scenario, the client receives a deserialized copy of an object from the remote service.</span></span> <span data-ttu-id="f68c2-118">Klient może wchodzić w interakcje z tej kopii lokalnej bez wywoływania z powrotem do usługi.</span><span class="sxs-lookup"><span data-stu-id="f68c2-118">The client can interact with this local copy without calling back to the service.</span></span>  <span data-ttu-id="f68c2-119">Innymi słowy klient ma gwarancję, że usługa nie będzie w żaden sposób zaangażowany, gdy metody na kopii lokalnej są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="f68c2-119">In other words, the client is guaranteed the service will not be involved in any way when methods on the local copy are called.</span></span> <span data-ttu-id="f68c2-120">WCF zawsze zwraca obiekty z usługi według wartości, więc następujące kroki opisują tworzenie zwykłej usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="f68c2-120">WCF always returns objects from the service by value, so the following steps describe creating a regular WCF service.</span></span>  
  
### <a name="step-1-define-the-wcf-service-interface"></a><span data-ttu-id="f68c2-121">Krok 1: Zdefiniuj interfejs usługi WCF</span><span class="sxs-lookup"><span data-stu-id="f68c2-121">Step 1: Define the WCF service interface</span></span>  
 <span data-ttu-id="f68c2-122">Zdefiniuj interfejs publiczny dla usługi WCF i oznacz go atrybutem [<xref:System.ServiceModel.ServiceContractAttribute>] .</span><span class="sxs-lookup"><span data-stu-id="f68c2-122">Define a public interface for the WCF service and mark it with the [<xref:System.ServiceModel.ServiceContractAttribute>] attribute.</span></span>  <span data-ttu-id="f68c2-123">Oznacz metody, które chcesz udostępnić<xref:System.ServiceModel.OperationContractAttribute>klientom za pomocą atrybutu [ ].</span><span class="sxs-lookup"><span data-stu-id="f68c2-123">Mark the methods you want to expose to clients with the [<xref:System.ServiceModel.OperationContractAttribute>] attribute.</span></span> <span data-ttu-id="f68c2-124">Poniższy przykład pokazuje przy użyciu tych atrybutów do identyfikowania interfejsu po stronie serwera i metod interfejsu, które klient może wywołać.</span><span class="sxs-lookup"><span data-stu-id="f68c2-124">The following example shows using these attributes to identify the server-side interface and interface methods a client can call.</span></span> <span data-ttu-id="f68c2-125">Metoda używana w tym scenariuszu jest pokazana pogrubioną czcionką.</span><span class="sxs-lookup"><span data-stu-id="f68c2-125">The method used for this scenario is shown in bold.</span></span>  
  
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
  
### <a name="step-2-define-the-data-contract"></a><span data-ttu-id="f68c2-126">Krok 2: Zdefiniuj kontrakt na dane</span><span class="sxs-lookup"><span data-stu-id="f68c2-126">Step 2: Define the data contract</span></span>  
 <span data-ttu-id="f68c2-127">Następnie należy utworzyć umowę danych dla usługi, która opisze, jak dane będą wymieniane między usługą i jej klientami.</span><span class="sxs-lookup"><span data-stu-id="f68c2-127">Next you should create a data contract for the service, which will describe how the data will be exchanged between the service and its clients.</span></span>  <span data-ttu-id="f68c2-128">Klasy opisane w umowie danych powinny być<xref:System.Runtime.Serialization.DataContractAttribute>oznaczone atrybutem [ ].</span><span class="sxs-lookup"><span data-stu-id="f68c2-128">Classes described in the data contract should be marked with the [<xref:System.Runtime.Serialization.DataContractAttribute>] attribute.</span></span> <span data-ttu-id="f68c2-129">Poszczególne właściwości lub pola, które mają być widoczne zarówno dla<xref:System.Runtime.Serialization.DataMemberAttribute>klienta, jak i dla serwera, powinny być oznaczone atrybutem [ ].</span><span class="sxs-lookup"><span data-stu-id="f68c2-129">The individual properties or fields you want visible to both client and server should be marked with the [<xref:System.Runtime.Serialization.DataMemberAttribute>] attribute.</span></span> <span data-ttu-id="f68c2-130">Jeśli chcesz, aby typy pochodzące z klasy w umowie danych były<xref:System.Runtime.Serialization.KnownTypeAttribute>dozwolone, należy je zidentyfikować za pomocą atrybutu [ ].</span><span class="sxs-lookup"><span data-stu-id="f68c2-130">If you want types derived from a class in the data contract to be allowed, you must identify them with the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute.</span></span> <span data-ttu-id="f68c2-131">WCF będzie tylko serializacji lub deserializacji typów w interfejsie usługi i typów identyfikowanych jako znane typy.</span><span class="sxs-lookup"><span data-stu-id="f68c2-131">WCF will only serialize or deserialize types in the service interface and types identified as known types.</span></span> <span data-ttu-id="f68c2-132">Jeśli spróbujesz użyć typu, który nie jest znanym typem, wystąpi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f68c2-132">If you attempt to use a type that is not a known type, an exception will occur.</span></span>  
  
 <span data-ttu-id="f68c2-133">Aby uzyskać więcej informacji na temat kontraktów danych, zobacz [Kontrakty danych](../wcf/samples/data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="f68c2-133">For more information about data contracts, see [Data Contracts](../wcf/samples/data-contracts.md).</span></span>  
  
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
  
### <a name="step-3-implement-the-wcf-service"></a><span data-ttu-id="f68c2-134">Krok 3: Zaimplementowanie usługi WCF</span><span class="sxs-lookup"><span data-stu-id="f68c2-134">Step 3: Implement the WCF service</span></span>  
 <span data-ttu-id="f68c2-135">Następnie należy zaimplementować klasę usługi WCF, która implementuje interfejs zdefiniowany w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="f68c2-135">Next, you should implement the WCF service class that implements the interface you defined in the previous step.</span></span>  
  
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
  
### <a name="step-4-configure-the-service-and-the-client"></a><span data-ttu-id="f68c2-136">Krok 4: Konfigurowanie usługi i klienta</span><span class="sxs-lookup"><span data-stu-id="f68c2-136">Step 4: Configure the service and the client</span></span>  
 <span data-ttu-id="f68c2-137">Aby uruchomić usługę WCF, należy zadeklarować punkt końcowy, który udostępnia tego interfejsu usługi przy określonym adresie URL przy użyciu określonego powiązania WCF.</span><span class="sxs-lookup"><span data-stu-id="f68c2-137">To run a WCF service, you need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="f68c2-138">Powiązanie określa szczegóły transportu, kodowania i protokołu dla klientów i serwera do komunikowania się.</span><span class="sxs-lookup"><span data-stu-id="f68c2-138">A binding specifies the transport, encoding and protocol details for the clients and server to communicate.</span></span> <span data-ttu-id="f68c2-139">Zazwyczaj dodajesz powiązania do pliku konfiguracyjnego projektu usługi (web.config).</span><span class="sxs-lookup"><span data-stu-id="f68c2-139">You typically add bindings to the service project’s configuration file (web.config).</span></span> <span data-ttu-id="f68c2-140">Poniżej przedstawiono wpis powiązania dla przykładowej usługi:</span><span class="sxs-lookup"><span data-stu-id="f68c2-140">The following shows a binding entry for the example service:</span></span>  
  
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
  
 <span data-ttu-id="f68c2-141">Następnie należy skonfigurować klienta, aby dopasować informacje wiązania określone przez usługę.</span><span class="sxs-lookup"><span data-stu-id="f68c2-141">Next, you need to configure the client to match the binding information specified by the service.</span></span> <span data-ttu-id="f68c2-142">Aby to zrobić, dodaj następujące elementy do pliku konfiguracji aplikacji klienta (app.config).</span><span class="sxs-lookup"><span data-stu-id="f68c2-142">To do so, add the following to the client’s application configuration (app.config) file.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="customermanager"
                address="http://localhost:8083/CustomerManager"
                binding="basicHttpBinding"
                contract="Shared.ICustomerManager"/>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="step-5-run-the-service"></a><span data-ttu-id="f68c2-143">Krok 5: Uruchom usługę</span><span class="sxs-lookup"><span data-stu-id="f68c2-143">Step 5: Run the service</span></span>  
 <span data-ttu-id="f68c2-144">Na koniec można samodzielnie hostować go w aplikacji konsoli, dodając następujące wiersze do aplikacji usługi i uruchamiając aplikację.</span><span class="sxs-lookup"><span data-stu-id="f68c2-144">Finally, you can self-host it in a console application by adding the following lines to the service app, and starting the app.</span></span> <span data-ttu-id="f68c2-145">Aby uzyskać więcej informacji na temat innych sposobów hostowania aplikacji usługi WCF, [Hosting Services](../wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="f68c2-145">For more information about other ways to host a WCF service application, [Hosting Services](../wcf/hosting-services.md).</span></span>  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a><span data-ttu-id="f68c2-146">Krok 6: Wywołanie usługi z klienta</span><span class="sxs-lookup"><span data-stu-id="f68c2-146">Step 6: Call the service from the client</span></span>  
 <span data-ttu-id="f68c2-147">Aby wywołać usługę z klienta, należy utworzyć fabrykę kanałów dla usługi i zażądać kanału, `GetCustomer` który umożliwi bezpośrednie wywołanie metody bezpośrednio od klienta.</span><span class="sxs-lookup"><span data-stu-id="f68c2-147">To call the service from the client, you need to create a channel factory for the service, and request a channel, which will enable you to directly call the `GetCustomer` method directly from the client.</span></span> <span data-ttu-id="f68c2-148">Kanał implementuje interfejs usługi i obsługuje podstawowej logiki żądania/odpowiedzi dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="f68c2-148">The channel implements the service’s interface and handles the underlying request/reply logic for you.</span></span>  <span data-ttu-id="f68c2-149">Zwracana wartość z tego wywołania metody jest deserializowane kopię odpowiedzi usługi.</span><span class="sxs-lookup"><span data-stu-id="f68c2-149">The return value from that method call is the deserialized copy of the service response.</span></span>  
  
```csharp  
ChannelFactory<ICustomerManager> factory =
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a><span data-ttu-id="f68c2-150">Klient wysyła obiekt według wartości do serwera</span><span class="sxs-lookup"><span data-stu-id="f68c2-150">The client sends a by-value object to the server</span></span>  
 <span data-ttu-id="f68c2-151">W tym scenariuszu klient wysyła obiekt do serwera, wartość według wartości.</span><span class="sxs-lookup"><span data-stu-id="f68c2-151">In this scenario, the client sends an object to the server, by-value.</span></span> <span data-ttu-id="f68c2-152">Oznacza to, że serwer otrzyma deserialiętowaną kopię obiektu.</span><span class="sxs-lookup"><span data-stu-id="f68c2-152">This means that the server will receive a deserialized copy of the object.</span></span>  <span data-ttu-id="f68c2-153">Serwer może wywołać metody na tej kopii i mieć gwarancję, że nie ma wywołania zwrotnego do kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="f68c2-153">The server can call methods on that copy and be guaranteed there is no callback into client code.</span></span> <span data-ttu-id="f68c2-154">Jak wspomniano wcześniej, normalna wymiana danych WCF jest wartością według wartości.</span><span class="sxs-lookup"><span data-stu-id="f68c2-154">As mentioned previously, normal WCF exchanges of data are by-value.</span></span>  <span data-ttu-id="f68c2-155">Gwarantuje to, że wywoływanie metod na jednym z tych obiektów jest wykonywane tylko lokalnie — nie będzie wywoływać kodu na kliencie.</span><span class="sxs-lookup"><span data-stu-id="f68c2-155">This guarantees that calling methods on one of these objects executes locally only – it will not invoke code on the client.</span></span>  
  
 <span data-ttu-id="f68c2-156">W tym scenariuszu przedstawiono następujące wywołanie metody COM:</span><span class="sxs-lookup"><span data-stu-id="f68c2-156">This scenario represents the following COM method call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 <span data-ttu-id="f68c2-157">W tym scenariuszu używa tego samego interfejsu usługi i umowy danych, jak pokazano w pierwszym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f68c2-157">This scenario uses the same service interface and data contract as shown in the first example.</span></span> <span data-ttu-id="f68c2-158">Ponadto klient i usługa zostaną skonfigurowane w ten sam sposób.</span><span class="sxs-lookup"><span data-stu-id="f68c2-158">In addition, the client and service will be configured in the same way.</span></span> <span data-ttu-id="f68c2-159">W tym przykładzie tworzony jest kanał, aby wysłać obiekt i uruchomić w ten sam sposób.</span><span class="sxs-lookup"><span data-stu-id="f68c2-159">In this example, a channel is created to send the object and run the same way.</span></span> <span data-ttu-id="f68c2-160">Jednak w tym przykładzie utworzysz klienta, który wywołuje usługę, przekazując obiekt według wartości.</span><span class="sxs-lookup"><span data-stu-id="f68c2-160">However, for this example, you will create a client that calls the service, passing an object by-value.</span></span> <span data-ttu-id="f68c2-161">Metoda usługi, która klient wywoła w umowie serwisowej, jest pogrubiona:</span><span class="sxs-lookup"><span data-stu-id="f68c2-161">The service method the client will call in the service contract is shown in bold:</span></span>  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a><span data-ttu-id="f68c2-162">Dodaj kod do klienta, który wysyła obiekt według wartości</span><span class="sxs-lookup"><span data-stu-id="f68c2-162">Add code to the client that sends a by-value object</span></span>  
 <span data-ttu-id="f68c2-163">Poniższy kod pokazuje, jak klient tworzy nowy obiekt klienta według wartości, tworzy kanał do komunikowania się z usługą `ICustomerManager` i wysyła do niego obiekt klienta.</span><span class="sxs-lookup"><span data-stu-id="f68c2-163">The following code shows how the client creates a new by-value customer object, creates a channel to communicate with the `ICustomerManager` service, and sends the customer object to it.</span></span>  
  
 <span data-ttu-id="f68c2-164">Obiekt klienta zostanie szeregizowany i wysłany do usługi, gdzie jest deserializowany przez usługę do nowej kopii tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f68c2-164">The customer object will be serialized, and sent to the service, where it is deserialized by the service into a new copy of that object.</span></span>  <span data-ttu-id="f68c2-165">Wszystkie metody, które usługa wywołuje na ten obiekt będzie wykonywany tylko lokalnie na serwerze.</span><span class="sxs-lookup"><span data-stu-id="f68c2-165">Any methods the service calls on this object will execute only locally on the server.</span></span> <span data-ttu-id="f68c2-166">Należy pamiętać, że ten kod ilustruje wysyłanie`PremiumCustomer`typu pochodnego ( ).</span><span class="sxs-lookup"><span data-stu-id="f68c2-166">It’s important to note that this code illustrates sending a derived type (`PremiumCustomer`).</span></span>  <span data-ttu-id="f68c2-167">Umowa serwisowa oczekuje `Customer` obiektu, ale umowa danych usługi<xref:System.Runtime.Serialization.KnownTypeAttribute>używa atrybutu `PremiumCustomer` [ ] do wskazania, że jest również dozwolone.</span><span class="sxs-lookup"><span data-stu-id="f68c2-167">The service contract expects a `Customer` object, but the service data contract uses the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute to indicate that `PremiumCustomer` is also allowed.</span></span>  <span data-ttu-id="f68c2-168">WCF zakończy się niepowodzeniem próby serializacji lub deserializacji dowolnego innego typu za pośrednictwem tego interfejsu usługi.</span><span class="sxs-lookup"><span data-stu-id="f68c2-168">WCF will fail attempts to serialize or deserialize any other type via this service interface.</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-reference"></a><span data-ttu-id="f68c2-169">Usługa zwraca obiekt przez odwołanie</span><span class="sxs-lookup"><span data-stu-id="f68c2-169">The service returns an object by reference</span></span>  
 <span data-ttu-id="f68c2-170">W tym scenariuszu aplikacja kliencka wywołuje usługę zdalną, a metoda zwraca obiekt, który jest przekazywany przez odwołanie z usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="f68c2-170">For this scenario, the client app makes a call to the remote service and the method returns an object, which is passed by reference from the service to the client.</span></span>  
  
 <span data-ttu-id="f68c2-171">Jak wspomniano wcześniej, usługi WCF zawsze zwracają obiekt według wartości.</span><span class="sxs-lookup"><span data-stu-id="f68c2-171">As mentioned previously, WCF services always return object by value.</span></span>  <span data-ttu-id="f68c2-172">Jednak można osiągnąć podobny wynik przy <xref:System.ServiceModel.EndpointAddress10> użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="f68c2-172">However, you can achieve a similar result by using the <xref:System.ServiceModel.EndpointAddress10> class.</span></span>  <span data-ttu-id="f68c2-173">Jest <xref:System.ServiceModel.EndpointAddress10> serializable przez wartość obiektu, który może być używany przez klienta do uzyskania sessionful przez obiekt odwołania na serwerze.</span><span class="sxs-lookup"><span data-stu-id="f68c2-173">The <xref:System.ServiceModel.EndpointAddress10> is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span>  
  
 <span data-ttu-id="f68c2-174">Zachowanie obiektu według odwołania w WCF pokazane w tym scenariuszu różni się od DCOM.</span><span class="sxs-lookup"><span data-stu-id="f68c2-174">The behavior of the by-reference object in WCF shown in this scenario is different than DCOM.</span></span>  <span data-ttu-id="f68c2-175">W DCOM serwer może zwrócić obiekt odwołania bezpośrednio do klienta, a klient może wywołać metody tego obiektu, które są wykonywane na serwerze.</span><span class="sxs-lookup"><span data-stu-id="f68c2-175">In DCOM, the server can return a by-reference object to the client directly, and the client can call that object’s methods, which execute on the server.</span></span>  <span data-ttu-id="f68c2-176">W WCF, jednak obiekt zwracany jest zawsze wartość według wartości.</span><span class="sxs-lookup"><span data-stu-id="f68c2-176">In WCF, however, the object returned is always by-value.</span></span>  <span data-ttu-id="f68c2-177">Klient musi podjąć, że obiekt według <xref:System.ServiceModel.EndpointAddress10> wartości, reprezentowane przez i używać go do tworzenia własnych sessionful obiektu przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f68c2-177">The client must take that by-value object, represented by <xref:System.ServiceModel.EndpointAddress10> and use it to create its own sessionful by-reference object.</span></span>  <span data-ttu-id="f68c2-178">Metoda klienta wywołuje obiekt sesji wykonywane na serwerze. Innymi słowy ten obiekt według odwołania w WCF jest normalną usługą WCF, która jest skonfigurowana do sesji.</span><span class="sxs-lookup"><span data-stu-id="f68c2-178">The client method calls on the sessionful object execute on the server.In other words, this by-reference object in WCF is a normal WCF service that is configured to be sessionful.</span></span>  
  
 <span data-ttu-id="f68c2-179">W WCF sesji jest sposobem korelowania wielu komunikatów wysyłanych między dwoma punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="f68c2-179">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span>  <span data-ttu-id="f68c2-180">Oznacza to, że gdy klient uzyskuje połączenie z tą usługą, zostanie ustanowiona sesja między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="f68c2-180">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span>  <span data-ttu-id="f68c2-181">Klient użyje pojedynczego unikatowego wystąpienia obiektu po stronie serwera dla wszystkich jego interakcji w ramach tej pojedynczej sesji.</span><span class="sxs-lookup"><span data-stu-id="f68c2-181">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span> <span data-ttu-id="f68c2-182">Umowy WCF sessionful są podobne do wzorców żądania/odpowiedzi sieci zorientowanych na połączenie.</span><span class="sxs-lookup"><span data-stu-id="f68c2-182">Sessionful WCF contracts are similar to connection-oriented network request/response patterns.</span></span>  
  
 <span data-ttu-id="f68c2-183">Ten scenariusz jest reprezentowany przez następującą metodę DCOM.</span><span class="sxs-lookup"><span data-stu-id="f68c2-183">This scenario is represented by the following DCOM method.</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a><span data-ttu-id="f68c2-184">Krok 1: Zdefiniuj interfejs i implementację usługi Sessionful WCF</span><span class="sxs-lookup"><span data-stu-id="f68c2-184">Step 1: Define the Sessionful WCF service interface and implementation</span></span>  
 <span data-ttu-id="f68c2-185">Najpierw zdefiniuj interfejs usługi WCF, który zawiera obiekt sessionful.</span><span class="sxs-lookup"><span data-stu-id="f68c2-185">First, define a WCF service interface that contains the sessionful object.</span></span>  
  
 <span data-ttu-id="f68c2-186">W tym kodzie sessionful obiekt `ServiceContract` jest oznaczony atrybutem, który identyfikuje go jako zwykły interfejs usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="f68c2-186">In this code, the sessionful object is marked with the `ServiceContract` attribute, which identifies it as a regular WCF service interface.</span></span>  <span data-ttu-id="f68c2-187">Ponadto właściwość <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> jest ustawiona, aby wskazać, że będzie to usługa sesyjna.</span><span class="sxs-lookup"><span data-stu-id="f68c2-187">In addition, the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> property is set to indicate it will be a sessionful service.</span></span>  
  
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
  
 <span data-ttu-id="f68c2-188">Poniższy kod przedstawia implementację usługi.</span><span class="sxs-lookup"><span data-stu-id="f68c2-188">The following code shows the service implementation.</span></span>  
  
 <span data-ttu-id="f68c2-189">Usługa jest oznaczona atrybutem [ServiceBehavior], a jego właściwość InstanceContextMode ustawiona na InstanceContextMode.PerSessions wskazuje, że dla każdej sesji powinno zostać utworzone unikatowe wystąpienie tego typu.</span><span class="sxs-lookup"><span data-stu-id="f68c2-189">The service is marked with the [ServiceBehavior] attribute, and its InstanceContextMode property set to InstanceContextMode.PerSessions to indicate that a unique instance of this type should be created for each session.</span></span>  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a><span data-ttu-id="f68c2-190">Krok 2: Zdefiniuj usługę fabryczną WCF dla obiektu sesyjnego</span><span class="sxs-lookup"><span data-stu-id="f68c2-190">Step 2: Define the WCF factory service for the sessionful object</span></span>  
 <span data-ttu-id="f68c2-191">Usługa, która tworzy obiekt sessionful musi być zdefiniowane i zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="f68c2-191">The service that creates the sessionful object must be defined and implemented.</span></span> <span data-ttu-id="f68c2-192">Poniższy kod pokazuje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="f68c2-192">The following code shows how to do this.</span></span> <span data-ttu-id="f68c2-193">Ten kod tworzy inną usługę WCF, która zwraca obiekt. <xref:System.ServiceModel.EndpointAddress10></span><span class="sxs-lookup"><span data-stu-id="f68c2-193">This code creates another WCF service that returns an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  <span data-ttu-id="f68c2-194">Jest to serializable formie punktu końcowego można użyć do utworzenia obiektu pełnej sesji.</span><span class="sxs-lookup"><span data-stu-id="f68c2-194">This is a serializable form of an endpoint the can use to create the session-full object.</span></span>  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 <span data-ttu-id="f68c2-195">Poniżej przedstawiono implementację tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f68c2-195">The following is the implementation of this service.</span></span> <span data-ttu-id="f68c2-196">Ta implementacja utrzymuje fabrykę pojedynczego kanału do tworzenia obiektów sesji.</span><span class="sxs-lookup"><span data-stu-id="f68c2-196">This implementation maintains a singleton channel factory to create sessionful objects.</span></span>  <span data-ttu-id="f68c2-197">Po `GetInstanceAddress` wywołaniu tworzy kanał i <xref:System.ServiceModel.EndpointAddress10> tworzy obiekt, który wskazuje adres zdalny skojarzony z tym kanałem.</span><span class="sxs-lookup"><span data-stu-id="f68c2-197">When `GetInstanceAddress` is called, it creates a channel and creates an <xref:System.ServiceModel.EndpointAddress10> object that points to the remote address associated with this channel.</span></span>   <span data-ttu-id="f68c2-198"><xref:System.ServiceModel.EndpointAddress10>jest typem danych, który może być zwracany do wartości klienta według wartości.</span><span class="sxs-lookup"><span data-stu-id="f68c2-198"><xref:System.ServiceModel.EndpointAddress10> is a data type that can be returned to the client by-value.</span></span>
  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a><span data-ttu-id="f68c2-199">Krok 3: Konfigurowanie i uruchamianie usług WCF</span><span class="sxs-lookup"><span data-stu-id="f68c2-199">Step 3: Configure and start the WCF services</span></span>  
 <span data-ttu-id="f68c2-200">Aby obsługiwać te usługi, należy wprowadzić następujące dodatki do pliku konfiguracyjnego serwera (web.config).</span><span class="sxs-lookup"><span data-stu-id="f68c2-200">To host these services, you will need to make the following additions to the server’s configuration file (web.config).</span></span>  
  
1. <span data-ttu-id="f68c2-201">Dodaj `<client>` sekcję opisującą punkt końcowy dla obiektu sesji.</span><span class="sxs-lookup"><span data-stu-id="f68c2-201">Add a `<client>` section that describes the endpoint for the sessionful object.</span></span>  <span data-ttu-id="f68c2-202">W tym scenariuszu serwer działa również jako klient i musi być skonfigurowany, aby to włączyć.</span><span class="sxs-lookup"><span data-stu-id="f68c2-202">In this scenario, the server also acts as a client and must be configured to enable this.</span></span>  
  
2. <span data-ttu-id="f68c2-203">W `<services>` sekcji zadeklarować punkty końcowe usługi dla obiektu fabrycznego i sessionful.</span><span class="sxs-lookup"><span data-stu-id="f68c2-203">In the `<services>` section, declare service endpoints for the factory and sessionful object.</span></span>  <span data-ttu-id="f68c2-204">Dzięki temu klient do komunikowania się z <xref:System.ServiceModel.EndpointAddress10> punktami końcowymi usługi, uzyskać i utworzyć kanał sessionful.</span><span class="sxs-lookup"><span data-stu-id="f68c2-204">This enables the client to communicate with the service endpoints, acquire the <xref:System.ServiceModel.EndpointAddress10> and create the sessionful channel.</span></span>  
  
 <span data-ttu-id="f68c2-205">Poniżej przedstawiono przykładowy plik konfiguracyjny z następującymi ustawieniami:</span><span class="sxs-lookup"><span data-stu-id="f68c2-205">The following is an example configuration file with these settings:</span></span>  
  
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
  
 <span data-ttu-id="f68c2-206">Dodaj następujące wiersze do aplikacji konsoli, aby samodzielnie hostować usługę i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="f68c2-206">Add the following lines to a console application, to self-host the service, and start the app.</span></span>  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a><span data-ttu-id="f68c2-207">Krok 4: Skonfiguruj klienta i zadzwoń do usługi</span><span class="sxs-lookup"><span data-stu-id="f68c2-207">Step 4: Configure the client and call the service</span></span>  
 <span data-ttu-id="f68c2-208">Skonfiguruj klienta do komunikowania się z usługami WCF, wykonując następujące wpisy w pliku konfiguracji aplikacji projektu (app.config).</span><span class="sxs-lookup"><span data-stu-id="f68c2-208">Configure the client to communicate with the WCF services by making the following entries in the project’s application configuration file (app.config).</span></span>  
  
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
  
 <span data-ttu-id="f68c2-209">Aby wywołać usługę, dodaj kod do klienta, aby wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f68c2-209">To call the service, add the code to the client to do the following:</span></span>  
  
1. <span data-ttu-id="f68c2-210">Utwórz kanał `ISessionBoundFactory` do usługi.</span><span class="sxs-lookup"><span data-stu-id="f68c2-210">Create a channel to the `ISessionBoundFactory` service.</span></span>  
  
2. <span data-ttu-id="f68c2-211">Użyj kanału do wywołania `ISessionBoundFactory` usługi <xref:System.ServiceModel.EndpointAddress10> uzyskać obiekt.</span><span class="sxs-lookup"><span data-stu-id="f68c2-211">Use the channel to invoke the `ISessionBoundFactory` service an obtain an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  
  
3. <span data-ttu-id="f68c2-212">Użyj, <xref:System.ServiceModel.EndpointAddress10> aby utworzyć kanał, aby uzyskać obiekt sesji.</span><span class="sxs-lookup"><span data-stu-id="f68c2-212">Use the <xref:System.ServiceModel.EndpointAddress10> to create a channel to obtain a sessionful object.</span></span>  
  
4. <span data-ttu-id="f68c2-213">Wywołanie `SetCurrentValue` `GetCurrentValue` i metody, aby zademonstrować, że pozostaje to samo wystąpienie obiektu jest używany w wielu wywołań.</span><span class="sxs-lookup"><span data-stu-id="f68c2-213">Call the `SetCurrentValue` and `GetCurrentValue` methods to demonstrate it remains the same object instance is used across multiple calls.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f68c2-214">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f68c2-214">See also</span></span>

- [<span data-ttu-id="f68c2-215">Podstawy programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="f68c2-215">Basic WCF Programming</span></span>](../wcf/basic-wcf-programming.md)
- [<span data-ttu-id="f68c2-216">Projektowanie i implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="f68c2-216">Designing and Implementing Services</span></span>](../wcf/designing-and-implementing-services.md)
- [<span data-ttu-id="f68c2-217">Kompilowanie klientów</span><span class="sxs-lookup"><span data-stu-id="f68c2-217">Building Clients</span></span>](../wcf/building-clients.md)
- [<span data-ttu-id="f68c2-218">Usługi dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="f68c2-218">Duplex Services</span></span>](../wcf/feature-details/duplex-services.md)
