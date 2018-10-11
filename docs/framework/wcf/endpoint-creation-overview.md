---
title: Przegląd tworzenia punktów końcowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: b72c3959b2a42c6a5abc8ef31975d5bdb9ce220e
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086846"
---
# <a name="endpoint-creation-overview"></a><span data-ttu-id="94bfb-102">Przegląd tworzenia punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="94bfb-102">Endpoint Creation Overview</span></span>
<span data-ttu-id="94bfb-103">Cała komunikacja z usługą Windows Communication Foundation (WCF) odbywa się przez *punktów końcowych* usługi.</span><span class="sxs-lookup"><span data-stu-id="94bfb-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="94bfb-104">Punkty końcowe zapewniają klientom dostęp do funkcji, która oferuje usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="94bfb-104">Endpoints provide the clients access to the functionality that a WCF service offers.</span></span> <span data-ttu-id="94bfb-105">W tej sekcji opisuje strukturę punktu końcowego i opisano sposób definiowania punktu końcowego w konfiguracji i w kodzie.</span><span class="sxs-lookup"><span data-stu-id="94bfb-105">This section describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="94bfb-106">Struktura punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="94bfb-106">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="94bfb-107">Każdy punkt końcowy zawiera adres który wskazuje, gdzie można znaleźć punktu końcowego, powiązanie, które określa, jak klient może komunikować się z punktem końcowym i kontraktu, który identyfikuje dostępne metody.</span><span class="sxs-lookup"><span data-stu-id="94bfb-107">Each endpoint contains an address that indicates where to find the endpoint, a binding that specifies how a client can communicate with the endpoint, and a contract that identifies the methods available.</span></span>  
  
