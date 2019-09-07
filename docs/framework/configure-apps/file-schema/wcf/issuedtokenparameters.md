---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 8432463ff62e4b5e54a491b574cc6a5285efe220
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397957"
---
# <a name="issuedtokenparameters"></a><span data-ttu-id="2c68f-101">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="2c68f-101">\<issuedTokenParameters></span></span>
<span data-ttu-id="2c68f-102">Określa parametry tokenu zabezpieczającego wydanego w federacyjnym scenariuszu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="2c68f-102">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
<span data-ttu-id="2c68f-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2c68f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2c68f-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2c68f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2c68f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="2c68f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="2c68f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="2c68f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="2c68f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="2c68f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="2c68f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="2c68f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="2c68f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuedTokenParameters >**</span><span class="sxs-lookup"><span data-stu-id="2c68f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenParameters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c68f-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c68f-110">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="2c68f-111">Typ</span><span class="sxs-lookup"><span data-stu-id="2c68f-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c68f-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2c68f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2c68f-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2c68f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c68f-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2c68f-114">Attributes</span></span>  
  
|<span data-ttu-id="2c68f-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2c68f-115">Attribute</span></span>|<span data-ttu-id="2c68f-116">Opis</span><span class="sxs-lookup"><span data-stu-id="2c68f-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2c68f-117">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="2c68f-117">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="2c68f-118">Określa wersje specyfikacji zabezpieczeń (WS-Security, WS-Trust, WS-Secure konwersacja i zasady WS-Security), które muszą być obsługiwane przez powiązanie.</span><span class="sxs-lookup"><span data-stu-id="2c68f-118">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="2c68f-119">Ta wartość jest typu <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="2c68f-119">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="2c68f-120">Dołączanie</span><span class="sxs-lookup"><span data-stu-id="2c68f-120">inclusionMode</span></span>|<span data-ttu-id="2c68f-121">Określa wymagania dotyczące dołączania tokenu.</span><span class="sxs-lookup"><span data-stu-id="2c68f-121">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="2c68f-122">Ten atrybut jest typu <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="2c68f-122">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="2c68f-123">keySize</span><span class="sxs-lookup"><span data-stu-id="2c68f-123">keySize</span></span>|<span data-ttu-id="2c68f-124">Liczba całkowita określająca rozmiar klucza tokenu.</span><span class="sxs-lookup"><span data-stu-id="2c68f-124">An integer that specifies the token key size.</span></span> <span data-ttu-id="2c68f-125">Wartość domyślna to 256.</span><span class="sxs-lookup"><span data-stu-id="2c68f-125">The default value is 256.</span></span>|  
|<span data-ttu-id="2c68f-126">keyType</span><span class="sxs-lookup"><span data-stu-id="2c68f-126">keyType</span></span>|<span data-ttu-id="2c68f-127">Prawidłowa wartość <xref:System.IdentityModel.Tokens.SecurityKeyType> określająca typ klucza.</span><span class="sxs-lookup"><span data-stu-id="2c68f-127">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="2c68f-128">Wartość domyślna to `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="2c68f-128">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="2c68f-129">Obiektu TokenType</span><span class="sxs-lookup"><span data-stu-id="2c68f-129">tokenType</span></span>|<span data-ttu-id="2c68f-130">Ciąg określający typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="2c68f-130">A string that specifies the token type.</span></span> <span data-ttu-id="2c68f-131">Wartość domyślna to "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="2c68f-131">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c68f-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2c68f-132">Child Elements</span></span>  
  
|<span data-ttu-id="2c68f-133">Element</span><span class="sxs-lookup"><span data-stu-id="2c68f-133">Element</span></span>|<span data-ttu-id="2c68f-134">Opis</span><span class="sxs-lookup"><span data-stu-id="2c68f-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c68f-135">\<additionalRequestParameters></span><span class="sxs-lookup"><span data-stu-id="2c68f-135">\<additionalRequestParameters></span></span>](additionalrequestparameters-element.md)|<span data-ttu-id="2c68f-136">Kolekcja elementów konfiguracji, które określają dodatkowe parametry żądania.</span><span class="sxs-lookup"><span data-stu-id="2c68f-136">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="2c68f-137">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="2c68f-137">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="2c68f-138">Określa kolekcję wymaganych typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="2c68f-138">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="2c68f-139">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="2c68f-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="2c68f-140">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="2c68f-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="2c68f-141">Każdy element w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń, które powinny być wyświetlane w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="2c68f-141">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="2c68f-142">\<> wystawcy</span><span class="sxs-lookup"><span data-stu-id="2c68f-142">\<issuer></span></span>](issuer-of-issuedtokenparameters.md)|<span data-ttu-id="2c68f-143">Element konfiguracji, który określa punkt końcowy, który wystawia bieżący token.</span><span class="sxs-lookup"><span data-stu-id="2c68f-143">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="2c68f-144">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="2c68f-144">\<issuerMetadata></span></span>](issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="2c68f-145">Element konfiguracji, który określa adres punktu końcowego metadanych wystawcy tokenu.</span><span class="sxs-lookup"><span data-stu-id="2c68f-145">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2c68f-146">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2c68f-146">Parent Elements</span></span>  
  
|<span data-ttu-id="2c68f-147">Element</span><span class="sxs-lookup"><span data-stu-id="2c68f-147">Element</span></span>|<span data-ttu-id="2c68f-148">Opis</span><span class="sxs-lookup"><span data-stu-id="2c68f-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c68f-149">\<secureConversationBootstrap></span><span class="sxs-lookup"><span data-stu-id="2c68f-149">\<secureConversationBootstrap></span></span>](secureconversationbootstrap.md)|<span data-ttu-id="2c68f-150">Określa wartości domyślne używane do inicjowania usługi bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="2c68f-150">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="2c68f-151">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="2c68f-151">\<security></span></span>](security-of-custombinding.md)|<span data-ttu-id="2c68f-152">Określa opcje zabezpieczeń dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="2c68f-152">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2c68f-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c68f-153">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="2c68f-154">Powiązania</span><span class="sxs-lookup"><span data-stu-id="2c68f-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2c68f-155">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="2c68f-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="2c68f-156">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="2c68f-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="2c68f-157">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="2c68f-157">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="2c68f-158">Instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="2c68f-158">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="2c68f-159">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="2c68f-159">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="2c68f-160">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="2c68f-160">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="2c68f-161">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="2c68f-161">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="2c68f-162">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="2c68f-162">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="2c68f-163">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="2c68f-163">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
