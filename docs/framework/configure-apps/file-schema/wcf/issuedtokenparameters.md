---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 07fc2c4c52c29de1cfc9f498a6dc6b6da887b502
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925342"
---
# <a name="issuedtokenparameters"></a><span data-ttu-id="8e388-101">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="8e388-101">\<issuedTokenParameters></span></span>
<span data-ttu-id="8e388-102">Określa parametry tokenu zabezpieczającego wydanego w federacyjnym scenariuszu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="8e388-102">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="8e388-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8e388-103">\<system.serviceModel></span></span>  
<span data-ttu-id="8e388-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="8e388-104">\<bindings></span></span>  
<span data-ttu-id="8e388-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="8e388-105">\<customBinding></span></span>  
<span data-ttu-id="8e388-106">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="8e388-106">\<binding></span></span>  
<span data-ttu-id="8e388-107">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="8e388-107">\<security></span></span>  
<span data-ttu-id="8e388-108">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="8e388-108">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e388-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="8e388-109">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="8e388-110">Typ</span><span class="sxs-lookup"><span data-stu-id="8e388-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e388-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8e388-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8e388-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8e388-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e388-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8e388-113">Attributes</span></span>  
  
|<span data-ttu-id="8e388-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8e388-114">Attribute</span></span>|<span data-ttu-id="8e388-115">Opis</span><span class="sxs-lookup"><span data-stu-id="8e388-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8e388-116">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="8e388-116">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="8e388-117">Określa wersje specyfikacji zabezpieczeń (WS-Security, WS-Trust, WS-Secure konwersacja i zasady WS-Security), które muszą być obsługiwane przez powiązanie.</span><span class="sxs-lookup"><span data-stu-id="8e388-117">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="8e388-118">Ta wartość jest typu <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="8e388-118">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="8e388-119">Dołączanie</span><span class="sxs-lookup"><span data-stu-id="8e388-119">inclusionMode</span></span>|<span data-ttu-id="8e388-120">Określa wymagania dotyczące dołączania tokenu.</span><span class="sxs-lookup"><span data-stu-id="8e388-120">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="8e388-121">Ten atrybut jest typu <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="8e388-121">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="8e388-122">keySize</span><span class="sxs-lookup"><span data-stu-id="8e388-122">keySize</span></span>|<span data-ttu-id="8e388-123">Liczba całkowita określająca rozmiar klucza tokenu.</span><span class="sxs-lookup"><span data-stu-id="8e388-123">An integer that specifies the token key size.</span></span> <span data-ttu-id="8e388-124">Wartość domyślna to 256.</span><span class="sxs-lookup"><span data-stu-id="8e388-124">The default value is 256.</span></span>|  
|<span data-ttu-id="8e388-125">keyType</span><span class="sxs-lookup"><span data-stu-id="8e388-125">keyType</span></span>|<span data-ttu-id="8e388-126">Prawidłowa wartość <xref:System.IdentityModel.Tokens.SecurityKeyType> określająca typ klucza.</span><span class="sxs-lookup"><span data-stu-id="8e388-126">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="8e388-127">Wartość domyślna to `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="8e388-127">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="8e388-128">Obiektu TokenType</span><span class="sxs-lookup"><span data-stu-id="8e388-128">tokenType</span></span>|<span data-ttu-id="8e388-129">Ciąg określający typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="8e388-129">A string that specifies the token type.</span></span> <span data-ttu-id="8e388-130">Wartość domyślna to "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="8e388-130">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8e388-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8e388-131">Child Elements</span></span>  
  
|<span data-ttu-id="8e388-132">Element</span><span class="sxs-lookup"><span data-stu-id="8e388-132">Element</span></span>|<span data-ttu-id="8e388-133">Opis</span><span class="sxs-lookup"><span data-stu-id="8e388-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e388-134">\<additionalRequestParameters></span><span class="sxs-lookup"><span data-stu-id="8e388-134">\<additionalRequestParameters></span></span>](additionalrequestparameters-element.md)|<span data-ttu-id="8e388-135">Kolekcja elementów konfiguracji, które określają dodatkowe parametry żądania.</span><span class="sxs-lookup"><span data-stu-id="8e388-135">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="8e388-136">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="8e388-136">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="8e388-137">Określa kolekcję wymaganych typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="8e388-137">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="8e388-138">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="8e388-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="8e388-139">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="8e388-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="8e388-140">Każdy element w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń, które powinny być wyświetlane w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="8e388-140">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="8e388-141">\<> wystawcy</span><span class="sxs-lookup"><span data-stu-id="8e388-141">\<issuer></span></span>](issuer-of-issuedtokenparameters.md)|<span data-ttu-id="8e388-142">Element konfiguracji, który określa punkt końcowy, który wystawia bieżący token.</span><span class="sxs-lookup"><span data-stu-id="8e388-142">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="8e388-143">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="8e388-143">\<issuerMetadata></span></span>](issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="8e388-144">Element konfiguracji, który określa adres punktu końcowego metadanych wystawcy tokenu.</span><span class="sxs-lookup"><span data-stu-id="8e388-144">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8e388-145">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8e388-145">Parent Elements</span></span>  
  
|<span data-ttu-id="8e388-146">Element</span><span class="sxs-lookup"><span data-stu-id="8e388-146">Element</span></span>|<span data-ttu-id="8e388-147">Opis</span><span class="sxs-lookup"><span data-stu-id="8e388-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e388-148">\<secureConversationBootstrap></span><span class="sxs-lookup"><span data-stu-id="8e388-148">\<secureConversationBootstrap></span></span>](secureconversationbootstrap.md)|<span data-ttu-id="8e388-149">Określa wartości domyślne używane do inicjowania usługi bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="8e388-149">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="8e388-150">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="8e388-150">\<security></span></span>](security-of-custombinding.md)|<span data-ttu-id="8e388-151">Określa opcje zabezpieczeń dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="8e388-151">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e388-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e388-152">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="8e388-153">Powiązania</span><span class="sxs-lookup"><span data-stu-id="8e388-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8e388-154">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="8e388-154">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8e388-155">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="8e388-155">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="8e388-156">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="8e388-156">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="8e388-157">Instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="8e388-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="8e388-158">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="8e388-158">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="8e388-159">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="8e388-159">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="8e388-160">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="8e388-160">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="8e388-161">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="8e388-161">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="8e388-162">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="8e388-162">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
