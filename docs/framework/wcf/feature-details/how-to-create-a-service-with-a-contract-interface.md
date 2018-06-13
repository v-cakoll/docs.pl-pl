---
title: 'Instrukcje: Tworzenie usługi przy użyciu interfejsu kontraktu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: 796870b80ed72db2353e79db3e4e3fc164c22875
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489797"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a><span data-ttu-id="7c694-102">Instrukcje: Tworzenie usługi przy użyciu interfejsu kontraktu</span><span class="sxs-lookup"><span data-stu-id="7c694-102">How to: Create a Service with a Contract Interface</span></span>
<span data-ttu-id="7c694-103">Jest to preferowany sposób tworzenia kontraktu usługi Windows Communication Foundation (WCF) przy użyciu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7c694-103">The preferred way to create a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="7c694-104">Tego kontraktu określono, kolekcji i struktura wiadomości wymagany dostęp do oferty usługi.</span><span class="sxs-lookup"><span data-stu-id="7c694-104">This contract specifies the collection and structure of messages required to access the operations the service offers.</span></span> <span data-ttu-id="7c694-105">Ten interfejs definiuje typów wejściowych i wyjściowych przez zastosowanie <xref:System.ServiceModel.ServiceContractAttribute> klasy interfejsu i <xref:System.ServiceModel.OperationContractAttribute> klas do metody, które chcesz udostępnić.</span><span class="sxs-lookup"><span data-stu-id="7c694-105">This interface defines the input and output types by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface and the <xref:System.ServiceModel.OperationContractAttribute> class to the methods that you want to expose.</span></span>  
  
 <span data-ttu-id="7c694-106">Aby uzyskać więcej informacji na temat kontraktów usług, zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="7c694-106">For more information about service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a><span data-ttu-id="7c694-107">Tworzenie przy użyciu interfejsu kontraktu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="7c694-107">Creating a WCF contract with an interface</span></span>  
  
1.  <span data-ttu-id="7c694-108">Utwórz nowy interfejs, za pomocą Visual Basic, C# lub dowolnego innego wspólnego języka środowiska uruchomieniowego języka.</span><span class="sxs-lookup"><span data-stu-id="7c694-108">Create a new interface using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2.  <span data-ttu-id="7c694-109">Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> klasy interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7c694-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
3.  <span data-ttu-id="7c694-110">Zdefiniuj metody w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="7c694-110">Define the methods in the interface.</span></span>  
  
4.  <span data-ttu-id="7c694-111">Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej metody, która musi być udostępniany jako część publicznego kontraktu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="7c694-111">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c694-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c694-112">Example</span></span>  
 <span data-ttu-id="7c694-113">Poniższy przykład kodu pokazuje interfejs, który definiuje kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="7c694-113">The following code example shows an interface that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <span data-ttu-id="7c694-114">Metody, które mają <xref:System.ServiceModel.OperationContractAttribute> klasa stosowana domyślnie używają komunikatów żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="7c694-114">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="7c694-115">Aby uzyskać więcej informacji o tym wzorcu komunikatów, zobacz [porady: tworzenie kontraktu "żądanie-odpowiedź"](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="7c694-115">For more information about this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="7c694-116">Można również utworzyć i używać innych wzorcach wiadomości przez ustawienie właściwości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="7c694-116">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="7c694-117">Więcej przykładów można znaleźć [porady: tworzenie kontraktu One-Way](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) i [porady: tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="7c694-117">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c694-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c694-118">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
