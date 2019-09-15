---
title: 'Instrukcje: Określanie powiązania klienta w kodzie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 37769a84ca623e2f7f246d36180aa17537e90bfa
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990236"
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="70ec5-102">Instrukcje: Określanie powiązania klienta w kodzie</span><span class="sxs-lookup"><span data-stu-id="70ec5-102">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="70ec5-103">W tym przykładzie klient został utworzony w celu korzystania z usługi kalkulatora, a powiązanie dla tego klienta jest określone w kodzie.</span><span class="sxs-lookup"><span data-stu-id="70ec5-103">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="70ec5-104">Klient uzyskuje dostęp `CalculatorService`do, który `ICalculator` implementuje interfejs, a zarówno usługa, <xref:System.ServiceModel.BasicHttpBinding> jak i klient używają klasy.</span><span class="sxs-lookup"><span data-stu-id="70ec5-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="70ec5-105">W tej procedurze przyjęto założenie, że usługa kalkulatora jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="70ec5-105">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="70ec5-106">Aby uzyskać informacje na temat tworzenia usługi, [zobacz How to: Określ powiązanie usługi w konfiguracji](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="70ec5-106">For information about building the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="70ec5-107">Używa także [narzędzia Svcutil. exe (narzędzie do przesyłania metadanych Windows Communication Foundation)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)(WCF) zapewnia automatyczne generowanie składników klienta.</span><span class="sxs-lookup"><span data-stu-id="70ec5-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="70ec5-108">Narzędzie generuje kod klienta na potrzeby uzyskiwania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="70ec5-108">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="70ec5-109">Klient jest skompilowany w dwóch częściach.</span><span class="sxs-lookup"><span data-stu-id="70ec5-109">The client is built in two parts.</span></span> <span data-ttu-id="70ec5-110">Svcutil. exe generuje `ClientCalculator` , który `ICalculator` implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="70ec5-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="70ec5-111">Ta aplikacja kliencka jest następnie tworzona przez konstruowanie wystąpienia `ClientCalculator` , a następnie określenie powiązania i adresu usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="70ec5-111">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="70ec5-112">Aby uzyskać kopię źródła tego przykładu, zobacz przykład [podstawowabinding](../../../docs/framework/wcf/samples/basicbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="70ec5-112">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="70ec5-113">Aby określić niestandardowe powiązanie w kodzie</span><span class="sxs-lookup"><span data-stu-id="70ec5-113">To specify a custom binding in code</span></span>  
  
1. <span data-ttu-id="70ec5-114">Użyj Svcutil. exe z wiersza polecenia w celu wygenerowania kodu z metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="70ec5-114">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. <span data-ttu-id="70ec5-115">Wygenerowany klient zawiera `ICalculator` interfejs, który definiuje kontrakt usługi, który musi spełniać implementacja klienta.</span><span class="sxs-lookup"><span data-stu-id="70ec5-115">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. <span data-ttu-id="70ec5-116">Wygenerowany klient również zawiera implementację `ClientCalculator`programu.</span><span class="sxs-lookup"><span data-stu-id="70ec5-116">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. <span data-ttu-id="70ec5-117">Utwórz wystąpienie `ClientCalculator` , które <xref:System.ServiceModel.BasicHttpBinding> używa klasy w aplikacji klienckiej, a następnie Wywołaj operacje usługi pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="70ec5-117">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. <span data-ttu-id="70ec5-118">Kompiluj i uruchom klienta.</span><span class="sxs-lookup"><span data-stu-id="70ec5-118">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70ec5-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70ec5-119">See also</span></span>

- [<span data-ttu-id="70ec5-120">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="70ec5-120">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
