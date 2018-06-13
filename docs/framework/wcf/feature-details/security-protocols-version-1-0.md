---
title: Protokoły zabezpieczeń wersja 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 1b1e911b20ac8974dbc8cfa79e03fbd14f9beb17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509180"
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="30aaa-102">Protokoły zabezpieczeń wersja 1.0</span><span class="sxs-lookup"><span data-stu-id="30aaa-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="30aaa-103">Protokoły zabezpieczeń usług sieci Web zapewniają mechanizmy zabezpieczeń usług sieci Web, które obejmują wszystkie istniejącym w przedsiębiorstwie wiadomości wymagania dotyczące zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="30aaa-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="30aaa-104">W tej sekcji opisano Windows Communication Foundation (WCF) w wersji 1.0 (w <xref:System.ServiceModel.Channels.SecurityBindingElement>) dla następujących sieci Web usług protokołów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="30aaa-104">This section describes the Windows Communication Foundation (WCF) version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="30aaa-105">Specyfikacja/dokumentu</span><span class="sxs-lookup"><span data-stu-id="30aaa-105">Specification/Document</span></span>|<span data-ttu-id="30aaa-106">Łącze</span><span class="sxs-lookup"><span data-stu-id="30aaa-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="30aaa-107">WSS: Zabezpieczenia komunikatów SOAP 1.0</span><span class="sxs-lookup"><span data-stu-id="30aaa-107">WSS: SOAP Message Security 1.0</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf|  
|<span data-ttu-id="30aaa-108">Programu WSS: Profil Token nazwy użytkownika 1.0</span><span class="sxs-lookup"><span data-stu-id="30aaa-108">WSS: Username Token Profile 1.0</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf|  
|<span data-ttu-id="30aaa-109">WSS: X509 Token profilu 1.0</span><span class="sxs-lookup"><span data-stu-id="30aaa-109">WSS: X509 Token Profile 1.0</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf|  
|<span data-ttu-id="30aaa-110">Programu WSS: SAML 1.1 Token profilu 1.0</span><span class="sxs-lookup"><span data-stu-id="30aaa-110">WSS: SAML 1.1 Token Profile 1.0</span></span>|http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf|  
|<span data-ttu-id="30aaa-111">Programu WSS: Zabezpieczenia komunikatów SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="30aaa-111">WSS: SOAP Message Security 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf|  
|<span data-ttu-id="30aaa-112">1.1 tokenu profilu programu WSS nazwy użytkownika</span><span class="sxs-lookup"><span data-stu-id="30aaa-112">WSS Username Token Profile 1.1</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf|  
|<span data-ttu-id="30aaa-113">Programu WSS: Profil tokenu X.509 1.1</span><span class="sxs-lookup"><span data-stu-id="30aaa-113">WSS: X.509 Token Profile 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf|  
|<span data-ttu-id="30aaa-114">WSS: 1.1 profilu Token protokołu Kerberos</span><span class="sxs-lookup"><span data-stu-id="30aaa-114">WSS: Kerberos Token Profile 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf|  
|<span data-ttu-id="30aaa-115">Programu WSS: SAML 1.1 Token 1.1 profilu</span><span class="sxs-lookup"><span data-stu-id="30aaa-115">WSS: SAML 1.1 Token Profile 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf|  
|<span data-ttu-id="30aaa-116">Zabezpieczenia WS konwersacji</span><span class="sxs-lookup"><span data-stu-id="30aaa-116">WS-Secure Conversation</span></span>|http://msdn.microsoft.com/ws/2005/02/ws-secure-conversation/|  
|<span data-ttu-id="30aaa-117">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="30aaa-117">WS-Trust</span></span>|http://msdn.microsoft.com/ws/2005/02/ws-trust/|  
|<span data-ttu-id="30aaa-118">Uwaga aplikacji:</span><span class="sxs-lookup"><span data-stu-id="30aaa-118">Application Note:</span></span><br /><br /> <span data-ttu-id="30aaa-119">Za pomocą protokołu WS-Trust na uzgadnianie protokołu TLS</span><span class="sxs-lookup"><span data-stu-id="30aaa-119">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="30aaa-120">Do opublikowania</span><span class="sxs-lookup"><span data-stu-id="30aaa-120">To be published</span></span>|  
|<span data-ttu-id="30aaa-121">Uwaga aplikacji:</span><span class="sxs-lookup"><span data-stu-id="30aaa-121">Application Note:</span></span><br /><br /> <span data-ttu-id="30aaa-122">Za pomocą protokołu WS-Trust dla SPNEGO</span><span class="sxs-lookup"><span data-stu-id="30aaa-122">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="30aaa-123">Do opublikowania</span><span class="sxs-lookup"><span data-stu-id="30aaa-123">To be published</span></span>|  
|<span data-ttu-id="30aaa-124">Uwaga aplikacji:</span><span class="sxs-lookup"><span data-stu-id="30aaa-124">Application Note:</span></span><br /><br /> <span data-ttu-id="30aaa-125">Usługi sieci Web adresowanie odwołania do punktu końcowego i tożsamość</span><span class="sxs-lookup"><span data-stu-id="30aaa-125">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="30aaa-126">Do opublikowania</span><span class="sxs-lookup"><span data-stu-id="30aaa-126">To be published</span></span>|  
|<span data-ttu-id="30aaa-127">WS-SecurityPolicy 1.1</span><span class="sxs-lookup"><span data-stu-id="30aaa-127">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="30aaa-128">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="30aaa-128">(2005/07)</span></span>|http://msdn.microsoft.com/ws/2005/07/ws-security-policy/<br /><br /> <span data-ttu-id="30aaa-129">zmienione erracie przesłane do Komitetu Technicznego WS-SX OASIS http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html</span><span class="sxs-lookup"><span data-stu-id="30aaa-129">as amended by errata submitted to OASIS WS-SX Technical Committee http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html</span></span>|  
  
 <span data-ttu-id="30aaa-130">Usługi WCF, wersja 1, zapewnia 17 tryby uwierzytelniania, które mogą służyć jako podstawa dla konfiguracji zabezpieczeń usług sieci Web.</span><span class="sxs-lookup"><span data-stu-id="30aaa-130">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="30aaa-131">Każdego trybu jest zoptymalizowana pod kątem wspólny zbiór wymagania dotyczące wdrażania, takie jak:</span><span class="sxs-lookup"><span data-stu-id="30aaa-131">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
-   <span data-ttu-id="30aaa-132">Poświadczenia używane do uwierzytelniania klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="30aaa-132">Credentials used to authenticate client and service.</span></span>  
  
-   <span data-ttu-id="30aaa-133">Mechanizmy ochrony zabezpieczeń transportu lub wiadomości.</span><span class="sxs-lookup"><span data-stu-id="30aaa-133">Message or transport security protection mechanisms.</span></span>  
  
