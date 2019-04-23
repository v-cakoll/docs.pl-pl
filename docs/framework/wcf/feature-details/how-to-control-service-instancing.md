---
title: 'Instrukcje: tworzenie wystąpienia usługi kontroli'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
ms.openlocfilehash: e8efbc5a3dec5f60dbefc8f6dc377d97b29b7653
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59330184"
---
# <a name="how-to-control-service-instancing"></a>Instrukcje: tworzenie wystąpienia usługi kontroli
Ustawianie trybu wystąpienia usługi pozwala na określenie, kiedy <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (i jego obiekt skojarzona usługa zdefiniowanych przez użytkownika) jest tworzony. Zobacz <xref:System.ServiceModel.InstanceContextMode> wyliczenie dla możliwe tryby. Aby uzyskać więcej informacji na temat zachowań, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md). Przykłady pracy, zobacz [zachowania](../../../../docs/framework/wcf/samples/behaviors.md).  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a>Aby kontrolować okres istnienia wystąpienia usługi przy użyciu kodu  
  
1. Zastosuj <xref:System.ServiceModel.ServiceBehaviorAttribute> klasę usługi.  
  
2. Ustaw <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość na jedną z następujących wartości: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, lub <xref:System.ServiceModel.InstanceContextMode.Single>.  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod ustawia przykład <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu <xref:System.ServiceModel.InstanceContextMode.PerCall>.  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>
- <xref:System.ServiceModel.InstanceContextMode>
- [Usługa: Przykłady zachowania](../samples/behaviors.md)
