---
title: Protokoły zabezpieczeń wersja 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
ms.openlocfilehash: 684ab50b6dab4b97577acf7673ed14c53e5af13e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748580"
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="ffe23-102">Protokoły zabezpieczeń wersja 1.0</span><span class="sxs-lookup"><span data-stu-id="ffe23-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="ffe23-103">Protokoły zabezpieczeń usług sieci Web zapewnia mechanizmy zabezpieczeń usług sieci Web, które obejmują wszystkie istniejące enterprise komunikatów wymagań dotyczących zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ffe23-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="ffe23-104">W tej sekcji opisano szczegóły Windows Communication Foundation (WCF) w wersji 1.0 (zaimplementowany w <xref:System.ServiceModel.Channels.SecurityBindingElement>) dla następujących sieci Web usług protokołów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ffe23-104">This section describes the Windows Communication Foundation (WCF) version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="ffe23-105">Specyfikacja/dokumentu</span><span class="sxs-lookup"><span data-stu-id="ffe23-105">Specification/Document</span></span>|<span data-ttu-id="ffe23-106">Łącze</span><span class="sxs-lookup"><span data-stu-id="ffe23-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="ffe23-107">WSS: SOAP Message Security 1.0</span><span class="sxs-lookup"><span data-stu-id="ffe23-107">WSS: SOAP Message Security 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|
|<span data-ttu-id="ffe23-108">WSS: Token nazwy użytkownika profilu 1.0</span><span class="sxs-lookup"><span data-stu-id="ffe23-108">WSS: Username Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="ffe23-109">WSS: X509 Token Profile 1.0</span><span class="sxs-lookup"><span data-stu-id="ffe23-109">WSS: X509 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|
|<span data-ttu-id="ffe23-110">WSS: SAML 1.1 Token Profile 1.0</span><span class="sxs-lookup"><span data-stu-id="ffe23-110">WSS: SAML 1.1 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|
|<span data-ttu-id="ffe23-111">WSS: Zabezpieczenia komunikatów SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="ffe23-111">WSS: SOAP Message Security 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|
|<span data-ttu-id="ffe23-112">1.1 tokenu profilu programu WSS nazwy użytkownika</span><span class="sxs-lookup"><span data-stu-id="ffe23-112">WSS Username Token Profile 1.1</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="ffe23-113">WSS: X.509 Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="ffe23-113">WSS: X.509 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|
|<span data-ttu-id="ffe23-114">WSS: 1.1 profilu tokenu protokołu Kerberos</span><span class="sxs-lookup"><span data-stu-id="ffe23-114">WSS: Kerberos Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|
|<span data-ttu-id="ffe23-115">WSS: SAML 1.1 Token 1.1 profilu</span><span class="sxs-lookup"><span data-stu-id="ffe23-115">WSS: SAML 1.1 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|
|<span data-ttu-id="ffe23-116">Zabezpieczenia WS konwersacji</span><span class="sxs-lookup"><span data-stu-id="ffe23-116">WS-Secure Conversation</span></span>|<http://specs.xmlsoap.org/ws/2005/02/sc/WS-SecureConversation.pdf>|
|<span data-ttu-id="ffe23-117">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="ffe23-117">WS-Trust</span></span>|<http://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf>|
|<span data-ttu-id="ffe23-118">Application Note:</span><span class="sxs-lookup"><span data-stu-id="ffe23-118">Application Note:</span></span><br /><br /> <span data-ttu-id="ffe23-119">Za pomocą protokołu WS-Trust dla uzgadniania TLS</span><span class="sxs-lookup"><span data-stu-id="ffe23-119">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="ffe23-120">Do opublikowania</span><span class="sxs-lookup"><span data-stu-id="ffe23-120">To be published</span></span>|  
|<span data-ttu-id="ffe23-121">Application Note:</span><span class="sxs-lookup"><span data-stu-id="ffe23-121">Application Note:</span></span><br /><br /> <span data-ttu-id="ffe23-122">Za pomocą protokołu WS-Trust dla SPNEGO</span><span class="sxs-lookup"><span data-stu-id="ffe23-122">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="ffe23-123">Do opublikowania</span><span class="sxs-lookup"><span data-stu-id="ffe23-123">To be published</span></span>|  
|<span data-ttu-id="ffe23-124">Application Note:</span><span class="sxs-lookup"><span data-stu-id="ffe23-124">Application Note:</span></span><br /><br /> <span data-ttu-id="ffe23-125">Usługi sieci Web, odnoszący się odwołania do punktu końcowego i tożsamości</span><span class="sxs-lookup"><span data-stu-id="ffe23-125">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="ffe23-126">Do opublikowania</span><span class="sxs-lookup"><span data-stu-id="ffe23-126">To be published</span></span>|  
|<span data-ttu-id="ffe23-127">WS-SecurityPolicy 1.1</span><span class="sxs-lookup"><span data-stu-id="ffe23-127">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="ffe23-128">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="ffe23-128">(2005/07)</span></span>|<http://specs.xmlsoap.org/ws/2005/07/securitypolicy/ws-securitypolicy.pdf><br /><br /> <span data-ttu-id="ffe23-129">ostatnio zmienione przez [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) przesłane do Komitet Techniczny usługi WS-SX OASIS</span><span class="sxs-lookup"><span data-stu-id="ffe23-129">as amended by [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) submitted to OASIS WS-SX Technical Committee</span></span> |  
  
 <span data-ttu-id="ffe23-130">Usługi WCF, wersja 1, zapewnia 17 tryby uwierzytelniania, które mogą służyć jako podstawa dla konfiguracji zabezpieczeń usług sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ffe23-130">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="ffe23-131">Każdego trybu została zoptymalizowana pod kątem wspólny zbiór wymagania dotyczące wdrażania, takich jak:</span><span class="sxs-lookup"><span data-stu-id="ffe23-131">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
- <span data-ttu-id="ffe23-132">Poświadczenia używane do uwierzytelniania klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="ffe23-132">Credentials used to authenticate client and service.</span></span>  
  
- <span data-ttu-id="ffe23-133">Mechanizmy ochrony zabezpieczeń wiadomości lub transportu.</span><span class="sxs-lookup"><span data-stu-id="ffe23-133">Message or transport security protection mechanisms.</span></span>  
  
