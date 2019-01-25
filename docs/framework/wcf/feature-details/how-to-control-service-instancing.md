---
title: 'Instrukcje: Tworzenie wystąpienia usługi kontroli'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
ms.openlocfilehash: 3e1e0669b083e30db01c571c44830adfaff31d79
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515316"
---
# <a name="how-to-control-service-instancing"></a><span data-ttu-id="c4f0d-102">Instrukcje: Tworzenie wystąpienia usługi kontroli</span><span class="sxs-lookup"><span data-stu-id="c4f0d-102">How to: Control Service Instancing</span></span>
<span data-ttu-id="c4f0d-103">Ustawianie trybu wystąpienia usługi pozwala na określenie, kiedy <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (i jego obiekt skojarzona usługa zdefiniowanych przez użytkownika) jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="c4f0d-103">Setting the instance mode of a service enables you to specify when a <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (and its associated user-defined service object) is created.</span></span> <span data-ttu-id="c4f0d-104">Zobacz <xref:System.ServiceModel.InstanceContextMode> wyliczenie dla możliwe tryby.</span><span class="sxs-lookup"><span data-stu-id="c4f0d-104">See the <xref:System.ServiceModel.InstanceContextMode> enumeration for the possible modes.</span></span> <span data-ttu-id="c4f0d-105">Aby uzyskać więcej informacji na temat zachowań, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="c4f0d-105">For more information about behaviors, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span> <span data-ttu-id="c4f0d-106">Przykłady pracy, zobacz [zachowania](../../../../docs/framework/wcf/samples/behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="c4f0d-106">For working examples, see [Behaviors](../../../../docs/framework/wcf/samples/behaviors.md).</span></span>  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a><span data-ttu-id="c4f0d-107">Aby kontrolować okres istnienia wystąpienia usługi przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="c4f0d-107">To control the service instance lifetime using code</span></span>  
  
1.  <span data-ttu-id="c4f0d-108">Zastosuj <xref:System.ServiceModel.ServiceBehaviorAttribute> klasę usługi.</span><span class="sxs-lookup"><span data-stu-id="c4f0d-108">Apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> to the service class.</span></span>  
  
2.  <span data-ttu-id="c4f0d-109">Ustaw <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość na jedną z następujących wartości: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, lub <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="c4f0d-109">Set the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property to one of the following values: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, or <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span>  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="c4f0d-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4f0d-110">Example</span></span>  
 <span data-ttu-id="c4f0d-111">Poniższy kod ustawia przykład <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu <xref:System.ServiceModel.InstanceContextMode.PerCall>.</span><span class="sxs-lookup"><span data-stu-id="c4f0d-111">The following code example sets the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property of the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to <xref:System.ServiceModel.InstanceContextMode.PerCall>.</span></span>  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="c4f0d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4f0d-112">See also</span></span>
- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>
- <xref:System.ServiceModel.InstanceContextMode>
- [<span data-ttu-id="c4f0d-113">Usługa: Przykłady zachowania</span><span class="sxs-lookup"><span data-stu-id="c4f0d-113">Service: Behaviors Samples</span></span>](https://msdn.microsoft.com/library/4e3c6513-a7ff-4b35-8dcf-b5506c6f39a7)
