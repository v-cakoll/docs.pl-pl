---
title: <add> dla <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 6ba935f7f6dae0e4d9e6581f53a50c684efcbed3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153090"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="08291-102">\<dodawanie> wymagań \<dotyczących typu oświadczeń></span><span class="sxs-lookup"><span data-stu-id="08291-102">\<add> of \<claimTypeRequirements></span></span>
<span data-ttu-id="08291-103">Określa typy wymaganych i opcjonalnych oświadczeń, które mają pojawić się w poświadczeniu federacyjnem.</span><span class="sxs-lookup"><span data-stu-id="08291-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="08291-104">Na przykład usługi określają wymagania dotyczące poświadczeń przychodzących, które muszą zawierać określony zestaw typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="08291-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
<span data-ttu-id="08291-105">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="08291-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="08291-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="08291-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="08291-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<wiązania>**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="08291-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="08291-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>niestandardowe**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="08291-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="08291-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wiążące>**</span><span class="sxs-lookup"><span data-stu-id="08291-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="08291-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>bezpieczeństwa**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="08291-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="08291-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wydaneTokenParameters>**](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="08291-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="08291-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimType Wymagania>**](claimtyperequirements-element.md)</span><span class="sxs-lookup"><span data-stu-id="08291-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)</span></span>\
<span data-ttu-id="08291-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dodaj>**</span><span class="sxs-lookup"><span data-stu-id="08291-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08291-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="08291-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08291-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="08291-115">Attributes and Elements</span></span>  
 <span data-ttu-id="08291-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="08291-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08291-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="08291-117">Attributes</span></span>  
  
|<span data-ttu-id="08291-118">Atrybut</span><span class="sxs-lookup"><span data-stu-id="08291-118">Attribute</span></span>|<span data-ttu-id="08291-119">Opis</span><span class="sxs-lookup"><span data-stu-id="08291-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="08291-120">Claimtype</span><span class="sxs-lookup"><span data-stu-id="08291-120">claimType</span></span>|<span data-ttu-id="08291-121">Identyfikator URI, który definiuje typ oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="08291-121">A URI that defines the type of a claim.</span></span> <span data-ttu-id="08291-122">Na przykład, aby kupić produkt w witrynie sieci Web, użytkownik musi przedstawić prawidłową kartę kredytową z wystarczającym limitem kredytowym.</span><span class="sxs-lookup"><span data-stu-id="08291-122">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="08291-123">Typ oświadczenia będzie identyfikatorem URI karty kredytowej.</span><span class="sxs-lookup"><span data-stu-id="08291-123">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="08291-124">isOprocjonalny</span><span class="sxs-lookup"><span data-stu-id="08291-124">isOptional</span></span>|<span data-ttu-id="08291-125">Wartość logiczna, która określa, czy jest to dla opcjonalnego oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="08291-125">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="08291-126">Ustaw ten atrybut, `false` jeśli jest to wymagane oświadczenie.</span><span class="sxs-lookup"><span data-stu-id="08291-126">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="08291-127">Tego atrybutu można użyć, gdy usługa prosi o pewne informacje, ale nie wymaga go.</span><span class="sxs-lookup"><span data-stu-id="08291-127">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="08291-128">Jeśli na przykład użytkownik wymaga wprowadzenia imienia, nazwiska i adresu, ale zdecyduj, że numer telefonu jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="08291-128">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08291-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="08291-129">Child Elements</span></span>  
 <span data-ttu-id="08291-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="08291-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08291-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="08291-131">Parent Elements</span></span>  
  
|<span data-ttu-id="08291-132">Element</span><span class="sxs-lookup"><span data-stu-id="08291-132">Element</span></span>|<span data-ttu-id="08291-133">Opis</span><span class="sxs-lookup"><span data-stu-id="08291-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08291-134">\<claimType Wymagania></span><span class="sxs-lookup"><span data-stu-id="08291-134">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="08291-135">Określa kolekcję wymaganych typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="08291-135">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="08291-136">W scenariuszu federacyjnego usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="08291-136">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="08291-137">Na przykład poświadczenia przychodzące muszą posiadać określony zestaw typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="08291-137">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="08291-138">Każdy element w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń oczekuje się, że pojawią się w poświadczeniu federacyjne.</span><span class="sxs-lookup"><span data-stu-id="08291-138">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08291-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="08291-139">Remarks</span></span>  
 <span data-ttu-id="08291-140">W scenariuszu federacyjnego usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="08291-140">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="08291-141">Na przykład poświadczenia przychodzące muszą posiadać określony zestaw typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="08291-141">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="08291-142">To wymaganie przejawia się w zasadach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="08291-142">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="08291-143">Gdy klient żąda poświadczeń z usługi federacyjnej (na przykład CardSpace), umieszcza wymagania w żądaniu tokenu (RequestSecurityToken), dzięki czemu usługa federacyjne może wystawiać poświadczenia, które spełniają odpowiednio wymagania.</span><span class="sxs-lookup"><span data-stu-id="08291-143">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08291-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="08291-144">Example</span></span>  
 <span data-ttu-id="08291-145">Następująca konfiguracja dodaje dwa wymagania typu oświadczenia do powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="08291-145">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="myFederatedBinding">
      <security mode="Message">
        <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">
          <claimTypeRequirements>
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress" />
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"
                 optional="true" />
          </claimTypeRequirements>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>
```  
  
## <a name="see-also"></a><span data-ttu-id="08291-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08291-146">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="08291-147">\<claimType Wymagania></span><span class="sxs-lookup"><span data-stu-id="08291-147">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)
- [<span data-ttu-id="08291-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="08291-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="08291-149">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="08291-149">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="08291-150">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="08291-150">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="08291-151">\<>niestandardowe</span><span class="sxs-lookup"><span data-stu-id="08291-151">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="08291-152">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="08291-152">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="08291-153">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="08291-153">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
