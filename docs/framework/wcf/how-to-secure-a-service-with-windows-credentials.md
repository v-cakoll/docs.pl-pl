---
title: 'Instrukcje: Zabezpieczanie usługi za pomocą poświadczeń systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: 19ac9da94ce6e405632293a7d569698c9d866bef
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856063"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a><span data-ttu-id="8037f-102">Instrukcje: Zabezpieczanie usługi za pomocą poświadczeń systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8037f-102">How to: Secure a Service with Windows Credentials</span></span>

<span data-ttu-id="8037f-103">W tym temacie pokazano, jak włączyć zabezpieczenia transportu w usłudze Windows Communication Foundation (WCF), która znajduje się w domenie systemu Windows i jest wywoływana przez klientów w tej samej domenie.</span><span class="sxs-lookup"><span data-stu-id="8037f-103">This topic shows how to enable transport security on a Windows Communication Foundation (WCF) service that resides in a Windows domain and is called by clients in the same domain.</span></span> <span data-ttu-id="8037f-104">Aby uzyskać więcej informacji na temat tego scenariusza, zobacz [zabezpieczenia transportu z uwierzytelnianiem systemu Windows](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8037f-104">For more information about this scenario, see [Transport Security with Windows Authentication](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md).</span></span> <span data-ttu-id="8037f-105">Aby uzyskać przykładową aplikację, zobacz przykład [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="8037f-105">For a sample application, see the [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span>

<span data-ttu-id="8037f-106">W tym temacie przyjęto założenie, że masz już zdefiniowany interfejs kontraktu i implementację, i dodaje do niego.</span><span class="sxs-lookup"><span data-stu-id="8037f-106">This topic assumes you have an existing contract interface and implementation already defined, and adds on to that.</span></span> <span data-ttu-id="8037f-107">Możesz również zmodyfikować istniejącą usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="8037f-107">You can also modify an existing service and client.</span></span>

<span data-ttu-id="8037f-108">Usługę można zabezpieczyć za pomocą poświadczeń systemu Windows w kodzie.</span><span class="sxs-lookup"><span data-stu-id="8037f-108">You can secure a service with Windows credentials completely in code.</span></span> <span data-ttu-id="8037f-109">Alternatywnie można pominąć część kodu przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8037f-109">Alternatively, you can omit some of the code by using a configuration file.</span></span> <span data-ttu-id="8037f-110">W tym temacie przedstawiono obie metody.</span><span class="sxs-lookup"><span data-stu-id="8037f-110">This topic shows both ways.</span></span> <span data-ttu-id="8037f-111">Upewnij się, że używasz tylko jednej z tych metod, a nie obu.</span><span class="sxs-lookup"><span data-stu-id="8037f-111">Be sure you only use one of the ways, not both.</span></span>

<span data-ttu-id="8037f-112">Pierwsze trzy procedury pokazują, jak zabezpieczyć usługę przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="8037f-112">The first three procedures show how to secure the service using code.</span></span> <span data-ttu-id="8037f-113">Czwarta i piąta procedura pokazuje, jak to zrobić za pomocą pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8037f-113">The fourth and fifth procedure shows how to do it with a configuration file.</span></span>

## <a name="using-code"></a><span data-ttu-id="8037f-114">Korzystanie z kodu</span><span class="sxs-lookup"><span data-stu-id="8037f-114">Using Code</span></span>

<span data-ttu-id="8037f-115">Kompletny kod dla usługi i klienta znajduje się w sekcji przykład na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="8037f-115">The complete code for the service and the client is in the Example section at the end of this topic.</span></span>

<span data-ttu-id="8037f-116">Pierwsza procedura zawiera instrukcje tworzenia i konfigurowania <xref:System.ServiceModel.WSHttpBinding> klasy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="8037f-116">The first procedure walks through creating and configuring a <xref:System.ServiceModel.WSHttpBinding> class in code.</span></span> <span data-ttu-id="8037f-117">Powiązanie używa transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="8037f-117">The binding uses the HTTP transport.</span></span> <span data-ttu-id="8037f-118">To samo powiązanie jest używane na kliencie.</span><span class="sxs-lookup"><span data-stu-id="8037f-118">The same binding is used on the client.</span></span>

#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a><span data-ttu-id="8037f-119">Aby utworzyć element WSHttpBinding, który używa poświadczeń systemu Windows i zabezpieczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="8037f-119">To create a WSHttpBinding that uses Windows credentials and message security</span></span>

1. <span data-ttu-id="8037f-120">Kod tej procedury jest wstawiany na początku `Run` metody `Test` klasy w kodzie usługi w sekcji przykład.</span><span class="sxs-lookup"><span data-stu-id="8037f-120">This procedure's code is inserted at the beginning of the `Run` method of the `Test` class in the service code in the Example section.</span></span>

2. <span data-ttu-id="8037f-121">Utworzenie wystąpienia <xref:System.ServiceModel.WSHttpBinding> klasy.</span><span class="sxs-lookup"><span data-stu-id="8037f-121">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

3. <span data-ttu-id="8037f-122"><xref:System.ServiceModel.WSHttpSecurity.Mode%2A> Ustaw właściwość <xref:System.ServiceModel.WSHttpSecurity> klasy na <xref:System.ServiceModel.SecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="8037f-122">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property of the <xref:System.ServiceModel.WSHttpSecurity> class to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>

4. <span data-ttu-id="8037f-123"><xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> Ustaw właściwość <xref:System.ServiceModel.MessageSecurityOverHttp> klasy na <xref:System.ServiceModel.MessageCredentialType.Windows>.</span><span class="sxs-lookup"><span data-stu-id="8037f-123">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property of the <xref:System.ServiceModel.MessageSecurityOverHttp> class to <xref:System.ServiceModel.MessageCredentialType.Windows>.</span></span>

5. <span data-ttu-id="8037f-124">Kod tej procedury jest następujący:</span><span class="sxs-lookup"><span data-stu-id="8037f-124">The code for this procedure is as follows:</span></span>

    [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
    [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]

### <a name="using-the-binding-in-a-service"></a><span data-ttu-id="8037f-125">Korzystanie z powiązania w usłudze</span><span class="sxs-lookup"><span data-stu-id="8037f-125">Using the Binding in a Service</span></span>

<span data-ttu-id="8037f-126">Jest to druga procedura, która pokazuje, jak używać powiązania w usłudze samodzielnej.</span><span class="sxs-lookup"><span data-stu-id="8037f-126">This is the second procedure, which shows how to use the binding in a self-hosted service.</span></span> <span data-ttu-id="8037f-127">Aby uzyskać więcej informacji na temat usług hostingu, zobacz [usługi hostingu](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="8037f-127">For more information about hosting services see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>

##### <a name="to-use-a-binding-in-a-service"></a><span data-ttu-id="8037f-128">Aby użyć powiązania w usłudze</span><span class="sxs-lookup"><span data-stu-id="8037f-128">To use a binding in a service</span></span>

1. <span data-ttu-id="8037f-129">Wstaw kod tej procedury po kodzie z poprzedniej procedury.</span><span class="sxs-lookup"><span data-stu-id="8037f-129">Insert this procedure's code after the code from the preceding procedure.</span></span>

2. <span data-ttu-id="8037f-130">Utwórz zmienną o nazwie `contractType` i przypisz ją do typu interfejsu (`ICalculator`). <xref:System.Type></span><span class="sxs-lookup"><span data-stu-id="8037f-130">Create a <xref:System.Type> variable named `contractType` and assign it the type of the interface (`ICalculator`).</span></span> <span data-ttu-id="8037f-131">Korzystając z Visual Basic, użyj `GetType` operatora; w przypadku używania C#, użyj `typeof` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="8037f-131">When using Visual Basic, use the `GetType` operator; when using C#, use the `typeof` keyword.</span></span>

3. <span data-ttu-id="8037f-132">Utwórz drugą <xref:System.Type> zmienną o nazwie `serviceType` i przypisz ją do typu zaimplementowanego kontraktu (`Calculator`).</span><span class="sxs-lookup"><span data-stu-id="8037f-132">Create a second <xref:System.Type> variable named `serviceType` and assign it the type of the implemented contract (`Calculator`).</span></span>

4. <span data-ttu-id="8037f-133">Utwórz wystąpienie <xref:System.Uri> klasy o nazwie `baseAddress` z adresem podstawowym usługi.</span><span class="sxs-lookup"><span data-stu-id="8037f-133">Create an instance of the <xref:System.Uri> class named `baseAddress` with the base address of the service.</span></span> <span data-ttu-id="8037f-134">Adres podstawowy musi mieć schemat zgodny z transportem.</span><span class="sxs-lookup"><span data-stu-id="8037f-134">The base address must have a scheme that matches the transport.</span></span> <span data-ttu-id="8037f-135">W tym przypadku schemat transportu to HTTP, a adres zawiera specjalny Uniform Resource Identifier (URI) "localhost" i numer portu (8036), a także podstawowy adres punktu końcowego ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/`.</span><span class="sxs-lookup"><span data-stu-id="8037f-135">In this case, the transport scheme is HTTP, and the address includes the special Uniform Resource Identifier (URI) "localhost" and a port number (8036) as well as a base endpoint address ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/`.</span></span>

5. <span data-ttu-id="8037f-136">Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> klasy `serviceType` za pomocą zmiennych i `baseAddress` .</span><span class="sxs-lookup"><span data-stu-id="8037f-136">Create an instance of the <xref:System.ServiceModel.ServiceHost> class with the `serviceType` and `baseAddress` variables.</span></span>

6. <span data-ttu-id="8037f-137">Dodaj punkt końcowy do usługi przy użyciu `contractType`elementu, powiązania i nazwy punktu końcowego (secureCalculator).</span><span class="sxs-lookup"><span data-stu-id="8037f-137">Add an endpoint to the service using the `contractType`, binding, and an endpoint name (secureCalculator).</span></span> <span data-ttu-id="8037f-138">Po zainicjowaniu wywołania usługi Klient musi połączyć adres podstawowy i nazwę punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="8037f-138">A client must concatenate the base address and the endpoint name when initiating a call to the service.</span></span>

7. <span data-ttu-id="8037f-139">Wywołaj <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metodę, aby uruchomić usługę.</span><span class="sxs-lookup"><span data-stu-id="8037f-139">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service.</span></span> <span data-ttu-id="8037f-140">Kod tej procedury jest przedstawiony tutaj:</span><span class="sxs-lookup"><span data-stu-id="8037f-140">The code for this procedure is shown here:</span></span>

    [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
    [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="8037f-141">Korzystanie z powiązania w kliencie</span><span class="sxs-lookup"><span data-stu-id="8037f-141">Using the Binding in a Client</span></span>

<span data-ttu-id="8037f-142">Ta procedura pokazuje, jak wygenerować serwer proxy, który komunikuje się z usługą.</span><span class="sxs-lookup"><span data-stu-id="8037f-142">This procedure shows how to generate a proxy that communicates with the service.</span></span> <span data-ttu-id="8037f-143">Serwer proxy jest generowany przy użyciu [Narzędzia do obsługi metadanych ServiceModel (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) , które używa metadanych usługi do utworzenia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="8037f-143">The proxy is generated with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) which uses the service metadata to create the proxy.</span></span>

<span data-ttu-id="8037f-144">Ta procedura powoduje także utworzenie wystąpienia <xref:System.ServiceModel.WSHttpBinding> klasy w celu komunikacji z usługą, a następnie wywołanie usługi.</span><span class="sxs-lookup"><span data-stu-id="8037f-144">This procedure also creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class to communicate with the service, and then calls the service.</span></span>

<span data-ttu-id="8037f-145">Ten przykład używa tylko kodu do utworzenia klienta.</span><span class="sxs-lookup"><span data-stu-id="8037f-145">This example uses only code to create the client.</span></span> <span data-ttu-id="8037f-146">Alternatywnie można użyć pliku konfiguracji, który jest przedstawiony w sekcji opisanej w poniższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="8037f-146">As an alternative, you can use a configuration file, which is shown in the section following this procedure.</span></span>

##### <a name="to-use-a-binding-in-a-client-with-code"></a><span data-ttu-id="8037f-147">Aby użyć powiązania w kliencie z kodem</span><span class="sxs-lookup"><span data-stu-id="8037f-147">To use a binding in a client with code</span></span>

1. <span data-ttu-id="8037f-148">Użyj narzędzia SvcUtil. exe, aby wygenerować kod serwera proxy z metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="8037f-148">Use the SvcUtil.exe tool to generate the proxy code from the service's metadata.</span></span> <span data-ttu-id="8037f-149">Aby uzyskać więcej informacji, zobacz [jak: Utwórz klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="8037f-149">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="8037f-150">Wygenerowany kod serwera proxy dziedziczy z <xref:System.ServiceModel.ClientBase%601> klasy, co zapewnia, że każdy klient ma wymagane konstruktory, metody i właściwości do komunikowania się z usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="8037f-150">The generated proxy code inherits from the <xref:System.ServiceModel.ClientBase%601> class, which ensures that every client has the necessary constructors, methods, and properties to communicate with a WCF service.</span></span> <span data-ttu-id="8037f-151">W tym przykładzie wygenerowany kod zawiera `CalculatorClient` klasę, która `ICalculator` implementuje interfejs, umożliwiając zgodność z kodem usługi.</span><span class="sxs-lookup"><span data-stu-id="8037f-151">In this example, the generated code includes the `CalculatorClient` class, which implements the `ICalculator` interface, enabling compatibility with the service code.</span></span>

2. <span data-ttu-id="8037f-152">Kod tej procedury jest wstawiany na początku `Main` metody programu klienckiego.</span><span class="sxs-lookup"><span data-stu-id="8037f-152">This procedure's code is inserted at the beginning of the `Main` method of the client program.</span></span>

3. <span data-ttu-id="8037f-153">Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw jego tryb zabezpieczeń na `Message` i jego typ poświadczeń klienta na `Windows`.</span><span class="sxs-lookup"><span data-stu-id="8037f-153">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to `Message` and its client credential type to `Windows`.</span></span> <span data-ttu-id="8037f-154">Przykład nazwy zmiennej `clientBinding`.</span><span class="sxs-lookup"><span data-stu-id="8037f-154">The example names the variable `clientBinding`.</span></span>

4. <span data-ttu-id="8037f-155">Utwórz wystąpienie <xref:System.ServiceModel.EndpointAddress> klasy o nazwie `serviceAddress`.</span><span class="sxs-lookup"><span data-stu-id="8037f-155">Create an instance of the <xref:System.ServiceModel.EndpointAddress> class named `serviceAddress`.</span></span> <span data-ttu-id="8037f-156">Zainicjuj wystąpienie z adresem podstawowym połączonym z nazwą punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="8037f-156">Initialize the instance with the base address concatenated with the endpoint name.</span></span>

5. <span data-ttu-id="8037f-157">Utwórz wystąpienie wygenerowanej klasy klienta przy użyciu `serviceAddress` `clientBinding` i zmiennych.</span><span class="sxs-lookup"><span data-stu-id="8037f-157">Create an instance of the generated client class with the `serviceAddress` and the `clientBinding` variables.</span></span>

6. <span data-ttu-id="8037f-158">Wywołaj <xref:System.ServiceModel.ClientBase%601.Open%2A> metodę, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="8037f-158">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

7. <span data-ttu-id="8037f-159">Wywołaj usługę i Wyświetl wyniki.</span><span class="sxs-lookup"><span data-stu-id="8037f-159">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
    [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]

## <a name="using-the-configuration-file"></a><span data-ttu-id="8037f-160">Korzystanie z pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8037f-160">Using the Configuration File</span></span>

<span data-ttu-id="8037f-161">Zamiast tworzyć powiązania z kodem proceduralnym, można użyć poniższego kodu dla sekcji powiązania w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8037f-161">Instead of creating the binding with procedural code, you can use the following code shown for the bindings section of the configuration file.</span></span>

<span data-ttu-id="8037f-162">Jeśli nie masz jeszcze zdefiniowanej usługi, zobacz [projektowanie i implementowanie usług](../../../docs/framework/wcf/designing-and-implementing-services.md)oraz [Konfigurowanie usług](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="8037f-162">If you do not already have a service defined, see [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md), and [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8037f-163">Ten kod konfiguracji jest używany zarówno w plikach konfiguracji usługi, jak i klienta.</span><span class="sxs-lookup"><span data-stu-id="8037f-163">This configuration code is used in both the service and client configuration files.</span></span>

#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a><span data-ttu-id="8037f-164">Aby włączyć zabezpieczenia transferu dla usługi w domenie systemu Windows przy użyciu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8037f-164">To enable transfer security on a service in a Windows domain using configuration</span></span>

1. <span data-ttu-id="8037f-165">Dodaj element [> WSHttpBindingdosekcjipowiązania>elementuwplikukonfiguracji.\<](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) [ \<](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="8037f-165">Add a [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element to the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section of the configuration file.</span></span>

2. <span data-ttu-id="8037f-166">Dodaj element >`binding`< do elementu <`WSHttpBinding` `configurationName` > i ustaw dla atrybutu wartość odpowiednią dla Twojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8037f-166">Add a <`binding`> element to the <`WSHttpBinding`> element and set the `configurationName` attribute to a value appropriate to your application.</span></span>

3. <span data-ttu-id="8037f-167">Dodaj element >`security`< i ustaw dla niego `mode` atrybut Message.</span><span class="sxs-lookup"><span data-stu-id="8037f-167">Add a <`security`> element and set the `mode` attribute to Message.</span></span>

4. <span data-ttu-id="8037f-168">Dodaj element >`message`< i `clientCredentialType` ustaw atrybut na Windows.</span><span class="sxs-lookup"><span data-stu-id="8037f-168">Add a <`message`> element and set the `clientCredentialType` attribute to Windows.</span></span>

5. <span data-ttu-id="8037f-169">W pliku konfiguracji usługi Zastąp `<bindings>` sekcję poniższym kodem.</span><span class="sxs-lookup"><span data-stu-id="8037f-169">In the service's configuration file, replace the `<bindings>` section with the following code.</span></span> <span data-ttu-id="8037f-170">Jeśli nie masz jeszcze pliku konfiguracji usługi, zobacz temat [Używanie powiązań do konfigurowania usług i klientów](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="8037f-170">If you do not already have a service configuration file, see [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>

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

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="8037f-171">Korzystanie z powiązania w kliencie</span><span class="sxs-lookup"><span data-stu-id="8037f-171">Using the Binding in a Client</span></span>

<span data-ttu-id="8037f-172">Ta procedura pokazuje, jak generować dwa pliki: serwer proxy, który komunikuje się z usługą i plikiem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8037f-172">This procedure shows how to generate two files: a proxy that communicates with the service and a configuration file.</span></span> <span data-ttu-id="8037f-173">Opisano w nim również zmiany programu klienckiego, czyli trzeci plik używany na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="8037f-173">It also describes changes to the client program, which is the third file used on the client.</span></span>

##### <a name="to-use-a-binding-in-a-client-with-configuration"></a><span data-ttu-id="8037f-174">Aby użyć powiązania w kliencie z konfiguracją</span><span class="sxs-lookup"><span data-stu-id="8037f-174">To use a binding in a client with configuration</span></span>

1. <span data-ttu-id="8037f-175">Użyj narzędzia SvcUtil. exe, aby wygenerować kod i plik konfiguracji serwera proxy z metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="8037f-175">Use the SvcUtil.exe tool to generate the proxy code and configuration file from the service's metadata.</span></span> <span data-ttu-id="8037f-176">Aby uzyskać więcej informacji, zobacz [jak: Utwórz klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="8037f-176">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>

2. <span data-ttu-id="8037f-177">Zastąp sekcję [ powiązania>wwygenerowanymplikukonfiguracjikodemkonfiguracjizpoprzedniejsekcji.\<](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="8037f-177">Replace the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) section of the generated configuration file with the configuration code from the preceding section.</span></span>

3. <span data-ttu-id="8037f-178">Kod proceduralny jest wstawiany na początku `Main` metody programu klienckiego.</span><span class="sxs-lookup"><span data-stu-id="8037f-178">Procedural code is inserted at the beginning of the `Main` method of the client program.</span></span>

4. <span data-ttu-id="8037f-179">Utwórz wystąpienie wygenerowanej klasy klienta przekazujące nazwę powiązania w pliku konfiguracji jako parametr wejściowy.</span><span class="sxs-lookup"><span data-stu-id="8037f-179">Create an instance of the generated client class passing the name of the binding in the configuration file as an input parameter.</span></span>

5. <span data-ttu-id="8037f-180">Wywołaj <xref:System.ServiceModel.ClientBase%601.Open%2A> metodę, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="8037f-180">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

6. <span data-ttu-id="8037f-181">Wywołaj usługę i Wyświetl wyniki.</span><span class="sxs-lookup"><span data-stu-id="8037f-181">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]

## <a name="example"></a><span data-ttu-id="8037f-182">Przykład</span><span class="sxs-lookup"><span data-stu-id="8037f-182">Example</span></span>

[!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]

[!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)]
[!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]

## <a name="see-also"></a><span data-ttu-id="8037f-183">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8037f-183">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- [<span data-ttu-id="8037f-184">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="8037f-184">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="8037f-185">Instrukcje: Tworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="8037f-185">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="8037f-186">Zabezpieczanie usług</span><span class="sxs-lookup"><span data-stu-id="8037f-186">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)
- [<span data-ttu-id="8037f-187">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="8037f-187">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)