- <span data-ttu-id="ffe23-134">Wzorce wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ffe23-134">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="ffe23-135">Tryb uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="ffe23-135">Authentication Mode</span></span>|<span data-ttu-id="ffe23-136">Uwierzytelnianie klienta</span><span class="sxs-lookup"><span data-stu-id="ffe23-136">Client Authentication</span></span>|<span data-ttu-id="ffe23-137">Uwierzytelnianie serwera</span><span class="sxs-lookup"><span data-stu-id="ffe23-137">Server Authentication</span></span>|<span data-ttu-id="ffe23-138">Tryb</span><span class="sxs-lookup"><span data-stu-id="ffe23-138">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="ffe23-139">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="ffe23-139">UserNameOverTransport</span></span>|<span data-ttu-id="ffe23-140">Nazwa użytkownika/hasło</span><span class="sxs-lookup"><span data-stu-id="ffe23-140">User name/password</span></span>|<span data-ttu-id="ffe23-141">X509</span><span class="sxs-lookup"><span data-stu-id="ffe23-141">X509</span></span>|<span data-ttu-id="ffe23-142">Transport</span><span class="sxs-lookup"><span data-stu-id="ffe23-142">Transport</span></span>|  
|<span data-ttu-id="ffe23-143">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="ffe23-143">CertificateOverTransport</span></span>|<span data-ttu-id="ffe23-144">X509</span><span class="sxs-lookup"><span data-stu-id="ffe23-144">X509</span></span>|<span data-ttu-id="ffe23-145">X509</span><span class="sxs-lookup"><span data-stu-id="ffe23-145">X509</span></span>|<span data-ttu-id="ffe23-146">Transport</span><span class="sxs-lookup"><span data-stu-id="ffe23-146">Transport</span></span>|  
|<span data-ttu-id="ffe23-147">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="ffe23-147">KerberosOverTransport</span></span>|<span data-ttu-id="ffe23-148">Windows</span><span class="sxs-lookup"><span data-stu-id="ffe23-148">Windows</span></span>|<span data-ttu-id="ffe23-149">X509</span><span class="sxs-lookup"><span data-stu-id="ffe23-149">X509</span></span>|<span data-ttu-id="ffe23-150">Transport</span><span class="sxs-lookup"><span data-stu-id="ffe23-150">Transport</span></span>|  
|<span data-ttu-id="ffe23-151">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="ffe23-151">IssuedTokenOverTransport</span></span>|<span data-ttu-id="ffe23-152">Federacyjna</span><span class="sxs-lookup"><span data-stu-id="ffe23-152">Federated</span></span>|<span data-ttu-id="ffe23-153">X509</span><span class="sxs-lookup"><span data-stu-id="ffe23-153">X509</span></span>|<span data-ttu-id="ffe23-154">Transport</span><span class="sxs-lookup"><span data-stu-id="ffe23-154">Transport</span></span>|  
|<span data-ttu-id="ffe23-155">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="ffe23-155">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="ffe23-156">Interfejs Sspi Windows negocjowane</span><span class="sxs-lookup"><span data-stu-id="ffe23-156">Windows Sspi Negotiated</span></span>|<span data-ttu-id="ffe23-157">Interfejs Sspi Windows negocjowane</span><span class="sxs-lookup"><span data-stu-id="ffe23-157">Windows Sspi Negotiated</span></span>|<span data-ttu-id="ffe23-158">Transport</span><span class="sxs-lookup"><span data-stu-id="ffe23-158">Transport</span></span>|  
|<span data-ttu-id="ffe23-159">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="ffe23-159">AnonymousForCertificate</span></span>|<span data-ttu-id="ffe23-160">Brak</span><span class="sxs-lookup"><span data-stu-id="ffe23-160">None</span></span>|<span data-ttu-id="ffe23-161">X509</span><span class="sxs-lookup"><span data-stu-id="ffe23-161">X509</span></span>|<span data-ttu-id="ffe23-162">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ffe23-162">Message</span></span>|  
|<span data-ttu-id="ffe23-163">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="ffe23-163">UserNameForCertificate</span></span>|<span data-ttu-id="ffe23-164">Nazwa użytkownika/hasło</span><span class="sxs-lookup"><span data-stu-id="ffe23-164">User name/password</span></span>|<span data-ttu-id="ffe23-165">X509</span><span class="sxs-lookup"><span data-stu-id="ffe23-165">X509</span></span>|<span data-ttu-id="ffe23-166">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ffe23-166">Message</span></span>|  
|<span data-ttu-id="ffe23-167">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="ffe23-167">MutualCertificate</span></span>|<span data-ttu-id="ffe23-168">X509</span><span class="sxs-lookup"><span data-stu-id="ffe23-168">X509</span></span>|<span data-ttu-id="ffe23-169">X509</span><span class="sxs-lookup"><span data-stu-id="ffe23-169">X509</span></span>|<span data-ttu-id="ffe23-170">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ffe23-170">Message</span></span>|  
|<span data-ttu-id="ffe23-171">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="ffe23-171">MutualCertificateDuplex</span></span>|<span data-ttu-id="ffe23-172">X509</span><span class="sxs-lookup"><span data-stu-id="ffe23-172">X509</span></span>|<span data-ttu-id="ffe23-173">X509</span><span class="sxs-lookup"><span data-stu-id="ffe23-173">X509</span></span>|<span data-ttu-id="ffe23-174">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ffe23-174">Message</span></span>|  
|<span data-ttu-id="ffe23-175">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="ffe23-175">IssuedTokenForCertificate</span></span>|<span data-ttu-id="ffe23-176">Federacyjna</span><span class="sxs-lookup"><span data-stu-id="ffe23-176">Federated</span></span>|<span data-ttu-id="ffe23-177">X509</span><span class="sxs-lookup"><span data-stu-id="ffe23-177">X509</span></span>|<span data-ttu-id="ffe23-178">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ffe23-178">Message</span></span>|  
|<span data-ttu-id="ffe23-179">Kerberos</span><span class="sxs-lookup"><span data-stu-id="ffe23-179">Kerberos</span></span>|<span data-ttu-id="ffe23-180">Windows</span><span class="sxs-lookup"><span data-stu-id="ffe23-180">Windows</span></span>|<span data-ttu-id="ffe23-181">Windows</span><span class="sxs-lookup"><span data-stu-id="ffe23-181">Windows</span></span>|<span data-ttu-id="ffe23-182">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ffe23-182">Message</span></span>|  
|<span data-ttu-id="ffe23-183">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="ffe23-183">IssuedToken</span></span>|<span data-ttu-id="ffe23-184">Federacyjna</span><span class="sxs-lookup"><span data-stu-id="ffe23-184">Federated</span></span>|<span data-ttu-id="ffe23-185">Federacyjna</span><span class="sxs-lookup"><span data-stu-id="ffe23-185">Federated</span></span>|<span data-ttu-id="ffe23-186">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ffe23-186">Message</span></span>|  
|<span data-ttu-id="ffe23-187">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="ffe23-187">SspiNegotiated</span></span>|<span data-ttu-id="ffe23-188">Interfejs Sspi Windows negocjowane</span><span class="sxs-lookup"><span data-stu-id="ffe23-188">Windows Sspi Negotiated</span></span>|<span data-ttu-id="ffe23-189">Interfejs Sspi Windows negocjowane</span><span class="sxs-lookup"><span data-stu-id="ffe23-189">Windows Sspi Negotiated</span></span>|<span data-ttu-id="ffe23-190">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ffe23-190">Message</span></span>|  
|<span data-ttu-id="ffe23-191">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ffe23-191">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="ffe23-192">Brak</span><span class="sxs-lookup"><span data-stu-id="ffe23-192">None</span></span>|<span data-ttu-id="ffe23-193">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="ffe23-193">X509, TLS-Nego</span></span>|<span data-ttu-id="ffe23-194">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ffe23-194">Message</span></span>|  
|<span data-ttu-id="ffe23-195">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ffe23-195">UserNameForSslNegotiated</span></span>|<span data-ttu-id="ffe23-196">Nazwa użytkownika/hasło</span><span class="sxs-lookup"><span data-stu-id="ffe23-196">User name/password</span></span>|<span data-ttu-id="ffe23-197">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="ffe23-197">X509, TLS-Nego</span></span>|<span data-ttu-id="ffe23-198">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ffe23-198">Message</span></span>|  
|<span data-ttu-id="ffe23-199">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ffe23-199">MutualSslNegotiated</span></span>|<span data-ttu-id="ffe23-200">X509</span><span class="sxs-lookup"><span data-stu-id="ffe23-200">X509</span></span>|<span data-ttu-id="ffe23-201">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="ffe23-201">X509, TLS-Nego</span></span>|<span data-ttu-id="ffe23-202">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ffe23-202">Message</span></span>|  
|<span data-ttu-id="ffe23-203">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ffe23-203">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="ffe23-204">Federacyjna</span><span class="sxs-lookup"><span data-stu-id="ffe23-204">Federated</span></span>|<span data-ttu-id="ffe23-205">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="ffe23-205">X509, TLS-Nego</span></span>|<span data-ttu-id="ffe23-206">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ffe23-206">Message</span></span>|  
  
 <span data-ttu-id="ffe23-207">Punktów końcowych przy użyciu tych trybów uwierzytelniania można wyrazić swoje wymagania dotyczące zabezpieczeń przy użyciu usługi WS-SecurityPolicy (WS-SP).</span><span class="sxs-lookup"><span data-stu-id="ffe23-207">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="ffe23-208">W tym dokumencie opisano strukturę nagłówka zabezpieczeń i infrastruktury komunikatów dla każdego trybu uwierzytelniania i zawiera przykłady zasad i wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ffe23-208">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="ffe23-209">Usługi WCF korzysta z protokołu WS-SecureConversation do zapewnienia obsługi bezpiecznych sesji, aby chronić wymianę wielu komunikatów między aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="ffe23-209">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="ffe23-210">Implementacja informacji na ten temat można znaleźć w "Secure sesji" poniżej.</span><span class="sxs-lookup"><span data-stu-id="ffe23-210">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="ffe23-211">Oprócz trybów uwierzytelniania WCF zawiera ustawienia, aby kontrolować popularne mechanizmy ochrony, które dotyczą większości trybów uwierzytelniania opartego na zabezpieczeń wiadomości, na przykład: kolejność podpisu i operacji szyfrowania, zestawy Algorytm wyprowadzania klucza , a potwierdzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="ffe23-211">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="ffe23-212">W tym dokumencie służą następujące przestrzenie nazw i prefiksy.</span><span class="sxs-lookup"><span data-stu-id="ffe23-212">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="ffe23-213">Prefiks</span><span class="sxs-lookup"><span data-stu-id="ffe23-213">Prefix</span></span>|<span data-ttu-id="ffe23-214">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="ffe23-214">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="ffe23-215">s</span><span class="sxs-lookup"><span data-stu-id="ffe23-215">s</span></span>|<https://www.w3.org/2003/05/soap-envelope/>|
