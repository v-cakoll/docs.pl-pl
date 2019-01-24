---
title: 'Instrukcje: Tworzenie niestandardowych zasad autoryzacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: ba5d8d02d0c8d5993e1b072298aadcaa5fe0fe35
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705907"
---
# <a name="how-to-create-a-custom-authorization-policy"></a><span data-ttu-id="87802-102">Instrukcje: Tworzenie niestandardowych zasad autoryzacji</span><span class="sxs-lookup"><span data-stu-id="87802-102">How to: Create a Custom Authorization Policy</span></span>
<span data-ttu-id="87802-103">Infrastruktura modelu tożsamości w Windows Communication Foundation (WCF) obsługuje model na podstawie oświadczeń autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="87802-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports a claim-based authorization model.</span></span> <span data-ttu-id="87802-104">Wyodrębnione z tokenów, opcjonalnie przetwarzane przez niestandardowych zasad autoryzacji i następnie umieszczać w oświadczeń <xref:System.IdentityModel.Policy.AuthorizationContext> , następnie można zbadać do podejmowania decyzji dotyczących autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="87802-104">Claims are extracted from tokens, optionally processed by custom authorization policy, and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext> that can then be examined to make authorization decisions.</span></span> <span data-ttu-id="87802-105">Zasady niestandardowe może służyć do przekształcania oświadczeń przychodzących tokenów oświadczeń oczekiwane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="87802-105">A custom policy can be used to transform claims from incoming tokens into claims expected by the application.</span></span> <span data-ttu-id="87802-106">W ten sposób warstwy aplikacji mogą być izolowane dane na różne oświadczenia, obsługiwane przez różne typy tokenów, które obsługuje usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="87802-106">In this way, the application layer can be insulated from the details on the differing claims served up by the different token types that WCF supports.</span></span> <span data-ttu-id="87802-107">W tym temacie pokazano, jak zaimplementować niestandardowych zasad autoryzacji oraz sposób dodawania tej zasady do kolekcji zasad używanych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="87802-107">This topic shows how to implement a custom authorization policy and how to add that policy to the collection of policies used by a service.</span></span>  
  
### <a name="to-implement-a-custom-authorization-policy"></a><span data-ttu-id="87802-108">Aby zaimplementować niestandardowych zasad autoryzacji</span><span class="sxs-lookup"><span data-stu-id="87802-108">To implement a custom authorization policy</span></span>  
  
1.  <span data-ttu-id="87802-109">Zdefiniuj nową klasę, która pochodzi od klasy <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="87802-109">Define a new class that derives from <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2.  <span data-ttu-id="87802-110">Implementowanie tylko do odczytu <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> właściwości przez wygenerowanie unikatowego ciągu w konstruktorze klasy i zwraca ciąg, w każdym przypadku, gdy uzyskano dostęp do właściwości.</span><span class="sxs-lookup"><span data-stu-id="87802-110">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> property by generating a unique string in the constructor for the class and returning that string whenever the property is accessed.</span></span>  
  
