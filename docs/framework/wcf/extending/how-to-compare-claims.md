---
title: 'Instrukcje: porównywanie oświadczeń'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], comparing
- claims [WCF]
ms.assetid: 0c4ec84d-53df-408f-8953-9bc437f56c28
ms.openlocfilehash: 932ad347730b35a936e040e116e5aa6af36cd3dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343314"
---
# <a name="how-to-compare-claims"></a><span data-ttu-id="0127f-102">Instrukcje: porównywanie oświadczeń</span><span class="sxs-lookup"><span data-stu-id="0127f-102">How to: Compare Claims</span></span>
<span data-ttu-id="0127f-103">Infrastruktura modelu tożsamości w Windows Communication Foundation (WCF) służy do sprawdzania autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="0127f-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) is used to perform authorization checking.</span></span> <span data-ttu-id="0127f-104">W efekcie zadanie często wykonywane jest porównanie oświadczeń w kontekście autoryzacji oświadczeń, wymagane do wykonania żądanej akcji ani uzyskać dostępu do żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="0127f-104">As such, a common task is to compare claims in the authorization context to the claims required to perform the requested action or access the requested resource.</span></span> <span data-ttu-id="0127f-105">W tym temacie opisano sposób porównywania roszczenia, w tym typów wbudowanych i niestandardowych oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="0127f-105">This topic describes how to compare claims, including built-in and custom claim types.</span></span> <span data-ttu-id="0127f-106">Aby uzyskać więcej informacji na temat infrastruktury modelu tożsamości, zobacz [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="0127f-106">For more information about the Identity Model infrastructure, see [Managing Claims and Authorization with the Identity Model](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>  
  
 <span data-ttu-id="0127f-107">Porównywanie oświadczeń obejmuje porównanie trzy części (typ prawa i zasobów) oświadczenia o tej samej części w innym oświadczeń, aby zobaczyć, czy są równe.</span><span class="sxs-lookup"><span data-stu-id="0127f-107">Claim comparison involves comparing the three parts of a claim (type, right, and resource) against the same parts in another claim to see if they are equal.</span></span> <span data-ttu-id="0127f-108">Zobacz poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="0127f-108">See the following example.</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
 [!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]  
  
 <span data-ttu-id="0127f-109">Zarówno oświadczeń ma typ oświadczenia <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, po prawej stronie <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>i zasobu ciągu "ktoś".</span><span class="sxs-lookup"><span data-stu-id="0127f-109">Both claims have a claim type of <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource of the string "someone".</span></span> <span data-ttu-id="0127f-110">Jak trzy części oświadczenia są równe, samodzielnie oświadczenia są równe.</span><span class="sxs-lookup"><span data-stu-id="0127f-110">As all three parts of the claim are equal, the claims themselves are equal.</span></span>  
  
 <span data-ttu-id="0127f-111">Typy wbudowane oświadczeń są porównywane za pomocą <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0127f-111">The built-in claim types are compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="0127f-112">Kod porównania specyficznego dla oświadczeń jest używany, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="0127f-112">Claim-specific comparison code is used where necessary.</span></span> <span data-ttu-id="0127f-113">Na przykład biorąc pod uwagę następujące dwa główne nazwy (UPN) oświadczenia użytkowników:</span><span class="sxs-lookup"><span data-stu-id="0127f-113">For example, given the following two user principal name (UPN) claims:</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
 [!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]  
  
 <span data-ttu-id="0127f-114">Kod porównania w <xref:System.IdentityModel.Claims.Claim.Equals%2A> metoda zwraca `true`, przyjmuje `example\someone` identyfikuje tego samego użytkownika domeny jako "someone@example.com".</span><span class="sxs-lookup"><span data-stu-id="0127f-114">the comparison code in the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method returns `true`, assuming `example\someone` identifies the same domain user as "someone@example.com".</span></span>  
  
 <span data-ttu-id="0127f-115">Niestandardowe typy oświadczeń można również porównać przy użyciu <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0127f-115">Custom claim types can also be compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="0127f-116">Jednak w przypadkach, gdzie typ zwrócony przez <xref:System.IdentityModel.Claims.Claim.Resource%2A> właściwość oświadczenia jest coś innego niż typ pierwotny <xref:System.IdentityModel.Claims.Claim.Equals%2A> zwraca `true` tylko wtedy, gdy wartości zwracane przez `Resource` właściwości są równe zgodnie z <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0127f-116">However, in cases where the type returned by the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property of the claim is something other than a primitive type, the <xref:System.IdentityModel.Claims.Claim.Equals%2A> returns `true` only if the values returned by the `Resource` properties are equal according to the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="0127f-117">W przypadkach, gdy nie jest to odpowiedni typ niestandardowy zwrócony przez `Resource` należy zastąpić właściwość <xref:System.IdentityModel.Claims.Claim.Equals%2A> i <xref:System.Object.GetHashCode%2A> metody, aby wykonać dowolne niestandardowe przetwarzanie danych jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="0127f-117">In cases where this is not appropriate, the custom type returned by the `Resource` property should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods to perform whatever custom processing is necessary.</span></span>  
  
