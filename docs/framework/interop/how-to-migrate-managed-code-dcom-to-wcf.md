---
title: 'Instrukcje: migrowanie zarządzanego kodu DCOM do WCF'
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 187bff7c75ba2a0887e3c5728a484a9231936511
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a><span data-ttu-id="22bc5-102">Instrukcje: migrowanie zarządzanego kodu DCOM do WCF</span><span class="sxs-lookup"><span data-stu-id="22bc5-102">How to: Migrate Managed-Code DCOM to WCF</span></span>
<span data-ttu-id="22bc5-103">Windows Communication Foundation (WCF) jest rozwiązaniem zalecanym i bezpieczne za pośrednictwem rozproszonej Component Object Model (DCOM) dla kodu zarządzanego połączeń między serwerami i klientami w środowisku rozproszonym.</span><span class="sxs-lookup"><span data-stu-id="22bc5-103">Windows Communication Foundation (WCF) is the recommended and secure choice over Distributed Component Object Model (DCOM) for managed code calls between servers and clients in a distributed environment.</span></span> <span data-ttu-id="22bc5-104">W tym artykule przedstawiono sposób można migrować kodu z modelu DCOM do WCF w następujących scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="22bc5-104">This article shows how you to migrate code from DCOM to WCF for the following scenarios.</span></span>  
  
-   <span data-ttu-id="22bc5-105">Usługa zdalnego zwraca obiekt przez wartość do klienta</span><span class="sxs-lookup"><span data-stu-id="22bc5-105">The remote service returns an object by-value to the client</span></span>  
  
-   <span data-ttu-id="22bc5-106">Klient wysyła obiektu przez wartość do zdalnej usługi</span><span class="sxs-lookup"><span data-stu-id="22bc5-106">The client sends an object by-value to the remote service</span></span>  
  
