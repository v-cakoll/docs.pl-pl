---
title: 'Instrukcje: Zabezpieczanie usługi za pomocą poświadczeń systemu Windows'
description: Dowiedz się, jak włączyć zabezpieczenia transportu w usłudze WCF, która znajduje się w domenie systemu Windows i jest wywoływana przez klientów w tej samej domenie.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: 8ef164e1475bfd5f047a99426a2bed43a7aa7353
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244636"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a><span data-ttu-id="19925-103">Instrukcje: Zabezpieczanie usługi za pomocą poświadczeń systemu Windows</span><span class="sxs-lookup"><span data-stu-id="19925-103">How to: Secure a Service with Windows Credentials</span></span>

<span data-ttu-id="19925-104">W tym temacie pokazano, jak włączyć zabezpieczenia transportu w usłudze Windows Communication Foundation (WCF), która znajduje się w domenie systemu Windows i jest wywoływana przez klientów w tej samej domenie.</span><span class="sxs-lookup"><span data-stu-id="19925-104">This topic shows how to enable transport security on a Windows Communication Foundation (WCF) service that resides in a Windows domain and is called by clients in the same domain.</span></span> <span data-ttu-id="19925-105">Aby uzyskać więcej informacji na temat tego scenariusza, zobacz [zabezpieczenia transportu z uwierzytelnianiem systemu Windows](./feature-details/transport-security-with-windows-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="19925-105">For more information about this scenario, see [Transport Security with Windows Authentication](./feature-details/transport-security-with-windows-authentication.md).</span></span> <span data-ttu-id="19925-106">Aby uzyskać przykładową aplikację, zobacz przykład [WSHttpBinding](./samples/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="19925-106">For a sample application, see the [WSHttpBinding](./samples/wshttpbinding.md) sample.</span></span>

<span data-ttu-id="19925-107">W tym temacie przyjęto założenie, że masz już zdefiniowany interfejs kontraktu i implementację, i dodaje do niego.</span><span class="sxs-lookup"><span data-stu-id="19925-107">This topic assumes you have an existing contract interface and implementation already defined, and adds on to that.</span></span> <span data-ttu-id="19925-108">Możesz również zmodyfikować istniejącą usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="19925-108">You can also modify an existing service and client.</span></span>

<span data-ttu-id="19925-109">Usługę można zabezpieczyć za pomocą poświadczeń systemu Windows w kodzie.</span><span class="sxs-lookup"><span data-stu-id="19925-109">You can secure a service with Windows credentials completely in code.</span></span> <span data-ttu-id="19925-110">Alternatywnie można pominąć część kodu przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="19925-110">Alternatively, you can omit some of the code by using a configuration file.</span></span> <span data-ttu-id="19925-111">W tym temacie przedstawiono obie metody.</span><span class="sxs-lookup"><span data-stu-id="19925-111">This topic shows both ways.</span></span> <span data-ttu-id="19925-112">Upewnij się, że używasz tylko jednej z tych metod, a nie obu.</span><span class="sxs-lookup"><span data-stu-id="19925-112">Be sure you only use one of the ways, not both.</span></span>

<span data-ttu-id="19925-113">Pierwsze trzy procedury pokazują, jak zabezpieczyć usługę przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="19925-113">The first three procedures show how to secure the service using code.</span></span> <span data-ttu-id="19925-114">Czwarta i piąta procedura pokazuje, jak to zrobić za pomocą pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="19925-114">The fourth and fifth procedure shows how to do it with a configuration file.</span></span>

## <a name="using-code"></a><span data-ttu-id="19925-115">Korzystanie z kodu</span><span class="sxs-lookup"><span data-stu-id="19925-115">Using Code</span></span>

<span data-ttu-id="19925-116">Kompletny kod dla usługi i klienta znajduje się w sekcji przykład na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="19925-116">The complete code for the service and the client is in the Example section at the end of this topic.</span></span>

<span data-ttu-id="19925-117">Pierwsza procedura zawiera instrukcje tworzenia i konfigurowania <xref:System.ServiceModel.WSHttpBinding> klasy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="19925-117">The first procedure walks through creating and configuring a <xref:System.ServiceModel.WSHttpBinding> class in code.</span></span> <span data-ttu-id="19925-118">Powiązanie używa transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="19925-118">The binding uses the HTTP transport.</span></span> <span data-ttu-id="19925-119">To samo powiązanie jest używane na kliencie.</span><span class="sxs-lookup"><span data-stu-id="19925-119">The same binding is used on the client.</span></span>

#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a><span data-ttu-id="19925-120">Aby utworzyć element WSHttpBinding, który używa poświadczeń systemu Windows i zabezpieczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="19925-120">To create a WSHttpBinding that uses Windows credentials and message security</span></span>

1. <span data-ttu-id="19925-121">Kod tej procedury jest wstawiany na początku `Run` metody `Test` klasy w kodzie usługi w sekcji przykład.</span><span class="sxs-lookup"><span data-stu-id="19925-121">This procedure's code is inserted at the beginning of the `Run` method of the `Test` class in the service code in the Example section.</span></span>

2. <span data-ttu-id="19925-122">Utworzenie wystąpienia <xref:System.ServiceModel.WSHttpBinding> klasy.</span><span class="sxs-lookup"><span data-stu-id="19925-122">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

3. <span data-ttu-id="19925-123">Ustaw <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> Właściwość <xref:System.ServiceModel.WSHttpSecurity> klasy na <xref:System.ServiceModel.SecurityMode.Message> .</span><span class="sxs-lookup"><span data-stu-id="19925-123">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property of the <xref:System.ServiceModel.WSHttpSecurity> class to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>

4. <span data-ttu-id="19925-124">Ustaw <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> Właściwość <xref:System.ServiceModel.MessageSecurityOverHttp> klasy na <xref:System.ServiceModel.MessageCredentialType.Windows> .</span><span class="sxs-lookup"><span data-stu-id="19925-124">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property of the <xref:System.ServiceModel.MessageSecurityOverHttp> class to <xref:System.ServiceModel.MessageCredentialType.Windows>.</span></span>

5. <span data-ttu-id="19925-125">Kod tej procedury jest następujący:</span><span class="sxs-lookup"><span data-stu-id="19925-125">The code for this procedure is as follows:</span></span>

    [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
    [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]

### <a name="using-the-binding-in-a-service"></a><span data-ttu-id="19925-126">Korzystanie z powiązania w usłudze</span><span class="sxs-lookup"><span data-stu-id="19925-126">Using the Binding in a Service</span></span>

<span data-ttu-id="19925-127">Jest to druga procedura, która pokazuje, jak używać powiązania w usłudze samodzielnej.</span><span class="sxs-lookup"><span data-stu-id="19925-127">This is the second procedure, which shows how to use the binding in a self-hosted service.</span></span> <span data-ttu-id="19925-128">Aby uzyskać więcej informacji na temat usług hostingu, zobacz [usługi hostingu](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="19925-128">For more information about hosting services see [Hosting Services](hosting-services.md).</span></span>

##### <a name="to-use-a-binding-in-a-service"></a><span data-ttu-id="19925-129">Aby użyć powiązania w usłudze</span><span class="sxs-lookup"><span data-stu-id="19925-129">To use a binding in a service</span></span>

1. <span data-ttu-id="19925-130">Wstaw kod tej procedury po kodzie z poprzedniej procedury.</span><span class="sxs-lookup"><span data-stu-id="19925-130">Insert this procedure's code after the code from the preceding procedure.</span></span>

2. <span data-ttu-id="19925-131">Utwórz <xref:System.Type> zmienną o nazwie `contractType` i przypisz ją do typu interfejsu ( `ICalculator` ).</span><span class="sxs-lookup"><span data-stu-id="19925-131">Create a <xref:System.Type> variable named `contractType` and assign it the type of the interface (`ICalculator`).</span></span> <span data-ttu-id="19925-132">Korzystając z Visual Basic, użyj `GetType` operatora; w przypadku używania języka C#, użyj `typeof` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="19925-132">When using Visual Basic, use the `GetType` operator; when using C#, use the `typeof` keyword.</span></span>

3. <span data-ttu-id="19925-133">Utwórz drugą <xref:System.Type> zmienną o nazwie `serviceType` i przypisz ją do typu zaimplementowanego kontraktu ( `Calculator` ).</span><span class="sxs-lookup"><span data-stu-id="19925-133">Create a second <xref:System.Type> variable named `serviceType` and assign it the type of the implemented contract (`Calculator`).</span></span>

4. <span data-ttu-id="19925-134">Utwórz wystąpienie <xref:System.Uri> klasy o nazwie `baseAddress` z adresem podstawowym usługi.</span><span class="sxs-lookup"><span data-stu-id="19925-134">Create an instance of the <xref:System.Uri> class named `baseAddress` with the base address of the service.</span></span> <span data-ttu-id="19925-135">Adres podstawowy musi mieć schemat zgodny z transportem.</span><span class="sxs-lookup"><span data-stu-id="19925-135">The base address must have a scheme that matches the transport.</span></span> <span data-ttu-id="19925-136">W tym przypadku schemat transportu to HTTP, a adres zawiera specjalny Uniform Resource Identifier (URI) "localhost" i numer portu (8036), a także podstawowy adres punktu końcowego ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/` .</span><span class="sxs-lookup"><span data-stu-id="19925-136">In this case, the transport scheme is HTTP, and the address includes the special Uniform Resource Identifier (URI) "localhost" and a port number (8036) as well as a base endpoint address ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/`.</span></span>

5. <span data-ttu-id="19925-137">Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> klasy za pomocą `serviceType` `baseAddress` zmiennych i.</span><span class="sxs-lookup"><span data-stu-id="19925-137">Create an instance of the <xref:System.ServiceModel.ServiceHost> class with the `serviceType` and `baseAddress` variables.</span></span>

6. <span data-ttu-id="19925-138">Dodaj punkt końcowy do usługi przy użyciu elementu `contractType` , powiązania i nazwy punktu końcowego (secureCalculator).</span><span class="sxs-lookup"><span data-stu-id="19925-138">Add an endpoint to the service using the `contractType`, binding, and an endpoint name (secureCalculator).</span></span> <span data-ttu-id="19925-139">Po zainicjowaniu wywołania usługi Klient musi połączyć adres podstawowy i nazwę punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="19925-139">A client must concatenate the base address and the endpoint name when initiating a call to the service.</span></span>

7. <span data-ttu-id="19925-140">Wywołaj <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metodę, aby uruchomić usługę.</span><span class="sxs-lookup"><span data-stu-id="19925-140">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service.</span></span> <span data-ttu-id="19925-141">Kod tej procedury jest przedstawiony tutaj:</span><span class="sxs-lookup"><span data-stu-id="19925-141">The code for this procedure is shown here:</span></span>

    [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
    [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="19925-142">Korzystanie z powiązania w kliencie</span><span class="sxs-lookup"><span data-stu-id="19925-142">Using the Binding in a Client</span></span>

<span data-ttu-id="19925-143">Ta procedura pokazuje, jak wygenerować serwer proxy, który komunikuje się z usługą.</span><span class="sxs-lookup"><span data-stu-id="19925-143">This procedure shows how to generate a proxy that communicates with the service.</span></span> <span data-ttu-id="19925-144">Serwer proxy jest generowany przy użyciu [Narzędzia do obsługi metadanych ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) , które używa metadanych usługi do utworzenia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="19925-144">The proxy is generated with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) which uses the service metadata to create the proxy.</span></span>

<span data-ttu-id="19925-145">Ta procedura powoduje także utworzenie wystąpienia <xref:System.ServiceModel.WSHttpBinding> klasy w celu komunikacji z usługą, a następnie wywołanie usługi.</span><span class="sxs-lookup"><span data-stu-id="19925-145">This procedure also creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class to communicate with the service, and then calls the service.</span></span>

<span data-ttu-id="19925-146">Ten przykład używa tylko kodu do utworzenia klienta.</span><span class="sxs-lookup"><span data-stu-id="19925-146">This example uses only code to create the client.</span></span> <span data-ttu-id="19925-147">Alternatywnie można użyć pliku konfiguracji, który jest przedstawiony w sekcji opisanej w poniższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="19925-147">As an alternative, you can use a configuration file, which is shown in the section following this procedure.</span></span>

#### <a name="to-use-a-binding-in-a-client-with-code"></a><span data-ttu-id="19925-148">Aby użyć powiązania w kliencie z kodem</span><span class="sxs-lookup"><span data-stu-id="19925-148">To use a binding in a client with code</span></span>

1. <span data-ttu-id="19925-149">Użyj narzędzia SvcUtil.exe do wygenerowania kodu serwera proxy z metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="19925-149">Use the SvcUtil.exe tool to generate the proxy code from the service's metadata.</span></span> <span data-ttu-id="19925-150">Aby uzyskać więcej informacji, zobacz [How to: Create a Client](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="19925-150">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="19925-151">Wygenerowany kod serwera proxy dziedziczy z <xref:System.ServiceModel.ClientBase%601> klasy, co zapewnia, że każdy klient ma wymagane konstruktory, metody i właściwości do komunikowania się z usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="19925-151">The generated proxy code inherits from the <xref:System.ServiceModel.ClientBase%601> class, which ensures that every client has the necessary constructors, methods, and properties to communicate with a WCF service.</span></span> <span data-ttu-id="19925-152">W tym przykładzie wygenerowany kod zawiera `CalculatorClient` klasę, która implementuje `ICalculator` interfejs, umożliwiając zgodność z kodem usługi.</span><span class="sxs-lookup"><span data-stu-id="19925-152">In this example, the generated code includes the `CalculatorClient` class, which implements the `ICalculator` interface, enabling compatibility with the service code.</span></span>

2. <span data-ttu-id="19925-153">Kod tej procedury jest wstawiany na początku `Main` metody programu klienckiego.</span><span class="sxs-lookup"><span data-stu-id="19925-153">This procedure's code is inserted at the beginning of the `Main` method of the client program.</span></span>

3. <span data-ttu-id="19925-154">Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw jego tryb zabezpieczeń na `Message` i jego typ poświadczeń klienta na `Windows` .</span><span class="sxs-lookup"><span data-stu-id="19925-154">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to `Message` and its client credential type to `Windows`.</span></span> <span data-ttu-id="19925-155">Przykład nazwy zmiennej `clientBinding` .</span><span class="sxs-lookup"><span data-stu-id="19925-155">The example names the variable `clientBinding`.</span></span>

4. <span data-ttu-id="19925-156">Utwórz wystąpienie <xref:System.ServiceModel.EndpointAddress> klasy o nazwie `serviceAddress` .</span><span class="sxs-lookup"><span data-stu-id="19925-156">Create an instance of the <xref:System.ServiceModel.EndpointAddress> class named `serviceAddress`.</span></span> <span data-ttu-id="19925-157">Zainicjuj wystąpienie z adresem podstawowym połączonym z nazwą punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="19925-157">Initialize the instance with the base address concatenated with the endpoint name.</span></span>

5. <span data-ttu-id="19925-158">Utwórz wystąpienie wygenerowanej klasy klienta przy użyciu `serviceAddress` i `clientBinding` zmiennych.</span><span class="sxs-lookup"><span data-stu-id="19925-158">Create an instance of the generated client class with the `serviceAddress` and the `clientBinding` variables.</span></span>

6. <span data-ttu-id="19925-159">Wywołaj <xref:System.ServiceModel.ClientBase%601.Open%2A> metodę, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="19925-159">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

7. <span data-ttu-id="19925-160">Wywołaj usługę i Wyświetl wyniki.</span><span class="sxs-lookup"><span data-stu-id="19925-160">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
    [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]

## <a name="using-the-configuration-file"></a><span data-ttu-id="19925-161">Korzystanie z pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="19925-161">Using the Configuration File</span></span>

<span data-ttu-id="19925-162">Zamiast tworzyć powiązania z kodem proceduralnym, można użyć poniższego kodu dla sekcji powiązania w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="19925-162">Instead of creating the binding with procedural code, you can use the following code shown for the bindings section of the configuration file.</span></span>

<span data-ttu-id="19925-163">Jeśli nie masz jeszcze zdefiniowanej usługi, zobacz [projektowanie i implementowanie usług](designing-and-implementing-services.md)oraz [Konfigurowanie usług](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="19925-163">If you do not already have a service defined, see [Designing and Implementing Services](designing-and-implementing-services.md), and [Configuring Services](configuring-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="19925-164">Ten kod konfiguracji jest używany zarówno w plikach konfiguracji usługi, jak i klienta.</span><span class="sxs-lookup"><span data-stu-id="19925-164">This configuration code is used in both the service and client configuration files.</span></span>

#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a><span data-ttu-id="19925-165">Aby włączyć zabezpieczenia transferu dla usługi w domenie systemu Windows przy użyciu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="19925-165">To enable transfer security on a service in a Windows domain using configuration</span></span>

1. <span data-ttu-id="19925-166">Dodaj [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element do [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) sekcji elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="19925-166">Add a [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element to the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element section of the configuration file.</span></span>

2. <span data-ttu-id="19925-167">Dodaj `binding` element> <do `WSHttpBinding` elementu <> i ustaw dla `configurationName` atrybutu wartość odpowiednią dla Twojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="19925-167">Add a <`binding`> element to the <`WSHttpBinding`> element and set the `configurationName` attribute to a value appropriate to your application.</span></span>

3. <span data-ttu-id="19925-168">Dodaj `security` element> <i ustaw dla niego `mode` atrybut Message.</span><span class="sxs-lookup"><span data-stu-id="19925-168">Add a <`security`> element and set the `mode` attribute to Message.</span></span>

4. <span data-ttu-id="19925-169">Dodaj `message` element> <i ustaw `clientCredentialType` atrybut na Windows.</span><span class="sxs-lookup"><span data-stu-id="19925-169">Add a <`message`> element and set the `clientCredentialType` attribute to Windows.</span></span>

5. <span data-ttu-id="19925-170">W pliku konfiguracji usługi Zastąp `<bindings>` sekcję poniższym kodem.</span><span class="sxs-lookup"><span data-stu-id="19925-170">In the service's configuration file, replace the `<bindings>` section with the following code.</span></span> <span data-ttu-id="19925-171">Jeśli nie masz jeszcze pliku konfiguracji usługi, zobacz temat [Używanie powiązań do konfigurowania usług i klientów](using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="19925-171">If you do not already have a service configuration file, see [Using Bindings to Configure Services and Clients](using-bindings-to-configure-services-and-clients.md).</span></span>

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

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="19925-172">Korzystanie z powiązania w kliencie</span><span class="sxs-lookup"><span data-stu-id="19925-172">Using the Binding in a Client</span></span>

<span data-ttu-id="19925-173">Ta procedura pokazuje, jak generować dwa pliki: serwer proxy, który komunikuje się z usługą i plikiem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="19925-173">This procedure shows how to generate two files: a proxy that communicates with the service and a configuration file.</span></span> <span data-ttu-id="19925-174">Opisano w nim również zmiany programu klienckiego, czyli trzeci plik używany na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="19925-174">It also describes changes to the client program, which is the third file used on the client.</span></span>

#### <a name="to-use-a-binding-in-a-client-with-configuration"></a><span data-ttu-id="19925-175">Aby użyć powiązania w kliencie z konfiguracją</span><span class="sxs-lookup"><span data-stu-id="19925-175">To use a binding in a client with configuration</span></span>

1. <span data-ttu-id="19925-176">Użyj narzędzia SvcUtil.exe, aby wygenerować kod i plik konfiguracji serwera proxy z metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="19925-176">Use the SvcUtil.exe tool to generate the proxy code and configuration file from the service's metadata.</span></span> <span data-ttu-id="19925-177">Aby uzyskać więcej informacji, zobacz [How to: Create a Client](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="19925-177">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span>

2. <span data-ttu-id="19925-178">Zamień [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) sekcję wygenerowanego pliku konfiguracji na kod konfiguracji z poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="19925-178">Replace the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) section of the generated configuration file with the configuration code from the preceding section.</span></span>

3. <span data-ttu-id="19925-179">Kod proceduralny jest wstawiany na początku `Main` metody programu klienckiego.</span><span class="sxs-lookup"><span data-stu-id="19925-179">Procedural code is inserted at the beginning of the `Main` method of the client program.</span></span>

4. <span data-ttu-id="19925-180">Utwórz wystąpienie wygenerowanej klasy klienta przekazujące nazwę powiązania w pliku konfiguracji jako parametr wejściowy.</span><span class="sxs-lookup"><span data-stu-id="19925-180">Create an instance of the generated client class passing the name of the binding in the configuration file as an input parameter.</span></span>

5. <span data-ttu-id="19925-181">Wywołaj <xref:System.ServiceModel.ClientBase%601.Open%2A> metodę, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="19925-181">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

6. <span data-ttu-id="19925-182">Wywołaj usługę i Wyświetl wyniki.</span><span class="sxs-lookup"><span data-stu-id="19925-182">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]

## <a name="example"></a><span data-ttu-id="19925-183">Przykład</span><span class="sxs-lookup"><span data-stu-id="19925-183">Example</span></span>

[!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]

[!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)]
[!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]

## <a name="see-also"></a><span data-ttu-id="19925-184">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19925-184">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- [<span data-ttu-id="19925-185">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="19925-185">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="19925-186">Instrukcje: tworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="19925-186">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [<span data-ttu-id="19925-187">Zabezpieczanie usług</span><span class="sxs-lookup"><span data-stu-id="19925-187">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="19925-188">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="19925-188">Security Overview</span></span>](./feature-details/security-overview.md)
