---
title: "Instrukcje: Zezwalanie na żądania metadanych podczas autoryzowania"
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
helpviewer_keywords: allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 103aba5118810064c1cafb7c82634ef000ced667
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a>Instrukcje: Zezwalanie na żądania metadanych podczas autoryzowania
Podczas przeprowadzania niestandardowej autoryzacji może być konieczne Zezwalaj na żądania metadanych do przetworzenia. Poniższy temat przeprowadzi Cię przez kroki, aby zweryfikować takie żądanie.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] autoryzacji, zobacz [autoryzacji](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
### <a name="to-allow-metadata-requests-during-authorization"></a>Aby zezwolić na żądania metadanych podczas autoryzowania  
  
1.  Tworzenie rozszerzenia <xref:System.ServiceModel.ServiceAuthorizationManager> klasy.  
  
2.  Zastąpienie <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody. Metoda zwraca `true` lub `false` w zależności od tego, czy jest dozwolone autoryzacji. Informacje o bieżącej procedury znajduje się w <xref:System.ServiceModel.OperationContext> przekazany jako parametr do metody.  
  
3.  Na zastąpienie zaznacz Nazwa kontraktu, przestrzeń nazw i akcji, jak pokazano w poniższym przykładzie. Jeśli warunki są prawidłowe, zwracany jest`true.`  
  
4.  Użyj punktów rozszerzalności fragmentów klasy. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Porady: tworzenie Menedżera autoryzacji niestandardowej dla usługi](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia Przesłonięcie elementu <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody.  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [Autoryzacji](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