-   <span data-ttu-id="30aaa-134">Wzorce wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="30aaa-134">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="30aaa-135">Tryb uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="30aaa-135">Authentication Mode</span></span>|<span data-ttu-id="30aaa-136">Uwierzytelnianie klienta</span><span class="sxs-lookup"><span data-stu-id="30aaa-136">Client Authentication</span></span>|<span data-ttu-id="30aaa-137">Uwierzytelnianie serwera</span><span class="sxs-lookup"><span data-stu-id="30aaa-137">Server Authentication</span></span>|<span data-ttu-id="30aaa-138">Tryb</span><span class="sxs-lookup"><span data-stu-id="30aaa-138">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="30aaa-139">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="30aaa-139">UserNameOverTransport</span></span>|<span data-ttu-id="30aaa-140">Nazwa użytkownika/hasło</span><span class="sxs-lookup"><span data-stu-id="30aaa-140">User name/password</span></span>|<span data-ttu-id="30aaa-141">X509</span><span class="sxs-lookup"><span data-stu-id="30aaa-141">X509</span></span>|<span data-ttu-id="30aaa-142">Transportu</span><span class="sxs-lookup"><span data-stu-id="30aaa-142">Transport</span></span>|  
|<span data-ttu-id="30aaa-143">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="30aaa-143">CertificateOverTransport</span></span>|<span data-ttu-id="30aaa-144">X509</span><span class="sxs-lookup"><span data-stu-id="30aaa-144">X509</span></span>|<span data-ttu-id="30aaa-145">X509</span><span class="sxs-lookup"><span data-stu-id="30aaa-145">X509</span></span>|<span data-ttu-id="30aaa-146">Transportu</span><span class="sxs-lookup"><span data-stu-id="30aaa-146">Transport</span></span>|  
|<span data-ttu-id="30aaa-147">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="30aaa-147">KerberosOverTransport</span></span>|<span data-ttu-id="30aaa-148">Windows</span><span class="sxs-lookup"><span data-stu-id="30aaa-148">Windows</span></span>|<span data-ttu-id="30aaa-149">X509</span><span class="sxs-lookup"><span data-stu-id="30aaa-149">X509</span></span>|<span data-ttu-id="30aaa-150">Transportu</span><span class="sxs-lookup"><span data-stu-id="30aaa-150">Transport</span></span>|  
|<span data-ttu-id="30aaa-151">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="30aaa-151">IssuedTokenOverTransport</span></span>|<span data-ttu-id="30aaa-152">Federacyjna</span><span class="sxs-lookup"><span data-stu-id="30aaa-152">Federated</span></span>|<span data-ttu-id="30aaa-153">X509</span><span class="sxs-lookup"><span data-stu-id="30aaa-153">X509</span></span>|<span data-ttu-id="30aaa-154">Transportu</span><span class="sxs-lookup"><span data-stu-id="30aaa-154">Transport</span></span>|  
|<span data-ttu-id="30aaa-155">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="30aaa-155">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="30aaa-156">Wynegocjowane interfejsu Sspi systemu Windows</span><span class="sxs-lookup"><span data-stu-id="30aaa-156">Windows Sspi Negotiated</span></span>|<span data-ttu-id="30aaa-157">Wynegocjowane interfejsu Sspi systemu Windows</span><span class="sxs-lookup"><span data-stu-id="30aaa-157">Windows Sspi Negotiated</span></span>|<span data-ttu-id="30aaa-158">Transportu</span><span class="sxs-lookup"><span data-stu-id="30aaa-158">Transport</span></span>|  
|<span data-ttu-id="30aaa-159">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="30aaa-159">AnonymousForCertificate</span></span>|<span data-ttu-id="30aaa-160">Brak</span><span class="sxs-lookup"><span data-stu-id="30aaa-160">None</span></span>|<span data-ttu-id="30aaa-161">X509</span><span class="sxs-lookup"><span data-stu-id="30aaa-161">X509</span></span>|<span data-ttu-id="30aaa-162">Komunikat</span><span class="sxs-lookup"><span data-stu-id="30aaa-162">Message</span></span>|  
|<span data-ttu-id="30aaa-163">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="30aaa-163">UserNameForCertificate</span></span>|<span data-ttu-id="30aaa-164">Nazwa użytkownika/hasło</span><span class="sxs-lookup"><span data-stu-id="30aaa-164">User name/password</span></span>|<span data-ttu-id="30aaa-165">X509</span><span class="sxs-lookup"><span data-stu-id="30aaa-165">X509</span></span>|<span data-ttu-id="30aaa-166">Komunikat</span><span class="sxs-lookup"><span data-stu-id="30aaa-166">Message</span></span>|  
|<span data-ttu-id="30aaa-167">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="30aaa-167">MutualCertificate</span></span>|<span data-ttu-id="30aaa-168">X509</span><span class="sxs-lookup"><span data-stu-id="30aaa-168">X509</span></span>|<span data-ttu-id="30aaa-169">X509</span><span class="sxs-lookup"><span data-stu-id="30aaa-169">X509</span></span>|<span data-ttu-id="30aaa-170">Komunikat</span><span class="sxs-lookup"><span data-stu-id="30aaa-170">Message</span></span>|  
|<span data-ttu-id="30aaa-171">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="30aaa-171">MutualCertificateDuplex</span></span>|<span data-ttu-id="30aaa-172">X509</span><span class="sxs-lookup"><span data-stu-id="30aaa-172">X509</span></span>|<span data-ttu-id="30aaa-173">X509</span><span class="sxs-lookup"><span data-stu-id="30aaa-173">X509</span></span>|<span data-ttu-id="30aaa-174">Komunikat</span><span class="sxs-lookup"><span data-stu-id="30aaa-174">Message</span></span>|  
|<span data-ttu-id="30aaa-175">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="30aaa-175">IssuedTokenForCertificate</span></span>|<span data-ttu-id="30aaa-176">Federacyjna</span><span class="sxs-lookup"><span data-stu-id="30aaa-176">Federated</span></span>|<span data-ttu-id="30aaa-177">X509</span><span class="sxs-lookup"><span data-stu-id="30aaa-177">X509</span></span>|<span data-ttu-id="30aaa-178">Komunikat</span><span class="sxs-lookup"><span data-stu-id="30aaa-178">Message</span></span>|  
|<span data-ttu-id="30aaa-179">Kerberos</span><span class="sxs-lookup"><span data-stu-id="30aaa-179">Kerberos</span></span>|<span data-ttu-id="30aaa-180">Windows</span><span class="sxs-lookup"><span data-stu-id="30aaa-180">Windows</span></span>|<span data-ttu-id="30aaa-181">Windows</span><span class="sxs-lookup"><span data-stu-id="30aaa-181">Windows</span></span>|<span data-ttu-id="30aaa-182">Komunikat</span><span class="sxs-lookup"><span data-stu-id="30aaa-182">Message</span></span>|  
|<span data-ttu-id="30aaa-183">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="30aaa-183">IssuedToken</span></span>|<span data-ttu-id="30aaa-184">Federacyjna</span><span class="sxs-lookup"><span data-stu-id="30aaa-184">Federated</span></span>|<span data-ttu-id="30aaa-185">Federacyjna</span><span class="sxs-lookup"><span data-stu-id="30aaa-185">Federated</span></span>|<span data-ttu-id="30aaa-186">Komunikat</span><span class="sxs-lookup"><span data-stu-id="30aaa-186">Message</span></span>|  
|<span data-ttu-id="30aaa-187">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="30aaa-187">SspiNegotiated</span></span>|<span data-ttu-id="30aaa-188">Wynegocjowane interfejsu Sspi systemu Windows</span><span class="sxs-lookup"><span data-stu-id="30aaa-188">Windows Sspi Negotiated</span></span>|<span data-ttu-id="30aaa-189">Wynegocjowane interfejsu Sspi systemu Windows</span><span class="sxs-lookup"><span data-stu-id="30aaa-189">Windows Sspi Negotiated</span></span>|<span data-ttu-id="30aaa-190">Komunikat</span><span class="sxs-lookup"><span data-stu-id="30aaa-190">Message</span></span>|  
|<span data-ttu-id="30aaa-191">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="30aaa-191">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="30aaa-192">Brak</span><span class="sxs-lookup"><span data-stu-id="30aaa-192">None</span></span>|<span data-ttu-id="30aaa-193">X509, TLS Nego</span><span class="sxs-lookup"><span data-stu-id="30aaa-193">X509, TLS-Nego</span></span>|<span data-ttu-id="30aaa-194">Komunikat</span><span class="sxs-lookup"><span data-stu-id="30aaa-194">Message</span></span>|  
|<span data-ttu-id="30aaa-195">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="30aaa-195">UserNameForSslNegotiated</span></span>|<span data-ttu-id="30aaa-196">Nazwa użytkownika/hasło</span><span class="sxs-lookup"><span data-stu-id="30aaa-196">User name/password</span></span>|<span data-ttu-id="30aaa-197">X509, TLS Nego</span><span class="sxs-lookup"><span data-stu-id="30aaa-197">X509, TLS-Nego</span></span>|<span data-ttu-id="30aaa-198">Komunikat</span><span class="sxs-lookup"><span data-stu-id="30aaa-198">Message</span></span>|  
|<span data-ttu-id="30aaa-199">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="30aaa-199">MutualSslNegotiated</span></span>|<span data-ttu-id="30aaa-200">X509</span><span class="sxs-lookup"><span data-stu-id="30aaa-200">X509</span></span>|<span data-ttu-id="30aaa-201">X509, TLS Nego</span><span class="sxs-lookup"><span data-stu-id="30aaa-201">X509, TLS-Nego</span></span>|<span data-ttu-id="30aaa-202">Komunikat</span><span class="sxs-lookup"><span data-stu-id="30aaa-202">Message</span></span>|  
|<span data-ttu-id="30aaa-203">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="30aaa-203">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="30aaa-204">Federacyjna</span><span class="sxs-lookup"><span data-stu-id="30aaa-204">Federated</span></span>|<span data-ttu-id="30aaa-205">X509, TLS Nego</span><span class="sxs-lookup"><span data-stu-id="30aaa-205">X509, TLS-Nego</span></span>|<span data-ttu-id="30aaa-206">Komunikat</span><span class="sxs-lookup"><span data-stu-id="30aaa-206">Message</span></span>|  
  
 <span data-ttu-id="30aaa-207">Punktów końcowych przy użyciu tych trybach uwierzytelniania można wyrazić ich wymagania dotyczące zabezpieczeń przy użyciu usługi WS-SecurityPolicy (WS-SP).</span><span class="sxs-lookup"><span data-stu-id="30aaa-207">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="30aaa-208">Ten dokument zawiera opis struktury nagłówka zabezpieczeń i infrastruktury komunikaty dla każdego trybu uwierzytelniania oraz przykłady zasad i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="30aaa-208">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="30aaa-209">Usługi WCF wykorzystuje WS-SecureConversation, aby zapewnić obsługę bezpiecznej sesji do ochrony wymiany wielu komunikatów między aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="30aaa-209">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="30aaa-210">Aby uzyskać szczegóły implementacji, zobacz "Secure sesji" poniżej.</span><span class="sxs-lookup"><span data-stu-id="30aaa-210">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="30aaa-211">Oprócz tryby uwierzytelniania WCF zawiera ustawienia, aby kontrolować typowych mechanizmów ochrony, które są stosowane do większości tryby uwierzytelniania zabezpieczeń wiadomości, na przykład: kolejność podpisu i operacji szyfrowania, mechanizmy Algorytm wyprowadzania klucza , a potwierdzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="30aaa-211">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="30aaa-212">Następujące prefiksy i przestrzenie nazw są używane w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="30aaa-212">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="30aaa-213">Prefiks</span><span class="sxs-lookup"><span data-stu-id="30aaa-213">Prefix</span></span>|<span data-ttu-id="30aaa-214">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="30aaa-214">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="30aaa-215">s</span><span class="sxs-lookup"><span data-stu-id="30aaa-215">s</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="30aaa-216">SP</span><span class="sxs-lookup"><span data-stu-id="30aaa-216">sp</span></span>|http://schemas.xmlsoap.org/ws/2005/07/securitypolicy|  
