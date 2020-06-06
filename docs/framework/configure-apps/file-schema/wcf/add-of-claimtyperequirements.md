---
title: <add> dla <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 6ba935f7f6dae0e4d9e6581f53a50c684efcbed3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153090"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="d74b6-102">\<add> dla \<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="d74b6-102">\<add> of \<claimTypeRequirements></span></span>
<span data-ttu-id="d74b6-103">Określa typy wymaganych i opcjonalnych oświadczeń, które powinny pojawiać się w poświadczeniu Federacji.</span><span class="sxs-lookup"><span data-stu-id="d74b6-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="d74b6-104">Na przykład usługi określają wymagania dotyczące poświadczeń przychodzących, które muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="d74b6-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="d74b6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d74b6-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d74b6-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d74b6-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d74b6-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d74b6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d74b6-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d74b6-108">Attributes</span></span>  
  
|<span data-ttu-id="d74b6-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d74b6-109">Attribute</span></span>|<span data-ttu-id="d74b6-110">Opis</span><span class="sxs-lookup"><span data-stu-id="d74b6-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d74b6-111">Claim</span><span class="sxs-lookup"><span data-stu-id="d74b6-111">claimType</span></span>|<span data-ttu-id="d74b6-112">Identyfikator URI, który definiuje typ żądania.</span><span class="sxs-lookup"><span data-stu-id="d74b6-112">A URI that defines the type of a claim.</span></span> <span data-ttu-id="d74b6-113">Na przykład aby zakupić produkt w witrynie sieci Web, użytkownik musi przedstawić ważną kartę kredytową z wystarczającym limitem kredytowym.</span><span class="sxs-lookup"><span data-stu-id="d74b6-113">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="d74b6-114">Typ zgłoszenia to identyfikator URI karty kredytowej.</span><span class="sxs-lookup"><span data-stu-id="d74b6-114">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="d74b6-115">isoption</span><span class="sxs-lookup"><span data-stu-id="d74b6-115">isOptional</span></span>|<span data-ttu-id="d74b6-116">Wartość logiczna określająca, czy jest to dla opcjonalnego żądania.</span><span class="sxs-lookup"><span data-stu-id="d74b6-116">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="d74b6-117">Ustaw ten atrybut na, `false` Jeśli jest to wymagane żądanie.</span><span class="sxs-lookup"><span data-stu-id="d74b6-117">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="d74b6-118">Tego atrybutu można użyć, gdy usługa żąda pewnych informacji, ale nie wymaga tego.</span><span class="sxs-lookup"><span data-stu-id="d74b6-118">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="d74b6-119">Na przykład, jeśli użytkownik musi wprowadzić imię, nazwisko i adres, ale zdecydować, że numer telefonu jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d74b6-119">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d74b6-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d74b6-120">Child Elements</span></span>  
 <span data-ttu-id="d74b6-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="d74b6-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d74b6-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d74b6-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d74b6-123">Element</span><span class="sxs-lookup"><span data-stu-id="d74b6-123">Element</span></span>|<span data-ttu-id="d74b6-124">Opis</span><span class="sxs-lookup"><span data-stu-id="d74b6-124">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="d74b6-125">Określa kolekcję wymaganych typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="d74b6-125">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="d74b6-126">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="d74b6-126">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="d74b6-127">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="d74b6-127">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="d74b6-128">Każdy element w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń, które powinny być wyświetlane w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="d74b6-128">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d74b6-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d74b6-129">Remarks</span></span>  
 <span data-ttu-id="d74b6-130">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="d74b6-130">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="d74b6-131">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="d74b6-131">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="d74b6-132">Ten wymóg jest zamieszczony w zasadach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d74b6-132">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="d74b6-133">Gdy klient zażąda poświadczeń z usługi federacyjnej (na przykład CardSpace), umieszcza wymagania w żądaniu tokenu (RequestSecurityToken), aby usługa federacyjna mogła wystawić poświadczenia spełniające odpowiednie wymagania.</span><span class="sxs-lookup"><span data-stu-id="d74b6-133">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d74b6-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="d74b6-134">Example</span></span>  
 <span data-ttu-id="d74b6-135">Następująca konfiguracja dodaje dwa wymagania dotyczące typów roszczeń do powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d74b6-135">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d74b6-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d74b6-136">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<claimTypeRequirements>](claimtyperequirements-element.md)
- [<span data-ttu-id="d74b6-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="d74b6-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d74b6-138">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="d74b6-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d74b6-139">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="d74b6-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="d74b6-140">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d74b6-140">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="d74b6-141">Zabezpieczenia wiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="d74b6-141">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
