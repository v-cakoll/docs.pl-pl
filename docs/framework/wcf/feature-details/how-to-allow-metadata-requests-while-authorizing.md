---
title: 'Instrukcje: Zezwalanie na żądania metadanych podczas autoryzowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
ms.openlocfilehash: 820725e22c8f07c10212f434e377d5b039cc75e2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591911"
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a>Instrukcje: Zezwalanie na żądania metadanych podczas autoryzowania
Podczas autoryzacji niestandardowej może być konieczne do umożliwienia żądanie metadanych do przetworzenia. Poniższy temat przedstawiono kroki, aby sprawdzić takie żądanie.  
  
 Aby uzyskać więcej informacji na temat autoryzacji Windows Communication Foundation (WCF), zobacz [autoryzacji](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
### <a name="to-allow-metadata-requests-during-authorization"></a>Aby zezwolić na żądania metadanych podczas autoryzacji  
  
1.  Utwórz rozszerzenie <xref:System.ServiceModel.ServiceAuthorizationManager> klasy.  
  
2.  Zastąp <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody. Metoda ta zwraca `true` lub `false` w zależności od tego, czy jest dozwolone autoryzacji. Informacje o bieżącej procedurze, znajduje się w <xref:System.ServiceModel.OperationContext> przekazany jako parametr do metody.  
  
3.  Override Sprawdź nazwę kontraktu, przestrzeń nazw i akcji, jak pokazano w poniższym przykładzie. Jeśli warunki są prawidłowe, a następnie wróć `true.`  
  
4.  Użyj punktu rozszerzalności, mogą wykorzystać klasy. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie Menedżera autoryzacji niestandardowej dla usługi](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano nadpisanie <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody.  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Autoryzacja](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
