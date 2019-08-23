---
title: <add><claimTypeRequirements> elementu
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 249227c20dd1610cba088017ae39e84d6cb683d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920208"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="192e7-102">\<Dodaj > \<elementu claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="192e7-102">\<add> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="192e7-103">Określa typy wymaganych i opcjonalnych oświadczeń, które powinny pojawiać się w poświadczeniu Federacji.</span><span class="sxs-lookup"><span data-stu-id="192e7-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="192e7-104">Na przykład usługi określają wymagania dotyczące poświadczeń przychodzących, które muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="192e7-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="192e7-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="192e7-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="192e7-106">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="192e7-106">\<bindings></span></span>  
<span data-ttu-id="192e7-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="192e7-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="192e7-108">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="192e7-108">\<binding></span></span>  
<span data-ttu-id="192e7-109">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="192e7-109">\<security></span></span>  
<span data-ttu-id="192e7-110">\<message></span><span class="sxs-lookup"><span data-stu-id="192e7-110">\<message></span></span>  
<span data-ttu-id="192e7-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="192e7-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="192e7-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="192e7-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="192e7-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="192e7-113">Attributes and Elements</span></span>  
 <span data-ttu-id="192e7-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="192e7-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="192e7-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="192e7-115">Attributes</span></span>  
  
|<span data-ttu-id="192e7-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="192e7-116">Attribute</span></span>|<span data-ttu-id="192e7-117">Opis</span><span class="sxs-lookup"><span data-stu-id="192e7-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="192e7-118">Claim</span><span class="sxs-lookup"><span data-stu-id="192e7-118">claimType</span></span>|<span data-ttu-id="192e7-119">Identyfikator URI, który definiuje typ żądania.</span><span class="sxs-lookup"><span data-stu-id="192e7-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="192e7-120">Na przykład aby zakupić produkt w witrynie sieci Web, użytkownik musi przedstawić ważną kartę kredytową z wystarczającym limitem kredytowym.</span><span class="sxs-lookup"><span data-stu-id="192e7-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="192e7-121">Typ zgłoszenia to identyfikator URI karty kredytowej.</span><span class="sxs-lookup"><span data-stu-id="192e7-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="192e7-122">isoption</span><span class="sxs-lookup"><span data-stu-id="192e7-122">isOptional</span></span>|<span data-ttu-id="192e7-123">Wartość logiczna określająca, czy jest to dla opcjonalnego żądania.</span><span class="sxs-lookup"><span data-stu-id="192e7-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="192e7-124">Ustaw ten atrybut na `false` , jeśli jest to wymagane żądanie.</span><span class="sxs-lookup"><span data-stu-id="192e7-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="192e7-125">Tego atrybutu można użyć, gdy usługa żąda pewnych informacji, ale nie wymaga tego.</span><span class="sxs-lookup"><span data-stu-id="192e7-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="192e7-126">Na przykład, jeśli użytkownik musi wprowadzić imię i nazwisko, nazwisko i adres, ale określić, że numer telefonu jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="192e7-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="192e7-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="192e7-127">Child Elements</span></span>  
 <span data-ttu-id="192e7-128">Brak.</span><span class="sxs-lookup"><span data-stu-id="192e7-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="192e7-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="192e7-129">Parent Elements</span></span>  
  
|<span data-ttu-id="192e7-130">Element</span><span class="sxs-lookup"><span data-stu-id="192e7-130">Element</span></span>|<span data-ttu-id="192e7-131">Opis</span><span class="sxs-lookup"><span data-stu-id="192e7-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="192e7-132">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="192e7-132">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="192e7-133">Określa kolekcję wymaganych typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="192e7-133">Specifies a collection of required claim types.</span></span> <span data-ttu-id="192e7-134">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="192e7-134">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="192e7-135">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="192e7-135">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="192e7-136">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="192e7-136">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="192e7-137">Każdy element w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń, które powinny być wyświetlane w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="192e7-137">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="192e7-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="192e7-138">Remarks</span></span>  
 <span data-ttu-id="192e7-139">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="192e7-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="192e7-140">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="192e7-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="192e7-141">Ten wymóg jest zamieszczony w zasadach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="192e7-141">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="192e7-142">Gdy klient zażąda poświadczeń z usługi federacyjnej (na przykład CardSpace), umieszcza wymagania w żądaniu tokenu (RequestSecurityToken), aby usługa federacyjna mogła wystawić poświadczenia spełniające odpowiednie wymagania.</span><span class="sxs-lookup"><span data-stu-id="192e7-142">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="192e7-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="192e7-143">Example</span></span>  
 <span data-ttu-id="192e7-144">Następująca konfiguracja dodaje dwa wymagania dotyczące typów roszczeń do powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="192e7-144">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="192e7-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="192e7-145">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
