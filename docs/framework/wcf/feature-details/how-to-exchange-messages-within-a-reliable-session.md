---
title: 'Instrukcje: Wymiana komunikatów w ramach sesji niezawodnej'
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 5b01ddfd95db2f7e88f9481265c348f4f16fbbee
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579479"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a><span data-ttu-id="fbf25-102">Instrukcje: Wymiana komunikatów w ramach sesji niezawodnej</span><span class="sxs-lookup"><span data-stu-id="fbf25-102">How to: Exchange Messages Within a Reliable Session</span></span>

<span data-ttu-id="fbf25-103">W tym temacie opisano kroki wymagane do umożliwienia niezawodnej sesji przy użyciu jednego z powiązań dostarczonych przez system, które obsługują taką sesję, ale nie jest to domyślnie możliwe.</span><span class="sxs-lookup"><span data-stu-id="fbf25-103">This topic outlines the steps required to enable a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="fbf25-104">Niezawodna sesja jest włączana za pomocą kodu lub deklaratywnie w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fbf25-104">You enable a reliable session imperatively using code or declaratively in your configuration file.</span></span> <span data-ttu-id="fbf25-105">Ta procedura korzysta z plików konfiguracji klienta i usługi w celu włączenia niezawodnej sesji i określenia, że komunikaty docierają do tej samej kolejności, w jakiej zostały wysłane.</span><span class="sxs-lookup"><span data-stu-id="fbf25-105">This procedure uses the client and service configuration files to enable the reliable session and to stipulate that the messages arrive in the same order in which they were sent.</span></span>

