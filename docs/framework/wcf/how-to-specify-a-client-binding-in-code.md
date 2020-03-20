---
title: 'Instrukcje: Określanie wiązania klienta w kodzie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 9be571d7be020aef546fdd7ec7cb7519a48ea350
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184055"
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="017bf-102">Instrukcje: Określanie wiązania klienta w kodzie</span><span class="sxs-lookup"><span data-stu-id="017bf-102">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="017bf-103">W tym przykładzie klient jest tworzony do korzystania z usługi kalkulatora i powiązanie dla tego klienta jest określony bezwzględnie w kodzie.</span><span class="sxs-lookup"><span data-stu-id="017bf-103">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="017bf-104">Klient uzyskuje dostęp `CalculatorService`do , `ICalculator` który implementuje interfejs, a zarówno <xref:System.ServiceModel.BasicHttpBinding> usługi i klienta używać klasy.</span><span class="sxs-lookup"><span data-stu-id="017bf-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="017bf-105">Ta procedura zakłada, że usługa kalkulatora jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="017bf-105">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="017bf-106">Aby uzyskać informacje na temat tworzenia usługi, zobacz [Jak: Określanie powiązania usługi w konfiguracji](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="017bf-106">For information about building the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="017bf-107">Używa również [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) zapewnia do automatycznego generowania składników klienta.</span><span class="sxs-lookup"><span data-stu-id="017bf-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="017bf-108">Narzędzie generuje kod klienta dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="017bf-108">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="017bf-109">Klient jest zbudowany w dwóch częściach.</span><span class="sxs-lookup"><span data-stu-id="017bf-109">The client is built in two parts.</span></span> <span data-ttu-id="017bf-110">Svcutil.exe `ClientCalculator` generuje, który implementuje `ICalculator` interfejs.</span><span class="sxs-lookup"><span data-stu-id="017bf-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="017bf-111">Ta aplikacja kliencka jest następnie konstruowana przez konstruowanie wystąpienia, `ClientCalculator` a następnie określanie powiązania i adresu dla usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="017bf-111">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="017bf-112">Aby uzyskać kopię źródłową tego przykładu, zobacz [BasicBinding](./samples/basicbinding.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="017bf-112">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="017bf-113">Aby określić niestandardowe powiązanie w kodzie</span><span class="sxs-lookup"><span data-stu-id="017bf-113">To specify a custom binding in code</span></span>  
  
1. <span data-ttu-id="017bf-114">Użyj programu Svcutil.exe z wiersza polecenia, aby wygenerować kod z metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="017bf-114">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="017bf-115">Klient, który jest `ICalculator` generowany zawiera interfejs, który definiuje umowy serwisowej, że implementacja klienta musi spełniać.</span><span class="sxs-lookup"><span data-stu-id="017bf-115">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. <span data-ttu-id="017bf-116">Wygenerowany klient zawiera również `ClientCalculator`implementację pliku .</span><span class="sxs-lookup"><span data-stu-id="017bf-116">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. <span data-ttu-id="017bf-117">Utwórz `ClientCalculator` wystąpienie, które <xref:System.ServiceModel.BasicHttpBinding> używa klasy w aplikacji klienckiej, a następnie wywołać operacje usługi pod określonym adresem.</span><span class="sxs-lookup"><span data-stu-id="017bf-117">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. <span data-ttu-id="017bf-118">Skompiluj i uruchom klienta.</span><span class="sxs-lookup"><span data-stu-id="017bf-118">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="017bf-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="017bf-119">See also</span></span>

- [<span data-ttu-id="017bf-120">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="017bf-120">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
