---
title: Protokoły zabezpieczeń wersja 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
ms.openlocfilehash: 2014e1f6f8fefa89ed44bd820c3712617ff51470
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184524"
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="76be3-102">Protokoły zabezpieczeń wersja 1.0</span><span class="sxs-lookup"><span data-stu-id="76be3-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="76be3-103">Protokoły zabezpieczeń usług sieci Web zapewniają mechanizmy zabezpieczeń usług sieci Web, które obejmują wszystkie istniejące wymagania dotyczące zabezpieczeń obsługi wiadomości w przedsiębiorstwie.</span><span class="sxs-lookup"><span data-stu-id="76be3-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="76be3-104">W tej sekcji opisano szczegóły programu Windows Communication Foundation (WCF) <xref:System.ServiceModel.Channels.SecurityBindingElement>w wersji 1.0 (zaimplementowane w ) dla następujących protokołów zabezpieczeń usług sieci Web.</span><span class="sxs-lookup"><span data-stu-id="76be3-104">This section describes the Windows Communication Foundation (WCF) version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="76be3-105">Specyfikacja/dokument</span><span class="sxs-lookup"><span data-stu-id="76be3-105">Specification/Document</span></span>|<span data-ttu-id="76be3-106">Link</span><span class="sxs-lookup"><span data-stu-id="76be3-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="76be3-107">WSS: Zabezpieczenia wiadomości SOAP 1.0</span><span class="sxs-lookup"><span data-stu-id="76be3-107">WSS: SOAP Message Security 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|
|<span data-ttu-id="76be3-108">WSS: Profil tokenu użytkownika 1.0</span><span class="sxs-lookup"><span data-stu-id="76be3-108">WSS: Username Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="76be3-109">WSS: Profil tokenu X509 1.0</span><span class="sxs-lookup"><span data-stu-id="76be3-109">WSS: X509 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|
|<span data-ttu-id="76be3-110">WSS: SAML 1.1 Profil tokenu 1.0</span><span class="sxs-lookup"><span data-stu-id="76be3-110">WSS: SAML 1.1 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|
|<span data-ttu-id="76be3-111">WSS: Zabezpieczenia wiadomości SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="76be3-111">WSS: SOAP Message Security 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|
|<span data-ttu-id="76be3-112">Profil tokenu nazwy użytkownika WSS 1.1</span><span class="sxs-lookup"><span data-stu-id="76be3-112">WSS Username Token Profile 1.1</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="76be3-113">WSS: Profil tokenu X.509 1.1</span><span class="sxs-lookup"><span data-stu-id="76be3-113">WSS: X.509 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|
|<span data-ttu-id="76be3-114">WSS: Profil tokenu Protokołu Kerberos 1.1</span><span class="sxs-lookup"><span data-stu-id="76be3-114">WSS: Kerberos Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|
|<span data-ttu-id="76be3-115">WSS: SAML 1.1 Profil tokenu 1.1</span><span class="sxs-lookup"><span data-stu-id="76be3-115">WSS: SAML 1.1 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|
|<span data-ttu-id="76be3-116">Rozmowa w zabezpieczeniu WS</span><span class="sxs-lookup"><span data-stu-id="76be3-116">WS-Secure Conversation</span></span>|<https://specs.xmlsoap.org/ws/2005/02/sc/WS-SecureConversation.pdf>|
|<span data-ttu-id="76be3-117">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="76be3-117">WS-Trust</span></span>|<https://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf>|
|<span data-ttu-id="76be3-118">Uwaga aplikacji:</span><span class="sxs-lookup"><span data-stu-id="76be3-118">Application Note:</span></span><br /><br /> <span data-ttu-id="76be3-119">Korzystanie z funkcji zaufania WS dla uzgadniania TLS</span><span class="sxs-lookup"><span data-stu-id="76be3-119">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="76be3-120">Do opublikowania</span><span class="sxs-lookup"><span data-stu-id="76be3-120">To be published</span></span>|  
|<span data-ttu-id="76be3-121">Uwaga aplikacji:</span><span class="sxs-lookup"><span data-stu-id="76be3-121">Application Note:</span></span><br /><br /> <span data-ttu-id="76be3-122">Korzystanie z funkcji WS-Trust dla usługi SPNEGO</span><span class="sxs-lookup"><span data-stu-id="76be3-122">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="76be3-123">Do opublikowania</span><span class="sxs-lookup"><span data-stu-id="76be3-123">To be published</span></span>|  
|<span data-ttu-id="76be3-124">Uwaga aplikacji:</span><span class="sxs-lookup"><span data-stu-id="76be3-124">Application Note:</span></span><br /><br /> <span data-ttu-id="76be3-125">Usługi sieci Web adresujące odwołania do punktów końcowych i tożsamość</span><span class="sxs-lookup"><span data-stu-id="76be3-125">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="76be3-126">Do opublikowania</span><span class="sxs-lookup"><span data-stu-id="76be3-126">To be published</span></span>|  
|<span data-ttu-id="76be3-127">WS-SecurityPolicy 1.1</span><span class="sxs-lookup"><span data-stu-id="76be3-127">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="76be3-128">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="76be3-128">(2005/07)</span></span>|<https://specs.xmlsoap.org/ws/2005/07/securitypolicy/ws-securitypolicy.pdf><br /><br /> <span data-ttu-id="76be3-129">zmieniona [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) przedłożona Komitetowi Techniczneemu OASIS WS-SX</span><span class="sxs-lookup"><span data-stu-id="76be3-129">as amended by [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) submitted to OASIS WS-SX Technical Committee</span></span> |  
  
 <span data-ttu-id="76be3-130">WCF, wersja 1, zawiera 17 trybów uwierzytelniania, które mogą być używane jako podstawa konfiguracji zabezpieczeń usług sieci Web.</span><span class="sxs-lookup"><span data-stu-id="76be3-130">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="76be3-131">Każdy tryb jest zoptymalizowany pod kątem wspólnego zestawu wymagań dotyczących wdrażania, takich jak:</span><span class="sxs-lookup"><span data-stu-id="76be3-131">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
- <span data-ttu-id="76be3-132">Poświadczenia używane do uwierzytelniania klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="76be3-132">Credentials used to authenticate client and service.</span></span>  
  
- <span data-ttu-id="76be3-133">Mechanizmy ochrony bezpieczeństwa wiadomości lub transportu.</span><span class="sxs-lookup"><span data-stu-id="76be3-133">Message or transport security protection mechanisms.</span></span>  
  
