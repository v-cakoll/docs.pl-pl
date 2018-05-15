---
title: 'Instrukcje: Zezwalanie na żądania metadanych podczas autoryzowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
ms.openlocfilehash: 2f855080cf3ba4cee08470af77c52945e47a2ec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a><span data-ttu-id="b7728-102">Instrukcje: Zezwalanie na żądania metadanych podczas autoryzowania</span><span class="sxs-lookup"><span data-stu-id="b7728-102">How To: Allow Metadata Requests While Authorizing</span></span>
<span data-ttu-id="b7728-103">Podczas przeprowadzania niestandardowej autoryzacji może być konieczne Zezwalaj na żądania metadanych do przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="b7728-103">During custom authorization, it may be necessary to allow a request for metadata to be processed.</span></span> <span data-ttu-id="b7728-104">Poniższy temat przeprowadzi Cię przez kroki, aby zweryfikować takie żądanie.</span><span class="sxs-lookup"><span data-stu-id="b7728-104">The following topic walks through the steps to validate such a request.</span></span>  
  
 <span data-ttu-id="b7728-105">Aby uzyskać więcej informacji na temat autoryzacji systemu Windows Communication Foundation (WCF), zobacz [autoryzacji](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="b7728-105">For more information about Windows Communication Foundation (WCF) authorization, see [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
### <a name="to-allow-metadata-requests-during-authorization"></a><span data-ttu-id="b7728-106">Aby zezwolić na żądania metadanych podczas autoryzowania</span><span class="sxs-lookup"><span data-stu-id="b7728-106">To allow metadata requests during authorization</span></span>  
  
1.  <span data-ttu-id="b7728-107">Tworzenie rozszerzenia <xref:System.ServiceModel.ServiceAuthorizationManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="b7728-107">Create an extension of the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
2.  <span data-ttu-id="b7728-108">Zastąpienie <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b7728-108">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="b7728-109">Metoda zwraca `true` lub `false` w zależności od tego, czy jest dozwolone autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="b7728-109">The method returns `true` or `false` depending on whether authorization is allowed.</span></span> <span data-ttu-id="b7728-110">Informacje o bieżącej procedury znajduje się w <xref:System.ServiceModel.OperationContext> przekazany jako parametr do metody.</span><span class="sxs-lookup"><span data-stu-id="b7728-110">Information about the current procedure is found in the <xref:System.ServiceModel.OperationContext> passed as a parameter to the method.</span></span>  
  
3.  <span data-ttu-id="b7728-111">Na zastąpienie zaznacz Nazwa kontraktu, przestrzeń nazw i akcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b7728-111">In the override, check the contract name, namespace, and the action as shown in the following example.</span></span> <span data-ttu-id="b7728-112">Jeśli warunki są prawidłowe, zwracany jest `true.`</span><span class="sxs-lookup"><span data-stu-id="b7728-112">If the conditions are valid, then return `true.`</span></span>  
  
4.  <span data-ttu-id="b7728-113">Użyj punktów rozszerzalności fragmentów klasy.</span><span class="sxs-lookup"><span data-stu-id="b7728-113">Use the extensibility point to employ the class.</span></span> <span data-ttu-id="b7728-114">Aby uzyskać więcej informacji, zobacz [porady: tworzenie Menedżera autoryzacji niestandardowej dla usługi](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="b7728-114">For more information, see [How to: Create a Custom Authorization Manager for a Service](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7728-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="b7728-115">Example</span></span>  
 <span data-ttu-id="b7728-116">Poniższy przykład przedstawia Przesłonięcie elementu <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b7728-116">The following example shows an override of the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span>  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b7728-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7728-117">See Also</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [<span data-ttu-id="b7728-118">Autoryzacja</span><span class="sxs-lookup"><span data-stu-id="b7728-118">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [<span data-ttu-id="b7728-119">Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości</span><span class="sxs-lookup"><span data-stu-id="b7728-119">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
