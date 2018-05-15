---
title: 'Instrukcje: Określanie powiązań klienta w konfiguracji'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: e2ea5a4b1c2ca9b661be5d4c653a3b5668bd26f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="25522-102">Instrukcje: Określanie powiązań klienta w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="25522-102">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="25522-103">W tym przykładzie utworzono aplikacji konsoli klienta do używania usługi Kalkulator i deklaratywnie określono powiązania dla tego klienta w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="25522-103">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="25522-104">Klient uzyskuje dostęp do `CalculatorService`, który implementuje `ICalculator` interfejsu i usługę i klienta, użyj <xref:System.ServiceModel.BasicHttpBinding> klasy.</span><span class="sxs-lookup"><span data-stu-id="25522-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="25522-105">Procedury opisane przyjęto założenie, że jest uruchomiona usługa Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="25522-105">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="25522-106">Aby uzyskać informacje o sposobie budowania usługi, zobacz [porady: Określanie powiązania usługi w konfiguracji](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="25522-106">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="25522-107">Zastosowano [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) czy Windows Communication Foundation (WCF) zapewnia automatyczne generowanie składników klienta.</span><span class="sxs-lookup"><span data-stu-id="25522-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) that Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="25522-108">Narzędzie generuje kod klienta i konfiguracji do uzyskiwania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="25522-108">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="25522-109">Klient korzysta z wbudowanej w dwóch częściach.</span><span class="sxs-lookup"><span data-stu-id="25522-109">The client is built in two parts.</span></span> <span data-ttu-id="25522-110">Generuje svcutil.exe `ClientCalculator` implementującej `ICalculator` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="25522-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="25522-111">Ta aplikacja kliencka jest następnie tworzony przez tworzenia wystąpienia `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="25522-111">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="25522-112">Jest zwykle najlepszym rozwiązaniem, aby określić powiązanie i informacje o adresie deklaratywnie w konfiguracji, a nie imperatively w kodzie.</span><span class="sxs-lookup"><span data-stu-id="25522-112">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="25522-113">Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne ponieważ powiązań i adresów dla wdrożonej usługi są zazwyczaj inne niż używane, gdy usługa jest obecnie opracowywane.</span><span class="sxs-lookup"><span data-stu-id="25522-113">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="25522-114">Ogólnie rzecz biorąc pamiętając powiązania i adresowanie poza kod umożliwia im to zmienić bez konieczności ponowne skompilowanie lub ponownego wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="25522-114">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="25522-115">Można wykonać następujące kroki konfiguracji za pomocą [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="25522-115">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="25522-116">Dla źródła kopię w tym przykładzie [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="25522-116">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="25522-117">Określanie powiązania w konfiguracji klienta</span><span class="sxs-lookup"><span data-stu-id="25522-117">Specifying a client binding in configuration</span></span>  
  
1.  <span data-ttu-id="25522-118">Użyj Svcutil.exe w wierszu polecenia, aby wygenerować kod na podstawie metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="25522-118">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  <span data-ttu-id="25522-119">Klient, który jest generowany zawiera `ICalculator` Interfejs definiujący kontrakt usługi, które muszą spełniać implementacja klienta.</span><span class="sxs-lookup"><span data-stu-id="25522-119">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3.  <span data-ttu-id="25522-120">Wygenerowanego klienta zawiera także wykonania `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="25522-120">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4.  <span data-ttu-id="25522-121">Svcutil.exe generuje również konfiguracji klienta, który używa <xref:System.ServiceModel.BasicHttpBinding> klasy.</span><span class="sxs-lookup"><span data-stu-id="25522-121">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="25522-122">Podczas korzystania z programu Visual Studio, nazwę tego pliku App.config. Należy pamiętać, że adres i informacje o powiązaniu nie określono dowolnym wewnątrz implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="25522-122">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="25522-123">Ponadto kodu nie ma do zapisania do pobierania informacji z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="25522-123">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5.  <span data-ttu-id="25522-124">Utwórz wystąpienie `ClientCalculator` w aplikacji, a następnie wywołać operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="25522-124">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6.  <span data-ttu-id="25522-125">Kompilowanie i uruchamianie klienta.</span><span class="sxs-lookup"><span data-stu-id="25522-125">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25522-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="25522-126">See Also</span></span>  
 [<span data-ttu-id="25522-127">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="25522-127">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
