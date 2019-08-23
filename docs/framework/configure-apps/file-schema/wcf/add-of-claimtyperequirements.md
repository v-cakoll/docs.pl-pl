---
title: <add> dla <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 7e7f0eac41e69e959aa6c4f8f3cfb488d4ea2917
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926798"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="295be-102">\<Dodawanie > \<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="295be-102">\<add> of \<claimTypeRequirements></span></span>
<span data-ttu-id="295be-103">Określa typy wymaganych i opcjonalnych oświadczeń, które powinny pojawiać się w poświadczeniu Federacji.</span><span class="sxs-lookup"><span data-stu-id="295be-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="295be-104">Na przykład usługi określają wymagania dotyczące poświadczeń przychodzących, które muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="295be-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="295be-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="295be-105">\<system.serviceModel></span></span>  
<span data-ttu-id="295be-106">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="295be-106">\<bindings></span></span>  
<span data-ttu-id="295be-107">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="295be-107">\<customBinding></span></span>  
<span data-ttu-id="295be-108">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="295be-108">\<binding></span></span>  
<span data-ttu-id="295be-109">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="295be-109">\<security></span></span>  
<span data-ttu-id="295be-110">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="295be-110">\<issuedTokenParameters></span></span>  
<span data-ttu-id="295be-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="295be-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="295be-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="295be-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="295be-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="295be-113">Attributes and Elements</span></span>  
 <span data-ttu-id="295be-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="295be-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="295be-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="295be-115">Attributes</span></span>  
  
|<span data-ttu-id="295be-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="295be-116">Attribute</span></span>|<span data-ttu-id="295be-117">Opis</span><span class="sxs-lookup"><span data-stu-id="295be-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="295be-118">Claim</span><span class="sxs-lookup"><span data-stu-id="295be-118">claimType</span></span>|<span data-ttu-id="295be-119">Identyfikator URI, który definiuje typ żądania.</span><span class="sxs-lookup"><span data-stu-id="295be-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="295be-120">Na przykład aby zakupić produkt w witrynie sieci Web, użytkownik musi przedstawić ważną kartę kredytową z wystarczającym limitem kredytowym.</span><span class="sxs-lookup"><span data-stu-id="295be-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="295be-121">Typ zgłoszenia to identyfikator URI karty kredytowej.</span><span class="sxs-lookup"><span data-stu-id="295be-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="295be-122">isoption</span><span class="sxs-lookup"><span data-stu-id="295be-122">isOptional</span></span>|<span data-ttu-id="295be-123">Wartość logiczna określająca, czy jest to dla opcjonalnego żądania.</span><span class="sxs-lookup"><span data-stu-id="295be-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="295be-124">Ustaw ten atrybut na `false` , jeśli jest to wymagane żądanie.</span><span class="sxs-lookup"><span data-stu-id="295be-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="295be-125">Tego atrybutu można użyć, gdy usługa żąda pewnych informacji, ale nie wymaga tego.</span><span class="sxs-lookup"><span data-stu-id="295be-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="295be-126">Na przykład, jeśli użytkownik musi wprowadzić imię i nazwisko, nazwisko i adres, ale określić, że numer telefonu jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="295be-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="295be-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="295be-127">Child Elements</span></span>  
 <span data-ttu-id="295be-128">Brak.</span><span class="sxs-lookup"><span data-stu-id="295be-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="295be-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="295be-129">Parent Elements</span></span>  
  
|<span data-ttu-id="295be-130">Element</span><span class="sxs-lookup"><span data-stu-id="295be-130">Element</span></span>|<span data-ttu-id="295be-131">Opis</span><span class="sxs-lookup"><span data-stu-id="295be-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="295be-132">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="295be-132">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="295be-133">Określa kolekcję wymaganych typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="295be-133">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="295be-134">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="295be-134">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="295be-135">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="295be-135">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="295be-136">Każdy element w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń, które powinny być wyświetlane w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="295be-136">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="295be-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="295be-137">Remarks</span></span>  
 <span data-ttu-id="295be-138">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="295be-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="295be-139">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="295be-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="295be-140">Ten wymóg jest zamieszczony w zasadach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="295be-140">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="295be-141">Gdy klient zażąda poświadczeń z usługi federacyjnej (na przykład CardSpace), umieszcza wymagania w żądaniu tokenu (RequestSecurityToken), aby usługa federacyjna mogła wystawić poświadczenia spełniające odpowiednie wymagania.</span><span class="sxs-lookup"><span data-stu-id="295be-141">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="295be-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="295be-142">Example</span></span>  
 <span data-ttu-id="295be-143">Następująca konfiguracja dodaje dwa wymagania dotyczące typów roszczeń do powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="295be-143">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="295be-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="295be-144">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="295be-145">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="295be-145">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)
- [<span data-ttu-id="295be-146">Powiązania</span><span class="sxs-lookup"><span data-stu-id="295be-146">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="295be-147">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="295be-147">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="295be-148">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="295be-148">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="295be-149">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="295be-149">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="295be-150">Instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="295be-150">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="295be-151">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="295be-151">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