|<span data-ttu-id="30aaa-217">a</span><span class="sxs-lookup"><span data-stu-id="30aaa-217">a</span></span>|http://www.w3.org/2005/08/addressing|  
|<span data-ttu-id="30aaa-218">wsse</span><span class="sxs-lookup"><span data-stu-id="30aaa-218">wsse</span></span>|<span data-ttu-id="30aaa-219">DO USTALENIA — IDENTYFIKATOR URI PROGRAMU WSS 1.0 JĘZYKA OASIS</span><span class="sxs-lookup"><span data-stu-id="30aaa-219">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="30aaa-220">wsse11</span><span class="sxs-lookup"><span data-stu-id="30aaa-220">wsse11</span></span>|<span data-ttu-id="30aaa-221">DO USTALENIA — IDENTYFIKATOR URI PROGRAMU WSS 1.1 JĘZYKA OASIS</span><span class="sxs-lookup"><span data-stu-id="30aaa-221">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="30aaa-222">wsu</span><span class="sxs-lookup"><span data-stu-id="30aaa-222">wsu</span></span>|<span data-ttu-id="30aaa-223">Do ustalenia — narzędzie identyfikatora URI OASIS WSS 1.0</span><span class="sxs-lookup"><span data-stu-id="30aaa-223">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="30aaa-224">ds</span><span class="sxs-lookup"><span data-stu-id="30aaa-224">ds</span></span>|<span data-ttu-id="30aaa-225">Do ustalenia — identyfikator URI XMLDSig W3C</span><span class="sxs-lookup"><span data-stu-id="30aaa-225">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="30aaa-226">Wst</span><span class="sxs-lookup"><span data-stu-id="30aaa-226">wst</span></span>|<span data-ttu-id="30aaa-227">Do ustalenia — identyfikator URI protokołu WS-Trust 2005/02</span><span class="sxs-lookup"><span data-stu-id="30aaa-227">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="30aaa-228">wssc</span><span class="sxs-lookup"><span data-stu-id="30aaa-228">wssc</span></span>|<span data-ttu-id="30aaa-229">Do ustalenia — WS-SecureConversation 2005/02 identyfikatora URI</span><span class="sxs-lookup"><span data-stu-id="30aaa-229">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="30aaa-230">wsaw</span><span class="sxs-lookup"><span data-stu-id="30aaa-230">wsaw</span></span>|<span data-ttu-id="30aaa-231">Do ustalenia - WS-Addressing przestrzeni nazw zasad</span><span class="sxs-lookup"><span data-stu-id="30aaa-231">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="30aaa-232">WSP</span><span class="sxs-lookup"><span data-stu-id="30aaa-232">wsp</span></span>|http://schemas.xmlsoap.org/ws/2004/09/policy|  
|<span data-ttu-id="30aaa-233">Mssp</span><span class="sxs-lookup"><span data-stu-id="30aaa-233">mssp</span></span>|http://schemas.microsoft.com/ws/2005/07/securitypolicy|  
  
