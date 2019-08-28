---
title: Przegląd tworzenia punktów końcowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: 0b0c22737e9407ebe2cb56c15fb7ff75d16b50a4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040309"
---
# <a name="endpoint-creation-overview"></a><span data-ttu-id="57130-102">Przegląd tworzenia punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="57130-102">Endpoint Creation Overview</span></span>

<span data-ttu-id="57130-103">Cała komunikacja z usługą Windows Communication Foundation (WCF) odbywa się za pomocą *punktów końcowych* usługi.</span><span class="sxs-lookup"><span data-stu-id="57130-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="57130-104">Punkty końcowe zapewniają klientom dostęp do funkcji oferowanych przez usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="57130-104">Endpoints provide the clients access to the functionality that a WCF service offers.</span></span> <span data-ttu-id="57130-105">W tej sekcji opisano strukturę punktu końcowego i przedstawiono sposób definiowania punktu końcowego w konfiguracji i w kodzie.</span><span class="sxs-lookup"><span data-stu-id="57130-105">This section describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code.</span></span>

## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="57130-106">Struktura punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="57130-106">The Structure of an Endpoint</span></span>

<span data-ttu-id="57130-107">Każdy punkt końcowy zawiera adres wskazujący, gdzie znaleźć punkt końcowy, powiązanie, które określa, jak klient może komunikować się z punktem końcowym, oraz umowę, która identyfikuje dostępne metody.</span><span class="sxs-lookup"><span data-stu-id="57130-107">Each endpoint contains an address that indicates where to find the endpoint, a binding that specifies how a client can communicate with the endpoint, and a contract that identifies the methods available.</span></span>

