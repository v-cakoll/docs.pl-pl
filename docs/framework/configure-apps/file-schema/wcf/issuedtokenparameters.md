---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 6bdf56e3d2084dec8d44e1c4d3f0c1e50b711b92
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153143"
---
# <a name="issuedtokenparameters"></a><span data-ttu-id="8fd8d-101">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="8fd8d-101">\<issuedTokenParameters></span></span>
<span data-ttu-id="8fd8d-102">Określa parametry dla tokenu zabezpieczenia, wydane w federacyjnym scenariuszu zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="8fd8d-102">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="8fd8d-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8fd8d-103">\<system.serviceModel></span></span>  
<span data-ttu-id="8fd8d-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="8fd8d-104">\<bindings></span></span>  
<span data-ttu-id="8fd8d-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="8fd8d-105">\<customBinding></span></span>  
<span data-ttu-id="8fd8d-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="8fd8d-106">\<binding></span></span>  
<span data-ttu-id="8fd8d-107">\<security></span><span class="sxs-lookup"><span data-stu-id="8fd8d-107">\<security></span></span>  
<span data-ttu-id="8fd8d-108">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="8fd8d-108">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fd8d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="8fd8d-109">Syntax</span></span>  
  
```xml  
<issuedTokenParameters defaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"
                       inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"
                       keySize="Integer"
                       keyType="AsymmetricKey/BearerKey/SymmetricKey"
                       tokenType="String">
  <additionalRequestParameters />
  <claimTypeRequirements>
    <add claimType="URI"
         isOptional="Boolean" />
  </claimTypeRequirements>
  <issuer address="String"
          binding="" />
  <issuerMetadata address="String" />
</issuedTokenParameters>
```  
  
## <a name="type"></a><span data-ttu-id="8fd8d-110">Typ</span><span class="sxs-lookup"><span data-stu-id="8fd8d-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8fd8d-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8fd8d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8fd8d-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8fd8d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8fd8d-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8fd8d-113">Attributes</span></span>  
  
|<span data-ttu-id="8fd8d-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8fd8d-114">Attribute</span></span>|<span data-ttu-id="8fd8d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="8fd8d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8fd8d-116">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="8fd8d-116">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="8fd8d-117">Określa wersje specyfikacji zabezpieczenia (WS-Security WS-Trust, zabezpieczenia WS konwersacji i polityki WS-Security) muszą być obsługiwane przez wiązanie.</span><span class="sxs-lookup"><span data-stu-id="8fd8d-117">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="8fd8d-118">Ta wartość jest typu <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="8fd8d-118">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="8fd8d-119">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="8fd8d-119">inclusionMode</span></span>|<span data-ttu-id="8fd8d-120">Określa wymagania dotyczące dołączania tokenu.</span><span class="sxs-lookup"><span data-stu-id="8fd8d-120">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="8fd8d-121">Ten atrybut jest typu <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="8fd8d-121">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="8fd8d-122">keySize</span><span class="sxs-lookup"><span data-stu-id="8fd8d-122">keySize</span></span>|<span data-ttu-id="8fd8d-123">Liczba całkowita określająca rozmiar klucza tokenu.</span><span class="sxs-lookup"><span data-stu-id="8fd8d-123">An integer that specifies the token key size.</span></span> <span data-ttu-id="8fd8d-124">Wartość domyślna to 256.</span><span class="sxs-lookup"><span data-stu-id="8fd8d-124">The default value is 256.</span></span>|  
|<span data-ttu-id="8fd8d-125">keyType</span><span class="sxs-lookup"><span data-stu-id="8fd8d-125">keyType</span></span>|<span data-ttu-id="8fd8d-126">Nieprawidłowa wartość <xref:System.IdentityModel.Tokens.SecurityKeyType> , który określa typ klucza.</span><span class="sxs-lookup"><span data-stu-id="8fd8d-126">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="8fd8d-127">Wartość domyślna to `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="8fd8d-127">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="8fd8d-128">tokenType</span><span class="sxs-lookup"><span data-stu-id="8fd8d-128">tokenType</span></span>|<span data-ttu-id="8fd8d-129">Ciąg określający typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="8fd8d-129">A string that specifies the token type.</span></span> <span data-ttu-id="8fd8d-130">Wartość domyślna to "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="8fd8d-130">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8fd8d-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8fd8d-131">Child Elements</span></span>  
  
|<span data-ttu-id="8fd8d-132">Element</span><span class="sxs-lookup"><span data-stu-id="8fd8d-132">Element</span></span>|<span data-ttu-id="8fd8d-133">Opis</span><span class="sxs-lookup"><span data-stu-id="8fd8d-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8fd8d-134">\<additionalRequestParameters></span><span class="sxs-lookup"><span data-stu-id="8fd8d-134">\<additionalRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|<span data-ttu-id="8fd8d-135">Kolekcja elementów konfiguracji, które określają dodatkowe parametry żądania.</span><span class="sxs-lookup"><span data-stu-id="8fd8d-135">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="8fd8d-136">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="8fd8d-136">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="8fd8d-137">Określa kolekcję wymaganych typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="8fd8d-137">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="8fd8d-138">W federacyjnym scenariuszu usługi stanu wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="8fd8d-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="8fd8d-139">Na przykład poświadczenia przychodzących musi mieć określone typy oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="8fd8d-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="8fd8d-140">Każdy element w tej kolekcji Określa typy wymaganych i opcjonalnych oświadczeń, oczekiwano w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="8fd8d-140">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="8fd8d-141">\<Wystawca ></span><span class="sxs-lookup"><span data-stu-id="8fd8d-141">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|<span data-ttu-id="8fd8d-142">Element konfiguracji, który określa punkt końcowy, który wystawia bieżącego tokenu.</span><span class="sxs-lookup"><span data-stu-id="8fd8d-142">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="8fd8d-143">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="8fd8d-143">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="8fd8d-144">Element konfiguracji, który określa adres punktu końcowego metadanych wystawcy tokenów.</span><span class="sxs-lookup"><span data-stu-id="8fd8d-144">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8fd8d-145">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8fd8d-145">Parent Elements</span></span>  
  
|<span data-ttu-id="8fd8d-146">Element</span><span class="sxs-lookup"><span data-stu-id="8fd8d-146">Element</span></span>|<span data-ttu-id="8fd8d-147">Opis</span><span class="sxs-lookup"><span data-stu-id="8fd8d-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8fd8d-148">\<secureConversationBootstrap></span><span class="sxs-lookup"><span data-stu-id="8fd8d-148">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="8fd8d-149">Określa wartości domyślne używane do inicjowania usługi bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="8fd8d-149">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="8fd8d-150">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="8fd8d-150">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="8fd8d-151">Określa opcje zabezpieczeń dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="8fd8d-151">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8fd8d-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8fd8d-152">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="8fd8d-153">Powiązania</span><span class="sxs-lookup"><span data-stu-id="8fd8d-153">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="8fd8d-154">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="8fd8d-154">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8fd8d-155">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="8fd8d-155">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="8fd8d-156">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="8fd8d-156">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="8fd8d-157">Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="8fd8d-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="8fd8d-158">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="8fd8d-158">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="8fd8d-159">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="8fd8d-159">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="8fd8d-160">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="8fd8d-160">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="8fd8d-161">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="8fd8d-161">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="8fd8d-162">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="8fd8d-162">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