-   <span data-ttu-id="22bc5-107">Zdalna usługa zwraca obiekt przez odwołanie do klienta</span><span class="sxs-lookup"><span data-stu-id="22bc5-107">The remote service returns an object by-reference to the client</span></span>  
  
 <span data-ttu-id="22bc5-108">Ze względów bezpieczeństwa wysyłania przez — odwołanie do obiektu z klienta do usługi jest niedozwolone w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="22bc5-108">For security reasons, sending an object by-reference from the client to the service is not allowed in WCF.</span></span> <span data-ttu-id="22bc5-109">Scenariusz, który wymaga konwersacji i z powrotem między klientem i serwerem można osiągnąć w programie WCF, za pomocą usługi duplex.</span><span class="sxs-lookup"><span data-stu-id="22bc5-109">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span>  <span data-ttu-id="22bc5-110">Aby uzyskać więcej informacji na temat usługi dwukierunkowe, zobacz [usługi dwukierunkowe](../../../docs/framework/wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="22bc5-110">For more information about duplex services, see [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="22bc5-111">Aby uzyskać więcej informacji na temat tworzenia usług WCF i klientów dla tych usług, zobacz [podstawowe programowania WCF](../../../docs/framework/wcf/basic-wcf-programming.md), [projektowanie i Implementowanie usług](../../../docs/framework/wcf/designing-and-implementing-services.md), i [kompilowanie klientów](../../../docs/framework/wcf/building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="22bc5-111">For more details about creating WCF services and clients for those services, see [Basic WCF Programming](../../../docs/framework/wcf/basic-wcf-programming.md), [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md), and [Building Clients](../../../docs/framework/wcf/building-clients.md).</span></span>  
  
## <a name="dcom-example-code"></a><span data-ttu-id="22bc5-112">DCOM przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="22bc5-112">DCOM example code</span></span>  
 <span data-ttu-id="22bc5-113">W tych sytuacjach interfejsów modelu DCOM, które zostały przedstawione za pomocą usługi WCF ma następującą strukturę:</span><span class="sxs-lookup"><span data-stu-id="22bc5-113">For these scenarios, the DCOM interfaces that are illustrated using WCF have the following structure:</span></span>  
  
```  
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
  
## <a name="the-service-returns-an-object-by-value"></a><span data-ttu-id="22bc5-114">Usługa zwraca obiekt przez wartość</span><span class="sxs-lookup"><span data-stu-id="22bc5-114">The service returns an object by-value</span></span>  
 <span data-ttu-id="22bc5-115">W tym scenariuszu należy wywołanie usługi, a metoda zwraca obiekt, który jest przekazywany przez wartość z serwera do klienta.</span><span class="sxs-lookup"><span data-stu-id="22bc5-115">For this scenario, you make a call to a service and it method returns an object, which is passed by-value from the server to the client.</span></span> <span data-ttu-id="22bc5-116">Ten scenariusz przedstawia następujące wywołanie COM:</span><span class="sxs-lookup"><span data-stu-id="22bc5-116">This scenario represents the following COM call:</span></span>  
  
```  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 <span data-ttu-id="22bc5-117">W tym scenariuszu klient odbiera kopię zdeserializowany obiekt z usługi zdalnej.</span><span class="sxs-lookup"><span data-stu-id="22bc5-117">In this scenario, the client receives a deserialized copy of an object from the remote service.</span></span> <span data-ttu-id="22bc5-118">Klient może współdziałać z lokalnej kopii bez wywołań zwrotnych do usługi.</span><span class="sxs-lookup"><span data-stu-id="22bc5-118">The client can interact with this local copy without calling back to the service.</span></span>  <span data-ttu-id="22bc5-119">Innymi słowy klienta jest gwarancji, że usługa nie zostanie zaangażowane w dowolny sposób, wywołanego metody kopii.</span><span class="sxs-lookup"><span data-stu-id="22bc5-119">In other words, the client is guaranteed the service will not be involved in any way when methods on the local copy are called.</span></span> <span data-ttu-id="22bc5-120">WCF zawsze zwraca obiekty z usługi wg wartości, więc w poniższych krokach opisano tworzenie regularne usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="22bc5-120">WCF always returns objects from the service by value, so the following steps describe creating a regular WCF service.</span></span>  
  
### <a name="step-1-define-the-wcf-service-interface"></a><span data-ttu-id="22bc5-121">Krok 1: Definiowanie interfejsu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="22bc5-121">Step 1: Define the WCF service interface</span></span>  
 <span data-ttu-id="22bc5-122">Zdefiniuj publiczny interfejs dla usługi WCF i oznacz ją z [<xref:System.ServiceModel.ServiceContractAttribute>] atrybutu.</span><span class="sxs-lookup"><span data-stu-id="22bc5-122">Define a public interface for the WCF service and mark it with the [<xref:System.ServiceModel.ServiceContractAttribute>] attribute.</span></span>  <span data-ttu-id="22bc5-123">Oznacz metody chcesz udostępnić klientom z [<xref:System.ServiceModel.OperationContractAttribute>] atrybutu.</span><span class="sxs-lookup"><span data-stu-id="22bc5-123">Mark the methods you want to expose to clients with the [<xref:System.ServiceModel.OperationContractAttribute>] attribute.</span></span> <span data-ttu-id="22bc5-124">W poniższym przykładzie pokazano, za pomocą tych atrybutów do identyfikowania interfejsu po stronie serwera i klienta można wywoływać metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="22bc5-124">The following example shows using these attributes to identify the server-side interface and interface methods a client can call.</span></span> <span data-ttu-id="22bc5-125">Metody używane w tym scenariuszu są pogrubione.</span><span class="sxs-lookup"><span data-stu-id="22bc5-125">The method used for this scenario is shown in bold.</span></span>  
  
```  
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
  
### <a name="step-2-define-the-data-contract"></a><span data-ttu-id="22bc5-126">Krok 2: Definiowanie kontraktu danych</span><span class="sxs-lookup"><span data-stu-id="22bc5-126">Step 2: Define the data contract</span></span>  
 <span data-ttu-id="22bc5-127">Następnie należy utworzyć kontrakt danych dla usługi, w której opisano, jak dane będą wymieniane między usługą i klientów.</span><span class="sxs-lookup"><span data-stu-id="22bc5-127">Next you should create a data contract for the service, which will describe how the data will be exchanged between the service and its clients.</span></span>  <span data-ttu-id="22bc5-128">Klasy opisane w kontraktu danych powinien być oznaczony przez [<xref:System.Runtime.Serialization.DataContractAttribute>] atrybutu.</span><span class="sxs-lookup"><span data-stu-id="22bc5-128">Classes described in the data contract should be marked with the [<xref:System.Runtime.Serialization.DataContractAttribute>] attribute.</span></span> <span data-ttu-id="22bc5-129">Indywidualne właściwości lub pola mają być widoczne dla klienta i serwera powinien być oznaczony przez [<xref:System.Runtime.Serialization.DataMemberAttribute>] atrybutu. Jeśli chcesz typów pochodnych klasy w kontrakcie danych mogą być musi zidentyfikować je za pomocą [<xref:System.Runtime.Serialization.KnownTypeAttribute>] atrybutu.</span><span class="sxs-lookup"><span data-stu-id="22bc5-129">The individual properties or fields you want visible to both client and server should be marked with the [<xref:System.Runtime.Serialization.DataMemberAttribute>] attribute.If you want types derived from a class in the data contract to be allowed, you must identify them with the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute.</span></span> <span data-ttu-id="22bc5-130">Usługi WCF zostaną tylko serializacji lub deserializacji typy w interfejsie usługi i zidentyfikowane jako znanych typów.</span><span class="sxs-lookup"><span data-stu-id="22bc5-130">WCF will only serialize or deserialize types in the service interface and types identified as known types.</span></span> <span data-ttu-id="22bc5-131">Przy próbie Użyj typu, który nie jest znanym typem, wystąpi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="22bc5-131">If you attempt to use a type that is not a known type, an exception will occur.</span></span>  
  
 <span data-ttu-id="22bc5-132">Aby uzyskać więcej informacji na temat kontraktów danych, zobacz [kontraktów danych](../../../docs/framework/wcf/samples/data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="22bc5-132">For more information about data contracts, see [Data Contracts](../../../docs/framework/wcf/samples/data-contracts.md).</span></span>  
  
```  
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
  
### <a name="step-3-implement-the-wcf-service"></a><span data-ttu-id="22bc5-133">Krok 3: Implementowanie usługi WCF</span><span class="sxs-lookup"><span data-stu-id="22bc5-133">Step 3: Implement the WCF service</span></span>  
 <span data-ttu-id="22bc5-134">Następnie należy zaimplementować klasy usługi WCF, który implementuje interfejs, który został zdefiniowany w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="22bc5-134">Next, you should implement the WCF service class that implements the interface you defined in the previous step.</span></span>  
  
```  
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
  
### <a name="step-4-configure-the-service-and-the-client"></a><span data-ttu-id="22bc5-135">Krok 4: Konfigurowanie usługi i klienta</span><span class="sxs-lookup"><span data-stu-id="22bc5-135">Step 4: Configure the service and the client</span></span>  
 <span data-ttu-id="22bc5-136">Aby uruchomić usługi WCF, należy zadeklarować punktu końcowego, który uwidacznia interfejs tej usługi pod określonym adresem URL używa określonego powiązania WCF.</span><span class="sxs-lookup"><span data-stu-id="22bc5-136">To run a WCF service, you need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="22bc5-137">Powiązanie określa szczegóły transportu, kodowanie i protokół dla klientów i serwerów, które do komunikacji.</span><span class="sxs-lookup"><span data-stu-id="22bc5-137">A binding specifies the transport, encoding and protocol details for the clients and server to communicate.</span></span> <span data-ttu-id="22bc5-138">Zazwyczaj można dodać powiązania do pliku konfiguracyjnego projektu usługi (web.config).</span><span class="sxs-lookup"><span data-stu-id="22bc5-138">You typically add bindings to the service project’s configuration file (web.config).</span></span> <span data-ttu-id="22bc5-139">Poniżej przedstawiono wpis powiązanie, na przykład usługi:</span><span class="sxs-lookup"><span data-stu-id="22bc5-139">The following shows a binding entry for the example service:</span></span>  
  
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
  
 <span data-ttu-id="22bc5-140">Następnie należy skonfigurować klienta do dopasowania informacje o powiązaniu, określony przez usługę.</span><span class="sxs-lookup"><span data-stu-id="22bc5-140">Next, you need to configure the client to match the binding information specified by the service.</span></span> <span data-ttu-id="22bc5-141">Aby to zrobić, dodaj następującą wartość do pliku konfiguracyjnego (app.config) aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="22bc5-141">To do so, add the following to the client’s application configuration (app.config) file.</span></span>  
  
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
  
### <a name="step-5-run-the-service"></a><span data-ttu-id="22bc5-142">Krok 5: Uruchom usługę</span><span class="sxs-lookup"><span data-stu-id="22bc5-142">Step 5: Run the service</span></span>  
 <span data-ttu-id="22bc5-143">Na koniec można samodzielnie obsługiwać go w aplikacji konsoli dodając następujące wiersze do usługi app Service i uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="22bc5-143">Finally, you can self-host it in a console application by adding the following lines to the service app, and starting the app.</span></span> <span data-ttu-id="22bc5-144">Aby uzyskać więcej informacji na temat innych sposobów hostowania aplikacji usługi WCF [Hosting usług](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="22bc5-144">For more information about other ways to host a WCF service application, [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
```  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a><span data-ttu-id="22bc5-145">Krok 6: Wywołania usługi z klienta</span><span class="sxs-lookup"><span data-stu-id="22bc5-145">Step 6: Call the service from the client</span></span>  
 <span data-ttu-id="22bc5-146">Aby wywołać usługę od klienta, należy utworzyć fabryki kanałów dla usługi i żądania kanału, który umożliwi bezpośrednio wywoływać `GetCustomer` metody bezpośrednio z klienta.</span><span class="sxs-lookup"><span data-stu-id="22bc5-146">To call the service from the client, you need to create a channel factory for the service, and request a channel, which will enable you to directly call the `GetCustomer` method directly from the client.</span></span> <span data-ttu-id="22bc5-147">Kanał implementuje interfejs usługi i obsługuje podstawowej logiki żądania/odpowiedzi dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="22bc5-147">The channel implements the service’s interface and handles the underlying request/reply logic for you.</span></span>  <span data-ttu-id="22bc5-148">Wartość zwrócona przez wywołanie tej metody jest zdeserializowany kopię odpowiedzi usługi.</span><span class="sxs-lookup"><span data-stu-id="22bc5-148">The return value from that method call is the deserialized copy of the service response.</span></span>  
  
```  
ChannelFactory<ICustomerManager> factory =   
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a><span data-ttu-id="22bc5-149">Klient wysyła obiekt przez wartości z serwerem</span><span class="sxs-lookup"><span data-stu-id="22bc5-149">The client sends a by-value object to the server</span></span>  
 <span data-ttu-id="22bc5-150">W tym scenariuszu urządzenie klienta wysyła obiekt do serwera, przez wartość.</span><span class="sxs-lookup"><span data-stu-id="22bc5-150">In this scenario, the client sends an object to the server, by-value.</span></span> <span data-ttu-id="22bc5-151">Oznacza to, że serwer otrzyma kopię zdeserializowany obiekt.</span><span class="sxs-lookup"><span data-stu-id="22bc5-151">This means that the server will receive a deserialized copy of the object.</span></span>  <span data-ttu-id="22bc5-152">Serwer można wywoływać metod w tej kopii i można zagwarantować, że nie istnieje żadne wywołanie zwrotne do kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="22bc5-152">The server can call methods on that copy and be guaranteed there is no callback into client code.</span></span> <span data-ttu-id="22bc5-153">Jak wspomniano wcześniej, normalne WCF wymiany danych są przez wartość.</span><span class="sxs-lookup"><span data-stu-id="22bc5-153">As mentioned previously, normal WCF exchanges of data are by-value.</span></span>  <span data-ttu-id="22bc5-154">Gwarantuje to, że wywołanie metod na jednym z tych obiektów jest wykonywana lokalnie tylko — nie wywoła kodu na kliencie.</span><span class="sxs-lookup"><span data-stu-id="22bc5-154">This guarantees that calling methods on one of these objects executes locally only – it will not invoke code on the client.</span></span>  
  
 <span data-ttu-id="22bc5-155">Ten scenariusz przedstawia następujące wywołanie metody COM:</span><span class="sxs-lookup"><span data-stu-id="22bc5-155">This scenario represents the following COM method call:</span></span>  
  
```  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 <span data-ttu-id="22bc5-156">W tym scenariuszu używa tego samego interfejsu i danych kontraktu usługi jak pokazano w pierwszym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="22bc5-156">This scenario uses the same service interface and data contract as shown in the first example.</span></span> <span data-ttu-id="22bc5-157">Ponadto klienta i usługi zostaną skonfigurowane w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="22bc5-157">In addition, the client and service will be configured in the same way.</span></span> <span data-ttu-id="22bc5-158">W tym przykładzie jest tworzony kanał, do Przenieś obiekt, a następnie uruchom ten sam sposób.</span><span class="sxs-lookup"><span data-stu-id="22bc5-158">In this example, a channel is created to send the object and run the same way.</span></span> <span data-ttu-id="22bc5-159">Jednak w tym przykładzie utworzysz klienta, który wywołuje usługę, przekazywanie obiektu przez wartość.</span><span class="sxs-lookup"><span data-stu-id="22bc5-159">However, for this example, you will create a client that calls the service, passing an object by-value.</span></span> <span data-ttu-id="22bc5-160">Metody usługi, które klient nawiąże połączenie w kontrakcie usługi jest wyświetlane wytłuszczonym drukiem:</span><span class="sxs-lookup"><span data-stu-id="22bc5-160">The service method the client will call in the service contract is shown in bold:</span></span>  
  
```  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a><span data-ttu-id="22bc5-161">Dodawanie kodu do klienta, który wysyła obiektu przez wartość</span><span class="sxs-lookup"><span data-stu-id="22bc5-161">Add code to the client that sends a by-value object</span></span>  
 <span data-ttu-id="22bc5-162">Poniższy kod przedstawia sposób klient tworzy nowy obiekt klienta przez wartość tworzy kanał do komunikacji z `ICustomerManager` usługi i wysyła do niego obiekt klienta.</span><span class="sxs-lookup"><span data-stu-id="22bc5-162">The following code shows how the client creates a new by-value customer object, creates a channel to communicate with the `ICustomerManager` service, and sends the customer object to it.</span></span>  
  
 <span data-ttu-id="22bc5-163">Obiekt klienta będą serializowane i wysyłane do usługi, w którym jest deserializacji przez usługę do nowej kopii tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="22bc5-163">The customer object will be serialized, and sent to the service, where it is deserialized by the service into a new copy of that object.</span></span>  <span data-ttu-id="22bc5-164">Wszystkie metody wywołuje usługę dla tego obiektu będą wykonywane tylko lokalnie na serwerze. Należy pamiętać, że ten kod ilustruje wysyłania typem pochodnym jest (`PremiumCustomer`).</span><span class="sxs-lookup"><span data-stu-id="22bc5-164">Any methods the service calls on this object will execute only locally on the server.It’s important to note that this code illustrates sending a derived type (`PremiumCustomer`).</span></span>  <span data-ttu-id="22bc5-165">Kontrakt usługi oczekuje `Customer` obiekt, ale dane usługi należy Zwiń używa [<xref:System.Runtime.Serialization.KnownTypeAttribute>] atrybutu, aby wskazać, że `PremiumCustomer` również jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="22bc5-165">The service contract expects a `Customer` object, but the service data contract uses the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute to indicate that `PremiumCustomer` is also allowed.</span></span>  <span data-ttu-id="22bc5-166">Usługi WCF zakończy się niepowodzeniem prób do serializacji lub deserializacji innego typu, za pośrednictwem tego interfejsu usługi.</span><span class="sxs-lookup"><span data-stu-id="22bc5-166">WCF will fail attempts to serialize or deserialize any other type via this service interface.</span></span>  
  
```  
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
  
## <a name="the-service-returns-an-object-by-reference"></a><span data-ttu-id="22bc5-167">Usługa zwraca obiekt przez odwołanie</span><span class="sxs-lookup"><span data-stu-id="22bc5-167">The service returns an object by reference</span></span>  
 <span data-ttu-id="22bc5-168">W tym scenariuszu aplikacji klienckiej nawiązuje połączenie z usługą zdalnego i metoda zwraca obiekt, który jest przekazywana przez odwołanie z usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="22bc5-168">For this scenario, the client app makes a call to the remote service and the method returns an object, which is passed by reference from the service to the client.</span></span>  
  
 <span data-ttu-id="22bc5-169">Jak wspomniano wcześniej, usługi WCF zawsze zwraca obiekt przez wartość.</span><span class="sxs-lookup"><span data-stu-id="22bc5-169">As mentioned previously, WCF services always return object by value.</span></span>  <span data-ttu-id="22bc5-170">Jednak można uzyskać podobny efekt za pomocą <xref:System.ServiceModel.EndpointAddress10> klasy.</span><span class="sxs-lookup"><span data-stu-id="22bc5-170">However, you can achieve a similar result by using the <xref:System.ServiceModel.EndpointAddress10> class.</span></span>  <span data-ttu-id="22bc5-171"><xref:System.ServiceModel.EndpointAddress10> Jest obiektem serializacji przez wartość używaną przez klienta można uzyskać obiektu sesyjnych przez odwołania na serwerze.</span><span class="sxs-lookup"><span data-stu-id="22bc5-171">The <xref:System.ServiceModel.EndpointAddress10> is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span>  
  
 <span data-ttu-id="22bc5-172">Zachowanie obiektu przez odwołanie w programie WCF wyświetlane w tym scenariuszu są inne niż modelu DCOM.</span><span class="sxs-lookup"><span data-stu-id="22bc5-172">The behavior of the by-reference object in WCF shown in this scenario is different than DCOM.</span></span>  <span data-ttu-id="22bc5-173">W modelu DCOM Serwer może zwrócić przez odwołanie obiektu do klienta bezpośrednio, a klient może wywołać metody tego obiektu, które wykonania na serwerze.</span><span class="sxs-lookup"><span data-stu-id="22bc5-173">In DCOM, the server can return a by-reference object to the client directly, and the client can call that object’s methods, which execute on the server.</span></span>  <span data-ttu-id="22bc5-174">W programie WCF jednak obiektu zwróconego jest zawsze przez wartość.</span><span class="sxs-lookup"><span data-stu-id="22bc5-174">In WCF, however, the object returned is always by-value.</span></span>  <span data-ttu-id="22bc5-175">Klient musi mieć przez wartość tego obiektu, w reprezentowany przez <xref:System.ServiceModel.EndpointAddress10> i użyć go do tworzenia własnego obiektu sesyjnych przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="22bc5-175">The client must take that by-value object, represented by <xref:System.ServiceModel.EndpointAddress10> and use it to create its own sessionful by-reference object.</span></span>  <span data-ttu-id="22bc5-176">Wywołania metody klienta w obiekcie sesyjnych wykonania na serwerze. Innymi słowy ten obiekt przez odwołanie w programie WCF jest normalne usługi WCF, który jest skonfigurowany tak, aby sesyjnych.</span><span class="sxs-lookup"><span data-stu-id="22bc5-176">The client method calls on the sessionful object execute on the server.In other words, this by-reference object in WCF is a normal WCF service that is configured to be sessionful.</span></span>  
  
 <span data-ttu-id="22bc5-177">W programie WCF sesja jest sposób korelacji wiele komunikatów przesyłanych między dwoma punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="22bc5-177">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span>  <span data-ttu-id="22bc5-178">Oznacza to, że gdy klient uzyskuje połączenie z tą usługą, sesja zostanie nawiązane między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="22bc5-178">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span>  <span data-ttu-id="22bc5-179">Klient będzie używać jednego wystąpienia unikatowy obiektu po stronie serwera dla wszystkich jego interakcji w tym jednej sesji.</span><span class="sxs-lookup"><span data-stu-id="22bc5-179">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span> <span data-ttu-id="22bc5-180">Przekroczono kontrakty WCF są podobne do wzorców żądanie/odpowiedź nawiązaniem połączenia sieciowego.</span><span class="sxs-lookup"><span data-stu-id="22bc5-180">Sessionful WCF contracts are similar to connection-oriented network request/response patterns.</span></span>  
  
 <span data-ttu-id="22bc5-181">Ten scenariusz jest reprezentowana przez następującą metodę modelu DCOM.</span><span class="sxs-lookup"><span data-stu-id="22bc5-181">This scenario is represented by the following DCOM method.</span></span>  
  
```  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a><span data-ttu-id="22bc5-182">Krok 1: Definiowanie interfejsu usługi Sessionful WCF i wdrażania</span><span class="sxs-lookup"><span data-stu-id="22bc5-182">Step 1: Define the Sessionful WCF service interface and implementation</span></span>  
 <span data-ttu-id="22bc5-183">Najpierw należy zdefiniować interfejsu usługi WCF, która zawiera obiekt sesyjnych.</span><span class="sxs-lookup"><span data-stu-id="22bc5-183">First, define a WCF service interface that contains the sessionful object.</span></span>  
  
 <span data-ttu-id="22bc5-184">W tym kodzie sesyjnych obiekt jest oznaczony atrybutem `ServiceContract` atrybut, który identyfikuje ją jako regularne interfejsu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="22bc5-184">In this code, the sessionful object is marked with the `ServiceContract` attribute, which identifies it as a regular WCF service interface.</span></span>  <span data-ttu-id="22bc5-185">Ponadto <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> właściwość jest ustawiona na wskazują, będzie on zamykania usługi.</span><span class="sxs-lookup"><span data-stu-id="22bc5-185">In addition, the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> property is set to indicate it will be a sessionful service.</span></span>  
  
```  
[ServiceContract(SessionMode = SessionMode.Allowed)]  
public interface ISessionBoundObject  
{  
    [OperationContract]  
    string GetCurrentValue();  
  
    [OperationContract]  
    void SetCurrentValue(string value);  
}  
```  
  
 <span data-ttu-id="22bc5-186">Poniższy kod przedstawia implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="22bc5-186">The following code shows the service implementation.</span></span>  
  
 <span data-ttu-id="22bc5-187">Usługa jest oznaczona atrybutem [ServiceBehavior] i jego właściwość InstanceContextMode ustawioną InstanceContextMode.PerSessions w celu wskazania, że unikatowe wystąpienie tego typu powinny być tworzone dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="22bc5-187">The service is marked with the [ServiceBehavior] attribute, and its InstanceContextMode property set to InstanceContextMode.PerSessions to indicate that a unique instance of this type should be created for each session.</span></span>  
  
```  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a><span data-ttu-id="22bc5-188">Krok 2: Definiowanie usługi fabryka WCF dla obiekt zamykania</span><span class="sxs-lookup"><span data-stu-id="22bc5-188">Step 2: Define the WCF factory service for the sessionful object</span></span>  
 <span data-ttu-id="22bc5-189">Usługa, która tworzy obiekt sesyjnych musi zdefiniowany i zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="22bc5-189">The service that creates the sessionful object must be defined and implemented.</span></span> <span data-ttu-id="22bc5-190">Poniższy kod przedstawia, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="22bc5-190">The following code shows how to do this.</span></span> <span data-ttu-id="22bc5-191">Ten kod tworzy innej usługi WCF, która zwraca <xref:System.ServiceModel.EndpointAddress10> obiektu.</span><span class="sxs-lookup"><span data-stu-id="22bc5-191">This code creates another WCF service that returns an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  <span data-ttu-id="22bc5-192">Jest to format możliwy do serializacji dla punktu końcowego może użyć do utworzenia obiektu sesji pełnej.</span><span class="sxs-lookup"><span data-stu-id="22bc5-192">This is a serializable form of an endpoint the can use to create the session-full object.</span></span>  
  
```  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 <span data-ttu-id="22bc5-193">Poniżej znajduje się wdrożenia tej usługi.</span><span class="sxs-lookup"><span data-stu-id="22bc5-193">Following is the implementation of this service.</span></span> <span data-ttu-id="22bc5-194">Ta implementacja obsługuje pojedyncze fabryki kanałów do tworzenia obiektów sesyjnych.</span><span class="sxs-lookup"><span data-stu-id="22bc5-194">This implementation maintains a singleton channel factory to create sessionful objects.</span></span>  <span data-ttu-id="22bc5-195">Gdy `GetInstanceAddress` jest nazywane, tworzy kanału i tworzy <xref:System.ServiceModel.EndpointAddress10> obiekt, który wskazuje zdalny adres skojarzony z tym kanale.</span><span class="sxs-lookup"><span data-stu-id="22bc5-195">When `GetInstanceAddress` is called, it creates a channel and creates an <xref:System.ServiceModel.EndpointAddress10> object that points to the remote address associated with this channel.</span></span>   <span data-ttu-id="22bc5-196"><xref:System.ServiceModel.EndpointAddress10> ma typ danych, który może być zwracany do klienta przez wartość.</span><span class="sxs-lookup"><span data-stu-id="22bc5-196"><xref:System.ServiceModel.EndpointAddress10> is a data type that can be returned to the client by-value.</span></span>  
  
```  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a><span data-ttu-id="22bc5-197">Krok 3: Konfigurowanie i uruchamianie usług WCF</span><span class="sxs-lookup"><span data-stu-id="22bc5-197">Step 3: Configure and start the WCF services</span></span>  
 <span data-ttu-id="22bc5-198">Aby zapewnić obsługę tych usług, należy wprowadzić następujące dodatki do pliku konfiguracji serwera (web.config).</span><span class="sxs-lookup"><span data-stu-id="22bc5-198">To host these services, you will need to make the following additions to the server’s configuration file (web.config).</span></span>  
  
1.  <span data-ttu-id="22bc5-199">Dodaj `<client>` opisy punktu końcowego dla obiektu sesyjnych.</span><span class="sxs-lookup"><span data-stu-id="22bc5-199">Add a `<client>` section that describes the endpoint for the sessionful object.</span></span>  <span data-ttu-id="22bc5-200">W tym scenariuszu serwer działa jako klient i musi być skonfigurowany, aby je włączyć.</span><span class="sxs-lookup"><span data-stu-id="22bc5-200">In this scenario, the server also acts as a client and must be configured to enable this.</span></span>  
  
2.  <span data-ttu-id="22bc5-201">W `<services>` sekcji, Zadeklaruj punktów końcowych usługi dla obiekt fabryki i sessionful.</span><span class="sxs-lookup"><span data-stu-id="22bc5-201">In the `<services>` section, declare service endpoints for the factory and sessionful object.</span></span>  <span data-ttu-id="22bc5-202">Dzięki temu klient do komunikacji z punktami końcowymi usługi, uzyskać <xref:System.ServiceModel.EndpointAddress10> i utworzyć podczas zamykania kanału sesji.</span><span class="sxs-lookup"><span data-stu-id="22bc5-202">This enables the client to communicate with the service endpoints, acquire the <xref:System.ServiceModel.EndpointAddress10> and create the sessionful channel.</span></span>  
  
 <span data-ttu-id="22bc5-203">Oto przykładowy plik konfiguracji przy użyciu tych ustawień:</span><span class="sxs-lookup"><span data-stu-id="22bc5-203">Following is an example configuration file with these settings:</span></span>  
  
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
  
 <span data-ttu-id="22bc5-204">Dodaj następujące wiersze do aplikacji konsoli, w celu hosta samodzielnego usługi i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="22bc5-204">Add the following lines to a console application, to self-host the service, and start the app.</span></span>  
  
```  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a><span data-ttu-id="22bc5-205">Krok 4: Konfigurowanie klienta i wywołania tej usługi</span><span class="sxs-lookup"><span data-stu-id="22bc5-205">Step 4: Configure the client and call the service</span></span>  
 <span data-ttu-id="22bc5-206">Konfigurowanie klienta do komunikowania się z usługi WCF, wprowadzając następujące wpisy w pliku konfiguracji projektu aplikacji (app.config).</span><span class="sxs-lookup"><span data-stu-id="22bc5-206">Configure the client to communicate with the WCF services by making the following entries in the project’s application configuration file (app.config).</span></span>  
  
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
  
 <span data-ttu-id="22bc5-207">Do wywołania tej usługi, należy dodać kodu do klienta, aby wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="22bc5-207">To call the service, add the code to the client to do the following:</span></span>  
  
1.  <span data-ttu-id="22bc5-208">Tworzenie kanału do `ISessionBoundFactory` usługi.</span><span class="sxs-lookup"><span data-stu-id="22bc5-208">Create a channel to the `ISessionBoundFactory` service.</span></span>  
  
2.  <span data-ttu-id="22bc5-209">Użyj kanału do wywołania `ISessionBoundFactory` usługi Uzyskaj <xref:System.ServiceModel.EndpointAddress10> bbject.</span><span class="sxs-lookup"><span data-stu-id="22bc5-209">Use the channel to invoke the `ISessionBoundFactory` service an obtain an <xref:System.ServiceModel.EndpointAddress10> bbject.</span></span>  
  
3.  <span data-ttu-id="22bc5-210">Użyj <xref:System.ServiceModel.EndpointAddress10> do utworzenia kanału do uzyskania zamykania obiektu.</span><span class="sxs-lookup"><span data-stu-id="22bc5-210">Use the <xref:System.ServiceModel.EndpointAddress10> to create a channel to obtain a sessionful object.</span></span>  
  
4.  <span data-ttu-id="22bc5-211">Wywołanie `SetCurrentValue` i `GetCurrentValue` używane w wielu wywołań metody, aby zademonstrować pozostaje w tym samym wystąpieniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="22bc5-211">Call the `SetCurrentValue` and `GetCurrentValue` methods to demonstrate it remains the same object instance is used across multiple calls.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="22bc5-212">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22bc5-212">See Also</span></span>  
 [<span data-ttu-id="22bc5-213">Podstawy programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="22bc5-213">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="22bc5-214">Projektowanie i implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="22bc5-214">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [<span data-ttu-id="22bc5-215">Kompilowanie klientów</span><span class="sxs-lookup"><span data-stu-id="22bc5-215">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
 [<span data-ttu-id="22bc5-216">Usługi dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="22bc5-216">Duplex Services</span></span>](../../../docs/framework/wcf/feature-details/duplex-services.md)
