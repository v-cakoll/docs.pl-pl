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
ms.openlocfilehash: 328d47a583a4f047fd54589a82d339de2cb1a16f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320989"
---
# <a name="how-to-examine-the-security-context"></a><span data-ttu-id="09864-102">Instrukcje: Badanie kontekstu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="09864-102">How to: Examine the Security Context</span></span>
<span data-ttu-id="09864-103">Podczas programowania usług Windows Communication Foundation (WCF) kontekst zabezpieczenia usługi umożliwia określenie szczegółowych informacji o poświadczeniach klienta i oświadczeniach używanych do uwierzytelniania w usłudze.</span><span class="sxs-lookup"><span data-stu-id="09864-103">When programming Windows Communication Foundation (WCF) services, the service security context enables you to determine details about the client credentials and claims used to authenticate with the service.</span></span> <span data-ttu-id="09864-104">Jest to realizowane przy użyciu właściwości klasy <xref:System.ServiceModel.ServiceSecurityContext>.</span><span class="sxs-lookup"><span data-stu-id="09864-104">This is done by using the properties of the <xref:System.ServiceModel.ServiceSecurityContext> class.</span></span>  
  
 <span data-ttu-id="09864-105">Na przykład można pobrać tożsamość bieżącego klienta przy użyciu właściwości <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> lub <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="09864-105">For example, you can retrieve the identity of the current client by using the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> or the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property.</span></span> <span data-ttu-id="09864-106">Aby określić, czy klient jest anonimowy, użyj właściwości <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A>.</span><span class="sxs-lookup"><span data-stu-id="09864-106">To determine whether the client is anonymous, use the <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> property.</span></span>  
  
 <span data-ttu-id="09864-107">Można również określić, jakie oświadczenia są wykonywane w imieniu klienta przez iterację kolekcji oświadczeń we właściwości <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A>.</span><span class="sxs-lookup"><span data-stu-id="09864-107">You can also determine what claims are being made on behalf of the client by iterating through the collection of claims in the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
### <a name="to-get-the-current-security-context"></a><span data-ttu-id="09864-108">Aby uzyskać bieżący kontekst zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="09864-108">To get the current security context</span></span>  
  
- <span data-ttu-id="09864-109">Uzyskaj dostęp do właściwości statycznej <xref:System.ServiceModel.ServiceSecurityContext.Current%2A>, aby uzyskać bieżący kontekst zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="09864-109">Access the static property <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> to get the current security context.</span></span> <span data-ttu-id="09864-110">Przeanalizuj wszystkie właściwości bieżącego kontekstu z odwołania.</span><span class="sxs-lookup"><span data-stu-id="09864-110">Examine any of the properties of the current context from the reference.</span></span>  
  
### <a name="to-determine-the-identity-of-the-caller"></a><span data-ttu-id="09864-111">Aby określić tożsamość obiektu wywołującego</span><span class="sxs-lookup"><span data-stu-id="09864-111">To determine the identity of the caller</span></span>  
  
1. <span data-ttu-id="09864-112">Drukuj wartość właściwości <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> i <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="09864-112">Print the value of the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> properties.</span></span>  
  
### <a name="to-parse-the-claims-of-a-caller"></a><span data-ttu-id="09864-113">Aby przeanalizować oświadczenia obiektu wywołującego</span><span class="sxs-lookup"><span data-stu-id="09864-113">To parse the claims of a caller</span></span>  
  
1. <span data-ttu-id="09864-114">Zwróć bieżącą klasę <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="09864-114">Return the current <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span> <span data-ttu-id="09864-115">Użyj właściwości <xref:System.ServiceModel.ServiceSecurityContext.Current%2A>, aby zwrócić bieżący kontekst zabezpieczeń usługi, a następnie Zwróć `AuthorizationContext` przy użyciu właściwości <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A>.</span><span class="sxs-lookup"><span data-stu-id="09864-115">Use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to return the current service security context, then return the `AuthorizationContext` using the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
2. <span data-ttu-id="09864-116">Przeanalizuj kolekcję obiektów <xref:System.IdentityModel.Claims.ClaimSet> zwracanych przez właściwość <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> klasy <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="09864-116">Parse the collection of <xref:System.IdentityModel.Claims.ClaimSet> objects returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09864-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="09864-117">Example</span></span>  
 <span data-ttu-id="09864-118">Poniższy przykład drukuje wartości właściwości <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> i <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> bieżącego kontekstu zabezpieczeń oraz Właściwość <xref:System.IdentityModel.Claims.Claim.ClaimType%2A>, wartość zasobu dla żądania oraz Właściwość <xref:System.IdentityModel.Claims.Claim.Right%2A> każdego żądania w bieżącym kontekście zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="09864-118">The following example prints the values of the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> properties of the current security context and the <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> property, the resource value of the claim, and the <xref:System.IdentityModel.Claims.Claim.Right%2A> property of every claim in the current security context.</span></span>  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="09864-119">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="09864-119">Compiling the Code</span></span>  
 <span data-ttu-id="09864-120">Kod używa następujących przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="09864-120">The code uses the following namespaces:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.IdentityModel.Policy>  
  
- <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a><span data-ttu-id="09864-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09864-121">See also</span></span>

- [<span data-ttu-id="09864-122">Zabezpieczanie usług</span><span class="sxs-lookup"><span data-stu-id="09864-122">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="09864-123">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="09864-123">Service Identity and Authentication</span></span>](./feature-details/service-identity-and-authentication.md)