### <a name="comparing-built-in-claims"></a><span data-ttu-id="0127f-118">Porównywanie oświadczeń wbudowane</span><span class="sxs-lookup"><span data-stu-id="0127f-118">Comparing built-in claims</span></span>  
  
1. <span data-ttu-id="0127f-119">Biorąc pod uwagę dwa wystąpienia <xref:System.IdentityModel.Claims.Claim> klasy, należy użyć <xref:System.IdentityModel.Claims.Claim.Equals%2A> się porównania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="0127f-119">Given two instances of the <xref:System.IdentityModel.Claims.Claim> class, use the <xref:System.IdentityModel.Claims.Claim.Equals%2A> to make the comparison, as shown in the following code.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]  
  
### <a name="comparing-custom-claims-with-primitive-resource-types"></a><span data-ttu-id="0127f-120">Porównywanie oświadczeń niestandardowych typów pierwotnych zasobów</span><span class="sxs-lookup"><span data-stu-id="0127f-120">Comparing custom claims with primitive resource types</span></span>  
  
1. <span data-ttu-id="0127f-121">Niestandardowe oświadczenia przy użyciu typów pierwotnych zasobów można wykonać porównania jak w przypadku wbudowanych oświadczenia, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="0127f-121">For custom claims with primitive resource types, comparison can be performed as for built-in claims, as shown in the following code.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]  
  
2. <span data-ttu-id="0127f-122">Aby zastąpić powinny oświadczenia niestandardowe, struktury lub klasy na podstawie typów zasobów, typ zasobu <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0127f-122">For custom claims with structure or class based resource types, the resource type should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span>  
  
3. <span data-ttu-id="0127f-123">Najpierw należy sprawdzić, czy `obj` parametr jest `null`i jeśli tak, zwracają `false`.</span><span class="sxs-lookup"><span data-stu-id="0127f-123">First check whether the `obj` parameter is `null`, and if so, return `false`.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]  
  
4. <span data-ttu-id="0127f-124">Następnie wywołaj <xref:System.Object.ReferenceEquals%2A> i przekazać `this` i `obj` jako parametry.</span><span class="sxs-lookup"><span data-stu-id="0127f-124">Next call <xref:System.Object.ReferenceEquals%2A> and pass `this` and `obj` as parameters.</span></span> <span data-ttu-id="0127f-125">Jeśli zostanie zwrócona `true`, a następnie wróć `true`.</span><span class="sxs-lookup"><span data-stu-id="0127f-125">If it returns `true`, then return `true`.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]  
  
5. <span data-ttu-id="0127f-126">Następnie Przystąp do przypisania `obj` do zmiennej lokalnej o typie danej klasy.</span><span class="sxs-lookup"><span data-stu-id="0127f-126">Next attempt to assign `obj` to a local variable of the class type.</span></span> <span data-ttu-id="0127f-127">W przypadku niepowodzenia odwołanie jest `null`.</span><span class="sxs-lookup"><span data-stu-id="0127f-127">If this fails, the reference is `null`.</span></span> <span data-ttu-id="0127f-128">W takiej sytuacji należy zwracać `false`.</span><span class="sxs-lookup"><span data-stu-id="0127f-128">In such cases, return `false`.</span></span>  
  
6. <span data-ttu-id="0127f-129">Wykonać porównanie niestandardowe poprawnie porównanie bieżącej oświadczenia do podanego oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="0127f-129">Perform the custom comparison necessary to correctly compare the current claim to the provided claim.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0127f-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="0127f-130">Example</span></span>  
 <span data-ttu-id="0127f-131">Poniższy przykład przedstawiono porównanie oświadczenia niestandardowe, gdzie zasobów oświadczeń jest typem niepodstawowe.</span><span class="sxs-lookup"><span data-stu-id="0127f-131">The following example shows a comparison of custom claims where the claim resource is a non-primitive type.</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
 [!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="0127f-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0127f-132">See also</span></span>

- [<span data-ttu-id="0127f-133">Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości</span><span class="sxs-lookup"><span data-stu-id="0127f-133">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [<span data-ttu-id="0127f-134">Instrukcje: Tworzenie oświadczenia niestandardowego</span><span class="sxs-lookup"><span data-stu-id="0127f-134">How to: Create a Custom Claim</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