- <span data-ttu-id="76be3-134">Wzorce wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="76be3-134">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="76be3-135">Tryb uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="76be3-135">Authentication Mode</span></span>|<span data-ttu-id="76be3-136">Uwierzytelnianie klienta</span><span class="sxs-lookup"><span data-stu-id="76be3-136">Client Authentication</span></span>|<span data-ttu-id="76be3-137">Uwierzytelnianie serwera</span><span class="sxs-lookup"><span data-stu-id="76be3-137">Server Authentication</span></span>|<span data-ttu-id="76be3-138">Tryb</span><span class="sxs-lookup"><span data-stu-id="76be3-138">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="76be3-139">Nazwa użytkownikaTransportuTransport</span><span class="sxs-lookup"><span data-stu-id="76be3-139">UserNameOverTransport</span></span>|<span data-ttu-id="76be3-140">Nazwa użytkownika/hasło</span><span class="sxs-lookup"><span data-stu-id="76be3-140">User name/password</span></span>|<span data-ttu-id="76be3-141">X509</span><span class="sxs-lookup"><span data-stu-id="76be3-141">X509</span></span>|<span data-ttu-id="76be3-142">Transport</span><span class="sxs-lookup"><span data-stu-id="76be3-142">Transport</span></span>|  
|<span data-ttu-id="76be3-143">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="76be3-143">CertificateOverTransport</span></span>|<span data-ttu-id="76be3-144">X509</span><span class="sxs-lookup"><span data-stu-id="76be3-144">X509</span></span>|<span data-ttu-id="76be3-145">X509</span><span class="sxs-lookup"><span data-stu-id="76be3-145">X509</span></span>|<span data-ttu-id="76be3-146">Transport</span><span class="sxs-lookup"><span data-stu-id="76be3-146">Transport</span></span>|  
|<span data-ttu-id="76be3-147">Protokół KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="76be3-147">KerberosOverTransport</span></span>|<span data-ttu-id="76be3-148">Windows</span><span class="sxs-lookup"><span data-stu-id="76be3-148">Windows</span></span>|<span data-ttu-id="76be3-149">X509</span><span class="sxs-lookup"><span data-stu-id="76be3-149">X509</span></span>|<span data-ttu-id="76be3-150">Transport</span><span class="sxs-lookup"><span data-stu-id="76be3-150">Transport</span></span>|  
|<span data-ttu-id="76be3-151">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="76be3-151">IssuedTokenOverTransport</span></span>|<span data-ttu-id="76be3-152">Federacyjni</span><span class="sxs-lookup"><span data-stu-id="76be3-152">Federated</span></span>|<span data-ttu-id="76be3-153">X509</span><span class="sxs-lookup"><span data-stu-id="76be3-153">X509</span></span>|<span data-ttu-id="76be3-154">Transport</span><span class="sxs-lookup"><span data-stu-id="76be3-154">Transport</span></span>|  
|<span data-ttu-id="76be3-155">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="76be3-155">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="76be3-156">Wynegocjowane SSPI systemu Windows</span><span class="sxs-lookup"><span data-stu-id="76be3-156">Windows Sspi Negotiated</span></span>|<span data-ttu-id="76be3-157">Wynegocjowane SSPI systemu Windows</span><span class="sxs-lookup"><span data-stu-id="76be3-157">Windows Sspi Negotiated</span></span>|<span data-ttu-id="76be3-158">Transport</span><span class="sxs-lookup"><span data-stu-id="76be3-158">Transport</span></span>|  
|<span data-ttu-id="76be3-159">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="76be3-159">AnonymousForCertificate</span></span>|<span data-ttu-id="76be3-160">Brak</span><span class="sxs-lookup"><span data-stu-id="76be3-160">None</span></span>|<span data-ttu-id="76be3-161">X509</span><span class="sxs-lookup"><span data-stu-id="76be3-161">X509</span></span>|<span data-ttu-id="76be3-162">Komunikat</span><span class="sxs-lookup"><span data-stu-id="76be3-162">Message</span></span>|  
|<span data-ttu-id="76be3-163">Certyfikat UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="76be3-163">UserNameForCertificate</span></span>|<span data-ttu-id="76be3-164">Nazwa użytkownika/hasło</span><span class="sxs-lookup"><span data-stu-id="76be3-164">User name/password</span></span>|<span data-ttu-id="76be3-165">X509</span><span class="sxs-lookup"><span data-stu-id="76be3-165">X509</span></span>|<span data-ttu-id="76be3-166">Komunikat</span><span class="sxs-lookup"><span data-stu-id="76be3-166">Message</span></span>|  
|<span data-ttu-id="76be3-167">Certyfikat MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="76be3-167">MutualCertificate</span></span>|<span data-ttu-id="76be3-168">X509</span><span class="sxs-lookup"><span data-stu-id="76be3-168">X509</span></span>|<span data-ttu-id="76be3-169">X509</span><span class="sxs-lookup"><span data-stu-id="76be3-169">X509</span></span>|<span data-ttu-id="76be3-170">Komunikat</span><span class="sxs-lookup"><span data-stu-id="76be3-170">Message</span></span>|  
|<span data-ttu-id="76be3-171">Wzajemne CertyfikatyOdlot</span><span class="sxs-lookup"><span data-stu-id="76be3-171">MutualCertificateDuplex</span></span>|<span data-ttu-id="76be3-172">X509</span><span class="sxs-lookup"><span data-stu-id="76be3-172">X509</span></span>|<span data-ttu-id="76be3-173">X509</span><span class="sxs-lookup"><span data-stu-id="76be3-173">X509</span></span>|<span data-ttu-id="76be3-174">Komunikat</span><span class="sxs-lookup"><span data-stu-id="76be3-174">Message</span></span>|  
|<span data-ttu-id="76be3-175">Certyfikat IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="76be3-175">IssuedTokenForCertificate</span></span>|<span data-ttu-id="76be3-176">Federacyjni</span><span class="sxs-lookup"><span data-stu-id="76be3-176">Federated</span></span>|<span data-ttu-id="76be3-177">X509</span><span class="sxs-lookup"><span data-stu-id="76be3-177">X509</span></span>|<span data-ttu-id="76be3-178">Komunikat</span><span class="sxs-lookup"><span data-stu-id="76be3-178">Message</span></span>|  
|<span data-ttu-id="76be3-179">Kerberos</span><span class="sxs-lookup"><span data-stu-id="76be3-179">Kerberos</span></span>|<span data-ttu-id="76be3-180">Windows</span><span class="sxs-lookup"><span data-stu-id="76be3-180">Windows</span></span>|<span data-ttu-id="76be3-181">Windows</span><span class="sxs-lookup"><span data-stu-id="76be3-181">Windows</span></span>|<span data-ttu-id="76be3-182">Komunikat</span><span class="sxs-lookup"><span data-stu-id="76be3-182">Message</span></span>|  
|<span data-ttu-id="76be3-183">Issuedtoken</span><span class="sxs-lookup"><span data-stu-id="76be3-183">IssuedToken</span></span>|<span data-ttu-id="76be3-184">Federacyjni</span><span class="sxs-lookup"><span data-stu-id="76be3-184">Federated</span></span>|<span data-ttu-id="76be3-185">Federacyjni</span><span class="sxs-lookup"><span data-stu-id="76be3-185">Federated</span></span>|<span data-ttu-id="76be3-186">Komunikat</span><span class="sxs-lookup"><span data-stu-id="76be3-186">Message</span></span>|  
|<span data-ttu-id="76be3-187">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="76be3-187">SspiNegotiated</span></span>|<span data-ttu-id="76be3-188">Wynegocjowane SSPI systemu Windows</span><span class="sxs-lookup"><span data-stu-id="76be3-188">Windows Sspi Negotiated</span></span>|<span data-ttu-id="76be3-189">Wynegocjowane SSPI systemu Windows</span><span class="sxs-lookup"><span data-stu-id="76be3-189">Windows Sspi Negotiated</span></span>|<span data-ttu-id="76be3-190">Komunikat</span><span class="sxs-lookup"><span data-stu-id="76be3-190">Message</span></span>|  
|<span data-ttu-id="76be3-191">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="76be3-191">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="76be3-192">Brak</span><span class="sxs-lookup"><span data-stu-id="76be3-192">None</span></span>|<span data-ttu-id="76be3-193">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="76be3-193">X509, TLS-Nego</span></span>|<span data-ttu-id="76be3-194">Komunikat</span><span class="sxs-lookup"><span data-stu-id="76be3-194">Message</span></span>|  
|<span data-ttu-id="76be3-195">Nazwa użytkownikaForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="76be3-195">UserNameForSslNegotiated</span></span>|<span data-ttu-id="76be3-196">Nazwa użytkownika/hasło</span><span class="sxs-lookup"><span data-stu-id="76be3-196">User name/password</span></span>|<span data-ttu-id="76be3-197">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="76be3-197">X509, TLS-Nego</span></span>|<span data-ttu-id="76be3-198">Komunikat</span><span class="sxs-lookup"><span data-stu-id="76be3-198">Message</span></span>|  
|<span data-ttu-id="76be3-199">MutualSslNegotowany</span><span class="sxs-lookup"><span data-stu-id="76be3-199">MutualSslNegotiated</span></span>|<span data-ttu-id="76be3-200">X509</span><span class="sxs-lookup"><span data-stu-id="76be3-200">X509</span></span>|<span data-ttu-id="76be3-201">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="76be3-201">X509, TLS-Nego</span></span>|<span data-ttu-id="76be3-202">Komunikat</span><span class="sxs-lookup"><span data-stu-id="76be3-202">Message</span></span>|  
|<span data-ttu-id="76be3-203">WydanaTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="76be3-203">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="76be3-204">Federacyjni</span><span class="sxs-lookup"><span data-stu-id="76be3-204">Federated</span></span>|<span data-ttu-id="76be3-205">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="76be3-205">X509, TLS-Nego</span></span>|<span data-ttu-id="76be3-206">Komunikat</span><span class="sxs-lookup"><span data-stu-id="76be3-206">Message</span></span>|  
  
 <span data-ttu-id="76be3-207">Punkty końcowe przy użyciu takich trybów uwierzytelniania można wyrazić swoje wymagania dotyczące zabezpieczeń przy użyciu WS-SecurityPolicy (WS-SP).</span><span class="sxs-lookup"><span data-stu-id="76be3-207">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="76be3-208">W tym dokumencie opisano strukturę nagłówka zabezpieczeń i komunikatów infrastruktury dla każdego trybu uwierzytelniania i przedstawiono przykłady zasad i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="76be3-208">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="76be3-209">WCF wykorzystuje WS-SecureConversation do zapewnienia bezpiecznej obsługi sesji w celu ochrony wymiany wielu komunikatów między aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="76be3-209">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="76be3-210">Zobacz "Bezpieczne sesje" poniżej, aby uzyskać szczegółowe informacje na temat implementacji.</span><span class="sxs-lookup"><span data-stu-id="76be3-210">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="76be3-211">Oprócz trybów uwierzytelniania WCF udostępnia ustawienia do kontrolowania typowych mechanizmów ochrony, które mają zastosowanie do większości trybów uwierzytelniania opartych na zabezpieczeniach wiadomości, na przykład: kolejność podpisu i operacje szyfrowania, zestawy algorytmów, wyprowadzanie kluczy i potwierdzenie podpisu.</span><span class="sxs-lookup"><span data-stu-id="76be3-211">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="76be3-212">W tym dokumencie są używane następujące prefiksy i przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="76be3-212">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="76be3-213">Prefiks</span><span class="sxs-lookup"><span data-stu-id="76be3-213">Prefix</span></span>|<span data-ttu-id="76be3-214">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="76be3-214">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="76be3-215">s</span><span class="sxs-lookup"><span data-stu-id="76be3-215">s</span></span>|<http://www.w3.org/2003/05/soap-envelope/>|
