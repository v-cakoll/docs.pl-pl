---
title: '&lt;add&gt; w &lt;claimTypeRequirements&gt;'
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: b4f9275fdc36ea3c7ba79c6609f039c3b1f4c3ed
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltclaimtyperequirementsgt"></a><span data-ttu-id="1e660-102">&lt;add&gt; w &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="1e660-102">&lt;add&gt; of &lt;claimTypeRequirements&gt;</span></span>
<span data-ttu-id="1e660-103">Określa typy wymaganych i opcjonalnych oświadczeń, które mogą występować w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="1e660-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="1e660-104">Na przykład usługi stanu wymagania dotyczące poświadczeń przychodzących, które muszą posiadać określone typy oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="1e660-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="1e660-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1e660-105">\<system.serviceModel></span></span>  
<span data-ttu-id="1e660-106">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="1e660-106">\<bindings></span></span>  
<span data-ttu-id="1e660-107">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1e660-107">\<customBinding></span></span>  
<span data-ttu-id="1e660-108">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="1e660-108">\<binding></span></span>  
<span data-ttu-id="1e660-109">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="1e660-109">\<security></span></span>  
<span data-ttu-id="1e660-110">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="1e660-110">\<issuedTokenParameters></span></span>  
<span data-ttu-id="1e660-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="1e660-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e660-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="1e660-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <add claimType="URI"  
           isOptional="Boolean" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e660-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1e660-113">Attributes and Elements</span></span>  
 <span data-ttu-id="1e660-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1e660-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e660-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1e660-115">Attributes</span></span>  
  
|<span data-ttu-id="1e660-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1e660-116">Attribute</span></span>|<span data-ttu-id="1e660-117">Opis</span><span class="sxs-lookup"><span data-stu-id="1e660-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1e660-118">Typ oświadczenia</span><span class="sxs-lookup"><span data-stu-id="1e660-118">claimType</span></span>|<span data-ttu-id="1e660-119">Identyfikator URI definiujący typ oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="1e660-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="1e660-120">Na przykład aby kupić produktu w witrynie sieci Web, użytkownik musi przedstawić ważnej karty kredytowej z limitem kredytu wystarczające.</span><span class="sxs-lookup"><span data-stu-id="1e660-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="1e660-121">Typ oświadczenia będą karty kredytowej identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="1e660-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="1e660-122">isOptional</span><span class="sxs-lookup"><span data-stu-id="1e660-122">isOptional</span></span>|<span data-ttu-id="1e660-123">Wartość logiczna określająca, czy jest to dla opcjonalnego roszczenia.</span><span class="sxs-lookup"><span data-stu-id="1e660-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="1e660-124">Ten atrybut na `false` Jeśli jest to wymagane oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="1e660-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="1e660-125">Można użyć tego atrybutu, gdy usługa wprowadza pewne informacje, ale nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="1e660-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="1e660-126">Na przykład jeśli wymagają od użytkownika wprowadzenia jego imię, nazwisko i adres, ale zdecydować, czy numer telefonu jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="1e660-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1e660-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1e660-127">Child Elements</span></span>  
 <span data-ttu-id="1e660-128">Brak.</span><span class="sxs-lookup"><span data-stu-id="1e660-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1e660-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1e660-129">Parent Elements</span></span>  
  
|<span data-ttu-id="1e660-130">Element</span><span class="sxs-lookup"><span data-stu-id="1e660-130">Element</span></span>|<span data-ttu-id="1e660-131">Opis</span><span class="sxs-lookup"><span data-stu-id="1e660-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e660-132">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="1e660-132">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="1e660-133">Określa kolekcję wymaganych typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="1e660-133">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="1e660-134">W federacyjnym scenariuszu usług stanu wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="1e660-134">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="1e660-135">Na przykład poświadczenia przychodzące musi mieć określone typy oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="1e660-135">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="1e660-136">Każdy element w tej kolekcji Określa typy wymaganych i opcjonalnych oświadczeń, które mogą występować w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="1e660-136">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e660-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1e660-137">Remarks</span></span>  
 <span data-ttu-id="1e660-138">W federacyjnym scenariuszu usług stanu wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="1e660-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="1e660-139">Na przykład poświadczenia przychodzące musi mieć określone typy oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="1e660-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="1e660-140">To wymaganie jest dyskowe widoczne w zasadach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="1e660-140">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="1e660-141">Gdy klient żądania poświadczeń z usługi federacyjnej (na przykład CardSpace), umieszcza wymagań do żądania tokenu (RequestSecurityToken) tak, aby usługi federacyjnej można wydać poświadczenia, które spełniają wymagania odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="1e660-141">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e660-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="1e660-142">Example</span></span>  
 <span data-ttu-id="1e660-143">Następująca konfiguracja dodaje dwa wymagania typu oświadczenia do powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="1e660-143">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
```xml  
<bindings>  
    <wsFederationHttpBinding>  
      <binding name="myFederatedBinding">  
        <security mode="Message">  
          <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">  
            <claimTypeRequirements>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress"/>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"    
optional="true" />  
            </claims>  
          </message>  
        </security>  
      </binding>  
    </wsFederationHttpBinding>  
</bindings>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1e660-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1e660-144">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="1e660-145">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="1e660-145">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)  
 [<span data-ttu-id="1e660-146">Powiązania</span><span class="sxs-lookup"><span data-stu-id="1e660-146">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="1e660-147">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="1e660-147">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="1e660-148">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="1e660-148">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="1e660-149">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1e660-149">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="1e660-150">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="1e660-150">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="1e660-151">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="1e660-151">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
