---
title: 'Instrukcje: Tworzenie kontraktu jednokierunkowego'
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
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f93247a96501359bcda8d2956308e6570c597f93
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-one-way-contract"></a><span data-ttu-id="bb641-102">Instrukcje: Tworzenie kontraktu jednokierunkowego</span><span class="sxs-lookup"><span data-stu-id="bb641-102">How to: Create a One-Way Contract</span></span>
<span data-ttu-id="bb641-103">W tym temacie przedstawiono podstawowe kroki, aby utworzyć metody, które używają kontraktu jednokierunkowego.</span><span class="sxs-lookup"><span data-stu-id="bb641-103">This topic shows the basic steps to create methods that use a one-way contract.</span></span> <span data-ttu-id="bb641-104">Takie metody wywoływać operacje na [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi od klienta, ale oczekiwano odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="bb641-104">Such methods invoke operations on a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service from a client but do not expect a reply.</span></span> <span data-ttu-id="bb641-105">Ten typ umowy można na przykład do publikowania powiadomienia dla wielu subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="bb641-105">This type of contract can be used, for example, to publish notifications to many subscribers.</span></span> <span data-ttu-id="bb641-106">Umożliwia także kontraktów jednokierunkowych podczas tworzenia kontraktu dwukierunkowego (dwukierunkowej), dzięki czemu klienci i serwery komunikować się ze sobą niezależnie, aby albo mogą inicjować połączenia do drugiego.</span><span class="sxs-lookup"><span data-stu-id="bb641-106">You can also use one-way contracts when creating a duplex (two-way) contract, which allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="bb641-107">Może to umożliwić w szczególności serwera w celu wykonywania wywołań jednokierunkowe klientowi, który klient można traktować jako zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="bb641-107">This can allow, in particular, the server to make one-way calls to the client that the client can treat as events.</span></span> <span data-ttu-id="bb641-108">Aby uzyskać szczegółowe informacje na temat określania metody jednokierunkowe, zobacz <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości i <xref:System.ServiceModel.OperationContractAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="bb641-108">For detailed information about specifying one-way methods, see the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property and the <xref:System.ServiceModel.OperationContractAttribute> class.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="bb641-109">Tworzenie aplikacji klienckich dla kontraktu dwukierunkowego, zobacz [jak: dostęp do usług pomocą kontraktów jednokierunkowych i kontraktów "żądanie-odpowiedź"](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="bb641-109"> creating a client application for a duplex contract, see [How to: Access Services with One-Way and Request-Reply Contracts](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md).</span></span> <span data-ttu-id="bb641-110">Dla przykładu pracy, zobacz [jednokierunkowe](../../../../docs/framework/wcf/samples/one-way.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="bb641-110">For a working sample, see the [One-Way](../../../../docs/framework/wcf/samples/one-way.md) sample.</span></span>  
  
### <a name="to-create-a-one-way-contract"></a><span data-ttu-id="bb641-111">Aby utworzyć kontraktu jednokierunkowego</span><span class="sxs-lookup"><span data-stu-id="bb641-111">To create a one-way contract</span></span>  
  
1.  <span data-ttu-id="bb641-112">Tworzenie kontraktu usługi, stosując <xref:System.ServiceModel.ServiceContractAttribute> interfejs, który definiuje metody usługi jest implementacja klasy.</span><span class="sxs-lookup"><span data-stu-id="bb641-112">Create the service contract by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface that defines the methods the service is to implement.</span></span>  
  
2.  <span data-ttu-id="bb641-113">Wskazuje, które metody w interfejsie klienta można wywoływane przez zastosowanie <xref:System.ServiceModel.OperationContractAttribute> klasy do nich.</span><span class="sxs-lookup"><span data-stu-id="bb641-113">Indicate which methods in the interface a client can invoked by applying the <xref:System.ServiceModel.OperationContractAttribute> class to them.</span></span>  
  
3.  <span data-ttu-id="bb641-114">Wyznaczyć operacje, które muszą mieć żadnych danych wyjściowych (Brak wartości zwracanej i poza nie lub parametrów ref) jako jednokierunkowe przez ustawienie <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="bb641-114">Designate operations that must have no output (no return value and no out or ref parameters) as one-way by setting the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true`.</span></span> <span data-ttu-id="bb641-115">Należy pamiętać, że operacje który przenoszenia <xref:System.ServiceModel.OperationContractAttribute> klasy spełnić kontraktu "żądanie-odpowiedź" Domyślnie, ponieważ <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> jest właściwość `false` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="bb641-115">Note that the operations that carry the <xref:System.ServiceModel.OperationContractAttribute> class satisfy a request-reply contract by default because the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property is `false` by default.</span></span> <span data-ttu-id="bb641-116">Dlatego należy jawnie określić wartości właściwości atrybutów można `true` Jeśli chcesz kontraktu jednokierunkowego dla metody.</span><span class="sxs-lookup"><span data-stu-id="bb641-116">So you must explicitly specify the value of the attribute property to be `true` if you want a one-way contract for the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb641-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb641-117">Example</span></span>  
 <span data-ttu-id="bb641-118">Poniższy przykładowy kod definiuje kontrakt dla usługi, które są dostępne różne metody jednokierunkowe.</span><span class="sxs-lookup"><span data-stu-id="bb641-118">The following code example defines a contract for a service that includes several one-way methods.</span></span> <span data-ttu-id="bb641-119">Wszystkie metody mają jednokierunkowe umowy z wyjątkiem `Equals`, która domyślnie żądanie odpowiedź i zwraca wynik.</span><span class="sxs-lookup"><span data-stu-id="bb641-119">All of the methods have one-way contracts except `Equals`, which defaults to request-reply and returns a result.</span></span>  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bb641-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb641-120">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [<span data-ttu-id="bb641-121">Projektowanie i Implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="bb641-121">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [<span data-ttu-id="bb641-122">Porady: definiowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="bb641-122">How to: Define a Service Contract</span></span>](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [<span data-ttu-id="bb641-123">Sesji</span><span class="sxs-lookup"><span data-stu-id="bb641-123">Session</span></span>](../../../../docs/framework/wcf/samples/session.md)  
 [<span data-ttu-id="bb641-124">Porady: tworzenie kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="bb641-124">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