|<span data-ttu-id="ffe23-216">SP</span><span class="sxs-lookup"><span data-stu-id="ffe23-216">sp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/>|
|<span data-ttu-id="ffe23-217">a</span><span class="sxs-lookup"><span data-stu-id="ffe23-217">a</span></span>|<https://www.w3.org/2005/08/addressing>|  
|<span data-ttu-id="ffe23-218">wsse</span><span class="sxs-lookup"><span data-stu-id="ffe23-218">wsse</span></span>|<span data-ttu-id="ffe23-219">TBD — IDENTYFIKATOR URI PROGRAMU WSS 1.0 JĘZYKA OASIS</span><span class="sxs-lookup"><span data-stu-id="ffe23-219">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="ffe23-220">wsse11</span><span class="sxs-lookup"><span data-stu-id="ffe23-220">wsse11</span></span>|<span data-ttu-id="ffe23-221">TBD — IDENTYFIKATOR URI PROGRAMU WSS 1.1 OASIS</span><span class="sxs-lookup"><span data-stu-id="ffe23-221">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="ffe23-222">wsu</span><span class="sxs-lookup"><span data-stu-id="ffe23-222">wsu</span></span>|<span data-ttu-id="ffe23-223">TBD — narzędzie do identyfikatora URI języka OASIS WSS 1.0</span><span class="sxs-lookup"><span data-stu-id="ffe23-223">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="ffe23-224">ds</span><span class="sxs-lookup"><span data-stu-id="ffe23-224">ds</span></span>|<span data-ttu-id="ffe23-225">TBD — identyfikator URI XMLDSig W3C</span><span class="sxs-lookup"><span data-stu-id="ffe23-225">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="ffe23-226">wst</span><span class="sxs-lookup"><span data-stu-id="ffe23-226">wst</span></span>|<span data-ttu-id="ffe23-227">TBD — identyfikator URI protokołu WS-Trust 2005/02</span><span class="sxs-lookup"><span data-stu-id="ffe23-227">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="ffe23-228">wssc</span><span class="sxs-lookup"><span data-stu-id="ffe23-228">wssc</span></span>|<span data-ttu-id="ffe23-229">TBD – WS-SecureConversation 2005/02 URI</span><span class="sxs-lookup"><span data-stu-id="ffe23-229">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="ffe23-230">wsaw</span><span class="sxs-lookup"><span data-stu-id="ffe23-230">wsaw</span></span>|<span data-ttu-id="ffe23-231">TBD — przestrzeń nazw usługi WS-Addressing zasad</span><span class="sxs-lookup"><span data-stu-id="ffe23-231">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="ffe23-232">WSP</span><span class="sxs-lookup"><span data-stu-id="ffe23-232">wsp</span></span>|<http://schemas.xmlsoap.org/ws/2004/09/policy>|  
|<span data-ttu-id="ffe23-233">mssp</span><span class="sxs-lookup"><span data-stu-id="ffe23-233">mssp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy>|
  
