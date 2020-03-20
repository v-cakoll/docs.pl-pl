---
title: <add>element <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: f6948052c62684faa734b592f5bdfc2e7827a07a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153103"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="db9b9-102">\<dodawanie> wymagań \<dotyczących typu oświadczeń> element</span><span class="sxs-lookup"><span data-stu-id="db9b9-102">\<add> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="db9b9-103">Określa typy wymaganych i opcjonalnych oświadczeń, które mają pojawić się w poświadczeniu federacyjnem.</span><span class="sxs-lookup"><span data-stu-id="db9b9-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="db9b9-104">Na przykład usługi określają wymagania dotyczące poświadczeń przychodzących, które muszą zawierać określony zestaw typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="db9b9-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
<span data-ttu-id="db9b9-105">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="db9b9-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="db9b9-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="db9b9-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="db9b9-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<wiązania>**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="db9b9-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="db9b9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationhttpbinowanie>**](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="db9b9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="db9b9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wiążące>**</span><span class="sxs-lookup"><span data-stu-id="db9b9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="db9b9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>bezpieczeństwa**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="db9b9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="db9b9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>wiadomości**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="db9b9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="db9b9-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimType Wymagania>**](claimtyperequirements-for-message.md)</span><span class="sxs-lookup"><span data-stu-id="db9b9-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span></span>\
<span data-ttu-id="db9b9-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dodaj>**</span><span class="sxs-lookup"><span data-stu-id="db9b9-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="db9b9-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="db9b9-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db9b9-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="db9b9-115">Attributes and Elements</span></span>  
 <span data-ttu-id="db9b9-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="db9b9-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db9b9-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="db9b9-117">Attributes</span></span>  
  
|<span data-ttu-id="db9b9-118">Atrybut</span><span class="sxs-lookup"><span data-stu-id="db9b9-118">Attribute</span></span>|<span data-ttu-id="db9b9-119">Opis</span><span class="sxs-lookup"><span data-stu-id="db9b9-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db9b9-120">Claimtype</span><span class="sxs-lookup"><span data-stu-id="db9b9-120">claimType</span></span>|<span data-ttu-id="db9b9-121">Identyfikator URI, który definiuje typ oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="db9b9-121">A URI that defines the type of a claim.</span></span> <span data-ttu-id="db9b9-122">Na przykład, aby kupić produkt w witrynie sieci Web, użytkownik musi przedstawić prawidłową kartę kredytową z wystarczającym limitem kredytowym.</span><span class="sxs-lookup"><span data-stu-id="db9b9-122">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="db9b9-123">Typ oświadczenia będzie identyfikatorem URI karty kredytowej.</span><span class="sxs-lookup"><span data-stu-id="db9b9-123">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="db9b9-124">isOprocjonalny</span><span class="sxs-lookup"><span data-stu-id="db9b9-124">isOptional</span></span>|<span data-ttu-id="db9b9-125">Wartość logiczna, która określa, czy jest to dla opcjonalnego oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="db9b9-125">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="db9b9-126">Ustaw ten atrybut, `false` jeśli jest to wymagane oświadczenie.</span><span class="sxs-lookup"><span data-stu-id="db9b9-126">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="db9b9-127">Tego atrybutu można użyć, gdy usługa prosi o pewne informacje, ale nie wymaga go.</span><span class="sxs-lookup"><span data-stu-id="db9b9-127">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="db9b9-128">Jeśli na przykład użytkownik wymaga wprowadzenia imienia, nazwiska i adresu, ale zdecyduj, że numer telefonu jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="db9b9-128">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db9b9-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="db9b9-129">Child Elements</span></span>  
 <span data-ttu-id="db9b9-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="db9b9-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db9b9-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="db9b9-131">Parent Elements</span></span>  
  
|<span data-ttu-id="db9b9-132">Element</span><span class="sxs-lookup"><span data-stu-id="db9b9-132">Element</span></span>|<span data-ttu-id="db9b9-133">Opis</span><span class="sxs-lookup"><span data-stu-id="db9b9-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db9b9-134">\<claimType Wymagania></span><span class="sxs-lookup"><span data-stu-id="db9b9-134">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="db9b9-135">Określa kolekcję wymaganych typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="db9b9-135">Specifies a collection of required claim types.</span></span> <span data-ttu-id="db9b9-136">Każdy element jest <xref:System.ServiceModel.Configuration.ClaimTypeElement>typu .</span><span class="sxs-lookup"><span data-stu-id="db9b9-136">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="db9b9-137">W scenariuszu federacyjnego usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="db9b9-137">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="db9b9-138">Na przykład poświadczenia przychodzące muszą posiadać określony zestaw typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="db9b9-138">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="db9b9-139">Każdy element w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń oczekuje się, że pojawią się w poświadczeniu federacyjne.</span><span class="sxs-lookup"><span data-stu-id="db9b9-139">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db9b9-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="db9b9-140">Remarks</span></span>  
 <span data-ttu-id="db9b9-141">W scenariuszu federacyjnego usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="db9b9-141">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="db9b9-142">Na przykład poświadczenia przychodzące muszą posiadać określony zestaw typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="db9b9-142">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="db9b9-143">To wymaganie przejawia się w zasadach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="db9b9-143">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="db9b9-144">Gdy klient żąda poświadczeń z usługi federacyjnej (na przykład CardSpace), umieszcza wymagania w żądaniu tokenu (RequestSecurityToken), dzięki czemu usługa federacyjne może wystawiać poświadczenia, które spełniają odpowiednio wymagania.</span><span class="sxs-lookup"><span data-stu-id="db9b9-144">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db9b9-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="db9b9-145">Example</span></span>  
 <span data-ttu-id="db9b9-146">Następująca konfiguracja dodaje dwa wymagania typu oświadczenia do powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="db9b9-146">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="db9b9-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db9b9-147">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
