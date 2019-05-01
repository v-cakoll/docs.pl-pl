---
title: 'Instrukcje: tworzenie oświadczenia niestandardowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: 1892e910a86e01b7b2ee0f6a2403ad7af4688808
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857782"
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="98098-102">Instrukcje: tworzenie oświadczenia niestandardowego</span><span class="sxs-lookup"><span data-stu-id="98098-102">How to: Create a Custom Claim</span></span>
<span data-ttu-id="98098-103">Infrastruktura modelu tożsamości w Windows Communication Foundation (WCF) zapewnia zestaw typów wbudowanych oświadczeń i uprawnień przy użyciu funkcji pomocnika dla tworzenia <xref:System.IdentityModel.Claims.Claim> wystąpień z tych typów i praw.</span><span class="sxs-lookup"><span data-stu-id="98098-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="98098-104">Te wbudowane oświadczenia są przeznaczone do informacji o modelu znaleziono w typy poświadczeń klienta, które obsługuje WCF domyślnie.</span><span class="sxs-lookup"><span data-stu-id="98098-104">These built-in claims are designed to model information found in client credential types that WCF supports by default.</span></span> <span data-ttu-id="98098-105">W wielu przypadkach wbudowanych oświadczenia są wystarczające; Jednak niektóre aplikacje mogą wymagać oświadczenia niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="98098-105">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="98098-106">Oświadczenia składa się z typu oświadczenia, zasobów, dla której oświadczenia ma zastosowanie do i potwierdzone praw za pośrednictwem tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="98098-106">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="98098-107">W tym temacie opisano tworzenie oświadczenia niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="98098-107">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="98098-108">Aby utworzyć oświadczenia niestandardowego, który jest oparty na typie danych pierwotnych</span><span class="sxs-lookup"><span data-stu-id="98098-108">To create a custom claim that is based on a primitive data type</span></span>  
  
