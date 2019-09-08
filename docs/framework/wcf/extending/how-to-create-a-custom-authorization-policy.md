---
title: 'Instrukcje: tworzenie niestandardowych zasad autoryzacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: 5d5268cd2171bdccc3885cd599fdc8c277e61aa4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795713"
---
# <a name="how-to-create-a-custom-authorization-policy"></a><span data-ttu-id="0e5db-102">Instrukcje: tworzenie niestandardowych zasad autoryzacji</span><span class="sxs-lookup"><span data-stu-id="0e5db-102">How to: Create a Custom Authorization Policy</span></span>
<span data-ttu-id="0e5db-103">Infrastruktura modelu tożsamości w Windows Communication Foundation (WCF) obsługuje model autoryzacji oparty na żądaniach.</span><span class="sxs-lookup"><span data-stu-id="0e5db-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports a claim-based authorization model.</span></span> <span data-ttu-id="0e5db-104">Oświadczenia są wyodrębniane z tokenów, opcjonalnie przetworzonych przez niestandardowe zasady autoryzacji, a <xref:System.IdentityModel.Policy.AuthorizationContext> następnie umieszczane w usłudze, które następnie można sprawdzić w celu podejmowania decyzji dotyczących autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="0e5db-104">Claims are extracted from tokens, optionally processed by custom authorization policy, and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext> that can then be examined to make authorization decisions.</span></span> <span data-ttu-id="0e5db-105">Zasady niestandardowe mogą służyć do przekształcania oświadczeń z tokenów przychodzących do oświadczeń oczekiwanych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="0e5db-105">A custom policy can be used to transform claims from incoming tokens into claims expected by the application.</span></span> <span data-ttu-id="0e5db-106">W ten sposób warstwa aplikacji może być izolowana od szczegółowych informacji o różnych oświadczeniach, które są obsługiwane przez różne typy tokenów obsługiwanych przez funkcję WCF.</span><span class="sxs-lookup"><span data-stu-id="0e5db-106">In this way, the application layer can be insulated from the details on the differing claims served up by the different token types that WCF supports.</span></span> <span data-ttu-id="0e5db-107">W tym temacie pokazano, jak zaimplementować niestandardowe zasady autoryzacji i jak dodać te zasady do kolekcji zasad używanych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="0e5db-107">This topic shows how to implement a custom authorization policy and how to add that policy to the collection of policies used by a service.</span></span>  
  
### <a name="to-implement-a-custom-authorization-policy"></a><span data-ttu-id="0e5db-108">Aby zaimplementować niestandardowe zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="0e5db-108">To implement a custom authorization policy</span></span>  
  
1. <span data-ttu-id="0e5db-109">Zdefiniuj nową klasę, która pochodzi od <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="0e5db-109">Define a new class that derives from <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="0e5db-110">Zaimplementuj właściwość tylko <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> do odczytu, generując unikatowy ciąg w konstruktorze klasy i zwracając ten ciąg za każdym razem, gdy uzyskuje się dostęp do właściwości.</span><span class="sxs-lookup"><span data-stu-id="0e5db-110">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> property by generating a unique string in the constructor for the class and returning that string whenever the property is accessed.</span></span>  
  
