---
title: 'Instrukcje: Określanie wiązań klienta w konfiguracji'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 574f56173c2acfcf41a5e9a9e99abe45281e3636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184036"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="05945-102">Instrukcje: Określanie wiązań klienta w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="05945-102">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="05945-103">W tym przykładzie aplikacja konsoli klienta jest tworzony do korzystania z usługi kalkulatora, a powiązanie dla tego klienta jest określony deklaratywnie w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="05945-103">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="05945-104">Klient uzyskuje dostęp `CalculatorService`do , `ICalculator` który implementuje interfejs, a zarówno <xref:System.ServiceModel.BasicHttpBinding> usługi i klienta używać klasy.</span><span class="sxs-lookup"><span data-stu-id="05945-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="05945-105">Opisana procedura zakłada, że usługa kalkulatora jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="05945-105">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="05945-106">Aby uzyskać informacje dotyczące sposobu tworzenia usługi, zobacz [Jak: Określanie powiązania usługi w konfiguracji](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="05945-106">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="05945-107">Używa również [ServiceModel Metadata Utility Tool (Svcutil.exe),](servicemodel-metadata-utility-tool-svcutil-exe.md) które program Windows Communication Foundation (WCF) zapewnia do automatycznego generowania składników klienta.</span><span class="sxs-lookup"><span data-stu-id="05945-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) that Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="05945-108">Narzędzie generuje kod klienta i konfiguracji dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="05945-108">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="05945-109">Klient jest zbudowany w dwóch częściach.</span><span class="sxs-lookup"><span data-stu-id="05945-109">The client is built in two parts.</span></span> <span data-ttu-id="05945-110">Svcutil.exe `ClientCalculator` generuje, który implementuje `ICalculator` interfejs.</span><span class="sxs-lookup"><span data-stu-id="05945-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="05945-111">Ta aplikacja kliencka jest następnie konstruowana przez skonstruowanie wystąpienia . `ClientCalculator`</span><span class="sxs-lookup"><span data-stu-id="05945-111">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="05945-112">Zazwyczaj jest najlepszym rozwiązaniem, aby określić informacje dotyczące powiązania i adresu deklaratywnie w konfiguracji, a nie bezwzględnie w kodzie.</span><span class="sxs-lookup"><span data-stu-id="05945-112">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="05945-113">Definiowanie punktów końcowych w kodzie zwykle nie jest praktyczne, ponieważ powiązania i adresy dla wdrożonej usługi zazwyczaj różnią się od tych używanych podczas opracowywania usługi.</span><span class="sxs-lookup"><span data-stu-id="05945-113">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="05945-114">Bardziej ogólnie, utrzymywanie powiązanie i adresowanie informacji z kodu pozwala na ich zmiany bez konieczności ponownego kompilowania lub ponownego rozmieszczenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="05945-114">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="05945-115">Wszystkie następujące kroki konfiguracji można wykonać za pomocą [narzędzia Edytor konfiguracji (SvcConfigEditor.exe).](configuration-editor-tool-svcconfigeditor-exe.md)</span><span class="sxs-lookup"><span data-stu-id="05945-115">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="05945-116">Aby uzyskać kopię źródłową tego przykładu, zobacz [BasicBinding](./samples/basicbinding.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="05945-116">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="05945-117">Określanie powiązania klienta w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="05945-117">Specifying a client binding in configuration</span></span>  
  
1. <span data-ttu-id="05945-118">Użyj programu Svcutil.exe z wiersza polecenia, aby wygenerować kod z metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="05945-118">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="05945-119">Klient, który jest `ICalculator` generowany zawiera interfejs, który definiuje umowy serwisowej, że implementacja klienta musi spełniać.</span><span class="sxs-lookup"><span data-stu-id="05945-119">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. <span data-ttu-id="05945-120">Wygenerowany klient zawiera również `ClientCalculator`implementację pliku .</span><span class="sxs-lookup"><span data-stu-id="05945-120">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. <span data-ttu-id="05945-121">Svcutil.exe generuje również konfigurację dla klienta, <xref:System.ServiceModel.BasicHttpBinding> który używa klasy.</span><span class="sxs-lookup"><span data-stu-id="05945-121">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="05945-122">Podczas korzystania z programu Visual Studio, nazwa tego pliku App.config. Należy zauważyć, że adres i informacje o powiązaniach nie są określone w dowolnym miejscu wewnątrz implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="05945-122">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="05945-123">Ponadto kod nie musi być zapisywany, aby pobrać te informacje z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="05945-123">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]

5. <span data-ttu-id="05945-124">Utwórz wystąpienie `ClientCalculator` w aplikacji, a następnie wywołaj operacje usługi.</span><span class="sxs-lookup"><span data-stu-id="05945-124">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. <span data-ttu-id="05945-125">Skompiluj i uruchom klienta.</span><span class="sxs-lookup"><span data-stu-id="05945-125">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05945-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05945-126">See also</span></span>

- [<span data-ttu-id="05945-127">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="05945-127">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
