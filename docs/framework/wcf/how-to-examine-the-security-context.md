---
title: 'Instrukcje: Badanie kontekstu zabezpieczeń'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceSecurityContext class
- WCF, security
- Claimset class
ms.assetid: 389b5a57-4175-4bc0-ada0-fc750d51149f
author: BrucePerlerMS
ms.openlocfilehash: c2cb1f6d06961546a04b4a132bf9861c925ca421
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47113861"
---
# <a name="how-to-examine-the-security-context"></a><span data-ttu-id="cca66-102">Instrukcje: Badanie kontekstu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="cca66-102">How to: Examine the Security Context</span></span>
<span data-ttu-id="cca66-103">Podczas programowania usług Windows Communication Foundation (WCF), Usługa kontekstu zabezpieczeń umożliwia określenie szczegółowe informacje dotyczące poświadczeń klienta i oświadczeń używany do uwierzytelniania w usłudze.</span><span class="sxs-lookup"><span data-stu-id="cca66-103">When programming Windows Communication Foundation (WCF) services, the service security context enables you to determine details about the client credentials and claims used to authenticate with the service.</span></span> <span data-ttu-id="cca66-104">Jest to wykonywane przy użyciu właściwości <xref:System.ServiceModel.ServiceSecurityContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="cca66-104">This is done by using the properties of the <xref:System.ServiceModel.ServiceSecurityContext> class.</span></span>  
  
 <span data-ttu-id="cca66-105">Na przykład, można pobrać tożsamości bieżącego klienta za pomocą <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> lub <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cca66-105">For example, you can retrieve the identity of the current client by using the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> or the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property.</span></span> <span data-ttu-id="cca66-106">Aby określić, czy klient jest anonimowe, użyj <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cca66-106">To determine whether the client is anonymous, use the <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> property.</span></span>  
  
 <span data-ttu-id="cca66-107">Możesz również określić, jakie oświadczenia są wykonywane w imieniu klienta przez iteracji w kolekcji oświadczeń w <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cca66-107">You can also determine what claims are being made on behalf of the client by iterating through the collection of claims in the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
### <a name="to-get-the-current-security-context"></a><span data-ttu-id="cca66-108">Aby uzyskać bieżący kontekst zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="cca66-108">To get the current security context</span></span>  
  
-   <span data-ttu-id="cca66-109">Dostęp do właściwości statycznej <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> można pobrać bieżącego kontekstu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="cca66-109">Access the static property <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> to get the current security context.</span></span> <span data-ttu-id="cca66-110">Sprawdź właściwości bieżącego kontekstu z odwołania.</span><span class="sxs-lookup"><span data-stu-id="cca66-110">Examine any of the properties of the current context from the reference.</span></span>  
  
### <a name="to-determine-the-identity-of-the-caller"></a><span data-ttu-id="cca66-111">Aby ustalić tożsamość elementu wywołującego</span><span class="sxs-lookup"><span data-stu-id="cca66-111">To determine the identity of the caller</span></span>  
  
1.  <span data-ttu-id="cca66-112">Drukuj wartość <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> i <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cca66-112">Print the value of the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> properties.</span></span>  
  
### <a name="to-parse-the-claims-of-a-caller"></a><span data-ttu-id="cca66-113">Aby przeanalizować oświadczenia obiekt wywołujący</span><span class="sxs-lookup"><span data-stu-id="cca66-113">To parse the claims of a caller</span></span>  
  
1.  <span data-ttu-id="cca66-114">Zwraca bieżący <xref:System.IdentityModel.Policy.AuthorizationContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="cca66-114">Return the current <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span> <span data-ttu-id="cca66-115">Użyj <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> właściwość zwraca bieżący kontekst zabezpieczeń usługi, a następnie wrócisz `AuthorizationContext` przy użyciu <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cca66-115">Use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to return the current service security context, then return the `AuthorizationContext` using the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
2.  <span data-ttu-id="cca66-116">Analizowanie kolekcję <xref:System.IdentityModel.Claims.ClaimSet> obiektów zwróconych przez <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> właściwość <xref:System.IdentityModel.Policy.AuthorizationContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="cca66-116">Parse the collection of <xref:System.IdentityModel.Claims.ClaimSet> objects returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cca66-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="cca66-117">Example</span></span>  
 <span data-ttu-id="cca66-118">Poniższy przykład drukuje wartości <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> i <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> właściwości bieżącego kontekstu zabezpieczeń i <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> właściwość, wartość zasobu, oświadczenia, a <xref:System.IdentityModel.Claims.Claim.Right%2A> właściwości każdego oświadczenia w bieżącym zabezpieczeń kontekst.</span><span class="sxs-lookup"><span data-stu-id="cca66-118">The following example prints the values of the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> properties of the current security context and the <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> property, the resource value of the claim, and the <xref:System.IdentityModel.Claims.Claim.Right%2A> property of every claim in the current security context.</span></span>  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cca66-119">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="cca66-119">Compiling the Code</span></span>  
 <span data-ttu-id="cca66-120">Kod używa następujących przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="cca66-120">The code uses the following namespaces:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.IdentityModel.Policy>  
  
-   <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a><span data-ttu-id="cca66-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cca66-121">See Also</span></span>  
 [<span data-ttu-id="cca66-122">Zabezpieczanie usług</span><span class="sxs-lookup"><span data-stu-id="cca66-122">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="cca66-123">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="cca66-123">Service Identity and Authentication</span></span>](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
