---
title: "Instrukcje: Wymiana komunikatów w ramach sesji niezawodnej"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c0465f50de37d7276cad5920c4b9fb9e544caf57
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a><span data-ttu-id="a1f1f-102">Instrukcje: Wymiana komunikatów w ramach sesji niezawodnej</span><span class="sxs-lookup"><span data-stu-id="a1f1f-102">How to: Exchange Messages Within a Reliable Session</span></span>

<span data-ttu-id="a1f1f-103">W tym temacie opisano kroki wymagane w celu umożliwienia niezawodnej sesji przy użyciu jednej powiązań dostarczane przez system, które obsługują sesji programu, ale nie domyślnie.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-103">This topic outlines the steps required to enable a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="a1f1f-104">Włącz niezawodnej sesji imperatively przy użyciu kodu lub deklaratywnie w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-104">You enable a reliable session imperatively using code or declaratively in your configuration file.</span></span> <span data-ttu-id="a1f1f-105">Ta procedura wykorzystuje pliki konfiguracji klienta i usługi, aby włączyć niezawodnej sesji i określić, że komunikaty dostarczone w tej samej kolejności, w jakiej zostały wysłane.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-105">This procedure uses the client and service configuration files to enable the reliable session and to stipulate that the messages arrive in the same order in which they were sent.</span></span>

<span data-ttu-id="a1f1f-106">Część klucza tej procedury jest, że element konfiguracji punktu końcowego zawiera `bindingConfiguration` atrybut, który odwołuje się do konfiguracji powiązania o nazwie `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-106">The key part of this procedure is that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="a1f1f-107">[  **\<Powiązania >** ](../../../../docs/framework/misc/binding.md) element konfiguracji odwołuje się do tej nazwy, aby włączyć niezawodnej sesji przez ustawienie `enabled` atrybutu [  **\<reliableSession >** ](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) elementu `true`.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-107">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) element to `true`.</span></span> <span data-ttu-id="a1f1f-108">Określ gwarancje uporządkowanego dostarczenia niezawodnej sesji przez ustawienie `ordered` atrybutu `true`.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-108">You specify the ordered delivery assurances for the reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="a1f1f-109">Dla źródła kopię w tym przykładzie [sesja niezawodna WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="a1f1f-109">For the source copy of this example, see [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="a1f1f-110">Skonfiguruj usługę z WSHttpBinding do użycia niezawodnej sesji</span><span class="sxs-lookup"><span data-stu-id="a1f1f-110">Configure the service with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="a1f1f-111">Definiowanie kontraktu usługi dla typu usługi.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. <span data-ttu-id="a1f1f-112">Implementowanie kontraktu usługi w klasie usługi.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="a1f1f-113">Należy pamiętać, że informacje powiązania lub adres nie jest określona wewnątrz implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="a1f1f-114">Nie są wymagane, aby napisać kod, aby pobrać adres lub powiązanie informacji o informacje z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-114">You aren't required to write code to retrieve the address or binding information information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. <span data-ttu-id="a1f1f-115">Utwórz *Web.config* pliku do konfigurowania punktu końcowego dla `CalculatorService` używającą <xref:System.ServiceModel.WSHttpBinding> z niezawodnej sesji włączona i uporządkowanego dostarczenia komunikatów wymagane.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding> with reliable session enabled and ordered delivery of messages required.</span></span>

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. <span data-ttu-id="a1f1f-116">Utwórz *Service.svc* pliku, który zawiera wiersz:</span><span class="sxs-lookup"><span data-stu-id="a1f1f-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1.  <span data-ttu-id="a1f1f-117">Miejsce *Service.svc* pliku w katalogu wirtualnym programu Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="a1f1f-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="a1f1f-118">Konfigurowanie klienta z WSHttpBinding do użycia niezawodnej sesji</span><span class="sxs-lookup"><span data-stu-id="a1f1f-118">Configure the client with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="a1f1f-119">Użyj [narzędzie do obsługi metadanych elementu ServiceModel (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z poziomu wiersza polecenia, aby wygenerować kod na podstawie metadanych usługi:</span><span class="sxs-lookup"><span data-stu-id="a1f1f-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata:</span></span>

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="a1f1f-120">Zawiera wygenerowanego klienta `ICalculator` Interfejs definiujący kontrakt usługi, które muszą spełniać implementacja klienta.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-120">The generated client contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. <span data-ttu-id="a1f1f-121">Aplikacja wygenerowanego klienta zawiera również implementacja `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="a1f1f-122">Należy pamiętać, że informacje adres i powiązanie nie jest określony dowolnym wewnątrz implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-122">Note that the address and binding information isn't specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="a1f1f-123">Nie są wymagane, aby napisać kod, aby pobrać adres lub powiązanie informacji o informacje z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-123">You aren't required to write code to retrieve the address or binding information information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. <span data-ttu-id="a1f1f-124">*Svcutil.exe* również generuje konfigurację dla klienta, który używa <xref:System.ServiceModel.WSHttpBinding> klasy.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-124">*Svcutil.exe* also generates the configuration for the client that uses the <xref:System.ServiceModel.WSHttpBinding> class.</span></span> <span data-ttu-id="a1f1f-125">Nazwa pliku konfiguracji *App.config* przy użyciu [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a1f1f-125">Name the configuration file *App.config* when using [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. <span data-ttu-id="a1f1f-126">Utwórz wystąpienie `ClientCalculator` w aplikacji i wywoływanie operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-126">Create an instance of the `ClientCalculator` in an application and call the service operations.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. <span data-ttu-id="a1f1f-127">Kompilowanie i uruchamianie klienta.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-127">Compile and run the client.</span></span>

## <a name="example"></a><span data-ttu-id="a1f1f-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1f1f-128">Example</span></span>

<span data-ttu-id="a1f1f-129">Domyślnie kilka powiązania dostarczane przez system obsługi niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-129">Several of the system-provided bindings support reliable sessions by default.</span></span> <span data-ttu-id="a1f1f-130">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="a1f1f-130">These include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

<span data-ttu-id="a1f1f-131">Na przykład sposobu tworzenia niestandardowego powiązania, który niezawodnej sesji obsługuje zobacz [porady: Tworzenie niestandardowego wiązania niezawodnej sesji z protokołu HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span><span class="sxs-lookup"><span data-stu-id="a1f1f-131">For an example of how to create a custom binding that supports reliable sessions, see [How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a1f1f-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1f1f-132">See also</span></span>

[<span data-ttu-id="a1f1f-133">Niezawodne sesje</span><span class="sxs-lookup"><span data-stu-id="a1f1f-133">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
