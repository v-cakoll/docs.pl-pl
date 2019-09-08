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
ms.openlocfilehash: 29254bd661e72b926b21695ccb646480c53b5475
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797094"
---
# <a name="how-to-compare-claims"></a><span data-ttu-id="86fde-102">Instrukcje: porównywanie oświadczeń</span><span class="sxs-lookup"><span data-stu-id="86fde-102">How to: Compare Claims</span></span>

<span data-ttu-id="86fde-103">Infrastruktura modelu tożsamości w Windows Communication Foundation (WCF) służy do sprawdzania autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="86fde-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) is used to perform authorization checking.</span></span> <span data-ttu-id="86fde-104">W związku z tym typowym zadaniem jest porównanie oświadczeń w kontekście autoryzacji do oświadczeń wymaganych do wykonania żądanej akcji lub uzyskania dostępu do żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="86fde-104">As such, a common task is to compare claims in the authorization context to the claims required to perform the requested action or access the requested resource.</span></span> <span data-ttu-id="86fde-105">W tym temacie opisano sposób porównywania oświadczeń, w tym wbudowanych i niestandardowych typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="86fde-105">This topic describes how to compare claims, including built-in and custom claim types.</span></span> <span data-ttu-id="86fde-106">Aby uzyskać więcej informacji na temat infrastruktury modelu tożsamości, zobacz [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="86fde-106">For more information about the Identity Model infrastructure, see [Managing Claims and Authorization with the Identity Model](../feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>

<span data-ttu-id="86fde-107">Porównanie roszczeń obejmuje porównanie trzech części roszczeń (typu, praw i zasobu) z tymi samymi częściami w innym zasobie, aby sprawdzić, czy są równe.</span><span class="sxs-lookup"><span data-stu-id="86fde-107">Claim comparison involves comparing the three parts of a claim (type, right, and resource) against the same parts in another claim to see if they are equal.</span></span> <span data-ttu-id="86fde-108">Zobacz Poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="86fde-108">See the following example.</span></span>

[!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
[!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]

<span data-ttu-id="86fde-109">Oba oświadczenia mają typ <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>oświadczenia, z <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>prawej strony i zasób ciągu "ktoś".</span><span class="sxs-lookup"><span data-stu-id="86fde-109">Both claims have a claim type of <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource of the string "someone".</span></span> <span data-ttu-id="86fde-110">Ponieważ wszystkie trzy części oświadczenia są równe, same oświadczenia są równe.</span><span class="sxs-lookup"><span data-stu-id="86fde-110">As all three parts of the claim are equal, the claims themselves are equal.</span></span>

<span data-ttu-id="86fde-111">Wbudowane typy zgłoszeń są porównywane przy użyciu <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="86fde-111">The built-in claim types are compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="86fde-112">Kod porównania specyficzny dla roszczeń jest używany w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="86fde-112">Claim-specific comparison code is used where necessary.</span></span> <span data-ttu-id="86fde-113">Na przykład uwzględniając następujące dwie oświadczenia głównej nazwy użytkownika (UPN):</span><span class="sxs-lookup"><span data-stu-id="86fde-113">For example, given the following two user principal name (UPN) claims:</span></span>

[!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
[!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]

<span data-ttu-id="86fde-114">Kod porównania w <xref:System.IdentityModel.Claims.Claim.Equals%2A> metodzie zwraca `true`, przy założeniu, że `example\someone` identyfikuje tego samego użytkownikasomeone@example.comdomeny jako "".</span><span class="sxs-lookup"><span data-stu-id="86fde-114">the comparison code in the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method returns `true`, assuming `example\someone` identifies the same domain user as "someone@example.com".</span></span>

<span data-ttu-id="86fde-115">Niestandardowe typy roszczeń można także porównać przy użyciu <xref:System.IdentityModel.Claims.Claim.Equals%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="86fde-115">Custom claim types can also be compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="86fde-116">Jednakże w przypadkach, gdy <xref:System.IdentityModel.Claims.Claim.Resource%2A> typ zwracany przez właściwość żądania jest coś innego niż typ pierwotny <xref:System.IdentityModel.Claims.Claim.Equals%2A> , zwraca `true` tylko wtedy, gdy wartości zwracane przez `Resource` właściwości są równe w zależnościod<xref:System.IdentityModel.Claims.Claim.Equals%2A> Metoda.</span><span class="sxs-lookup"><span data-stu-id="86fde-116">However, in cases where the type returned by the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property of the claim is something other than a primitive type, the <xref:System.IdentityModel.Claims.Claim.Equals%2A> returns `true` only if the values returned by the `Resource` properties are equal according to the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="86fde-117">W przypadkach, gdy nie jest to odpowiednie, typ niestandardowy zwracany przez `Resource` właściwość powinna <xref:System.IdentityModel.Claims.Claim.Equals%2A> przesłaniać metody i <xref:System.Object.GetHashCode%2A> , aby wykonać dowolne niestandardowe przetwarzanie.</span><span class="sxs-lookup"><span data-stu-id="86fde-117">In cases where this is not appropriate, the custom type returned by the `Resource` property should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods to perform whatever custom processing is necessary.</span></span>

## <a name="comparing-built-in-claims"></a><span data-ttu-id="86fde-118">Porównywanie wbudowanych oświadczeń</span><span class="sxs-lookup"><span data-stu-id="86fde-118">Comparing built-in claims</span></span>

1. <span data-ttu-id="86fde-119">Podano dwa wystąpienia <xref:System.IdentityModel.Claims.Claim> klasy, użyj, <xref:System.IdentityModel.Claims.Claim.Equals%2A> aby dokonać porównania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="86fde-119">Given two instances of the <xref:System.IdentityModel.Claims.Claim> class, use the <xref:System.IdentityModel.Claims.Claim.Equals%2A> to make the comparison, as shown in the following code.</span></span>

     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]

### <a name="comparing-custom-claims-with-primitive-resource-types"></a><span data-ttu-id="86fde-120">Porównywanie oświadczeń niestandardowych z typami zasobów pierwotnych</span><span class="sxs-lookup"><span data-stu-id="86fde-120">Comparing custom claims with primitive resource types</span></span>

1. <span data-ttu-id="86fde-121">W przypadku oświadczeń niestandardowych z typami zasobów pierwotnych można wykonać porównanie jako dla oświadczeń wbudowanych, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="86fde-121">For custom claims with primitive resource types, comparison can be performed as for built-in claims, as shown in the following code.</span></span>

     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]

