---
title: <add><claimTypeRequirements>elementu
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: f6948052c62684faa734b592f5bdfc2e7827a07a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153103"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="b95d9-102">\<add>\<claimTypeRequirements>elementu</span><span class="sxs-lookup"><span data-stu-id="b95d9-102">\<add> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="b95d9-103">Określa typy wymaganych i opcjonalnych oświadczeń, które powinny pojawiać się w poświadczeniu Federacji.</span><span class="sxs-lookup"><span data-stu-id="b95d9-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="b95d9-104">Na przykład usługi określają wymagania dotyczące poświadczeń przychodzących, które muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="b95d9-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**
  
## <a name="syntax"></a><span data-ttu-id="b95d9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b95d9-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b95d9-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b95d9-106">Attributes and Elements</span></span>  
 <span data-ttu-id="b95d9-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b95d9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b95d9-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b95d9-108">Attributes</span></span>  
  
|<span data-ttu-id="b95d9-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b95d9-109">Attribute</span></span>|<span data-ttu-id="b95d9-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b95d9-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b95d9-111">Claim</span><span class="sxs-lookup"><span data-stu-id="b95d9-111">claimType</span></span>|<span data-ttu-id="b95d9-112">Identyfikator URI, który definiuje typ żądania.</span><span class="sxs-lookup"><span data-stu-id="b95d9-112">A URI that defines the type of a claim.</span></span> <span data-ttu-id="b95d9-113">Na przykład aby zakupić produkt w witrynie sieci Web, użytkownik musi przedstawić ważną kartę kredytową z wystarczającym limitem kredytowym.</span><span class="sxs-lookup"><span data-stu-id="b95d9-113">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="b95d9-114">Typ zgłoszenia to identyfikator URI karty kredytowej.</span><span class="sxs-lookup"><span data-stu-id="b95d9-114">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="b95d9-115">isoption</span><span class="sxs-lookup"><span data-stu-id="b95d9-115">isOptional</span></span>|<span data-ttu-id="b95d9-116">Wartość logiczna określająca, czy jest to dla opcjonalnego żądania.</span><span class="sxs-lookup"><span data-stu-id="b95d9-116">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="b95d9-117">Ustaw ten atrybut na, `false` Jeśli jest to wymagane żądanie.</span><span class="sxs-lookup"><span data-stu-id="b95d9-117">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="b95d9-118">Tego atrybutu można użyć, gdy usługa żąda pewnych informacji, ale nie wymaga tego.</span><span class="sxs-lookup"><span data-stu-id="b95d9-118">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="b95d9-119">Na przykład, jeśli użytkownik musi wprowadzić imię, nazwisko i adres, ale zdecydować, że numer telefonu jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b95d9-119">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b95d9-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b95d9-120">Child Elements</span></span>  
 <span data-ttu-id="b95d9-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="b95d9-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b95d9-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b95d9-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b95d9-123">Element</span><span class="sxs-lookup"><span data-stu-id="b95d9-123">Element</span></span>|<span data-ttu-id="b95d9-124">Opis</span><span class="sxs-lookup"><span data-stu-id="b95d9-124">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="b95d9-125">Określa kolekcję wymaganych typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="b95d9-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="b95d9-126">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="b95d9-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="b95d9-127">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="b95d9-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="b95d9-128">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="b95d9-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="b95d9-129">Każdy element w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń, które powinny być wyświetlane w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="b95d9-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b95d9-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b95d9-130">Remarks</span></span>  
 <span data-ttu-id="b95d9-131">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="b95d9-131">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="b95d9-132">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="b95d9-132">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="b95d9-133">Ten wymóg jest zamieszczony w zasadach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="b95d9-133">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="b95d9-134">Gdy klient zażąda poświadczeń z usługi federacyjnej (na przykład CardSpace), umieszcza wymagania w żądaniu tokenu (RequestSecurityToken), aby usługa federacyjna mogła wystawić poświadczenia spełniające odpowiednie wymagania.</span><span class="sxs-lookup"><span data-stu-id="b95d9-134">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b95d9-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="b95d9-135">Example</span></span>  
 <span data-ttu-id="b95d9-136">Następująca konfiguracja dodaje dwa wymagania dotyczące typów roszczeń do powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="b95d9-136">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b95d9-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b95d9-137">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
