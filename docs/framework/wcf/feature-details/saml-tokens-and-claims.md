---
title: "Tokeny i oświadczenia języka SAML"
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
helpviewer_keywords:
- WCF, federation
- federation
- issued tokens
- SAML token
ms.assetid: 930b6e34-9eab-4e95-826c-4e06659bb977
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e1d797b7c86f57f4f9cf4d604e264d3534a79bf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="saml-tokens-and-claims"></a><span data-ttu-id="368bd-102">Tokeny i oświadczenia języka SAML</span><span class="sxs-lookup"><span data-stu-id="368bd-102">SAML Tokens and Claims</span></span>
<span data-ttu-id="368bd-103">Zabezpieczenia potwierdzenia Markup Language (SAML) *tokenów* są oświadczenia reprezentacji XML.</span><span class="sxs-lookup"><span data-stu-id="368bd-103">Security Assertions Markup Language (SAML) *tokens* are XML representations of claims.</span></span> <span data-ttu-id="368bd-104">Domyślnie tokeny SAML [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] są używane w scenariuszach zabezpieczeń *wystawionych tokenów*.</span><span class="sxs-lookup"><span data-stu-id="368bd-104">By default, SAML tokens [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uses in federated security scenarios are *issued tokens*.</span></span>  
  
 <span data-ttu-id="368bd-105">Tokeny SAML wykonania instrukcji, które są zestawy oświadczeń przez jedną jednostkę o innej jednostki.</span><span class="sxs-lookup"><span data-stu-id="368bd-105">SAML tokens carry statements that are sets of claims made by one entity about another entity.</span></span> <span data-ttu-id="368bd-106">Na przykład w scenariuszach zabezpieczeń instrukcje są wykonywane przez usługę tokenu zabezpieczającego o użytkowniku w systemie.</span><span class="sxs-lookup"><span data-stu-id="368bd-106">For example, in federated security scenarios, the statements are made by a security token service about a user in the system.</span></span> <span data-ttu-id="368bd-107">Usługa tokenu zabezpieczającego podpisuje token SAML, aby wskazać wiarygodności instrukcji zawartych w tokenie.</span><span class="sxs-lookup"><span data-stu-id="368bd-107">The security token service signs the SAML token to indicate the veracity of the statements contained in the token.</span></span> <span data-ttu-id="368bd-108">Ponadto tokenu SAML jest skojarzony z materiału klucza kryptograficznego, gdy użytkownik tokenu SAML okaże informacje dotyczące.</span><span class="sxs-lookup"><span data-stu-id="368bd-108">In addition, the SAML token is associated with cryptographic key material that the user of the SAML token proves knowledge of.</span></span> <span data-ttu-id="368bd-109">To potwierdzenie spełnia uzależniona, która była tokenu SAML, w rzeczywistości wystawiony dla tego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="368bd-109">This proof satisfies the relying party that the SAML token was, in fact, issued to that user.</span></span> <span data-ttu-id="368bd-110">Na przykład w typowy scenariusz:</span><span class="sxs-lookup"><span data-stu-id="368bd-110">For example, in a typical scenario:</span></span>  
  
1.  <span data-ttu-id="368bd-111">Klient żąda tokenu SAML z usługą tokenu zabezpieczeń uwierzytelniania z usługą tokenu zabezpieczeń przy użyciu poświadczeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="368bd-111">A client requests a SAML token from a security token service, authenticating to that security token service by using Windows credentials.</span></span>  
  
2.  <span data-ttu-id="368bd-112">Usługa tokenu zabezpieczającego wystawia SAML token do klienta.</span><span class="sxs-lookup"><span data-stu-id="368bd-112">The security token service issues a SAML token to the client.</span></span> <span data-ttu-id="368bd-113">Tokenu SAML jest podpisany przy użyciu certyfikatu skojarzonego z usługą tokenu zabezpieczeń i zawiera klucz potwierdzający zaszyfrowane dla usługi docelowej.</span><span class="sxs-lookup"><span data-stu-id="368bd-113">The SAML token is signed with a certificate associated with the security token service and contains a proof key encrypted for the target service.</span></span>  
  
3.  <span data-ttu-id="368bd-114">Klient odbiera również kopię *klucz potwierdzający*.</span><span class="sxs-lookup"><span data-stu-id="368bd-114">The client also receives a copy of the *proof key*.</span></span> <span data-ttu-id="368bd-115">Klient przedstawia tokenu SAML z usługą aplikacji ( *jednostki uzależnionej*) i podpisuje wiadomości z tego klucza potwierdzającego.</span><span class="sxs-lookup"><span data-stu-id="368bd-115">The client then presents the SAML token to the application service (the *relying party*) and signs the message with that proof key.</span></span>  
  
4.  <span data-ttu-id="368bd-116">Podpis za pośrednictwem tokenu SAML informuje jednostki uzależnionej, czy usługa tokenu zabezpieczającego wystawiony token.</span><span class="sxs-lookup"><span data-stu-id="368bd-116">The signature over the SAML token tells the relying party that the security token service issued the token.</span></span> <span data-ttu-id="368bd-117">Podpisu wiadomości utworzone za pomocą klucza potwierdzającego informuje jednostki uzależnionej, czy token został wystawiony dla klienta.</span><span class="sxs-lookup"><span data-stu-id="368bd-117">The message signature created with the proof key tells the relying party that the token was issued to the client.</span></span>  
  
## <a name="from-claims-to-samlattributes"></a><span data-ttu-id="368bd-118">Z oświadczeń do SamlAttributes</span><span class="sxs-lookup"><span data-stu-id="368bd-118">From Claims to SamlAttributes</span></span>  
 <span data-ttu-id="368bd-119">W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], instrukcje w tokenach SAML są modelowane jako <xref:System.IdentityModel.Tokens.SamlAttribute> obiektów, które mogą być umieszczane bezpośrednio z <xref:System.IdentityModel.Claims.Claim> obiekty dostarczane <xref:System.IdentityModel.Claims.Claim> obiekt ma <xref:System.IdentityModel.Claims.Claim.Right%2A> właściwość <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> i <xref:System.IdentityModel.Claims.Claim.Resource%2A> Właściwość jest typu <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="368bd-119">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], statements in SAML tokens are modeled as <xref:System.IdentityModel.Tokens.SamlAttribute> objects, which can be populated directly from <xref:System.IdentityModel.Claims.Claim> objects, provided the <xref:System.IdentityModel.Claims.Claim> object has a <xref:System.IdentityModel.Claims.Claim.Right%2A> property of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> and the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property is of type <xref:System.String>.</span></span> <span data-ttu-id="368bd-120">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="368bd-120">For example:</span></span>  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
