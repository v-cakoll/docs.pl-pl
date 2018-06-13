---
title: 'Porady: Tworzenie wystąpienia usługi sterowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
ms.openlocfilehash: 2f9e4f298eb95498ec8d3603624763bfd95bfda1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489147"
---
# <a name="how-to-control-service-instancing"></a>Porady: Tworzenie wystąpienia usługi sterowania
Ustawianie trybu wystąpienia usługi umożliwia określenie, kiedy <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (i jego obiekt skojarzona usługa zdefiniowane przez użytkownika) jest tworzony. Zobacz <xref:System.ServiceModel.InstanceContextMode> wyliczenie dla trybów. Aby uzyskać więcej informacji dotyczących zachowania, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md). Przykłady pracy można znaleźć [zachowania](../../../../docs/framework/wcf/samples/behaviors.md).  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a>Aby kontrolować okres istnienia wystąpienia usługi przy użyciu kodu  
  
1.  Zastosuj <xref:System.ServiceModel.ServiceBehaviorAttribute> klasą usług.  
  
2.  Ustaw <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość na jedną z następujących wartości: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, lub <xref:System.ServiceModel.InstanceContextMode.Single>.  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przykładzie <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu <xref:System.ServiceModel.InstanceContextMode.PerCall>.  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>  
 <xref:System.ServiceModel.InstanceContextMode>  
 [Usługi: Przykłady zachowania](http://msdn.microsoft.com/library/4e3c6513-a7ff-4b35-8dcf-b5506c6f39a7)
