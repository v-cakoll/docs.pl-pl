---
title: 'Instrukcje: Określanie powiązań usługi w kodzie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 67ab5dd8-79c1-4e62-aa75-828ea918a53a
ms.openlocfilehash: 3c6cfd084055d59d3292b49897ff710f14f92737
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320873"
---
# <a name="how-to-specify-a-service-binding-in-code"></a><span data-ttu-id="6c14c-102">Instrukcje: Określanie powiązań usługi w kodzie</span><span class="sxs-lookup"><span data-stu-id="6c14c-102">How to: Specify a Service Binding in Code</span></span>
<span data-ttu-id="6c14c-103">W tym przykładzie jest definiowana umowa `ICalculator` dla usługi kalkulatora, usługa jest zaimplementowana w klasie `CalculatorService`, a następnie jej punkt końcowy jest zdefiniowany w kodzie, w którym jest określony, że usługa musi używać klasy <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="6c14c-103">In this example, an `ICalculator` contract is defined for a calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is defined in code, where it is specified that the service must use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="6c14c-104">Zazwyczaj najlepszym rozwiązaniem jest określenie informacji o powiązaniach i adresie w konfiguracji, a nie w sposób konieczny w kodzie.</span><span class="sxs-lookup"><span data-stu-id="6c14c-104">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="6c14c-105">Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne, ponieważ powiązania i adresy dla wdrożonej usługi są zwykle inne niż te używane podczas tworzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="6c14c-105">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="6c14c-106">Ogólnie rzecz biorąc, przechowywanie informacji o powiązaniach i adresach poza kodem pozwala na ich zmianę bez konieczności ponownego kompilowania lub wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6c14c-106">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="6c14c-107">Opis sposobu konfigurowania tej usługi przy użyciu elementów konfiguracji zamiast kodu znajduje się [w temacie How to: Określanie powiązania usługi w konfiguracji](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="6c14c-107">For a description of how to configure this service using configuration elements instead of code, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
### <a name="to-specify-in-code-to-use-the-basichttpbinding-for-the-service"></a><span data-ttu-id="6c14c-108">Aby określić w kodzie, aby użyć BasicHttpBinding dla usługi</span><span class="sxs-lookup"><span data-stu-id="6c14c-108">To specify in code to use the BasicHttpBinding for the service</span></span>  
  
1. <span data-ttu-id="6c14c-109">Zdefiniuj kontrakt usługi dla typu usługi.</span><span class="sxs-lookup"><span data-stu-id="6c14c-109">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. <span data-ttu-id="6c14c-110">Zaimplementuj kontrakt usługi w klasie usługi.</span><span class="sxs-lookup"><span data-stu-id="6c14c-110">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. <span data-ttu-id="6c14c-111">W aplikacji hostingowej Utwórz adres podstawowy usługi i powiązanie, które ma być używane z usługą.</span><span class="sxs-lookup"><span data-stu-id="6c14c-111">In the hosting application, create the base address for the service and the binding to use with the service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. <span data-ttu-id="6c14c-112">Utwórz hosta dla usługi, Dodaj punkt końcowy, a następnie otwórz hosta.</span><span class="sxs-lookup"><span data-stu-id="6c14c-112">Create the host for the service, add the endpoint, and then open the host.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#4)]
     [!code-vb[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#4)]  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="6c14c-113">Aby zmodyfikować wartości domyślne właściwości powiązania</span><span class="sxs-lookup"><span data-stu-id="6c14c-113">To modify the default values of the binding properties</span></span>  
  
1. <span data-ttu-id="6c14c-114">Aby zmodyfikować jedną z domyślnych wartości właściwości <xref:System.ServiceModel.BasicHttpBinding>, przed utworzeniem hosta ustaw wartość właściwości w powiązaniu z nową wartością.</span><span class="sxs-lookup"><span data-stu-id="6c14c-114">To modify one of the default property values of the <xref:System.ServiceModel.BasicHttpBinding> class, set the property value on the binding to the new value before creating the host.</span></span> <span data-ttu-id="6c14c-115">Na przykład aby zmienić domyślne wartości limitu czasu otwarcia i zamknięcia wynoszące 1 minutę na 2 minuty, użyj poniższego.</span><span class="sxs-lookup"><span data-stu-id="6c14c-115">For example, to change the default open and close timeout values of 1 minute to 2 minutes, use the following.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#5)]
     [!code-vb[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="6c14c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c14c-116">See also</span></span>

- [<span data-ttu-id="6c14c-117">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="6c14c-117">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6c14c-118">Określanie adresu punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="6c14c-118">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)