2. <span data-ttu-id="86fde-122">W przypadku oświadczeń niestandardowych ze strukturą lub typami zasobów opartymi na klasie typ zasobu powinien <xref:System.IdentityModel.Claims.Claim.Equals%2A> zastąpić metodę.</span><span class="sxs-lookup"><span data-stu-id="86fde-122">For custom claims with structure or class based resource types, the resource type should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span>

3. <span data-ttu-id="86fde-123">Najpierw sprawdź, czy `obj` parametr jest `null`, i jeśli tak, Return `false`.</span><span class="sxs-lookup"><span data-stu-id="86fde-123">First check whether the `obj` parameter is `null`, and if so, return `false`.</span></span>

     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]

4. <span data-ttu-id="86fde-124">Następne wywołanie <xref:System.Object.ReferenceEquals%2A> i przekazanie `obj` `this` oraz jako parametry.</span><span class="sxs-lookup"><span data-stu-id="86fde-124">Next call <xref:System.Object.ReferenceEquals%2A> and pass `this` and `obj` as parameters.</span></span> <span data-ttu-id="86fde-125">Jeśli funkcja zwróci `true`wartość, zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="86fde-125">If it returns `true`, then return `true`.</span></span>

     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]

5. <span data-ttu-id="86fde-126">Kolejna próba przypisania `obj` do zmiennej lokalnej typu klasy.</span><span class="sxs-lookup"><span data-stu-id="86fde-126">Next attempt to assign `obj` to a local variable of the class type.</span></span> <span data-ttu-id="86fde-127">Jeśli to się nie powiedzie, `null`odwołanie jest.</span><span class="sxs-lookup"><span data-stu-id="86fde-127">If this fails, the reference is `null`.</span></span> <span data-ttu-id="86fde-128">W takich przypadkach zwracamy `false`.</span><span class="sxs-lookup"><span data-stu-id="86fde-128">In such cases, return `false`.</span></span>

6. <span data-ttu-id="86fde-129">Wykonaj niestandardowe porównanie niezbędne do poprawnego porównania bieżącego żądania z podanym zastrzeżeniem.</span><span class="sxs-lookup"><span data-stu-id="86fde-129">Perform the custom comparison necessary to correctly compare the current claim to the provided claim.</span></span>

## <a name="example"></a><span data-ttu-id="86fde-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="86fde-130">Example</span></span>

<span data-ttu-id="86fde-131">Poniższy przykład przedstawia porównanie niestandardowych oświadczeń, w których zasób oświadczenia jest typem niepierwotnym.</span><span class="sxs-lookup"><span data-stu-id="86fde-131">The following example shows a comparison of custom claims where the claim resource is a non-primitive type.</span></span>

[!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
[!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]

## <a name="see-also"></a><span data-ttu-id="86fde-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86fde-132">See also</span></span>

- [<span data-ttu-id="86fde-133">Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości</span><span class="sxs-lookup"><span data-stu-id="86fde-133">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [<span data-ttu-id="86fde-134">Instrukcje: Tworzenie niestandardowego żądania</span><span class="sxs-lookup"><span data-stu-id="86fde-134">How to: Create a Custom Claim</span></span>](how-to-create-a-custom-claim.md)
