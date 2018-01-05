---
title: '&lt;issuedTokenParameters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bac725e0c4fe590623ac82ec45bcf669a2e57179
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuedtokenparametersgt"></a><span data-ttu-id="1a50a-102">&lt;issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="1a50a-102">&lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="1a50a-103">Określa parametry dla tokenu zabezpieczenia, wydane w federacyjnym scenariuszu zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="1a50a-103">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="1a50a-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="1a50a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1a50a-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="1a50a-105">\<bindings></span></span>  
<span data-ttu-id="1a50a-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1a50a-106">\<customBinding></span></span>  
<span data-ttu-id="1a50a-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="1a50a-107">\<binding></span></span>  
<span data-ttu-id="1a50a-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="1a50a-108">\<security></span></span>  
<span data-ttu-id="1a50a-109">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="1a50a-109">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a50a-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a50a-110">Syntax</span></span>  
  
```xml  
<issuedTokenParameters   
      DefaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"  
      inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"  
      keySize="Integer"  
   keyType="AsymmetricKey/BearerKey/SymmetricKey"  
      tokenType="String" >  
   <additionalRequestParameters />  
      <claimTypeRequirements>  
            <add claimType="URI"  
           isOptional="Boolean" />  
      </claimTypeRequirements>  
      <issuer address="String"   
                      binding=" " />  
      <issuerMetadata address="String" />   
</issuedTokenParameters>  
```  
  
## <a name="type"></a><span data-ttu-id="1a50a-111">Typ</span><span class="sxs-lookup"><span data-stu-id="1a50a-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a50a-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1a50a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1a50a-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1a50a-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a50a-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1a50a-114">Attributes</span></span>  
  
|<span data-ttu-id="1a50a-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1a50a-115">Attribute</span></span>|<span data-ttu-id="1a50a-116">Opis</span><span class="sxs-lookup"><span data-stu-id="1a50a-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1a50a-117">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="1a50a-117">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="1a50a-118">Określa wersje specyfikacji zabezpieczenia (WS-Security WS-Trust, zabezpieczenia WS konwersacji i polityki WS-Security) które muszą być obsługiwane przez powiązanie.</span><span class="sxs-lookup"><span data-stu-id="1a50a-118">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="1a50a-119">Ta wartość jest typu <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="1a50a-119">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="1a50a-120">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="1a50a-120">inclusionMode</span></span>|<span data-ttu-id="1a50a-121">Określa wymagań dotyczących dołączania tokenu.</span><span class="sxs-lookup"><span data-stu-id="1a50a-121">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="1a50a-122">Ten atrybut jest typu <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="1a50a-122">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="1a50a-123">KeySize</span><span class="sxs-lookup"><span data-stu-id="1a50a-123">keySize</span></span>|<span data-ttu-id="1a50a-124">Liczba całkowita określająca rozmiar klucza tokenu.</span><span class="sxs-lookup"><span data-stu-id="1a50a-124">An integer that specifies the token key size.</span></span> <span data-ttu-id="1a50a-125">Wartość domyślna to 256.</span><span class="sxs-lookup"><span data-stu-id="1a50a-125">The default value is 256.</span></span>|  
|<span data-ttu-id="1a50a-126">Właściwość KeyType</span><span class="sxs-lookup"><span data-stu-id="1a50a-126">keyType</span></span>|<span data-ttu-id="1a50a-127">Nieprawidłowa wartość <xref:System.IdentityModel.Tokens.SecurityKeyType> , który określa typ klucza.</span><span class="sxs-lookup"><span data-stu-id="1a50a-127">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="1a50a-128">Wartość domyślna to `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="1a50a-128">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="1a50a-129">tokenType</span><span class="sxs-lookup"><span data-stu-id="1a50a-129">tokenType</span></span>|<span data-ttu-id="1a50a-130">Ciąg określający typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="1a50a-130">A string that specifies the token type.</span></span> <span data-ttu-id="1a50a-131">Wartość domyślna to "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="1a50a-131">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a50a-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1a50a-132">Child Elements</span></span>  
  
|<span data-ttu-id="1a50a-133">Element</span><span class="sxs-lookup"><span data-stu-id="1a50a-133">Element</span></span>|<span data-ttu-id="1a50a-134">Opis</span><span class="sxs-lookup"><span data-stu-id="1a50a-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a50a-135">\<additionalRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="1a50a-135">\<additionalRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|<span data-ttu-id="1a50a-136">Kolekcja elementów konfiguracji, które określają dodatkowe parametry żądania.</span><span class="sxs-lookup"><span data-stu-id="1a50a-136">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="1a50a-137">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="1a50a-137">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="1a50a-138">Określa kolekcję wymaganych typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="1a50a-138">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="1a50a-139">W federacyjnym scenariuszu usług stanu wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="1a50a-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="1a50a-140">Na przykład poświadczenia przychodzące musi mieć określone typy oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="1a50a-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="1a50a-141">Każdy element w tej kolekcji Określa typy wymaganych i opcjonalnych oświadczeń, które mogą występować w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="1a50a-141">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="1a50a-142">\<Wystawca ></span><span class="sxs-lookup"><span data-stu-id="1a50a-142">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|<span data-ttu-id="1a50a-143">Element konfiguracji, który określa punkt końcowy, który wystawia bieżący token.</span><span class="sxs-lookup"><span data-stu-id="1a50a-143">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="1a50a-144">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="1a50a-144">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="1a50a-145">Element konfiguracji, który określa adres punktu końcowego metadanych wystawca tokenów.</span><span class="sxs-lookup"><span data-stu-id="1a50a-145">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1a50a-146">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1a50a-146">Parent Elements</span></span>  
  
|<span data-ttu-id="1a50a-147">Element</span><span class="sxs-lookup"><span data-stu-id="1a50a-147">Element</span></span>|<span data-ttu-id="1a50a-148">Opis</span><span class="sxs-lookup"><span data-stu-id="1a50a-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a50a-149">\<secureConversationBootstrap ></span><span class="sxs-lookup"><span data-stu-id="1a50a-149">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="1a50a-150">Określa wartości domyślne używane do inicjowania usługi bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="1a50a-150">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="1a50a-151">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="1a50a-151">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="1a50a-152">Określa opcje zabezpieczeń dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="1a50a-152">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1a50a-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a50a-153">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="1a50a-154">Powiązania</span><span class="sxs-lookup"><span data-stu-id="1a50a-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="1a50a-155">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="1a50a-155">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="1a50a-156">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="1a50a-156">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="1a50a-157">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1a50a-157">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="1a50a-158">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="1a50a-158">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="1a50a-159">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="1a50a-159">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)  
 [<span data-ttu-id="1a50a-160">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="1a50a-160">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="1a50a-161">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="1a50a-161">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="1a50a-162">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="1a50a-162">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="1a50a-163">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="1a50a-163">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