## <a name="1-token-profiles"></a><span data-ttu-id="30aaa-234">1. Profile tokenu</span><span class="sxs-lookup"><span data-stu-id="30aaa-234">1. Token Profiles</span></span>  
 <span data-ttu-id="30aaa-235">Specyfikacje zabezpieczenia usług sieci Web reprezentować poświadczeń tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="30aaa-235">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="30aaa-236">Usługi WCF obsługuje następujące typy tokenów:</span><span class="sxs-lookup"><span data-stu-id="30aaa-236">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="30aaa-237">1.1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="30aaa-237">1.1 UsernameToken</span></span>  
 <span data-ttu-id="30aaa-238">Usługi WCF następujące profile UsernameToken10 i UsernameToken11 z następującymi ograniczeniami:</span><span class="sxs-lookup"><span data-stu-id="30aaa-238">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="30aaa-239">Atrybut R1101 PasswordType w elemencie UsernameToken\Password albo pominięcia ani mieć wartości #PasswordText (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="30aaa-239">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="30aaa-240">Co można zaimplementować #PasswordDigest przy użyciu rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="30aaa-240">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="30aaa-241">Zaobserwowano, że #PasswordDigest został często pomylone jako mechanizm ochrony dostatecznie bezpieczne hasło.</span><span class="sxs-lookup"><span data-stu-id="30aaa-241">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="30aaa-242">Ale #PasswordDigest nie może służyć jako zamiennik szyfrowania UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="30aaa-242">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="30aaa-243">Podstawowym celem #PasswordDigest jest ochrona przed atakami powtarzania.</span><span class="sxs-lookup"><span data-stu-id="30aaa-243">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="30aaa-244">Tryby uwierzytelniania usługi WCF kontrolowaniu zagrożenia atakiem polegającym na odtwarzaniu przy użyciu sygnatury komunikatów.</span><span class="sxs-lookup"><span data-stu-id="30aaa-244">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="30aaa-245">B1102 WCF nigdy nie emituje identyfikator jednorazowy i utworzono elementy podrzędne UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="30aaa-245">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="30aaa-246">Te elementy podrzędne mają na celu pomoc wykrywania powtarzania.</span><span class="sxs-lookup"><span data-stu-id="30aaa-246">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="30aaa-247">Usługi WCF użyje sygnatury komunikatów.</span><span class="sxs-lookup"><span data-stu-id="30aaa-247">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="30aaa-248">OASIS WSS SOAP komunikatów zabezpieczeń UsernameToken Profile 1.1 (UsernameToken11) wprowadzono wyprowadzania klucza z hasła funkcji.</span><span class="sxs-lookup"><span data-stu-id="30aaa-248">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="30aaa-249">Hasło B1103 UsernameToken nie mogą być używane dla klucza pochodnego i w związku z tym dla operacji kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="30aaa-249">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="30aaa-250">Uzasadnienie: hasła są zazwyczaj uznane za zbyt słabe do użycia dla operacji kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="30aaa-250">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="30aaa-251">1.2 x 509 tokenu</span><span class="sxs-lookup"><span data-stu-id="30aaa-251">1.2 X509 Token</span></span>  
 <span data-ttu-id="30aaa-252">Usługi WCF obsługuje certyfikaty X509v3 jako typ poświadczeń i X509TokenProfile1.0 i X509TokenProfile1.1 jest zgodny z następującymi ograniczeniami:</span><span class="sxs-lookup"><span data-stu-id="30aaa-252">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="30aaa-253">Atrybut R1201 ValueType w elemencie BinarySecurityToken musi mieć wartość #X509v3, gdy zawiera certyfikat X509v3.</span><span class="sxs-lookup"><span data-stu-id="30aaa-253">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="30aaa-254">WSS X509 Token profilu 1.0 i 1.1 zdefiniuj również #X509PKIPathv1 oraz PKCS7 # jako typów wartości.</span><span class="sxs-lookup"><span data-stu-id="30aaa-254">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="30aaa-255">Usługi WCF nie obsługuje tego typu.</span><span class="sxs-lookup"><span data-stu-id="30aaa-255">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="30aaa-256">R1202 czy rozszerzenia SubjectKeyIdentifier (SKI) znajduje się w X509 certyfikat, wsse:KeyIdentifier powinien być używany dla zewnętrznych odwołań do tokenu, z Właściwość ValueType atrybutu jako #X509SubjectKeyIdentifier i jego zawartości wartość algorytmem Base64 rozszerzenie SKI certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="30aaa-256">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="30aaa-257">Odwołania SKI powszechnie implementowanych i sprawdzone na typ wysokiej interoperacyjne odwołania zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="30aaa-257">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="30aaa-258">R1203 Odwołanie zewnętrzne do X509 zabezpieczeń tokenu nie powinien używać ds:X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="30aaa-258">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="30aaa-259">R1204 X509TokenProfile1.1 Jeśli jest używany, odwołanie zewnętrzne do X509 zabezpieczeń tokenów należy używać odcisk palca wprowadzone przez 1.1 WS-Security.</span><span class="sxs-lookup"><span data-stu-id="30aaa-259">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="30aaa-260">Usługi WCF obsługuje X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="30aaa-260">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="30aaa-261">Istnieją jednak współdziałanie z X509IssuerSerial: WCF używa ciągu do porównywania dwóch wartości X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="30aaa-261">However There are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="30aaa-262">W związku z tym jeśli jedna zmienia kolejność składników nazwa podmiotu i wysyła do usługi WCF odwołanie do certyfikatu go nie znaleziono.</span><span class="sxs-lookup"><span data-stu-id="30aaa-262">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="30aaa-263">1.3 Token protokołu Kerberos</span><span class="sxs-lookup"><span data-stu-id="30aaa-263">1.3 Kerberos Token</span></span>  
 <span data-ttu-id="30aaa-264">Usługi WCF obsługuje KerberosTokenProfile1.1 na potrzeby uwierzytelniania systemu Windows z następującymi ograniczeniami:</span><span class="sxs-lookup"><span data-stu-id="30aaa-264">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="30aaa-265">R1301 A Kerberos tokenu musi zawierać wartość GSS opakowana AP_REQ v4 protokołu Kerberos, zgodnie z definicją w GSS_API i specyfikacja protokołu Kerberos, a musi mieć atrybut ValueType o wartości GSS_Kerberosv5_AP_REQ #.</span><span class="sxs-lookup"><span data-stu-id="30aaa-265">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="30aaa-266">Używa WCF GSS opakowana Kerberos uwierzytelniania Kerberos, nie systemu od zera region-REQ.</span><span class="sxs-lookup"><span data-stu-id="30aaa-266">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="30aaa-267">Jest to najlepsze rozwiązanie bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="30aaa-267">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="30aaa-268">1.4 SAML Token w wersji 1.1</span><span class="sxs-lookup"><span data-stu-id="30aaa-268">1.4 SAML v1.1 Token</span></span>  
 <span data-ttu-id="30aaa-269">Usługi WCF obsługuje profile tokenu SAML programu WSS 1.0 i 1.1 tokeny SAML w wersji 1.1.</span><span class="sxs-lookup"><span data-stu-id="30aaa-269">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="30aaa-270">Istnieje możliwość wykonania innych wersji formatów tokenu SAML.</span><span class="sxs-lookup"><span data-stu-id="30aaa-270">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="30aaa-271">W wersji 1.5 Token kontekstu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="30aaa-271">1.5 Security Context Token</span></span>  
 <span data-ttu-id="30aaa-272">Usługi WCF obsługuje zabezpieczeń kontekstu tokenu (SCT) wprowadzone w WS SecureCoversation.</span><span class="sxs-lookup"><span data-stu-id="30aaa-272">WCF supports the Security Context Token (SCT) introduced in WS-SecureCoversation.</span></span> <span data-ttu-id="30aaa-273">SCT jest używana do reprezentowania w kontekście zabezpieczeń określonych w SecureConversation również jako negocjacji binarnej protokoły TLS i SSPI, opisane poniżej.</span><span class="sxs-lookup"><span data-stu-id="30aaa-273">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="30aaa-274">2. Wspólne parametry zabezpieczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="30aaa-274">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="30aaa-275">2.1 Sygnatura czasowa</span><span class="sxs-lookup"><span data-stu-id="30aaa-275">2.1 TimeStamp</span></span>  
 <span data-ttu-id="30aaa-276">Obecności znacznika czasu jest kontrolowany przy użyciu <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> właściwość <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="30aaa-276">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="30aaa-277">Usługi WCF zawsze serializuje wsse:TimeStamp z wsse: utworzyć i wsse: wygasa pól.</span><span class="sxs-lookup"><span data-stu-id="30aaa-277">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="30aaa-278">Wsse:TimeStamp są zawsze podpisane podczas podpisywania jest używany.</span><span class="sxs-lookup"><span data-stu-id="30aaa-278">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="30aaa-279">2.2 kolejność ochrony</span><span class="sxs-lookup"><span data-stu-id="30aaa-279">2.2 Protection Order</span></span>  
 <span data-ttu-id="30aaa-280">Usługi WCF obsługuje porządku ochrony wiadomości "Znak przed szyfrowania" i "Szyfrowania przed znak" (1.1 zasad zabezpieczeń).</span><span class="sxs-lookup"><span data-stu-id="30aaa-280">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="30aaa-281">"Zaloguj się przed Szyfruj" zaleca się powodów takich jak: komunikaty chronione przy użyciu szyfrowania przed logowania są otwarte na ataki podstawienia podpisu, chyba że jest używany mechanizm WS-Security 1.1 SignatureConfirmation i sprawia, że podpis za pośrednictwem zaszyfrowaną zawartość Inspekcja trudniej.</span><span class="sxs-lookup"><span data-stu-id="30aaa-281">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="30aaa-282">2.3 Podpis ochrony</span><span class="sxs-lookup"><span data-stu-id="30aaa-282">2.3 Signature Protection</span></span>  
 <span data-ttu-id="30aaa-283">Podczas szyfrowania przed znak jest używany, zalecane jest ochrona podpisu przed atakami ukierunkowany na odgadnięcie zaszyfrowaną zawartość lub klucza podpisywania (szczególnie, gdy token niestandardowy jest używany z słabe materiału klucza).</span><span class="sxs-lookup"><span data-stu-id="30aaa-283">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="30aaa-284">2.4 pakiet algorytmów</span><span class="sxs-lookup"><span data-stu-id="30aaa-284">2.4 Algorithm Suite</span></span>  
 <span data-ttu-id="30aaa-285">Usługi WCF obsługuje wszystkie pakiety algorytm 1.1 zasad zabezpieczeń na liście.</span><span class="sxs-lookup"><span data-stu-id="30aaa-285">WCF supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="30aaa-286">2.5 klucza pochodnego</span><span class="sxs-lookup"><span data-stu-id="30aaa-286">2.5 Key Derivation</span></span>  
 <span data-ttu-id="30aaa-287">Usługi WCF używa "Klucza pochodnego dla kluczy symetrycznych", zgodnie z opisem w WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="30aaa-287">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="30aaa-288">2.6 potwierdzenie podpisu</span><span class="sxs-lookup"><span data-stu-id="30aaa-288">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="30aaa-289">Potwierdzenie podpisu może być jako ochronę przed atakami środkowej man chronić zbiór podpisów.</span><span class="sxs-lookup"><span data-stu-id="30aaa-289">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="30aaa-290">2.7 układ nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="30aaa-290">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="30aaa-291">Każdy tryb uwierzytelniania opisano niektóre układ nagłówka zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="30aaa-291">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="30aaa-292">Elementy w nagłówku zabezpieczeń są uporządkowane częściowo.</span><span class="sxs-lookup"><span data-stu-id="30aaa-292">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="30aaa-293">Aby zdefiniować kolejność elementów podrzędnych nagłówka zabezpieczeń, polityki WS-Security definiuje następujące tryby układ nagłówka zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="30aaa-293">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="30aaa-294">Ograniczeniami</span><span class="sxs-lookup"><span data-stu-id="30aaa-294">Strict</span></span>|<span data-ttu-id="30aaa-295">Elementy są dodawane do następującego nagłówka zabezpieczeń się, że reguły numerowane układu opisanego w zasady zabezpieczeń sekcji 7.7.1 zgodnie z ogólną zasadą "deklaruje przed użyciem".</span><span class="sxs-lookup"><span data-stu-id="30aaa-295">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="30aaa-296">Swobodny</span><span class="sxs-lookup"><span data-stu-id="30aaa-296">Lax</span></span>|<span data-ttu-id="30aaa-297">Elementy są dodawane do nagłówka zabezpieczeń w dowolnej kolejności, która odpowiada programu WSS: zabezpieczenia wiadomości protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="30aaa-297">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="30aaa-298">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="30aaa-298">LaxTimestampFirst</span></span>|<span data-ttu-id="30aaa-299">Tym samym Lax z tą różnicą, że pierwszy element w nagłówku zabezpieczeń muszą być wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="30aaa-299">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="30aaa-300">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="30aaa-300">LaxTimestampLast</span></span>|<span data-ttu-id="30aaa-301">Identyczny swobodny z tą różnicą, że ostatni element w nagłówku zabezpieczeń muszą być wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="30aaa-301">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="30aaa-302">Usługi WCF obsługuje wszystkie cztery tryby układzie nagłówka zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="30aaa-302">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="30aaa-303">Zabezpieczenia nagłówka struktury i komunikat dla tryby uwierzytelniania poniżej przykładów trybu "Strict".</span><span class="sxs-lookup"><span data-stu-id="30aaa-303">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="30aaa-304">2. Wspólne parametry zabezpieczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="30aaa-304">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="30aaa-305">Ta sekcja zawiera przykładowe zasady dla każdego trybu uwierzytelniania wraz z przykładami przedstawiający Struktura nagłówka zabezpieczeń w wiadomości wymieniane przez klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="30aaa-305">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="30aaa-306">6.1 ochrony transportu</span><span class="sxs-lookup"><span data-stu-id="30aaa-306">6.1 Transport Protection</span></span>  
 <span data-ttu-id="30aaa-307">Usługi WCF zawiera pięć tryby uwierzytelniania, korzystających z bezpiecznego transportu do ochrony wiadomości. UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport i SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="30aaa-307">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="30aaa-308">Te tryby uwierzytelniania są konstruowane przy użyciu opisanego w SecurityPolicy powiązania transportu.</span><span class="sxs-lookup"><span data-stu-id="30aaa-308">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="30aaa-309">W przypadku UserNameOverTransport tryb uwierzytelniania UsernameToken jest podpisany token pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="30aaa-309">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="30aaa-310">W trybach uwierzytelniania tokenu jest wyświetlany jako podpisany token zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="30aaa-310">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="30aaa-311">Dodatek C.1.2 i C.1.3 SecurityPolicy opisują szczegółowo układ nagłówka zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="30aaa-311">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="30aaa-312">Następujące nagłówki zabezpieczeń przykład Pokaż Strict układu dla trybu danego uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="30aaa-312">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="30aaa-313">Wartość właściwości "Kluczy pochodnych" tokenów we wszystkich przypadkach jest "false".</span><span class="sxs-lookup"><span data-stu-id="30aaa-313">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="30aaa-314">Wartości różnych właściwości powiązania transportu są następujące:</span><span class="sxs-lookup"><span data-stu-id="30aaa-314">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="30aaa-315">Sygnatura czasowa: true</span><span class="sxs-lookup"><span data-stu-id="30aaa-315">Timestamp: true</span></span>  
  
 <span data-ttu-id="30aaa-316">Układ nagłówka zabezpieczeń: Strict</span><span class="sxs-lookup"><span data-stu-id="30aaa-316">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="30aaa-317">Pakiet algorytmów: Basic256</span><span class="sxs-lookup"><span data-stu-id="30aaa-317">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="30aaa-318">6.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="30aaa-318">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="30aaa-319">Z tego trybu uwierzytelniania klienta jest uwierzytelniany w usłudze Token nazwy użytkownika, który znajduje się na warstwie SOAP jako podpisanego tokenu pomocniczego zawsze wysyłany z inicjatora do adresata.</span><span class="sxs-lookup"><span data-stu-id="30aaa-319">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="30aaa-320">Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="30aaa-320">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="30aaa-321">Wiązanie używane jest powiązania transportu.</span><span class="sxs-lookup"><span data-stu-id="30aaa-321">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="30aaa-322">Zasady</span><span class="sxs-lookup"><span data-stu-id="30aaa-322">Policy</span></span>  
  
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
  
 <span data-ttu-id="30aaa-323">Układ nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="30aaa-323">Security Header Layout</span></span>  
  
 <span data-ttu-id="30aaa-324">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-324">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-325">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-325">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="30aaa-326">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="30aaa-326">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="30aaa-327">Z tego trybu uwierzytelniania, który uwierzytelnia klienta za pomocą X.509 certyfikatów, która jest wyświetlana w warstwie protokołu SOAP jako tokenu pomocniczego zawsze wysyłany z inicjatora do adresata.</span><span class="sxs-lookup"><span data-stu-id="30aaa-327">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="30aaa-328">Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="30aaa-328">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="30aaa-329">Wiązanie używane jest powiązania transportu.</span><span class="sxs-lookup"><span data-stu-id="30aaa-329">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="30aaa-330">Zasady</span><span class="sxs-lookup"><span data-stu-id="30aaa-330">Policy</span></span>  
  
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
  
 <span data-ttu-id="30aaa-331">Układ nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="30aaa-331">Security Header Layout</span></span>  
  
 <span data-ttu-id="30aaa-332">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-332">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-333">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-333">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="30aaa-334">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="30aaa-334">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="30aaa-335">W ten tryb uwierzytelniania klienta nie uwierzytelniania w usłudze, w związku, ale raczej wyświetlany token wystawiony przez zabezpieczenia tokenu usługi (STS) oraz okaże się wiedzę na temat klucza wspólnego.</span><span class="sxs-lookup"><span data-stu-id="30aaa-335">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="30aaa-336">Wystawiony token jest wyświetlany w warstwie protokołu SOAP jako tokenu pomocniczego zawsze wysyłany z inicjatora do adresata.</span><span class="sxs-lookup"><span data-stu-id="30aaa-336">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="30aaa-337">Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="30aaa-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="30aaa-338">Powiązanie jest powiązania transportu.</span><span class="sxs-lookup"><span data-stu-id="30aaa-338">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="30aaa-339">Zasady</span><span class="sxs-lookup"><span data-stu-id="30aaa-339">Policy</span></span>  
  
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
  
 <span data-ttu-id="30aaa-340">Układ nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="30aaa-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="30aaa-341">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-341">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-342">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="30aaa-343">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="30aaa-343">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="30aaa-344">Z tego trybu uwierzytelniania klient przeprowadza uwierzytelnianie usługi przy użyciu biletu protokołu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="30aaa-344">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="30aaa-345">Token protokołu Kerberos jest wyświetlany w warstwie protokołu SOAP jako tokenu pomocniczego.</span><span class="sxs-lookup"><span data-stu-id="30aaa-345">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="30aaa-346">Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="30aaa-346">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="30aaa-347">Powiązanie jest powiązania transportu.</span><span class="sxs-lookup"><span data-stu-id="30aaa-347">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="30aaa-348">Zasady</span><span class="sxs-lookup"><span data-stu-id="30aaa-348">Policy</span></span>  
  
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
  
 <span data-ttu-id="30aaa-349">Układ nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="30aaa-349">Security Header Layout</span></span>  
  
 <span data-ttu-id="30aaa-350">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-350">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-351">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-351">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="30aaa-352">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="30aaa-352">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="30aaa-353">W tym trybie protokół negocjacji służy do uwierzytelniania klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="30aaa-353">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="30aaa-354">Protokół Kerberos jest używany, jeśli to możliwe, w przeciwnym razie NTLM.</span><span class="sxs-lookup"><span data-stu-id="30aaa-354">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="30aaa-355">Wynikowa SCT pojawia się w warstwie protokołu SOAP jako tokenu pomocniczego zawsze wysyłany z inicjatora do adresata.</span><span class="sxs-lookup"><span data-stu-id="30aaa-355">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="30aaa-356">Usługa Ponadto jest uwierzytelniany w przypadku warstwy transportu za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="30aaa-356">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="30aaa-357">Wiązanie używane jest powiązania transportu.</span><span class="sxs-lookup"><span data-stu-id="30aaa-357">The binding used is a transport binding.</span></span> <span data-ttu-id="30aaa-358">"SPNEGO" (negocjacji) opisano, jak WCF używa interfejsu SSPI protokołu negocjacji binarnej z protokołu WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="30aaa-358">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="30aaa-359">Przykłady nagłówka zabezpieczeń w tej sekcji są po nawiązaniu SCT za pośrednictwem uzgadnianie SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="30aaa-359">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="30aaa-360">Zasady</span><span class="sxs-lookup"><span data-stu-id="30aaa-360">Policy</span></span>  
  
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
  
