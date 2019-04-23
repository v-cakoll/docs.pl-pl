---
title: Rozszerzanie zabezpieczeń
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
ms.openlocfilehash: 95dacf3ef975be1ddd56db747936cca35db50625
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59099641"
---
# <a name="extending-security"></a><span data-ttu-id="fc09f-102">Rozszerzanie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="fc09f-102">Extending Security</span></span>
<span data-ttu-id="fc09f-103">Aby uwzględnić nowe oświadczenia i tokeny niestandardowe, można rozszerzyć infrastruktura zabezpieczeń programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="fc09f-103">To accommodate new claim types and custom tokens, you can extend the security infrastructure of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="fc09f-104">Tematy w tej sekcji pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="fc09f-104">The topics in this section show you how this is done.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fc09f-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="fc09f-105">In This Section</span></span>  
  
 [<span data-ttu-id="fc09f-106">Niestandardowe poświadczenia i weryfikacja poświadczeń</span><span class="sxs-lookup"><span data-stu-id="fc09f-106">Custom Credential and Credential Validation</span></span>](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 <span data-ttu-id="fc09f-107">W tym artykule wyjaśniono, jak Model tożsamości jest używany podczas sprawdzania poprawności niestandardowych poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="fc09f-107">Explains how the Identity Model is used when validating custom credentials.</span></span>  
  
 [<span data-ttu-id="fc09f-108">Tokeny niestandardowe</span><span class="sxs-lookup"><span data-stu-id="fc09f-108">Custom Tokens</span></span>](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 <span data-ttu-id="fc09f-109">Wystawionych tokenów z Usługa tokenu zabezpieczającego (STS) zazwyczaj są tokeny SAML.</span><span class="sxs-lookup"><span data-stu-id="fc09f-109">Issued tokens from a Security Token Service (STS) are typically SAML tokens.</span></span> <span data-ttu-id="fc09f-110">W tym temacie wyjaśniono, jak utworzyć niestandardowy typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="fc09f-110">This topic explains how to create a custom token type.</span></span>  
  
 [<span data-ttu-id="fc09f-111">Autoryzacja niestandardowa</span><span class="sxs-lookup"><span data-stu-id="fc09f-111">Custom Authorization</span></span>](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 <span data-ttu-id="fc09f-112">Wyjaśnia, jak zaimplementować niestandardowy autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="fc09f-112">Explains how to implement custom authorization.</span></span>  
  
 [<span data-ttu-id="fc09f-113">Przesłanianie tożsamości usługi na potrzeby uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="fc09f-113">Overriding the Identity of a Service for Authentication</span></span>](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 <span data-ttu-id="fc09f-114">W tym artykule opisano sposób zastąpienia tożsamości usługi na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fc09f-114">Describes how to override the identity of a service for authentication.</span></span>  
  
 [<span data-ttu-id="fc09f-115">Instrukcje: Tworzenie niestandardowego weryfikatora tożsamości klienta</span><span class="sxs-lookup"><span data-stu-id="fc09f-115">How to: Create a Custom Client Identity Verifier</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 <span data-ttu-id="fc09f-116">Pokazuje, jak w celu weryfikowania tożsamości niestandardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="fc09f-116">Demonstrates how to validate a custom endpoint identity.</span></span>  
  
 [<span data-ttu-id="fc09f-117">Instrukcje: Używanie osobnych certyfikatów X.509 do podpisywania i szyfrowania</span><span class="sxs-lookup"><span data-stu-id="fc09f-117">How to: Use Separate X.509 Certificates for Signing and Encryption</span></span>](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 <span data-ttu-id="fc09f-118">Komunikaty są zwykle podpisane i szyfrowane za pomocą jednego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="fc09f-118">Messages are typically signed and encrypted with a single certificate.</span></span> <span data-ttu-id="fc09f-119">W tym temacie wyjaśniono, jak dwa certyfikaty mogą być używane, gdy jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="fc09f-119">This topic explains how two certificates can be used, when required.</span></span>  
  
 [<span data-ttu-id="fc09f-120">Instrukcje: Zmienianie dostawcy kryptograficznego dla klucza prywatnego certyfikatu X.509</span><span class="sxs-lookup"><span data-stu-id="fc09f-120">How to: Change the Cryptographic Provider for an X.509 Certificate's Private Key</span></span>](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 <span data-ttu-id="fc09f-121">Wyjaśnia, jak zmienić dostawcy usług kryptograficznych, używane do zapewnienia klucza prywatnego certyfikatu X.509 oraz integrować dostawcę w ramach usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="fc09f-121">Explains how to change the cryptographic provider used to provide an X.509 certificate's private key and how to integrate the provider into the Windows Communication Foundation (WCF) framework.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fc09f-122">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="fc09f-122">Reference</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a><span data-ttu-id="fc09f-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="fc09f-123">Related Sections</span></span>  
 [<span data-ttu-id="fc09f-124">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="fc09f-124">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [<span data-ttu-id="fc09f-125">Podstawy programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="fc09f-125">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## <a name="see-also"></a><span data-ttu-id="fc09f-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc09f-126">See also</span></span>

- [<span data-ttu-id="fc09f-127">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="fc09f-127">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