>  <span data-ttu-id="368bd-121">Gdy tokenów SAML są serializowane w wiadomości, gdy zostaną wystawione przez usługi tokenu zabezpieczającego lub mają być przedstawiane przez klientów do usług w ramach uwierzytelniania, maksymalny przydział rozmiaru komunikatu musi być wystarczająco duży, aby zmieścił się w tokenie SAML i inne części wiadomości.</span><span class="sxs-lookup"><span data-stu-id="368bd-121">When SAML tokens are serialized in messages, either when they are issued by a security token service or when they are presented by clients to services as part of authentication, the maximum message size quota must be sufficiently large to accommodate the SAML token and the other message parts.</span></span> <span data-ttu-id="368bd-122">W przypadku normalnych przydziały rozmiar komunikatu domyślne są wystarczające.</span><span class="sxs-lookup"><span data-stu-id="368bd-122">In normal cases, the default message size quotas are sufficient.</span></span> <span data-ttu-id="368bd-123">Jednak w przypadku, gdy tokenu SAML jest duży, ponieważ zawiera on setki oświadczenia, konieczne może być zwiększyć przydziały w celu uwzględnienia Zserializowany token.</span><span class="sxs-lookup"><span data-stu-id="368bd-123">However, in cases where a SAML token is large because it contains hundreds of claims, you may need to increase the quotas to accommodate the serialized token.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="368bd-124">[Zagadnienia dotyczące zabezpieczeń dla danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span><span class="sxs-lookup"><span data-stu-id="368bd-124"> [Security Considerations for Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span></span>  
  
## <a name="from-samlattributes-to-claims"></a><span data-ttu-id="368bd-125">Z SamlAttributes oświadczeń</span><span class="sxs-lookup"><span data-stu-id="368bd-125">From SamlAttributes to Claims</span></span>  
 <span data-ttu-id="368bd-126">Po odebraniu wiadomości tokeny SAML, różne oświadczenia w tokenie SAML są włączone do <xref:System.IdentityModel.Policy.IAuthorizationPolicy> obiektów, które są umieszczane w <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="368bd-126">When SAML tokens are received in messages, the various statements in the SAML token are turned into <xref:System.IdentityModel.Policy.IAuthorizationPolicy> objects that are placed into the <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="368bd-127">Oświadczenia z każdym instrukcji SAML są zwracane przez <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> właściwość <xref:System.IdentityModel.Policy.AuthorizationContext> i można zbadać w celu określenia, czy do uwierzytelniania i autoryzacji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="368bd-127">The claims from each SAML statement are returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> and can be examined to determine whether to authenticate and authorize the user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="368bd-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="368bd-128">See Also</span></span>  
 <xref:System.IdentityModel.Policy.AuthorizationContext>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 <xref:System.IdentityModel.Claims.ClaimSet>  
 [<span data-ttu-id="368bd-129">Federacyjna</span><span class="sxs-lookup"><span data-stu-id="368bd-129">Federation</span></span>](../../../../docs/framework/wcf/feature-details/federation.md)  
 [<span data-ttu-id="368bd-130">Porady: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="368bd-130">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="368bd-131">Porady: Konfigurowanie poświadczeń usługi federacyjnej</span><span class="sxs-lookup"><span data-stu-id="368bd-131">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [<span data-ttu-id="368bd-132">Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości</span><span class="sxs-lookup"><span data-stu-id="368bd-132">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="368bd-133">Oświadczenia i tokeny</span><span class="sxs-lookup"><span data-stu-id="368bd-133">Claims and Tokens</span></span>](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)  
 [<span data-ttu-id="368bd-134">Tworzenie oświadczenia i wartości zasobów</span><span class="sxs-lookup"><span data-stu-id="368bd-134">Claim Creation and Resource Values</span></span>](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)  
 [<span data-ttu-id="368bd-135">Porady: tworzenie oświadczenia niestandardowego</span><span class="sxs-lookup"><span data-stu-id="368bd-135">How to: Create a Custom Claim</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
