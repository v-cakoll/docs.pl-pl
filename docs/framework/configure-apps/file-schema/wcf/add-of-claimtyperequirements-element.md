---
title: <add> z <claimTypeRequirements> — element
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 47eb9f95fd024b7df24a16781b3d89fe6deb0b8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701154"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="727b4-102">\<Dodaj > z \<claimTypeRequirements > element</span><span class="sxs-lookup"><span data-stu-id="727b4-102">\<add> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="727b4-103">Określa typy wymaganych i opcjonalnych oświadczeń, oczekiwano w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="727b4-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="727b4-104">Na przykład usługi stanu wymagania dotyczące poświadczeń przychodzących, które muszą posiadać określone typy oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="727b4-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="727b4-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="727b4-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="727b4-106">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="727b4-106">\<bindings></span></span>  
<span data-ttu-id="727b4-107">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="727b4-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="727b4-108">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="727b4-108">\<binding></span></span>  
<span data-ttu-id="727b4-109">\<security></span><span class="sxs-lookup"><span data-stu-id="727b4-109">\<security></span></span>  
<span data-ttu-id="727b4-110">\<message></span><span class="sxs-lookup"><span data-stu-id="727b4-110">\<message></span></span>  
<span data-ttu-id="727b4-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="727b4-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="727b4-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="727b4-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="727b4-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="727b4-113">Attributes and Elements</span></span>  
 <span data-ttu-id="727b4-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="727b4-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="727b4-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="727b4-115">Attributes</span></span>  
  
|<span data-ttu-id="727b4-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="727b4-116">Attribute</span></span>|<span data-ttu-id="727b4-117">Opis</span><span class="sxs-lookup"><span data-stu-id="727b4-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="727b4-118">Typ oświadczenia</span><span class="sxs-lookup"><span data-stu-id="727b4-118">claimType</span></span>|<span data-ttu-id="727b4-119">Identyfikator URI definiujący typ oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="727b4-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="727b4-120">Na przykład aby kupić produkt z witryny sieci Web, użytkownik musi przedstawić ważnej karty kredytowej z wystarczającą limit środków.</span><span class="sxs-lookup"><span data-stu-id="727b4-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="727b4-121">Typ oświadczenia będzie karty kredytowej identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="727b4-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="727b4-122">isOptional</span><span class="sxs-lookup"><span data-stu-id="727b4-122">isOptional</span></span>|<span data-ttu-id="727b4-123">Wartość logiczna określająca, czy jest to dla opcjonalnego roszczenia.</span><span class="sxs-lookup"><span data-stu-id="727b4-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="727b4-124">Ustaw ten atrybut na `false` Jeśli jest to wymagane oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="727b4-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="727b4-125">Można użyć tego atrybutu, gdy usługa poprosi o podanie pewnych informacji, ale nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="727b4-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="727b4-126">Na przykład jeśli możesz wymagać od użytkownika, wprowadź swoje imię, nazwisko i adres, ale zdecydować, że numer telefonu jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="727b4-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="727b4-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="727b4-127">Child Elements</span></span>  
 <span data-ttu-id="727b4-128">Brak.</span><span class="sxs-lookup"><span data-stu-id="727b4-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="727b4-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="727b4-129">Parent Elements</span></span>  
  
|<span data-ttu-id="727b4-130">Element</span><span class="sxs-lookup"><span data-stu-id="727b4-130">Element</span></span>|<span data-ttu-id="727b4-131">Opis</span><span class="sxs-lookup"><span data-stu-id="727b4-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="727b4-132">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="727b4-132">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="727b4-133">Określa kolekcję wymaganych typów oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="727b4-133">Specifies a collection of required claim types.</span></span> <span data-ttu-id="727b4-134">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="727b4-134">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="727b4-135">W federacyjnym scenariuszu usługi stanu wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="727b4-135">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="727b4-136">Na przykład poświadczenia przychodzących musi mieć określone typy oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="727b4-136">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="727b4-137">Każdy element w tej kolekcji Określa typy wymaganych i opcjonalnych oświadczeń, oczekiwano w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="727b4-137">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="727b4-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="727b4-138">Remarks</span></span>  
 <span data-ttu-id="727b4-139">W federacyjnym scenariuszu usługi stanu wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="727b4-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="727b4-140">Na przykład poświadczenia przychodzących musi mieć określone typy oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="727b4-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="727b4-141">To wymaganie jest manifestowany w zasadach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="727b4-141">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="727b4-142">Jeśli poświadczenia żądania klienta z usługi federacyjnej (na przykład CardSpace), umieszcza je wymagań do żądania tokenu (elemencie RequestSecurityToken) tak, aby usługi federacyjnej może wystawiać poświadczenia, które spełniają wymogi odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="727b4-142">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="727b4-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="727b4-143">Example</span></span>  
 <span data-ttu-id="727b4-144">Następująca konfiguracja dodaje dwa wymagania dotyczące typu oświadczenia do powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="727b4-144">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="727b4-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="727b4-145">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
