---
title: 'Instrukcje: Określanie powiązania klienta w kodzie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 3a05c60b6e68f87c31e74774bf0b50e535477b56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498374"
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="5d0eb-102">Instrukcje: Określanie powiązania klienta w kodzie</span><span class="sxs-lookup"><span data-stu-id="5d0eb-102">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="5d0eb-103">W tym przykładzie klient jest tworzony na korzystanie z usługi Kalkulator i imperatively określono powiązania dla tego klienta w kodzie.</span><span class="sxs-lookup"><span data-stu-id="5d0eb-103">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="5d0eb-104">Klient uzyskuje dostęp do `CalculatorService`, który implementuje `ICalculator` interfejsu i usługę i klienta, użyj <xref:System.ServiceModel.BasicHttpBinding> klasy.</span><span class="sxs-lookup"><span data-stu-id="5d0eb-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="5d0eb-105">W tej procedurze założono, że jest uruchomiona usługa Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="5d0eb-105">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="5d0eb-106">Dla informacji o tworzeniu usługi, zobacz [porady: Określanie powiązania usługi w konfiguracji](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="5d0eb-106">For information about building the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="5d0eb-107">Ponadto użyto [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) umożliwia automatyczne generowanie składniki klienta.</span><span class="sxs-lookup"><span data-stu-id="5d0eb-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="5d0eb-108">Narzędzie generuje kod klienta do uzyskiwania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="5d0eb-108">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="5d0eb-109">Klient korzysta z wbudowanej w dwóch częściach.</span><span class="sxs-lookup"><span data-stu-id="5d0eb-109">The client is built in two parts.</span></span> <span data-ttu-id="5d0eb-110">Generuje svcutil.exe `ClientCalculator` implementującej `ICalculator` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5d0eb-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="5d0eb-111">Ta aplikacja kliencka jest następnie tworzony przez tworzenia wystąpienia `ClientCalculator` , a następnie określając powiązanie i adres dla usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="5d0eb-111">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="5d0eb-112">Dla źródła kopię w tym przykładzie [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="5d0eb-112">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="5d0eb-113">Aby określić niestandardowego powiązania w kodzie</span><span class="sxs-lookup"><span data-stu-id="5d0eb-113">To specify a custom binding in code</span></span>  
  
1.  <span data-ttu-id="5d0eb-114">Użyj Svcutil.exe w wierszu polecenia, aby wygenerować kod na podstawie metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="5d0eb-114">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  <span data-ttu-id="5d0eb-115">Klient, który jest generowany zawiera `ICalculator` Interfejs definiujący kontrakt usługi, które muszą spełniać implementacja klienta.</span><span class="sxs-lookup"><span data-stu-id="5d0eb-115">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3.  <span data-ttu-id="5d0eb-116">Wygenerowanego klienta zawiera także wykonania `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="5d0eb-116">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4.  <span data-ttu-id="5d0eb-117">Utwórz wystąpienie `ClientCalculator` używającą <xref:System.ServiceModel.BasicHttpBinding> klasy w aplikacji klienta, a następnie wywołać operacji usługi pod określonym adresem.</span><span class="sxs-lookup"><span data-stu-id="5d0eb-117">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5.  <span data-ttu-id="5d0eb-118">Kompilowanie i uruchamianie klienta.</span><span class="sxs-lookup"><span data-stu-id="5d0eb-118">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d0eb-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d0eb-119">See Also</span></span>  
 [<span data-ttu-id="5d0eb-120">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="5d0eb-120">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
