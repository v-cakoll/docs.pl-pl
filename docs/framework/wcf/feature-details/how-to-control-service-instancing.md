---
title: 'Instrukcje: tworzenie wystąpienia usługi kontroli'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
ms.openlocfilehash: 8a73dd90d268c61e0df974861753119e205a870f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599077"
---
# <a name="how-to-control-service-instancing"></a>Instrukcje: tworzenie wystąpienia usługi kontroli
Ustawienie trybu wystąpienia usługi pozwala określić, kiedy <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> zostanie utworzony (i skojarzony z nim obiekt usługi zdefiniowany przez użytkownika). Zobacz <xref:System.ServiceModel.InstanceContextMode> Wyliczenie dla możliwych trybów. Aby uzyskać więcej informacji na temat zachowań, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../extending/configuring-and-extending-the-runtime-with-behaviors.md). Aby zapoznać się z przykładami roboczymi, zobacz [Behaviors](../samples/behaviors.md).  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a>Aby sterować okresem istnienia wystąpienia usługi przy użyciu kodu  
  
1. Zastosuj <xref:System.ServiceModel.ServiceBehaviorAttribute> do klasy usługi.  
  
2. Ustaw <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> Właściwość na jedną z następujących wartości: <xref:System.ServiceModel.InstanceContextMode.PerCall> , <xref:System.ServiceModel.InstanceContextMode.PerSession> , lub <xref:System.ServiceModel.InstanceContextMode.Single> .  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu ustawia <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> Właściwość <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu na <xref:System.ServiceModel.InstanceContextMode.PerCall> .  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>
- <xref:System.ServiceModel.InstanceContextMode>
- [Usługa: Przykłady zachowań](../samples/behaviors.md)