|<span data-ttu-id="76be3-216">sp</span><span class="sxs-lookup"><span data-stu-id="76be3-216">sp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/>|
|<span data-ttu-id="76be3-217">a</span><span class="sxs-lookup"><span data-stu-id="76be3-217">a</span></span>|<http://www.w3.org/2005/08/addressing>|  
|<span data-ttu-id="76be3-218">wsse</span><span class="sxs-lookup"><span data-stu-id="76be3-218">wsse</span></span>|<span data-ttu-id="76be3-219">TBD – OASIS WSS 1.0 URI</span><span class="sxs-lookup"><span data-stu-id="76be3-219">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="76be3-220">wsse11</span><span class="sxs-lookup"><span data-stu-id="76be3-220">wsse11</span></span>|<span data-ttu-id="76be3-221">TBD – OASIS WSS 1.1 URI</span><span class="sxs-lookup"><span data-stu-id="76be3-221">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="76be3-222">wsu</span><span class="sxs-lookup"><span data-stu-id="76be3-222">wsu</span></span>|<span data-ttu-id="76be3-223">TBD – OASIS WSS 1.0 Narzędzie URI</span><span class="sxs-lookup"><span data-stu-id="76be3-223">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="76be3-224">ds</span><span class="sxs-lookup"><span data-stu-id="76be3-224">ds</span></span>|<span data-ttu-id="76be3-225">TBD – W3C XMLDSig URI</span><span class="sxs-lookup"><span data-stu-id="76be3-225">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="76be3-226">Wst</span><span class="sxs-lookup"><span data-stu-id="76be3-226">wst</span></span>|<span data-ttu-id="76be3-227">TBD – WS-Trust 2005/02 URI</span><span class="sxs-lookup"><span data-stu-id="76be3-227">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="76be3-228">wssc</span><span class="sxs-lookup"><span data-stu-id="76be3-228">wssc</span></span>|<span data-ttu-id="76be3-229">TBD – WS-SecureConversation 2005/02 URI</span><span class="sxs-lookup"><span data-stu-id="76be3-229">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="76be3-230">wsaw</span><span class="sxs-lookup"><span data-stu-id="76be3-230">wsaw</span></span>|<span data-ttu-id="76be3-231">TBD — obszar nazw zasad adresowania WS</span><span class="sxs-lookup"><span data-stu-id="76be3-231">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="76be3-232">wsp.</span><span class="sxs-lookup"><span data-stu-id="76be3-232">wsp</span></span>|<http://schemas.xmlsoap.org/ws/2004/09/policy>|  
|<span data-ttu-id="76be3-233">mssp</span><span class="sxs-lookup"><span data-stu-id="76be3-233">mssp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy>|
  
