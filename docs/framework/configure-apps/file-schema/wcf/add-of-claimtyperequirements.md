---
title: <add> dla <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 53da9dacbd3277bd8b608296a1515e3da7296f1c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398369"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="bd7d8-102">\<Dodawanie > \<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="bd7d8-102">\<add> of \<claimTypeRequirements></span></span>
<span data-ttu-id="bd7d8-103">Określa typy wymaganych i opcjonalnych oświadczeń, które powinny pojawiać się w poświadczeniu Federacji.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="bd7d8-104">Na przykład usługi określają wymagania dotyczące poświadczeń przychodzących, które muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
<span data-ttu-id="bd7d8-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bd7d8-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bd7d8-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bd7d8-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bd7d8-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="bd7d8-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="bd7d8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="bd7d8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="bd7d8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="bd7d8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="bd7d8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="bd7d8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="bd7d8-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedTokenParameters >** ](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="bd7d8-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="bd7d8-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequirements >** ](claimtyperequirements-element.md)</span><span class="sxs-lookup"><span data-stu-id="bd7d8-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)</span></span>\
<span data-ttu-id="bd7d8-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="bd7d8-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd7d8-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd7d8-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd7d8-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bd7d8-115">Attributes and Elements</span></span>  
 <span data-ttu-id="bd7d8-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd7d8-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bd7d8-117">Attributes</span></span>  
  
|<span data-ttu-id="bd7d8-118">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bd7d8-118">Attribute</span></span>|<span data-ttu-id="bd7d8-119">Opis</span><span class="sxs-lookup"><span data-stu-id="bd7d8-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd7d8-120">Claim</span><span class="sxs-lookup"><span data-stu-id="bd7d8-120">claimType</span></span>|<span data-ttu-id="bd7d8-121">Identyfikator URI, który definiuje typ żądania.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-121">A URI that defines the type of a claim.</span></span> <span data-ttu-id="bd7d8-122">Na przykład aby zakupić produkt w witrynie sieci Web, użytkownik musi przedstawić ważną kartę kredytową z wystarczającym limitem kredytowym.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-122">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="bd7d8-123">Typ zgłoszenia to identyfikator URI karty kredytowej.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-123">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="bd7d8-124">isoption</span><span class="sxs-lookup"><span data-stu-id="bd7d8-124">isOptional</span></span>|<span data-ttu-id="bd7d8-125">Wartość logiczna określająca, czy jest to dla opcjonalnego żądania.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-125">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="bd7d8-126">Ustaw ten atrybut na `false` , jeśli jest to wymagane żądanie.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-126">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="bd7d8-127">Tego atrybutu można użyć, gdy usługa żąda pewnych informacji, ale nie wymaga tego.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-127">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="bd7d8-128">Na przykład, jeśli użytkownik musi wprowadzić imię i nazwisko, nazwisko i adres, ale określić, że numer telefonu jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-128">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd7d8-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bd7d8-129">Child Elements</span></span>  
 <span data-ttu-id="bd7d8-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bd7d8-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bd7d8-131">Parent Elements</span></span>  
  
|<span data-ttu-id="bd7d8-132">Element</span><span class="sxs-lookup"><span data-stu-id="bd7d8-132">Element</span></span>|<span data-ttu-id="bd7d8-133">Opis</span><span class="sxs-lookup"><span data-stu-id="bd7d8-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd7d8-134">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="bd7d8-134">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="bd7d8-135">Określa kolekcję wymaganych typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-135">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="bd7d8-136">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-136">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="bd7d8-137">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-137">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="bd7d8-138">Każdy element w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń, które powinny być wyświetlane w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-138">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd7d8-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd7d8-139">Remarks</span></span>  
 <span data-ttu-id="bd7d8-140">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-140">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="bd7d8-141">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-141">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="bd7d8-142">Ten wymóg jest zamieszczony w zasadach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-142">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="bd7d8-143">Gdy klient zażąda poświadczeń z usługi federacyjnej (na przykład CardSpace), umieszcza wymagania w żądaniu tokenu (RequestSecurityToken), aby usługa federacyjna mogła wystawić poświadczenia spełniające odpowiednie wymagania.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-143">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd7d8-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="bd7d8-144">Example</span></span>  
 <span data-ttu-id="bd7d8-145">Następująca konfiguracja dodaje dwa wymagania dotyczące typów roszczeń do powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="bd7d8-145">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bd7d8-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd7d8-146">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="bd7d8-147">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="bd7d8-147">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)
- [<span data-ttu-id="bd7d8-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="bd7d8-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bd7d8-149">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="bd7d8-149">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="bd7d8-150">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="bd7d8-150">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="bd7d8-151">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="bd7d8-151">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="bd7d8-152">Instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="bd7d8-152">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="bd7d8-153">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="bd7d8-153">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
