---
title: 'Instrukcje: Określanie powiązania klienta w kodzie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: c95e30c65c6096140fca0c1241e76fbc7af4df3d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59303443"
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="97c96-102">Instrukcje: Określanie powiązania klienta w kodzie</span><span class="sxs-lookup"><span data-stu-id="97c96-102">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="97c96-103">W tym przykładzie zostanie utworzona usługa Kalkulator klienta i obowiązkowo określono powiązania dla tego klienta w kodzie.</span><span class="sxs-lookup"><span data-stu-id="97c96-103">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="97c96-104">Klient uzyskuje dostęp do `CalculatorService`, który implementuje `ICalculator` interfejsu i usługi oraz klienta, użyj <xref:System.ServiceModel.BasicHttpBinding> klasy.</span><span class="sxs-lookup"><span data-stu-id="97c96-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="97c96-105">W tej procedurze założono, że usługa Kalkulator jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="97c96-105">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="97c96-106">Aby uzyskać informacje o tworzeniu usługi, zobacz [jak: Określanie wiązań usługi w konfiguracji](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="97c96-106">For information about building the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="97c96-107">Korzysta również [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) umożliwia automatyczne generowanie składniki klienta.</span><span class="sxs-lookup"><span data-stu-id="97c96-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="97c96-108">Narzędzie generuje kod klienta do uzyskania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="97c96-108">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="97c96-109">Klient została stworzona w dwóch częściach.</span><span class="sxs-lookup"><span data-stu-id="97c96-109">The client is built in two parts.</span></span> <span data-ttu-id="97c96-110">Generuje svcutil.exe `ClientCalculator` implementującej `ICalculator` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="97c96-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="97c96-111">Ta aplikacja kliencka jest następnie tworzony przez utworzenie wystąpienia `ClientCalculator` , a następnie określając powiązania i adres usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="97c96-111">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="97c96-112">Źródło kopię w tym przykładzie można zobaczyć [element basicbinding elementem](../../../docs/framework/wcf/samples/basicbinding.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="97c96-112">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="97c96-113">Aby określić niestandardowe powiązanie w kodzie</span><span class="sxs-lookup"><span data-stu-id="97c96-113">To specify a custom binding in code</span></span>  
  
1. <span data-ttu-id="97c96-114">Umożliwia Svcutil.exe w wierszu polecenia generowanie kodu na podstawie metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="97c96-114">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. <span data-ttu-id="97c96-115">Klient, który jest generowany zawiera `ICalculator` Interfejs definiujący kontrakt usługi, które muszą spełniać implementacji klienta.</span><span class="sxs-lookup"><span data-stu-id="97c96-115">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. <span data-ttu-id="97c96-116">Wygenerowanego klienta zawiera również implementację `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="97c96-116">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. <span data-ttu-id="97c96-117">Utwórz wystąpienie obiektu `ClientCalculator` , który używa <xref:System.ServiceModel.BasicHttpBinding> klasy w aplikacji klienckiej, a następnie Wywołaj operacje usług pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="97c96-117">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. <span data-ttu-id="97c96-118">Kompilowanie i uruchamianie klienta.</span><span class="sxs-lookup"><span data-stu-id="97c96-118">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97c96-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97c96-119">See also</span></span>

- [<span data-ttu-id="97c96-120">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="97c96-120">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