## <a name="1-token-profiles"></a><span data-ttu-id="76be3-234">1. Profile tokenów</span><span class="sxs-lookup"><span data-stu-id="76be3-234">1. Token Profiles</span></span>  
 <span data-ttu-id="76be3-235">Specyfikacje zabezpieczeń usług sieci Web reprezentują poświadczenia jako tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="76be3-235">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="76be3-236">WCF obsługuje następujące typy tokenów:</span><span class="sxs-lookup"><span data-stu-id="76be3-236">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="76be3-237">1.1 Nazwa użytkownikaDoken</span><span class="sxs-lookup"><span data-stu-id="76be3-237">1.1 UsernameToken</span></span>  
 <span data-ttu-id="76be3-238">WCF następuje UsernameToken10 i UsernameToken11 profile z następujących ograniczeń:</span><span class="sxs-lookup"><span data-stu-id="76be3-238">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="76be3-239">Atrybut PasswordType R1101 w elemencie UsernameToken\Password MUSI zostać pominięty lub mieć wartość #PasswordText (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="76be3-239">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="76be3-240">Można zaimplementować #PasswordDigest przy użyciu rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="76be3-240">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="76be3-241">Zaobserwowano, że #PasswordDigest często mylił się jako wystarczająco bezpieczny mechanizm ochrony hasłem.</span><span class="sxs-lookup"><span data-stu-id="76be3-241">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="76be3-242">Ale #PasswordDigest nie może służyć jako substytut szyfrowania UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="76be3-242">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="76be3-243">Głównym celem #PasswordDigest jest ochrona przed atakami powtarzania.</span><span class="sxs-lookup"><span data-stu-id="76be3-243">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="76be3-244">W trybach uwierzytelniania WCF zagrożenia ataku powtarzania są ograniczane przy użyciu podpisów wiadomości.</span><span class="sxs-lookup"><span data-stu-id="76be3-244">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="76be3-245">B1102 WCF nigdy nie emituje Nonce i utworzone podelementów UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="76be3-245">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="76be3-246">Te podkawiany mają na celu ułatwienie wykrywania powtarzania.</span><span class="sxs-lookup"><span data-stu-id="76be3-246">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="76be3-247">WCF zamiast tego używa podpisów wiadomości.</span><span class="sxs-lookup"><span data-stu-id="76be3-247">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="76be3-248">Oasis WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) wprowadzono klucz pochodny z funkcji hasła.</span><span class="sxs-lookup"><span data-stu-id="76be3-248">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="76be3-249">B1103 Nazwa użytkownikaNaken hasło nie może być używany do wyprowadzania klucza, a zatem do operacji kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="76be3-249">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="76be3-250">Uzasadnienie: hasła są zazwyczaj uważane za zbyt słabe, aby można je było używać do operacji kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="76be3-250">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="76be3-251">1.2 Token X509</span><span class="sxs-lookup"><span data-stu-id="76be3-251">1.2 X509 Token</span></span>  
 <span data-ttu-id="76be3-252">WCF obsługuje certyfikaty X509v3 jako typ poświadczeń i następuje X509TokenProfile1.0 i X509TokenProfile1.1 z następującymi ograniczeniami:</span><span class="sxs-lookup"><span data-stu-id="76be3-252">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="76be3-253">R1201 Atrybut ValueType w elemencie BinarySecurityToken musi mieć wartość #X509v3, gdy zawiera certyfikat X509v3.</span><span class="sxs-lookup"><span data-stu-id="76be3-253">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="76be3-254">WSS X509 Token Profile 1.0 i 1.1 definiują również #X509PKIPathv1 i #PKCS7 jako typy wartości.</span><span class="sxs-lookup"><span data-stu-id="76be3-254">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="76be3-255">WCF nie obsługuje tych typów.</span><span class="sxs-lookup"><span data-stu-id="76be3-255">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="76be3-256">R1202 Jeśli rozszerzenie SubjectKeyIdentifier (SKI) jest obecne w certyfikacie X509, wsse:KeyIdentifier powinien być używany do zewnętrznych odwołań do tokenu, z atrybutem ValueType jako #X509SubjectKeyIdentifier i jego zawartości wartości zakodowanej base64 rozszerzenia SKI certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="76be3-256">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="76be3-257">Referencje SKI są szeroko stosowane i udowodnione jako wysoce interoperacyjny zewnętrzny typ odniesienia.</span><span class="sxs-lookup"><span data-stu-id="76be3-257">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="76be3-258">R1203 Zewnętrzne odwołanie do tokenu zabezpieczającego X509 NIE POWINNO używać ds:X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="76be3-258">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="76be3-259">R1204 Jeśli X509TokenProfile1.1 jest w użyciu, zewnętrzne odwołanie do tokenu zabezpieczającego X509 należy użyć odcisk palca wprowadzony przez WS-Security 1.1.</span><span class="sxs-lookup"><span data-stu-id="76be3-259">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="76be3-260">WCF obsługuje X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="76be3-260">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="76be3-261">Istnieją jednak problemy ze współdziałaniem z X509IssuerSerial: WCF używa ciągu do porównania dwóch wartości X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="76be3-261">However There are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="76be3-262">W związku z tym jeśli jeden ponownie zamówi składniki nazwy podmiotu i wysyła do usługi WCF odwołanie do certyfikatu, nie może być znaleziony.</span><span class="sxs-lookup"><span data-stu-id="76be3-262">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="76be3-263">1.3 Token Protokołu Kerberos</span><span class="sxs-lookup"><span data-stu-id="76be3-263">1.3 Kerberos Token</span></span>  
 <span data-ttu-id="76be3-264">WCF obsługuje Protokół KerberosTokenProfile1.1 do celów uwierzytelniania systemu Windows z następującymi ograniczeniami:</span><span class="sxs-lookup"><span data-stu-id="76be3-264">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="76be3-265">R1301 Token Protokołu Kerberos musi zawierać wartość Opakowanego protokołu Kerberos v4 AP_REQ, zgodnie z definicją w GSS_API i specyfikacji Protokołu Kerberos, oraz musi mieć atrybut ValueType z wartością #GSS_Kerberosv5_AP_REQ.</span><span class="sxs-lookup"><span data-stu-id="76be3-265">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="76be3-266">WCF używa GSS opakowane Kerberos AP-REQ, a nie nagie AP-REQ.</span><span class="sxs-lookup"><span data-stu-id="76be3-266">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="76be3-267">Jest to najlepsze rozwiązanie w zakresie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="76be3-267">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="76be3-268">1.4 SamL v1.1 Token</span><span class="sxs-lookup"><span data-stu-id="76be3-268">1.4 SAML v1.1 Token</span></span>  
 <span data-ttu-id="76be3-269">WCF obsługuje WSS SAML Token profile 1.0 i 1.1 dla SAML v1.1 tokenów.</span><span class="sxs-lookup"><span data-stu-id="76be3-269">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="76be3-270">Możliwe jest zaimplementowanie innych wersji formatów tokenów SAML.</span><span class="sxs-lookup"><span data-stu-id="76be3-270">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="76be3-271">1.5 Token kontekstu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="76be3-271">1.5 Security Context Token</span></span>  
 <span data-ttu-id="76be3-272">WCF obsługuje token kontekstu zabezpieczeń (SCT) wprowadzony w WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="76be3-272">WCF supports the Security Context Token (SCT) introduced in WS-SecureConversation.</span></span> <span data-ttu-id="76be3-273">SCT jest używany do reprezentowania kontekstu zabezpieczeń ustanowionego w SecureConversation, a także binarnych protokołów negocjacji TLS i SSPI, opisanych poniżej.</span><span class="sxs-lookup"><span data-stu-id="76be3-273">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="76be3-274">2. Typowe parametry zabezpieczeń wiadomości</span><span class="sxs-lookup"><span data-stu-id="76be3-274">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="76be3-275">2.1 Sygnatura czasowa</span><span class="sxs-lookup"><span data-stu-id="76be3-275">2.1 TimeStamp</span></span>  
 <span data-ttu-id="76be3-276">Obecność sygnatury <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> czasowej <xref:System.ServiceModel.Channels.SecurityBindingElement> jest kontrolowana przy użyciu właściwości klasy.</span><span class="sxs-lookup"><span data-stu-id="76be3-276">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="76be3-277">WCF zawsze serializuje wsse:TimeStamp z wsse:Created i wsse:Expires fields.</span><span class="sxs-lookup"><span data-stu-id="76be3-277">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="76be3-278">Sygnatura czasowa wsse:Timestamp jest zawsze podpisywane podczas podpisywania jest używany.</span><span class="sxs-lookup"><span data-stu-id="76be3-278">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="76be3-279">2.2 Nakaz ochrony</span><span class="sxs-lookup"><span data-stu-id="76be3-279">2.2 Protection Order</span></span>  
 <span data-ttu-id="76be3-280">WCF obsługuje kolejność ochrony wiadomości "Sign Before Encrypt" i "Encrypt Before Sign" (Zasady zabezpieczeń 1.1).</span><span class="sxs-lookup"><span data-stu-id="76be3-280">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="76be3-281">"Sign Before Encrypt" jest zalecane z powodów takich jak: wiadomości chronione szyfruj przed podpisaniem są otwarte dla ataków substytucyjnych podpisu, chyba że używany jest mechanizm SignatureConfirmation w ramach WS-Security 1.1, a podpis za pomocą zaszyfrowanej zawartości tworzy audytu.</span><span class="sxs-lookup"><span data-stu-id="76be3-281">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="76be3-282">2.3 Ochrona podpisu</span><span class="sxs-lookup"><span data-stu-id="76be3-282">2.3 Signature Protection</span></span>  
 <span data-ttu-id="76be3-283">Gdy encrypt before sign jest używany, zaleca się, aby chronić podpis, aby zapobiec atakom siłowych w celu odgadnięcia zaszyfrowanej zawartości lub klucza podpisywania (zwłaszcza gdy niestandardowy token jest używany ze słabym materiałem klucza).</span><span class="sxs-lookup"><span data-stu-id="76be3-283">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="76be3-284">2.4 Pakiet algorytmów</span><span class="sxs-lookup"><span data-stu-id="76be3-284">2.4 Algorithm Suite</span></span>  
 <span data-ttu-id="76be3-285">WCF obsługuje wszystkie zestawy algorytmów wymienione w zasadach zabezpieczeń 1.1.</span><span class="sxs-lookup"><span data-stu-id="76be3-285">WCF supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="76be3-286">2.5 Wyprowadzanie kluczy</span><span class="sxs-lookup"><span data-stu-id="76be3-286">2.5 Key Derivation</span></span>  
 <span data-ttu-id="76be3-287">WCF używa "Wyprowadzanie kluczy symetrycznych" zgodnie z opisem w WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="76be3-287">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="76be3-288">2.6 Potwierdzenie podpisu</span><span class="sxs-lookup"><span data-stu-id="76be3-288">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="76be3-289">Potwierdzenie podpisu może być jako ochrona przed atakami pośrednika, aby chronić zestaw podpisów.</span><span class="sxs-lookup"><span data-stu-id="76be3-289">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="76be3-290">2.7 Układ nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="76be3-290">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="76be3-291">Każdy tryb uwierzytelniania opisuje określony układ nagłówka zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="76be3-291">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="76be3-292">Elementy w nagłówku zabezpieczeń są częściowo uporządkowane.</span><span class="sxs-lookup"><span data-stu-id="76be3-292">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="76be3-293">Aby zdefiniować kolejność elementów podrzędnych nagłówka zabezpieczeń, usługa WS-Security Policy definiuje następujące tryby układu nagłówka zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="76be3-293">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="76be3-294">Dokładny</span><span class="sxs-lookup"><span data-stu-id="76be3-294">Strict</span></span>|<span data-ttu-id="76be3-295">Elementy są dodawane do nagłówka zabezpieczeń zgodnie z zasadami układu numerowanymi opisanymi w sekcji Zasady zabezpieczeń 7.7.1 zgodnie z ogólną zasadą "deklarowania przed użyciem".</span><span class="sxs-lookup"><span data-stu-id="76be3-295">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="76be3-296">Lax</span><span class="sxs-lookup"><span data-stu-id="76be3-296">Lax</span></span>|<span data-ttu-id="76be3-297">Elementy są dodawane do nagłówka zabezpieczeń w dowolnej kolejności zgodnej z zasadami WSS: SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="76be3-297">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="76be3-298">LaxTimestampPierwsz</span><span class="sxs-lookup"><span data-stu-id="76be3-298">LaxTimestampFirst</span></span>|<span data-ttu-id="76be3-299">Tak samo jak Lax, z tą różnicą, że pierwszy element w nagłówku zabezpieczeń musi być sygnaturą czasową wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="76be3-299">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="76be3-300">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="76be3-300">LaxTimestampLast</span></span>|<span data-ttu-id="76be3-301">Tak samo jak lax, z tą różnicą, że ostatni element w nagłówku zabezpieczeń musi być wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="76be3-301">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="76be3-302">WCF obsługuje wszystkie cztery tryby dla układu nagłówka zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="76be3-302">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="76be3-303">Struktura nagłówka zabezpieczeń i przykłady komunikatów dla trybów uwierzytelniania poniżej są zgodne z trybem "Ścisłe".</span><span class="sxs-lookup"><span data-stu-id="76be3-303">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="76be3-304">2. Typowe parametry zabezpieczeń wiadomości</span><span class="sxs-lookup"><span data-stu-id="76be3-304">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="76be3-305">W tej sekcji przedstawiono przykładowe zasady dla każdego trybu uwierzytelniania wraz z przykładami przedstawiającymi strukturę nagłówka zabezpieczeń w wiadomościach wymienianych przez klienta i usługę.</span><span class="sxs-lookup"><span data-stu-id="76be3-305">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="76be3-306">6.1 Ochrona przed transportem</span><span class="sxs-lookup"><span data-stu-id="76be3-306">6.1 Transport Protection</span></span>  
 <span data-ttu-id="76be3-307">WCF zapewnia pięć trybów uwierzytelniania, które używają bezpiecznego transportu do ochrony wiadomości; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport i SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="76be3-307">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="76be3-308">Te tryby uwierzytelniania są konstruowane przy użyciu powiązania transportu opisanego w SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="76be3-308">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="76be3-309">W trybie uwierzytelniania UserNameOverTransport Nazwa_użytkownika Jest podpisanym tokenem pomocniczym.</span><span class="sxs-lookup"><span data-stu-id="76be3-309">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="76be3-310">W przypadku innych trybów uwierzytelniania token jest wyświetlany jako podpisany token zatwierdzający.</span><span class="sxs-lookup"><span data-stu-id="76be3-310">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="76be3-311">Załącznik C.1.2 i C.1.3 securityPolicy szczegółowo opisują układ nagłówka zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="76be3-311">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="76be3-312">Poniższe przykładowe nagłówki zabezpieczeń pokazują ścisły układ dla danego trybu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="76be3-312">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="76be3-313">Wartość właściwości "Klucze pochodne" dla tokenów we wszystkich przypadkach jest "false".</span><span class="sxs-lookup"><span data-stu-id="76be3-313">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="76be3-314">Wartości różnych właściwości powiązania transportu są następujące:</span><span class="sxs-lookup"><span data-stu-id="76be3-314">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="76be3-315">Sygnatura czasowa: true</span><span class="sxs-lookup"><span data-stu-id="76be3-315">Timestamp: true</span></span>  
  
 <span data-ttu-id="76be3-316">Układ nagłówka zabezpieczeń: Ścisły</span><span class="sxs-lookup"><span data-stu-id="76be3-316">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="76be3-317">Pakiet algorytmów: Basic256</span><span class="sxs-lookup"><span data-stu-id="76be3-317">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="76be3-318">6.1.1 Nazwa użytkownikaTransporttransport</span><span class="sxs-lookup"><span data-stu-id="76be3-318">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="76be3-319">W tym trybie uwierzytelniania klient uwierzytelnia się za pomocą tokenu nazwy użytkownika, który pojawia się w warstwie SOAP jako podpisany token pomocniczy, który jest zawsze wysyłany z inicjatora do adresata.</span><span class="sxs-lookup"><span data-stu-id="76be3-319">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="76be3-320">Usługa jest uwierzytelniona przy użyciu certyfikatu X.509 w warstwie transportu.</span><span class="sxs-lookup"><span data-stu-id="76be3-320">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="76be3-321">Używane powiązanie jest powiązanie transportu.</span><span class="sxs-lookup"><span data-stu-id="76be3-321">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="76be3-322">Zasady</span><span class="sxs-lookup"><span data-stu-id="76be3-322">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='UsernameOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:SignedSupportingTokens >  
        <wsp:Policy>  
          <sp:UsernameToken
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:WssUsernameToken10 />
            </wsp:Policy>  
          </sp:UsernameToken>  
        </wsp:Policy>  
      </sp:SignedSupportingTokens>  
      <sp:Wss11 >  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10 >  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="76be3-323">Układ nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="76be3-323">Security Header Layout</span></span>  
  
 <span data-ttu-id="76be3-324">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-324">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:UsernameToken ... >  
  ...  
  </wsse:UsernameToken>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-325">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-325">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="76be3-326">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="76be3-326">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="76be3-327">W tym trybie uwierzytelniania klient uwierzytelnia się przy użyciu certyfikatu X.509, który pojawia się w warstwie SOAP jako token pomocniczy, który jest zawsze wysyłany z inicjatora do adresata.</span><span class="sxs-lookup"><span data-stu-id="76be3-327">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="76be3-328">Usługa jest uwierzytelniona przy użyciu certyfikatu X.509 w warstwie transportu.</span><span class="sxs-lookup"><span data-stu-id="76be3-328">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="76be3-329">Używane powiązanie jest powiązanie transportu.</span><span class="sxs-lookup"><span data-stu-id="76be3-329">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="76be3-330">Zasady</span><span class="sxs-lookup"><span data-stu-id="76be3-330">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CertificateOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding xmlns:sp='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy' >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
             <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:RequireThumbprintReference />
              <sp:WssX509V3Token10 />
            </wsp:Policy>  
          </sp:X509Token>  
          <sp:SignedParts>  
            <sp:Header Name='To'
