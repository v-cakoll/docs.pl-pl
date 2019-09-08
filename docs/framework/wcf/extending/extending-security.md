---
title: Rozszerzanie zabezpieczeń
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
ms.openlocfilehash: 45216493a3afa23f24a085964a2c43e19b197d4b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797123"
---
# <a name="extending-security"></a><span data-ttu-id="89949-102">Rozszerzanie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="89949-102">Extending Security</span></span>
<span data-ttu-id="89949-103">W celu uwzględnienia nowych typów i tokenów niestandardowych można zwiększyć infrastrukturę zabezpieczeń Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="89949-103">To accommodate new claim types and custom tokens, you can extend the security infrastructure of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="89949-104">W tematach w tej sekcji pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="89949-104">The topics in this section show you how this is done.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="89949-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="89949-105">In This Section</span></span>  
  
 [<span data-ttu-id="89949-106">Niestandardowe poświadczenia i weryfikacja poświadczeń</span><span class="sxs-lookup"><span data-stu-id="89949-106">Custom Credential and Credential Validation</span></span>](custom-credential-and-credential-validation.md)  
 <span data-ttu-id="89949-107">Wyjaśnia, jak model tożsamości jest używany podczas sprawdzania poprawności poświadczeń niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="89949-107">Explains how the Identity Model is used when validating custom credentials.</span></span>  
  
 [<span data-ttu-id="89949-108">Tokeny niestandardowe</span><span class="sxs-lookup"><span data-stu-id="89949-108">Custom Tokens</span></span>](custom-tokens.md)  
 <span data-ttu-id="89949-109">Wystawione tokeny z usługi tokenu zabezpieczającego (STS) są zazwyczaj tokenami SAML.</span><span class="sxs-lookup"><span data-stu-id="89949-109">Issued tokens from a Security Token Service (STS) are typically SAML tokens.</span></span> <span data-ttu-id="89949-110">W tym temacie wyjaśniono, jak utworzyć niestandardowy typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="89949-110">This topic explains how to create a custom token type.</span></span>  
  
 [<span data-ttu-id="89949-111">Autoryzacja niestandardowa</span><span class="sxs-lookup"><span data-stu-id="89949-111">Custom Authorization</span></span>](custom-authorization.md)  
 <span data-ttu-id="89949-112">Wyjaśnia, jak zaimplementować autoryzację niestandardową.</span><span class="sxs-lookup"><span data-stu-id="89949-112">Explains how to implement custom authorization.</span></span>  
  
 [<span data-ttu-id="89949-113">Przesłanianie tożsamości usługi na potrzeby uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="89949-113">Overriding the Identity of a Service for Authentication</span></span>](overriding-the-identity-of-a-service-for-authentication.md)  
 <span data-ttu-id="89949-114">Opisuje sposób przesłania tożsamości usługi na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="89949-114">Describes how to override the identity of a service for authentication.</span></span>  
  
 [<span data-ttu-id="89949-115">Instrukcje: Tworzenie niestandardowego weryfikatora tożsamości klienta</span><span class="sxs-lookup"><span data-stu-id="89949-115">How to: Create a Custom Client Identity Verifier</span></span>](how-to-create-a-custom-client-identity-verifier.md)  
 <span data-ttu-id="89949-116">Pokazuje, jak zweryfikować tożsamość niestandardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="89949-116">Demonstrates how to validate a custom endpoint identity.</span></span>  
  
 [<span data-ttu-id="89949-117">Instrukcje: Używanie osobnych certyfikatów X. 509 do podpisywania i szyfrowania</span><span class="sxs-lookup"><span data-stu-id="89949-117">How to: Use Separate X.509 Certificates for Signing and Encryption</span></span>](how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 <span data-ttu-id="89949-118">Komunikaty są zwykle podpisywane i szyfrowane za pomocą jednego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="89949-118">Messages are typically signed and encrypted with a single certificate.</span></span> <span data-ttu-id="89949-119">W tym temacie wyjaśniono, w jaki sposób mogą być używane dwa certyfikaty, jeśli jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="89949-119">This topic explains how two certificates can be used, when required.</span></span>  
  
 [<span data-ttu-id="89949-120">Instrukcje: Zmień dostawcę usług kryptograficznych dla klucza prywatnego certyfikatu X. 509</span><span class="sxs-lookup"><span data-stu-id="89949-120">How to: Change the Cryptographic Provider for an X.509 Certificate's Private Key</span></span>](change-cryptographic-provider-x509-certificate-private-key.md)  
 <span data-ttu-id="89949-121">Wyjaśnia, jak zmienić dostawcę usług kryptograficznych używany do udostępniania klucza prywatnego certyfikatu X. 509 oraz jak zintegrować dostawcę z platformą Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="89949-121">Explains how to change the cryptographic provider used to provide an X.509 certificate's private key and how to integrate the provider into the Windows Communication Foundation (WCF) framework.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="89949-122">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="89949-122">Reference</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a><span data-ttu-id="89949-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="89949-123">Related Sections</span></span>  
 [<span data-ttu-id="89949-124">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="89949-124">Security</span></span>](../feature-details/security.md)  
  
 [<span data-ttu-id="89949-125">Podstawy programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="89949-125">Basic WCF Programming</span></span>](../basic-wcf-programming.md)  
  
## <a name="see-also"></a><span data-ttu-id="89949-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89949-126">See also</span></span>

- [<span data-ttu-id="89949-127">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="89949-127">Security Overview</span></span>](../feature-details/security-overview.md)
