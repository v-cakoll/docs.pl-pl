---
title: 'Instrukcje: zezwalanie na żądania metadanych podczas autoryzowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
ms.openlocfilehash: bea4f7e90df29678697fe6708bdc6a73145522db
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59317704"
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a><span data-ttu-id="1c40e-102">Instrukcje: zezwalanie na żądania metadanych podczas autoryzowania</span><span class="sxs-lookup"><span data-stu-id="1c40e-102">How To: Allow Metadata Requests While Authorizing</span></span>
<span data-ttu-id="1c40e-103">Podczas autoryzacji niestandardowej może być konieczne do umożliwienia żądanie metadanych do przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="1c40e-103">During custom authorization, it may be necessary to allow a request for metadata to be processed.</span></span> <span data-ttu-id="1c40e-104">Poniższy temat przedstawiono kroki, aby sprawdzić takie żądanie.</span><span class="sxs-lookup"><span data-stu-id="1c40e-104">The following topic walks through the steps to validate such a request.</span></span>  
  
 <span data-ttu-id="1c40e-105">Aby uzyskać więcej informacji na temat autoryzacji Windows Communication Foundation (WCF), zobacz [autoryzacji](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="1c40e-105">For more information about Windows Communication Foundation (WCF) authorization, see [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
### <a name="to-allow-metadata-requests-during-authorization"></a><span data-ttu-id="1c40e-106">Aby zezwolić na żądania metadanych podczas autoryzacji</span><span class="sxs-lookup"><span data-stu-id="1c40e-106">To allow metadata requests during authorization</span></span>  
  
1. <span data-ttu-id="1c40e-107">Utwórz rozszerzenie <xref:System.ServiceModel.ServiceAuthorizationManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="1c40e-107">Create an extension of the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
2. <span data-ttu-id="1c40e-108">Zastąp <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1c40e-108">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="1c40e-109">Metoda ta zwraca `true` lub `false` w zależności od tego, czy jest dozwolone autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="1c40e-109">The method returns `true` or `false` depending on whether authorization is allowed.</span></span> <span data-ttu-id="1c40e-110">Informacje o bieżącej procedurze, znajduje się w <xref:System.ServiceModel.OperationContext> przekazany jako parametr do metody.</span><span class="sxs-lookup"><span data-stu-id="1c40e-110">Information about the current procedure is found in the <xref:System.ServiceModel.OperationContext> passed as a parameter to the method.</span></span>  
  
3. <span data-ttu-id="1c40e-111">Override Sprawdź nazwę kontraktu, przestrzeń nazw i akcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1c40e-111">In the override, check the contract name, namespace, and the action as shown in the following example.</span></span> <span data-ttu-id="1c40e-112">Jeśli warunki są prawidłowe, a następnie wróć `true.`</span><span class="sxs-lookup"><span data-stu-id="1c40e-112">If the conditions are valid, then return `true.`</span></span>  
  
4. <span data-ttu-id="1c40e-113">Użyj punktu rozszerzalności, mogą wykorzystać klasy.</span><span class="sxs-lookup"><span data-stu-id="1c40e-113">Use the extensibility point to employ the class.</span></span> <span data-ttu-id="1c40e-114">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie Menedżera autoryzacji niestandardowej dla usługi](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="1c40e-114">For more information, see [How to: Create a Custom Authorization Manager for a Service](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c40e-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c40e-115">Example</span></span>  
 <span data-ttu-id="1c40e-116">W poniższym przykładzie pokazano nadpisanie <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1c40e-116">The following example shows an override of the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span>  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1c40e-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c40e-117">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="1c40e-118">Autoryzacja</span><span class="sxs-lookup"><span data-stu-id="1c40e-118">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [<span data-ttu-id="1c40e-119">Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości</span><span class="sxs-lookup"><span data-stu-id="1c40e-119">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
