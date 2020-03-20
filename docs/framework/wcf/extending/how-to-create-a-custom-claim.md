---
title: 'Instrukcje: Tworzenie oświadczenia niestandardowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: e78f577e0fd3473575fab998e55616936212ebb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185619"
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="48edc-102">Instrukcje: Tworzenie oświadczenia niestandardowego</span><span class="sxs-lookup"><span data-stu-id="48edc-102">How to: Create a Custom Claim</span></span>
<span data-ttu-id="48edc-103">Infrastruktura modelu tożsamości w programie Windows Communication Foundation (WCF) udostępnia zestaw wbudowanych typów <xref:System.IdentityModel.Claims.Claim> oświadczeń i praw z funkcjami pomocnika do tworzenia wystąpień z tymi typami i prawami.</span><span class="sxs-lookup"><span data-stu-id="48edc-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="48edc-104">Te wbudowane oświadczenia są przeznaczone do modelowania informacji znalezionych w typach poświadczeń klienta, które WCF obsługuje domyślnie.</span><span class="sxs-lookup"><span data-stu-id="48edc-104">These built-in claims are designed to model information found in client credential types that WCF supports by default.</span></span> <span data-ttu-id="48edc-105">W wielu przypadkach wbudowane oświadczenia są wystarczające; jednak niektóre aplikacje mogą wymagać oświadczeń niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="48edc-105">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="48edc-106">Oświadczenie składa się z typu oświadczenia, zasobu, którego dotyczy oświadczenie i prawa, które jest dochodzony przez ten zasób.</span><span class="sxs-lookup"><span data-stu-id="48edc-106">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="48edc-107">W tym temacie opisano sposób tworzenia oświadczenia niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="48edc-107">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="48edc-108">Aby utworzyć oświadczenie niestandardowe oparte na pierwotnym typie danych</span><span class="sxs-lookup"><span data-stu-id="48edc-108">To create a custom claim that is based on a primitive data type</span></span>  
  
