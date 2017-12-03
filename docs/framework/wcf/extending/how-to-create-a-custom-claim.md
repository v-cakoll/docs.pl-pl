---
title: "Instrukcje: Tworzenie oświadczenia niestandardowego"
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
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f0cc23d5b6720d78afdc1acd50a2b84b76b977e9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="32546-102">Instrukcje: Tworzenie oświadczenia niestandardowego</span><span class="sxs-lookup"><span data-stu-id="32546-102">How to: Create a Custom Claim</span></span>
<span data-ttu-id="32546-103">Infrastruktura modelu tożsamości w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] udostępnia funkcje pomocnicze zestaw wbudowanych oświadczenia i prawa do tworzenia <xref:System.IdentityModel.Claims.Claim> wystąpień z tych typów i praw.</span><span class="sxs-lookup"><span data-stu-id="32546-103">The Identity Model infrastructure in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="32546-104">Te wbudowane oświadczenia są przeznaczone do informacji o modelu znaleziono w kliencie poświadczeń typy, które [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje domyślnie.</span><span class="sxs-lookup"><span data-stu-id="32546-104">These built-in claims are designed to model information found in client credential types that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports by default.</span></span> <span data-ttu-id="32546-105">W wielu przypadkach wbudowanych oświadczenia są wystarczające; Jednak niektóre aplikacje mogą wymagać oświadczenia niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="32546-105">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="32546-106">Oświadczenie składa się z typu oświadczenia, zasobów, dla której oświadczenia dotyczy i praw potwierdzona za pośrednictwem tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="32546-106">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="32546-107">W tym temacie opisano tworzenie oświadczenia niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="32546-107">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="32546-108">Aby tworzenie oświadczenia niestandardowego, który jest oparty na typie danych pierwotnych</span><span class="sxs-lookup"><span data-stu-id="32546-108">To create a custom claim that is based on a primitive data type</span></span>  
  
1.  <span data-ttu-id="32546-109">Tworzenie oświadczenia niestandardowego przez przekazanie typu oświadczenia i wartości zasobów prawo do <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="32546-109">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1.  <span data-ttu-id="32546-110">Wybierz unikatową wartość dla typu oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="32546-110">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="32546-111">Typ oświadczenia jest identyfikator unikatowy ciąg.</span><span class="sxs-lookup"><span data-stu-id="32546-111">The claim type is a unique string identifier.</span></span> <span data-ttu-id="32546-112">Odpowiada projektanta oświadczenia niestandardowego upewnij się, że identyfikator ciągu, który jest używany dla typu oświadczenia jest unikatowa.</span><span class="sxs-lookup"><span data-stu-id="32546-112">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="32546-113">Aby uzyskać listę typów oświadczeń, które są zdefiniowane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], zobacz <xref:System.IdentityModel.Claims.ClaimTypes> klasy.</span><span class="sxs-lookup"><span data-stu-id="32546-113">For a list of claim types that are defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2.  <span data-ttu-id="32546-114">Wybierz typ danych pierwotnych i wartość zasobu.</span><span class="sxs-lookup"><span data-stu-id="32546-114">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="32546-115">Zasób jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="32546-115">A resource is an object.</span></span> <span data-ttu-id="32546-116">Typ CLR zasób może być typu pierwotnego, takich jak <xref:System.String> lub <xref:System.Int32>, lub typ możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="32546-116">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="32546-117">Typ CLR zasobu musi być możliwy do serializacji, ponieważ oświadczenia są serializowane w różnych momentach przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="32546-117">The CLR type of the resource must be serializable, because claims are serialized at various points by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="32546-118">Typy pierwotne są możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="32546-118">Primitive types are serializable.</span></span>  
  
    3.  <span data-ttu-id="32546-119">Wybierz uprawnienia, który jest definiowana za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lub unikatową wartość dla niestandardowego prawo.</span><span class="sxs-lookup"><span data-stu-id="32546-119">Choose a right that is defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="32546-120">Prawo to identyfikator unikatowy ciąg.</span><span class="sxs-lookup"><span data-stu-id="32546-120">A right is a unique string identifier.</span></span> <span data-ttu-id="32546-121">Prawa, które są zdefiniowane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] są zdefiniowane w <xref:System.IdentityModel.Claims.Rights> klasy.</span><span class="sxs-lookup"><span data-stu-id="32546-121">The rights that are defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="32546-122">Odpowiada projektanta oświadczenia niestandardowego upewnij się, że identyfikator ciągu, który jest używany do prawej jest unikatowa.</span><span class="sxs-lookup"><span data-stu-id="32546-122">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="32546-123">Poniższy przykład kodu tworzy oświadczenia niestandardowego o typie oświadczenia `http://example.org/claims/simplecustomclaim`, dla zasobu o nazwie `Driver's License`oraz <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> prawo.</span><span class="sxs-lookup"><span data-stu-id="32546-123">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="32546-124">Aby tworzenie oświadczenia niestandardowego, który jest oparty na typie danych innego niż pierwotny</span><span class="sxs-lookup"><span data-stu-id="32546-124">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1.  <span data-ttu-id="32546-125">Tworzenie oświadczenia niestandardowego przez przekazanie typu oświadczenia i wartości zasobów prawo do <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="32546-125">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1.  <span data-ttu-id="32546-126">Wybierz unikatową wartość dla typu oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="32546-126">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="32546-127">Typ oświadczenia jest identyfikator unikatowy ciąg.</span><span class="sxs-lookup"><span data-stu-id="32546-127">The claim type is a unique string identifier.</span></span> <span data-ttu-id="32546-128">Odpowiada projektanta oświadczenia niestandardowego upewnij się, że identyfikator ciągu, który jest używany dla typu oświadczenia jest unikatowa.</span><span class="sxs-lookup"><span data-stu-id="32546-128">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="32546-129">Aby uzyskać listę typów oświadczeń, które są zdefiniowane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], zobacz <xref:System.IdentityModel.Claims.ClaimTypes> klasy.</span><span class="sxs-lookup"><span data-stu-id="32546-129">For a list of claim types that are defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2.  <span data-ttu-id="32546-130">Wybierz lub zdefiniuj serializacji typu innego niż pierwotny dla zasobu.</span><span class="sxs-lookup"><span data-stu-id="32546-130">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="32546-131">Zasób jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="32546-131">A resource is an object.</span></span> <span data-ttu-id="32546-132">Typ CLR zasobu musi być możliwy do serializacji, ponieważ oświadczenia są serializowane w różnych momentach przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="32546-132">The CLR type of the resource must be serializable, because claims are serialized at various points by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="32546-133">Typy pierwotne są już możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="32546-133">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="32546-134">Jeśli nowy typ jest zdefiniowany, zastosuj <xref:System.Runtime.Serialization.DataContractAttribute> do klasy.</span><span class="sxs-lookup"><span data-stu-id="32546-134">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="32546-135">Mają zastosowanie również <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu do wszystkich elementów członkowskich typu nowe, które muszą być Zserializowany jako część oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="32546-135">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="32546-136">Poniższy przykład kodu określa niestandardowy typ zasobu o nazwie `MyResourceType`.</span><span class="sxs-lookup"><span data-stu-id="32546-136">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3.  <span data-ttu-id="32546-137">Wybierz uprawnienia, który jest definiowana za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lub unikatową wartość dla niestandardowego prawo.</span><span class="sxs-lookup"><span data-stu-id="32546-137">Choose a right that is defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="32546-138">Prawo to identyfikator unikatowy ciąg.</span><span class="sxs-lookup"><span data-stu-id="32546-138">A right is a unique string identifier.</span></span> <span data-ttu-id="32546-139">Prawa, które są zdefiniowane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] są zdefiniowane w <xref:System.IdentityModel.Claims.Rights> klasy.</span><span class="sxs-lookup"><span data-stu-id="32546-139">The rights that are defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="32546-140">Odpowiada projektanta oświadczenia niestandardowego upewnij się, że identyfikator ciągu, który jest używany do prawej jest unikatowa.</span><span class="sxs-lookup"><span data-stu-id="32546-140">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="32546-141">Poniższy przykład kodu tworzy oświadczenia niestandardowego o typie oświadczenia `http://example.org/claims/complexcustomclaim`, niestandardowy typ zasobu z `MyResourceType`oraz <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> prawo.</span><span class="sxs-lookup"><span data-stu-id="32546-141">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a><span data-ttu-id="32546-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="32546-142">Example</span></span>  
 <span data-ttu-id="32546-143">W poniższym przykładzie pokazano, jak tworzenie oświadczenia niestandardowego o typie pierwotnym zasobów i oświadczenia niestandardowe przy użyciu typu innego niż pierwotny zasobu.</span><span class="sxs-lookup"><span data-stu-id="32546-143">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="32546-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32546-144">See Also</span></span>  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Claims.Rights>  
 <xref:System.IdentityModel.Claims.ClaimTypes>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [<span data-ttu-id="32546-145">Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości</span><span class="sxs-lookup"><span data-stu-id="32546-145">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="32546-146">Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości</span><span class="sxs-lookup"><span data-stu-id="32546-146">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