- <span data-ttu-id="57130-108">**Adres**.</span><span class="sxs-lookup"><span data-stu-id="57130-108">**Address**.</span></span> <span data-ttu-id="57130-109">Adres jednoznacznie identyfikuje punkt końcowy i informuje potencjalnych klientów, w których znajduje się usługa.</span><span class="sxs-lookup"><span data-stu-id="57130-109">The address uniquely identifies the endpoint and tells potential consumers where the service is located.</span></span> <span data-ttu-id="57130-110">Jest reprezentowana w modelu obiektów WCF przez <xref:System.ServiceModel.EndpointAddress> adres, który zawiera Uniform Resource Identifier (URI) i właściwości adresu, które obejmują tożsamość, niektóre elementy Web Services Description Language (WSDL) i kolekcję opcjonalną nagłówka.</span><span class="sxs-lookup"><span data-stu-id="57130-110">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> address, which contains a Uniform Resource Identifier (URI) and address properties that include an identity, some Web Services Description Language (WSDL) elements, and a collection of optional headers.</span></span> <span data-ttu-id="57130-111">Opcjonalne nagłówki zawierają dodatkowe informacje o adresach, które identyfikują lub współpracują z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="57130-111">The optional headers provide additional detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="57130-112">Aby uzyskać więcej informacji, zobacz [Określanie adresu punktu końcowego](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="57130-112">For more information, see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>

- <span data-ttu-id="57130-113">**Powiązanie**.</span><span class="sxs-lookup"><span data-stu-id="57130-113">**Binding**.</span></span> <span data-ttu-id="57130-114">Powiązanie określa sposób komunikacji z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="57130-114">The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="57130-115">Powiązanie określa, w jaki sposób punkt końcowy komunikuje się z całym świecie, w tym który protokół transportowy do użycia (na przykład TCP lub HTTP), którego kodowanie ma być używane dla komunikatów (na przykład tekst lub binarny), a wymagania dotyczące zabezpieczeń są niezbędne (dla przykład SSL [SSL] lub zabezpieczenia komunikatów SOAP).</span><span class="sxs-lookup"><span data-stu-id="57130-115">The binding specifies how the endpoint communicates with the world, including which transport protocol to use (for example, TCP or HTTP), which encoding to use for the messages (for example, text or binary), and which security requirements are necessary (for example, Secure Sockets Layer [SSL] or SOAP message security).</span></span> <span data-ttu-id="57130-116">Aby uzyskać więcej informacji, zobacz [using bindings to configure Services and clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="57130-116">For more information, see [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>

- <span data-ttu-id="57130-117">**Kontrakt usługi**.</span><span class="sxs-lookup"><span data-stu-id="57130-117">**Service contract**.</span></span> <span data-ttu-id="57130-118">Kontrakt usługi zawiera opis funkcji, które punkt końcowy uwidacznia dla klienta.</span><span class="sxs-lookup"><span data-stu-id="57130-118">The service contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="57130-119">Kontrakt określa operacje, które klient może wywołać, formę komunikatu oraz typ parametrów wejściowych lub danych wymaganych do wywołania operacji oraz rodzaj przetwarzania lub komunikatów odpowiedzi, których może oczekiwać klient.</span><span class="sxs-lookup"><span data-stu-id="57130-119">A contract specifies the operations that a client can call, the form of the message and the type of input parameters or data required to call the operation, and the kind of processing or response message the client can expect.</span></span> <span data-ttu-id="57130-120">Trzy podstawowe typy kontraktów odnoszą się do podstawowych wzorców wymiany komunikatów (MEPs): datagram (jednokierunkowe), żądanie/odpowiedź i dupleks (dwukierunkowe).</span><span class="sxs-lookup"><span data-stu-id="57130-120">Three basic types of contracts correspond to basic message exchange patterns (MEPs): datagram (one-way), request/reply, and duplex (bidirectional).</span></span> <span data-ttu-id="57130-121">Kontrakt usługi może również korzystać z kontraktów danych i komunikatów w celu wymagania określonych typów danych i formatów komunikatów podczas uzyskiwania dostępu do nich.</span><span class="sxs-lookup"><span data-stu-id="57130-121">The service contract can also employ data and message contracts to require specific data types and message formats when being accessed.</span></span> <span data-ttu-id="57130-122">Aby uzyskać więcej informacji na temat sposobu definiowania kontraktu usługi, zobacz [Projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="57130-122">For more information about how to define a service contract, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md).</span></span> <span data-ttu-id="57130-123">Należy pamiętać, że klient może być również wymagany do wdrożenia kontraktu zdefiniowanego przez usługę, zwanego kontraktem wywołania zwrotnego, aby odbierać komunikaty z usługi w trybie dupleksu unikatowy MEP.</span><span class="sxs-lookup"><span data-stu-id="57130-123">Note that a client may also be required to implement a service-defined contract, called a callback contract, to receive messages from the service in a duplex MEP.</span></span> <span data-ttu-id="57130-124">Aby uzyskać więcej informacji, zobacz [usługi dupleksowe](../../../docs/framework/wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="57130-124">For more information, see [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span>

<span data-ttu-id="57130-125">Punkt końcowy usługi można określić samodzielnie za pomocą kodu lub deklaratywnie za pośrednictwem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="57130-125">The endpoint for a service can be specified either imperatively by using code or declaratively through configuration.</span></span> <span data-ttu-id="57130-126">Jeśli nie określono żadnych punktów końcowych, środowisko uruchomieniowe zapewnia domyślne punkty końcowe, dodając jeden domyślny punkt końcowy dla każdego adresu podstawowego dla każdego kontraktu usługi zaimplementowanego przez usługę.</span><span class="sxs-lookup"><span data-stu-id="57130-126">If no endpoints are specified then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="57130-127">Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne, ponieważ powiązania i adresy dla wdrożonej usługi są zwykle inne niż te używane podczas tworzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="57130-127">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="57130-128">Ogólnie rzecz biorąc, bardziej praktyczne jest zdefiniowanie punktów końcowych usługi przy użyciu konfiguracji zamiast kodu.</span><span class="sxs-lookup"><span data-stu-id="57130-128">Generally, it is more practical to define service endpoints using configuration rather than code.</span></span> <span data-ttu-id="57130-129">Przechowywanie informacji o powiązaniach i adresowaniu poza kodem pozwala im zmieniać bez konieczności ponownego kompilowania i wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57130-129">Keeping the binding and addressing information out of the code allows them to change without having to recompile and redeploy the application.</span></span>

> [!NOTE]
> <span data-ttu-id="57130-130">Podczas dodawania punktu końcowego usługi, który wykonuje personifikację, należy użyć jednej z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metod <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> lub metody w celu poprawnego załadowania kontraktu do nowego <xref:System.ServiceModel.Description.ServiceDescription> obiektu.</span><span class="sxs-lookup"><span data-stu-id="57130-130">When adding a service endpoint that performs impersonation, you must either use one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods or the <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> method to properly load the contract into a new <xref:System.ServiceModel.Description.ServiceDescription> object.</span></span>

## <a name="defining-endpoints-in-code"></a><span data-ttu-id="57130-131">Definiowanie punktów końcowych w kodzie</span><span class="sxs-lookup"><span data-stu-id="57130-131">Defining Endpoints in Code</span></span>

<span data-ttu-id="57130-132">Poniższy przykład ilustruje sposób określania punktu końcowego w kodzie przy użyciu następujących metod:</span><span class="sxs-lookup"><span data-stu-id="57130-132">The following example illustrates how to specify an endpoint in code with the following:</span></span>

- <span data-ttu-id="57130-133">Zdefiniuj kontrakt dla `IEcho` typu usługi, który akceptuje nazwę i echo kogoś z odpowiedzi "Hello \<Name >!".</span><span class="sxs-lookup"><span data-stu-id="57130-133">Define a contract for an `IEcho` type of service that accepts someone's name and echo with the response "Hello \<name>!".</span></span>

- <span data-ttu-id="57130-134">`IEcho` Implementowanie `Echo` usługi typu zdefiniowanej przez kontrakt.</span><span class="sxs-lookup"><span data-stu-id="57130-134">Implement an `Echo` service of the type defined by the `IEcho` contract.</span></span>

- <span data-ttu-id="57130-135">Określ adres `http://localhost:8000/Echo` punktu końcowego dla usługi.</span><span class="sxs-lookup"><span data-stu-id="57130-135">Specify an endpoint address of `http://localhost:8000/Echo` for the service.</span></span>

- <span data-ttu-id="57130-136">`Echo` Skonfiguruj usługę <xref:System.ServiceModel.WSHttpBinding> przy użyciu powiązania.</span><span class="sxs-lookup"><span data-stu-id="57130-136">Configure the `Echo` service using a <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>

```csharp
namespace Echo
{
   // Define the contract for the IEcho service
   [ServiceContract]
   public interface IEcho
   {
       [OperationContract]
       String Hello(string name)
   }

   // Create an Echo service that implements IEcho contract
   class Echo : IEcho
   {
      public string Hello(string name)
      {
         return "Hello" + name + "!";
      }
      public static void Main ()
      {
          //Specify the base address for Echo service.
          Uri echoUri = new Uri("http://localhost:8000/");

          //Create a ServiceHost for the Echo service.
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);

          // Use a predefined WSHttpBinding to configure the service.
          WSHttpBinding binding = new WSHttpBinding();

          // Add the endpoint for this service to the service host.
          serviceHost.AddServiceEndpoint(
             typeof(IEcho),
             binding,
             echoUri
           );

          // Open the service host to run it.
          serviceHost.Open();
     }
  }
}
```

```vb
' Define the contract for the IEcho service
    <ServiceContract()> _
    Public Interface IEcho
        <OperationContract()> _
        Function Hello(ByVal name As String) As String
    End Interface

' Create an Echo service that implements IEcho contract
    Public Class Echo
        Implements IEcho
        Public Function Hello(ByVal name As String) As String _
 Implements ICalculator.Hello
            Dim result As String = "Hello" + name + "!"
            Return result
        End Function

' Specify the base address for Echo service.
Dim echoUri As Uri = New Uri("http://localhost:8000/")

' Create a ServiceHost for the Echo service.
Dim svcHost As ServiceHost = New ServiceHost(GetType(HelloWorld), echoUri)

' Use a predefined WSHttpBinding to configure the service.
Dim binding As New WSHttpBinding()

' Add the endpoint for this service to the service host.
serviceHost.AddServiceEndpoint(GetType(IEcho), binding, echoUri)

' Open the service host to run it.
serviceHost.Open()
```

> [!NOTE]
> <span data-ttu-id="57130-137">Host usługi jest tworzony przy użyciu adresu podstawowego, a następnie pozostała część adresu względem adresu podstawowego jest określana jako część punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="57130-137">The service host is created with a base address and then the rest of the address, relative to the base address, is specified as part of an endpoint.</span></span> <span data-ttu-id="57130-138">Takie partycjonowanie adresu pozwala na bardziej wygodne definiowanie wielu punktów końcowych dla usług na hoście.</span><span class="sxs-lookup"><span data-stu-id="57130-138">This partitioning of the address allows multiple endpoints to be defined more conveniently for services at a host.</span></span>

> [!NOTE]
> <span data-ttu-id="57130-139">Właściwości w aplikacji usługi nie mogą być modyfikowane po <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metodzie <xref:System.ServiceModel.ServiceHostBase>. <xref:System.ServiceModel.Description.ServiceDescription></span><span class="sxs-lookup"><span data-stu-id="57130-139">Properties of <xref:System.ServiceModel.Description.ServiceDescription> in the service application must not be modified subsequent to the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method on <xref:System.ServiceModel.ServiceHostBase>.</span></span> <span data-ttu-id="57130-140">Niektóre elementy członkowskie, takie jak <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> Właściwość `AddServiceEndpoint` i metody w <xref:System.ServiceModel.ServiceHostBase> i <xref:System.ServiceModel.ServiceHost>, zgłaszają wyjątek, jeśli zostały zmodyfikowane po tym punkcie.</span><span class="sxs-lookup"><span data-stu-id="57130-140">Some members, such as the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property and the `AddServiceEndpoint` methods on <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.ServiceHost>, throw an exception if modified past that point.</span></span> <span data-ttu-id="57130-141">Inne umożliwiają modyfikowanie ich, ale wynik jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="57130-141">Others permit you to modify them, but the result is undefined.</span></span>
>
> <span data-ttu-id="57130-142">Analogicznie, na kliencie <xref:System.ServiceModel.Description.ServiceEndpoint> wartości nie mogą być modyfikowane po <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> wywołaniu metody <xref:System.ServiceModel.ChannelFactory>.</span><span class="sxs-lookup"><span data-stu-id="57130-142">Similarly, on the client the <xref:System.ServiceModel.Description.ServiceEndpoint> values must not be modified after the call to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> on the <xref:System.ServiceModel.ChannelFactory>.</span></span> <span data-ttu-id="57130-143"><xref:System.ServiceModel.ChannelFactory.Credentials%2A> Właściwość zgłasza wyjątek, jeśli został zmodyfikowany poza tym punktem.</span><span class="sxs-lookup"><span data-stu-id="57130-143">The <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property throws an exception if modified past that point.</span></span> <span data-ttu-id="57130-144">Inne wartości opisu klienta można modyfikować bez błędu, ale wynik jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="57130-144">The other client description values can be modified without error, but the result is undefined.</span></span>
>
> <span data-ttu-id="57130-145">Niezależnie od tego, czy dla usługi lub klienta zaleca się zmodyfikowanie opisu przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="57130-145">Whether for the service or client, it is recommended that you modify the description prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>

## <a name="defining-endpoints-in-configuration"></a><span data-ttu-id="57130-146">Definiowanie punktów końcowych w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="57130-146">Defining Endpoints in Configuration</span></span>

<span data-ttu-id="57130-147">Podczas tworzenia aplikacji często chcesz odroczyć decyzje administratora, który wdraża aplikację.</span><span class="sxs-lookup"><span data-stu-id="57130-147">When creating an application, you often want to defer decisions to the administrator who is deploying the application.</span></span> <span data-ttu-id="57130-148">Na przykład często nie ma możliwości znajomości informacji o adresie usługi (URI).</span><span class="sxs-lookup"><span data-stu-id="57130-148">For example, there is often no way of knowing in advance what a service address (a URI) will be.</span></span> <span data-ttu-id="57130-149">Zamiast kodowania adresu, preferowane jest umożliwienie administratorowi wykonania tej czynności po utworzeniu usługi.</span><span class="sxs-lookup"><span data-stu-id="57130-149">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="57130-150">Ta elastyczność jest realizowana przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="57130-150">This flexibility is accomplished through configuration.</span></span> <span data-ttu-id="57130-151">Aby uzyskać szczegółowe informacje, zobacz [Konfigurowanie usług](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="57130-151">For details, see [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="57130-152">Użyj [Narzędzia metadanych ServiceModel (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z przełącznikiem filename `/config:`nazwy*pliku* `]` ,`[,`aby szybko utworzyć pliki konfiguracyjne.</span><span class="sxs-lookup"><span data-stu-id="57130-152">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config:`*filename*`[,`*filename*`]` switch to quickly create configuration files.</span></span>

## <a name="using-default-endpoints"></a><span data-ttu-id="57130-153">Używanie domyślnych punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="57130-153">Using Default Endpoints</span></span>

<span data-ttu-id="57130-154">Jeśli w kodzie lub w konfiguracji nie określono żadnych punktów końcowych, środowisko uruchomieniowe zapewnia domyślne punkty końcowe, dodając jeden domyślny punkt końcowy dla każdego adresu podstawowego dla każdego kontraktu usługi zaimplementowanego przez usługę.</span><span class="sxs-lookup"><span data-stu-id="57130-154">If no endpoints are specified in code or in configuration then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="57130-155">Adres podstawowy może być określony w kodzie lub w konfiguracji, a domyślne punkty końcowe są dodawane, gdy <xref:System.ServiceModel.ICommunicationObject.Open> jest wywoływana <xref:System.ServiceModel.ServiceHost>na.</span><span class="sxs-lookup"><span data-stu-id="57130-155">The base address can be specified in code or in configuration, and the default endpoints are added when <xref:System.ServiceModel.ICommunicationObject.Open> is called on the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="57130-156">Ten przykład jest taki sam jak w poprzedniej sekcji, ale ponieważ nie określono żadnych punktów końcowych, dodawane są domyślne punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="57130-156">This example is the same example from the previous section, but since no endpoints are specified, the default endpoints are added.</span></span>

```csharp
namespace Echo
{
   // Define the contract for the IEcho service
   [ServiceContract]
   public interface IEcho
   {
       [OperationContract]
       String Hello(string name)
   }

   // Create an Echo service that implements IEcho contract
   public class Echo : IEcho
   {
      public string Hello(string name)
      {
         return "Hello" + name + "!";
      }
      public static void Main ()
      {
          //Specify the base address for Echo service.
          Uri echoUri = new Uri("http://localhost:8000/");

          //Create a ServiceHost for the Echo service.
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);

          // Open the service host to run it. Default endpoints
          // are added when the service is opened.
          serviceHost.Open();
     }
  }
}
```

```vb
' Define the contract for the IEcho service
    <ServiceContract()> _
    Public Interface IEcho
        <OperationContract()> _
        Function Hello(ByVal name As String) As String
    End Interface

' Create an Echo service that implements IEcho contract
    Public Class Echo
        Implements IEcho
        Public Function Hello(ByVal name As String) As String _
 Implements ICalculator.Hello
            Dim result As String = "Hello" + name + "!"
            Return result
        End Function

' Specify the base address for Echo service.
Dim echoUri As Uri = New Uri("http://localhost:8000/")

' Open the service host to run it. Default endpoints
' are added when the service is opened.
serviceHost.Open()
```

 <span data-ttu-id="57130-157">Jeśli punkty końcowe są podane jawnie, można nadal dodawać domyślne punkty końcowe, wywołując <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> <xref:System.ServiceModel.ServiceHost> dla przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>metody.</span><span class="sxs-lookup"><span data-stu-id="57130-157">If endpoints are explicitly provided, the default endpoints can still be added by calling <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> on the <xref:System.ServiceModel.ServiceHost> before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="57130-158">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, zobacz [Uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="57130-158">For more information about default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="57130-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57130-159">See also</span></span>

- [<span data-ttu-id="57130-160">Implementowanie kontraktów usług</span><span class="sxs-lookup"><span data-stu-id="57130-160">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
