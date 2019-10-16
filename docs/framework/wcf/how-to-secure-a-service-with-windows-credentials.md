---
title: 'Instrukcje: Zabezpieczanie usługi za pomocą poświadczeń systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: d02e697b23b6c745a59f3c9c37dd9c565f2f710e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320923"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a><span data-ttu-id="63143-102">Instrukcje: Zabezpieczanie usługi za pomocą poświadczeń systemu Windows</span><span class="sxs-lookup"><span data-stu-id="63143-102">How to: Secure a Service with Windows Credentials</span></span>

<span data-ttu-id="63143-103">W tym temacie pokazano, jak włączyć zabezpieczenia transportu w usłudze Windows Communication Foundation (WCF), która znajduje się w domenie systemu Windows i jest wywoływana przez klientów w tej samej domenie.</span><span class="sxs-lookup"><span data-stu-id="63143-103">This topic shows how to enable transport security on a Windows Communication Foundation (WCF) service that resides in a Windows domain and is called by clients in the same domain.</span></span> <span data-ttu-id="63143-104">Aby uzyskać więcej informacji na temat tego scenariusza, zobacz [zabezpieczenia transportu z uwierzytelnianiem systemu Windows](./feature-details/transport-security-with-windows-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="63143-104">For more information about this scenario, see [Transport Security with Windows Authentication](./feature-details/transport-security-with-windows-authentication.md).</span></span> <span data-ttu-id="63143-105">Aby uzyskać przykładową aplikację, zobacz przykład [WSHttpBinding](./samples/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="63143-105">For a sample application, see the [WSHttpBinding](./samples/wshttpbinding.md) sample.</span></span>

<span data-ttu-id="63143-106">W tym temacie przyjęto założenie, że masz już zdefiniowany interfejs kontraktu i implementację, i dodaje do niego.</span><span class="sxs-lookup"><span data-stu-id="63143-106">This topic assumes you have an existing contract interface and implementation already defined, and adds on to that.</span></span> <span data-ttu-id="63143-107">Możesz również zmodyfikować istniejącą usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="63143-107">You can also modify an existing service and client.</span></span>

<span data-ttu-id="63143-108">Usługę można zabezpieczyć za pomocą poświadczeń systemu Windows w kodzie.</span><span class="sxs-lookup"><span data-stu-id="63143-108">You can secure a service with Windows credentials completely in code.</span></span> <span data-ttu-id="63143-109">Alternatywnie można pominąć część kodu przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="63143-109">Alternatively, you can omit some of the code by using a configuration file.</span></span> <span data-ttu-id="63143-110">W tym temacie przedstawiono obie metody.</span><span class="sxs-lookup"><span data-stu-id="63143-110">This topic shows both ways.</span></span> <span data-ttu-id="63143-111">Upewnij się, że używasz tylko jednej z tych metod, a nie obu.</span><span class="sxs-lookup"><span data-stu-id="63143-111">Be sure you only use one of the ways, not both.</span></span>

<span data-ttu-id="63143-112">Pierwsze trzy procedury pokazują, jak zabezpieczyć usługę przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="63143-112">The first three procedures show how to secure the service using code.</span></span> <span data-ttu-id="63143-113">Czwarta i piąta procedura pokazuje, jak to zrobić za pomocą pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="63143-113">The fourth and fifth procedure shows how to do it with a configuration file.</span></span>

## <a name="using-code"></a><span data-ttu-id="63143-114">Korzystanie z kodu</span><span class="sxs-lookup"><span data-stu-id="63143-114">Using Code</span></span>

<span data-ttu-id="63143-115">Kompletny kod dla usługi i klienta znajduje się w sekcji przykład na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="63143-115">The complete code for the service and the client is in the Example section at the end of this topic.</span></span>

<span data-ttu-id="63143-116">Pierwsza procedura zawiera instrukcje tworzenia i konfigurowania klasy <xref:System.ServiceModel.WSHttpBinding> w kodzie.</span><span class="sxs-lookup"><span data-stu-id="63143-116">The first procedure walks through creating and configuring a <xref:System.ServiceModel.WSHttpBinding> class in code.</span></span> <span data-ttu-id="63143-117">Powiązanie używa transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="63143-117">The binding uses the HTTP transport.</span></span> <span data-ttu-id="63143-118">To samo powiązanie jest używane na kliencie.</span><span class="sxs-lookup"><span data-stu-id="63143-118">The same binding is used on the client.</span></span>

#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a><span data-ttu-id="63143-119">Aby utworzyć element WSHttpBinding, który używa poświadczeń systemu Windows i zabezpieczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="63143-119">To create a WSHttpBinding that uses Windows credentials and message security</span></span>

1. <span data-ttu-id="63143-120">Kod tej procedury został wstawiony na początku metody `Run` klasy `Test` w kodzie usługi w sekcji przykład.</span><span class="sxs-lookup"><span data-stu-id="63143-120">This procedure's code is inserted at the beginning of the `Run` method of the `Test` class in the service code in the Example section.</span></span>

2. <span data-ttu-id="63143-121">Utworzenie wystąpienia <xref:System.ServiceModel.WSHttpBinding> klasy.</span><span class="sxs-lookup"><span data-stu-id="63143-121">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

3. <span data-ttu-id="63143-122">Ustaw właściwość <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> klasy <xref:System.ServiceModel.WSHttpSecurity> na <xref:System.ServiceModel.SecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="63143-122">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property of the <xref:System.ServiceModel.WSHttpSecurity> class to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>

4. <span data-ttu-id="63143-123">Ustaw właściwość <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> klasy <xref:System.ServiceModel.MessageSecurityOverHttp> na <xref:System.ServiceModel.MessageCredentialType.Windows>.</span><span class="sxs-lookup"><span data-stu-id="63143-123">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property of the <xref:System.ServiceModel.MessageSecurityOverHttp> class to <xref:System.ServiceModel.MessageCredentialType.Windows>.</span></span>

5. <span data-ttu-id="63143-124">Kod tej procedury jest następujący:</span><span class="sxs-lookup"><span data-stu-id="63143-124">The code for this procedure is as follows:</span></span>

    [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
    [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]

### <a name="using-the-binding-in-a-service"></a><span data-ttu-id="63143-125">Korzystanie z powiązania w usłudze</span><span class="sxs-lookup"><span data-stu-id="63143-125">Using the Binding in a Service</span></span>

<span data-ttu-id="63143-126">Jest to druga procedura, która pokazuje, jak używać powiązania w usłudze samodzielnej.</span><span class="sxs-lookup"><span data-stu-id="63143-126">This is the second procedure, which shows how to use the binding in a self-hosted service.</span></span> <span data-ttu-id="63143-127">Aby uzyskać więcej informacji na temat usług hostingu, zobacz [usługi hostingu](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="63143-127">For more information about hosting services see [Hosting Services](hosting-services.md).</span></span>

##### <a name="to-use-a-binding-in-a-service"></a><span data-ttu-id="63143-128">Aby użyć powiązania w usłudze</span><span class="sxs-lookup"><span data-stu-id="63143-128">To use a binding in a service</span></span>

1. <span data-ttu-id="63143-129">Wstaw kod tej procedury po kodzie z poprzedniej procedury.</span><span class="sxs-lookup"><span data-stu-id="63143-129">Insert this procedure's code after the code from the preceding procedure.</span></span>

2. <span data-ttu-id="63143-130">Utwórz zmienną <xref:System.Type> o nazwie `contractType` i przypisz ją do typu interfejsu (`ICalculator`).</span><span class="sxs-lookup"><span data-stu-id="63143-130">Create a <xref:System.Type> variable named `contractType` and assign it the type of the interface (`ICalculator`).</span></span> <span data-ttu-id="63143-131">Korzystając z Visual Basic, należy użyć operatora `GetType`; Korzystając C#z programu, użyj słowa kluczowego `typeof`.</span><span class="sxs-lookup"><span data-stu-id="63143-131">When using Visual Basic, use the `GetType` operator; when using C#, use the `typeof` keyword.</span></span>

3. <span data-ttu-id="63143-132">Utwórz drugą zmienną <xref:System.Type> o nazwie `serviceType` i przypisz ją do typu wdrożonego kontraktu (`Calculator`).</span><span class="sxs-lookup"><span data-stu-id="63143-132">Create a second <xref:System.Type> variable named `serviceType` and assign it the type of the implemented contract (`Calculator`).</span></span>

4. <span data-ttu-id="63143-133">Utwórz wystąpienie klasy <xref:System.Uri> o nazwie `baseAddress` z adresem podstawowym usługi.</span><span class="sxs-lookup"><span data-stu-id="63143-133">Create an instance of the <xref:System.Uri> class named `baseAddress` with the base address of the service.</span></span> <span data-ttu-id="63143-134">Adres podstawowy musi mieć schemat zgodny z transportem.</span><span class="sxs-lookup"><span data-stu-id="63143-134">The base address must have a scheme that matches the transport.</span></span> <span data-ttu-id="63143-135">W tym przypadku schemat transportu to HTTP, a adres zawiera specjalny Uniform Resource Identifier (URI) "localhost" i numer portu (8036), a także podstawowy adres punktu końcowego ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/`.</span><span class="sxs-lookup"><span data-stu-id="63143-135">In this case, the transport scheme is HTTP, and the address includes the special Uniform Resource Identifier (URI) "localhost" and a port number (8036) as well as a base endpoint address ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/`.</span></span>

5. <span data-ttu-id="63143-136">Utwórz wystąpienie klasy <xref:System.ServiceModel.ServiceHost> ze zmiennymi `serviceType` i `baseAddress`.</span><span class="sxs-lookup"><span data-stu-id="63143-136">Create an instance of the <xref:System.ServiceModel.ServiceHost> class with the `serviceType` and `baseAddress` variables.</span></span>

6. <span data-ttu-id="63143-137">Dodaj punkt końcowy do usługi przy użyciu `contractType`, powiązania i nazwy punktu końcowego (secureCalculator).</span><span class="sxs-lookup"><span data-stu-id="63143-137">Add an endpoint to the service using the `contractType`, binding, and an endpoint name (secureCalculator).</span></span> <span data-ttu-id="63143-138">Po zainicjowaniu wywołania usługi Klient musi połączyć adres podstawowy i nazwę punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="63143-138">A client must concatenate the base address and the endpoint name when initiating a call to the service.</span></span>

7. <span data-ttu-id="63143-139">Wywołaj metodę <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>, aby uruchomić usługę.</span><span class="sxs-lookup"><span data-stu-id="63143-139">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service.</span></span> <span data-ttu-id="63143-140">Kod tej procedury jest przedstawiony tutaj:</span><span class="sxs-lookup"><span data-stu-id="63143-140">The code for this procedure is shown here:</span></span>

    [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
    [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="63143-141">Korzystanie z powiązania w kliencie</span><span class="sxs-lookup"><span data-stu-id="63143-141">Using the Binding in a Client</span></span>

<span data-ttu-id="63143-142">Ta procedura pokazuje, jak wygenerować serwer proxy, który komunikuje się z usługą.</span><span class="sxs-lookup"><span data-stu-id="63143-142">This procedure shows how to generate a proxy that communicates with the service.</span></span> <span data-ttu-id="63143-143">Serwer proxy jest generowany przy użyciu [Narzędzia do obsługi metadanych ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) , które używa metadanych usługi do utworzenia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="63143-143">The proxy is generated with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) which uses the service metadata to create the proxy.</span></span>

<span data-ttu-id="63143-144">Ta procedura powoduje także utworzenie wystąpienia klasy <xref:System.ServiceModel.WSHttpBinding> w celu komunikacji z usługą, a następnie wywołanie usługi.</span><span class="sxs-lookup"><span data-stu-id="63143-144">This procedure also creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class to communicate with the service, and then calls the service.</span></span>

<span data-ttu-id="63143-145">Ten przykład używa tylko kodu do utworzenia klienta.</span><span class="sxs-lookup"><span data-stu-id="63143-145">This example uses only code to create the client.</span></span> <span data-ttu-id="63143-146">Alternatywnie można użyć pliku konfiguracji, który jest przedstawiony w sekcji opisanej w poniższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="63143-146">As an alternative, you can use a configuration file, which is shown in the section following this procedure.</span></span>

#### <a name="to-use-a-binding-in-a-client-with-code"></a><span data-ttu-id="63143-147">Aby użyć powiązania w kliencie z kodem</span><span class="sxs-lookup"><span data-stu-id="63143-147">To use a binding in a client with code</span></span>

1. <span data-ttu-id="63143-148">Użyj narzędzia SvcUtil. exe, aby wygenerować kod serwera proxy z metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="63143-148">Use the SvcUtil.exe tool to generate the proxy code from the service's metadata.</span></span> <span data-ttu-id="63143-149">Aby uzyskać więcej informacji, zobacz [How to: Create a Client](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="63143-149">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="63143-150">Wygenerowany kod serwera proxy dziedziczy z klasy <xref:System.ServiceModel.ClientBase%601>, co zapewnia, że każdy klient ma wymagane konstruktory, metody i właściwości do komunikowania się z usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="63143-150">The generated proxy code inherits from the <xref:System.ServiceModel.ClientBase%601> class, which ensures that every client has the necessary constructors, methods, and properties to communicate with a WCF service.</span></span> <span data-ttu-id="63143-151">W tym przykładzie wygenerowany kod zawiera klasę `CalculatorClient`, która implementuje interfejs `ICalculator`, co umożliwia zgodność z kodem usługi.</span><span class="sxs-lookup"><span data-stu-id="63143-151">In this example, the generated code includes the `CalculatorClient` class, which implements the `ICalculator` interface, enabling compatibility with the service code.</span></span>

2. <span data-ttu-id="63143-152">Kod tej procedury został wstawiony na początku metody `Main` programu klienckiego.</span><span class="sxs-lookup"><span data-stu-id="63143-152">This procedure's code is inserted at the beginning of the `Main` method of the client program.</span></span>

3. <span data-ttu-id="63143-153">Utwórz wystąpienie klasy <xref:System.ServiceModel.WSHttpBinding> i ustaw jego tryb zabezpieczeń na `Message` i jego typ poświadczeń klienta na `Windows`.</span><span class="sxs-lookup"><span data-stu-id="63143-153">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to `Message` and its client credential type to `Windows`.</span></span> <span data-ttu-id="63143-154">Przykład nazwy zmiennej `clientBinding`.</span><span class="sxs-lookup"><span data-stu-id="63143-154">The example names the variable `clientBinding`.</span></span>

4. <span data-ttu-id="63143-155">Utwórz wystąpienie klasy <xref:System.ServiceModel.EndpointAddress> o nazwie `serviceAddress`.</span><span class="sxs-lookup"><span data-stu-id="63143-155">Create an instance of the <xref:System.ServiceModel.EndpointAddress> class named `serviceAddress`.</span></span> <span data-ttu-id="63143-156">Zainicjuj wystąpienie z adresem podstawowym połączonym z nazwą punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="63143-156">Initialize the instance with the base address concatenated with the endpoint name.</span></span>

5. <span data-ttu-id="63143-157">Utwórz wystąpienie wygenerowanej klasy klienta z `serviceAddress` i `clientBinding` zmiennych.</span><span class="sxs-lookup"><span data-stu-id="63143-157">Create an instance of the generated client class with the `serviceAddress` and the `clientBinding` variables.</span></span>

6. <span data-ttu-id="63143-158">Wywołaj metodę <xref:System.ServiceModel.ClientBase%601.Open%2A>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="63143-158">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

7. <span data-ttu-id="63143-159">Wywołaj usługę i Wyświetl wyniki.</span><span class="sxs-lookup"><span data-stu-id="63143-159">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
    [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]

## <a name="using-the-configuration-file"></a><span data-ttu-id="63143-160">Korzystanie z pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="63143-160">Using the Configuration File</span></span>

<span data-ttu-id="63143-161">Zamiast tworzyć powiązania z kodem proceduralnym, można użyć poniższego kodu dla sekcji powiązania w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="63143-161">Instead of creating the binding with procedural code, you can use the following code shown for the bindings section of the configuration file.</span></span>

<span data-ttu-id="63143-162">Jeśli nie masz jeszcze zdefiniowanej usługi, zobacz [projektowanie i implementowanie usług](designing-and-implementing-services.md)oraz [Konfigurowanie usług](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="63143-162">If you do not already have a service defined, see [Designing and Implementing Services](designing-and-implementing-services.md), and [Configuring Services](configuring-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="63143-163">Ten kod konfiguracji jest używany zarówno w plikach konfiguracji usługi, jak i klienta.</span><span class="sxs-lookup"><span data-stu-id="63143-163">This configuration code is used in both the service and client configuration files.</span></span>

#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a><span data-ttu-id="63143-164">Aby włączyć zabezpieczenia transferu dla usługi w domenie systemu Windows przy użyciu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="63143-164">To enable transfer security on a service in a Windows domain using configuration</span></span>

1. <span data-ttu-id="63143-165">Dodaj element [\<wsHttpBinding >](../configure-apps/file-schema/wcf/wshttpbinding.md) do sekcji [> elementu \<bindings](../configure-apps/file-schema/wcf/bindings.md) w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="63143-165">Add a [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element to the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element section of the configuration file.</span></span>

2. <span data-ttu-id="63143-166">Dodaj element < `binding` > do elementu < `WSHttpBinding` > i ustaw dla atrybutu `configurationName` wartość odpowiednią dla Twojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="63143-166">Add a <`binding`> element to the <`WSHttpBinding`> element and set the `configurationName` attribute to a value appropriate to your application.</span></span>

3. <span data-ttu-id="63143-167">Dodaj element < `security` > i ustaw dla niego atrybut `mode`.</span><span class="sxs-lookup"><span data-stu-id="63143-167">Add a <`security`> element and set the `mode` attribute to Message.</span></span>

4. <span data-ttu-id="63143-168">Dodaj element < `message` > i ustaw atrybut `clientCredentialType` w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="63143-168">Add a <`message`> element and set the `clientCredentialType` attribute to Windows.</span></span>

5. <span data-ttu-id="63143-169">W pliku konfiguracyjnym usługi Zastąp sekcję `<bindings>` następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="63143-169">In the service's configuration file, replace the `<bindings>` section with the following code.</span></span> <span data-ttu-id="63143-170">Jeśli nie masz jeszcze pliku konfiguracji usługi, zobacz temat [Używanie powiązań do konfigurowania usług i klientów](using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="63143-170">If you do not already have a service configuration file, see [Using Bindings to Configure Services and Clients](using-bindings-to-configure-services-and-clients.md).</span></span>

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

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="63143-171">Korzystanie z powiązania w kliencie</span><span class="sxs-lookup"><span data-stu-id="63143-171">Using the Binding in a Client</span></span>

<span data-ttu-id="63143-172">Ta procedura pokazuje, jak generować dwa pliki: serwer proxy, który komunikuje się z usługą i plikiem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="63143-172">This procedure shows how to generate two files: a proxy that communicates with the service and a configuration file.</span></span> <span data-ttu-id="63143-173">Opisano w nim również zmiany programu klienckiego, czyli trzeci plik używany na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="63143-173">It also describes changes to the client program, which is the third file used on the client.</span></span>

#### <a name="to-use-a-binding-in-a-client-with-configuration"></a><span data-ttu-id="63143-174">Aby użyć powiązania w kliencie z konfiguracją</span><span class="sxs-lookup"><span data-stu-id="63143-174">To use a binding in a client with configuration</span></span>

1. <span data-ttu-id="63143-175">Użyj narzędzia SvcUtil. exe, aby wygenerować kod i plik konfiguracji serwera proxy z metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="63143-175">Use the SvcUtil.exe tool to generate the proxy code and configuration file from the service's metadata.</span></span> <span data-ttu-id="63143-176">Aby uzyskać więcej informacji, zobacz [How to: Create a Client](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="63143-176">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span>

2. <span data-ttu-id="63143-177">Zastąp sekcję [\<bindings >](../configure-apps/file-schema/wcf/bindings.md) w wygenerowanym pliku konfiguracji kodem konfiguracji z poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="63143-177">Replace the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) section of the generated configuration file with the configuration code from the preceding section.</span></span>

3. <span data-ttu-id="63143-178">Kod proceduralny jest wstawiany na początku metody `Main` programu klienckiego.</span><span class="sxs-lookup"><span data-stu-id="63143-178">Procedural code is inserted at the beginning of the `Main` method of the client program.</span></span>

4. <span data-ttu-id="63143-179">Utwórz wystąpienie wygenerowanej klasy klienta przekazujące nazwę powiązania w pliku konfiguracji jako parametr wejściowy.</span><span class="sxs-lookup"><span data-stu-id="63143-179">Create an instance of the generated client class passing the name of the binding in the configuration file as an input parameter.</span></span>

5. <span data-ttu-id="63143-180">Wywołaj metodę <xref:System.ServiceModel.ClientBase%601.Open%2A>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="63143-180">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

6. <span data-ttu-id="63143-181">Wywołaj usługę i Wyświetl wyniki.</span><span class="sxs-lookup"><span data-stu-id="63143-181">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]

## <a name="example"></a><span data-ttu-id="63143-182">Przykład</span><span class="sxs-lookup"><span data-stu-id="63143-182">Example</span></span>

[!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]

[!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)]
[!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]

## <a name="see-also"></a><span data-ttu-id="63143-183">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63143-183">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- [<span data-ttu-id="63143-184">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="63143-184">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="63143-185">Instrukcje: tworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="63143-185">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [<span data-ttu-id="63143-186">Zabezpieczanie usług</span><span class="sxs-lookup"><span data-stu-id="63143-186">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="63143-187">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="63143-187">Security Overview</span></span>](./feature-details/security-overview.md)
