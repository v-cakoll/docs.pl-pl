---
title: '&lt;add&gt; w &lt;claimTypeRequirements&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cc644648ad244eb642f96fdc93213fbd38152f48
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="11364-102">&lt;add&gt; w &lt;claimTypeRequirements&gt;, element</span><span class="sxs-lookup"><span data-stu-id="11364-102">&lt;add&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="11364-103">Określa typy wymaganych i opcjonalnych oświadczeń, które mogą występować w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="11364-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="11364-104">Na przykład usługi stanu wymagania dotyczące poświadczeń przychodzących, które muszą posiadać określone typy oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="11364-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="11364-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="11364-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="11364-106">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="11364-106">\<bindings></span></span>  
<span data-ttu-id="11364-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="11364-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="11364-108">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="11364-108">\<binding></span></span>  
<span data-ttu-id="11364-109">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="11364-109">\<security></span></span>  
<span data-ttu-id="11364-110">\<komunikat ></span><span class="sxs-lookup"><span data-stu-id="11364-110">\<message></span></span>  
<span data-ttu-id="11364-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="11364-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11364-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="11364-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <add claimType="URI"  
        isOptional="Boolean" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11364-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="11364-113">Attributes and Elements</span></span>  
 <span data-ttu-id="11364-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="11364-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11364-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="11364-115">Attributes</span></span>  
  
|<span data-ttu-id="11364-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="11364-116">Attribute</span></span>|<span data-ttu-id="11364-117">Opis</span><span class="sxs-lookup"><span data-stu-id="11364-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="11364-118">Typ oświadczenia</span><span class="sxs-lookup"><span data-stu-id="11364-118">claimType</span></span>|<span data-ttu-id="11364-119">Identyfikator URI definiujący typ oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="11364-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="11364-120">Na przykład aby kupić produktu w witrynie sieci Web, użytkownik musi przedstawić ważnej karty kredytowej z limitem kredytu wystarczające.</span><span class="sxs-lookup"><span data-stu-id="11364-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="11364-121">Typ oświadczenia będą karty kredytowej identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="11364-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="11364-122">isOptional</span><span class="sxs-lookup"><span data-stu-id="11364-122">isOptional</span></span>|<span data-ttu-id="11364-123">Wartość logiczna określająca, czy jest to dla opcjonalnego roszczenia.</span><span class="sxs-lookup"><span data-stu-id="11364-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="11364-124">Ten atrybut na `false` Jeśli jest to wymagane oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="11364-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="11364-125">Można użyć tego atrybutu, gdy usługa wprowadza pewne informacje, ale nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="11364-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="11364-126">Na przykład jeśli wymagają od użytkownika wprowadzenia jego imię, nazwisko i adres, ale zdecydować, czy numer telefonu jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="11364-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11364-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="11364-127">Child Elements</span></span>  
 <span data-ttu-id="11364-128">Brak.</span><span class="sxs-lookup"><span data-stu-id="11364-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="11364-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="11364-129">Parent Elements</span></span>  
  
|<span data-ttu-id="11364-130">Element</span><span class="sxs-lookup"><span data-stu-id="11364-130">Element</span></span>|<span data-ttu-id="11364-131">Opis</span><span class="sxs-lookup"><span data-stu-id="11364-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11364-132">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="11364-132">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="11364-133">Określa kolekcję wymaganych typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="11364-133">Specifies a collection of required claim types.</span></span> <span data-ttu-id="11364-134">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="11364-134">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="11364-135">W federacyjnym scenariuszu usług stanu wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="11364-135">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="11364-136">Na przykład poświadczenia przychodzące musi mieć określone typy oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="11364-136">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="11364-137">Każdy element w tej kolekcji Określa typy wymaganych i opcjonalnych oświadczeń, które mogą występować w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="11364-137">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11364-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11364-138">Remarks</span></span>  
 <span data-ttu-id="11364-139">W federacyjnym scenariuszu usług stanu wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="11364-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="11364-140">Na przykład poświadczenia przychodzące musi mieć określone typy oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="11364-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="11364-141">To wymaganie jest dyskowe widoczne w zasadach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="11364-141">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="11364-142">Gdy klient żądania poświadczeń z usługi federacyjnej (na przykład CardSpace), umieszcza wymagań do żądania tokenu (RequestSecurityToken) tak, aby usługi federacyjnej można wydać poświadczenia, które spełniają wymagania odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="11364-142">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11364-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="11364-143">Example</span></span>  
 <span data-ttu-id="11364-144">Następująca konfiguracja dodaje dwa wymagania typu oświadczenia do powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="11364-144">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="11364-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11364-145">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
