---
title: 'Instrukcje: Wymiana komunikatów w ramach sesji niezawodnej'
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 6b204749ce86b79bf46b2d5c96be1b00dca9500d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43419473"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a><span data-ttu-id="32c48-102">Instrukcje: Wymiana komunikatów w ramach sesji niezawodnej</span><span class="sxs-lookup"><span data-stu-id="32c48-102">How to: Exchange Messages Within a Reliable Session</span></span>

<span data-ttu-id="32c48-103">W tym temacie opisano kroki wymagane w celu umożliwienia niezawodnej sesji przy użyciu jednej z powiązań dostarczanych przez system, które obsługują sesji programu, ale nie domyślnie.</span><span class="sxs-lookup"><span data-stu-id="32c48-103">This topic outlines the steps required to enable a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="32c48-104">Włącz niezawodnej sesji obowiązkowo przy użyciu kodu lub deklaratywnie w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="32c48-104">You enable a reliable session imperatively using code or declaratively in your configuration file.</span></span> <span data-ttu-id="32c48-105">Ta procedura wykorzystuje pliki konfiguracji klienta i usługi, aby umożliwić niezawodnej sesji i określać, że komunikaty zostaną dostarczone w tej samej kolejności, w jakiej zostały wysłane.</span><span class="sxs-lookup"><span data-stu-id="32c48-105">This procedure uses the client and service configuration files to enable the reliable session and to stipulate that the messages arrive in the same order in which they were sent.</span></span>

<span data-ttu-id="32c48-106">Kluczowa część tej procedury jest, że element konfiguracji punktu końcowego zawiera `bindingConfiguration` atrybut, który odwołuje się do konfiguracji powiązania o nazwie `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="32c48-106">The key part of this procedure is that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="32c48-107">[  **\<Powiązania >** ](../../../../docs/framework/misc/binding.md) element konfiguracji odwołuje się do tej nazwy, aby umożliwić niezawodnej sesji przez ustawienie `enabled` atrybutu [  **\<reliableSession >** ](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) elementu `true`.</span><span class="sxs-lookup"><span data-stu-id="32c48-107">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) element to `true`.</span></span> <span data-ttu-id="32c48-108">Określ gwarancje dostarczenia uporządkowane w niezawodnej sesji przez ustawienie `ordered` atrybutu `true`.</span><span class="sxs-lookup"><span data-stu-id="32c48-108">You specify the ordered delivery assurances for the reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="32c48-109">Źródło kopię w tym przykładzie można zobaczyć [sesja niezawodna WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="32c48-109">For the source copy of this example, see [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="32c48-110">Konfigurowanie usługi przy użyciu WSHttpBinding używać niezawodnej sesji</span><span class="sxs-lookup"><span data-stu-id="32c48-110">Configure the service with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="32c48-111">Definiowanie kontraktu usługi dla typu usługi.</span><span class="sxs-lookup"><span data-stu-id="32c48-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. <span data-ttu-id="32c48-112">Implementowanie kontraktu usługi, w klasie usługi.</span><span class="sxs-lookup"><span data-stu-id="32c48-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="32c48-113">Należy pamiętać, że informacji adres lub powiązanie nie jest określona wewnątrz implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="32c48-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="32c48-114">Nie są wymagane, aby napisać kod, aby pobrać adres lub powiązania informacji o informacje z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="32c48-114">You aren't required to write code to retrieve the address or binding information information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. <span data-ttu-id="32c48-115">Tworzenie *Web.config* pliku, aby skonfigurować punkt końcowy dla `CalculatorService` , który używa <xref:System.ServiceModel.WSHttpBinding> za pomocą niezawodnej sesji włączone i uporządkowane dostarczania wiadomości wymagane.</span><span class="sxs-lookup"><span data-stu-id="32c48-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding> with reliable session enabled and ordered delivery of messages required.</span></span>

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. <span data-ttu-id="32c48-116">Tworzenie *Service.svc* pliku zawierające następujący wiersz:</span><span class="sxs-lookup"><span data-stu-id="32c48-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1.  <span data-ttu-id="32c48-117">Miejsce *Service.svc* pliku w katalogu wirtualnego Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="32c48-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="32c48-118">Konfigurowanie klienta za pomocą WSHttpBinding używać niezawodnej sesji</span><span class="sxs-lookup"><span data-stu-id="32c48-118">Configure the client with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="32c48-119">Użyj [narzędzie do metadanych elementu ServiceModel (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z poziomu wiersza polecenia, aby wygenerować kod z metadanych usługi:</span><span class="sxs-lookup"><span data-stu-id="32c48-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata:</span></span>

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="32c48-120">Zawiera wygenerowanego klienta `ICalculator` Interfejs definiujący kontrakt usługi, które muszą spełniać implementacji klienta.</span><span class="sxs-lookup"><span data-stu-id="32c48-120">The generated client contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. <span data-ttu-id="32c48-121">Aplikacja wygenerowanego klienta zawiera również implementację `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="32c48-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="32c48-122">Należy pamiętać, że informacje dotyczące adresów i powiązanie nie jest określona w dowolne miejsce wewnątrz implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="32c48-122">Note that the address and binding information isn't specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="32c48-123">Nie są wymagane, aby napisać kod, aby pobrać adres lub powiązania informacji o informacje z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="32c48-123">You aren't required to write code to retrieve the address or binding information information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. <span data-ttu-id="32c48-124">*Svcutil.exe* również generuje konfigurację dla klienta, który używa <xref:System.ServiceModel.WSHttpBinding> klasy.</span><span class="sxs-lookup"><span data-stu-id="32c48-124">*Svcutil.exe* also generates the configuration for the client that uses the <xref:System.ServiceModel.WSHttpBinding> class.</span></span> <span data-ttu-id="32c48-125">Nadaj plikowi konfiguracji nazwę *App.config* przy użyciu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="32c48-125">Name the configuration file *App.config* when using Visual Studio.</span></span>

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. <span data-ttu-id="32c48-126">Utwórz wystąpienie obiektu `ClientCalculator` w aplikacji i wywoływanie operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="32c48-126">Create an instance of the `ClientCalculator` in an application and call the service operations.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. <span data-ttu-id="32c48-127">Kompilowanie i uruchamianie klienta.</span><span class="sxs-lookup"><span data-stu-id="32c48-127">Compile and run the client.</span></span>

## <a name="example"></a><span data-ttu-id="32c48-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="32c48-128">Example</span></span>

<span data-ttu-id="32c48-129">Domyślnie kilka powiązania dostarczane przez system obsługuje sesji uwierzytelnianych.</span><span class="sxs-lookup"><span data-stu-id="32c48-129">Several of the system-provided bindings support reliable sessions by default.</span></span> <span data-ttu-id="32c48-130">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="32c48-130">These include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

<span data-ttu-id="32c48-131">Na przykład sposobu tworzenia niestandardowego powiązania, które obsługuje niezawodne sesje zobacz [porady: Tworzenie niestandardowego powiązania niezawodnej sesji za pomocą protokołu HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span><span class="sxs-lookup"><span data-stu-id="32c48-131">For an example of how to create a custom binding that supports reliable sessions, see [How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="32c48-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32c48-132">See also</span></span>

[<span data-ttu-id="32c48-133">Niezawodne sesje</span><span class="sxs-lookup"><span data-stu-id="32c48-133">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
