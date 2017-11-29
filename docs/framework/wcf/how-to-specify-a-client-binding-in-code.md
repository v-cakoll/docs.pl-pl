---
title: "Instrukcje: Określanie wiązania klienta w kodzie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 50b27432081f15955ef7ccd63e91a7cbd75d50f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="50f79-102">Instrukcje: Określanie wiązania klienta w kodzie</span><span class="sxs-lookup"><span data-stu-id="50f79-102">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="50f79-103">W tym przykładzie klient jest tworzony na korzystanie z usługi Kalkulator i imperatively określono powiązania dla tego klienta w kodzie.</span><span class="sxs-lookup"><span data-stu-id="50f79-103">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="50f79-104">Klient uzyskuje dostęp do `CalculatorService`, który implementuje `ICalculator` interfejsu i usługę i klienta, użyj <xref:System.ServiceModel.BasicHttpBinding> klasy.</span><span class="sxs-lookup"><span data-stu-id="50f79-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="50f79-105">W tej procedurze założono, że jest uruchomiona usługa Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="50f79-105">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="50f79-106">Dla informacji o tworzeniu usługi, zobacz [porady: Określanie powiązania usługi w konfiguracji](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="50f79-106">For information about building the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="50f79-107">Zastosowano [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] umożliwia automatyczne generowanie składników klienta.</span><span class="sxs-lookup"><span data-stu-id="50f79-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] provides to automatically generate the client components.</span></span> <span data-ttu-id="50f79-108">Narzędzie generuje kod klienta do uzyskiwania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="50f79-108">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="50f79-109">Klient korzysta z wbudowanej w dwóch częściach.</span><span class="sxs-lookup"><span data-stu-id="50f79-109">The client is built in two parts.</span></span> <span data-ttu-id="50f79-110">Generuje svcutil.exe `ClientCalculator` implementującej `ICalculator` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="50f79-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="50f79-111">Ta aplikacja kliencka jest następnie tworzony przez tworzenia wystąpienia `ClientCalculator` , a następnie określając powiązanie i adres dla usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="50f79-111">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="50f79-112">Dla źródła kopię w tym przykładzie [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="50f79-112">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="50f79-113">Aby określić niestandardowego powiązania w kodzie</span><span class="sxs-lookup"><span data-stu-id="50f79-113">To specify a custom binding in code</span></span>  
  
1.  <span data-ttu-id="50f79-114">Użyj Svcutil.exe w wierszu polecenia, aby wygenerować kod na podstawie metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="50f79-114">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  <span data-ttu-id="50f79-115">Klient, który jest generowany zawiera `ICalculator` Interfejs definiujący kontrakt usługi, które muszą spełniać implementacja klienta.</span><span class="sxs-lookup"><span data-stu-id="50f79-115">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3.  <span data-ttu-id="50f79-116">Wygenerowanego klienta zawiera także wykonania `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="50f79-116">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4.  <span data-ttu-id="50f79-117">Utwórz wystąpienie `ClientCalculator` używającą <xref:System.ServiceModel.BasicHttpBinding> klasy w aplikacji klienta, a następnie wywołać operacji usługi pod określonym adresem.</span><span class="sxs-lookup"><span data-stu-id="50f79-117">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5.  <span data-ttu-id="50f79-118">Kompilowanie i uruchamianie klienta.</span><span class="sxs-lookup"><span data-stu-id="50f79-118">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50f79-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50f79-119">See Also</span></span>  
 [<span data-ttu-id="50f79-120">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="50f79-120">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