## <a name="1-token-profiles"></a><span data-ttu-id="ffe23-234">1. Profile tokenu</span><span class="sxs-lookup"><span data-stu-id="ffe23-234">1. Token Profiles</span></span>  
 <span data-ttu-id="ffe23-235">Specyfikacje zabezpieczenia usług sieci Web reprezentują poświadczeń jako tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="ffe23-235">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="ffe23-236">Usługi WCF obsługuje następujące typy tokenów:</span><span class="sxs-lookup"><span data-stu-id="ffe23-236">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="ffe23-237">1.1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="ffe23-237">1.1 UsernameToken</span></span>  
 <span data-ttu-id="ffe23-238">Usługi WCF następujące profile UsernameToken10 i UsernameToken11 z następującymi ograniczeniami:</span><span class="sxs-lookup"><span data-stu-id="ffe23-238">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="ffe23-239">R1101 PasswordType atrybutu elementu UsernameToken\Password musi albo zostać pominięty ani mieć wartości #PasswordText (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="ffe23-239">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="ffe23-240">Jeden można zaimplementować #PasswordDigest za pomocą funkcji rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="ffe23-240">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="ffe23-241">Zaobserwowano, że #PasswordDigest został często mylone jako mechanizm ochrony dostatecznie bezpieczne hasło.</span><span class="sxs-lookup"><span data-stu-id="ffe23-241">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="ffe23-242">Ale #PasswordDigest nie może służyć jako substytut dla szyfrowania UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="ffe23-242">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="ffe23-243">Podstawowym celem #PasswordDigest to ochronę przed atakami powtarzania.</span><span class="sxs-lookup"><span data-stu-id="ffe23-243">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="ffe23-244">W trybach uwierzytelniania WCF powtarzania atak zagrożeń zostaną skorygowane przy użyciu sygnatury komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ffe23-244">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="ffe23-245">B1102 WCF nigdy nie emituje jednorazowego i utworzono elementy podrzędne UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="ffe23-245">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="ffe23-246">Te elementy podrzędne mają na celu pomóc wykrywania powtarzania.</span><span class="sxs-lookup"><span data-stu-id="ffe23-246">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="ffe23-247">Usługi WCF zamiast nich używa sygnatury komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ffe23-247">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="ffe23-248">OASIS WSS protokołu SOAP wiadomości zabezpieczeń UsernameToken Profile 1.1 (UsernameToken11) wprowadzono klucza pochodnego od funkcji haseł.</span><span class="sxs-lookup"><span data-stu-id="ffe23-248">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="ffe23-249">B1103 UsernameToken hasło nie może być używany dla klucza pochodnego i w związku z tym do operacji kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="ffe23-249">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="ffe23-250">Uzasadnienie: hasła są zazwyczaj uważane za zbyt słabe ma być używany dla operacji kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="ffe23-250">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="ffe23-251">1.2 x 509 tokenu</span><span class="sxs-lookup"><span data-stu-id="ffe23-251">1.2 X509 Token</span></span>  
 <span data-ttu-id="ffe23-252">Program WCF obsługuje certyfikaty X509v3 jako typu poświadczeń i X509TokenProfile1.0 i X509TokenProfile1.1 jest zgodna z następującymi ograniczeniami:</span><span class="sxs-lookup"><span data-stu-id="ffe23-252">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="ffe23-253">Atrybut ValueType R1201 w elemencie BinarySecurityToken musi mieć wartość #X509v3, gdy zawiera on certyfikat X509v3.</span><span class="sxs-lookup"><span data-stu-id="ffe23-253">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="ffe23-254">Grupie WSS X509 tokenu profilu 1.0 i 1.1 zdefiniuj również #X509PKIPathv1 i PKCS7 # jako typów wartości.</span><span class="sxs-lookup"><span data-stu-id="ffe23-254">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="ffe23-255">Usługi WCF nie obsługuje tego typu.</span><span class="sxs-lookup"><span data-stu-id="ffe23-255">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="ffe23-256">R1202 czy rozszerzenia SubjectKeyIdentifier (NARCIARSKIE) znajduje się w X509 certyfikatu, wsse:KeyIdentifier powinna być używana do odwołania zewnętrzne do tokenu, za pomocą ValueType atrybutu jako #X509SubjectKeyIdentifier i jego zawartości wartość algorytmem Base64 rozszerzenie NARCIARSKIE certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="ffe23-256">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="ffe23-257">Odwołania NARCIARSKIE powszechnie implementowanych i sprawdzone na typ wysoce interoperacyjne odwołania zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="ffe23-257">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="ffe23-258">R1203 Odwołanie zewnętrzne do X509 zabezpieczeń tokenu nie powinien używać ds:X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="ffe23-258">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="ffe23-259">R1204 X509TokenProfile1.1 Jeśli jest używany, odwołanie zewnętrzne do X509 zabezpieczeń tokenu należy używać odcisku palca, wynikające z 1.1 WS-Security.</span><span class="sxs-lookup"><span data-stu-id="ffe23-259">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="ffe23-260">Usługi WCF obsługuje X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="ffe23-260">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="ffe23-261">Istnieją jednak zagadnienia dotyczące współdziałania z X509IssuerSerial: Usługi WCF używa parametrów, aby porównać dwie wartości X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="ffe23-261">However There are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="ffe23-262">W związku z tym jeśli jeden zmienia kolejność elementów w nazwie podmiotu i wysyła do usługi WCF z odwołaniem do certyfikatu, jego mogą nie być odnajdowane.</span><span class="sxs-lookup"><span data-stu-id="ffe23-262">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="ffe23-263">1.3 Token protokołu Kerberos</span><span class="sxs-lookup"><span data-stu-id="ffe23-263">1.3 Kerberos Token</span></span>  
 <span data-ttu-id="ffe23-264">Usługi WCF obsługuje KerberosTokenProfile1.1 na potrzeby uwierzytelniania Windows z następującymi ograniczeniami:</span><span class="sxs-lookup"><span data-stu-id="ffe23-264">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="ffe23-265">R1301 Kerberos tokenu musi zawierać wartość GSS opakowane AP_REQ v4 protokołu Kerberos, zgodnie z definicją w GSS_API i specyfikacji protokołu Kerberos, a musi mieć atrybut ValueType o wartości GSS_Kerberosv5_AP_REQ #.</span><span class="sxs-lookup"><span data-stu-id="ffe23-265">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="ffe23-266">Zastosowań WCF GSS opakowane Kerberos uwierzytelniania Kerberos, nie bez AP-REQ.</span><span class="sxs-lookup"><span data-stu-id="ffe23-266">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="ffe23-267">Jest to ze względów bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="ffe23-267">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="ffe23-268">1.4 SAML w wersji 1.1 tokenu</span><span class="sxs-lookup"><span data-stu-id="ffe23-268">1.4 SAML v1.1 Token</span></span>  
 <span data-ttu-id="ffe23-269">Usługi WCF obsługuje profile tokenu języka SAML WSS 1.0 i 1.1 tokenów w wersji 1.1 protokołu SAML.</span><span class="sxs-lookup"><span data-stu-id="ffe23-269">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="ffe23-270">Istnieje możliwość zaimplementowania inne wersje formatów tokenu języka SAML.</span><span class="sxs-lookup"><span data-stu-id="ffe23-270">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="ffe23-271">W wersji 1.5 Token kontekstu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ffe23-271">1.5 Security Context Token</span></span>  
 <span data-ttu-id="ffe23-272">Usługi WCF obsługuje zabezpieczenia kontekstu tokenu (SCT) wprowadzone w WS SecureCoversation.</span><span class="sxs-lookup"><span data-stu-id="ffe23-272">WCF supports the Security Context Token (SCT) introduced in WS-SecureCoversation.</span></span> <span data-ttu-id="ffe23-273">SCT jest używana do reprezentowania kontekstu zabezpieczeń ustanowionych w mechanizmu SecureConversation również jako negocjacji binarnej protokoły TLS i SSPI, opisane poniżej.</span><span class="sxs-lookup"><span data-stu-id="ffe23-273">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="ffe23-274">2. Wspólne parametry zabezpieczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="ffe23-274">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="ffe23-275">2.1 Sygnatura czasowa</span><span class="sxs-lookup"><span data-stu-id="ffe23-275">2.1 TimeStamp</span></span>  
 <span data-ttu-id="ffe23-276">Obecności sygnatury czasowej jest kontrolowany przy użyciu <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> właściwość <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="ffe23-276">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="ffe23-277">Usługi WCF zawsze serializuje wsse:TimeStamp z wsse: utworzone i wsse: wygasa pola.</span><span class="sxs-lookup"><span data-stu-id="ffe23-277">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="ffe23-278">Wsse:TimeStamp zawsze jest podpisany, podczas podpisywania jest używany.</span><span class="sxs-lookup"><span data-stu-id="ffe23-278">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="ffe23-279">2.2 kolejność ochrony</span><span class="sxs-lookup"><span data-stu-id="ffe23-279">2.2 Protection Order</span></span>  
 <span data-ttu-id="ffe23-280">Usługi WCF obsługuje kolejności ochrony komunikat "Logowanie przed szyfrowania" i "Szyfrowania przed znakiem" (1.1 zasady zabezpieczeń).</span><span class="sxs-lookup"><span data-stu-id="ffe23-280">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="ffe23-281">"Sign przed Szyfruj" jest zalecane w przypadku powodów takich jak: komunikaty chronione przy użyciu szyfrowania przed logowania są otwarte ataków podstawienia podpisu, chyba że jest używany mechanizm WS-Security 1.1 SignatureConfirmation i sprawia, że podpis za pośrednictwem zaszyfrowaną zawartość Inspekcja trudniejsze.</span><span class="sxs-lookup"><span data-stu-id="ffe23-281">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="ffe23-282">2.3 sygnatury ochrony</span><span class="sxs-lookup"><span data-stu-id="ffe23-282">2.3 Signature Protection</span></span>  
 <span data-ttu-id="ffe23-283">Szyfrowanie przed znak jest używany, zaleca ochronę podpisu, aby uniemożliwić ataki siłowe dla zgadywania zaszyfrowaną zawartość lub klucza podpisywania (zwłaszcza gdy niestandardowy token jest używany z słabe materiału klucza).</span><span class="sxs-lookup"><span data-stu-id="ffe23-283">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="ffe23-284">2.4 pakiet algorytmów</span><span class="sxs-lookup"><span data-stu-id="ffe23-284">2.4 Algorithm Suite</span></span>  
 <span data-ttu-id="ffe23-285">Usługi WCF obsługuje wszystkie zestawy algorytm 1.1 zasad zabezpieczeń na liście.</span><span class="sxs-lookup"><span data-stu-id="ffe23-285">WCF supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="ffe23-286">2.5 klucza pochodnego</span><span class="sxs-lookup"><span data-stu-id="ffe23-286">2.5 Key Derivation</span></span>  
 <span data-ttu-id="ffe23-287">Usługi WCF używa "Wyprowadzania klucza dla kluczy symetrycznych", zgodnie z opisem w WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="ffe23-287">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="ffe23-288">2.6 potwierdzenie podpisu</span><span class="sxs-lookup"><span data-stu-id="ffe23-288">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="ffe23-289">Potwierdzenie podpisu mogą być jako ochrony przed atakami środkowej man chronić zestawu podpisami.</span><span class="sxs-lookup"><span data-stu-id="ffe23-289">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="ffe23-290">W wersji 2.7 układ nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ffe23-290">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="ffe23-291">Każdy tryb uwierzytelniania w tym artykule opisano niektóre układ nagłówka zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ffe23-291">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="ffe23-292">Elementy w nagłówku zabezpieczeń są częściowo uporządkowanych.</span><span class="sxs-lookup"><span data-stu-id="ffe23-292">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="ffe23-293">Aby zdefiniować kolejność elementów podrzędnych nagłówka zabezpieczeń, polityki WS-Security definiuje następujące tryby układ nagłówka zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="ffe23-293">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ffe23-294">Strict</span><span class="sxs-lookup"><span data-stu-id="ffe23-294">Strict</span></span>|<span data-ttu-id="ffe23-295">Elementy są dodawane do następujących nagłówka zabezpieczeń, że reguły numerowane układ opisanego w zasady zabezpieczeń w sekcji 7.7.1 zgodnie z ogólną zasadą "zadeklarować przed użyciem".</span><span class="sxs-lookup"><span data-stu-id="ffe23-295">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="ffe23-296">Łagodnymi</span><span class="sxs-lookup"><span data-stu-id="ffe23-296">Lax</span></span>|<span data-ttu-id="ffe23-297">Elementy są dodawane do nagłówka zabezpieczeń w dowolnej kolejności, który jest zgodny z programu WSS: SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="ffe23-297">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="ffe23-298">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="ffe23-298">LaxTimestampFirst</span></span>|<span data-ttu-id="ffe23-299">Tym samym Lax z tą różnicą, że pierwszy element w nagłówku zabezpieczeń muszą być wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="ffe23-299">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="ffe23-300">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="ffe23-300">LaxTimestampLast</span></span>|<span data-ttu-id="ffe23-301">Takie same jak łagodnymi, z tą różnicą, że ostatni element w nagłówku zabezpieczeń musi być wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="ffe23-301">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="ffe23-302">Usługi WCF obsługuje wszystkie cztery tryby układ nagłówka zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ffe23-302">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="ffe23-303">Zabezpieczeń nagłówka struktury i komunikat dla trybów uwierzytelniania poniższych przykładów w trybie "Strict".</span><span class="sxs-lookup"><span data-stu-id="ffe23-303">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="ffe23-304">2. Wspólne parametry zabezpieczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="ffe23-304">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="ffe23-305">Ta sekcja zawiera przykładowe zasady dla każdego trybu uwierzytelniania oraz przykłady pokazujące Struktura nagłówka zabezpieczeń wiadomości wymieniane przez klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="ffe23-305">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="ffe23-306">6.1 ochrony transportu</span><span class="sxs-lookup"><span data-stu-id="ffe23-306">6.1 Transport Protection</span></span>  
 <span data-ttu-id="ffe23-307">Usługi WCF zawiera pięć tryby uwierzytelniania, korzystających z bezpiecznym transportem do ochrony wiadomości; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport i SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="ffe23-307">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="ffe23-308">Te tryby uwierzytelniania są konstruowane przy użyciu opisanego w SecurityPolicy powiązania transportu.</span><span class="sxs-lookup"><span data-stu-id="ffe23-308">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="ffe23-309">W przypadku UserNameOverTransport tryb uwierzytelniania UsernameToken jest podpisany token pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="ffe23-309">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="ffe23-310">W innych trybach uwierzytelniania tokenu jest wyświetlana jako podpisany token zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="ffe23-310">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="ffe23-311">Dodatek C.1.2 i C.1.3 SecurityPolicy opisują szczegółowo układ nagłówka zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ffe23-311">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="ffe23-312">Następujące nagłówki zabezpieczeń przykład Pokaż Strict układu dla trybu uwierzytelniania danego.</span><span class="sxs-lookup"><span data-stu-id="ffe23-312">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="ffe23-313">Wartość właściwości "Klucze pochodne" dla tokenów we wszystkich przypadkach jest "false".</span><span class="sxs-lookup"><span data-stu-id="ffe23-313">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="ffe23-314">Wartości różnych właściwości powiązania transportu są następujące:</span><span class="sxs-lookup"><span data-stu-id="ffe23-314">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="ffe23-315">Sygnatura czasowa: true</span><span class="sxs-lookup"><span data-stu-id="ffe23-315">Timestamp: true</span></span>  
  
 <span data-ttu-id="ffe23-316">Układ nagłówka zabezpieczeń: Strict</span><span class="sxs-lookup"><span data-stu-id="ffe23-316">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="ffe23-317">Algorithm Suite: Basic256</span><span class="sxs-lookup"><span data-stu-id="ffe23-317">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="ffe23-318">6.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="ffe23-318">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="ffe23-319">W tym trybie uwierzytelniania klient uwierzytelnia się za pomocą Token nazwy użytkownika, który jest wyświetlany w warstwie SOAP jako podpisany token pomocniczy, które zawsze są wysyłane do adresata inicjatora.</span><span class="sxs-lookup"><span data-stu-id="ffe23-319">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="ffe23-320">Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="ffe23-320">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="ffe23-321">Wiązanie używane jest powiązania transportu.</span><span class="sxs-lookup"><span data-stu-id="ffe23-321">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="ffe23-322">Zasady</span><span class="sxs-lookup"><span data-stu-id="ffe23-322">Policy</span></span>  
  
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
  
 <span data-ttu-id="ffe23-323">Układ nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ffe23-323">Security Header Layout</span></span>  
  
 <span data-ttu-id="ffe23-324">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-324">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-325">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-325">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="ffe23-326">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="ffe23-326">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="ffe23-327">W tym trybie uwierzytelniania, który klient jest uwierzytelniany przy użyciu X.509 certyfikatu, które pojawia się w warstwie SOAP jako tokenu pomocniczego zawsze wysyłane z inicjatora do adresata.</span><span class="sxs-lookup"><span data-stu-id="ffe23-327">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="ffe23-328">Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="ffe23-328">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="ffe23-329">Wiązanie używane jest powiązania transportu.</span><span class="sxs-lookup"><span data-stu-id="ffe23-329">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="ffe23-330">Zasady</span><span class="sxs-lookup"><span data-stu-id="ffe23-330">Policy</span></span>  
  
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
  
 <span data-ttu-id="ffe23-331">Układ nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ffe23-331">Security Header Layout</span></span>  
  
 <span data-ttu-id="ffe23-332">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-332">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-333">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-333">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="ffe23-334">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="ffe23-334">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="ffe23-335">W tym trybie uwierzytelniania klient nie uwierzytelnia się do usługi, w efekcie, ale raczej przedstawia token wystawiony przez Usługa tokenu zabezpieczającego (STS) i upoważnienie wiedzę na temat klucza współużytkowanego.</span><span class="sxs-lookup"><span data-stu-id="ffe23-335">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="ffe23-336">Wystawiony token pojawi się w warstwie SOAP jako tokenu pomocniczego zawsze wysyłane z inicjatora do adresata.</span><span class="sxs-lookup"><span data-stu-id="ffe23-336">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="ffe23-337">Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="ffe23-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="ffe23-338">Powiązanie to powiązanie transportu.</span><span class="sxs-lookup"><span data-stu-id="ffe23-338">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="ffe23-339">Zasady</span><span class="sxs-lookup"><span data-stu-id="ffe23-339">Policy</span></span>  
  
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
  
 <span data-ttu-id="ffe23-340">Układ nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ffe23-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="ffe23-341">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-341">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-342">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="ffe23-343">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="ffe23-343">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="ffe23-344">W tym trybie uwierzytelniania klient uwierzytelnia się w usłudze przy użyciu biletu protokołu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="ffe23-344">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="ffe23-345">Token protokołu Kerberos jest wyświetlana w warstwie SOAP jako tokenu pomocniczego.</span><span class="sxs-lookup"><span data-stu-id="ffe23-345">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="ffe23-346">Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="ffe23-346">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="ffe23-347">Powiązanie to powiązanie transportu.</span><span class="sxs-lookup"><span data-stu-id="ffe23-347">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="ffe23-348">Zasady</span><span class="sxs-lookup"><span data-stu-id="ffe23-348">Policy</span></span>  
  
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
  
 <span data-ttu-id="ffe23-349">Układ nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ffe23-349">Security Header Layout</span></span>  
  
 <span data-ttu-id="ffe23-350">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-350">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-351">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-351">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="ffe23-352">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="ffe23-352">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="ffe23-353">W tym trybie protokół negocjacji służy do uwierzytelniania klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="ffe23-353">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="ffe23-354">Protokół Kerberos jest używany, jeśli jest to możliwe, w przeciwnym razie uwierzytelnianie NTLM.</span><span class="sxs-lookup"><span data-stu-id="ffe23-354">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="ffe23-355">Wynikowy SCT pojawia się w warstwie SOAP jako tokenu pomocniczego zawsze wysyłane z inicjatora do adresata.</span><span class="sxs-lookup"><span data-stu-id="ffe23-355">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="ffe23-356">Usługa również jest uwierzytelniany w warstwie transportowej przez certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="ffe23-356">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="ffe23-357">Wiązanie używane jest powiązania transportu.</span><span class="sxs-lookup"><span data-stu-id="ffe23-357">The binding used is a transport binding.</span></span> <span data-ttu-id="ffe23-358">"SPNEGO" (negocjacji) opisano, jak WCF za pomocą interfejsu SSPI negocjacji binarnej protokołu WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="ffe23-358">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="ffe23-359">Przykłady nagłówka zabezpieczeń w tej sekcji są po SCT została ustanowiona przy użyciu uzgadnianie SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="ffe23-359">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="ffe23-360">Zasady</span><span class="sxs-lookup"><span data-stu-id="ffe23-360">Policy</span></span>  
  
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
  
