---
title: "Porady: tworzenie weryfikatora tożsamości niestandardowego klienta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b10dd9be996369385ca323b0409145a9cde46a1e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a><span data-ttu-id="bbcb8-102">Porady: tworzenie weryfikatora tożsamości niestandardowego klienta</span><span class="sxs-lookup"><span data-stu-id="bbcb8-102">How to: Create a Custom Client Identity Verifier</span></span>
<span data-ttu-id="bbcb8-103">*Tożsamości* funkcji [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] z góry określić oczekiwaną tożsamość usługi przez klienta.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-103">The *identity* feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] enables a client to specify in advance the expected identity of the service.</span></span> <span data-ttu-id="bbcb8-104">Zawsze, gdy serwer uwierzytelnia do klienta, tożsamość jest sprawdzana względem Oczekiwana tożsamość.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-104">Whenever a server authenticates itself to the client, the identity is checked against the expected identity.</span></span> <span data-ttu-id="bbcb8-105">(Aby uzyskać informacje o tożsamości i jej działania, zobacz [uwierzytelnianie i tożsamość usługi](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)</span><span class="sxs-lookup"><span data-stu-id="bbcb8-105">(For an explanation of identity and how it works, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)</span></span>  
  
 <span data-ttu-id="bbcb8-106">W razie potrzeby można dostosować weryfikacji przy użyciu weryfikatora tożsamości niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-106">If needed, the verification can be customized using a custom identity verifier.</span></span> <span data-ttu-id="bbcb8-107">Na przykład można wykonać testy weryfikacji tożsamości dodatkowych usług.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-107">For example, you can perform additional service identity verification checks.</span></span> <span data-ttu-id="bbcb8-108">W tym przykładzie weryfikatora tożsamość niestandardowa sprawdza dodatkowe oświadczeń w certyfikatu X.509 zwrócone z serwera.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-108">In this example, the custom identity verifier checks additional claims in the X.509 certificate returned from the server.</span></span> <span data-ttu-id="bbcb8-109">Przykładową aplikację, zobacz [tożsamość usług — przykład](../../../../docs/framework/wcf/samples/service-identity-sample.md).</span><span class="sxs-lookup"><span data-stu-id="bbcb8-109">For a sample application, see [Service Identity Sample](../../../../docs/framework/wcf/samples/service-identity-sample.md).</span></span>  
  
### <a name="to-extend-the-endpointidentity-class"></a><span data-ttu-id="bbcb8-110">Aby rozszerzyć klasy właściwość EndpointIdentity elementu</span><span class="sxs-lookup"><span data-stu-id="bbcb8-110">To extend the EndpointIdentity class</span></span>  
  
1.  <span data-ttu-id="bbcb8-111">Zdefiniuj nową klasę, która jest pochodną <xref:System.ServiceModel.EndpointIdentity> klasy.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-111">Define a new class that derives from the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="bbcb8-112">W tym przykładzie nazwy rozszerzenia `OrgEndpointIdentity`.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-112">This example names the extension `OrgEndpointIdentity`.</span></span>  
  
2.  <span data-ttu-id="bbcb8-113">Dodawanie członków prywatnych oraz właściwości, które będą używane przez rozszerzony <xref:System.ServiceModel.Security.IdentityVerifier> klasy można przeprowadzić sprawdzenia tożsamości przed oświadczenia w tokenie zabezpieczającym zwrócony przez usługę.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-113">Add private members along with properties that will be used by the extended <xref:System.ServiceModel.Security.IdentityVerifier> class to perform the identity check against claims in the security token returned from the service.</span></span> <span data-ttu-id="bbcb8-114">W tym przykładzie zdefiniowano jedną właściwość: `OrganizationClaim` właściwości.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-114">This example defines one property: the `OrganizationClaim` property.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a><span data-ttu-id="bbcb8-115">Aby rozszerzyć klasy IdentityVerifier</span><span class="sxs-lookup"><span data-stu-id="bbcb8-115">To extend the IdentityVerifier class</span></span>  
  
1.  <span data-ttu-id="bbcb8-116">Zdefiniuj nową klasę, która jest pochodną <xref:System.ServiceModel.Security.IdentityVerifier>.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-116">Define a new class that derives from <xref:System.ServiceModel.Security.IdentityVerifier>.</span></span> <span data-ttu-id="bbcb8-117">W tym przykładzie nazwy rozszerzenia `CustomIdentityVerifier`.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-117">This example names the extension `CustomIdentityVerifier`.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2.  <span data-ttu-id="bbcb8-118">Zastąpienie <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-118">Override the <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> method.</span></span> <span data-ttu-id="bbcb8-119">Metoda określa, czy sprawdzić tożsamości powodzeniem lub niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-119">The method determines whether the identity check succeeded or failed.</span></span>  
  
3.  <span data-ttu-id="bbcb8-120">`CheckAccess` Metoda ma dwa parametry.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-120">The `CheckAccess` method has two parameters.</span></span> <span data-ttu-id="bbcb8-121">Pierwsza to wystąpienie <xref:System.ServiceModel.EndpointIdentity> klasy.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-121">The first is an instance of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="bbcb8-122">Drugim jest wystąpieniem <xref:System.IdentityModel.Policy.AuthorizationContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-122">The second is an instance of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
     <span data-ttu-id="bbcb8-123">W implementacji metody, sprawdź kolekcji oświadczeń zwrócony przez <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> właściwość <xref:System.IdentityModel.Policy.AuthorizationContext> klasy, a następnie automatycznie uwierzytelniające zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-123">In the method implementation, examine the collection of claims returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class, and perform authentication checks as required.</span></span> <span data-ttu-id="bbcb8-124">Ten przykład rozpoczyna się od znajdowanie oświadczenie jest typu "Nazwy wyróżniającej", a następnie porównuje Nazwa rozszerzenia <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span><span class="sxs-lookup"><span data-stu-id="bbcb8-124">This example begins by finding any claim that is of type "Distinguished Name" and then compares the name to the extension of the <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a><span data-ttu-id="bbcb8-125">Aby zaimplementować metodę TryGetIdentity</span><span class="sxs-lookup"><span data-stu-id="bbcb8-125">To implement the TryGetIdentity method</span></span>  
  
1.  <span data-ttu-id="bbcb8-126">Implementowanie <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> metodę, która określa, czy wystąpienie <xref:System.ServiceModel.EndpointIdentity> klasy może być zwracany przez klienta.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-126">Implement the <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> method, which determines whether an instance of the <xref:System.ServiceModel.EndpointIdentity> class can be returned by the client.</span></span> <span data-ttu-id="bbcb8-127">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Infrastruktury wymaga wykonania `TryGetIdentity` metodę, aby najpierw pobrać tożsamości usługi z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-127">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure calls the implementation of the `TryGetIdentity` method first to retrieve the service's identity from the message.</span></span> <span data-ttu-id="bbcb8-128">Następnie wywołuje infrastruktury `CheckAccess` implementację zwróconego `EndpointIdentity` i <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-128">Next, the infrastructure calls the `CheckAccess` implementation with the returned `EndpointIdentity` and <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span>  
  
2.  <span data-ttu-id="bbcb8-129">W `TryGetIdentity` metodę, umieść następujący kod:</span><span class="sxs-lookup"><span data-stu-id="bbcb8-129">In the `TryGetIdentity` method, put the following code:</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a><span data-ttu-id="bbcb8-130">Do wdrażania niestandardowego powiązania i ustawić IdentityVerifier niestandardowych</span><span class="sxs-lookup"><span data-stu-id="bbcb8-130">To implement a custom binding and set the custom IdentityVerifier</span></span>  
  
1.  <span data-ttu-id="bbcb8-131">Tworzenie metody, która zwraca <xref:System.ServiceModel.Channels.Binding> obiektu.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-131">Create a method that returns a <xref:System.ServiceModel.Channels.Binding> object.</span></span> <span data-ttu-id="bbcb8-132">Rozpoczyna się w tym przykładzie tworzy wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustawia jej tryb zabezpieczeń <xref:System.ServiceModel.SecurityMode.Message>, a jego <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> do <xref:System.ServiceModel.MessageCredentialType.None>.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-132">This example begins creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class and sets its security mode to <xref:System.ServiceModel.SecurityMode.Message>, and its <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> to <xref:System.ServiceModel.MessageCredentialType.None>.</span></span>  
  
2.  <span data-ttu-id="bbcb8-133">Utwórz <xref:System.ServiceModel.Channels.BindingElementCollection> przy użyciu <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-133">Create a <xref:System.ServiceModel.Channels.BindingElementCollection> using the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3.  <span data-ttu-id="bbcb8-134">Zwraca <xref:System.ServiceModel.Channels.SecurityBindingElement> z kolekcji i rzutować obiekt <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> zmiennej.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-134">Return the <xref:System.ServiceModel.Channels.SecurityBindingElement> from the collection and cast it to a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> variable.</span></span>  
  
4.  <span data-ttu-id="bbcb8-135">Ustaw <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> właściwość <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> klasę, aby nowe wystąpienie klasy `CustomIdentityVerifier` klasy utworzone wcześniej.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-135">Set the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> property of the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class to a new instance of the `CustomIdentityVerifier` class created previously.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5.  <span data-ttu-id="bbcb8-136">Niestandardowego powiązania, który jest zwracany jest używany do utworzenia wystąpienia klienta i klasy.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-136">The custom binding that is returned is used to create an instance of the client and class.</span></span> <span data-ttu-id="bbcb8-137">Klient następnie można przeprowadzić weryfikacji tożsamości niestandardowej usługi, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-137">The client can then perform a custom identity verification check of the service as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="bbcb8-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="bbcb8-138">Example</span></span>  
 <span data-ttu-id="bbcb8-139">W poniższym przykładzie przedstawiono pełną implementację <xref:System.ServiceModel.Security.IdentityVerifier> klasy.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-139">The following example shows a complete implementation of the <xref:System.ServiceModel.Security.IdentityVerifier> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="bbcb8-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="bbcb8-140">Example</span></span>  
 <span data-ttu-id="bbcb8-141">W poniższym przykładzie przedstawiono pełną implementację <xref:System.ServiceModel.EndpointIdentity> klasy.</span><span class="sxs-lookup"><span data-stu-id="bbcb8-141">The following example shows a complete implementation of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="bbcb8-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bbcb8-142">See Also</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 <xref:System.ServiceModel.EndpointIdentity>  
 <xref:System.ServiceModel.Security.IdentityVerifier>  
 [<span data-ttu-id="bbcb8-143">Tożsamość usług — przykład</span><span class="sxs-lookup"><span data-stu-id="bbcb8-143">Service Identity Sample</span></span>](../../../../docs/framework/wcf/samples/service-identity-sample.md)  
 [<span data-ttu-id="bbcb8-144">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="bbcb8-144">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)  
 [<span data-ttu-id="bbcb8-145">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="bbcb8-145">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