### <a name="security-header-examples"></a><span data-ttu-id="30aaa-361">Przykłady nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="30aaa-361">Security Header Examples</span></span>  
 <span data-ttu-id="30aaa-362">Po Token kontekstu zabezpieczeń za pomocą uzgadniania SPNEGO przy użyciu protokołu WS-Trust negocjacji binarnej komunikatów aplikacji ma nagłówki zabezpieczeń o następującej strukturze.</span><span class="sxs-lookup"><span data-stu-id="30aaa-362">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="30aaa-363">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-363">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-364">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-364">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="30aaa-365">6.2 za pomocą certyfikatów X.509 do usługi uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="30aaa-365">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="30aaa-366">W tej sekcji opisano następujące tryby uwierzytelniania: MutualCertificate WSS1.0, wzajemne CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate i IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="30aaa-366">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="30aaa-367">6.2.1 MutualCertificate WSS1.0</span><span class="sxs-lookup"><span data-stu-id="30aaa-367">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="30aaa-368">Z tego trybu uwierzytelniania, który uwierzytelnia klienta za pomocą X.509 certyfikatów, która jest wyświetlana w warstwie protokołu SOAP jako token inicjatora.</span><span class="sxs-lookup"><span data-stu-id="30aaa-368">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="30aaa-369">Usługa jest również uwierzytelniony za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="30aaa-369">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="30aaa-370">Wiązanie używane jest powiązanie asymetrycznego z następujących wartości właściwości:</span><span class="sxs-lookup"><span data-stu-id="30aaa-370">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="30aaa-371">Token inicjatora: certyfikat X.509 klienta, z ustawioną .../IncludeToken/AlwaysToRecipient tryb dołączania</span><span class="sxs-lookup"><span data-stu-id="30aaa-371">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="30aaa-372">Odbiorcy tokenu: Serwer do certyfikatu X.509, włączenia trybu ustawiono .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="30aaa-372">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="30aaa-373">Token ochrony: False</span><span class="sxs-lookup"><span data-stu-id="30aaa-373">Token Protection: False</span></span>  
  
 <span data-ttu-id="30aaa-374">Cały nagłówek i podpisy treści: True</span><span class="sxs-lookup"><span data-stu-id="30aaa-374">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="30aaa-375">Kolejność Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="30aaa-375">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="30aaa-376">Szyfrowanie podpisów: True</span><span class="sxs-lookup"><span data-stu-id="30aaa-376">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="30aaa-377">Zasady</span><span class="sxs-lookup"><span data-stu-id="30aaa-377">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30aaa-378">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30aaa-378">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30aaa-379">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-379">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-380">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-380">Response</span></span>  
  
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
  
 <span data-ttu-id="30aaa-381">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30aaa-381">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="30aaa-382">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-382">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-383">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-383">Response</span></span>  
  
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
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="30aaa-384">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="30aaa-384">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="30aaa-385">Z tego trybu uwierzytelniania, który uwierzytelnia klienta za pomocą X.509 certyfikatów, która jest wyświetlana w warstwie protokołu SOAP jako token inicjatora.</span><span class="sxs-lookup"><span data-stu-id="30aaa-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="30aaa-386">Usługa jest również uwierzytelniony za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="30aaa-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="30aaa-387">Wiązanie używane jest powiązanie asymetrycznego z następujących wartości właściwości:</span><span class="sxs-lookup"><span data-stu-id="30aaa-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="30aaa-388">Token inicjatora: X509 klienta certyfikatu, tryb dołączania jest ustawiony na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="30aaa-388">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="30aaa-389">Odbiorcy tokenu: X509 serwera certyfikatów, tryb dołączania jest ustawiony na .../IncludeToken/AlwaysToInitiator</span><span class="sxs-lookup"><span data-stu-id="30aaa-389">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="30aaa-390">Token ochrony: False</span><span class="sxs-lookup"><span data-stu-id="30aaa-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="30aaa-391">Cały nagłówek i podpisy treści: True</span><span class="sxs-lookup"><span data-stu-id="30aaa-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="30aaa-392">Kolejność Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="30aaa-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="30aaa-393">Szyfrowanie podpisów: True</span><span class="sxs-lookup"><span data-stu-id="30aaa-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="30aaa-394">Zasady</span><span class="sxs-lookup"><span data-stu-id="30aaa-394">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30aaa-395">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30aaa-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30aaa-396">Żądanie i odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-396">Request and Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30aaa-397">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30aaa-397">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30aaa-398">Żądanie i odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-398">Request and Response</span></span>  
  
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
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="30aaa-399">6.2.3 przy użyciu SymmetricBinding X.509 usługi uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="30aaa-399">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="30aaa-400">"WSS10" przewidzianych ograniczoną obsługę scenariuszy z X509 tokenów.</span><span class="sxs-lookup"><span data-stu-id="30aaa-400">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="30aaa-401">Na przykład nie było możliwości wykonania w celu zapewnienia ochrony podpis i szyfrowanie wiadomości za pomocą tylko usługi X509 tokenu.</span><span class="sxs-lookup"><span data-stu-id="30aaa-401">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="30aaa-402">"WSS11" wprowadzono użycie EncryptedKey jako tokenu symetrycznego.</span><span class="sxs-lookup"><span data-stu-id="30aaa-402">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="30aaa-403">Teraz tymczasowego klucza zaszyfrowanego dla certyfikatu X.509 usługi można użyć do ochrony wiadomości zarówno żądań i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="30aaa-403">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="30aaa-404">Tryby uwierzytelniania opisanego w sekcji 6.4 poniżej użycia tego wzorca.</span><span class="sxs-lookup"><span data-stu-id="30aaa-404">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="30aaa-405">WS-SecurityPolicy opisuje tego wzorca z usługą za pomocą SymmetricBinding X509 token jako token ochrony.</span><span class="sxs-lookup"><span data-stu-id="30aaa-405">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="30aaa-406">Tryby uwierzytelniania AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 i IssuedTokenForCertificate wszystkich za pomocą podobnego wystąpienia sp:SymmetricBinding wartości następujących właściwości:</span><span class="sxs-lookup"><span data-stu-id="30aaa-406">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="30aaa-407">Token ochrony: X509 serwera certyfikatów, tryb dołączania jest ustawiony na .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="30aaa-407">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="30aaa-408">Token ochrony: False</span><span class="sxs-lookup"><span data-stu-id="30aaa-408">Token Protection: False</span></span>  
  
 <span data-ttu-id="30aaa-409">Cały nagłówek i podpisy treści: True</span><span class="sxs-lookup"><span data-stu-id="30aaa-409">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="30aaa-410">Kolejność Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="30aaa-410">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="30aaa-411">Szyfrowanie podpisów: True</span><span class="sxs-lookup"><span data-stu-id="30aaa-411">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="30aaa-412">Powyżej tryby uwierzytelniania różnią się tylko przez pomocnicze tokeny, których używają.</span><span class="sxs-lookup"><span data-stu-id="30aaa-412">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="30aaa-413">AnonymousForCertificate nie ma żadnych tokenów pomocniczych, MutualCertificate WSS 1.1 ma klienta X509 certyfikatów jako wprowadzająca tokenami pomocniczymi, UserNameForCertificate ma Token nazwy użytkownika jako podpisanego tokenu pomocniczego i IssuedTokenForCertificate został wystawiony token jako tokenu pomocniczego.</span><span class="sxs-lookup"><span data-stu-id="30aaa-413">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="30aaa-414">Zasady</span><span class="sxs-lookup"><span data-stu-id="30aaa-414">Policy</span></span>  
  
 <span data-ttu-id="30aaa-415">Powiązanie symetryczne</span><span class="sxs-lookup"><span data-stu-id="30aaa-415">Symmetric Binding</span></span>  
  
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
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="30aaa-416">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="30aaa-416">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="30aaa-417">Z tego trybu uwierzytelniania anonimowego jest klient i Usługa uwierzytelniania za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="30aaa-417">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="30aaa-418">Wiązanie używane jest wystąpieniem symetrycznego powiązanie, zgodnie z opisem w 6.4.2.</span><span class="sxs-lookup"><span data-stu-id="30aaa-418">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="30aaa-419">Zasady</span><span class="sxs-lookup"><span data-stu-id="30aaa-419">Policy</span></span>  
  
 <span data-ttu-id="30aaa-420">Zobacz "Policy" w 6.2.3 powyżej dla powiązania szczegóły</span><span class="sxs-lookup"><span data-stu-id="30aaa-420">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30aaa-421">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30aaa-421">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30aaa-422">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-422">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-423">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-423">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30aaa-424">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30aaa-424">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30aaa-425">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-425">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-426">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-426">Response</span></span>  
  
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
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="30aaa-427">6.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="30aaa-427">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="30aaa-428">Z tego trybu uwierzytelniania klient przeprowadza uwierzytelnianie usługi przy użyciu Token nazwy użytkownika, który jest wyświetlany w warstwie protokołu SOAP jako podpisanego tokenu pomocniczego.</span><span class="sxs-lookup"><span data-stu-id="30aaa-428">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="30aaa-429">Usługa uwierzytelnia klienta, za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="30aaa-429">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="30aaa-430">Wiązanie używane jest symetrycznego powiązania z tokenem ochrony klucza wygenerowanych przez klienta, szyfrowany za pomocą klucza publicznego usługi trwa.</span><span class="sxs-lookup"><span data-stu-id="30aaa-430">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="30aaa-431">Zasady</span><span class="sxs-lookup"><span data-stu-id="30aaa-431">Policy</span></span>  
  
 <span data-ttu-id="30aaa-432">Zobacz "Policy" w 6.2.3 powyżej dla powiązania szczegóły</span><span class="sxs-lookup"><span data-stu-id="30aaa-432">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="30aaa-433">Podpisany Token pomocniczy</span><span class="sxs-lookup"><span data-stu-id="30aaa-433">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30aaa-434">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30aaa-434">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30aaa-435">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-435">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-436">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-436">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30aaa-437">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30aaa-437">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30aaa-438">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-438">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-439">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-439">Response</span></span>  
  
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
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="30aaa-440">6.2.6 MutualCertificate (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="30aaa-440">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="30aaa-441">Z tego trybu uwierzytelniania, który uwierzytelnia klienta za pomocą X.509 certyfikatów, która jest wyświetlana w warstwie protokołu SOAP jako tokenu pomocniczego.</span><span class="sxs-lookup"><span data-stu-id="30aaa-441">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="30aaa-442">Usługa jest również uwierzytelniony za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="30aaa-442">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="30aaa-443">Wiązanie używane jest symetrycznego powiązania z tokenem ochrony klucza wygenerowanych przez klienta, szyfrowany za pomocą klucza publicznego usługi trwa.</span><span class="sxs-lookup"><span data-stu-id="30aaa-443">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="30aaa-444">Zasady</span><span class="sxs-lookup"><span data-stu-id="30aaa-444">Policy</span></span>  
  
 <span data-ttu-id="30aaa-445">Zobacz zasady w 6.2.3 dla powiązania szczegóły</span><span class="sxs-lookup"><span data-stu-id="30aaa-445">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="30aaa-446">Wprowadzająca Obsługa tokenu</span><span class="sxs-lookup"><span data-stu-id="30aaa-446">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30aaa-447">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30aaa-447">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30aaa-448">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-448">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-449">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-449">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30aaa-450">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30aaa-450">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30aaa-451">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-451">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-452">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-452">Response</span></span>  
  
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
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="30aaa-453">6.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="30aaa-453">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="30aaa-454">To uwierzytelnianie trybu tak, ale zamiast tego klient nie uwierzytelniania w usłudze przedstawia token wystawiony przez usługę STS i okaże się wiedzę na temat klucza wspólnego.</span><span class="sxs-lookup"><span data-stu-id="30aaa-454">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="30aaa-455">Wystawiony token jest wyświetlany w warstwie protokołu SOAP jako tokenu pomocniczego.</span><span class="sxs-lookup"><span data-stu-id="30aaa-455">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="30aaa-456">Usługa uwierzytelnia klienta, za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="30aaa-456">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="30aaa-457">Wiązanie używane jest symetrycznego powiązania z tokenem ochrony klucza wygenerowanych przez klienta, szyfrowany za pomocą klucza publicznego usługi trwa.</span><span class="sxs-lookup"><span data-stu-id="30aaa-457">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="30aaa-458">Zasady</span><span class="sxs-lookup"><span data-stu-id="30aaa-458">Policy</span></span>  
  
 <span data-ttu-id="30aaa-459">Zobacz zasady w 6.2.3 powyżej szczegółowe powiązania</span><span class="sxs-lookup"><span data-stu-id="30aaa-459">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="30aaa-460">Wprowadzająca Obsługa tokenu</span><span class="sxs-lookup"><span data-stu-id="30aaa-460">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30aaa-461">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30aaa-461">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30aaa-462">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-462">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-463">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-463">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30aaa-464">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30aaa-464">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30aaa-465">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-465">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-466">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-466">Response</span></span>  
  
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
  
## <a name="63-kerberos"></a><span data-ttu-id="30aaa-467">6.3 protokołu Kerberos</span><span class="sxs-lookup"><span data-stu-id="30aaa-467">6.3 Kerberos</span></span>  
 <span data-ttu-id="30aaa-468">Z tego trybu uwierzytelniania klient przeprowadza uwierzytelnianie usługi przy użyciu biletu protokołu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="30aaa-468">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="30aaa-469">Korzystając z tego samego biletu także uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="30aaa-469">That same ticket also provides server authentication.</span></span> <span data-ttu-id="30aaa-470">Wiązanie używane jest symetrycznego powiązania z następującymi właściwościami;</span><span class="sxs-lookup"><span data-stu-id="30aaa-470">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="30aaa-471">Token ochrony: Biletu Kerberos, tryb dołączania ustawiono .../IncludeToken/Once</span><span class="sxs-lookup"><span data-stu-id="30aaa-471">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="30aaa-472">Token ochrony: False</span><span class="sxs-lookup"><span data-stu-id="30aaa-472">Token Protection: False</span></span>  
  
 <span data-ttu-id="30aaa-473">Cały nagłówek i podpisy treści: True</span><span class="sxs-lookup"><span data-stu-id="30aaa-473">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="30aaa-474">Kolejność Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="30aaa-474">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="30aaa-475">Szyfrowanie podpisów: True</span><span class="sxs-lookup"><span data-stu-id="30aaa-475">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="30aaa-476">Zasady</span><span class="sxs-lookup"><span data-stu-id="30aaa-476">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30aaa-477">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30aaa-477">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30aaa-478">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-478">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-479">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-479">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30aaa-480">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30aaa-480">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30aaa-481">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-481">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="30aaa-482">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-482">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="30aaa-483">6.4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="30aaa-483">6.4 IssuedToken</span></span>  
 <span data-ttu-id="30aaa-484">W ten tryb uwierzytelniania, które klient nie uwierzytelniania w usłudze, zamiast klienta wyświetlany token wystawiony przez usługę STS oraz okaże się wiedzę na temat klucza wspólnego.</span><span class="sxs-lookup"><span data-stu-id="30aaa-484">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="30aaa-485">Usługa nie jest uwierzytelniony do klienta tak, zamiast niego usługi STS szyfruje klucz udostępniony jako część wystawionego tokenu tak, aby tylko usługa może odszyfrować klucza.</span><span class="sxs-lookup"><span data-stu-id="30aaa-485">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="30aaa-486">Wiązanie używane jest jako symetrycznego powiązania z następującymi właściwościami;</span><span class="sxs-lookup"><span data-stu-id="30aaa-486">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="30aaa-487">Token ochrony: Wystawiony Token, tryb dołączania jest ustawiony na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="30aaa-487">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="30aaa-488">Token ochrony: False</span><span class="sxs-lookup"><span data-stu-id="30aaa-488">Token Protection: False</span></span>  
  
 <span data-ttu-id="30aaa-489">Cały nagłówek i podpisy treści: True</span><span class="sxs-lookup"><span data-stu-id="30aaa-489">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="30aaa-490">Kolejność Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="30aaa-490">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="30aaa-491">Szyfrowanie podpisów: True</span><span class="sxs-lookup"><span data-stu-id="30aaa-491">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="30aaa-492">Zasady</span><span class="sxs-lookup"><span data-stu-id="30aaa-492">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30aaa-493">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30aaa-493">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30aaa-494">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-494">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-495">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-495">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30aaa-496">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30aaa-496">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30aaa-497">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-497">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-498">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-498">Response</span></span>  
  
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
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="30aaa-499">6.5 przy użyciu SslNegotiated dla usługi uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="30aaa-499">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="30aaa-500">W tej sekcji opisano grupę tryby uwierzytelniania, które symetrycznego powiązania za pomocą tokenu ochrony jest kontekst tokenu zabezpieczeń na WS-SecureConversation (WS-SC), wykonując protokół TLS za pośrednictwem protokołu WS-Trust (WS-T) RST negocjowane jest którego wartość klucza / Odpowiedź RSTR wiadomości.</span><span class="sxs-lookup"><span data-stu-id="30aaa-500">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="30aaa-501">Szczegóły implementacji uzgadniania TLS za pomocą protokołu WS-Trust są opisane w TLSNEGO.</span><span class="sxs-lookup"><span data-stu-id="30aaa-501">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="30aaa-502">W tym miejscu w przykładach komunikat możemy przyjmie założenie, że SCT z kontekstem zabezpieczeń skojarzony jest już ustalone przez uzgadniania.</span><span class="sxs-lookup"><span data-stu-id="30aaa-502">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="30aaa-503">Wiązanie używane jest symetrycznego powiązania z następującymi właściwościami;</span><span class="sxs-lookup"><span data-stu-id="30aaa-503">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="30aaa-504">Token ochrony: SslContextToken, tryb dołączania ustawiono .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="30aaa-504">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="30aaa-505">Token ochrony: False</span><span class="sxs-lookup"><span data-stu-id="30aaa-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="30aaa-506">Cały nagłówek i podpisy treści: True</span><span class="sxs-lookup"><span data-stu-id="30aaa-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="30aaa-507">Kolejność Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="30aaa-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="30aaa-508">Szyfrowanie podpisów: True</span><span class="sxs-lookup"><span data-stu-id="30aaa-508">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="30aaa-509">6.5.1 zasady SslNegotiated usługi uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="30aaa-509">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="30aaa-510">Zasady dla wszystkich metod uwierzytelniania w tej sekcji są podobne i różnią się tylko przez określonych podpisanych obsługi lub potwierdzania tokenów używanych.</span><span class="sxs-lookup"><span data-stu-id="30aaa-510">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
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
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="30aaa-511">6.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="30aaa-511">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="30aaa-512">Z tego trybu uwierzytelniania anonimowego jest klient i Usługa uwierzytelniania za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="30aaa-512">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="30aaa-513">Wiązanie używane jest wystąpieniem symetrycznego powiązanie, zgodnie z opisem w powyższej 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="30aaa-513">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="30aaa-514">Zasady</span><span class="sxs-lookup"><span data-stu-id="30aaa-514">Policy</span></span>  
  
 <span data-ttu-id="30aaa-515">Zobacz zasady w 6.5.1 powyżej szczegółowe powiązania.</span><span class="sxs-lookup"><span data-stu-id="30aaa-515">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30aaa-516">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30aaa-516">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30aaa-517">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-517">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-518">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-518">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30aaa-519">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30aaa-519">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30aaa-520">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-520">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-521">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-521">Response</span></span>  
  
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
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="30aaa-522">6.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="30aaa-522">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="30aaa-523">Z tego uwierzytelnienia jest tryb, który klient jest uwierzytelniany przy użyciu Token nazwy użytkownika, który jest wyświetlany w warstwie protokołu SOAP jako podpisanego tokenu pomocniczego.</span><span class="sxs-lookup"><span data-stu-id="30aaa-523">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="30aaa-524">Usługa jest uwierzytelniany przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="30aaa-524">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="30aaa-525">Wiązanie używane jest wystąpieniem symetrycznego powiązanie, zgodnie z opisem w 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="30aaa-525">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="30aaa-526">Zasady</span><span class="sxs-lookup"><span data-stu-id="30aaa-526">Policy</span></span>  
  
 <span data-ttu-id="30aaa-527">W sekcji 6.5.1 powyżej powiązanie szczegóły</span><span class="sxs-lookup"><span data-stu-id="30aaa-527">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="30aaa-528">Podpisany Token pomocniczy</span><span class="sxs-lookup"><span data-stu-id="30aaa-528">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30aaa-529">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30aaa-529">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30aaa-530">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-530">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-531">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-531">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30aaa-532">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30aaa-532">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30aaa-533">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-533">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-534">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-534">Response</span></span>  
  
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
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="30aaa-535">6.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="30aaa-535">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="30aaa-536">To uwierzytelnianie trybu tak, ale zamiast tego klient nie uwierzytelniania w usłudze przedstawia token wystawiony przez usługę STS i okaże się wiedzę na temat klucza wspólnego.</span><span class="sxs-lookup"><span data-stu-id="30aaa-536">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="30aaa-537">Wystawiony token jest wyświetlany w warstwie protokołu SOAP jako tokenu pomocniczego.</span><span class="sxs-lookup"><span data-stu-id="30aaa-537">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="30aaa-538">Usługa jest uwierzytelniany przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="30aaa-538">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="30aaa-539">Wiązanie używane jest wystąpieniem symetrycznego powiązanie, zgodnie z opisem w powyższej 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="30aaa-539">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="30aaa-540">Zasady</span><span class="sxs-lookup"><span data-stu-id="30aaa-540">Policy</span></span>  
  
 <span data-ttu-id="30aaa-541">W sekcji 6.5.1 powyżej powiązanie szczegóły</span><span class="sxs-lookup"><span data-stu-id="30aaa-541">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="30aaa-542">Wprowadzająca Obsługa tokenu</span><span class="sxs-lookup"><span data-stu-id="30aaa-542">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30aaa-543">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30aaa-543">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30aaa-544">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-544">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-545">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-545">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30aaa-546">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30aaa-546">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30aaa-547">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-547">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-548">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-548">Response</span></span>  
  
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
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="30aaa-549">6.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="30aaa-549">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="30aaa-550">Z tego trybu uwierzytelniania klient i Usługa uwierzytelniania za pomocą certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="30aaa-550">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="30aaa-551">Wiązanie używane jest wystąpieniem symetrycznego powiązanie, zgodnie z opisem w powyższej 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="30aaa-551">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="30aaa-552">Zasady</span><span class="sxs-lookup"><span data-stu-id="30aaa-552">Policy</span></span>  
  
 <span data-ttu-id="30aaa-553">W sekcji 6.5.1 powyżej powiązanie szczegóły</span><span class="sxs-lookup"><span data-stu-id="30aaa-553">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="30aaa-554">Wprowadzająca Obsługa tokenu</span><span class="sxs-lookup"><span data-stu-id="30aaa-554">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30aaa-555">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30aaa-555">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30aaa-556">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-556">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-557">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-557">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30aaa-558">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30aaa-558">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30aaa-559">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-559">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-560">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-560">Response</span></span>  
  
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
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="30aaa-561">6.6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="30aaa-561">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="30aaa-562">Z tego trybu uwierzytelniania protokół negocjacji służy do uwierzytelniania klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="30aaa-562">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="30aaa-563">Protokół Kerberos jest używany, jeśli to możliwe, w przeciwnym razie NTLM.</span><span class="sxs-lookup"><span data-stu-id="30aaa-563">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="30aaa-564">Wiązanie używane jest symetrycznego powiązania z następującymi właściwościami;</span><span class="sxs-lookup"><span data-stu-id="30aaa-564">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="30aaa-565">Token ochrony: SpnegoContextToken, tryb dołączania ustawiono .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="30aaa-565">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="30aaa-566">Token ochrony: False</span><span class="sxs-lookup"><span data-stu-id="30aaa-566">Token Protection: False</span></span>  
  
 <span data-ttu-id="30aaa-567">Cały nagłówek i podpisy treści: True</span><span class="sxs-lookup"><span data-stu-id="30aaa-567">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="30aaa-568">Kolejność Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="30aaa-568">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="30aaa-569">Szyfrowanie podpisów: True</span><span class="sxs-lookup"><span data-stu-id="30aaa-569">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="30aaa-570">Zasady</span><span class="sxs-lookup"><span data-stu-id="30aaa-570">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30aaa-571">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30aaa-571">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30aaa-572">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-572">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-573">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-573">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30aaa-574">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30aaa-574">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30aaa-575">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-575">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-576">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-576">Response</span></span>  
  
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
  
### <a name="67-secureconversation"></a><span data-ttu-id="30aaa-577">6.7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="30aaa-577">6.7 SecureConversation</span></span>  
 <span data-ttu-id="30aaa-578">Wiązanie używane jest symetrycznego powiązania z tokenem ochrony trwa SCT na WS-SecureConversation (WS-SC).</span><span class="sxs-lookup"><span data-stu-id="30aaa-578">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="30aaa-579">SCT negocjowane jest za pomocą protokołu WS-Trust (WS-Trust) lub protokołu WS-SecureConversation (WS-SC) zgodnie z zagnieżdżonych powiązania, który sam jest powiązanie symetrycznego, które wykorzystuje protokół negocjacji.</span><span class="sxs-lookup"><span data-stu-id="30aaa-579">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="30aaa-580">Protokół negocjacji będzie korzystać z protokołu Kerberos do uwierzytelniania klienta i serwera, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="30aaa-580">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="30aaa-581">Jeśli nie można użyć protokołu Kerberos, jego powróci do uwierzytelniania NTLM.</span><span class="sxs-lookup"><span data-stu-id="30aaa-581">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="30aaa-582">Zasady</span><span class="sxs-lookup"><span data-stu-id="30aaa-582">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="30aaa-583">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="30aaa-583">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="30aaa-584">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-584">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-585">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-585">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="30aaa-586">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="30aaa-586">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="30aaa-587">Żądanie</span><span class="sxs-lookup"><span data-stu-id="30aaa-587">Request</span></span>  
  
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
  
 <span data-ttu-id="30aaa-588">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="30aaa-588">Response</span></span>  
  
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
