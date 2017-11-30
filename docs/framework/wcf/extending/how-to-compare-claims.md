---
title: "Porady: Porównywanie oświadczeń"
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
helpviewer_keywords:
- claims [WCF], comparing
- claims [WCF]
ms.assetid: 0c4ec84d-53df-408f-8953-9bc437f56c28
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fd23edd9e390b1f2018419c3c43be8091500c929
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compare-claims"></a><span data-ttu-id="ff8f1-102">Porady: Porównywanie oświadczeń</span><span class="sxs-lookup"><span data-stu-id="ff8f1-102">How to: Compare Claims</span></span>
<span data-ttu-id="ff8f1-103">Infrastruktura modelu tożsamości w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] służy do sprawdzania autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-103">The Identity Model infrastructure in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is used to perform authorization checking.</span></span> <span data-ttu-id="ff8f1-104">W efekcie typowych zadań jest porównywanie oświadczeń w kontekście autoryzacji oświadczeń wymagane do wykonania żądanej akcji lub dostęp do żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-104">As such, a common task is to compare claims in the authorization context to the claims required to perform the requested action or access the requested resource.</span></span> <span data-ttu-id="ff8f1-105">W tym temacie opisano sposób porównywania roszczenia, w tym typy oświadczeń wbudowanych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-105">This topic describes how to compare claims, including built-in and custom claim types.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ff8f1-106">Infrastruktura modelu tożsamości, zobacz [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="ff8f1-106"> the Identity Model infrastructure, see [Managing Claims and Authorization with the Identity Model](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>  
  
 <span data-ttu-id="ff8f1-107">Porównanie oświadczeń obejmuje porównanie trzech części oświadczenia (typ uprawnienia i zasobów) o tej samej części w innym oświadczeń, aby zobaczyć, czy są równe.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-107">Claim comparison involves comparing the three parts of a claim (type, right, and resource) against the same parts in another claim to see if they are equal.</span></span> <span data-ttu-id="ff8f1-108">Zobacz poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-108">See the following example.</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
 [!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]  
  
 <span data-ttu-id="ff8f1-109">Zarówno oświadczenia mają typ oświadczenia <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, prawej strony <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>i zasobów ciągu "ktoś".</span><span class="sxs-lookup"><span data-stu-id="ff8f1-109">Both claims have a claim type of <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource of the string "someone".</span></span> <span data-ttu-id="ff8f1-110">Wszystkie trzy elementy oświadczenia są takie same, same oświadczenia są takie same.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-110">As all three parts of the claim are equal, the claims themselves are equal.</span></span>  
  
 <span data-ttu-id="ff8f1-111">Typy wbudowane oświadczeń są porównywane przy użyciu <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-111">The built-in claim types are compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="ff8f1-112">Kod oświadczenia dotyczące porównania jest używany w przypadku, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-112">Claim-specific comparison code is used where necessary.</span></span> <span data-ttu-id="ff8f1-113">Przykładowo podana następujące dwa główne oświadczeniach nazwy użytkownika (UPN):</span><span class="sxs-lookup"><span data-stu-id="ff8f1-113">For example, given the following two user principal name (UPN) claims:</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
 [!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]  
  
 <span data-ttu-id="ff8f1-114">Kod porównania w <xref:System.IdentityModel.Claims.Claim.Equals%2A> metoda zwraca `true`, przyjmuje `example\someone` tego samego użytkownika domeny identyfikuje "someone@example.com".</span><span class="sxs-lookup"><span data-stu-id="ff8f1-114">the comparison code in the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method returns `true`, assuming `example\someone` identifies the same domain user as "someone@example.com".</span></span>  
  
 <span data-ttu-id="ff8f1-115">Niestandardowe typy oświadczeń można również porównać przy użyciu <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-115">Custom claim types can also be compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="ff8f1-116">Jednak w przypadku, gdy typ zwracany przez <xref:System.IdentityModel.Claims.Claim.Resource%2A> właściwość oświadczenia jest typem pierwotnym <xref:System.IdentityModel.Claims.Claim.Equals%2A> zwraca `true` tylko wtedy, gdy wartości zwracane przez `Resource` właściwości są takie same, zgodnie z <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-116">However, in cases where the type returned by the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property of the claim is something other than a primitive type, the <xref:System.IdentityModel.Claims.Claim.Equals%2A> returns `true` only if the values returned by the `Resource` properties are equal according to the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="ff8f1-117">W przypadkach, gdy nie jest to odpowiedni niestandardowy typ zwrócony przez `Resource` powinny zastępować właściwość <xref:System.IdentityModel.Claims.Claim.Equals%2A> i <xref:System.Object.GetHashCode%2A> metody służące do wykonania niestandardowej przetwarzania jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-117">In cases where this is not appropriate, the custom type returned by the `Resource` property should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods to perform whatever custom processing is necessary.</span></span>  
  
### <a name="comparing-built-in-claims"></a><span data-ttu-id="ff8f1-118">Porównywanie oświadczeń wbudowane</span><span class="sxs-lookup"><span data-stu-id="ff8f1-118">Comparing built-in claims</span></span>  
  
1.  <span data-ttu-id="ff8f1-119">Podane dwa wystąpienia <xref:System.IdentityModel.Claims.Claim> klasy, należy użyć <xref:System.IdentityModel.Claims.Claim.Equals%2A> do wykonania porównania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-119">Given two instances of the <xref:System.IdentityModel.Claims.Claim> class, use the <xref:System.IdentityModel.Claims.Claim.Equals%2A> to make the comparison, as shown in the following code.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]  
  
### <a name="comparing-custom-claims-with-primitive-resource-types"></a><span data-ttu-id="ff8f1-120">Porównywanie oświadczeń niestandardowych typów pierwotnych zasobów</span><span class="sxs-lookup"><span data-stu-id="ff8f1-120">Comparing custom claims with primitive resource types</span></span>  
  
1.  <span data-ttu-id="ff8f1-121">Niestandardowe oświadczeń z typów pierwotnych zasobów można wykonać porównania podobnie jak w przypadku oświadczeń wbudowane, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-121">For custom claims with primitive resource types, comparison can be performed as for built-in claims, as shown in the following code.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]  
  
2.  <span data-ttu-id="ff8f1-122">Dla oświadczenia niestandardowe struktury lub klasy na podstawie typów zasobów, typ zasobu powinny zastępować <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-122">For custom claims with structure or class based resource types, the resource type should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span>  
  
3.  <span data-ttu-id="ff8f1-123">Najpierw sprawdź, czy `obj` parametr jest `null`, a jeśli tak, wróć `false`.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-123">First check whether the `obj` parameter is `null`, and if so, return `false`.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]  
  
4.  <span data-ttu-id="ff8f1-124">Następnie wywołaj <xref:System.Object.ReferenceEquals%2A> i przekaż `this` i `obj` jako parametry.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-124">Next call <xref:System.Object.ReferenceEquals%2A> and pass `this` and `obj` as parameters.</span></span> <span data-ttu-id="ff8f1-125">Jeśli zmienna zwraca `true`, następnie zwracany `true`.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-125">If it returns `true`, then return `true`.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]  
  
5.  <span data-ttu-id="ff8f1-126">Następnie Przystąp do przypisania `obj` do zmiennej lokalnej typu klasy.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-126">Next attempt to assign `obj` to a local variable of the class type.</span></span> <span data-ttu-id="ff8f1-127">Jeśli to się nie powiedzie, odwołanie jest `null`.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-127">If this fails, the reference is `null`.</span></span> <span data-ttu-id="ff8f1-128">W takiej sytuacji należy zwracać `false`.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-128">In such cases, return `false`.</span></span>  
  
6.  <span data-ttu-id="ff8f1-129">Porównania niestandardowych poprawnie porównanie bieżącego oświadczenia do podanego oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-129">Perform the custom comparison necessary to correctly compare the current claim to the provided claim.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff8f1-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff8f1-130">Example</span></span>  
 <span data-ttu-id="ff8f1-131">W poniższym przykładzie przedstawiono porównanie oświadczenia niestandardowe, gdy zasób oświadczenia jest typu innego niż pierwotny.</span><span class="sxs-lookup"><span data-stu-id="ff8f1-131">The following example shows a comparison of custom claims where the claim resource is a non-primitive type.</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
 [!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="ff8f1-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff8f1-132">See Also</span></span>  
 [<span data-ttu-id="ff8f1-133">Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości</span><span class="sxs-lookup"><span data-stu-id="ff8f1-133">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="ff8f1-134">Porady: tworzenie oświadczenia niestandardowego</span><span class="sxs-lookup"><span data-stu-id="ff8f1-134">How to: Create a Custom Claim</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
