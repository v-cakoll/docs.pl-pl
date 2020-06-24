---
title: 'Instrukcje: Tworzenie oświadczenia niestandardowego'
description: Dowiedz się, jak utworzyć niestandardową funkcję w programie WCF. Usługa WCF obsługuje różne wbudowane oświadczenia, a niektóre aplikacje mogą wymagać oświadczeń niestandardowych.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: 89f2b1359b48b71720db6ff38f27883745cfe612
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247549"
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="22c83-104">Instrukcje: Tworzenie oświadczenia niestandardowego</span><span class="sxs-lookup"><span data-stu-id="22c83-104">How to: Create a Custom Claim</span></span>
<span data-ttu-id="22c83-105">Infrastruktura modelu tożsamości w programie Windows Communication Foundation (WCF) udostępnia zestaw wbudowanych typów i praw do funkcji pomocnika do tworzenia <xref:System.IdentityModel.Claims.Claim> wystąpień z tymi typami i prawami.</span><span class="sxs-lookup"><span data-stu-id="22c83-105">The Identity Model infrastructure in Windows Communication Foundation (WCF) provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="22c83-106">Te wbudowane oświadczenia są przeznaczone do informacji o modelu znajdujących się w typach poświadczeń klienta obsługiwanych domyślnie przez program WCF.</span><span class="sxs-lookup"><span data-stu-id="22c83-106">These built-in claims are designed to model information found in client credential types that WCF supports by default.</span></span> <span data-ttu-id="22c83-107">W wielu przypadkach wbudowane oświadczenia są wystarczające; Niektóre aplikacje mogą jednak wymagać oświadczeń niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="22c83-107">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="22c83-108">Każde z nich składa się z typu, zasobu, którego dotyczy to i po prawej stronie tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="22c83-108">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="22c83-109">W tym temacie opisano sposób tworzenia niestandardowego żądania.</span><span class="sxs-lookup"><span data-stu-id="22c83-109">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="22c83-110">Aby utworzyć niestandardową wartość, która jest oparta na typie danych pierwotnych</span><span class="sxs-lookup"><span data-stu-id="22c83-110">To create a custom claim that is based on a primitive data type</span></span>  
  