1. <span data-ttu-id="98098-109">Tworzenie oświadczenia niestandardowego, przekazując typ oświadczenia, wartość zasobu i po prawej stronie, aby <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="98098-109">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="98098-110">Decyzję w sprawie unikatową wartość dla typu oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="98098-110">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="98098-111">Typ oświadczenia jest identyfikator unikatowy ciąg.</span><span class="sxs-lookup"><span data-stu-id="98098-111">The claim type is a unique string identifier.</span></span> <span data-ttu-id="98098-112">Odpowiada za projektanta oświadczenia niestandardowego upewnij się, że identyfikator ciągu, który jest używany dla typu oświadczenia jest unikatowa.</span><span class="sxs-lookup"><span data-stu-id="98098-112">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="98098-113">Aby uzyskać listę typów oświadczeń, które są zdefiniowane przez architekturę WCF, zobacz <xref:System.IdentityModel.Claims.ClaimTypes> klasy.</span><span class="sxs-lookup"><span data-stu-id="98098-113">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="98098-114">Wybierz typ danych pierwotnych i wartość zasobu.</span><span class="sxs-lookup"><span data-stu-id="98098-114">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="98098-115">Zasób jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="98098-115">A resource is an object.</span></span> <span data-ttu-id="98098-116">Typ CLR zasób może być podstawowy, taką jak <xref:System.String> lub <xref:System.Int32>, lub dowolny typ możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="98098-116">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="98098-117">Typ CLR zasobu musi być możliwy do serializacji, ponieważ oświadczeń są serializowane w różnych momentach przez architekturę WCF.</span><span class="sxs-lookup"><span data-stu-id="98098-117">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="98098-118">Typy pierwotne są możliwe do serializacji.</span><span class="sxs-lookup"><span data-stu-id="98098-118">Primitive types are serializable.</span></span>  
  
    3. <span data-ttu-id="98098-119">Wybierz po prawej stronie, który jest definiowany przez WCF lub unikatową wartość dla niestandardowych po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="98098-119">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="98098-120">Po prawej stronie jest identyfikator unikatowy ciąg.</span><span class="sxs-lookup"><span data-stu-id="98098-120">A right is a unique string identifier.</span></span> <span data-ttu-id="98098-121">Prawa, które są definiowane przez architekturę WCF są zdefiniowane w <xref:System.IdentityModel.Claims.Rights> klasy.</span><span class="sxs-lookup"><span data-stu-id="98098-121">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="98098-122">Odpowiada za projektanta oświadczenia niestandardowego upewnij się, że identyfikator ciągu, który jest używany do prawej strony jest unikatowa.</span><span class="sxs-lookup"><span data-stu-id="98098-122">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="98098-123">Poniższy przykład kodu tworzy niestandardowe oświadczenia o typie oświadczenia `http://example.org/claims/simplecustomclaim`, zasobu o nazwie `Driver's License`i <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> prawo.</span><span class="sxs-lookup"><span data-stu-id="98098-123">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="98098-124">Aby utworzyć oświadczenia niestandardowego, który jest oparty na typie danych niepodstawowe</span><span class="sxs-lookup"><span data-stu-id="98098-124">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1. <span data-ttu-id="98098-125">Tworzenie oświadczenia niestandardowego, przekazując typ oświadczenia, wartość zasobu i po prawej stronie, aby <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="98098-125">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="98098-126">Decyzję w sprawie unikatową wartość dla typu oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="98098-126">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="98098-127">Typ oświadczenia jest identyfikator unikatowy ciąg.</span><span class="sxs-lookup"><span data-stu-id="98098-127">The claim type is a unique string identifier.</span></span> <span data-ttu-id="98098-128">Odpowiada za projektanta oświadczenia niestandardowego upewnij się, że identyfikator ciągu, który jest używany dla typu oświadczenia jest unikatowa.</span><span class="sxs-lookup"><span data-stu-id="98098-128">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="98098-129">Aby uzyskać listę typów oświadczeń, które są zdefiniowane przez architekturę WCF, zobacz <xref:System.IdentityModel.Claims.ClaimTypes> klasy.</span><span class="sxs-lookup"><span data-stu-id="98098-129">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="98098-130">Wybierz, czy definiowane serializacji typu niepodstawowych dla zasobu.</span><span class="sxs-lookup"><span data-stu-id="98098-130">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="98098-131">Zasób jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="98098-131">A resource is an object.</span></span> <span data-ttu-id="98098-132">Typ CLR zasobu musi być możliwy do serializacji, ponieważ oświadczeń są serializowane w różnych momentach przez architekturę WCF.</span><span class="sxs-lookup"><span data-stu-id="98098-132">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="98098-133">Typy pierwotne są już możliwe do serializacji.</span><span class="sxs-lookup"><span data-stu-id="98098-133">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="98098-134">Jeśli nowy typ jest zdefiniowany, zastosuj <xref:System.Runtime.Serialization.DataContractAttribute> do klasy.</span><span class="sxs-lookup"><span data-stu-id="98098-134">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="98098-135">Mają zastosowanie również w <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu dla wszystkich członków nowy typ, który musi być serializowana jako część oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="98098-135">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="98098-136">Poniższy kod definiuje niestandardowy typ zasobu o nazwie `MyResourceType`.</span><span class="sxs-lookup"><span data-stu-id="98098-136">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3. <span data-ttu-id="98098-137">Wybierz po prawej stronie, który jest definiowany przez WCF lub unikatową wartość dla niestandardowych po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="98098-137">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="98098-138">Po prawej stronie jest identyfikator unikatowy ciąg.</span><span class="sxs-lookup"><span data-stu-id="98098-138">A right is a unique string identifier.</span></span> <span data-ttu-id="98098-139">Prawa, które są definiowane przez architekturę WCF są zdefiniowane w <xref:System.IdentityModel.Claims.Rights> klasy.</span><span class="sxs-lookup"><span data-stu-id="98098-139">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="98098-140">Odpowiada za projektanta oświadczenia niestandardowego upewnij się, że identyfikator ciągu, który jest używany do prawej strony jest unikatowa.</span><span class="sxs-lookup"><span data-stu-id="98098-140">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="98098-141">Poniższy przykład kodu tworzy niestandardowe oświadczenia o typie oświadczenia `http://example.org/claims/complexcustomclaim`, niestandardowy typ zasobu z `MyResourceType`i <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> prawo.</span><span class="sxs-lookup"><span data-stu-id="98098-141">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a><span data-ttu-id="98098-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="98098-142">Example</span></span>  
 <span data-ttu-id="98098-143">Poniższy przykład kodu pokazuje, jak utworzyć oświadczenia niestandardowego z typem pierwotnym zasobów i oświadczenia niestandardowego typu zasobów niepodstawowe.</span><span class="sxs-lookup"><span data-stu-id="98098-143">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="98098-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98098-144">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="98098-145">Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości</span><span class="sxs-lookup"><span data-stu-id="98098-145">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
