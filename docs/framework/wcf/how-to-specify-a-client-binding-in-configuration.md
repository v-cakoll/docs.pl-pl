---
title: 'Instrukcje: Określanie wiązań klienta w konfiguracji'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: b16f4b062f7f97a5855b06bdcf348911ee0497d2
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320862"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="614b0-102">Instrukcje: Określanie wiązań klienta w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="614b0-102">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="614b0-103">W tym przykładzie aplikacja konsoli klienta zostanie utworzona w celu korzystania z usługi kalkulatora, a powiązanie dla tego klienta jest określone w konfiguracji w sposób deklaratywny.</span><span class="sxs-lookup"><span data-stu-id="614b0-103">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="614b0-104">Klient uzyskuje dostęp do `CalculatorService`, który implementuje interfejs `ICalculator`, a zarówno usługa, jak i klient używają klasy <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="614b0-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="614b0-105">W opisanej procedurze przyjęto założenie, że usługa kalkulatora jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="614b0-105">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="614b0-106">Aby uzyskać informacje na temat sposobu tworzenia usługi, zobacz [How to: Określanie powiązania usługi w konfiguracji](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="614b0-106">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="614b0-107">Używa także narzędzia do [przesyłania metadanych modelu ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) , które zapewnia Windows Communication Foundation (WCF), aby automatycznie generować składniki klienta.</span><span class="sxs-lookup"><span data-stu-id="614b0-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) that Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="614b0-108">Narzędzie generuje kod klienta i konfigurację w celu uzyskania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="614b0-108">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="614b0-109">Klient jest skompilowany w dwóch częściach.</span><span class="sxs-lookup"><span data-stu-id="614b0-109">The client is built in two parts.</span></span> <span data-ttu-id="614b0-110">Svcutil. exe generuje `ClientCalculator` implementujący interfejs `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="614b0-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="614b0-111">Ta aplikacja kliencka jest następnie tworzona przez konstruowanie wystąpienia `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="614b0-111">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="614b0-112">Zazwyczaj najlepszym rozwiązaniem jest określenie informacji o powiązaniach i adresie w konfiguracji, a nie w sposób konieczny w kodzie.</span><span class="sxs-lookup"><span data-stu-id="614b0-112">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="614b0-113">Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne, ponieważ powiązania i adresy dla wdrożonej usługi są zwykle inne niż te używane podczas tworzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="614b0-113">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="614b0-114">Ogólnie rzecz biorąc, przechowywanie informacji o powiązaniach i adresach poza kodem pozwala na ich zmianę bez konieczności ponownego kompilowania lub wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="614b0-114">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="614b0-115">Wszystkie poniższe kroki konfiguracji można wykonać za pomocą [Narzędzia Edytora konfiguracji (SvcConfigEditor. exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="614b0-115">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="614b0-116">Aby uzyskać kopię źródła tego przykładu, zobacz przykład [podstawowabinding](./samples/basicbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="614b0-116">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="614b0-117">Określanie powiązania klienta w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="614b0-117">Specifying a client binding in configuration</span></span>  
  
1. <span data-ttu-id="614b0-118">Użyj Svcutil. exe z wiersza polecenia w celu wygenerowania kodu z metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="614b0-118">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. <span data-ttu-id="614b0-119">Wygenerowany klient zawiera interfejs `ICalculator`, który definiuje kontrakt usługi, który musi spełniać implementacja klienta.</span><span class="sxs-lookup"><span data-stu-id="614b0-119">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. <span data-ttu-id="614b0-120">Wygenerowany klient również zawiera implementację `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="614b0-120">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. <span data-ttu-id="614b0-121">Svcutil. exe generuje również konfigurację dla klienta, który używa klasy <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="614b0-121">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="614b0-122">W przypadku korzystania z programu Visual Studio Nazwij ten plik App. config. Należy zauważyć, że informacje o adresie i powiązaniu nie są określone w dowolnym miejscu w ramach implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="614b0-122">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="614b0-123">Ponadto kod nie musi być zapisany, aby można było pobrać te informacje z pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="614b0-123">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5. <span data-ttu-id="614b0-124">Utwórz wystąpienie `ClientCalculator` w aplikacji, a następnie Wywołaj operacje usługi.</span><span class="sxs-lookup"><span data-stu-id="614b0-124">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. <span data-ttu-id="614b0-125">Kompiluj i uruchom klienta.</span><span class="sxs-lookup"><span data-stu-id="614b0-125">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="614b0-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="614b0-126">See also</span></span>

- [<span data-ttu-id="614b0-127">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="614b0-127">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