3.  <span data-ttu-id="87802-111">Implementowanie tylko do odczytu <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> właściwości, zwracając <xref:System.IdentityModel.Claims.ClaimSet> reprezentujący wystawcy zasad.</span><span class="sxs-lookup"><span data-stu-id="87802-111">Implement the read-only <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> property by returning a <xref:System.IdentityModel.Claims.ClaimSet> that represents the policy issuer.</span></span> <span data-ttu-id="87802-112">Może to być `ClaimSet` reprezentujący aplikację lub wbudowanego `ClaimSet` (na przykład `ClaimSet` zwróconą przez statyczną <xref:System.IdentityModel.Claims.ClaimSet.System%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="87802-112">This could be a `ClaimSet` that represents the application or a built-in `ClaimSet` (for example, the `ClaimSet` returned by the static <xref:System.IdentityModel.Claims.ClaimSet.System%2A> property.</span></span>  
  
4.  <span data-ttu-id="87802-113">Implementowanie <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda zgodnie z opisem w poniższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="87802-113">Implement the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method as described in the following procedure.</span></span>  
  
### <a name="to-implement-the-evaluate-method"></a><span data-ttu-id="87802-114">Aby wdrożyć metodę Evaluate</span><span class="sxs-lookup"><span data-stu-id="87802-114">To implement the Evaluate method</span></span>  
  
1.  <span data-ttu-id="87802-115">Dwa parametry są przekazywane do tej metody: wystąpienie <xref:System.IdentityModel.Policy.EvaluationContext> klasy i odwołanie do obiektu.</span><span class="sxs-lookup"><span data-stu-id="87802-115">Two parameters are passed to this method: an instance of the <xref:System.IdentityModel.Policy.EvaluationContext> class and an object reference.</span></span>  
  
2.  <span data-ttu-id="87802-116">Jeśli dodanie niestandardowych zasad autoryzacji <xref:System.IdentityModel.Claims.ClaimSet> wystąpienia, bez względu na bieżącą zawartość <xref:System.IdentityModel.Policy.EvaluationContext>, następnie dodać każdy `ClaimSet` przez wywołanie metody <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> metody i wróć `true` z <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="87802-116">If the custom authorization policy adds <xref:System.IdentityModel.Claims.ClaimSet> instances without regard to the current content of the <xref:System.IdentityModel.Policy.EvaluationContext>, then add each `ClaimSet` by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and return `true` from the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> method.</span></span> <span data-ttu-id="87802-117">Zwracanie `true` wskazuje infrastruktury autoryzacji, że zasady autoryzacji ma wykonać swoją pracę i nie trzeba ponownie wywołana.</span><span class="sxs-lookup"><span data-stu-id="87802-117">Returning `true` indicates to the authorization infrastructure that the authorization policy has performed its work and does not need to be called again.</span></span>  
  
3.  <span data-ttu-id="87802-118">Jeśli niestandardowych zasad autoryzacji dodaje zestawów oświadczeń tylko wtedy, gdy niektóre oświadczenia jest już obecny w `EvaluationContext`, poszukaj te oświadczenia, sprawdzając `ClaimSet` wystąpień zwrócona przez <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="87802-118">If the custom authorization policy adds claim sets only if certain claims are already present in the `EvaluationContext`, then look for those claims by examining the `ClaimSet` instances returned by the <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> property.</span></span> <span data-ttu-id="87802-119">Jeśli oświadczenia są obecne, Dodaj nowe oświadczenie ustawia przez wywołanie metody <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> metoda i jeśli nie ma więcej oświadczeń zestawy mają być dodawane zwracany `true`oznaczający infrastruktury autoryzacji, że zasady autoryzacji zakończy pracę.</span><span class="sxs-lookup"><span data-stu-id="87802-119">If the claims are present, then add the new claim sets by calling the <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> method and, if no more claim sets are to be added, return `true`, indicating to the authorization infrastructure that the authorization policy has completed its work.</span></span> <span data-ttu-id="87802-120">Jeśli oświadczenia nie są obecne, zwracają `false`, wskazujący, że zasady autoryzacji powinna zostać wywołana, jeśli inne zasady autoryzacji, Dodaj więcej w zestawie oświadczeń do `EvaluationContext`.</span><span class="sxs-lookup"><span data-stu-id="87802-120">If the claims are not present, return `false`, indicating that the authorization policy should be called again if other authorization policies add more claim sets to the `EvaluationContext`.</span></span>  
  
4.  <span data-ttu-id="87802-121">W bardziej złożonych scenariuszy przetwarzania, drugi parametr <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda jest używana do przechowywania zmiennej stanu, który infrastruktury autoryzacji będzie przekazywany w trakcie każde kolejne wywołanie <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metodę dla konkretnej wersji ewaluacyjnej.</span><span class="sxs-lookup"><span data-stu-id="87802-121">In more complex processing scenarios, the second parameter of the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method is used to store a state variable that the authorization infrastructure will pass back during each subsequent call to the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method for a particular evaluation.</span></span>  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a><span data-ttu-id="87802-122">Aby określić niestandardowych zasad autoryzacji za pomocą konfiguracji</span><span class="sxs-lookup"><span data-stu-id="87802-122">To specify a custom authorization policy through configuration</span></span>  
  
1.  <span data-ttu-id="87802-123">Określ typ niestandardowych zasad autoryzacji w `policyType` atrybutu w `add` element `authorizationPolicies` element `serviceAuthorization` elementu.</span><span class="sxs-lookup"><span data-stu-id="87802-123">Specify the type of the custom authorization policy in the `policyType` attribute in the `add` element in the `authorizationPolicies` element in the `serviceAuthorization` element.</span></span>  
  
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
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a><span data-ttu-id="87802-124">Aby określić niestandardowych zasad autoryzacji za pomocą kodu</span><span class="sxs-lookup"><span data-stu-id="87802-124">To specify a custom authorization policy through code</span></span>  
  
1.  <span data-ttu-id="87802-125">Tworzenie <xref:System.Collections.Generic.List%601> z <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="87802-125">Create a <xref:System.Collections.Generic.List%601> of <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
2.  <span data-ttu-id="87802-126">Utwórz wystąpienie niestandardowych zasad autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="87802-126">Create an instance of the custom authorization policy.</span></span>  
  
3.  <span data-ttu-id="87802-127">Dodaj wystąpienie zasad autoryzacji do listy.</span><span class="sxs-lookup"><span data-stu-id="87802-127">Add the authorization policy instance to the list.</span></span>  
  
4.  <span data-ttu-id="87802-128">Powtórz kroki 2 i 3 dla każdego niestandardowych zasad autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="87802-128">Repeat steps 2 and 3 for each custom authorization policy.</span></span>  
  
5.  <span data-ttu-id="87802-129">Przypisz wersji tylko do odczytu na liście, aby <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="87802-129">Assign a read-only version of the list to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> property.</span></span>  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="87802-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="87802-130">Example</span></span>  
 <span data-ttu-id="87802-131">Poniższy przykład pokazuje kompletną <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementacji.</span><span class="sxs-lookup"><span data-stu-id="87802-131">The following example shows a complete <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementation.</span></span>  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="87802-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87802-132">See also</span></span>
- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="87802-133">Instrukcje: Porównywanie oświadczeń</span><span class="sxs-lookup"><span data-stu-id="87802-133">How to: Compare Claims</span></span>](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)
- [<span data-ttu-id="87802-134">Instrukcje: Tworzenie Menedżera autoryzacji niestandardowej dla usługi</span><span class="sxs-lookup"><span data-stu-id="87802-134">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="87802-135">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="87802-135">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