3. <span data-ttu-id="0e5db-111">Zaimplementuj właściwość tylko <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> do odczytu, zwracając element <xref:System.IdentityModel.Claims.ClaimSet> reprezentujący wystawcę zasad.</span><span class="sxs-lookup"><span data-stu-id="0e5db-111">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> property by returning a <xref:System.IdentityModel.Claims.ClaimSet> that represents the policy issuer.</span></span> <span data-ttu-id="0e5db-112">Może to być element `ClaimSet` reprezentujący aplikację lub `ClaimSet` wbudowaną `ClaimSet` (na przykład zwracaną przez właściwość statyczną <xref:System.IdentityModel.Claims.ClaimSet.System%2A> .</span><span class="sxs-lookup"><span data-stu-id="0e5db-112">This could be a `ClaimSet` that represents the application or a built-in `ClaimSet` (for example, the `ClaimSet` returned by the static <xref:System.IdentityModel.Claims.ClaimSet.System%2A> property.</span></span>  
  
4. <span data-ttu-id="0e5db-113">Zaimplementuj <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metodę zgodnie z opisem w poniższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="0e5db-113">Implement the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method as described in the following procedure.</span></span>  
  
### <a name="to-implement-the-evaluate-method"></a><span data-ttu-id="0e5db-114">Aby zaimplementować metodę szacowania</span><span class="sxs-lookup"><span data-stu-id="0e5db-114">To implement the Evaluate method</span></span>  
  
1. <span data-ttu-id="0e5db-115">Do tej metody są przesyłane dwa parametry: wystąpienie <xref:System.IdentityModel.Policy.EvaluationContext> klasy i odwołania do obiektu.</span><span class="sxs-lookup"><span data-stu-id="0e5db-115">Two parameters are passed to this method: an instance of the <xref:System.IdentityModel.Policy.EvaluationContext> class and an object reference.</span></span>  
  
2. <span data-ttu-id="0e5db-116">Jeśli niestandardowe zasady <xref:System.IdentityModel.Claims.ClaimSet> autoryzacji dodaje wystąpienia bez względu na bieżącą zawartość <xref:System.IdentityModel.Policy.EvaluationContext>, a następnie <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> Dodaj każdy z nich `ClaimSet` , wywołując metodę i zwracają `true` z <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0e5db-116">If the custom authorization policy adds <xref:System.IdentityModel.Claims.ClaimSet> instances without regard to the current content of the <xref:System.IdentityModel.Policy.EvaluationContext>, then add each `ClaimSet` by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and return `true` from the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> method.</span></span> <span data-ttu-id="0e5db-117">Zwrócenie `true` wskazuje na infrastrukturę autoryzacji, że zasady autoryzacji wykonała swoją pracy i nie muszą być ponownie wywoływane.</span><span class="sxs-lookup"><span data-stu-id="0e5db-117">Returning `true` indicates to the authorization infrastructure that the authorization policy has performed its work and does not need to be called again.</span></span>  
  
3. <span data-ttu-id="0e5db-118">Jeśli niestandardowe zasady autoryzacji dodają zestawy oświadczeń tylko wtedy `EvaluationContext`, gdy pewne oświadczenia znajdują się już w, należy poszukać tych oświadczeń poprzez sprawdzenie `ClaimSet` wystąpień zwracanych <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> przez właściwość.</span><span class="sxs-lookup"><span data-stu-id="0e5db-118">If the custom authorization policy adds claim sets only if certain claims are already present in the `EvaluationContext`, then look for those claims by examining the `ClaimSet` instances returned by the <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> property.</span></span> <span data-ttu-id="0e5db-119">Jeśli oświadczenia są obecne, Dodaj nowe zestawy oświadczeń przez wywołanie <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> metody i, jeśli nie ma więcej zestawów oświadczeń, zwróć `true`, wskazując na infrastrukturę autoryzacji, że zasady autoryzacji ukończyły pracę.</span><span class="sxs-lookup"><span data-stu-id="0e5db-119">If the claims are present, then add the new claim sets by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and, if no more claim sets are to be added, return `true`, indicating to the authorization infrastructure that the authorization policy has completed its work.</span></span> <span data-ttu-id="0e5db-120">Jeśli oświadczenia nie są obecne, zwróć `false`, wskazując, że zasady autoryzacji powinny być ponownie wywoływane, jeśli inne zasady autoryzacji dodają więcej zestawów oświadczeń `EvaluationContext`do.</span><span class="sxs-lookup"><span data-stu-id="0e5db-120">If the claims are not present, return `false`, indicating that the authorization policy should be called again if other authorization policies add more claim sets to the `EvaluationContext`.</span></span>  
  
4. <span data-ttu-id="0e5db-121">W bardziej złożonych scenariuszach przetwarzania drugi parametr <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metody jest używany do przechowywania zmiennej stanu, którą infrastruktura autoryzacji przejdzie z powrotem podczas każdego kolejnego wywołania <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metody dla określonej oceny.</span><span class="sxs-lookup"><span data-stu-id="0e5db-121">In more complex processing scenarios, the second parameter of the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method is used to store a state variable that the authorization infrastructure will pass back during each subsequent call to the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method for a particular evaluation.</span></span>  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a><span data-ttu-id="0e5db-122">Aby określić niestandardowe zasady autoryzacji za pomocą konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0e5db-122">To specify a custom authorization policy through configuration</span></span>  
  
1. <span data-ttu-id="0e5db-123">Określ typ niestandardowych zasad autoryzacji `policyType` w atrybucie `add` w `authorizationPolicies` elemencie elementu w `serviceAuthorization` elemencie.</span><span class="sxs-lookup"><span data-stu-id="0e5db-123">Specify the type of the custom authorization policy in the `policyType` attribute in the `add` element in the `authorizationPolicies` element in the `serviceAuthorization` element.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
        <serviceAuthorization serviceAuthorizationManagerType=  
                  "Samples.MyServiceAuthorizationManager" >  
          <authorizationPolicies>  
            <add policyType="Samples.MyAuthorizationPolicy" />  
          </authorizationPolicies>  
        </serviceAuthorization>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a><span data-ttu-id="0e5db-124">Aby określić niestandardowe zasady autoryzacji za pomocą kodu</span><span class="sxs-lookup"><span data-stu-id="0e5db-124">To specify a custom authorization policy through code</span></span>  
  
1. <span data-ttu-id="0e5db-125">Utwórz element <xref:System.Collections.Generic.List%601>. <xref:System.IdentityModel.Policy.IAuthorizationPolicy></span><span class="sxs-lookup"><span data-stu-id="0e5db-125">Create a <xref:System.Collections.Generic.List%601> of <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2. <span data-ttu-id="0e5db-126">Utwórz wystąpienie niestandardowych zasad autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="0e5db-126">Create an instance of the custom authorization policy.</span></span>  
  
3. <span data-ttu-id="0e5db-127">Dodaj wystąpienie zasad autoryzacji do listy.</span><span class="sxs-lookup"><span data-stu-id="0e5db-127">Add the authorization policy instance to the list.</span></span>  
  
4. <span data-ttu-id="0e5db-128">Powtórz kroki 2 i 3 dla każdej niestandardowej zasady autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="0e5db-128">Repeat steps 2 and 3 for each custom authorization policy.</span></span>  
  
5. <span data-ttu-id="0e5db-129">Przypisz do <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> właściwości wersję z listy tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="0e5db-129">Assign a read-only version of the list to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> property.</span></span>  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="0e5db-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="0e5db-130">Example</span></span>  
 <span data-ttu-id="0e5db-131">Poniższy przykład pokazuje kompletną <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementację.</span><span class="sxs-lookup"><span data-stu-id="0e5db-131">The following example shows a complete <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementation.</span></span>  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="0e5db-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e5db-132">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="0e5db-133">Instrukcje: Porównaj oświadczenia</span><span class="sxs-lookup"><span data-stu-id="0e5db-133">How to: Compare Claims</span></span>](how-to-compare-claims.md)
- [<span data-ttu-id="0e5db-134">Instrukcje: Tworzenie niestandardowego Menedżera autoryzacji dla usługi</span><span class="sxs-lookup"><span data-stu-id="0e5db-134">How to: Create a Custom Authorization Manager for a Service</span></span>](how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="0e5db-135">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="0e5db-135">Authorization Policy</span></span>](../samples/authorization-policy.md)