<span data-ttu-id="fbf25-106">Kluczową częścią tej procedury jest to, że element konfiguracji punktu końcowego zawiera `bindingConfiguration` atrybut odwołujący się do konfiguracji powiązania o nazwie `Binding1` .</span><span class="sxs-lookup"><span data-stu-id="fbf25-106">The key part of this procedure is that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="fbf25-107">[**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)Element konfiguracji odwołuje się do tej nazwy, aby umożliwić niezawodne sesje przez ustawienie `enabled` atrybutu [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) elementu na `true` .</span><span class="sxs-lookup"><span data-stu-id="fbf25-107">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) element to `true`.</span></span> <span data-ttu-id="fbf25-108">Należy określić uporządkowane gwarancje dostarczania dla niezawodnej sesji przez ustawienie `ordered` atrybutu na `true` .</span><span class="sxs-lookup"><span data-stu-id="fbf25-108">You specify the ordered delivery assurances for the reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="fbf25-109">Aby uzyskać kopię źródła tego przykładu, zobacz temat [Niezawodna sesja WS](../samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="fbf25-109">For the source copy of this example, see [WS Reliable Session](../samples/ws-reliable-session.md).</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="fbf25-110">Konfigurowanie usługi za pomocą WSHttpBinding do korzystania z niezawodnej sesji</span><span class="sxs-lookup"><span data-stu-id="fbf25-110">Configure the service with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="fbf25-111">Zdefiniuj kontrakt usługi dla typu usługi.</span><span class="sxs-lookup"><span data-stu-id="fbf25-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. <span data-ttu-id="fbf25-112">Zaimplementuj kontrakt usługi w klasie usługi.</span><span class="sxs-lookup"><span data-stu-id="fbf25-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="fbf25-113">Należy zauważyć, że adres lub informacje o powiązaniu nie są określone w implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="fbf25-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="fbf25-114">Nie trzeba pisać kodu w celu pobrania adresu lub informacji o powiązaniu z pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="fbf25-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. <span data-ttu-id="fbf25-115">Utwórz plik *Web. config* , aby skonfigurować punkt końcowy dla programu `CalculatorService` , który korzysta z <xref:System.ServiceModel.WSHttpBinding> włączonej niezawodnej sesji z włączoną obsługą i uporządkowane dostarczanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="fbf25-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding> with reliable session enabled and ordered delivery of messages required.</span></span>

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. <span data-ttu-id="fbf25-116">Utwórz plik *usługi SVC* , który zawiera wiersz:</span><span class="sxs-lookup"><span data-stu-id="fbf25-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. <span data-ttu-id="fbf25-117">Umieść plik *Service. svc* w katalogu wirtualnym Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="fbf25-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="fbf25-118">Konfigurowanie klienta z WSHttpBinding do korzystania z niezawodnej sesji</span><span class="sxs-lookup"><span data-stu-id="fbf25-118">Configure the client with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="fbf25-119">Użyj [Narzędzia metadanych ServiceModel (*Svcutil. exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) z wiersza polecenia, aby wygenerować kod na podstawie metadanych usługi:</span><span class="sxs-lookup"><span data-stu-id="fbf25-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata:</span></span>

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="fbf25-120">Wygenerowany klient zawiera `ICalculator` interfejs, który definiuje kontrakt usługi, który musi spełniać implementacja klienta.</span><span class="sxs-lookup"><span data-stu-id="fbf25-120">The generated client contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. <span data-ttu-id="fbf25-121">Wygenerowana aplikacja kliencka zawiera również implementację programu `ClientCalculator` .</span><span class="sxs-lookup"><span data-stu-id="fbf25-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="fbf25-122">Należy zauważyć, że informacje o adresie i powiązaniu nie są określone w dowolnym miejscu w implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="fbf25-122">Note that the address and binding information isn't specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="fbf25-123">Nie trzeba pisać kodu w celu pobrania adresu lub informacji o powiązaniu z pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="fbf25-123">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. <span data-ttu-id="fbf25-124">*Svcutil. exe* generuje również konfigurację dla klienta, który używa <xref:System.ServiceModel.WSHttpBinding> klasy.</span><span class="sxs-lookup"><span data-stu-id="fbf25-124">*Svcutil.exe* also generates the configuration for the client that uses the <xref:System.ServiceModel.WSHttpBinding> class.</span></span> <span data-ttu-id="fbf25-125">Nazwij plik konfiguracji *App. config* podczas korzystania z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fbf25-125">Name the configuration file *App.config* when using Visual Studio.</span></span>

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. <span data-ttu-id="fbf25-126">Utwórz wystąpienie elementu `ClientCalculator` w aplikacji i Wywołaj operacje usługi.</span><span class="sxs-lookup"><span data-stu-id="fbf25-126">Create an instance of the `ClientCalculator` in an application and call the service operations.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. <span data-ttu-id="fbf25-127">Kompiluj i uruchom klienta.</span><span class="sxs-lookup"><span data-stu-id="fbf25-127">Compile and run the client.</span></span>

## <a name="example"></a><span data-ttu-id="fbf25-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="fbf25-128">Example</span></span>

<span data-ttu-id="fbf25-129">Niektóre powiązania dostarczone przez system domyślnie obsługują niezawodne sesje.</span><span class="sxs-lookup"><span data-stu-id="fbf25-129">Several of the system-provided bindings support reliable sessions by default.</span></span> <span data-ttu-id="fbf25-130">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="fbf25-130">These include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

<span data-ttu-id="fbf25-131">Aby zapoznać się z przykładem tworzenia niestandardowego powiązania, które obsługuje niezawodne sesje, zobacz [How to: Create an Custom niezawodnej sesji powiązania z protokołem HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md).</span><span class="sxs-lookup"><span data-stu-id="fbf25-131">For an example of how to create a custom binding that supports reliable sessions, see [How to: Create a Custom Reliable Session Binding with HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fbf25-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fbf25-132">See also</span></span>

- [<span data-ttu-id="fbf25-133">Niezawodne sesje</span><span class="sxs-lookup"><span data-stu-id="fbf25-133">Reliable Sessions</span></span>](reliable-sessions.md)
