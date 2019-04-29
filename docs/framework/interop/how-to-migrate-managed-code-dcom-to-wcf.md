---
title: 'Instrukcje: Migrowanie zarządzanego kodu DCOM do WCF'
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74acea566e4b0e407e86cb67d3f521f18c2d68af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643065"
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a><span data-ttu-id="c5483-102">Instrukcje: Migrowanie zarządzanego kodu DCOM do WCF</span><span class="sxs-lookup"><span data-stu-id="c5483-102">How to: Migrate Managed-Code DCOM to WCF</span></span>
<span data-ttu-id="c5483-103">Windows Communication Foundation (WCF) jest rozwiązaniem zalecane i bezpieczne za pośrednictwem rozproszonych Component Object Model (DCOM) dla kodu zarządzanego wywołań między serwerami i klientami w środowisku rozproszonym.</span><span class="sxs-lookup"><span data-stu-id="c5483-103">Windows Communication Foundation (WCF) is the recommended and secure choice over Distributed Component Object Model (DCOM) for managed code calls between servers and clients in a distributed environment.</span></span> <span data-ttu-id="c5483-104">W tym artykule pokazano, jak można przeprowadzić migrację kodu z modelu DCOM do WCF w następujących scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="c5483-104">This article shows how you to migrate code from DCOM to WCF for the following scenarios.</span></span>  
  
- <span data-ttu-id="c5483-105">Usługa zdalna zwraca obiekt przez wartość do klienta</span><span class="sxs-lookup"><span data-stu-id="c5483-105">The remote service returns an object by-value to the client</span></span>  
  
- <span data-ttu-id="c5483-106">Klient wysyła przez wartość obiektu do usługi zdalnej</span><span class="sxs-lookup"><span data-stu-id="c5483-106">The client sends an object by-value to the remote service</span></span>  
  