Namespace='http://www.w3.org/2005/08/addressing' />
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="76be3-331">Układ nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="76be3-331">Security Header Layout</span></span>  
  
 <span data-ttu-id="76be3-332">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-332">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wse:Timestamp u:Id="_0">  
  ...  
  </wse:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-333">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-333">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="76be3-334">6.1.3 WydanyTokenTransport</span><span class="sxs-lookup"><span data-stu-id="76be3-334">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="76be3-335">W tym trybie uwierzytelniania klient nie uwierzytelnia się w usłudze jako takiej, ale raczej przedstawia token wystawiony przez usługę tokenu zabezpieczającego (STS) i potwierdza znajomość klucza udostępnionego.</span><span class="sxs-lookup"><span data-stu-id="76be3-335">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="76be3-336">Wystawiony token pojawia się w warstwie SOAP jako token pomocniczy, który jest zawsze wysyłany z inicjatora do adresata.</span><span class="sxs-lookup"><span data-stu-id="76be3-336">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="76be3-337">Usługa jest uwierzytelniona przy użyciu certyfikatu X.509 w warstwie transportu.</span><span class="sxs-lookup"><span data-stu-id="76be3-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="76be3-338">Powiązanie jest powiązanie transportu.</span><span class="sxs-lookup"><span data-stu-id="76be3-338">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="76be3-339">Zasady</span><span class="sxs-lookup"><span data-stu-id="76be3-339">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='IssuedTokenOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:IssuedToken
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <sp:RequestSecurityTokenTemplate>  
              <wst:KeyType>  
              http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
              </wst:KeyType>
            </sp:RequestSecurityTokenTemplate>  
            <wsp:Policy>  
              <sp:RequireInternalReference />
            </wsp:Policy>  
          </sp:IssuedToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'
Namespace='http://www.w3.org/2005/08/addressing' />
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="76be3-340">Układ nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="76be3-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="76be3-341">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-341">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion ...>  
  ...  
  </saml:Assertion>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-342">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="76be3-343">6.1.4 Protokół KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="76be3-343">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="76be3-344">W tym trybie uwierzytelniania klient uwierzytelnia się w usłudze przy użyciu biletu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="76be3-344">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="76be3-345">Token Protokołu Kerberos pojawia się w warstwie SOAP jako token pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="76be3-345">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="76be3-346">Usługa jest uwierzytelniona przy użyciu certyfikatu X.509 w warstwie transportu.</span><span class="sxs-lookup"><span data-stu-id="76be3-346">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="76be3-347">Powiązanie jest powiązanie transportu.</span><span class="sxs-lookup"><span data-stu-id="76be3-347">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="76be3-348">Zasady</span><span class="sxs-lookup"><span data-stu-id="76be3-348">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='KerberosOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:KerberosToken  
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
            <wsp:Policy>  
              <sp:WssGssKerberosV5ApReqToken11 />
            </wsp:Policy>  
          </sp:KerberosToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'
Namespace='http://www.w3.org/2005/08/addressing' />
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="76be3-349">Układ nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="76be3-349">Security Header Layout</span></span>  
  
 <span data-ttu-id="76be3-350">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-350">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken ValueType="...#GSS_Kerberosv5_AP_REQ">  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-351">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-351">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="76be3-352">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="76be3-352">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="76be3-353">W tym trybie protokół negocjacji jest używany do wykonywania uwierzytelniania klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="76be3-353">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="76be3-354">Kerberos jest używany, jeśli to możliwe, w przeciwnym razie NTLM.</span><span class="sxs-lookup"><span data-stu-id="76be3-354">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="76be3-355">Wynikowy SCT pojawia się w warstwie SOAP jako token pomocniczy, który jest zawsze wysyłany od inicjatora do adresata.</span><span class="sxs-lookup"><span data-stu-id="76be3-355">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="76be3-356">Usługa jest dodatkowo uwierzytelniona w warstwie transportu za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="76be3-356">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="76be3-357">Używane powiązanie jest powiązanie transportu.</span><span class="sxs-lookup"><span data-stu-id="76be3-357">The binding used is a transport binding.</span></span> <span data-ttu-id="76be3-358">"SPNEGO" (negocjacja) opisuje, jak WCF używa protokołu negocjacji binarnych SSPI z WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="76be3-358">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="76be3-359">Przykłady nagłówka zabezpieczeń w tej sekcji są po SCT został ustanowiony za pośrednictwem uzgadniania SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="76be3-359">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="76be3-360">Zasady</span><span class="sxs-lookup"><span data-stu-id="76be3-360">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SspiNegotiatedOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:SpnegoContextToken
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy />
          </sp:SpnegoContextToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'