-   <span data-ttu-id="94bfb-108">**Adres**.</span><span class="sxs-lookup"><span data-stu-id="94bfb-108">**Address**.</span></span> <span data-ttu-id="94bfb-109">Adres jednoznacznie identyfikuje punkt końcowy i informuje o potencjalnych klientów, w którym znajduje się usługa.</span><span class="sxs-lookup"><span data-stu-id="94bfb-109">The address uniquely identifies the endpoint and tells potential consumers where the service is located.</span></span> <span data-ttu-id="94bfb-110">Jest reprezentowana w modelu obiektu programu WCF za <xref:System.ServiceModel.EndpointAddress> adresu, który zawiera jednolity identyfikator zasobów (URI) i właściwości adresu, które obejmują tożsamość, niektóre elementy sieci Web Services Description Language (WSDL) oraz zbiór opcjonalne nagłówki.</span><span class="sxs-lookup"><span data-stu-id="94bfb-110">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> address, which contains a Uniform Resource Identifier (URI) and address properties that include an identity, some Web Services Description Language (WSDL) elements, and a collection of optional headers.</span></span> <span data-ttu-id="94bfb-111">Opcjonalne nagłówki zawierają dodatkowe szczegółowe informacje adresowania, aby zidentyfikować lub nawiązać kontakt z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="94bfb-111">The optional headers provide additional detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="94bfb-112">Aby uzyskać więcej informacji, zobacz [Określanie adresu punktu końcowego](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="94bfb-112">For more information, see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
-   <span data-ttu-id="94bfb-113">**Powiązanie**.</span><span class="sxs-lookup"><span data-stu-id="94bfb-113">**Binding**.</span></span> <span data-ttu-id="94bfb-114">Powiązanie Określa, jak komunikować się z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="94bfb-114">The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="94bfb-115">Powiązanie Określa, jak punkt końcowy komunikuje się z świat, w tym protokół transportu (na przykład, TCP lub HTTP), które kodowanie do użycia dla wiadomości (na przykład tekst lub dane binarne), a wymagania zabezpieczeń, które są niezbędne (dla przykład Secure Sockets Layer [SSL] lub zabezpieczeń wiadomości protokołu SOAP).</span><span class="sxs-lookup"><span data-stu-id="94bfb-115">The binding specifies how the endpoint communicates with the world, including which transport protocol to use (for example, TCP or HTTP), which encoding to use for the messages (for example, text or binary), and which security requirements are necessary (for example, Secure Sockets Layer [SSL] or SOAP message security).</span></span> <span data-ttu-id="94bfb-116">Aby uzyskać więcej informacji, zobacz [przy użyciu powiązania do konfigurowania usług i klientów](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="94bfb-116">For more information, see [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>  
  
-   <span data-ttu-id="94bfb-117">**Kontrakt usługi**.</span><span class="sxs-lookup"><span data-stu-id="94bfb-117">**Service contract**.</span></span> <span data-ttu-id="94bfb-118">Kontrakt usługi opisano, jakie funkcje uwidacznia punkt końcowy, do klienta.</span><span class="sxs-lookup"><span data-stu-id="94bfb-118">The service contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="94bfb-119">Kontrakt określa operacje, które klient może wywołać, formularz wiadomości i typ parametrów wejściowych lub dane wymagane do wywołania operacji i rodzaju przetwarzania lub komunikat odpowiedzi, których można oczekiwać, że klient.</span><span class="sxs-lookup"><span data-stu-id="94bfb-119">A contract specifies the operations that a client can call, the form of the message and the type of input parameters or data required to call the operation, and the kind of processing or response message the client can expect.</span></span> <span data-ttu-id="94bfb-120">Podstawowe wiadomości programu exchange wzorców (MEPs) odpowiadają trzy podstawowe typy kontraktów: datagramów (jednokierunkowe), żądanie/nietypizowana odpowiedź i dupleks (dwukierunkowe).</span><span class="sxs-lookup"><span data-stu-id="94bfb-120">Three basic types of contracts correspond to basic message exchange patterns (MEPs): datagram (one-way), request/reply, and duplex (bidirectional).</span></span> <span data-ttu-id="94bfb-121">Kontrakt usługi można również używać kontraktów danych i komunikatów wymaga konkretnych typów danych i formaty wiadomości, podczas którego uzyskiwany jest dostęp.</span><span class="sxs-lookup"><span data-stu-id="94bfb-121">The service contract can also employ data and message contracts to require specific data types and message formats when being accessed.</span></span> <span data-ttu-id="94bfb-122">Aby uzyskać więcej informacji na temat Definiowanie kontraktu usługi, zobacz [projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="94bfb-122">For more information about how to define a service contract, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md).</span></span> <span data-ttu-id="94bfb-123">Należy pamiętać o tym, czy klient może być wymagane do implementowania kontraktu zdefiniowane przez usługę, o nazwie kontrakt wywołania zwrotnego do odbierania komunikatów z usługi w MEP dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="94bfb-123">Note that a client may also be required to implement a service-defined contract, called a callback contract, to receive messages from the service in a duplex MEP.</span></span> <span data-ttu-id="94bfb-124">Aby uzyskać więcej informacji, zobacz [usługi dwukierunkowe](../../../docs/framework/wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="94bfb-124">For more information, see [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="94bfb-125">Obowiązkowo przy użyciu kodu lub deklaratywne przy użyciu konfiguracji można określić punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="94bfb-125">The endpoint for a service can be specified either imperatively by using code or declaratively through configuration.</span></span> <span data-ttu-id="94bfb-126">Jeśli nie określono żadnych punktów końcowych następnie środowisko wykonawcze zapewnia domyślne punkty końcowe, dodając jeden domyślny punkt końcowy dla każdego adresu podstawowego dla każdej umowy serwisowej implementowane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="94bfb-126">If no endpoints are specified then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="94bfb-127">Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne ponieważ powiązań i adresów dla wdrożonej usługi są zazwyczaj inne niż używane, gdy usługa jest obecnie sporządzana.</span><span class="sxs-lookup"><span data-stu-id="94bfb-127">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="94bfb-128">Ogólnie rzecz biorąc lepiej jest punkty końcowe usługi przy użyciu konfiguracji zamiast kodu.</span><span class="sxs-lookup"><span data-stu-id="94bfb-128">Generally, it is more practical to define service endpoints using configuration rather than code.</span></span> <span data-ttu-id="94bfb-129">Zachowanie powiązania i adresowanie z kodu pozwala zmienić bez konieczności ponownego kompilowania i ponownego wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="94bfb-129">Keeping the binding and addressing information out of the code allows them to change without having to recompile and redeploy the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94bfb-130">Podczas dodawania punktu końcowego usługi, który wykonuje personifikacji, należy użyć jednej z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody lub <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> metoda prawidłowo załadować umowy do nowej <xref:System.ServiceModel.Description.ServiceDescription> obiektu.</span><span class="sxs-lookup"><span data-stu-id="94bfb-130">When adding a service endpoint that performs impersonation, you must either use one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods or the <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> method to properly load the contract into a new <xref:System.ServiceModel.Description.ServiceDescription> object.</span></span>  
  
## <a name="defining-endpoints-in-code"></a><span data-ttu-id="94bfb-131">Definiowanie punktów końcowych w kodzie</span><span class="sxs-lookup"><span data-stu-id="94bfb-131">Defining Endpoints in Code</span></span>  
 <span data-ttu-id="94bfb-132">Poniższy przykład ilustruje sposób określania punktu końcowego w kodzie za pomocą następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="94bfb-132">The following example illustrates how to specify an endpoint in code with the following:</span></span>  
  
-   <span data-ttu-id="94bfb-133">Definiowanie kontraktu w celu `IEcho` typ usługi, który akceptuje nazwy i echa z odpowiedzią innego użytkownika "Hello \<name >!".</span><span class="sxs-lookup"><span data-stu-id="94bfb-133">Define a contract for an `IEcho` type of service that accepts someone's name and echo with the response "Hello \<name>!".</span></span>  
  
-   <span data-ttu-id="94bfb-134">Implementowanie `Echo` usługi typu zdefiniowanego przez `IEcho` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="94bfb-134">Implement an `Echo` service of the type defined by the `IEcho` contract.</span></span>  
  
-   <span data-ttu-id="94bfb-135">Określ adres punktu końcowego `http://localhost:8000/Echo` dla usługi.</span><span class="sxs-lookup"><span data-stu-id="94bfb-135">Specify an endpoint address of `http://localhost:8000/Echo` for the service.</span></span>  
  
-   <span data-ttu-id="94bfb-136">Konfigurowanie `Echo` usługi przy użyciu <xref:System.ServiceModel.WSHttpBinding> powiązania.</span><span class="sxs-lookup"><span data-stu-id="94bfb-136">Configure the `Echo` service using a <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
```csharp  
Namespace Echo  
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
>  <span data-ttu-id="94bfb-137">Host usługi jest tworzona przy użyciu adres podstawowy, a następnie pozostałą część adresu, określany względem adresu podstawowego jest określone jako część punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="94bfb-137">The service host is created with a base address and then the rest of the address, relative to the base address, is specified as part of an endpoint.</span></span> <span data-ttu-id="94bfb-138">Ten podział adres umożliwia wielu punktów końcowych zdefiniowanych w bardzo ułatwia usługi na hoście.</span><span class="sxs-lookup"><span data-stu-id="94bfb-138">This partitioning of the address allows multiple endpoints to be defined more conveniently for services at a host.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94bfb-139">Właściwości <xref:System.ServiceModel.Description.ServiceDescription> w usłudze aplikacji nie mogą zostać zmodyfikowane subsequent do <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metody <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="94bfb-139">Properties of <xref:System.ServiceModel.Description.ServiceDescription> in the service application must not be modified subsequent to the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method on <xref:System.ServiceModel.ServiceHostBase>.</span></span> <span data-ttu-id="94bfb-140">Niektóre elementy członkowskie, takie jak <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwości i `AddServiceEndpoint` metod <xref:System.ServiceModel.ServiceHostBase> i <xref:System.ServiceModel.ServiceHost>, zgłosić wyjątek, jeśli zmodyfikowane poza tym punktem.</span><span class="sxs-lookup"><span data-stu-id="94bfb-140">Some members, such as the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property and the `AddServiceEndpoint` methods on <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.ServiceHost>, throw an exception if modified past that point.</span></span> <span data-ttu-id="94bfb-141">Inne pozwala na ich modyfikować, ale wynik jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="94bfb-141">Others permit you to modify them, but the result is undefined.</span></span>  
>   
>  <span data-ttu-id="94bfb-142">Podobnie, na komputerze klienckim <xref:System.ServiceModel.Description.ServiceEndpoint> wartości nie mogą zostać zmodyfikowane po wywołaniu <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> na <xref:System.ServiceModel.ChannelFactory>.</span><span class="sxs-lookup"><span data-stu-id="94bfb-142">Similarly, on the client the <xref:System.ServiceModel.Description.ServiceEndpoint> values must not be modified after the call to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> on the <xref:System.ServiceModel.ChannelFactory>.</span></span> <span data-ttu-id="94bfb-143"><xref:System.ServiceModel.ChannelFactory.Credentials%2A> Właściwość zgłasza wyjątek, jeśli zmodyfikować ostatnie tego punktu.</span><span class="sxs-lookup"><span data-stu-id="94bfb-143">The <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property throws an exception if modified past that point.</span></span> <span data-ttu-id="94bfb-144">Inne wartości Opis klienta można zmodyfikować bez błędów, ale wynik jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="94bfb-144">The other client description values can be modified without error, but the result is undefined.</span></span>  
>   
>  <span data-ttu-id="94bfb-145">Czy usługi lub klienta, zalecane jest zmodyfikowanie opis przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="94bfb-145">Whether for the service or client, it is recommended that you modify the description prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
## <a name="defining-endpoints-in-configuration"></a><span data-ttu-id="94bfb-146">Definiowanie punktów końcowych w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="94bfb-146">Defining Endpoints in Configuration</span></span>  
 <span data-ttu-id="94bfb-147">Podczas tworzenia aplikacji, często zachodzi potrzeba Odrocz decyzje przez administratora, który jest wdrożenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="94bfb-147">When creating an application, you often want to defer decisions to the administrator who is deploying the application.</span></span> <span data-ttu-id="94bfb-148">Na przykład często występuje będzie żadnej możliwość określenia, z wyprzedzeniem, jakie usługi, adresów (URI).</span><span class="sxs-lookup"><span data-stu-id="94bfb-148">For example, there is often no way of knowing in advance what a service address (a URI) will be.</span></span> <span data-ttu-id="94bfb-149">Zamiast kodować adresu, jest bardziej pożądane, aby umożliwić administratorowi to zrobić po utworzeniu usługi.</span><span class="sxs-lookup"><span data-stu-id="94bfb-149">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="94bfb-150">Ta elastyczność odbywa się za pośrednictwem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="94bfb-150">This flexibility is accomplished through configuration.</span></span> <span data-ttu-id="94bfb-151">Aby uzyskać więcej informacji, zobacz [Konfigurowanie usług](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="94bfb-151">For details, see [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94bfb-152">Użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z `/config:` *filename*`[,`*filename* `]` przejdź do Szybko twórz plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="94bfb-152">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config:`*filename*`[,`*filename*`]` switch to quickly create configuration files.</span></span>  
  
## <a name="using-default-endpoints"></a><span data-ttu-id="94bfb-153">Przy użyciu domyślnych punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="94bfb-153">Using Default Endpoints</span></span>  
 <span data-ttu-id="94bfb-154">Jeśli nie określono żadnych punktów końcowych w kodzie lub w konfiguracji następnie środowisko wykonawcze zapewnia domyślne punkty końcowe, dodając jeden domyślny punkt końcowy dla każdego adresu podstawowego dla każdej umowy serwisowej implementowane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="94bfb-154">If no endpoints are specified in code or in configuration then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="94bfb-155">Adres podstawowy, można określić w kodzie lub w konfiguracji i domyślne punkty końcowe są dodawane, gdy <xref:System.ServiceModel.ICommunicationObject.Open> jest wywoływana w <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="94bfb-155">The base address can be specified in code or in configuration, and the default endpoints are added when <xref:System.ServiceModel.ICommunicationObject.Open> is called on the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="94bfb-156">W tym przykładzie jest tym samym przykładzie w poprzedniej sekcji, ale ponieważ nie określono żadnych punktów końcowych, domyślne punkty końcowe są dodawane.</span><span class="sxs-lookup"><span data-stu-id="94bfb-156">This example is the same example from the previous section, but since no endpoints are specified, the default endpoints are added.</span></span>  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   Interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   Class Echo : IEcho  
   {  
      Public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      static void Main ()  
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
  
 <span data-ttu-id="94bfb-157">Jeśli punkty końcowe są podane jawnie, nadal można dodać domyślnych punktów końcowych przez wywołanie metody <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> na <xref:System.ServiceModel.ServiceHost> przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="94bfb-157">If endpoints are explicitly provided, the default endpoints can still be added by calling <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> on the <xref:System.ServiceModel.ServiceHost> before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="94bfb-158">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, zobacz [uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="94bfb-158">For more information about default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94bfb-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="94bfb-159">See Also</span></span>  
 [<span data-ttu-id="94bfb-160">Implementowanie kontraktów usług</span><span class="sxs-lookup"><span data-stu-id="94bfb-160">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