1. <span data-ttu-id="48edc-109">Utwórz oświadczenie niestandardowe, przekazując typ oświadczenia, <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> wartość zasobu i prawo do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="48edc-109">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="48edc-110">Zdecyduj o unikatowej wartości dla typu oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="48edc-110">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="48edc-111">Typ oświadczenia jest unikatowym identyfikatorem ciągu.</span><span class="sxs-lookup"><span data-stu-id="48edc-111">The claim type is a unique string identifier.</span></span> <span data-ttu-id="48edc-112">Jest to niestandardowy projektant oświadczeń jest odpowiedzialny, aby upewnić się, że identyfikator ciągu, który jest używany dla typu oświadczenia jest unikatowy.</span><span class="sxs-lookup"><span data-stu-id="48edc-112">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="48edc-113">Aby uzyskać listę typów oświadczeń, które są zdefiniowane przez WCF, zobacz <xref:System.IdentityModel.Claims.ClaimTypes> klasy.</span><span class="sxs-lookup"><span data-stu-id="48edc-113">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="48edc-114">Wybierz pierwotny typ i wartość danych dla zasobu.</span><span class="sxs-lookup"><span data-stu-id="48edc-114">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="48edc-115">Zasób jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="48edc-115">A resource is an object.</span></span> <span data-ttu-id="48edc-116">Typ CLR zasobu może być pierwotny, <xref:System.String> taki <xref:System.Int32>jak lub , lub dowolny typ serializowalny.</span><span class="sxs-lookup"><span data-stu-id="48edc-116">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="48edc-117">Typ CLR zasobu musi być serializowalny, ponieważ oświadczenia są serializowane w różnych punktach przez WCF.</span><span class="sxs-lookup"><span data-stu-id="48edc-117">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="48edc-118">Typy pierwotne są serializable.</span><span class="sxs-lookup"><span data-stu-id="48edc-118">Primitive types are serializable.</span></span>  
  
    3. <span data-ttu-id="48edc-119">Wybierz prawo, które jest zdefiniowane przez WCF lub unikatową wartość dla prawa niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="48edc-119">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="48edc-120">Prawo jest unikatowy identyfikator ciągu.</span><span class="sxs-lookup"><span data-stu-id="48edc-120">A right is a unique string identifier.</span></span> <span data-ttu-id="48edc-121">Prawa, które są zdefiniowane przez WCF są zdefiniowane w <xref:System.IdentityModel.Claims.Rights> klasie.</span><span class="sxs-lookup"><span data-stu-id="48edc-121">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="48edc-122">Jest to niestandardowy projektant oświadczeń jest odpowiedzialny, aby upewnić się, że identyfikator ciągu, który jest używany dla prawej jest unikatowa.</span><span class="sxs-lookup"><span data-stu-id="48edc-122">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="48edc-123">Poniższy przykład kodu tworzy oświadczenie niestandardowe `http://example.org/claims/simplecustomclaim`z typem `Driver's License`oświadczenia , <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> dla zasobu o nazwie i z prawej strony.</span><span class="sxs-lookup"><span data-stu-id="48edc-123">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="48edc-124">Aby utworzyć oświadczenie niestandardowe oparte na nieizbowym typie danych</span><span class="sxs-lookup"><span data-stu-id="48edc-124">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1. <span data-ttu-id="48edc-125">Utwórz oświadczenie niestandardowe, przekazując typ oświadczenia, <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> wartość zasobu i prawo do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="48edc-125">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="48edc-126">Zdecyduj o unikatowej wartości dla typu oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="48edc-126">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="48edc-127">Typ oświadczenia jest unikatowym identyfikatorem ciągu.</span><span class="sxs-lookup"><span data-stu-id="48edc-127">The claim type is a unique string identifier.</span></span> <span data-ttu-id="48edc-128">Jest to niestandardowy projektant oświadczeń jest odpowiedzialny, aby upewnić się, że identyfikator ciągu, który jest używany dla typu oświadczenia jest unikatowy.</span><span class="sxs-lookup"><span data-stu-id="48edc-128">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="48edc-129">Aby uzyskać listę typów oświadczeń, które są zdefiniowane przez WCF, zobacz <xref:System.IdentityModel.Claims.ClaimTypes> klasy.</span><span class="sxs-lookup"><span data-stu-id="48edc-129">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="48edc-130">Wybierz lub zdefiniuj serializowalny typ nieiwersyjny dla zasobu.</span><span class="sxs-lookup"><span data-stu-id="48edc-130">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="48edc-131">Zasób jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="48edc-131">A resource is an object.</span></span> <span data-ttu-id="48edc-132">Typ CLR zasobu musi być serializowalny, ponieważ oświadczenia są serializowane w różnych punktach przez WCF.</span><span class="sxs-lookup"><span data-stu-id="48edc-132">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="48edc-133">Typy pierwotne są już serializable.</span><span class="sxs-lookup"><span data-stu-id="48edc-133">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="48edc-134">Po zdefiniowaniu nowego typu <xref:System.Runtime.Serialization.DataContractAttribute> zastosuj do klasy.</span><span class="sxs-lookup"><span data-stu-id="48edc-134">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="48edc-135">Zastosuj również <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut do wszystkich elementów członkowskich nowego typu, które muszą być serializowane jako część oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="48edc-135">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="48edc-136">Poniższy przykład kodu definiuje niestandardowy `MyResourceType`typ zasobu o nazwie .</span><span class="sxs-lookup"><span data-stu-id="48edc-136">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)]
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]
  
    3. <span data-ttu-id="48edc-137">Wybierz prawo, które jest zdefiniowane przez WCF lub unikatową wartość dla prawa niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="48edc-137">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="48edc-138">Prawo jest unikatowy identyfikator ciągu.</span><span class="sxs-lookup"><span data-stu-id="48edc-138">A right is a unique string identifier.</span></span> <span data-ttu-id="48edc-139">Prawa, które są zdefiniowane przez WCF są zdefiniowane w <xref:System.IdentityModel.Claims.Rights> klasie.</span><span class="sxs-lookup"><span data-stu-id="48edc-139">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="48edc-140">Jest to niestandardowy projektant oświadczeń jest odpowiedzialny, aby upewnić się, że identyfikator ciągu, który jest używany dla prawej jest unikatowa.</span><span class="sxs-lookup"><span data-stu-id="48edc-140">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="48edc-141">Poniższy przykład kodu tworzy oświadczenie niestandardowe `http://example.org/claims/complexcustomclaim`z typem `MyResourceType`oświadczenia , <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> niestandardowy typ zasobu , i z prawej.</span><span class="sxs-lookup"><span data-stu-id="48edc-141">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)]
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]
  
## <a name="example"></a><span data-ttu-id="48edc-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="48edc-142">Example</span></span>  
 <span data-ttu-id="48edc-143">W poniższym przykładzie kodu pokazano, jak utworzyć oświadczenie niestandardowe z pierwotnym typem zasobu i oświadczeniem niestandardowym z nieiderzym typem zasobu.</span><span class="sxs-lookup"><span data-stu-id="48edc-143">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="48edc-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48edc-144">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="48edc-145">Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości</span><span class="sxs-lookup"><span data-stu-id="48edc-145">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
