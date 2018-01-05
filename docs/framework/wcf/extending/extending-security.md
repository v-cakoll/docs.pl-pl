---
title: "Rozszerzanie zabezpieczeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
caps.latest.revision: "23"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: ecbbaac0023ca528967abe2cb60c3d790772fb2e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="extending-security"></a><span data-ttu-id="85b3a-102">Rozszerzanie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="85b3a-102">Extending Security</span></span>
<span data-ttu-id="85b3a-103">Aby uwzględnić nowe typy oświadczeń i tokeny niestandardowe, można rozszerzyć infrastruktura zabezpieczeń [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85b3a-103">To accommodate new claim types and custom tokens, you can extend the security infrastructure of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="85b3a-104">Tematy w tej sekcji opisano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="85b3a-104">The topics in this section show you how this is done.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="85b3a-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="85b3a-105">In This Section</span></span>  
 [<span data-ttu-id="85b3a-106">Architektura zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="85b3a-106">Security Architecture</span></span>](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f)  
 <span data-ttu-id="85b3a-107">Przeprowadzi Cię przez architekturę [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczeń systemu.</span><span class="sxs-lookup"><span data-stu-id="85b3a-107">Walks through the architecture of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security system.</span></span>  
  
 [<span data-ttu-id="85b3a-108">Niestandardowe poświadczenia i weryfikacja poświadczeń</span><span class="sxs-lookup"><span data-stu-id="85b3a-108">Custom Credential and Credential Validation</span></span>](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 <span data-ttu-id="85b3a-109">Wyjaśniono, jak Model tożsamości jest używany podczas sprawdzania poprawności niestandardowych poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="85b3a-109">Explains how the Identity Model is used when validating custom credentials.</span></span>  
  
 [<span data-ttu-id="85b3a-110">Tokeny niestandardowe</span><span class="sxs-lookup"><span data-stu-id="85b3a-110">Custom Tokens</span></span>](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 <span data-ttu-id="85b3a-111">Wystawione tokeny z zabezpieczeń tokenu usługi (STS) są zwykle tokeny SAML.</span><span class="sxs-lookup"><span data-stu-id="85b3a-111">Issued tokens from a Security Token Service (STS) are typically SAML tokens.</span></span> <span data-ttu-id="85b3a-112">W tym temacie wyjaśniono, jak utworzyć niestandardowy typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="85b3a-112">This topic explains how to create a custom token type.</span></span>  
  
 [<span data-ttu-id="85b3a-113">Autoryzacja niestandardowa</span><span class="sxs-lookup"><span data-stu-id="85b3a-113">Custom Authorization</span></span>](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 <span data-ttu-id="85b3a-114">Wyjaśniono, jak wdrożyć przeprowadzania niestandardowej autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="85b3a-114">Explains how to implement custom authorization.</span></span>  
  
 [<span data-ttu-id="85b3a-115">Przesłanianie tożsamości usługi na potrzeby uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="85b3a-115">Overriding the Identity of a Service for Authentication</span></span>](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 <span data-ttu-id="85b3a-116">Opisuje sposób zastępowania tożsamości usługi na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="85b3a-116">Describes how to override the identity of a service for authentication.</span></span>  
  
 [<span data-ttu-id="85b3a-117">Instrukcje: tworzenie niestandardowego weryfikatora tożsamości klienta</span><span class="sxs-lookup"><span data-stu-id="85b3a-117">How to: Create a Custom Client Identity Verifier</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 <span data-ttu-id="85b3a-118">Pokazuje, jak można sprawdzić poprawności tożsamości niestandardowej punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="85b3a-118">Demonstrates how to validate a custom endpoint identity.</span></span>  
  
 [<span data-ttu-id="85b3a-119">Instrukcje: używanie osobnych certyfikatów X.509 do podpisywania i szyfrowania</span><span class="sxs-lookup"><span data-stu-id="85b3a-119">How to: Use Separate X.509 Certificates for Signing and Encryption</span></span>](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 <span data-ttu-id="85b3a-120">Komunikaty są zwykle podpisane i zaszyfrowane za pomocą jednego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="85b3a-120">Messages are typically signed and encrypted with a single certificate.</span></span> <span data-ttu-id="85b3a-121">W tym temacie opisano sposób dwa certyfikaty mogą być używane, na żądanie.</span><span class="sxs-lookup"><span data-stu-id="85b3a-121">This topic explains how two certificates can be used, when required.</span></span>  
  
 [<span data-ttu-id="85b3a-122">Instrukcje: zmienianie dostawcy kryptograficznego dla klucza prywatnego certyfikatu X.509</span><span class="sxs-lookup"><span data-stu-id="85b3a-122">How to: Change the Cryptographic Provider for an X.509 Certificate's Private Key</span></span>](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 <span data-ttu-id="85b3a-123">Wyjaśniono, jak zmienić dostawcy usług kryptograficznych, umożliwiające uzyskanie klucza prywatnego certyfikatu X.509 i integrowanie dostawcy do [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] framework.</span><span class="sxs-lookup"><span data-stu-id="85b3a-123">Explains how to change the cryptographic provider used to provide an X.509 certificate's private key and how to integrate the provider into the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] framework.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="85b3a-124">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="85b3a-124">Reference</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a><span data-ttu-id="85b3a-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="85b3a-125">Related Sections</span></span>  
 [<span data-ttu-id="85b3a-126">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="85b3a-126">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [<span data-ttu-id="85b3a-127">Podstawy programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="85b3a-127">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## <a name="see-also"></a><span data-ttu-id="85b3a-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85b3a-128">See Also</span></span>  
 [<span data-ttu-id="85b3a-129">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="85b3a-129">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