### <a name="security-header-examples"></a><span data-ttu-id="ffe23-361">Przykłady nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ffe23-361">Security Header Examples</span></span>  
 <span data-ttu-id="ffe23-362">Gdy Token kontekstu zabezpieczeń zostanie nawiązane za pośrednictwem uzgadnianie SPNEGO przy użyciu protokołu WS-Trust negocjacji binarnej, komunikatów aplikacji ma nagłówki zabezpieczeń o następującej strukturze.</span><span class="sxs-lookup"><span data-stu-id="ffe23-362">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="ffe23-363">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-363">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-364">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-364">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="ffe23-365">6.2 przy użyciu certyfikatów X.509 dla usługi uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="ffe23-365">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="ffe23-366">W tej sekcji opisano następujące tryby uwierzytelniania: MutualCertificate WSS1.0, wzajemne CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate i IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="ffe23-366">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="ffe23-367">6.2.1 MutualCertificate WSS1.0</span><span class="sxs-lookup"><span data-stu-id="ffe23-367">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="ffe23-368">W tym trybie uwierzytelniania, który klient jest uwierzytelniany przy użyciu X.509 certyfikatu, która jest wyświetlana jako token inicjatora w warstwie protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="ffe23-368">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="ffe23-369">Usługa jest również uwierzytelniany przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="ffe23-369">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="ffe23-370">Powiązania używanego to asymetryczny powiązania z następującymi wartościami właściwości:</span><span class="sxs-lookup"><span data-stu-id="ffe23-370">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="ffe23-371">Token inicjatora: klienta certyfikat X.509 z trybem włączenia równa .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="ffe23-371">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="ffe23-372">Odbiorcy tokenu: Certyfikat X.509 serwera w trybie dołączania ustawiono .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="ffe23-372">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="ffe23-373">Ochrona tokenu: False</span><span class="sxs-lookup"><span data-stu-id="ffe23-373">Token Protection: False</span></span>  
  
 <span data-ttu-id="ffe23-374">Cały nagłówek i treść podpisów: Prawda</span><span class="sxs-lookup"><span data-stu-id="ffe23-374">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="ffe23-375">Kolejność ochrony: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="ffe23-375">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="ffe23-376">Szyfruj podpisu: Prawda</span><span class="sxs-lookup"><span data-stu-id="ffe23-376">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="ffe23-377">Zasady</span><span class="sxs-lookup"><span data-stu-id="ffe23-377">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ffe23-378">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ffe23-378">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ffe23-379">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-379">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-380">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-380">Response</span></span>  
  
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
  
 <span data-ttu-id="ffe23-381">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ffe23-381">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="ffe23-382">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-382">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-383">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-383">Response</span></span>  
  
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
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="ffe23-384">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="ffe23-384">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="ffe23-385">W tym trybie uwierzytelniania, który klient jest uwierzytelniany przy użyciu X.509 certyfikatu, która jest wyświetlana jako token inicjatora w warstwie protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="ffe23-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="ffe23-386">Usługa jest również uwierzytelniany przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="ffe23-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="ffe23-387">Powiązania używanego to asymetryczny powiązania z następującymi wartościami właściwości:</span><span class="sxs-lookup"><span data-stu-id="ffe23-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="ffe23-388">Token inicjatora: X509 klienta certyfikatu, tryb dołączania jest ustawiony na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="ffe23-388">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="ffe23-389">Odbiorcy tokenu: X509 serwera certyfikatów, tryb dołączania jest ustawiony na .../IncludeToken/AlwaysToInitiator</span><span class="sxs-lookup"><span data-stu-id="ffe23-389">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="ffe23-390">Ochrona tokenu: False</span><span class="sxs-lookup"><span data-stu-id="ffe23-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="ffe23-391">Cały nagłówek i treść podpisów: Prawda</span><span class="sxs-lookup"><span data-stu-id="ffe23-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="ffe23-392">Kolejność ochrony: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="ffe23-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="ffe23-393">Szyfruj podpisu: Prawda</span><span class="sxs-lookup"><span data-stu-id="ffe23-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="ffe23-394">Zasady</span><span class="sxs-lookup"><span data-stu-id="ffe23-394">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ffe23-395">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ffe23-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ffe23-396">Żądania i odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="ffe23-396">Request and Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ffe23-397">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ffe23-397">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ffe23-398">Żądania i odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="ffe23-398">Request and Response</span></span>  
  
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
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="ffe23-399">6.2.3 przy użyciu SymmetricBinding X.509 usługi uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="ffe23-399">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="ffe23-400">"WSS10" parametru ograniczoną obsługę scenariuszy obejmujących X509 tokenów.</span><span class="sxs-lookup"><span data-stu-id="ffe23-400">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="ffe23-401">Na przykład nie było możliwości w celu zapewnienia ochrony podpis i szyfrowanie komunikatów przy użyciu tylko usługa X509 tokenu.</span><span class="sxs-lookup"><span data-stu-id="ffe23-401">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="ffe23-402">"WSS11" wprowadzono użycie EncryptedKey jako token symetryczny.</span><span class="sxs-lookup"><span data-stu-id="ffe23-402">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="ffe23-403">Teraz klucz tymczasowy, szyfrowane certyfikacie X.509 może służyć do ochrony komunikatów żądań i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="ffe23-403">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="ffe23-404">Tryby uwierzytelniania opisanego w sekcji 6.4 poniżej Użyj tego wzorca.</span><span class="sxs-lookup"><span data-stu-id="ffe23-404">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="ffe23-405">WS SecurityPolicy opisuje tego wzorca SymmetricBinding przy użyciu usługi X509 token jako token ochrony.</span><span class="sxs-lookup"><span data-stu-id="ffe23-405">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="ffe23-406">Tryby uwierzytelniania AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 i IssuedTokenForCertificate wszystkie za pomocą podobne wystąpienie sp:SymmetricBinding następujące wartości właściwości:</span><span class="sxs-lookup"><span data-stu-id="ffe23-406">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="ffe23-407">Token ochrony: X509 serwera certyfikatów, tryb dołączania jest ustawiony na .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="ffe23-407">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="ffe23-408">Ochrona tokenu: False</span><span class="sxs-lookup"><span data-stu-id="ffe23-408">Token Protection: False</span></span>  
  
 <span data-ttu-id="ffe23-409">Cały nagłówek i treść podpisów: Prawda</span><span class="sxs-lookup"><span data-stu-id="ffe23-409">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="ffe23-410">Kolejność ochrony: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="ffe23-410">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="ffe23-411">Szyfruj podpisu: Prawda</span><span class="sxs-lookup"><span data-stu-id="ffe23-411">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="ffe23-412">Powyższe tryby uwierzytelniania różnią się tylko tokenów pomocniczych, których używają.</span><span class="sxs-lookup"><span data-stu-id="ffe23-412">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="ffe23-413">AnonymousForCertificate, nie ma żadnych tokenów pomocniczych, MutualCertificate WSS 1.1 ma klienta X509 certyfikatu jako potwierdzających Obsługa tokenów, UserNameForCertificate ma Token nazwy użytkownika jako podpisany token pomocniczy i IssuedTokenForCertificate jest wystawiony token tokenu pomocniczego.</span><span class="sxs-lookup"><span data-stu-id="ffe23-413">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="ffe23-414">Zasady</span><span class="sxs-lookup"><span data-stu-id="ffe23-414">Policy</span></span>  
  
 <span data-ttu-id="ffe23-415">Symetryczne powiązania</span><span class="sxs-lookup"><span data-stu-id="ffe23-415">Symmetric Binding</span></span>  
  
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
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="ffe23-416">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="ffe23-416">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="ffe23-417">W tym trybie uwierzytelniania klienta jest anonimowa, a usługa jest uwierzytelniany przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="ffe23-417">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="ffe23-418">Wiązanie używane jest wystąpienie symetrycznego powiązania zgodnie z opisem w 6.4.2.</span><span class="sxs-lookup"><span data-stu-id="ffe23-418">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="ffe23-419">Zasady</span><span class="sxs-lookup"><span data-stu-id="ffe23-419">Policy</span></span>  
  
 <span data-ttu-id="ffe23-420">Aby uzyskać szczegóły powiązania, zobacz "Policy" w powyższej 6.2.3</span><span class="sxs-lookup"><span data-stu-id="ffe23-420">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ffe23-421">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ffe23-421">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ffe23-422">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-422">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-423">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-423">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ffe23-424">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ffe23-424">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ffe23-425">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-425">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-426">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-426">Response</span></span>  
  
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
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="ffe23-427">6.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="ffe23-427">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="ffe23-428">W tym trybie uwierzytelniania klient uwierzytelnia się do usługi przy użyciu Token nazwy użytkownika, który jest wyświetlany w warstwie SOAP jako podpisany token pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="ffe23-428">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="ffe23-429">Usługa jest uwierzytelniany przez klienta za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="ffe23-429">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="ffe23-430">Wiązanie używane jest symetryczne powiązania z tokenem ochrony jest klucz generowany przez klienta, szyfrowane przy użyciu klucza publicznego usługi.</span><span class="sxs-lookup"><span data-stu-id="ffe23-430">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="ffe23-431">Zasady</span><span class="sxs-lookup"><span data-stu-id="ffe23-431">Policy</span></span>  
  
 <span data-ttu-id="ffe23-432">Aby uzyskać szczegóły powiązania, zobacz "Policy" w powyższej 6.2.3</span><span class="sxs-lookup"><span data-stu-id="ffe23-432">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="ffe23-433">Podpisany Token pomocniczy</span><span class="sxs-lookup"><span data-stu-id="ffe23-433">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ffe23-434">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ffe23-434">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ffe23-435">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-435">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-436">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-436">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ffe23-437">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ffe23-437">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ffe23-438">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-438">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-439">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-439">Response</span></span>  
  
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
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="ffe23-440">6.2.6 MutualCertificate (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="ffe23-440">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="ffe23-441">W tym trybie uwierzytelniania, który klient jest uwierzytelniany przy użyciu X.509 certyfikatu, która jest wyświetlana jako tokenu pomocniczego w warstwie protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="ffe23-441">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="ffe23-442">Usługa jest również uwierzytelniany przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="ffe23-442">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="ffe23-443">Wiązanie używane jest symetryczne powiązania z tokenem ochrony jest klucz generowany przez klienta, szyfrowane przy użyciu klucza publicznego usługi.</span><span class="sxs-lookup"><span data-stu-id="ffe23-443">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="ffe23-444">Zasady</span><span class="sxs-lookup"><span data-stu-id="ffe23-444">Policy</span></span>  
  
 <span data-ttu-id="ffe23-445">Zobacz zasady w 6.2.3 powiązania szczegóły</span><span class="sxs-lookup"><span data-stu-id="ffe23-445">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="ffe23-446">Potwierdzających tokenu obsługi</span><span class="sxs-lookup"><span data-stu-id="ffe23-446">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ffe23-447">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ffe23-447">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ffe23-448">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-448">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-449">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-449">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ffe23-450">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ffe23-450">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ffe23-451">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-451">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-452">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-452">Response</span></span>  
  
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
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="ffe23-453">6.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="ffe23-453">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="ffe23-454">Z tego uwierzytelnienia tryb, który jako takie, ale zamiast tego klient nie uwierzytelniania w usłudze przedstawia token wystawiony przez usługę STS i upoważnienie wiedzę na temat klucza współużytkowanego.</span><span class="sxs-lookup"><span data-stu-id="ffe23-454">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="ffe23-455">Wystawiony token pojawi się w warstwie SOAP jako tokenu pomocniczego.</span><span class="sxs-lookup"><span data-stu-id="ffe23-455">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="ffe23-456">Usługa jest uwierzytelniany przez klienta za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="ffe23-456">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="ffe23-457">Wiązanie używane jest symetryczne powiązania z tokenem ochrony jest klucz generowany przez klienta, szyfrowane przy użyciu klucza publicznego usługi.</span><span class="sxs-lookup"><span data-stu-id="ffe23-457">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="ffe23-458">Zasady</span><span class="sxs-lookup"><span data-stu-id="ffe23-458">Policy</span></span>  
  
 <span data-ttu-id="ffe23-459">Zobacz zasady w 6.2.3 powyżej, aby uzyskać szczegółowe informacje powiązania</span><span class="sxs-lookup"><span data-stu-id="ffe23-459">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="ffe23-460">Potwierdzających tokenu obsługi</span><span class="sxs-lookup"><span data-stu-id="ffe23-460">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ffe23-461">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ffe23-461">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ffe23-462">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-462">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-463">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-463">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ffe23-464">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ffe23-464">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ffe23-465">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-465">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-466">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-466">Response</span></span>  
  
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
  
## <a name="63-kerberos"></a><span data-ttu-id="ffe23-467">6.3 protokołu Kerberos</span><span class="sxs-lookup"><span data-stu-id="ffe23-467">6.3 Kerberos</span></span>  
 <span data-ttu-id="ffe23-468">W tym trybie uwierzytelniania klient uwierzytelnia się w usłudze przy użyciu biletu protokołu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="ffe23-468">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="ffe23-469">Korzystając z tego samego biletu zapewnia również uwierzytelnianie serwera.</span><span class="sxs-lookup"><span data-stu-id="ffe23-469">That same ticket also provides server authentication.</span></span> <span data-ttu-id="ffe23-470">Wiązanie używane jest symetryczne powiązania z następującymi właściwościami;</span><span class="sxs-lookup"><span data-stu-id="ffe23-470">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="ffe23-471">Token ochrony: Bilet protokołu Kerberos, tryb dołączania jest ustawiony na .../IncludeToken/Once</span><span class="sxs-lookup"><span data-stu-id="ffe23-471">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="ffe23-472">Ochrona tokenu: False</span><span class="sxs-lookup"><span data-stu-id="ffe23-472">Token Protection: False</span></span>  
  
 <span data-ttu-id="ffe23-473">Cały nagłówek i treść podpisów: Prawda</span><span class="sxs-lookup"><span data-stu-id="ffe23-473">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="ffe23-474">Kolejność ochrony: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="ffe23-474">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="ffe23-475">Szyfruj podpisu: Prawda</span><span class="sxs-lookup"><span data-stu-id="ffe23-475">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="ffe23-476">Zasady</span><span class="sxs-lookup"><span data-stu-id="ffe23-476">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ffe23-477">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ffe23-477">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ffe23-478">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-478">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-479">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-479">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ffe23-480">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ffe23-480">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ffe23-481">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-481">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="ffe23-482">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-482">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="ffe23-483">6.4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="ffe23-483">6.4 IssuedToken</span></span>  
 <span data-ttu-id="ffe23-484">W tym trybie uwierzytelniania, których klient nie uwierzytelnia się do usługi jako takie, zamiast Klient przedstawia token wystawiony przez usługę STS i upoważnienie wiedzę na temat klucza współużytkowanego.</span><span class="sxs-lookup"><span data-stu-id="ffe23-484">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="ffe23-485">Usługa nie jest uwierzytelniony do klienta jako takie, zamiast tego Usługa STS szyfruje klucz współużytkowany jako część wystawiony token taki sposób, że tylko usługi może odszyfrować klucz.</span><span class="sxs-lookup"><span data-stu-id="ffe23-485">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="ffe23-486">Wiązanie używane jest w powiązaniu symetrycznego z następującymi właściwościami;</span><span class="sxs-lookup"><span data-stu-id="ffe23-486">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="ffe23-487">Token ochrony: Wystawiony Token, tryb dołączania jest ustawiony na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="ffe23-487">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="ffe23-488">Ochrona tokenu: False</span><span class="sxs-lookup"><span data-stu-id="ffe23-488">Token Protection: False</span></span>  
  
 <span data-ttu-id="ffe23-489">Cały nagłówek i treść podpisów: Prawda</span><span class="sxs-lookup"><span data-stu-id="ffe23-489">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="ffe23-490">Kolejność ochrony: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="ffe23-490">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="ffe23-491">Szyfruj podpisu: Prawda</span><span class="sxs-lookup"><span data-stu-id="ffe23-491">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="ffe23-492">Zasady</span><span class="sxs-lookup"><span data-stu-id="ffe23-492">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ffe23-493">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ffe23-493">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ffe23-494">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-494">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-495">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-495">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ffe23-496">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ffe23-496">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ffe23-497">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-497">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-498">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-498">Response</span></span>  
  
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
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="ffe23-499">6.5 uwierzytelniania przy użyciu SslNegotiated usługi</span><span class="sxs-lookup"><span data-stu-id="ffe23-499">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="ffe23-500">W tej sekcji opisano tryby uwierzytelniania, które powiązania symetrycznego za pomocą tokenu ochrony jest kontekst tokenu zabezpieczeń dla protokołu WS-SecureConversation (WS-SC) którego wartość klucza jest negocjowane, wykonując protokołu TLS za pośrednictwem usługi WS-Trust (WS-T) RST grupy / RSTR wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ffe23-500">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="ffe23-501">Szczegóły implementacji uzgadniania TLS przy użyciu protokołu WS-Trust są opisane w TLSNEGO.</span><span class="sxs-lookup"><span data-stu-id="ffe23-501">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="ffe23-502">W tym miejscu w przykładach komunikat założono będzie, SCT z kontekstem zabezpieczeń skojarzone jest już ustanowione przez uzgadniania.</span><span class="sxs-lookup"><span data-stu-id="ffe23-502">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="ffe23-503">Wiązanie używane jest symetryczne powiązania z następującymi właściwościami;</span><span class="sxs-lookup"><span data-stu-id="ffe23-503">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="ffe23-504">Token ochrony: SslContextToken, tryb dołączania jest ustawiony na .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="ffe23-504">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="ffe23-505">Ochrona tokenu: False</span><span class="sxs-lookup"><span data-stu-id="ffe23-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="ffe23-506">Cały nagłówek i treść podpisów: Prawda</span><span class="sxs-lookup"><span data-stu-id="ffe23-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="ffe23-507">Kolejność ochrony: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="ffe23-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="ffe23-508">Szyfruj podpisu: Prawda</span><span class="sxs-lookup"><span data-stu-id="ffe23-508">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="ffe23-509">6.5.1 zasady SslNegotiated usługi uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="ffe23-509">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="ffe23-510">Zasady dla wszystkich metod uwierzytelniania w tej sekcji są podobne i różnią się tylko określonego podpisanego obsługi lub potwierdzania tokeny używane.</span><span class="sxs-lookup"><span data-stu-id="ffe23-510">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
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
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="ffe23-511">6.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ffe23-511">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="ffe23-512">W tym trybie uwierzytelniania klienta jest anonimowa, a usługa jest uwierzytelniany przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="ffe23-512">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="ffe23-513">Wiązanie używane jest wystąpienie symetrycznego powiązania zgodnie z opisem w powyższej 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="ffe23-513">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="ffe23-514">Zasady</span><span class="sxs-lookup"><span data-stu-id="ffe23-514">Policy</span></span>  
  
 <span data-ttu-id="ffe23-515">Zobacz zasady w 6.5.1 powyżej, aby uzyskać szczegółowe informacje powiązania.</span><span class="sxs-lookup"><span data-stu-id="ffe23-515">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ffe23-516">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ffe23-516">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ffe23-517">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-517">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-518">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-518">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ffe23-519">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ffe23-519">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ffe23-520">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-520">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-521">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-521">Response</span></span>  
  
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
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="ffe23-522">6.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ffe23-522">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="ffe23-523">Za pomocą tego uwierzytelnienia tryb, który klient jest uwierzytelniany przy użyciu Token nazwy użytkownika, który jest wyświetlany w warstwie protokołu SOAP jako podpisany token pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="ffe23-523">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="ffe23-524">Usługa jest uwierzytelniany przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="ffe23-524">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="ffe23-525">Wiązanie używane jest wystąpienie symetrycznego powiązania zgodnie z opisem w 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="ffe23-525">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="ffe23-526">Zasady</span><span class="sxs-lookup"><span data-stu-id="ffe23-526">Policy</span></span>  
  
 <span data-ttu-id="ffe23-527">W sekcji powyżej 6.5.1 szczegóły powiązania</span><span class="sxs-lookup"><span data-stu-id="ffe23-527">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="ffe23-528">Podpisany Token pomocniczy</span><span class="sxs-lookup"><span data-stu-id="ffe23-528">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ffe23-529">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ffe23-529">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ffe23-530">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-530">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-531">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-531">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ffe23-532">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ffe23-532">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ffe23-533">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-533">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-534">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-534">Response</span></span>  
  
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
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="ffe23-535">6.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ffe23-535">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="ffe23-536">Za pomocą tego uwierzytelnienia tryb, który jako takie, ale zamiast tego klient nie uwierzytelniania w usłudze przedstawia token wystawiony przez usługę STS i upoważnienie wiedzę na temat klucza współużytkowanego.</span><span class="sxs-lookup"><span data-stu-id="ffe23-536">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="ffe23-537">Wystawiony token pojawi się w warstwie SOAP jako tokenu pomocniczego.</span><span class="sxs-lookup"><span data-stu-id="ffe23-537">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="ffe23-538">Usługa jest uwierzytelniany przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="ffe23-538">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="ffe23-539">Wiązanie używane jest wystąpienie symetrycznego powiązania zgodnie z opisem w powyższej 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="ffe23-539">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="ffe23-540">Zasady</span><span class="sxs-lookup"><span data-stu-id="ffe23-540">Policy</span></span>  
  
 <span data-ttu-id="ffe23-541">W sekcji powyżej 6.5.1 szczegóły powiązania</span><span class="sxs-lookup"><span data-stu-id="ffe23-541">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="ffe23-542">Potwierdzających tokenu obsługi</span><span class="sxs-lookup"><span data-stu-id="ffe23-542">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ffe23-543">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ffe23-543">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ffe23-544">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-544">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-545">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-545">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ffe23-546">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ffe23-546">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ffe23-547">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-547">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-548">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-548">Response</span></span>  
  
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
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="ffe23-549">6.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ffe23-549">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="ffe23-550">W tym trybie uwierzytelniania klienta i usługę uwierzytelniania przy użyciu certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="ffe23-550">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="ffe23-551">Wiązanie używane jest wystąpienie symetrycznego powiązania zgodnie z opisem w powyższej 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="ffe23-551">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="ffe23-552">Zasady</span><span class="sxs-lookup"><span data-stu-id="ffe23-552">Policy</span></span>  
  
 <span data-ttu-id="ffe23-553">W sekcji powyżej 6.5.1 szczegóły powiązania</span><span class="sxs-lookup"><span data-stu-id="ffe23-553">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="ffe23-554">Potwierdzających tokenu obsługi</span><span class="sxs-lookup"><span data-stu-id="ffe23-554">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ffe23-555">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ffe23-555">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ffe23-556">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-556">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-557">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-557">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ffe23-558">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ffe23-558">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ffe23-559">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-559">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-560">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-560">Response</span></span>  
  
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
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="ffe23-561">6.6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="ffe23-561">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="ffe23-562">W tym trybie uwierzytelniania protokół negocjacji służy do uwierzytelniania klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="ffe23-562">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="ffe23-563">Protokół Kerberos jest używany, jeśli jest to możliwe, w przeciwnym razie uwierzytelnianie NTLM.</span><span class="sxs-lookup"><span data-stu-id="ffe23-563">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="ffe23-564">Wiązanie używane jest symetryczne powiązania z następującymi właściwościami;</span><span class="sxs-lookup"><span data-stu-id="ffe23-564">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="ffe23-565">Token ochrony: SpnegoContextToken, tryb dołączania jest ustawiony na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="ffe23-565">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="ffe23-566">Ochrona tokenu: False</span><span class="sxs-lookup"><span data-stu-id="ffe23-566">Token Protection: False</span></span>  
  
 <span data-ttu-id="ffe23-567">Cały nagłówek i treść podpisów: Prawda</span><span class="sxs-lookup"><span data-stu-id="ffe23-567">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="ffe23-568">Kolejność ochrony: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="ffe23-568">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="ffe23-569">Szyfruj podpisu: Prawda</span><span class="sxs-lookup"><span data-stu-id="ffe23-569">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="ffe23-570">Zasady</span><span class="sxs-lookup"><span data-stu-id="ffe23-570">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ffe23-571">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ffe23-571">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ffe23-572">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-572">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-573">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-573">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ffe23-574">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ffe23-574">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ffe23-575">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-575">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-576">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-576">Response</span></span>  
  
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
  
### <a name="67-secureconversation"></a><span data-ttu-id="ffe23-577">6.7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="ffe23-577">6.7 SecureConversation</span></span>  
 <span data-ttu-id="ffe23-578">Wiązanie używane jest symetryczne powiązania z tokenem ochrony jest SCT na WS-SecureConversation (WS-SC).</span><span class="sxs-lookup"><span data-stu-id="ffe23-578">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="ffe23-579">SCT jest negocjowane przy użyciu protokołu WS-Trust (WS-Trust) lub protokołu WS-SecureConversation (WS-SC), zgodnie z zagnieżdżonych powiązania, który sam jest symetryczne powiązania, które wykorzystuje protokół negocjacji.</span><span class="sxs-lookup"><span data-stu-id="ffe23-579">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="ffe23-580">Protokół negocjacji użyje protokołu Kerberos do uwierzytelniania klienta i serwera, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="ffe23-580">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="ffe23-581">Jeśli nie można użyć protokołu Kerberos, jego powróci do uwierzytelniania NTLM.</span><span class="sxs-lookup"><span data-stu-id="ffe23-581">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="ffe23-582">Zasady</span><span class="sxs-lookup"><span data-stu-id="ffe23-582">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ffe23-583">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ffe23-583">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ffe23-584">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-584">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-585">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-585">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ffe23-586">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ffe23-586">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ffe23-587">Request</span><span class="sxs-lookup"><span data-stu-id="ffe23-587">Request</span></span>  
  
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
  
 <span data-ttu-id="ffe23-588">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ffe23-588">Response</span></span>  
  
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
