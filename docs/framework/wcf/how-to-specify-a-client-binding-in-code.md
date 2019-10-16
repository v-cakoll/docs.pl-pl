---
title: 'Instrukcje: Określanie wiązania klienta w kodzie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: ec5db7a305a63ac7ae9c2e2a7bb1c9c7691b8daa
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320888"
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="2dffb-102">Instrukcje: Określanie wiązania klienta w kodzie</span><span class="sxs-lookup"><span data-stu-id="2dffb-102">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="2dffb-103">W tym przykładzie klient został utworzony w celu korzystania z usługi kalkulatora, a powiązanie dla tego klienta jest określone w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2dffb-103">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="2dffb-104">Klient uzyskuje dostęp do `CalculatorService`, który implementuje interfejs `ICalculator`, a zarówno usługa, jak i klient używają klasy <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="2dffb-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="2dffb-105">W tej procedurze przyjęto założenie, że usługa kalkulatora jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="2dffb-105">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="2dffb-106">Aby uzyskać informacje na temat tworzenia usługi, zobacz [How to: Określanie powiązania usługi w konfiguracji](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="2dffb-106">For information about building the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="2dffb-107">Używa także [narzędzia Svcutil. exe (narzędzie do przesyłania metadanych Windows Communication Foundation)](servicemodel-metadata-utility-tool-svcutil-exe.md)(WCF) zapewnia automatyczne generowanie składników klienta.</span><span class="sxs-lookup"><span data-stu-id="2dffb-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="2dffb-108">Narzędzie generuje kod klienta na potrzeby uzyskiwania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="2dffb-108">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="2dffb-109">Klient jest skompilowany w dwóch częściach.</span><span class="sxs-lookup"><span data-stu-id="2dffb-109">The client is built in two parts.</span></span> <span data-ttu-id="2dffb-110">Svcutil. exe generuje `ClientCalculator` implementujący interfejs `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="2dffb-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="2dffb-111">Ta aplikacja kliencka jest następnie tworzona przez konstruowanie wystąpienia `ClientCalculator`, a następnie określenie powiązania i adresu usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2dffb-111">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="2dffb-112">Aby uzyskać kopię źródła tego przykładu, zobacz przykład [podstawowabinding](./samples/basicbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="2dffb-112">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="2dffb-113">Aby określić niestandardowe powiązanie w kodzie</span><span class="sxs-lookup"><span data-stu-id="2dffb-113">To specify a custom binding in code</span></span>  
  
1. <span data-ttu-id="2dffb-114">Użyj Svcutil. exe z wiersza polecenia w celu wygenerowania kodu z metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="2dffb-114">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. <span data-ttu-id="2dffb-115">Wygenerowany klient zawiera interfejs `ICalculator`, który definiuje kontrakt usługi, który musi spełniać implementacja klienta.</span><span class="sxs-lookup"><span data-stu-id="2dffb-115">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. <span data-ttu-id="2dffb-116">Wygenerowany klient również zawiera implementację `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="2dffb-116">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. <span data-ttu-id="2dffb-117">Utwórz wystąpienie `ClientCalculator`, które używa klasy <xref:System.ServiceModel.BasicHttpBinding> w aplikacji klienckiej, a następnie Wywołaj operacje usługi o określonym adresie.</span><span class="sxs-lookup"><span data-stu-id="2dffb-117">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. <span data-ttu-id="2dffb-118">Kompiluj i uruchom klienta.</span><span class="sxs-lookup"><span data-stu-id="2dffb-118">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dffb-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2dffb-119">See also</span></span>

- [<span data-ttu-id="2dffb-120">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="2dffb-120">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
