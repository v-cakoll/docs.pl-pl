---
title: 'Instrukcje: Zabezpieczanie usługi za pomocą poświadczeń systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: c47539e0c614992efd74296171034b8091ba3f15
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183324"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a><span data-ttu-id="e8684-102">Instrukcje: Zabezpieczanie usługi za pomocą poświadczeń systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e8684-102">How to: Secure a Service with Windows Credentials</span></span>
<span data-ttu-id="e8684-103">W tym temacie przedstawiono sposób włączania zabezpieczenia transportu usługi Windows Communication Foundation (WCF), który znajduje się w domenie, Windows i jest wywoływana przez klientów w tej samej domenie.</span><span class="sxs-lookup"><span data-stu-id="e8684-103">This topic shows how to enable transport security on a Windows Communication Foundation (WCF) service that resides in a Windows domain and is called by clients in the same domain.</span></span> <span data-ttu-id="e8684-104">Aby uzyskać więcej informacji na temat tego scenariusza, zobacz [zabezpieczenia transportu z uwierzytelnianiem Windows](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e8684-104">For more information about this scenario, see [Transport Security with Windows Authentication](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md).</span></span> <span data-ttu-id="e8684-105">Dla przykładowej aplikacji, zobacz [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="e8684-105">For a sample application, see the [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span>  
  
 <span data-ttu-id="e8684-106">W tym temacie przyjęto założenie, masz istniejący interfejs kontrakt i implementacja już zdefiniowane i dodaje się, że.</span><span class="sxs-lookup"><span data-stu-id="e8684-106">This topic assumes you have an existing contract interface and implementation already defined, and adds on to that.</span></span> <span data-ttu-id="e8684-107">Można także modyfikować istniejące usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="e8684-107">You can also modify an existing service and client.</span></span>  
  
 <span data-ttu-id="e8684-108">Aby zabezpieczyć usługi przy użyciu poświadczeń Windows całkowicie w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e8684-108">You can secure a service with Windows credentials completely in code.</span></span> <span data-ttu-id="e8684-109">Alternatywnie możesz pominąć część kodu przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e8684-109">Alternatively, you can omit some of the code by using a configuration file.</span></span> <span data-ttu-id="e8684-110">W tym temacie pokazano w obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="e8684-110">This topic shows both ways.</span></span> <span data-ttu-id="e8684-111">Upewnij się, że używasz tylko jednej z metod, nie obydwa.</span><span class="sxs-lookup"><span data-stu-id="e8684-111">Be sure you only use one of the ways, not both.</span></span>  
  
 <span data-ttu-id="e8684-112">Pierwsze trzy procedury pokazują, jak zabezpieczyć usługę za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="e8684-112">The first three procedures show how to secure the service using code.</span></span> <span data-ttu-id="e8684-113">Czwarty i piąty procedura pokazuje, jak to zrobić za pomocą pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e8684-113">The fourth and fifth procedure shows how to do it with a configuration file.</span></span>  
  
## <a name="using-code"></a><span data-ttu-id="e8684-114">Przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="e8684-114">Using Code</span></span>  
 <span data-ttu-id="e8684-115">Kompletny kod dla usługi i klienta znajduje się w sekcji przykład, na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e8684-115">The complete code for the service and the client is in the Example section at the end of this topic.</span></span>  
  
 <span data-ttu-id="e8684-116">Pierwsza procedura przeprowadzi tworzenia i konfigurowania <xref:System.ServiceModel.WSHttpBinding> klasy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e8684-116">The first procedure walks through creating and configuring a <xref:System.ServiceModel.WSHttpBinding> class in code.</span></span> <span data-ttu-id="e8684-117">Powiązanie korzysta z protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="e8684-117">The binding uses the HTTP transport.</span></span> <span data-ttu-id="e8684-118">Tego samego powiązania jest używany na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="e8684-118">The same binding is used on the client.</span></span>  
  
#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a><span data-ttu-id="e8684-119">Aby utworzyć WSHttpBinding, który używa poświadczeń Windows i zabezpieczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="e8684-119">To create a WSHttpBinding that uses Windows credentials and message security</span></span>  
  
1.  <span data-ttu-id="e8684-120">Ta procedura kod dodaje się na początku `Run` metody `Test` klasy w kodzie usługi, w sekcji przykład.</span><span class="sxs-lookup"><span data-stu-id="e8684-120">This procedure's code is inserted at the beginning of the `Run` method of the `Test` class in the service code in the Example section.</span></span>  
  
2.  <span data-ttu-id="e8684-121">Utworzenie wystąpienia <xref:System.ServiceModel.WSHttpBinding> klasy.</span><span class="sxs-lookup"><span data-stu-id="e8684-121">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>  
  
3.  <span data-ttu-id="e8684-122">Ustaw <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> właściwość <xref:System.ServiceModel.WSHttpSecurity> klasy <xref:System.ServiceModel.SecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="e8684-122">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property of the <xref:System.ServiceModel.WSHttpSecurity> class to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>  
  
4.  <span data-ttu-id="e8684-123">Ustaw <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> właściwość <xref:System.ServiceModel.MessageSecurityOverHttp> klasy <xref:System.ServiceModel.MessageCredentialType.Windows>.</span><span class="sxs-lookup"><span data-stu-id="e8684-123">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property of the <xref:System.ServiceModel.MessageSecurityOverHttp> class to <xref:System.ServiceModel.MessageCredentialType.Windows>.</span></span>  
  
5.  <span data-ttu-id="e8684-124">Kod do wykonania tej procedury jest następująca:</span><span class="sxs-lookup"><span data-stu-id="e8684-124">The code for this procedure is as follows:</span></span>  
  
     [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
     [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]  
  
### <a name="using-the-binding-in-a-service"></a><span data-ttu-id="e8684-125">Za pomocą tego powiązania w ramach usługi</span><span class="sxs-lookup"><span data-stu-id="e8684-125">Using the Binding in a Service</span></span>  
 <span data-ttu-id="e8684-126">Jest to druga procedura pokazuje, jak stosować powiązanie samodzielnie hostowanej usługi.</span><span class="sxs-lookup"><span data-stu-id="e8684-126">This is the second procedure, which shows how to use the binding in a self-hosted service.</span></span> <span data-ttu-id="e8684-127">Aby uzyskać więcej informacji na temat usługi hostingowe zobacz [usług obsługującego](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="e8684-127">For more information about hosting services see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
##### <a name="to-use-a-binding-in-a-service"></a><span data-ttu-id="e8684-128">Aby użyć powiązania w ramach usługi</span><span class="sxs-lookup"><span data-stu-id="e8684-128">To use a binding in a service</span></span>  
  
1.  <span data-ttu-id="e8684-129">Wstaw kod tej procedury po kodu z poprzedniej procedury.</span><span class="sxs-lookup"><span data-stu-id="e8684-129">Insert this procedure's code after the code from the preceding procedure.</span></span>  
  
2.  <span data-ttu-id="e8684-130">Tworzenie <xref:System.Type> zmiennej o nazwie `contractType` i przypisać jej typ interfejsu (`ICalculator`).</span><span class="sxs-lookup"><span data-stu-id="e8684-130">Create a <xref:System.Type> variable named `contractType` and assign it the type of the interface (`ICalculator`).</span></span> <span data-ttu-id="e8684-131">Podczas korzystania z języka Visual Basic należy używać `GetType` operatora; przy użyciu języka C#, użyj `typeof` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="e8684-131">When using Visual Basic, use the `GetType` operator; when using C#, use the `typeof` keyword.</span></span>  
  
3.  <span data-ttu-id="e8684-132">Utwórz drugi `Type` zmiennej o nazwie `serviceType` i przypisać jej typ kontraktu zaimplementowano (`Calculator`).</span><span class="sxs-lookup"><span data-stu-id="e8684-132">Create a second `Type` variable named `serviceType` and assign it the type of the implemented contract (`Calculator`).</span></span>  
  
4.  <span data-ttu-id="e8684-133">Utwórz wystąpienie obiektu <xref:System.Uri> klasę o nazwie `baseAddress` przy użyciu podstawowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="e8684-133">Create an instance of the <xref:System.Uri> class named `baseAddress` with the base address of the service.</span></span> <span data-ttu-id="e8684-134">Adres podstawowy musi mieć schemat, który odpowiada transportu.</span><span class="sxs-lookup"><span data-stu-id="e8684-134">The base address must have a scheme that matches the transport.</span></span> <span data-ttu-id="e8684-135">W takim przypadku schemat transportu jest protokół HTTP, a adres zawiera specjalne identyfikator (URI) "localhost" i numer portu (8036) oraz adres podstawowego punktu końcowego ("serviceModelSamples /): `http://localhost:8036/serviceModelSamples/`.</span><span class="sxs-lookup"><span data-stu-id="e8684-135">In this case, the transport scheme is HTTP, and the address includes the special Uniform Resource Identifier (URI) "localhost" and a port number (8036) as well as a base endpoint address ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/`.</span></span>  
  
5.  <span data-ttu-id="e8684-136">Utwórz wystąpienie obiektu <xref:System.ServiceModel.ServiceHost> klasy `serviceType` i `baseAddress` zmiennych.</span><span class="sxs-lookup"><span data-stu-id="e8684-136">Create an instance of the <xref:System.ServiceModel.ServiceHost> class with the `serviceType` and `baseAddress` variables.</span></span>  
  
6.  <span data-ttu-id="e8684-137">Dodawanie punktu końcowego do usługi za pomocą `contractType`, powiązanie i nazwę punktu końcowego (secureCalculator).</span><span class="sxs-lookup"><span data-stu-id="e8684-137">Add an endpoint to the service using the `contractType`, binding, and an endpoint name (secureCalculator).</span></span> <span data-ttu-id="e8684-138">Klienta należy złączyć adres podstawowy, a nazwa punktu końcowego za zaufany podczas inicjowania połączenia z usługą.</span><span class="sxs-lookup"><span data-stu-id="e8684-138">A client must concatenate the base address and the endpoint name when initiating a call to the service.</span></span>  
  
7.  <span data-ttu-id="e8684-139">Wywołaj <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metodę, aby uruchomić usługę.</span><span class="sxs-lookup"><span data-stu-id="e8684-139">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service.</span></span> <span data-ttu-id="e8684-140">Kod do wykonania tej procedury jest następujący:</span><span class="sxs-lookup"><span data-stu-id="e8684-140">The code for this procedure is shown here:</span></span>  
  
     [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
     [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]  
  
### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="e8684-141">Za pomocą tego powiązania w kliencie WPF</span><span class="sxs-lookup"><span data-stu-id="e8684-141">Using the Binding in a Client</span></span>  
 <span data-ttu-id="e8684-142">Ta procedura pokazuje sposób generowania serwera proxy, który komunikuje się z usługą.</span><span class="sxs-lookup"><span data-stu-id="e8684-142">This procedure shows how to generate a proxy that communicates with the service.</span></span> <span data-ttu-id="e8684-143">Serwer proxy jest generowany przy użyciu [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) który używa metadanych usługi w celu utworzenia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="e8684-143">The proxy is generated with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) which uses the service metadata to create the proxy.</span></span>  
  
 <span data-ttu-id="e8684-144">Ta procedura powoduje utworzenie wystąpienia <xref:System.ServiceModel.WSHttpBinding> klasy do komunikowania się z usługą, a następnie wywołuje usługę.</span><span class="sxs-lookup"><span data-stu-id="e8684-144">This procedure also creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class to communicate with the service, and then calls the service.</span></span>  
  
 <span data-ttu-id="e8684-145">W tym przykładzie używa tylko kod tworzenia klienta.</span><span class="sxs-lookup"><span data-stu-id="e8684-145">This example uses only code to create the client.</span></span> <span data-ttu-id="e8684-146">Alternatywnie można użyć pliku konfiguracji, który jest pokazany w sekcji następującej procedury.</span><span class="sxs-lookup"><span data-stu-id="e8684-146">As an alternative, you can use a configuration file, which is shown in the section following this procedure.</span></span>  
  
##### <a name="to-use-a-binding-in-a-client-with-code"></a><span data-ttu-id="e8684-147">Aby użyć powiązania w kliencie przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="e8684-147">To use a binding in a client with code</span></span>  
  
1.  <span data-ttu-id="e8684-148">Użyj narzędzia SvcUtil.exe do generowania kodu serwera proxy z metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="e8684-148">Use the SvcUtil.exe tool to generate the proxy code from the service's metadata.</span></span> <span data-ttu-id="e8684-149">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="e8684-149">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="e8684-150">Kod wygenerowany serwer proxy dziedziczy <xref:System.ServiceModel.ClientBase%601> klasy, która gwarantuje, że każdy klient ma niezbędne konstruktorów, metod i właściwości w celu komunikowania się z usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="e8684-150">The generated proxy code inherits from the <xref:System.ServiceModel.ClientBase%601> class, which ensures that every client has the necessary constructors, methods, and properties to communicate with a WCF service.</span></span> <span data-ttu-id="e8684-151">W tym przykładzie zawiera wygenerowanego kodu `CalculatorClient` klasy, która implementuje `ICalculator` interfejsu, włączanie zgodności z kodem usługi.</span><span class="sxs-lookup"><span data-stu-id="e8684-151">In this example, the generated code includes the `CalculatorClient` class, which implements the `ICalculator` interface, enabling compatibility with the service code.</span></span>  
  
2.  <span data-ttu-id="e8684-152">Ta procedura kod dodaje się na początku `Main` metoda program kliencki.</span><span class="sxs-lookup"><span data-stu-id="e8684-152">This procedure's code is inserted at the beginning of the `Main` method of the client program.</span></span>  
  
3.  <span data-ttu-id="e8684-153">Utwórz wystąpienie obiektu <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw jego tryb zabezpieczeń `Message` i typ do poświadczeń klienta `Windows`.</span><span class="sxs-lookup"><span data-stu-id="e8684-153">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to `Message` and its client credential type to `Windows`.</span></span> <span data-ttu-id="e8684-154">Przykład nazwy zmiennej `clientBinding`.</span><span class="sxs-lookup"><span data-stu-id="e8684-154">The example names the variable `clientBinding`.</span></span>  
  
4.  <span data-ttu-id="e8684-155">Utwórz wystąpienie obiektu <xref:System.ServiceModel.EndpointAddress> klasę o nazwie `serviceAddress`.</span><span class="sxs-lookup"><span data-stu-id="e8684-155">Create an instance of the <xref:System.ServiceModel.EndpointAddress> class named `serviceAddress`.</span></span> <span data-ttu-id="e8684-156">Inicjuje wystąpienie przy użyciu podstawowego adresu połączona z wybranej nazwy punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e8684-156">Initialize the instance with the base address concatenated with the endpoint name.</span></span>  
  
5.  <span data-ttu-id="e8684-157">Utwórz wystąpienie wygenerowanej klasy klienta za pomocą `serviceAddress` i `clientBinding` zmiennych.</span><span class="sxs-lookup"><span data-stu-id="e8684-157">Create an instance of the generated client class with the `serviceAddress` and the `clientBinding` variables.</span></span>  
  
6.  <span data-ttu-id="e8684-158">Wywołaj <xref:System.ServiceModel.ClientBase%601.Open%2A> metodzie, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="e8684-158">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>  
  
7.  <span data-ttu-id="e8684-159">Wywoła usługę i wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="e8684-159">Call the service and display the results.</span></span>  
  
     [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
     [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]  
  
## <a name="using-the-configuration-file"></a><span data-ttu-id="e8684-160">Przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e8684-160">Using the Configuration File</span></span>  
 <span data-ttu-id="e8684-161">Zamiast tworzenia powiązania z kodem proceduralnym, można użyć następującego kodu pokazano sekcję powiązania w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e8684-161">Instead of creating the binding with procedural code, you can use the following code shown for the bindings section of the configuration file.</span></span>  
  
 <span data-ttu-id="e8684-162">Jeśli nie masz już usługę zdefiniowane, zobacz [projektowanie i Implementowanie usług](../../../docs/framework/wcf/designing-and-implementing-services.md), i [Konfigurowanie usług](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="e8684-162">If you do not already have a service defined, see [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md), and [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
 <span data-ttu-id="e8684-163">**Uwaga** kod tej konfiguracji jest używany w plikach konfiguracji usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="e8684-163">**Note** This configuration code is used in both the service and client configuration files.</span></span>  
  
#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a><span data-ttu-id="e8684-164">Aby włączyć zabezpieczenia transferu na usługi w domenie Windows przy użyciu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e8684-164">To enable transfer security on a service in a Windows domain using configuration</span></span>  
  
1.  <span data-ttu-id="e8684-165">Dodaj [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu [ \<powiązania >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e8684-165">Add a [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element to the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section of the configuration file.</span></span>  
  
2.  <span data-ttu-id="e8684-166">Dodaj <`binding`> elementu <`WSHttpBinding`> element i ustaw `configurationName` atrybut na wartość, które są odpowiednie dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e8684-166">Add a <`binding`> element to the <`WSHttpBinding`> element and set the `configurationName` attribute to a value appropriate to your application.</span></span>  
  
3.  <span data-ttu-id="e8684-167">Dodaj <`security`> element i ustaw `mode` atrybutu do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e8684-167">Add a <`security`> element and set the `mode` attribute to Message.</span></span>  
  
4.  <span data-ttu-id="e8684-168">Dodaj <`message`> element i ustaw `clientCredentialType` atrybutu Windows.</span><span class="sxs-lookup"><span data-stu-id="e8684-168">Add a <`message`> element and set the `clientCredentialType` attribute to Windows.</span></span>  
  
5.  <span data-ttu-id="e8684-169">W pliku konfiguracji usługi, należy zastąpić `<bindings>` sekcję poniższym kodem.</span><span class="sxs-lookup"><span data-stu-id="e8684-169">In the service's configuration file, replace the `<bindings>` section with the following code.</span></span> <span data-ttu-id="e8684-170">Jeśli nie masz jeszcze pliku konfiguracji usługi, zobacz [przy użyciu powiązania do konfigurowania usług i klientów](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="e8684-170">If you do not already have a service configuration file, see [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>  
  
    ```xml  
    <bindings>  
      <wsHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    ```  
  
### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="e8684-171">Za pomocą tego powiązania w kliencie WPF</span><span class="sxs-lookup"><span data-stu-id="e8684-171">Using the Binding in a Client</span></span>  
 <span data-ttu-id="e8684-172">Ta procedura pokazuje, jak można wygenerować dwa pliki: serwer proxy, który komunikuje się z usługą i pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e8684-172">This procedure shows how to generate two files: a proxy that communicates with the service and a configuration file.</span></span> <span data-ttu-id="e8684-173">Omówiono także zmiany w programie klienckim jest trzeci plik używany przez klienta.</span><span class="sxs-lookup"><span data-stu-id="e8684-173">It also describes changes to the client program, which is the third file used on the client.</span></span>  
  
##### <a name="to-use-a-binding-in-a-client-with-configuration"></a><span data-ttu-id="e8684-174">Aby użyć powiązania w kliencie za pomocą konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e8684-174">To use a binding in a client with configuration</span></span>  
  
1.  <span data-ttu-id="e8684-175">Użyj narzędzia SvcUtil.exe do generowania pliku kodu i konfiguracji serwera proxy z metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="e8684-175">Use the SvcUtil.exe tool to generate the proxy code and configuration file from the service's metadata.</span></span> <span data-ttu-id="e8684-176">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="e8684-176">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="e8684-177">Zastąp [ \<powiązania >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) części pliku konfiguracyjnego wygenerowane z kodu konfiguracji z poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="e8684-177">Replace the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) section of the generated configuration file with the configuration code from the preceding section.</span></span>  
  
3.  <span data-ttu-id="e8684-178">Kod proceduralny zostanie wstawiony na początku `Main` metoda program kliencki.</span><span class="sxs-lookup"><span data-stu-id="e8684-178">Procedural code is inserted at the beginning of the `Main` method of the client program.</span></span>  
  
4.  <span data-ttu-id="e8684-179">Utwórz wystąpienie wygenerowanej klasy klienta przekazując nazwę powiązania w pliku konfiguracyjnym jako parametr wejściowy.</span><span class="sxs-lookup"><span data-stu-id="e8684-179">Create an instance of the generated client class passing the name of the binding in the configuration file as an input parameter.</span></span>  
  
5.  <span data-ttu-id="e8684-180">Wywołaj <xref:System.ServiceModel.ClientBase%601.Open%2A> metodzie, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="e8684-180">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>  
  
6.  <span data-ttu-id="e8684-181">Wywoła usługę i wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="e8684-181">Call the service and display the results.</span></span>  
  
     [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="e8684-182">Przykład</span><span class="sxs-lookup"><span data-stu-id="e8684-182">Example</span></span>  
 [!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]  
  
 [!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)] 
 [!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]      
  
## <a name="see-also"></a><span data-ttu-id="e8684-183">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8684-183">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpBinding>  
 [<span data-ttu-id="e8684-184">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="e8684-184">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="e8684-185">Instrukcje: tworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="e8684-185">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="e8684-186">Zabezpieczanie usług</span><span class="sxs-lookup"><span data-stu-id="e8684-186">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="e8684-187">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="e8684-187">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)