- <span data-ttu-id="c5483-107">Usługa zdalna zwraca obiekt przez odwołanie do klienta</span><span class="sxs-lookup"><span data-stu-id="c5483-107">The remote service returns an object by-reference to the client</span></span>  
  
 <span data-ttu-id="c5483-108">Ze względów bezpieczeństwa wysyłanie przez — odwołanie do obiektu z klienta do usługi jest niedozwolone w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="c5483-108">For security reasons, sending an object by-reference from the client to the service is not allowed in WCF.</span></span> <span data-ttu-id="c5483-109">Scenariusz, który wymaga konwersacji i z powrotem między klientem i serwerem można osiągnąć programu WCF za pomocą usługi duplex.</span><span class="sxs-lookup"><span data-stu-id="c5483-109">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span>  <span data-ttu-id="c5483-110">Aby uzyskać więcej informacji na temat usługi dwukierunkowe, zobacz [usługi dwukierunkowe](../../../docs/framework/wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="c5483-110">For more information about duplex services, see [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="c5483-111">Aby uzyskać więcej informacji na temat tworzenia usług WCF i klientów dla tych usług, zobacz [programowanie WCF Basic](../../../docs/framework/wcf/basic-wcf-programming.md), [projektowanie i Implementowanie usług](../../../docs/framework/wcf/designing-and-implementing-services.md), i [kompilowanie klientów](../../../docs/framework/wcf/building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="c5483-111">For more details about creating WCF services and clients for those services, see [Basic WCF Programming](../../../docs/framework/wcf/basic-wcf-programming.md), [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md), and [Building Clients](../../../docs/framework/wcf/building-clients.md).</span></span>  
  
## <a name="dcom-example-code"></a><span data-ttu-id="c5483-112">DCOM przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="c5483-112">DCOM example code</span></span>  
 <span data-ttu-id="c5483-113">W tych scenariuszach interfejsów modelu DCOM, które zostały przedstawione przy użyciu usługi WCF mają następującą strukturę:</span><span class="sxs-lookup"><span data-stu-id="c5483-113">For these scenarios, the DCOM interfaces that are illustrated using WCF have the following structure:</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-value"></a><span data-ttu-id="c5483-114">Usługa zwraca obiekt przez wartość</span><span class="sxs-lookup"><span data-stu-id="c5483-114">The service returns an object by-value</span></span>  
 <span data-ttu-id="c5483-115">W tym scenariuszu było wywołanie usługi i jej metoda zwraca obiekt, który jest przekazywany przez wartość z serwera do klienta.</span><span class="sxs-lookup"><span data-stu-id="c5483-115">For this scenario, you make a call to a service and it method returns an object, which is passed by-value from the server to the client.</span></span> <span data-ttu-id="c5483-116">Ten scenariusz przedstawia następujące wywołania modelu COM:</span><span class="sxs-lookup"><span data-stu-id="c5483-116">This scenario represents the following COM call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 <span data-ttu-id="c5483-117">W tym scenariuszu klient otrzymuje kopię po deserializacji obiektu ze zdalnej usługi.</span><span class="sxs-lookup"><span data-stu-id="c5483-117">In this scenario, the client receives a deserialized copy of an object from the remote service.</span></span> <span data-ttu-id="c5483-118">Klient może interakcyjnie przeprowadzić ta lokalna kopia bez wywołań zwrotnych do usługi.</span><span class="sxs-lookup"><span data-stu-id="c5483-118">The client can interact with this local copy without calling back to the service.</span></span>  <span data-ttu-id="c5483-119">Innymi słowy klient ma żadnej gwarancji, że usługa nie będzie angażowany w jakikolwiek sposób, po wywołaniu metod w lokalnej kopii.</span><span class="sxs-lookup"><span data-stu-id="c5483-119">In other words, the client is guaranteed the service will not be involved in any way when methods on the local copy are called.</span></span> <span data-ttu-id="c5483-120">Usługi WCF zawsze zwraca obiekty z usługi według wartości, więc w poniższych krokach opisano tworzenie usługi WCF regularne.</span><span class="sxs-lookup"><span data-stu-id="c5483-120">WCF always returns objects from the service by value, so the following steps describe creating a regular WCF service.</span></span>  
  
### <a name="step-1-define-the-wcf-service-interface"></a><span data-ttu-id="c5483-121">Krok 1. Zdefiniuj interfejs usługi WCF</span><span class="sxs-lookup"><span data-stu-id="c5483-121">Step 1: Define the WCF service interface</span></span>  
 <span data-ttu-id="c5483-122">Zdefiniuj interfejs publiczny dla usługi WCF i oznacz go za pomocą [<xref:System.ServiceModel.ServiceContractAttribute>] atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c5483-122">Define a public interface for the WCF service and mark it with the [<xref:System.ServiceModel.ServiceContractAttribute>] attribute.</span></span>  <span data-ttu-id="c5483-123">Oznacz metody ma zostać uwidoczniona dla klientów z [<xref:System.ServiceModel.OperationContractAttribute>] atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c5483-123">Mark the methods you want to expose to clients with the [<xref:System.ServiceModel.OperationContractAttribute>] attribute.</span></span> <span data-ttu-id="c5483-124">Poniższy przykład pokazuje, przy użyciu tych atrybutów do identyfikowania interfejsu po stronie serwera i klienta można wywoływać metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c5483-124">The following example shows using these attributes to identify the server-side interface and interface methods a client can call.</span></span> <span data-ttu-id="c5483-125">Metody używane w tym scenariuszu jest wyświetlany czcionką pogrubioną.</span><span class="sxs-lookup"><span data-stu-id="c5483-125">The method used for this scenario is shown in bold.</span></span>  
  
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
  
### <a name="step-2-define-the-data-contract"></a><span data-ttu-id="c5483-126">Krok 2. Definiowanie kontraktu danych</span><span class="sxs-lookup"><span data-stu-id="c5483-126">Step 2: Define the data contract</span></span>  
 <span data-ttu-id="c5483-127">Następnie należy utworzyć kontraktu danych dla usługi, w której opisano, jak dane będą wymieniane między usługą i jej klientów.</span><span class="sxs-lookup"><span data-stu-id="c5483-127">Next you should create a data contract for the service, which will describe how the data will be exchanged between the service and its clients.</span></span>  <span data-ttu-id="c5483-128">Klasy, które opisano w kontraktu danych powinien być oznaczony przez [<xref:System.Runtime.Serialization.DataContractAttribute>] atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c5483-128">Classes described in the data contract should be marked with the [<xref:System.Runtime.Serialization.DataContractAttribute>] attribute.</span></span> <span data-ttu-id="c5483-129">Indywidualne właściwości lub pól mają być widoczne dla klienta i serwera powinien być oznaczony przez [<xref:System.Runtime.Serialization.DataMemberAttribute>] atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c5483-129">The individual properties or fields you want visible to both client and server should be marked with the [<xref:System.Runtime.Serialization.DataMemberAttribute>] attribute.</span></span> <span data-ttu-id="c5483-130">Jeśli chcesz, aby typy pochodzące z klasy w kontraktu danych, które mają być dozwolone, należy zidentyfikować je za pomocą [<xref:System.Runtime.Serialization.KnownTypeAttribute>] atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c5483-130">If you want types derived from a class in the data contract to be allowed, you must identify them with the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute.</span></span> <span data-ttu-id="c5483-131">Usługi WCF będzie tylko serializacji lub deserializacji, typy w interfejsie usługi i zidentyfikowane jako znanych typów.</span><span class="sxs-lookup"><span data-stu-id="c5483-131">WCF will only serialize or deserialize types in the service interface and types identified as known types.</span></span> <span data-ttu-id="c5483-132">Jeśli spróbujesz użyć typu, który nie jest znany typ, wystąpi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c5483-132">If you attempt to use a type that is not a known type, an exception will occur.</span></span>  
  
 <span data-ttu-id="c5483-133">Aby uzyskać więcej informacji na temat kontraktów danych zobacz [kontraktów danych](../../../docs/framework/wcf/samples/data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="c5483-133">For more information about data contracts, see [Data Contracts](../../../docs/framework/wcf/samples/data-contracts.md).</span></span>  
  
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
  
### <a name="step-3-implement-the-wcf-service"></a><span data-ttu-id="c5483-134">Krok 3. Implementowanie usługi WCF</span><span class="sxs-lookup"><span data-stu-id="c5483-134">Step 3: Implement the WCF service</span></span>  
 <span data-ttu-id="c5483-135">Następnie należy zaimplementować klasę usługi WCF, który implementuje interfejs, który został zdefiniowany w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="c5483-135">Next, you should implement the WCF service class that implements the interface you defined in the previous step.</span></span>  
  
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
  
### <a name="step-4-configure-the-service-and-the-client"></a><span data-ttu-id="c5483-136">Krok 4. Konfigurowanie usługi i klienta</span><span class="sxs-lookup"><span data-stu-id="c5483-136">Step 4: Configure the service and the client</span></span>  
 <span data-ttu-id="c5483-137">Aby uruchomić usługę WCF, należy zadeklarować punktu końcowego uwidocznionego interfejsu usług pod określonym adresem URL używa określonego powiązania WCF.</span><span class="sxs-lookup"><span data-stu-id="c5483-137">To run a WCF service, you need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="c5483-138">Powiązanie określa szczegóły transportu, kodowanie i protokołu dla klientów i serwera, do komunikowania się.</span><span class="sxs-lookup"><span data-stu-id="c5483-138">A binding specifies the transport, encoding and protocol details for the clients and server to communicate.</span></span> <span data-ttu-id="c5483-139">Zazwyczaj dodajesz powiązań do pliku konfiguracyjnego projektu usługi (web.config).</span><span class="sxs-lookup"><span data-stu-id="c5483-139">You typically add bindings to the service project’s configuration file (web.config).</span></span> <span data-ttu-id="c5483-140">Na poniższym obrazie przedstawiono wpis powiązania usługi przykładu:</span><span class="sxs-lookup"><span data-stu-id="c5483-140">The following shows a binding entry for the example service:</span></span>  
  
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
  
 <span data-ttu-id="c5483-141">Następnie należy skonfigurować klienta do dopasowania informacje o powiązaniu, określony przez usługę.</span><span class="sxs-lookup"><span data-stu-id="c5483-141">Next, you need to configure the client to match the binding information specified by the service.</span></span> <span data-ttu-id="c5483-142">Aby to zrobić, Dodaj następujący element do klienta pliku konfiguracji aplikacji (app.config).</span><span class="sxs-lookup"><span data-stu-id="c5483-142">To do so, add the following to the client’s application configuration (app.config) file.</span></span>  
  
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
  
### <a name="step-5-run-the-service"></a><span data-ttu-id="c5483-143">Krok 5. Uruchom usługę</span><span class="sxs-lookup"><span data-stu-id="c5483-143">Step 5: Run the service</span></span>  
 <span data-ttu-id="c5483-144">Na koniec można samodzielnie go umieścić w aplikacji konsoli, dodając następujące wiersze do usługi app Service i uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c5483-144">Finally, you can self-host it in a console application by adding the following lines to the service app, and starting the app.</span></span> <span data-ttu-id="c5483-145">Aby uzyskać więcej informacji na temat innych sposobów hostowania aplikacji usługi WCF [usług obsługującego](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="c5483-145">For more information about other ways to host a WCF service application, [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a><span data-ttu-id="c5483-146">Krok 6. Wywołania usługi przez klienta</span><span class="sxs-lookup"><span data-stu-id="c5483-146">Step 6: Call the service from the client</span></span>  
 <span data-ttu-id="c5483-147">Aby wywołać usługę od klienta, musisz tworzenie fabryki kanałów dla usługi i żądania kanał, który umożliwi bezpośrednio wywołać `GetCustomer` metoda bezpośrednio z klienta.</span><span class="sxs-lookup"><span data-stu-id="c5483-147">To call the service from the client, you need to create a channel factory for the service, and request a channel, which will enable you to directly call the `GetCustomer` method directly from the client.</span></span> <span data-ttu-id="c5483-148">Kanał implementuje interfejs usługi i obsługuje podstawowej logiki żądanie/nietypizowana odpowiedź dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="c5483-148">The channel implements the service’s interface and handles the underlying request/reply logic for you.</span></span>  <span data-ttu-id="c5483-149">Wartość zwrócona przez wywołanie tej metody jest zdeserializowany kopię odpowiedzi usługi.</span><span class="sxs-lookup"><span data-stu-id="c5483-149">The return value from that method call is the deserialized copy of the service response.</span></span>  
  
```csharp  
ChannelFactory<ICustomerManager> factory =   
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a><span data-ttu-id="c5483-150">Klient wysyła obiekt przez wartość do serwera</span><span class="sxs-lookup"><span data-stu-id="c5483-150">The client sends a by-value object to the server</span></span>  
 <span data-ttu-id="c5483-151">W tym scenariuszu klient przesyła dany obiekt z serwerem przez wartość.</span><span class="sxs-lookup"><span data-stu-id="c5483-151">In this scenario, the client sends an object to the server, by-value.</span></span> <span data-ttu-id="c5483-152">Oznacza to, że serwer otrzyma kopię po deserializacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="c5483-152">This means that the server will receive a deserialized copy of the object.</span></span>  <span data-ttu-id="c5483-153">Serwer można wywoływać metody dla tej kopii i zapewniona jest bez wywołania zwrotnego do kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="c5483-153">The server can call methods on that copy and be guaranteed there is no callback into client code.</span></span> <span data-ttu-id="c5483-154">Jak wspomniano wcześniej, normalne WCF wymiany danych są przez wartość.</span><span class="sxs-lookup"><span data-stu-id="c5483-154">As mentioned previously, normal WCF exchanges of data are by-value.</span></span>  <span data-ttu-id="c5483-155">Gwarantuje to, że wywołanie metody w jednej z tych obiektów jest wykonywana lokalnie tylko — nie wywoła kodu na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="c5483-155">This guarantees that calling methods on one of these objects executes locally only – it will not invoke code on the client.</span></span>  
  
 <span data-ttu-id="c5483-156">Ten scenariusz przedstawia następujące wywołanie metody COM:</span><span class="sxs-lookup"><span data-stu-id="c5483-156">This scenario represents the following COM method call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 <span data-ttu-id="c5483-157">W tym scenariuszu ten sam kontrakt interfejsu i danych usługi jak pokazano w pierwszym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c5483-157">This scenario uses the same service interface and data contract as shown in the first example.</span></span> <span data-ttu-id="c5483-158">Ponadto klienta i usługi zostaną skonfigurowane w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="c5483-158">In addition, the client and service will be configured in the same way.</span></span> <span data-ttu-id="c5483-159">W tym przykładzie zostanie utworzona kanał Wyślij obiektu i uruchom ten sam sposób.</span><span class="sxs-lookup"><span data-stu-id="c5483-159">In this example, a channel is created to send the object and run the same way.</span></span> <span data-ttu-id="c5483-160">Jednak w tym przykładzie utworzysz klienta, który wywołuje usługę, przekazując obiekt przez wartość.</span><span class="sxs-lookup"><span data-stu-id="c5483-160">However, for this example, you will create a client that calls the service, passing an object by-value.</span></span> <span data-ttu-id="c5483-161">Metoda usługi, którego klient będzie wywoływać w kontrakcie usługi jest wyświetlany czcionką pogrubioną:</span><span class="sxs-lookup"><span data-stu-id="c5483-161">The service method the client will call in the service contract is shown in bold:</span></span>  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a><span data-ttu-id="c5483-162">Dodaj kod do klienta, który wysyła obiekt według wartości</span><span class="sxs-lookup"><span data-stu-id="c5483-162">Add code to the client that sends a by-value object</span></span>  
 <span data-ttu-id="c5483-163">W poniższym kodzie, jak klient tworzy nowy obiekt klienta przez wartość, tworzy kanał do komunikowania się z `ICustomerManager` usługi, a następnie wysyła obiekt klienta.</span><span class="sxs-lookup"><span data-stu-id="c5483-163">The following code shows how the client creates a new by-value customer object, creates a channel to communicate with the `ICustomerManager` service, and sends the customer object to it.</span></span>  
  
 <span data-ttu-id="c5483-164">Obiekt klienta będą serializowane i wysyłane do usługi, w których jest ona przeprowadzona przez usługę do nowej kopii tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="c5483-164">The customer object will be serialized, and sent to the service, where it is deserialized by the service into a new copy of that object.</span></span>  <span data-ttu-id="c5483-165">Wszystkie metody, które wywołuje usługę, dla tego obiektu zostanie wykonana tylko lokalnie na serwerze.</span><span class="sxs-lookup"><span data-stu-id="c5483-165">Any methods the service calls on this object will execute only locally on the server.</span></span> <span data-ttu-id="c5483-166">Należy pamiętać, że ten kod ilustruje wysyłania typem pochodnym jest (`PremiumCustomer`).</span><span class="sxs-lookup"><span data-stu-id="c5483-166">It’s important to note that this code illustrates sending a derived type (`PremiumCustomer`).</span></span>  <span data-ttu-id="c5483-167">Kontrakt usługi oczekuje `Customer` obiekt, ale dane usługi kontraktu używa [<xref:System.Runtime.Serialization.KnownTypeAttribute>] atrybutu, aby wskazać, że `PremiumCustomer` jest też dozwolony.</span><span class="sxs-lookup"><span data-stu-id="c5483-167">The service contract expects a `Customer` object, but the service data contract uses the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute to indicate that `PremiumCustomer` is also allowed.</span></span>  <span data-ttu-id="c5483-168">Usługi WCF zakończy się niepowodzeniem próby serializacji lub deserializacji dowolny inny typ za pośrednictwem tego interfejsu usługi.</span><span class="sxs-lookup"><span data-stu-id="c5483-168">WCF will fail attempts to serialize or deserialize any other type via this service interface.</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-reference"></a><span data-ttu-id="c5483-169">Usługa zwraca obiekt przez odwołanie</span><span class="sxs-lookup"><span data-stu-id="c5483-169">The service returns an object by reference</span></span>  
 <span data-ttu-id="c5483-170">W tym scenariuszu aplikacja kliencka nawiązuje połączenie usługi zdalnej, a metoda zwraca obiekt, który jest przekazywany przez odwołanie usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="c5483-170">For this scenario, the client app makes a call to the remote service and the method returns an object, which is passed by reference from the service to the client.</span></span>  
  
 <span data-ttu-id="c5483-171">Jak wspomniano wcześniej, usługi WCF zawsze zwracają obiekt przez wartość.</span><span class="sxs-lookup"><span data-stu-id="c5483-171">As mentioned previously, WCF services always return object by value.</span></span>  <span data-ttu-id="c5483-172">Jednak można osiągnąć podobny efekt, za pomocą <xref:System.ServiceModel.EndpointAddress10> klasy.</span><span class="sxs-lookup"><span data-stu-id="c5483-172">However, you can achieve a similar result by using the <xref:System.ServiceModel.EndpointAddress10> class.</span></span>  <span data-ttu-id="c5483-173"><xref:System.ServiceModel.EndpointAddress10> Jest obiektem serializacji przez wartość, która może służyć przez klienta do uzyskiwania obiektu sesji przez odwołanie, na serwerze.</span><span class="sxs-lookup"><span data-stu-id="c5483-173">The <xref:System.ServiceModel.EndpointAddress10> is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span>  
  
 <span data-ttu-id="c5483-174">Zachowanie obiektu przez odwołanie w programie WCF przedstawione w tym scenariuszu jest inny niż model DCOM.</span><span class="sxs-lookup"><span data-stu-id="c5483-174">The behavior of the by-reference object in WCF shown in this scenario is different than DCOM.</span></span>  <span data-ttu-id="c5483-175">W modelu DCOM Serwer może zwrócić obiekt przez odniesienie do klienta bezpośrednio, a klient może wywołać metody tego obiektu, które wykonania na serwerze.</span><span class="sxs-lookup"><span data-stu-id="c5483-175">In DCOM, the server can return a by-reference object to the client directly, and the client can call that object’s methods, which execute on the server.</span></span>  <span data-ttu-id="c5483-176">W programie WCF jednak obiekt zwrócony jest zawsze przez wartość.</span><span class="sxs-lookup"><span data-stu-id="c5483-176">In WCF, however, the object returned is always by-value.</span></span>  <span data-ttu-id="c5483-177">Klient musi podjąć tego obiektu przez wartość, reprezentowane przez <xref:System.ServiceModel.EndpointAddress10> i użyć go do utworzenia własnego obiektu sesji przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="c5483-177">The client must take that by-value object, represented by <xref:System.ServiceModel.EndpointAddress10> and use it to create its own sessionful by-reference object.</span></span>  <span data-ttu-id="c5483-178">Wykonywanie wywołań metod klienta w obiekcie sesji na serwerze. Innymi słowy ten obiekt przez odwołanie w programie WCF jest normalne usługi WCF, który jest skonfigurowany jako sesji.</span><span class="sxs-lookup"><span data-stu-id="c5483-178">The client method calls on the sessionful object execute on the server.In other words, this by-reference object in WCF is a normal WCF service that is configured to be sessionful.</span></span>  
  
 <span data-ttu-id="c5483-179">W programie WCF sesja jest sposób korelacji wielu komunikatów przesyłanych między dwoma punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="c5483-179">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span>  <span data-ttu-id="c5483-180">Oznacza to, że gdy klient uzyskuje połączenie z tą usługą, sesji zostanie nawiązane między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="c5483-180">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span>  <span data-ttu-id="c5483-181">Klient użyje jednego unikatowego wystąpienia obiektu po stronie serwera dla wszystkich jego interakcji w ramach tej jednej sesji.</span><span class="sxs-lookup"><span data-stu-id="c5483-181">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span> <span data-ttu-id="c5483-182">Przekroczono kontraktów WCF są podobne do wzorców żądań/odpowiedzi nawiązaniem połączenia sieciowego.</span><span class="sxs-lookup"><span data-stu-id="c5483-182">Sessionful WCF contracts are similar to connection-oriented network request/response patterns.</span></span>  
  
 <span data-ttu-id="c5483-183">Ten scenariusz jest reprezentowany przez następującą metodę modelu DCOM.</span><span class="sxs-lookup"><span data-stu-id="c5483-183">This scenario is represented by the following DCOM method.</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a><span data-ttu-id="c5483-184">Krok 1. Zdefiniuj interfejs usługi Sessionful WCF i implementacja</span><span class="sxs-lookup"><span data-stu-id="c5483-184">Step 1: Define the Sessionful WCF service interface and implementation</span></span>  
 <span data-ttu-id="c5483-185">Najpierw należy zdefiniować interfejsu usługi WCF, która zawiera obiekt sesji.</span><span class="sxs-lookup"><span data-stu-id="c5483-185">First, define a WCF service interface that contains the sessionful object.</span></span>  
  
 <span data-ttu-id="c5483-186">W tym kodzie obiekt sesji jest oznaczona atrybutem `ServiceContract` atrybut, który identyfikuje ją jako regularnych interface usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="c5483-186">In this code, the sessionful object is marked with the `ServiceContract` attribute, which identifies it as a regular WCF service interface.</span></span>  <span data-ttu-id="c5483-187">Ponadto <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> właściwość jest ustawiona, aby wskazać, będzie on sesji usługi.</span><span class="sxs-lookup"><span data-stu-id="c5483-187">In addition, the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> property is set to indicate it will be a sessionful service.</span></span>  
  
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
  
 <span data-ttu-id="c5483-188">Poniższy kod przedstawia implementację usługi.</span><span class="sxs-lookup"><span data-stu-id="c5483-188">The following code shows the service implementation.</span></span>  
  
 <span data-ttu-id="c5483-189">Usługa jest oznaczona atrybutem [ServiceBehavior], a jego właściwość InstanceContextMode właściwością InstanceContextMode.PerSessions do wskazania, że unikatowego wystąpienia tego typu powinny być tworzone dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="c5483-189">The service is marked with the [ServiceBehavior] attribute, and its InstanceContextMode property set to InstanceContextMode.PerSessions to indicate that a unique instance of this type should be created for each session.</span></span>  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a><span data-ttu-id="c5483-190">Krok 2. Zdefiniuj usługę WCF fabryki dla obiektu sesji</span><span class="sxs-lookup"><span data-stu-id="c5483-190">Step 2: Define the WCF factory service for the sessionful object</span></span>  
 <span data-ttu-id="c5483-191">Usługa, która tworzy obiekt sesji należy zdefiniowane i zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="c5483-191">The service that creates the sessionful object must be defined and implemented.</span></span> <span data-ttu-id="c5483-192">Poniższy kod pokazuje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="c5483-192">The following code shows how to do this.</span></span> <span data-ttu-id="c5483-193">Ten kod tworzy innej usługi WCF, która zwraca <xref:System.ServiceModel.EndpointAddress10> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c5483-193">This code creates another WCF service that returns an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  <span data-ttu-id="c5483-194">Jest to format możliwy do serializacji dla punktu końcowego usługi mogą użyć do utworzenia obiektu sesji pełnej.</span><span class="sxs-lookup"><span data-stu-id="c5483-194">This is a serializable form of an endpoint the can use to create the session-full object.</span></span>  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 <span data-ttu-id="c5483-195">Poniżej przedstawiono implementację tej usługi.</span><span class="sxs-lookup"><span data-stu-id="c5483-195">Following is the implementation of this service.</span></span> <span data-ttu-id="c5483-196">Ta implementacja obsługuje pojedyncze fabryki kanałów, aby utworzyć obiekty sesji.</span><span class="sxs-lookup"><span data-stu-id="c5483-196">This implementation maintains a singleton channel factory to create sessionful objects.</span></span>  <span data-ttu-id="c5483-197">Gdy `GetInstanceAddress` jest wywoływana, tworzy kanał i tworzy <xref:System.ServiceModel.EndpointAddress10> obiektu, który wskazuje na zdalny adres skojarzony z tym kanałem.</span><span class="sxs-lookup"><span data-stu-id="c5483-197">When `GetInstanceAddress` is called, it creates a channel and creates an <xref:System.ServiceModel.EndpointAddress10> object that points to the remote address associated with this channel.</span></span>   <span data-ttu-id="c5483-198"><xref:System.ServiceModel.EndpointAddress10> jest typem danych, które mogą być zwrócone do klienta przez wartość.</span><span class="sxs-lookup"><span data-stu-id="c5483-198"><xref:System.ServiceModel.EndpointAddress10> is a data type that can be returned to the client by-value.</span></span>  
  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a><span data-ttu-id="c5483-199">Krok 3. Konfigurowanie i uruchamianie usług WCF</span><span class="sxs-lookup"><span data-stu-id="c5483-199">Step 3: Configure and start the WCF services</span></span>  
 <span data-ttu-id="c5483-200">Aby zapewnić obsługę tych usług, należy wprowadzić następujące dodatki do pliku konfiguracji serwera (web.config).</span><span class="sxs-lookup"><span data-stu-id="c5483-200">To host these services, you will need to make the following additions to the server’s configuration file (web.config).</span></span>  
  
1. <span data-ttu-id="c5483-201">Dodaj `<client>` sekcja, która opisuje punktu końcowego dla obiektu sesji.</span><span class="sxs-lookup"><span data-stu-id="c5483-201">Add a `<client>` section that describes the endpoint for the sessionful object.</span></span>  <span data-ttu-id="c5483-202">W tym scenariuszu serwer działa jako klient i musi być skonfigurowany, aby włączyć tę opcję.</span><span class="sxs-lookup"><span data-stu-id="c5483-202">In this scenario, the server also acts as a client and must be configured to enable this.</span></span>  
  
2. <span data-ttu-id="c5483-203">W `<services>` sekcji, Zadeklaruj punktów końcowych usługi dla obiektu ustawień fabrycznych i sessionful.</span><span class="sxs-lookup"><span data-stu-id="c5483-203">In the `<services>` section, declare service endpoints for the factory and sessionful object.</span></span>  <span data-ttu-id="c5483-204">Dzięki temu klient do komunikacji z punktami końcowymi usługi, uzyskiwanie <xref:System.ServiceModel.EndpointAddress10> i utworzyć kanału sesji.</span><span class="sxs-lookup"><span data-stu-id="c5483-204">This enables the client to communicate with the service endpoints, acquire the <xref:System.ServiceModel.EndpointAddress10> and create the sessionful channel.</span></span>  
  
 <span data-ttu-id="c5483-205">Poniżej przedstawiono przykładowy plik konfiguracji przy użyciu tych ustawień:</span><span class="sxs-lookup"><span data-stu-id="c5483-205">Following is an example configuration file with these settings:</span></span>  
  
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
  
 <span data-ttu-id="c5483-206">Dodaj następujące wiersze do aplikacji konsoli, na potrzeby samodzielnego hostowania usług i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="c5483-206">Add the following lines to a console application, to self-host the service, and start the app.</span></span>  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a><span data-ttu-id="c5483-207">Krok 4. Konfigurowanie klienta i wywołać usługę</span><span class="sxs-lookup"><span data-stu-id="c5483-207">Step 4: Configure the client and call the service</span></span>  
 <span data-ttu-id="c5483-208">Skonfiguruj klienta do komunikowania się z usługami WCF, wprowadzając następujące wpisy w pliku konfiguracyjnym aplikacji projektu (app.config).</span><span class="sxs-lookup"><span data-stu-id="c5483-208">Configure the client to communicate with the WCF services by making the following entries in the project’s application configuration file (app.config).</span></span>  
  
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
  
 <span data-ttu-id="c5483-209">Aby wywołać usługę, Dodaj kod do klienta, aby wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="c5483-209">To call the service, add the code to the client to do the following:</span></span>  
  
1. <span data-ttu-id="c5483-210">Utwórz kanał `ISessionBoundFactory` usługi.</span><span class="sxs-lookup"><span data-stu-id="c5483-210">Create a channel to the `ISessionBoundFactory` service.</span></span>  
  
2. <span data-ttu-id="c5483-211">Wywoływanie przy użyciu kanału `ISessionBoundFactory` usługi Uzyskaj <xref:System.ServiceModel.EndpointAddress10> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c5483-211">Use the channel to invoke the `ISessionBoundFactory` service an obtain an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  
  
3. <span data-ttu-id="c5483-212">Użyj <xref:System.ServiceModel.EndpointAddress10> próba utworzenia kanału do uzyskiwania obiektu sesji.</span><span class="sxs-lookup"><span data-stu-id="c5483-212">Use the <xref:System.ServiceModel.EndpointAddress10> to create a channel to obtain a sessionful object.</span></span>  
  
4. <span data-ttu-id="c5483-213">Wywołaj `SetCurrentValue` i `GetCurrentValue` używane w wielu wywołań metody, aby zademonstrować, pozostaje on tego samego wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="c5483-213">Call the `SetCurrentValue` and `GetCurrentValue` methods to demonstrate it remains the same object instance is used across multiple calls.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5483-214">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5483-214">See also</span></span>

- [<span data-ttu-id="c5483-215">Podstawy programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="c5483-215">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)
- [<span data-ttu-id="c5483-216">Projektowanie i implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="c5483-216">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)
- [<span data-ttu-id="c5483-217">Kompilowanie klientów</span><span class="sxs-lookup"><span data-stu-id="c5483-217">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)
- [<span data-ttu-id="c5483-218">Usługi dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="c5483-218">Duplex Services</span></span>](../../../docs/framework/wcf/feature-details/duplex-services.md)