Namespace='http://www.w3.org/2005/08/addressing' />
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples"></a><span data-ttu-id="76be3-361">Przykłady nagłówków zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="76be3-361">Security Header Examples</span></span>  
 <span data-ttu-id="76be3-362">Po ustanowieniu tokenu kontekstu zabezpieczeń za pomocą uzgadniania SPNEGO przy użyciu negocjacji binarnych WS-Trust komunikaty aplikacji mają nagłówki zabezpieczeń o następującej strukturze.</span><span class="sxs-lookup"><span data-stu-id="76be3-362">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="76be3-363">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-363">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:SecurityContextToken u:Id="uuid-2202746a-7725-453d-8747-809cb718dab0-29" >  
  ...  
  </wssc:SecurityContextToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-364">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-364">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="76be3-365">6.2 Korzystanie z certyfikatów X.509 do uwierzytelniania usługi</span><span class="sxs-lookup"><span data-stu-id="76be3-365">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="76be3-366">W tej sekcji opisano następujące tryby uwierzytelniania: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate i IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="76be3-366">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="76be3-367">6.2.1 Certyfikat wzajemny WSS1.0</span><span class="sxs-lookup"><span data-stu-id="76be3-367">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="76be3-368">W tym trybie uwierzytelniania klient uwierzytelnia się przy użyciu certyfikatu X.509, który pojawia się w warstwie SOAP jako token inicjatora.</span><span class="sxs-lookup"><span data-stu-id="76be3-368">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="76be3-369">Usługa jest również uwierzytelniona przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="76be3-369">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="76be3-370">Użyte powiązanie jest powiązaniem asymetrycznym z następującymi wartościami właściwości:</span><span class="sxs-lookup"><span data-stu-id="76be3-370">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="76be3-371">Token inicjatora: certyfikat X.509 klienta, z trybem dołączania ustawionym na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="76be3-371">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="76be3-372">Token odbiorcy: Certyfikat X.509 serwera z trybem włączenia jest ustawiony .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="76be3-372">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="76be3-373">Ochrona tokenu: Fałsz</span><span class="sxs-lookup"><span data-stu-id="76be3-373">Token Protection: False</span></span>  
  
 <span data-ttu-id="76be3-374">Cały nagłówek i podpisy treści: True</span><span class="sxs-lookup"><span data-stu-id="76be3-374">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="76be3-375">Kolejność ochrony: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="76be3-375">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="76be3-376">Szyfruj podpis: True</span><span class="sxs-lookup"><span data-stu-id="76be3-376">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="76be3-377">Zasady</span><span class="sxs-lookup"><span data-stu-id="76be3-377">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificate_WSS10_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="76be3-378">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="76be3-378">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="76be3-379">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-379">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-380">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-380">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-381">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="76be3-381">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="76be3-382">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-382">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-383">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-383">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="76be3-384">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="76be3-384">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="76be3-385">W tym trybie uwierzytelniania klient uwierzytelnia się przy użyciu certyfikatu X.509, który pojawia się w warstwie SOAP jako token inicjatora.</span><span class="sxs-lookup"><span data-stu-id="76be3-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="76be3-386">Usługa jest również uwierzytelniona przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="76be3-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="76be3-387">Użyte powiązanie jest powiązaniem asymetrycznym z następującymi wartościami właściwości:</span><span class="sxs-lookup"><span data-stu-id="76be3-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="76be3-388">Token inicjatora: Certyfikat X509 klienta, tryb dołączania jest ustawiony na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="76be3-388">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="76be3-389">Token odbiorcy: Certyfikat X509 serwera, tryb dołączania jest ustawiony na .../IncludeToken/AlwaysToInitiator</span><span class="sxs-lookup"><span data-stu-id="76be3-389">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="76be3-390">Ochrona tokenu: Fałsz</span><span class="sxs-lookup"><span data-stu-id="76be3-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="76be3-391">Cały nagłówek i podpisy treści: True</span><span class="sxs-lookup"><span data-stu-id="76be3-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="76be3-392">Kolejność ochrony: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="76be3-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="76be3-393">Szyfruj podpis: True</span><span class="sxs-lookup"><span data-stu-id="76be3-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="76be3-394">Zasady</span><span class="sxs-lookup"><span data-stu-id="76be3-394">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificateDuplex_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToInitiator' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="76be3-395">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="76be3-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="76be3-396">Prośba i odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-396">Request and Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="76be3-397">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="76be3-397">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="76be3-398">Prośba i odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-398">Request and Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="76be3-399">6.2.3 Korzystanie z symetrycznego powiązania z uwierzytelnianiem usługi X.509</span><span class="sxs-lookup"><span data-stu-id="76be3-399">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="76be3-400">"WSS10" zapewnia ograniczoną obsługę scenariuszy z tokenami X509.</span><span class="sxs-lookup"><span data-stu-id="76be3-400">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="76be3-401">Na przykład nie było sposobu zapewnienia ochrony podpisu i szyfrowania dla wiadomości przy użyciu tylko usługi token X509.</span><span class="sxs-lookup"><span data-stu-id="76be3-401">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="76be3-402">"WSS11" wprowadzono użycie EncryptedKey jako token symetryczny.</span><span class="sxs-lookup"><span data-stu-id="76be3-402">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="76be3-403">Teraz klucz tymczasowy zaszyfrowany dla certyfikatu X.509 usługi może służyć zarówno do ochrony wiadomości żądania i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="76be3-403">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="76be3-404">Tryby uwierzytelniania opisane w sekcji 6.4 poniżej używają tego wzorca.</span><span class="sxs-lookup"><span data-stu-id="76be3-404">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="76be3-405">WS-SecurityPolicy opisuje ten wzorzec przy użyciu SymmetricBinding z tokenem Usługi X509 jako token ochrony.</span><span class="sxs-lookup"><span data-stu-id="76be3-405">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="76be3-406">Tryby uwierzytelniania AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 i IssuedTokenForCertificate używają podobnego wystąpienia sp:SymmetricBinding z następującymi wartościami właściwości:</span><span class="sxs-lookup"><span data-stu-id="76be3-406">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="76be3-407">Token ochrony: Certyfikat X509 serwera, tryb dołączania jest ustawiony na .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="76be3-407">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="76be3-408">Ochrona tokenu: Fałsz</span><span class="sxs-lookup"><span data-stu-id="76be3-408">Token Protection: False</span></span>  
  
 <span data-ttu-id="76be3-409">Cały nagłówek i podpisy treści: True</span><span class="sxs-lookup"><span data-stu-id="76be3-409">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="76be3-410">Kolejność ochrony: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="76be3-410">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="76be3-411">Szyfruj podpis: True</span><span class="sxs-lookup"><span data-stu-id="76be3-411">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="76be3-412">Powyższe tryby uwierzytelniania różnią się tylko tokenami pomocniczymi, których używają.</span><span class="sxs-lookup"><span data-stu-id="76be3-412">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="76be3-413">AnonymousForCertificate nie ma żadnych tokenów pomocniczych, MutualCertificate WSS 1.1 ma certyfikat X509 klienta jako tokeny wspierające, UserNameForCertificate ma token UserName jako podpisany token pomocniczy i IssuedTokenForCertificate ma wystawiony token jako token pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="76be3-413">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="76be3-414">Zasady</span><span class="sxs-lookup"><span data-stu-id="76be3-414">Policy</span></span>  
  
 <span data-ttu-id="76be3-415">Wiązanie symetryczne</span><span class="sxs-lookup"><span data-stu-id="76be3-415">Symmetric Binding</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SymmetricCert_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                  <sp:RequireThumbprintReference />
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />  
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting Token Assertions appear here -->  
      ...  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
          <sp:RequireSignatureConfirmation />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="76be3-416">6.2.4 AnonimowośćDocertytutututu</span><span class="sxs-lookup"><span data-stu-id="76be3-416">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="76be3-417">W tym trybie uwierzytelniania klient jest anonimowy, a usługa jest uwierzytelniana przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="76be3-417">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="76be3-418">Użyte powiązanie jest wystąpieniem wiązania symetrycznego, jak opisano w 6.4.2.</span><span class="sxs-lookup"><span data-stu-id="76be3-418">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="76be3-419">Zasady</span><span class="sxs-lookup"><span data-stu-id="76be3-419">Policy</span></span>  
  
 <span data-ttu-id="76be3-420">Szczegółowe informacje na temat wiążących informacji znajdują się w informacji dodatkowej do "Polityki" w pkt 6.2.3 powyżej</span><span class="sxs-lookup"><span data-stu-id="76be3-420">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="76be3-421">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="76be3-421">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="76be3-422">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-422">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-423">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-423">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="76be3-424">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="76be3-424">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="76be3-425">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-425">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-426">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-426">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="76be3-427">6.2.5 Nazwa użytkownikaDocertyfikat</span><span class="sxs-lookup"><span data-stu-id="76be3-427">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="76be3-428">W tym trybie uwierzytelniania klient uwierzytelnia się w usłudze przy użyciu tokenu nazwy użytkownika, który pojawia się w warstwie SOAP jako podpisany token pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="76be3-428">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="76be3-429">Usługa uwierzytelnia się klientowi przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="76be3-429">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="76be3-430">Używane powiązanie jest powiązanie symetryczne z tokenem ochrony jest klucz generowany przez klienta, zaszyfrowane za pomocą klucza publicznego usługi.</span><span class="sxs-lookup"><span data-stu-id="76be3-430">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="76be3-431">Zasady</span><span class="sxs-lookup"><span data-stu-id="76be3-431">Policy</span></span>  
  
 <span data-ttu-id="76be3-432">Szczegółowe informacje na temat wiążących informacji znajdują się w informacji dodatkowej do "Polityki" w pkt 6.2.3 powyżej</span><span class="sxs-lookup"><span data-stu-id="76be3-432">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="76be3-433">Podpisany token pomocniczy</span><span class="sxs-lookup"><span data-stu-id="76be3-433">Signed Supporting Token</span></span>  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="76be3-434">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="76be3-434">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="76be3-435">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-435">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-436">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-436">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="76be3-437">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="76be3-437">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="76be3-438">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-438">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-439">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-439">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="76be3-440">6.2.6 Certyfikat wzajemny (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="76be3-440">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="76be3-441">W tym trybie uwierzytelniania klient uwierzytelnia się przy użyciu certyfikatu X.509, który pojawia się w warstwie SOAP jako token pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="76be3-441">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="76be3-442">Usługa jest również uwierzytelniona przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="76be3-442">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="76be3-443">Używane powiązanie jest powiązanie symetryczne z tokenem ochrony jest klucz generowany przez klienta, zaszyfrowane za pomocą klucza publicznego usługi.</span><span class="sxs-lookup"><span data-stu-id="76be3-443">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="76be3-444">Zasady</span><span class="sxs-lookup"><span data-stu-id="76be3-444">Policy</span></span>  
  
 <span data-ttu-id="76be3-445">Szczegółowe informacje na temat zasad znajdują się w 6.2.3</span><span class="sxs-lookup"><span data-stu-id="76be3-445">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="76be3-446">Zatwierdzający token pomocniczy</span><span class="sxs-lookup"><span data-stu-id="76be3-446">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />
        <sp:WssX509V3Token10 />
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="76be3-447">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="76be3-447">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="76be3-448">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-448">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-449">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-449">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="76be3-450">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="76be3-450">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="76be3-451">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-451">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-452">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-452">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="76be3-453">6.2.7 Certyfikat WydanyTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="76be3-453">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="76be3-454">W tym trybie uwierzytelniania klient nie uwierzytelnia się w usłudze jako takiej, ale zamiast tego przedstawia token wystawiony przez usługę STS i potwierdza znajomość klucza udostępnionego.</span><span class="sxs-lookup"><span data-stu-id="76be3-454">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="76be3-455">Wystawiony token pojawia się w warstwie SOAP jako token pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="76be3-455">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="76be3-456">Usługa uwierzytelnia się klientowi przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="76be3-456">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="76be3-457">Używane powiązanie jest powiązanie symetryczne z tokenem ochrony jest klucz generowany przez klienta, zaszyfrowane za pomocą klucza publicznego usługi.</span><span class="sxs-lookup"><span data-stu-id="76be3-457">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="76be3-458">Zasady</span><span class="sxs-lookup"><span data-stu-id="76be3-458">Policy</span></span>  
  
 <span data-ttu-id="76be3-459">Szczegółowe informacje na temat zasad znajdują się w 6.2.3 powyżej</span><span class="sxs-lookup"><span data-stu-id="76be3-459">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="76be3-460">Zatwierdzający token pomocniczy</span><span class="sxs-lookup"><span data-stu-id="76be3-460">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
       </wst:KeyType>  
     </sp:RequestSecurityTokenTemplate>  
     <wsp:Policy>  
       <sp:RequireDerivedKeys />
       <sp:RequireInternalReference />
     </wsp:Policy>  
   </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="76be3-461">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="76be3-461">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="76be3-462">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-462">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-463">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-463">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="76be3-464">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="76be3-464">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="76be3-465">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-465">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-466">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-466">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
## <a name="63-kerberos"></a><span data-ttu-id="76be3-467">6.3 Protokół Kerberos</span><span class="sxs-lookup"><span data-stu-id="76be3-467">6.3 Kerberos</span></span>  
 <span data-ttu-id="76be3-468">W tym trybie uwierzytelniania klient uwierzytelnia się w usłudze przy użyciu biletu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="76be3-468">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="76be3-469">Ten sam bilet zapewnia również uwierzytelnianie serwera.</span><span class="sxs-lookup"><span data-stu-id="76be3-469">That same ticket also provides server authentication.</span></span> <span data-ttu-id="76be3-470">Użyte powiązanie jest powiązaniem symetrycznym z następującymi właściwościami;</span><span class="sxs-lookup"><span data-stu-id="76be3-470">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="76be3-471">Token ochrony: Bilet Kerberos, tryb włączenia jest ustawiony na .../IncludeToken/Once</span><span class="sxs-lookup"><span data-stu-id="76be3-471">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="76be3-472">Ochrona tokenu: Fałsz</span><span class="sxs-lookup"><span data-stu-id="76be3-472">Token Protection: False</span></span>  
  
 <span data-ttu-id="76be3-473">Cały nagłówek i podpisy treści: True</span><span class="sxs-lookup"><span data-stu-id="76be3-473">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="76be3-474">Kolejność ochrony: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="76be3-474">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="76be3-475">Szyfruj podpis: True</span><span class="sxs-lookup"><span data-stu-id="76be3-475">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="76be3-476">Zasady</span><span class="sxs-lookup"><span data-stu-id="76be3-476">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='Kerberos_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:KerberosToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                  <sp:WssGssKerberosV5ApReqToken11 />
                </wsp:Policy>  
              </sp:KerberosToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="76be3-477">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="76be3-477">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="76be3-478">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-478">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-479">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-479">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="76be3-480">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="76be3-480">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="76be3-481">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-481">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-482">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-482">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="76be3-483">6.4 WydanyDokład</span><span class="sxs-lookup"><span data-stu-id="76be3-483">6.4 IssuedToken</span></span>  
 <span data-ttu-id="76be3-484">W tym trybie uwierzytelniania klient nie uwierzytelnia się w usłudze, jako taki, a klient przedstawia token wystawiony przez usługę STS i potwierdza znajomość klucza udostępnionego.</span><span class="sxs-lookup"><span data-stu-id="76be3-484">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="76be3-485">Usługa nie jest uwierzytelniana do klienta, jako takie, zamiast STS szyfruje klucz udostępniony jako część wystawionego tokenu, tak aby tylko usługa może odszyfrować klucz.</span><span class="sxs-lookup"><span data-stu-id="76be3-485">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="76be3-486">Używane powiązanie jest jako wiązanie symetryczne z następującymi właściwościami;</span><span class="sxs-lookup"><span data-stu-id="76be3-486">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="76be3-487">Token ochrony: Wystawiony token, tryb włączenia jest ustawiony na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="76be3-487">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="76be3-488">Ochrona tokenu: Fałsz</span><span class="sxs-lookup"><span data-stu-id="76be3-488">Token Protection: False</span></span>  
  
 <span data-ttu-id="76be3-489">Cały nagłówek i podpisy treści: True</span><span class="sxs-lookup"><span data-stu-id="76be3-489">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="76be3-490">Kolejność ochrony: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="76be3-490">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="76be3-491">Szyfruj podpis: True</span><span class="sxs-lookup"><span data-stu-id="76be3-491">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="76be3-492">Zasady</span><span class="sxs-lookup"><span data-stu-id="76be3-492">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple3_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <sp:RequestSecurityTokenTemplate>  
                  <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
                  </wst:KeyType>
                </sp:RequestSecurityTokenTemplate>  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                  <sp:RequireInternalReference />
                </wsp:Policy>  
              </sp:IssuedToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="76be3-493">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="76be3-493">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="76be3-494">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-494">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-495">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-495">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="76be3-496">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="76be3-496">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="76be3-497">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-497">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-498">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-498">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="76be3-499">6.5 Korzystanie z usługi SslNegotiated do uwierzytelniania usługi</span><span class="sxs-lookup"><span data-stu-id="76be3-499">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="76be3-500">W tej sekcji opisano grupę trybów uwierzytelniania, które używają powiązania symetrycznego z tokenem ochrony jako token kontekstu zabezpieczeń na WS-SecureConversation (WS-SecureConversation (WS-SC), którego wartość klucza jest negocjowana przez wykonanie protokołu TLS za pomocą komunikatów RST/RSTR usługi WS-Trust (WS-T).</span><span class="sxs-lookup"><span data-stu-id="76be3-500">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="76be3-501">Szczegóły implementacji uzgadniania TLS przy użyciu programu WS-Trust są opisane w TLSNEGO.</span><span class="sxs-lookup"><span data-stu-id="76be3-501">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="76be3-502">W tym miejscu w przykładach wiadomości zakładamy, że SCT z skojarzonym kontekstem zabezpieczeń jest już ustanowiony za pomocą uzgadniania.</span><span class="sxs-lookup"><span data-stu-id="76be3-502">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="76be3-503">Użyte powiązanie jest powiązaniem symetrycznym z następującymi właściwościami;</span><span class="sxs-lookup"><span data-stu-id="76be3-503">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="76be3-504">Token ochrony: SslContextToken, tryb włączenia jest ustawiony na .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="76be3-504">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="76be3-505">Ochrona tokenu: Fałsz</span><span class="sxs-lookup"><span data-stu-id="76be3-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="76be3-506">Cały nagłówek i podpisy treści: True</span><span class="sxs-lookup"><span data-stu-id="76be3-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="76be3-507">Kolejność ochrony: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="76be3-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="76be3-508">Szyfruj podpis: True</span><span class="sxs-lookup"><span data-stu-id="76be3-508">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="76be3-509">6.5.1 Zasady uwierzytelniania usługi SslNegotiated</span><span class="sxs-lookup"><span data-stu-id="76be3-509">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="76be3-510">Zasady dla wszystkich trybów uwierzytelniania w tej sekcji są podobne i różnią się tylko określonymi podpisanymi tokenami pomocniczymi lub aprobującymi używanymi.</span><span class="sxs-lookup"><span data-stu-id="76be3-510">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SslNegotiated_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <mssp:SslContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' />  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                </wsp:Policy>  
              </mssp:SslContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting token assertions go here -->  
      ..  
      <sp:Wss11>
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="76be3-511">6.5.2 AnonimowoDo negocjacji</span><span class="sxs-lookup"><span data-stu-id="76be3-511">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="76be3-512">W tym trybie uwierzytelniania klient jest anonimowy, a usługa jest uwierzytelniana przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="76be3-512">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="76be3-513">Użyte powiązanie jest wystąpieniem wiązania symetrycznego, jak opisano w 6.5.1 powyżej.</span><span class="sxs-lookup"><span data-stu-id="76be3-513">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="76be3-514">Zasady</span><span class="sxs-lookup"><span data-stu-id="76be3-514">Policy</span></span>  
  
 <span data-ttu-id="76be3-515">Szczegółowe informacje dotyczące powiązania można znaleźć w polityce w 6.5.1 powyżej.</span><span class="sxs-lookup"><span data-stu-id="76be3-515">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="76be3-516">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="76be3-516">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="76be3-517">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-517">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-518">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-518">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="76be3-519">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="76be3-519">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="76be3-520">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-520">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-521">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-521">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="76be3-522">6.5.3 Nazwa użytkownikaDo negocjacji</span><span class="sxs-lookup"><span data-stu-id="76be3-522">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="76be3-523">W tym trybie uwierzytelniania klient uwierzytelnia się przy użyciu tokenu nazwy użytkownika, który pojawia się w warstwie SOAP jako podpisany token pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="76be3-523">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="76be3-524">Usługa jest uwierzytelniona przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="76be3-524">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="76be3-525">Użyte powiązanie jest wystąpieniem wiązania symetrycznego, jak opisano w 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="76be3-525">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="76be3-526">Zasady</span><span class="sxs-lookup"><span data-stu-id="76be3-526">Policy</span></span>  
  
 <span data-ttu-id="76be3-527">Szczegółowe informacje dotyczące wiązania znajdują się w punkcie 6.5.1 powyżej</span><span class="sxs-lookup"><span data-stu-id="76be3-527">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="76be3-528">Podpisany token pomocniczy</span><span class="sxs-lookup"><span data-stu-id="76be3-528">Signed Supporting Token</span></span>  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="76be3-529">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="76be3-529">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="76be3-530">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-530">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-531">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-531">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="76be3-532">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="76be3-532">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="76be3-533">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-533">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-534">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-534">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="76be3-535">6.5.4 WydanyTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="76be3-535">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="76be3-536">W tym trybie uwierzytelniania klient nie uwierzytelnia się w usłudze jako takiej, ale zamiast tego przedstawia token wystawiony przez usługę STS i potwierdza znajomość klucza udostępnionego.</span><span class="sxs-lookup"><span data-stu-id="76be3-536">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="76be3-537">Wystawiony token pojawia się w warstwie SOAP jako token pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="76be3-537">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="76be3-538">Usługa jest uwierzytelniona przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="76be3-538">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="76be3-539">Użyte powiązanie jest wystąpieniem wiązania symetrycznego, jak opisano w 6.5.1 powyżej.</span><span class="sxs-lookup"><span data-stu-id="76be3-539">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="76be3-540">Zasady</span><span class="sxs-lookup"><span data-stu-id="76be3-540">Policy</span></span>  
  
 <span data-ttu-id="76be3-541">Szczegółowe informacje dotyczące wiązania znajdują się w punkcie 6.5.1 powyżej</span><span class="sxs-lookup"><span data-stu-id="76be3-541">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="76be3-542">Zatwierdzający token pomocniczy</span><span class="sxs-lookup"><span data-stu-id="76be3-542">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
        </wst:KeyType>
      </sp:RequestSecurityTokenTemplate>  
      <wsp:Policy>  
        <sp:RequireDerivedKeys />
        <sp:RequireInternalReference />
      </wsp:Policy>  
    </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="76be3-543">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="76be3-543">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="76be3-544">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-544">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-545">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-545">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="76be3-546">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="76be3-546">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="76be3-547">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-547">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-548">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-548">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="76be3-549">6.5.5 Objednanie</span><span class="sxs-lookup"><span data-stu-id="76be3-549">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="76be3-550">W tym trybie uwierzytelniania klient i usługa uwierzytelniają się przy użyciu certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="76be3-550">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="76be3-551">Użyte powiązanie jest wystąpieniem wiązania symetrycznego, jak opisano w 6.5.1 powyżej.</span><span class="sxs-lookup"><span data-stu-id="76be3-551">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="76be3-552">Zasady</span><span class="sxs-lookup"><span data-stu-id="76be3-552">Policy</span></span>  
  
 <span data-ttu-id="76be3-553">Szczegółowe informacje dotyczące wiązania znajdują się w punkcie 6.5.1 powyżej</span><span class="sxs-lookup"><span data-stu-id="76be3-553">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="76be3-554">Zatwierdzający token pomocniczy</span><span class="sxs-lookup"><span data-stu-id="76be3-554">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />
        <sp:WssX509V3Token10 />
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="76be3-555">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="76be3-555">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="76be3-556">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-556">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-557">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-557">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="76be3-558">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="76be3-558">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="76be3-559">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-559">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-560">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-560">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="76be3-561">6.6 SspiNegotyzowany</span><span class="sxs-lookup"><span data-stu-id="76be3-561">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="76be3-562">W tym trybie uwierzytelniania protokół negocjacji jest używany do wykonywania uwierzytelniania klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="76be3-562">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="76be3-563">Kerberos jest używany, jeśli to możliwe, w przeciwnym razie NTLM.</span><span class="sxs-lookup"><span data-stu-id="76be3-563">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="76be3-564">Użyte powiązanie jest powiązaniem symetrycznym z następującymi właściwościami;</span><span class="sxs-lookup"><span data-stu-id="76be3-564">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="76be3-565">Token ochrony: SpnegoContextToken, tryb włączenia jest ustawiony na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="76be3-565">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="76be3-566">Ochrona tokenu: Fałsz</span><span class="sxs-lookup"><span data-stu-id="76be3-566">Token Protection: False</span></span>  
  
 <span data-ttu-id="76be3-567">Cały nagłówek i podpisy treści: True</span><span class="sxs-lookup"><span data-stu-id="76be3-567">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="76be3-568">Kolejność ochrony: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="76be3-568">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="76be3-569">Szyfruj podpis: True</span><span class="sxs-lookup"><span data-stu-id="76be3-569">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="76be3-570">Zasady</span><span class="sxs-lookup"><span data-stu-id="76be3-570">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple13_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                </wsp:Policy>  
              </sp:SpnegoContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="76be3-571">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="76be3-571">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="76be3-572">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-572">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-573">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-573">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="76be3-574">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="76be3-574">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="76be3-575">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-575">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-576">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-576">Response</span></span>  
  
```xml  
<wsse:Security>  
<wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="67-secureconversation"></a><span data-ttu-id="76be3-577">6.7 Bezpieczna konwersacja</span><span class="sxs-lookup"><span data-stu-id="76be3-577">6.7 SecureConversation</span></span>  
 <span data-ttu-id="76be3-578">Używane powiązanie jest powiązanie symetryczne z tokenem ochrony jest SCT na WS-SecureConversation (WS-SC).</span><span class="sxs-lookup"><span data-stu-id="76be3-578">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="76be3-579">SCT jest negocjowany przy użyciu WS-Trust (WS-Trust) lub WS-SecureConversation (WS-SC) zgodnie z zagnieżdżonego powiązania, który sam w sobie jest powiązanie symetryczne, który używa protokołu negocjacji.</span><span class="sxs-lookup"><span data-stu-id="76be3-579">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="76be3-580">Protokół negocjacji będzie używany do wykonywania uwierzytelniania klienta i serwera, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="76be3-580">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="76be3-581">Jeśli protokołu Kerberos nie można użyć, powróci do NTLM.</span><span class="sxs-lookup"><span data-stu-id="76be3-581">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="76be3-582">Zasady</span><span class="sxs-lookup"><span data-stu-id="76be3-582">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SecureConversation_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SecureConversationToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                  <sp:BootstrapPolicy>  
                    <wsp:Policy>  
                      <sp:SignedParts>  
                        <sp:Body />
                        <sp:Header Name='To' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='From' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='FaultTo' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='ReplyTo' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='MessageID' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='RelatesTo' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='Action' Namespace='http://www.w3.org/2005/08/addressing' />
                      </sp:SignedParts>  
                      <sp:EncryptedParts>  
                        <sp:Body />
                      </sp:EncryptedParts>  
                      <sp:SymmetricBinding>  
                        <wsp:Policy>  
                          <sp:ProtectionToken>  
                            <wsp:Policy>  
                              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                                <wsp:Policy>  
                                  <sp:RequireDerivedKeys />
                                </wsp:Policy>  
                              </sp:SpnegoContextToken>  
                            </wsp:Policy>  
                          </sp:ProtectionToken>  
                          <sp:AlgorithmSuite>  
                            <wsp:Policy>  
                              <sp:Basic256 />
                            </wsp:Policy>  
                          </sp:AlgorithmSuite>  
                          <sp:Layout>  
                            <wsp:Policy>  
                              <sp:Strict />
                            </wsp:Policy>  
                          </sp:Layout>  
                          <sp:IncludeTimestamp />
                          <sp:EncryptSignature />
                          <sp:OnlySignEntireHeadersAndBody />
                        </wsp:Policy>  
                      </sp:SymmetricBinding>  
                      <sp:Wss11>  
                        <wsp:Policy>  
                          <sp:MustSupportRefKeyIdentifier />
                          <sp:MustSupportRefIssuerSerial />
                          <sp:MustSupportRefThumbprint />
                          <sp:MustSupportRefEncryptedKey />
                        </wsp:Policy>  
                      </sp:Wss11>  
                      <sp:Trust10>  
                        <wsp:Policy>  
                          <sp:MustSupportIssuedTokens />
                          <sp:RequireClientEntropy />
                          <sp:RequireServerEntropy />
                        </wsp:Policy>  
                      </sp:Trust10>  
                    </wsp:Policy>  
                  </sp:BootstrapPolicy>  
                </wsp:Policy>  
              </sp:SecureConversationToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="76be3-583">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="76be3-583">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="76be3-584">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-584">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-585">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-585">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="76be3-586">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="76be3-586">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="76be3-587">Żądanie</span><span class="sxs-lookup"><span data-stu-id="76be3-587">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="76be3-588">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="76be3-588">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```
