---
title: 'Instrukcje: Określanie wiązań usługi w kodzie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 67ab5dd8-79c1-4e62-aa75-828ea918a53a
ms.openlocfilehash: f39b9d7bfdc1a5d8bf33c20f047738be1e41f226
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531215"
---
# <a name="how-to-specify-a-service-binding-in-code"></a><span data-ttu-id="e1ce5-102">Instrukcje: Określanie wiązań usługi w kodzie</span><span class="sxs-lookup"><span data-stu-id="e1ce5-102">How to: Specify a Service Binding in Code</span></span>
<span data-ttu-id="e1ce5-103">W tym przykładzie `ICalculator` kontraktu jest zdefiniowany dla usługi Kalkulator, usługa jest wdrażana w `CalculatorService` klasy, a następnie jej punkt końcowy jest zdefiniowana w kodzie, w której jest określony, że należy używać usługa programu <xref:System.ServiceModel.BasicHttpBinding> klasy.</span><span class="sxs-lookup"><span data-stu-id="e1ce5-103">In this example, an `ICalculator` contract is defined for a calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is defined in code, where it is specified that the service must use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="e1ce5-104">Jest zwykle najlepszym rozwiązaniem jest, aby określić powiązanie i informacje o adresie deklaratywnie w konfiguracji, a nie obowiązkowo w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e1ce5-104">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="e1ce5-105">Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne ponieważ powiązań i adresów dla wdrożonej usługi są zazwyczaj inne niż używane, gdy usługa jest obecnie sporządzana.</span><span class="sxs-lookup"><span data-stu-id="e1ce5-105">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="e1ce5-106">Ogólnie rzecz biorąc zachowanie wiązania i adresowanie z kodu pozwala na zmianę bez konieczności ponownego kompilowania lub ponownego wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1ce5-106">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="e1ce5-107">Aby uzyskać opis sposobu konfigurowania tej usługi, za pomocą elementów konfiguracji zamiast kodu, zobacz [jak: Określanie wiązań usługi w konfiguracji](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="e1ce5-107">For a description of how to configure this service using configuration elements instead of code, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
### <a name="to-specify-in-code-to-use-the-basichttpbinding-for-the-service"></a><span data-ttu-id="e1ce5-108">Aby określić w kodzie, aby użyć BasicHttpBinding usługi</span><span class="sxs-lookup"><span data-stu-id="e1ce5-108">To specify in code to use the BasicHttpBinding for the service</span></span>  
  
1.  <span data-ttu-id="e1ce5-109">Definiowanie kontraktu usługi dla typu usługi.</span><span class="sxs-lookup"><span data-stu-id="e1ce5-109">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2.  <span data-ttu-id="e1ce5-110">Implementowanie kontraktu usługi, w klasie usługi.</span><span class="sxs-lookup"><span data-stu-id="e1ce5-110">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3.  <span data-ttu-id="e1ce5-111">W aplikacji macierzystej Utwórz adres podstawowy dla usługi i powiązania w celu użycia z usługą.</span><span class="sxs-lookup"><span data-stu-id="e1ce5-111">In the hosting application, create the base address for the service and the binding to use with the service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4.  <span data-ttu-id="e1ce5-112">Utwórz hosta usługi, Dodaj punkt końcowy, a następnie otwórz hosta.</span><span class="sxs-lookup"><span data-stu-id="e1ce5-112">Create the host for the service, add the endpoint, and then open the host.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#4)]
     [!code-vb[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#4)]  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="e1ce5-113">Aby zmodyfikować domyślne wartości właściwości powiązania</span><span class="sxs-lookup"><span data-stu-id="e1ce5-113">To modify the default values of the binding properties</span></span>  
  
1.  <span data-ttu-id="e1ce5-114">Aby zmodyfikować jedną z domyślnych wartości właściwości z <xref:System.ServiceModel.BasicHttpBinding> klasy, ustaw wartość właściwości w powiązaniu na nową wartość przed utworzeniem hosta.</span><span class="sxs-lookup"><span data-stu-id="e1ce5-114">To modify one of the default property values of the <xref:System.ServiceModel.BasicHttpBinding> class, set the property value on the binding to the new value before creating the host.</span></span> <span data-ttu-id="e1ce5-115">Na przykład aby zmienić domyślne otwierających i zamykających wartości limitu czasu wynoszącym 1 minutę 2 minuty, należy użyć.</span><span class="sxs-lookup"><span data-stu-id="e1ce5-115">For example, to change the default open and close timeout values of 1 minute to 2 minutes, use the following.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#5)]
     [!code-vb[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="e1ce5-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1ce5-116">See also</span></span>
- [<span data-ttu-id="e1ce5-117">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="e1ce5-117">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e1ce5-118">Określanie adresu punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="e1ce5-118">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
