---
title: 'Instrukcje: tworzenie punktu końcowego w kodzie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fbb22fa-2930-48b8-b437-def1de87c6a0
ms.openlocfilehash: 9b7b983122b9e30fd7c6b0d0c517a9483b8881c5
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301465"
---
# <a name="how-to-create-a-service-endpoint-in-code"></a><span data-ttu-id="9feba-102">Instrukcje: tworzenie punktu końcowego w kodzie</span><span class="sxs-lookup"><span data-stu-id="9feba-102">How to: Create a Service Endpoint in Code</span></span>
<span data-ttu-id="9feba-103">W tym przykładzie `ICalculator` kontraktu jest zdefiniowany dla usługi Kalkulator, usługa jest wdrażana w `CalculatorService` klasy, a następnie jej punkt końcowy jest zdefiniowana w kodzie, w której jest określony, że należy używać usługa programu <xref:System.ServiceModel.BasicHttpBinding> klasy.</span><span class="sxs-lookup"><span data-stu-id="9feba-103">In this example, an `ICalculator` contract is defined for a calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is defined in code, where it is specified that the service must use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="9feba-104">Jest zwykle najlepszym rozwiązaniem jest, aby określić powiązanie i informacje o adresie deklaratywnie w konfiguracji, a nie obowiązkowo w kodzie.</span><span class="sxs-lookup"><span data-stu-id="9feba-104">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="9feba-105">Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne ponieważ powiązań i adresów dla wdrożonej usługi są zazwyczaj inne niż używane, gdy usługa jest obecnie sporządzana.</span><span class="sxs-lookup"><span data-stu-id="9feba-105">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="9feba-106">Ogólnie rzecz biorąc zachowanie wiązania i adresowanie z kodu pozwala na zmianę bez konieczności ponownego kompilowania lub ponownego wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9feba-106">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
#### <a name="to-create-a-service-endpoint-in-code"></a><span data-ttu-id="9feba-107">Aby utworzyć punkt końcowy usługi w kodzie</span><span class="sxs-lookup"><span data-stu-id="9feba-107">To create a service endpoint in code</span></span>  
  
1. <span data-ttu-id="9feba-108">Utwórz interfejs, który definiuje kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="9feba-108">Create the interface that defines the service contract.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. <span data-ttu-id="9feba-109">Implementowanie kontraktu usługi, zdefiniowane w kroku 1.</span><span class="sxs-lookup"><span data-stu-id="9feba-109">Implement the service contract defined in step 1.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. <span data-ttu-id="9feba-110">W aplikacji macierzystej Utwórz adres podstawowy dla usługi i powiązania do użycia z usługą.</span><span class="sxs-lookup"><span data-stu-id="9feba-110">In the hosting application, create the base address for the service and the binding to be used with the service.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. <span data-ttu-id="9feba-111">Tworzenie hosta i wywołania <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=nameWithType> lub jednego z innych przeciążeń, aby dodać punkt końcowy usługi dla hosta.</span><span class="sxs-lookup"><span data-stu-id="9feba-111">Create the host and call <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=nameWithType> or one of the other overloads to add the service endpoint for the host.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#6)]
     [!code-vb[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#6)]  
  
     <span data-ttu-id="9feba-112">Aby określić powiązanie w kodzie, ale Użyj domyślnych punktów końcowych, udostępniane przez środowisko uruchomieniowe, Przekaż adres podstawowy do konstruktora podczas tworzenia <xref:System.ServiceModel.ServiceHost>, a nie wywołuj <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9feba-112">To specify the binding in code but to use the default endpoints provided by the runtime, pass the base address into the constructor when creating the <xref:System.ServiceModel.ServiceHost>, and do not call <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#7)]
     [!code-vb[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#7)]  
  
     <span data-ttu-id="9feba-113">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="9feba-113">For more information about default endpoints, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9feba-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9feba-114">See also</span></span>

- [<span data-ttu-id="9feba-115">Instrukcje: Określanie wiązań usługi w kodzie</span><span class="sxs-lookup"><span data-stu-id="9feba-115">How to: Specify a Service Binding in Code</span></span>](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)
