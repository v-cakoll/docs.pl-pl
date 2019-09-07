---
title: <add><claimTypeRequirements> elementu
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 9c56cccd7a6f72a701e4b8652afecc2361e6218a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400687"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="fea3b-102">\<Dodaj > \<elementu claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="fea3b-102">\<add> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="fea3b-103">Określa typy wymaganych i opcjonalnych oświadczeń, które powinny pojawiać się w poświadczeniu Federacji.</span><span class="sxs-lookup"><span data-stu-id="fea3b-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="fea3b-104">Na przykład usługi określają wymagania dotyczące poświadczeń przychodzących, które muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="fea3b-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
<span data-ttu-id="fea3b-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fea3b-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fea3b-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="fea3b-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="fea3b-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="fea3b-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="fea3b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="fea3b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="fea3b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="fea3b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="fea3b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="fea3b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="fea3b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> komunikatu**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="fea3b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="fea3b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequirements >** ](claimtyperequirements-for-message.md)</span><span class="sxs-lookup"><span data-stu-id="fea3b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span></span>\
<span data-ttu-id="fea3b-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="fea3b-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="fea3b-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="fea3b-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fea3b-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fea3b-115">Attributes and Elements</span></span>  
 <span data-ttu-id="fea3b-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fea3b-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fea3b-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fea3b-117">Attributes</span></span>  
  
|<span data-ttu-id="fea3b-118">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fea3b-118">Attribute</span></span>|<span data-ttu-id="fea3b-119">Opis</span><span class="sxs-lookup"><span data-stu-id="fea3b-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fea3b-120">Claim</span><span class="sxs-lookup"><span data-stu-id="fea3b-120">claimType</span></span>|<span data-ttu-id="fea3b-121">Identyfikator URI, który definiuje typ żądania.</span><span class="sxs-lookup"><span data-stu-id="fea3b-121">A URI that defines the type of a claim.</span></span> <span data-ttu-id="fea3b-122">Na przykład aby zakupić produkt w witrynie sieci Web, użytkownik musi przedstawić ważną kartę kredytową z wystarczającym limitem kredytowym.</span><span class="sxs-lookup"><span data-stu-id="fea3b-122">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="fea3b-123">Typ zgłoszenia to identyfikator URI karty kredytowej.</span><span class="sxs-lookup"><span data-stu-id="fea3b-123">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="fea3b-124">isoption</span><span class="sxs-lookup"><span data-stu-id="fea3b-124">isOptional</span></span>|<span data-ttu-id="fea3b-125">Wartość logiczna określająca, czy jest to dla opcjonalnego żądania.</span><span class="sxs-lookup"><span data-stu-id="fea3b-125">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="fea3b-126">Ustaw ten atrybut na `false` , jeśli jest to wymagane żądanie.</span><span class="sxs-lookup"><span data-stu-id="fea3b-126">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="fea3b-127">Tego atrybutu można użyć, gdy usługa żąda pewnych informacji, ale nie wymaga tego.</span><span class="sxs-lookup"><span data-stu-id="fea3b-127">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="fea3b-128">Na przykład, jeśli użytkownik musi wprowadzić imię i nazwisko, nazwisko i adres, ale określić, że numer telefonu jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fea3b-128">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fea3b-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fea3b-129">Child Elements</span></span>  
 <span data-ttu-id="fea3b-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="fea3b-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fea3b-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fea3b-131">Parent Elements</span></span>  
  
|<span data-ttu-id="fea3b-132">Element</span><span class="sxs-lookup"><span data-stu-id="fea3b-132">Element</span></span>|<span data-ttu-id="fea3b-133">Opis</span><span class="sxs-lookup"><span data-stu-id="fea3b-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fea3b-134">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="fea3b-134">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="fea3b-135">Określa kolekcję wymaganych typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="fea3b-135">Specifies a collection of required claim types.</span></span> <span data-ttu-id="fea3b-136">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="fea3b-136">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="fea3b-137">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="fea3b-137">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="fea3b-138">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="fea3b-138">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="fea3b-139">Każdy element w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń, które powinny być wyświetlane w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="fea3b-139">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fea3b-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fea3b-140">Remarks</span></span>  
 <span data-ttu-id="fea3b-141">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="fea3b-141">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="fea3b-142">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="fea3b-142">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="fea3b-143">Ten wymóg jest zamieszczony w zasadach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="fea3b-143">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="fea3b-144">Gdy klient zażąda poświadczeń z usługi federacyjnej (na przykład CardSpace), umieszcza wymagania w żądaniu tokenu (RequestSecurityToken), aby usługa federacyjna mogła wystawić poświadczenia spełniające odpowiednie wymagania.</span><span class="sxs-lookup"><span data-stu-id="fea3b-144">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fea3b-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="fea3b-145">Example</span></span>  
 <span data-ttu-id="fea3b-146">Następująca konfiguracja dodaje dwa wymagania dotyczące typów roszczeń do powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="fea3b-146">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fea3b-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fea3b-147">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
