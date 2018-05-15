---
title: Rozszerzanie zabezpieczeń
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 94aefe80674c5b4ec6fcce6a41d9b68e093f4262
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="extending-security"></a><span data-ttu-id="14627-102">Rozszerzanie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="14627-102">Extending Security</span></span>
<span data-ttu-id="14627-103">Aby uwzględnić nowe typy oświadczeń i tokeny niestandardowe, można rozszerzyć infrastruktury zabezpieczeń programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="14627-103">To accommodate new claim types and custom tokens, you can extend the security infrastructure of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="14627-104">Tematy w tej sekcji opisano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="14627-104">The topics in this section show you how this is done.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="14627-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="14627-105">In This Section</span></span>  
 [<span data-ttu-id="14627-106">Architektura zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="14627-106">Security Architecture</span></span>](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)  
 <span data-ttu-id="14627-107">Przeprowadzi Cię przez architekturę WCF systemu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="14627-107">Walks through the architecture of the WCF security system.</span></span>  
  
 [<span data-ttu-id="14627-108">Niestandardowe poświadczenia i weryfikacja poświadczeń</span><span class="sxs-lookup"><span data-stu-id="14627-108">Custom Credential and Credential Validation</span></span>](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 <span data-ttu-id="14627-109">Wyjaśniono, jak Model tożsamości jest używany podczas sprawdzania poprawności niestandardowych poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="14627-109">Explains how the Identity Model is used when validating custom credentials.</span></span>  
  
 [<span data-ttu-id="14627-110">Tokeny niestandardowe</span><span class="sxs-lookup"><span data-stu-id="14627-110">Custom Tokens</span></span>](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 <span data-ttu-id="14627-111">Wystawione tokeny z zabezpieczeń tokenu usługi (STS) są zwykle tokeny SAML.</span><span class="sxs-lookup"><span data-stu-id="14627-111">Issued tokens from a Security Token Service (STS) are typically SAML tokens.</span></span> <span data-ttu-id="14627-112">W tym temacie wyjaśniono, jak utworzyć niestandardowy typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="14627-112">This topic explains how to create a custom token type.</span></span>  
  
 [<span data-ttu-id="14627-113">Autoryzacja niestandardowa</span><span class="sxs-lookup"><span data-stu-id="14627-113">Custom Authorization</span></span>](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 <span data-ttu-id="14627-114">Wyjaśniono, jak wdrożyć przeprowadzania niestandardowej autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="14627-114">Explains how to implement custom authorization.</span></span>  
  
 [<span data-ttu-id="14627-115">Przesłanianie tożsamości usługi na potrzeby uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="14627-115">Overriding the Identity of a Service for Authentication</span></span>](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 <span data-ttu-id="14627-116">Opisuje sposób zastępowania tożsamości usługi na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="14627-116">Describes how to override the identity of a service for authentication.</span></span>  
  
 [<span data-ttu-id="14627-117">Instrukcje: tworzenie niestandardowego weryfikatora tożsamości klienta</span><span class="sxs-lookup"><span data-stu-id="14627-117">How to: Create a Custom Client Identity Verifier</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 <span data-ttu-id="14627-118">Pokazuje, jak można sprawdzić poprawności tożsamości niestandardowej punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="14627-118">Demonstrates how to validate a custom endpoint identity.</span></span>  
  
 [<span data-ttu-id="14627-119">Instrukcje: używanie osobnych certyfikatów X.509 do podpisywania i szyfrowania</span><span class="sxs-lookup"><span data-stu-id="14627-119">How to: Use Separate X.509 Certificates for Signing and Encryption</span></span>](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 <span data-ttu-id="14627-120">Komunikaty są zwykle podpisane i zaszyfrowane za pomocą jednego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="14627-120">Messages are typically signed and encrypted with a single certificate.</span></span> <span data-ttu-id="14627-121">W tym temacie opisano sposób dwa certyfikaty mogą być używane, na żądanie.</span><span class="sxs-lookup"><span data-stu-id="14627-121">This topic explains how two certificates can be used, when required.</span></span>  
  
 [<span data-ttu-id="14627-122">Instrukcje: zmienianie dostawcy kryptograficznego dla klucza prywatnego certyfikatu X.509</span><span class="sxs-lookup"><span data-stu-id="14627-122">How to: Change the Cryptographic Provider for an X.509 Certificate's Private Key</span></span>](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 <span data-ttu-id="14627-123">Wyjaśniono, jak zmienić dostawcy usług kryptograficznych, umożliwiające uzyskanie klucza prywatnego certyfikatu X.509 i sposobu integracji dostawcę w ramach usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="14627-123">Explains how to change the cryptographic provider used to provide an X.509 certificate's private key and how to integrate the provider into the Windows Communication Foundation (WCF) framework.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="14627-124">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="14627-124">Reference</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a><span data-ttu-id="14627-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="14627-125">Related Sections</span></span>  
 [<span data-ttu-id="14627-126">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="14627-126">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [<span data-ttu-id="14627-127">Podstawy programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="14627-127">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## <a name="see-also"></a><span data-ttu-id="14627-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14627-128">See Also</span></span>  
 [<span data-ttu-id="14627-129">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="14627-129">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