1. <span data-ttu-id="22c83-111">Utwórz niestandardową autoryzację, przekazując typ, wartość zasobu i prawo do <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="22c83-111">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="22c83-112">Wybierz unikatową wartość dla typu zgłoszenia.</span><span class="sxs-lookup"><span data-stu-id="22c83-112">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="22c83-113">Typ zgłoszenia jest unikatowym identyfikatorem ciągu.</span><span class="sxs-lookup"><span data-stu-id="22c83-113">The claim type is a unique string identifier.</span></span> <span data-ttu-id="22c83-114">Jest on odpowiedzialny za niestandardowy Projektant roszczeń, aby upewnić się, że identyfikator ciągu, który jest używany dla typu, jest unikatowy.</span><span class="sxs-lookup"><span data-stu-id="22c83-114">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="22c83-115">Aby uzyskać listę typów, które są zdefiniowane przez funkcję WCF, zobacz <xref:System.IdentityModel.Claims.ClaimTypes> Klasa.</span><span class="sxs-lookup"><span data-stu-id="22c83-115">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="22c83-116">Wybierz typ danych pierwotnych i wartość zasobu.</span><span class="sxs-lookup"><span data-stu-id="22c83-116">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="22c83-117">Zasób jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="22c83-117">A resource is an object.</span></span> <span data-ttu-id="22c83-118">Typ CLR zasobu może być typem pierwotnym, takim jak <xref:System.String> lub <xref:System.Int32> , lub dowolnym typem możliwym do serializacji.</span><span class="sxs-lookup"><span data-stu-id="22c83-118">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="22c83-119">Typ CLR zasobu musi być możliwy do serializacji, ponieważ oświadczenia są serializowane w różnych punktach przez WCF.</span><span class="sxs-lookup"><span data-stu-id="22c83-119">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="22c83-120">Typy pierwotne są możliwe do serializacji.</span><span class="sxs-lookup"><span data-stu-id="22c83-120">Primitive types are serializable.</span></span>  
  
    3. <span data-ttu-id="22c83-121">Wybierz prawo zdefiniowane przez funkcję WCF lub unikatową wartość dla prawa niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="22c83-121">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="22c83-122">Prawo jest unikatowym identyfikatorem ciągu.</span><span class="sxs-lookup"><span data-stu-id="22c83-122">A right is a unique string identifier.</span></span> <span data-ttu-id="22c83-123">Prawa zdefiniowane przez funkcję WCF są zdefiniowane w <xref:System.IdentityModel.Claims.Rights> klasie.</span><span class="sxs-lookup"><span data-stu-id="22c83-123">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="22c83-124">Jest to odpowiedzialność projektanta niestandardowego, aby upewnić się, że identyfikator ciągu, który jest używany przez prawo jest unikatowy.</span><span class="sxs-lookup"><span data-stu-id="22c83-124">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="22c83-125">Poniższy przykład kodu tworzy niestandardowe zgłoszenie z typem zgłoszenia `http://example.org/claims/simplecustomclaim` dla zasobu o nazwie `Driver's License` i z <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> prawej strony.</span><span class="sxs-lookup"><span data-stu-id="22c83-125">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="22c83-126">Aby utworzyć niestandardową wartość, która jest oparta na typie danych niepierwotnym</span><span class="sxs-lookup"><span data-stu-id="22c83-126">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1. <span data-ttu-id="22c83-127">Utwórz niestandardową autoryzację, przekazując typ, wartość zasobu i prawo do <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="22c83-127">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="22c83-128">Wybierz unikatową wartość dla typu zgłoszenia.</span><span class="sxs-lookup"><span data-stu-id="22c83-128">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="22c83-129">Typ zgłoszenia jest unikatowym identyfikatorem ciągu.</span><span class="sxs-lookup"><span data-stu-id="22c83-129">The claim type is a unique string identifier.</span></span> <span data-ttu-id="22c83-130">Jest on odpowiedzialny za niestandardowy Projektant roszczeń, aby upewnić się, że identyfikator ciągu, który jest używany dla typu, jest unikatowy.</span><span class="sxs-lookup"><span data-stu-id="22c83-130">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="22c83-131">Aby uzyskać listę typów, które są zdefiniowane przez funkcję WCF, zobacz <xref:System.IdentityModel.Claims.ClaimTypes> Klasa.</span><span class="sxs-lookup"><span data-stu-id="22c83-131">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="22c83-132">Wybierz lub Zdefiniuj możliwy do serializacji typ inny niż pierwotny dla zasobu.</span><span class="sxs-lookup"><span data-stu-id="22c83-132">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="22c83-133">Zasób jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="22c83-133">A resource is an object.</span></span> <span data-ttu-id="22c83-134">Typ CLR zasobu musi być możliwy do serializacji, ponieważ oświadczenia są serializowane w różnych punktach przez WCF.</span><span class="sxs-lookup"><span data-stu-id="22c83-134">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="22c83-135">Typy pierwotne są już serializowane.</span><span class="sxs-lookup"><span data-stu-id="22c83-135">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="22c83-136">Po zdefiniowaniu nowego typu należy zastosować <xref:System.Runtime.Serialization.DataContractAttribute> do klasy.</span><span class="sxs-lookup"><span data-stu-id="22c83-136">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="22c83-137">Zastosuj również <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut do wszystkich elementów członkowskich nowego typu, które muszą być serializowane w ramach tego żądania.</span><span class="sxs-lookup"><span data-stu-id="22c83-137">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="22c83-138">Poniższy przykład kodu definiuje niestandardowy typ zasobu o nazwie `MyResourceType` .</span><span class="sxs-lookup"><span data-stu-id="22c83-138">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)]
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]
  
    3. <span data-ttu-id="22c83-139">Wybierz prawo zdefiniowane przez funkcję WCF lub unikatową wartość dla prawa niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="22c83-139">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="22c83-140">Prawo jest unikatowym identyfikatorem ciągu.</span><span class="sxs-lookup"><span data-stu-id="22c83-140">A right is a unique string identifier.</span></span> <span data-ttu-id="22c83-141">Prawa zdefiniowane przez funkcję WCF są zdefiniowane w <xref:System.IdentityModel.Claims.Rights> klasie.</span><span class="sxs-lookup"><span data-stu-id="22c83-141">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="22c83-142">Jest to odpowiedzialność projektanta niestandardowego, aby upewnić się, że identyfikator ciągu, który jest używany przez prawo jest unikatowy.</span><span class="sxs-lookup"><span data-stu-id="22c83-142">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="22c83-143">Poniższy przykład kodu tworzy niestandardowe zgłoszenie z typem zgłoszenia `http://example.org/claims/complexcustomclaim` , niestandardowym typem zasobu `MyResourceType` i z <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> prawej strony.</span><span class="sxs-lookup"><span data-stu-id="22c83-143">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)]
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]
  
## <a name="example"></a><span data-ttu-id="22c83-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="22c83-144">Example</span></span>  
 <span data-ttu-id="22c83-145">Poniższy przykład kodu demonstruje sposób tworzenia niestandardowego zgłoszenia z typem zasobu pierwotnego i niestandardowym niepierwotnym typem zasobu.</span><span class="sxs-lookup"><span data-stu-id="22c83-145">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="22c83-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22c83-146">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="22c83-147">Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości</span><span class="sxs-lookup"><span data-stu-id="22c83-147">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
