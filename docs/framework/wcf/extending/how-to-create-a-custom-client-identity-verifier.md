---
title: 'Instrukcje: tworzenie niestandardowego weryfikatora tożsamości klienta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
ms.openlocfilehash: c7aede448fa0a759035380c533f2a9457a534bd1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165831"
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a><span data-ttu-id="ec925-102">Instrukcje: tworzenie niestandardowego weryfikatora tożsamości klienta</span><span class="sxs-lookup"><span data-stu-id="ec925-102">How to: Create a Custom Client Identity Verifier</span></span>
<span data-ttu-id="ec925-103">*Tożsamości* funkcji Windows Communication Foundation (WCF) umożliwia klientowi określenie z wyprzedzeniem oczekiwaną tożsamość usługi.</span><span class="sxs-lookup"><span data-stu-id="ec925-103">The *identity* feature of Windows Communication Foundation (WCF) enables a client to specify in advance the expected identity of the service.</span></span> <span data-ttu-id="ec925-104">Zawsze, gdy serwer uwierzytelnia klienta, tożsamość jest sprawdzana względem oczekiwaną tożsamość.</span><span class="sxs-lookup"><span data-stu-id="ec925-104">Whenever a server authenticates itself to the client, the identity is checked against the expected identity.</span></span> <span data-ttu-id="ec925-105">(Objaśnienia dotyczące tożsamości i jak to działa, zobacz [uwierzytelnianie i tożsamość usług](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)</span><span class="sxs-lookup"><span data-stu-id="ec925-105">(For an explanation of identity and how it works, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)</span></span>  
  
 <span data-ttu-id="ec925-106">Jeśli to konieczne, można dostosować weryfikacji przy użyciu weryfikatora tożsamości niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="ec925-106">If needed, the verification can be customized using a custom identity verifier.</span></span> <span data-ttu-id="ec925-107">Na przykład można wykonać testy weryfikacyjne opisane tożsamości usługi dodatkowe.</span><span class="sxs-lookup"><span data-stu-id="ec925-107">For example, you can perform additional service identity verification checks.</span></span> <span data-ttu-id="ec925-108">W tym przykładzie weryfikatora tożsamości niestandardowej sprawdza, czy dodatkowe oświadczenia w certyfikacie X.509 zwrócona z serwera.</span><span class="sxs-lookup"><span data-stu-id="ec925-108">In this example, the custom identity verifier checks additional claims in the X.509 certificate returned from the server.</span></span> <span data-ttu-id="ec925-109">Dla przykładowej aplikacji, zobacz [tożsamość usług — przykład](../../../../docs/framework/wcf/samples/service-identity-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ec925-109">For a sample application, see [Service Identity Sample](../../../../docs/framework/wcf/samples/service-identity-sample.md).</span></span>  
  
### <a name="to-extend-the-endpointidentity-class"></a><span data-ttu-id="ec925-110">Aby rozszerzyć klasę wartość właściwości EndpointIdentity</span><span class="sxs-lookup"><span data-stu-id="ec925-110">To extend the EndpointIdentity class</span></span>  
  
1.  <span data-ttu-id="ec925-111">Zdefiniuj nową klasę, która pochodzi od klasy <xref:System.ServiceModel.EndpointIdentity> klasy.</span><span class="sxs-lookup"><span data-stu-id="ec925-111">Define a new class that derives from the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="ec925-112">W tym przykładzie nazwy rozszerzenia `OrgEndpointIdentity`.</span><span class="sxs-lookup"><span data-stu-id="ec925-112">This example names the extension `OrgEndpointIdentity`.</span></span>  
  
2.  <span data-ttu-id="ec925-113">Dodaj składowe prywatne oraz właściwości, które będą używane przez rozszerzonych <xref:System.ServiceModel.Security.IdentityVerifier> klasy do sprawdzania tożsamości przed oświadczenia w tokenie zabezpieczającym zwrócony przez usługę.</span><span class="sxs-lookup"><span data-stu-id="ec925-113">Add private members along with properties that will be used by the extended <xref:System.ServiceModel.Security.IdentityVerifier> class to perform the identity check against claims in the security token returned from the service.</span></span> <span data-ttu-id="ec925-114">Ten przykład definiuje jedną właściwość: `OrganizationClaim` właściwości.</span><span class="sxs-lookup"><span data-stu-id="ec925-114">This example defines one property: the `OrganizationClaim` property.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a><span data-ttu-id="ec925-115">Aby rozszerzyć klasę IdentityVerifier</span><span class="sxs-lookup"><span data-stu-id="ec925-115">To extend the IdentityVerifier class</span></span>  
  
1.  <span data-ttu-id="ec925-116">Zdefiniuj nową klasę, która pochodzi od klasy <xref:System.ServiceModel.Security.IdentityVerifier>.</span><span class="sxs-lookup"><span data-stu-id="ec925-116">Define a new class that derives from <xref:System.ServiceModel.Security.IdentityVerifier>.</span></span> <span data-ttu-id="ec925-117">W tym przykładzie nazwy rozszerzenia `CustomIdentityVerifier`.</span><span class="sxs-lookup"><span data-stu-id="ec925-117">This example names the extension `CustomIdentityVerifier`.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2.  <span data-ttu-id="ec925-118">Zastąp <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ec925-118">Override the <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> method.</span></span> <span data-ttu-id="ec925-119">Metoda określa, czy sprawdzić tożsamości zakończonych powodzeniem lub niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="ec925-119">The method determines whether the identity check succeeded or failed.</span></span>  
  
3.  <span data-ttu-id="ec925-120">`CheckAccess` Metoda ma dwa parametry.</span><span class="sxs-lookup"><span data-stu-id="ec925-120">The `CheckAccess` method has two parameters.</span></span> <span data-ttu-id="ec925-121">Pierwsza to wystąpienie <xref:System.ServiceModel.EndpointIdentity> klasy.</span><span class="sxs-lookup"><span data-stu-id="ec925-121">The first is an instance of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="ec925-122">Druga to wystąpienie <xref:System.IdentityModel.Policy.AuthorizationContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="ec925-122">The second is an instance of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
     <span data-ttu-id="ec925-123">W implementacji metody Sprawdź zbiór oświadczenia zwrócone przez <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> właściwość <xref:System.IdentityModel.Policy.AuthorizationContext> klasy i wykonywania kontroli uwierzytelniania zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="ec925-123">In the method implementation, examine the collection of claims returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class, and perform authentication checks as required.</span></span> <span data-ttu-id="ec925-124">W tym przykładzie rozpoczyna się od wyszukiwania wszelkie roszczenia, które jest typu "Nazwy wyróżniającej", a następnie porównuje nazwę z rozszerzeniem programu <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span><span class="sxs-lookup"><span data-stu-id="ec925-124">This example begins by finding any claim that is of type "Distinguished Name" and then compares the name to the extension of the <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a><span data-ttu-id="ec925-125">Aby wdrożyć metodę TryGetIdentity</span><span class="sxs-lookup"><span data-stu-id="ec925-125">To implement the TryGetIdentity method</span></span>  
  
1.  <span data-ttu-id="ec925-126">Implementowanie <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> metody, która określa, czy wystąpienie <xref:System.ServiceModel.EndpointIdentity> klasy mogą być zwracane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="ec925-126">Implement the <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> method, which determines whether an instance of the <xref:System.ServiceModel.EndpointIdentity> class can be returned by the client.</span></span> <span data-ttu-id="ec925-127">Infrastruktura WCF wymaga wykonania `TryGetIdentity` metoda najpierw pobierania tożsamości usługi z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="ec925-127">The WCF infrastructure calls the implementation of the `TryGetIdentity` method first to retrieve the service's identity from the message.</span></span> <span data-ttu-id="ec925-128">Następnie wywołuje infrastruktury `CheckAccess` wdrożenia za pomocą zwróconych `EndpointIdentity` i <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="ec925-128">Next, the infrastructure calls the `CheckAccess` implementation with the returned `EndpointIdentity` and <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span>  
  
2.  <span data-ttu-id="ec925-129">W `TryGetIdentity` metodę, umieść następujący kod:</span><span class="sxs-lookup"><span data-stu-id="ec925-129">In the `TryGetIdentity` method, put the following code:</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a><span data-ttu-id="ec925-130">Implementowanie niestandardowego powiązania i ustaw IdentityVerifier niestandardowe</span><span class="sxs-lookup"><span data-stu-id="ec925-130">To implement a custom binding and set the custom IdentityVerifier</span></span>  
  
1.  <span data-ttu-id="ec925-131">Utwórz metodę, która zwraca <xref:System.ServiceModel.Channels.Binding> obiektu.</span><span class="sxs-lookup"><span data-stu-id="ec925-131">Create a method that returns a <xref:System.ServiceModel.Channels.Binding> object.</span></span> <span data-ttu-id="ec925-132">Rozpoczyna się w tym przykładzie tworzone jest wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustawia jej tryb zabezpieczeń <xref:System.ServiceModel.SecurityMode.Message>i jego <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> do <xref:System.ServiceModel.MessageCredentialType.None>.</span><span class="sxs-lookup"><span data-stu-id="ec925-132">This example begins creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class and sets its security mode to <xref:System.ServiceModel.SecurityMode.Message>, and its <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> to <xref:System.ServiceModel.MessageCredentialType.None>.</span></span>  
  
2.  <span data-ttu-id="ec925-133">Tworzenie <xref:System.ServiceModel.Channels.BindingElementCollection> przy użyciu <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ec925-133">Create a <xref:System.ServiceModel.Channels.BindingElementCollection> using the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3.  <span data-ttu-id="ec925-134">Zwróć <xref:System.ServiceModel.Channels.SecurityBindingElement> z kolekcji i obsadź ją <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ec925-134">Return the <xref:System.ServiceModel.Channels.SecurityBindingElement> from the collection and cast it to a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> variable.</span></span>  
  
4.  <span data-ttu-id="ec925-135">Ustaw <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> właściwość <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> nowe wystąpienie klasy `CustomIdentityVerifier` klasy został wcześniej utworzony.</span><span class="sxs-lookup"><span data-stu-id="ec925-135">Set the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> property of the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class to a new instance of the `CustomIdentityVerifier` class created previously.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5.  <span data-ttu-id="ec925-136">Niestandardowego powiązania, który jest zwracany jest używany do utworzenia wystąpienia klienta i klasy.</span><span class="sxs-lookup"><span data-stu-id="ec925-136">The custom binding that is returned is used to create an instance of the client and class.</span></span> <span data-ttu-id="ec925-137">Klienta można wykonać sprawdzenia weryfikacji tożsamości niestandardowej usługi jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ec925-137">The client can then perform a custom identity verification check of the service as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="ec925-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="ec925-138">Example</span></span>  
 <span data-ttu-id="ec925-139">W poniższym przykładzie pokazano pełne wdrożenie <xref:System.ServiceModel.Security.IdentityVerifier> klasy.</span><span class="sxs-lookup"><span data-stu-id="ec925-139">The following example shows a complete implementation of the <xref:System.ServiceModel.Security.IdentityVerifier> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="ec925-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="ec925-140">Example</span></span>  
 <span data-ttu-id="ec925-141">W poniższym przykładzie pokazano pełne wdrożenie <xref:System.ServiceModel.EndpointIdentity> klasy.</span><span class="sxs-lookup"><span data-stu-id="ec925-141">The following example shows a complete implementation of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="ec925-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec925-142">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- <xref:System.ServiceModel.EndpointIdentity>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [<span data-ttu-id="ec925-143">Tożsamość usług — przykład</span><span class="sxs-lookup"><span data-stu-id="ec925-143">Service Identity Sample</span></span>](../../../../docs/framework/wcf/samples/service-identity-sample.md)
- [<span data-ttu-id="ec925-144">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="ec925-144">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
