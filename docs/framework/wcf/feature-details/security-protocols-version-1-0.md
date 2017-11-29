---
title: "Protokoły zabezpieczeń wersja 1.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f40c79ad1a6eedc2b1de4dffa9de5b48aeb8e6f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="124f5-102">Protokoły zabezpieczeń wersja 1.0</span><span class="sxs-lookup"><span data-stu-id="124f5-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="124f5-103">Protokoły zabezpieczeń usług sieci Web zapewniają mechanizmy zabezpieczeń usług sieci Web, które obejmują wszystkie istniejącym w przedsiębiorstwie wiadomości wymagania dotyczące zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="124f5-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="124f5-104">W tej sekcji opisano [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] szczegółów w wersji 1.0 (w <xref:System.ServiceModel.Channels.SecurityBindingElement>) dla następujących sieci Web usług protokołów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="124f5-104">This section describes the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="124f5-105">Specyfikacja/dokumentu</span><span class="sxs-lookup"><span data-stu-id="124f5-105">Specification/Document</span></span>|<span data-ttu-id="124f5-106">Łącze</span><span class="sxs-lookup"><span data-stu-id="124f5-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="124f5-107">WSS: Zabezpieczenia komunikatów SOAP 1.0</span><span class="sxs-lookup"><span data-stu-id="124f5-107">WSS: SOAP Message Security 1.0</span></span>|<span data-ttu-id="124f5-108">http://docs.oasis-open.org/WSS/2004/01/oasis-200401-WSS-SOAP-Message-Security-1.0.PDF</span><span class="sxs-lookup"><span data-stu-id="124f5-108">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf</span></span>|  
|<span data-ttu-id="124f5-109">Programu WSS: Profil Token nazwy użytkownika 1.0</span><span class="sxs-lookup"><span data-stu-id="124f5-109">WSS: Username Token Profile 1.0</span></span>|<span data-ttu-id="124f5-110">http://docs.oasis-open.org/WSS/2004/01/oasis-200401-WSS-username-token-profile-1.0.PDF</span><span class="sxs-lookup"><span data-stu-id="124f5-110">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="124f5-111">WSS: X509 Token profilu 1.0</span><span class="sxs-lookup"><span data-stu-id="124f5-111">WSS: X509 Token Profile 1.0</span></span>|<span data-ttu-id="124f5-112">http://docs.oasis-open.org/WSS/2004/01/oasis-200401-WSS-x509-token-profile-1.0.PDF</span><span class="sxs-lookup"><span data-stu-id="124f5-112">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="124f5-113">Programu WSS: SAML 1.1 Token profilu 1.0</span><span class="sxs-lookup"><span data-stu-id="124f5-113">WSS: SAML 1.1 Token Profile 1.0</span></span>|<span data-ttu-id="124f5-114">http://docs.oasis-open.org/WSS/oasis-WSS-SAML-token-profile-1.0.PDF</span><span class="sxs-lookup"><span data-stu-id="124f5-114">http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="124f5-115">Programu WSS: Zabezpieczenia komunikatów SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="124f5-115">WSS: SOAP Message Security 1.1</span></span>|<span data-ttu-id="124f5-116">http://www.oasis-open.org/committees/Download.php/16790/WSS-V1.1-spec-OS-SOAPMessageSecurity.PDF</span><span class="sxs-lookup"><span data-stu-id="124f5-116">http://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf</span></span>|  
|<span data-ttu-id="124f5-117">1.1 tokenu profilu programu WSS nazwy użytkownika</span><span class="sxs-lookup"><span data-stu-id="124f5-117">WSS Username Token Profile 1.1</span></span>|<span data-ttu-id="124f5-118">http://docs.oasis-open.org/WSS/2004/01/oasis-200401-WSS-username-token-profile-1.0.PDF</span><span class="sxs-lookup"><span data-stu-id="124f5-118">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="124f5-119">Programu WSS: Profil tokenu X.509 1.1</span><span class="sxs-lookup"><span data-stu-id="124f5-119">WSS: X.509 Token Profile 1.1</span></span>|<span data-ttu-id="124f5-120">http://www.oasis-open.org/committees/Download.php/16785/WSS-V1.1-spec-OS-x509TokenProfile.PDF</span><span class="sxs-lookup"><span data-stu-id="124f5-120">http://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf</span></span>|  
|<span data-ttu-id="124f5-121">WSS: 1.1 profilu Token protokołu Kerberos</span><span class="sxs-lookup"><span data-stu-id="124f5-121">WSS: Kerberos Token Profile 1.1</span></span>|<span data-ttu-id="124f5-122">http://www.oasis-open.org/committees/Download.php/16788/WSS-V1.1-spec-OS-KerberosTokenProfile.PDF</span><span class="sxs-lookup"><span data-stu-id="124f5-122">http://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf</span></span>|  
|<span data-ttu-id="124f5-123">Programu WSS: SAML 1.1 Token 1.1 profilu</span><span class="sxs-lookup"><span data-stu-id="124f5-123">WSS: SAML 1.1 Token Profile 1.1</span></span>|<span data-ttu-id="124f5-124">http://www.oasis-open.org/committees/Download.php/16768/WSS-V1.1-spec-OS-SAMLTokenProfile.PDF</span><span class="sxs-lookup"><span data-stu-id="124f5-124">http://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf</span></span>|  
|<span data-ttu-id="124f5-125">Zabezpieczenia WS konwersacji</span><span class="sxs-lookup"><span data-stu-id="124f5-125">WS-Secure Conversation</span></span>|<span data-ttu-id="124f5-126">http://msdn.microsoft.com/ws/2005/02/ws-Secure-Conversation/</span><span class="sxs-lookup"><span data-stu-id="124f5-126">http://msdn.microsoft.com/ws/2005/02/ws-secure-conversation/</span></span>|  
|<span data-ttu-id="124f5-127">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="124f5-127">WS-Trust</span></span>|<span data-ttu-id="124f5-128">http://msdn.microsoft.com/ws/2005/02/WS-Trust/</span><span class="sxs-lookup"><span data-stu-id="124f5-128">http://msdn.microsoft.com/ws/2005/02/ws-trust/</span></span>|  
|<span data-ttu-id="124f5-129">Uwaga aplikacji:</span><span class="sxs-lookup"><span data-stu-id="124f5-129">Application Note:</span></span><br /><br /> <span data-ttu-id="124f5-130">Za pomocą protokołu WS-Trust na uzgadnianie protokołu TLS</span><span class="sxs-lookup"><span data-stu-id="124f5-130">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="124f5-131">Do opublikowania</span><span class="sxs-lookup"><span data-stu-id="124f5-131">To be published</span></span>|  
|<span data-ttu-id="124f5-132">Uwaga aplikacji:</span><span class="sxs-lookup"><span data-stu-id="124f5-132">Application Note:</span></span><br /><br /> <span data-ttu-id="124f5-133">Za pomocą protokołu WS-Trust dla SPNEGO</span><span class="sxs-lookup"><span data-stu-id="124f5-133">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="124f5-134">Do opublikowania</span><span class="sxs-lookup"><span data-stu-id="124f5-134">To be published</span></span>|  
|<span data-ttu-id="124f5-135">Uwaga aplikacji:</span><span class="sxs-lookup"><span data-stu-id="124f5-135">Application Note:</span></span><br /><br /> <span data-ttu-id="124f5-136">Usługi sieci Web adresowanie odwołania do punktu końcowego i tożsamość</span><span class="sxs-lookup"><span data-stu-id="124f5-136">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="124f5-137">Do opublikowania</span><span class="sxs-lookup"><span data-stu-id="124f5-137">To be published</span></span>|  
|<span data-ttu-id="124f5-138">WS-SecurityPolicy 1.1</span><span class="sxs-lookup"><span data-stu-id="124f5-138">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="124f5-139">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="124f5-139">(2005/07)</span></span>|<span data-ttu-id="124f5-140">http://msdn.microsoft.com/ws/2005/07/WS-Security-Policy/</span><span class="sxs-lookup"><span data-stu-id="124f5-140">http://msdn.microsoft.com/ws/2005/07/ws-security-policy/</span></span><br /><br /> <span data-ttu-id="124f5-141">zmienione erracie przesłane do http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html Komitet Techniczny WS-SX OASIS</span><span class="sxs-lookup"><span data-stu-id="124f5-141">as amended by errata submitted to OASIS WS-SX Technical Committee http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html</span></span>|  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="124f5-142">, wersja 1, zapewnia 17 tryby uwierzytelniania, które mogą służyć jako podstawa dla konfiguracji zabezpieczeń usług sieci Web.</span><span class="sxs-lookup"><span data-stu-id="124f5-142">, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="124f5-143">Każdego trybu jest zoptymalizowana pod kątem wspólny zbiór wymagania dotyczące wdrażania, takie jak:</span><span class="sxs-lookup"><span data-stu-id="124f5-143">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
-   <span data-ttu-id="124f5-144">Poświadczenia używane do uwierzytelniania klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="124f5-144">Credentials used to authenticate client and service.</span></span>  
  
-   <span data-ttu-id="124f5-145">Mechanizmy ochrony zabezpieczeń transportu lub wiadomości.</span><span class="sxs-lookup"><span data-stu-id="124f5-145">Message or transport security protection mechanisms.</span></span>  
  
-   <span data-ttu-id="124f5-146">Wzorce wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="124f5-146">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="124f5-147">Tryb uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="124f5-147">Authentication Mode</span></span>|<span data-ttu-id="124f5-148">Uwierzytelnianie klienta</span><span class="sxs-lookup"><span data-stu-id="124f5-148">Client Authentication</span></span>|<span data-ttu-id="124f5-149">Uwierzytelnianie serwera</span><span class="sxs-lookup"><span data-stu-id="124f5-149">Server Authentication</span></span>|<span data-ttu-id="124f5-150">Tryb</span><span class="sxs-lookup"><span data-stu-id="124f5-150">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="124f5-151">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="124f5-151">UserNameOverTransport</span></span>|<span data-ttu-id="124f5-152">Nazwa użytkownika/hasło</span><span class="sxs-lookup"><span data-stu-id="124f5-152">User name/password</span></span>|<span data-ttu-id="124f5-153">X509</span><span class="sxs-lookup"><span data-stu-id="124f5-153">X509</span></span>|<span data-ttu-id="124f5-154">Transportu</span><span class="sxs-lookup"><span data-stu-id="124f5-154">Transport</span></span>|  
|<span data-ttu-id="124f5-155">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="124f5-155">CertificateOverTransport</span></span>|<span data-ttu-id="124f5-156">X509</span><span class="sxs-lookup"><span data-stu-id="124f5-156">X509</span></span>|<span data-ttu-id="124f5-157">X509</span><span class="sxs-lookup"><span data-stu-id="124f5-157">X509</span></span>|<span data-ttu-id="124f5-158">Transportu</span><span class="sxs-lookup"><span data-stu-id="124f5-158">Transport</span></span>|  
|<span data-ttu-id="124f5-159">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="124f5-159">KerberosOverTransport</span></span>|<span data-ttu-id="124f5-160">Windows</span><span class="sxs-lookup"><span data-stu-id="124f5-160">Windows</span></span>|<span data-ttu-id="124f5-161">X509</span><span class="sxs-lookup"><span data-stu-id="124f5-161">X509</span></span>|<span data-ttu-id="124f5-162">Transportu</span><span class="sxs-lookup"><span data-stu-id="124f5-162">Transport</span></span>|  
|<span data-ttu-id="124f5-163">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="124f5-163">IssuedTokenOverTransport</span></span>|<span data-ttu-id="124f5-164">Federacyjna</span><span class="sxs-lookup"><span data-stu-id="124f5-164">Federated</span></span>|<span data-ttu-id="124f5-165">X509</span><span class="sxs-lookup"><span data-stu-id="124f5-165">X509</span></span>|<span data-ttu-id="124f5-166">Transportu</span><span class="sxs-lookup"><span data-stu-id="124f5-166">Transport</span></span>|  
|<span data-ttu-id="124f5-167">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="124f5-167">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="124f5-168">Wynegocjowane interfejsu Sspi systemu Windows</span><span class="sxs-lookup"><span data-stu-id="124f5-168">Windows Sspi Negotiated</span></span>|<span data-ttu-id="124f5-169">Wynegocjowane interfejsu Sspi systemu Windows</span><span class="sxs-lookup"><span data-stu-id="124f5-169">Windows Sspi Negotiated</span></span>|<span data-ttu-id="124f5-170">Transportu</span><span class="sxs-lookup"><span data-stu-id="124f5-170">Transport</span></span>|  
|<span data-ttu-id="124f5-171">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="124f5-171">AnonymousForCertificate</span></span>|<span data-ttu-id="124f5-172">Brak</span><span class="sxs-lookup"><span data-stu-id="124f5-172">None</span></span>|<span data-ttu-id="124f5-173">X509</span><span class="sxs-lookup"><span data-stu-id="124f5-173">X509</span></span>|<span data-ttu-id="124f5-174">Komunikat</span><span class="sxs-lookup"><span data-stu-id="124f5-174">Message</span></span>|  
|<span data-ttu-id="124f5-175">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="124f5-175">UserNameForCertificate</span></span>|<span data-ttu-id="124f5-176">Nazwa użytkownika/hasło</span><span class="sxs-lookup"><span data-stu-id="124f5-176">User name/password</span></span>|<span data-ttu-id="124f5-177">X509</span><span class="sxs-lookup"><span data-stu-id="124f5-177">X509</span></span>|<span data-ttu-id="124f5-178">Komunikat</span><span class="sxs-lookup"><span data-stu-id="124f5-178">Message</span></span>|  
|<span data-ttu-id="124f5-179">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="124f5-179">MutualCertificate</span></span>|<span data-ttu-id="124f5-180">X509</span><span class="sxs-lookup"><span data-stu-id="124f5-180">X509</span></span>|<span data-ttu-id="124f5-181">X509</span><span class="sxs-lookup"><span data-stu-id="124f5-181">X509</span></span>|<span data-ttu-id="124f5-182">Komunikat</span><span class="sxs-lookup"><span data-stu-id="124f5-182">Message</span></span>|  
|<span data-ttu-id="124f5-183">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="124f5-183">MutualCertificateDuplex</span></span>|<span data-ttu-id="124f5-184">X509</span><span class="sxs-lookup"><span data-stu-id="124f5-184">X509</span></span>|<span data-ttu-id="124f5-185">X509</span><span class="sxs-lookup"><span data-stu-id="124f5-185">X509</span></span>|<span data-ttu-id="124f5-186">Komunikat</span><span class="sxs-lookup"><span data-stu-id="124f5-186">Message</span></span>|  
|<span data-ttu-id="124f5-187">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="124f5-187">IssuedTokenForCertificate</span></span>|<span data-ttu-id="124f5-188">Federacyjna</span><span class="sxs-lookup"><span data-stu-id="124f5-188">Federated</span></span>|<span data-ttu-id="124f5-189">X509</span><span class="sxs-lookup"><span data-stu-id="124f5-189">X509</span></span>|<span data-ttu-id="124f5-190">Komunikat</span><span class="sxs-lookup"><span data-stu-id="124f5-190">Message</span></span>|  
|<span data-ttu-id="124f5-191">Kerberos</span><span class="sxs-lookup"><span data-stu-id="124f5-191">Kerberos</span></span>|<span data-ttu-id="124f5-192">Windows</span><span class="sxs-lookup"><span data-stu-id="124f5-192">Windows</span></span>|<span data-ttu-id="124f5-193">Windows</span><span class="sxs-lookup"><span data-stu-id="124f5-193">Windows</span></span>|<span data-ttu-id="124f5-194">Komunikat</span><span class="sxs-lookup"><span data-stu-id="124f5-194">Message</span></span>|  
|<span data-ttu-id="124f5-195">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="124f5-195">IssuedToken</span></span>|<span data-ttu-id="124f5-196">Federacyjna</span><span class="sxs-lookup"><span data-stu-id="124f5-196">Federated</span></span>|<span data-ttu-id="124f5-197">Federacyjna</span><span class="sxs-lookup"><span data-stu-id="124f5-197">Federated</span></span>|<span data-ttu-id="124f5-198">Komunikat</span><span class="sxs-lookup"><span data-stu-id="124f5-198">Message</span></span>|  
|<span data-ttu-id="124f5-199">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="124f5-199">SspiNegotiated</span></span>|<span data-ttu-id="124f5-200">Wynegocjowane interfejsu Sspi systemu Windows</span><span class="sxs-lookup"><span data-stu-id="124f5-200">Windows Sspi Negotiated</span></span>|<span data-ttu-id="124f5-201">Wynegocjowane interfejsu Sspi systemu Windows</span><span class="sxs-lookup"><span data-stu-id="124f5-201">Windows Sspi Negotiated</span></span>|<span data-ttu-id="124f5-202">Komunikat</span><span class="sxs-lookup"><span data-stu-id="124f5-202">Message</span></span>|  
|<span data-ttu-id="124f5-203">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="124f5-203">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="124f5-204">Brak</span><span class="sxs-lookup"><span data-stu-id="124f5-204">None</span></span>|<span data-ttu-id="124f5-205">X509, TLS Nego</span><span class="sxs-lookup"><span data-stu-id="124f5-205">X509, TLS-Nego</span></span>|<span data-ttu-id="124f5-206">Komunikat</span><span class="sxs-lookup"><span data-stu-id="124f5-206">Message</span></span>|  
|<span data-ttu-id="124f5-207">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="124f5-207">UserNameForSslNegotiated</span></span>|<span data-ttu-id="124f5-208">Nazwa użytkownika/hasło</span><span class="sxs-lookup"><span data-stu-id="124f5-208">User name/password</span></span>|<span data-ttu-id="124f5-209">X509, TLS Nego</span><span class="sxs-lookup"><span data-stu-id="124f5-209">X509, TLS-Nego</span></span>|<span data-ttu-id="124f5-210">Komunikat</span><span class="sxs-lookup"><span data-stu-id="124f5-210">Message</span></span>|  
|<span data-ttu-id="124f5-211">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="124f5-211">MutualSslNegotiated</span></span>|<span data-ttu-id="124f5-212">X509</span><span class="sxs-lookup"><span data-stu-id="124f5-212">X509</span></span>|<span data-ttu-id="124f5-213">X509, TLS Nego</span><span class="sxs-lookup"><span data-stu-id="124f5-213">X509, TLS-Nego</span></span>|<span data-ttu-id="124f5-214">Komunikat</span><span class="sxs-lookup"><span data-stu-id="124f5-214">Message</span></span>|  
|<span data-ttu-id="124f5-215">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="124f5-215">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="124f5-216">Federacyjna</span><span class="sxs-lookup"><span data-stu-id="124f5-216">Federated</span></span>|<span data-ttu-id="124f5-217">X509, TLS Nego</span><span class="sxs-lookup"><span data-stu-id="124f5-217">X509, TLS-Nego</span></span>|<span data-ttu-id="124f5-218">Komunikat</span><span class="sxs-lookup"><span data-stu-id="124f5-218">Message</span></span>|  
  
 <span data-ttu-id="124f5-219">Punktów końcowych przy użyciu tych trybach uwierzytelniania można wyrazić ich wymagania dotyczące zabezpieczeń przy użyciu usługi WS-SecurityPolicy (WS-SP).</span><span class="sxs-lookup"><span data-stu-id="124f5-219">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="124f5-220">Ten dokument zawiera opis struktury nagłówka zabezpieczeń i infrastruktury komunikaty dla każdego trybu uwierzytelniania oraz przykłady zasad i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="124f5-220">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="124f5-221">wykorzystuje WS-SecureConversation, aby zapewnić obsługę bezpiecznej sesji do ochrony wymiany wielu komunikatów między aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="124f5-221"> leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="124f5-222">Aby uzyskać szczegóły implementacji, zobacz "Secure sesji" poniżej.</span><span class="sxs-lookup"><span data-stu-id="124f5-222">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="124f5-223">Oprócz tryby uwierzytelniania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zawiera ustawienia, aby kontrolować typowych mechanizmów ochrony, które są stosowane do większości tryby uwierzytelniania zabezpieczeń wiadomości, na przykład: kolejność podpisywania lub szyfrowania, mechanizmy algorytmu wyprowadzania klucza, a potwierdzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="124f5-223">In addition to authentication modes, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="124f5-224">Następujące prefiksy i przestrzenie nazw są używane w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="124f5-224">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="124f5-225">Prefiks</span><span class="sxs-lookup"><span data-stu-id="124f5-225">Prefix</span></span>|<span data-ttu-id="124f5-226">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="124f5-226">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="124f5-227">s</span><span class="sxs-lookup"><span data-stu-id="124f5-227">s</span></span>|<span data-ttu-id="124f5-228">http://www.w3.org/2003/05/SOAP-Envelope</span><span class="sxs-lookup"><span data-stu-id="124f5-228">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="124f5-229">SP</span><span class="sxs-lookup"><span data-stu-id="124f5-229">sp</span></span>|<span data-ttu-id="124f5-230">http://schemas.xmlsoap.org/ws/2005/07/SECURITYPOLICY</span><span class="sxs-lookup"><span data-stu-id="124f5-230">http://schemas.xmlsoap.org/ws/2005/07/securitypolicy</span></span>|  
|<span data-ttu-id="124f5-231">A</span><span class="sxs-lookup"><span data-stu-id="124f5-231">a</span></span>|<span data-ttu-id="124f5-232">http://www.w3.org/2005/08/Addressing</span><span class="sxs-lookup"><span data-stu-id="124f5-232">http://www.w3.org/2005/08/addressing</span></span>|  
|<span data-ttu-id="124f5-233">wsse</span><span class="sxs-lookup"><span data-stu-id="124f5-233">wsse</span></span>|<span data-ttu-id="124f5-234">DO USTALENIA — IDENTYFIKATOR URI PROGRAMU WSS 1.0 JĘZYKA OASIS</span><span class="sxs-lookup"><span data-stu-id="124f5-234">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="124f5-235">wsse11</span><span class="sxs-lookup"><span data-stu-id="124f5-235">wsse11</span></span>|<span data-ttu-id="124f5-236">DO USTALENIA — IDENTYFIKATOR URI PROGRAMU WSS 1.1 JĘZYKA OASIS</span><span class="sxs-lookup"><span data-stu-id="124f5-236">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="124f5-237">wsu</span><span class="sxs-lookup"><span data-stu-id="124f5-237">wsu</span></span>|<span data-ttu-id="124f5-238">Do ustalenia — narzędzie identyfikatora URI OASIS WSS 1.0</span><span class="sxs-lookup"><span data-stu-id="124f5-238">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="124f5-239">ds</span><span class="sxs-lookup"><span data-stu-id="124f5-239">ds</span></span>|<span data-ttu-id="124f5-240">Do ustalenia — identyfikator URI XMLDSig W3C</span><span class="sxs-lookup"><span data-stu-id="124f5-240">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="124f5-241">Wst</span><span class="sxs-lookup"><span data-stu-id="124f5-241">wst</span></span>|<span data-ttu-id="124f5-242">Do ustalenia — identyfikator URI protokołu WS-Trust 2005/02</span><span class="sxs-lookup"><span data-stu-id="124f5-242">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="124f5-243">wssc</span><span class="sxs-lookup"><span data-stu-id="124f5-243">wssc</span></span>|<span data-ttu-id="124f5-244">Do ustalenia — WS-SecureConversation 2005/02 identyfikatora URI</span><span class="sxs-lookup"><span data-stu-id="124f5-244">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="124f5-245">wsaw</span><span class="sxs-lookup"><span data-stu-id="124f5-245">wsaw</span></span>|<span data-ttu-id="124f5-246">Do ustalenia - WS-Addressing przestrzeni nazw zasad</span><span class="sxs-lookup"><span data-stu-id="124f5-246">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="124f5-247">WSP</span><span class="sxs-lookup"><span data-stu-id="124f5-247">wsp</span></span>|<span data-ttu-id="124f5-248">http://schemas.xmlsoap.org/ws/2004/09/Policy</span><span class="sxs-lookup"><span data-stu-id="124f5-248">http://schemas.xmlsoap.org/ws/2004/09/policy</span></span>|  
|<span data-ttu-id="124f5-249">Mssp</span><span class="sxs-lookup"><span data-stu-id="124f5-249">mssp</span></span>|<span data-ttu-id="124f5-250">http://schemas.microsoft.com/ws/2005/07/SECURITYPOLICY</span><span class="sxs-lookup"><span data-stu-id="124f5-250">http://schemas.microsoft.com/ws/2005/07/securitypolicy</span></span>|  
  
## <a name="1-token-profiles"></a><span data-ttu-id="124f5-251">1. Profile tokenu</span><span class="sxs-lookup"><span data-stu-id="124f5-251">1. Token Profiles</span></span>  
 <span data-ttu-id="124f5-252">Specyfikacje zabezpieczenia usług sieci Web reprezentować poświadczeń tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="124f5-252">Web Services Security specifications represent credential as security tokens.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="124f5-253">obsługuje następujące typy tokenów:</span><span class="sxs-lookup"><span data-stu-id="124f5-253"> supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="124f5-254">1.1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="124f5-254">1.1 UsernameToken</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="124f5-255">następujące profile UsernameToken10 i UsernameToken11 z następującymi ograniczeniami:</span><span class="sxs-lookup"><span data-stu-id="124f5-255"> follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="124f5-256">Atrybut R1101 PasswordType w elemencie UsernameToken\Password albo pominięcia ani mieć wartości #PasswordText (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="124f5-256">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="124f5-257">Co można zaimplementować #PasswordDigest przy użyciu rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="124f5-257">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="124f5-258">Zaobserwowano, że #PasswordDigest został często pomylone jako mechanizm ochrony dostatecznie bezpieczne hasło.</span><span class="sxs-lookup"><span data-stu-id="124f5-258">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="124f5-259">Ale #PasswordDigest nie może służyć jako zamiennik szyfrowania UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="124f5-259">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="124f5-260">Podstawowym celem #PasswordDigest jest ochrona przed atakami powtarzania.</span><span class="sxs-lookup"><span data-stu-id="124f5-260">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="124f5-261">W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tryby uwierzytelniania, zagrożenia atakiem polegającym na odtwarzaniu, zostały skorygowane przy użyciu sygnatury komunikatów.</span><span class="sxs-lookup"><span data-stu-id="124f5-261">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="124f5-262">B1102 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nigdy nie emituje identyfikator jednorazowy i utworzono elementy podrzędne UsernameToken.</span><span class="sxs-lookup"><span data-stu-id="124f5-262">B1102 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="124f5-263">Te elementy podrzędne mają na celu pomoc wykrywania powtarzania.</span><span class="sxs-lookup"><span data-stu-id="124f5-263">These sub-elements are intended to help replay detection.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="124f5-264">użyje sygnatury komunikatów.</span><span class="sxs-lookup"><span data-stu-id="124f5-264"> uses message signatures instead.</span></span>  
  
 <span data-ttu-id="124f5-265">OASIS WSS SOAP komunikatów zabezpieczeń UsernameToken Profile 1.1 (UsernameToken11) wprowadzono wyprowadzania klucza z hasła funkcji.</span><span class="sxs-lookup"><span data-stu-id="124f5-265">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="124f5-266">Hasło B1103 UsernameToken nie mogą być używane dla klucza pochodnego i w związku z tym dla operacji kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="124f5-266">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="124f5-267">Uzasadnienie: hasła są zazwyczaj uznane za zbyt słabe do użycia dla operacji kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="124f5-267">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="124f5-268">1.2 x 509 tokenu</span><span class="sxs-lookup"><span data-stu-id="124f5-268">1.2 X509 Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="124f5-269">obsługuje certyfikaty X509v3 jako typ poświadczeń i X509TokenProfile1.0 i X509TokenProfile1.1 jest zgodny z następującymi ograniczeniami:</span><span class="sxs-lookup"><span data-stu-id="124f5-269"> supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="124f5-270">Atrybut R1201 ValueType w elemencie BinarySecurityToken musi mieć wartość #X509v3, gdy zawiera certyfikat X509v3.</span><span class="sxs-lookup"><span data-stu-id="124f5-270">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="124f5-271">WSS X509 Token profilu 1.0 i 1.1 zdefiniuj również #X509PKIPathv1 oraz PKCS&#7; jako typów wartości.</span><span class="sxs-lookup"><span data-stu-id="124f5-271">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="124f5-272">nie obsługuje tego typu.</span><span class="sxs-lookup"><span data-stu-id="124f5-272"> does not support these types.</span></span>  
  
 <span data-ttu-id="124f5-273">R1202 czy rozszerzenia SubjectKeyIdentifier (SKI) znajduje się w X509 certyfikat, wsse:KeyIdentifier powinien być używany dla zewnętrznych odwołań do tokenu, z Właściwość ValueType atrybutu jako #X509SubjectKeyIdentifier i jego zawartości wartość algorytmem Base64 rozszerzenie SKI certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="124f5-273">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="124f5-274">Odwołania SKI powszechnie implementowanych i sprawdzone na typ wysokiej interoperacyjne odwołania zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="124f5-274">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="124f5-275">R1203 Odwołanie zewnętrzne do X509 zabezpieczeń tokenu nie powinien używać ds:X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="124f5-275">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="124f5-276">R1204 X509TokenProfile1.1 Jeśli jest używany, odwołanie zewnętrzne do X509 zabezpieczeń tokenów należy używać odcisk palca wprowadzone przez 1.1 WS-Security.</span><span class="sxs-lookup"><span data-stu-id="124f5-276">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="124f5-277">obsługuje X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="124f5-277"> supports X509IssuerSerial.</span></span> <span data-ttu-id="124f5-278">Istnieją jednak współdziałanie z X509IssuerSerial: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa ciągu do porównywania dwóch wartości X509IssuerSerial.</span><span class="sxs-lookup"><span data-stu-id="124f5-278">However There are interoperability issues with X509IssuerSerial: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="124f5-279">W związku z tym jeśli jedna zmienia kolejność składników nazwa podmiotu i wysyła do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi odwołanie do certyfikatu, nie można odnaleźć.</span><span class="sxs-lookup"><span data-stu-id="124f5-279">Therefore if one reorders components of the Subject Name and sends to an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="124f5-280">1.3 Token protokołu Kerberos</span><span class="sxs-lookup"><span data-stu-id="124f5-280">1.3 Kerberos Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="124f5-281">obsługuje KerberosTokenProfile1.1 na potrzeby uwierzytelniania systemu Windows z następującymi ograniczeniami:</span><span class="sxs-lookup"><span data-stu-id="124f5-281"> supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="124f5-282">R1301 A Kerberos tokenu musi zawierać wartość GSS opakowana AP_REQ v4 protokołu Kerberos, zgodnie z definicją w GSS_API i specyfikacja protokołu Kerberos, a musi mieć atrybut ValueType o wartości GSS_Kerberosv5_AP_REQ #.</span><span class="sxs-lookup"><span data-stu-id="124f5-282">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="124f5-283">używa GSS opakowana Kerberos uwierzytelniania Kerberos, nie systemu od zera region-REQ.</span><span class="sxs-lookup"><span data-stu-id="124f5-283"> uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="124f5-284">Jest to najlepsze rozwiązanie bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="124f5-284">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="124f5-285">1.4 SAML Token w wersji 1.1</span><span class="sxs-lookup"><span data-stu-id="124f5-285">1.4 SAML v1.1 Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="124f5-286">obsługuje profile tokenu SAML programu WSS 1.0 i 1.1 tokeny SAML w wersji 1.1.</span><span class="sxs-lookup"><span data-stu-id="124f5-286"> supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="124f5-287">Istnieje możliwość wykonania innych wersji formatów tokenu SAML.</span><span class="sxs-lookup"><span data-stu-id="124f5-287">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="124f5-288">W wersji 1.5 Token kontekstu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="124f5-288">1.5 Security Context Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="124f5-289">obsługuje zabezpieczenia kontekstu tokenu (SCT) wprowadzone w WS SecureCoversation.</span><span class="sxs-lookup"><span data-stu-id="124f5-289"> supports the Security Context Token (SCT) introduced in WS-SecureCoversation.</span></span> <span data-ttu-id="124f5-290">SCT jest używana do reprezentowania w kontekście zabezpieczeń określonych w SecureConversation również jako negocjacji binarnej protokoły TLS i SSPI, opisane poniżej.</span><span class="sxs-lookup"><span data-stu-id="124f5-290">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="124f5-291">2. Wspólne parametry zabezpieczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="124f5-291">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="124f5-292">2.1 Sygnatura czasowa</span><span class="sxs-lookup"><span data-stu-id="124f5-292">2.1 TimeStamp</span></span>  
 <span data-ttu-id="124f5-293">Obecności znacznika czasu jest kontrolowany przy użyciu <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> właściwość <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="124f5-293">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="124f5-294">zawsze serializuje wsse:TimeStamp z wsse: utworzyć i wsse: wygasa pól.</span><span class="sxs-lookup"><span data-stu-id="124f5-294"> always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="124f5-295">Wsse:TimeStamp są zawsze podpisane podczas podpisywania jest używany.</span><span class="sxs-lookup"><span data-stu-id="124f5-295">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="124f5-296">2.2 kolejność ochrony</span><span class="sxs-lookup"><span data-stu-id="124f5-296">2.2 Protection Order</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="124f5-297">obsługuje porządku ochrony wiadomości "Znak przed szyfrowania" i "Szyfrowania przed znak" (1.1 zasad zabezpieczeń).</span><span class="sxs-lookup"><span data-stu-id="124f5-297"> supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="124f5-298">"Zaloguj się przed Szyfruj" zaleca się powodów takich jak: komunikaty chronione przy użyciu szyfrowania przed logowania są otwarte na ataki podstawienia podpisu, chyba że jest używany mechanizm WS-Security 1.1 SignatureConfirmation i sprawia, że podpis za pośrednictwem zaszyfrowaną zawartość Inspekcja trudniej.</span><span class="sxs-lookup"><span data-stu-id="124f5-298">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="124f5-299">2.3 Podpis ochrony</span><span class="sxs-lookup"><span data-stu-id="124f5-299">2.3 Signature Protection</span></span>  
 <span data-ttu-id="124f5-300">Podczas szyfrowania przed znak jest używany, zalecane jest ochrona podpisu przed atakami ukierunkowany na odgadnięcie zaszyfrowaną zawartość lub klucza podpisywania (szczególnie, gdy token niestandardowy jest używany z słabe materiału klucza).</span><span class="sxs-lookup"><span data-stu-id="124f5-300">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="124f5-301">2.4 pakiet algorytmów</span><span class="sxs-lookup"><span data-stu-id="124f5-301">2.4 Algorithm Suite</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="124f5-302">obsługuje wszystkie pakiety algorytm 1.1 zasad zabezpieczeń na liście.</span><span class="sxs-lookup"><span data-stu-id="124f5-302"> supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="124f5-303">2.5 klucza pochodnego</span><span class="sxs-lookup"><span data-stu-id="124f5-303">2.5 Key Derivation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="124f5-304">używa "Klucza pochodnego dla kluczy symetrycznych", zgodnie z opisem w WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="124f5-304"> uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="124f5-305">2.6 potwierdzenie podpisu</span><span class="sxs-lookup"><span data-stu-id="124f5-305">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="124f5-306">Potwierdzenie podpisu może być jako ochronę przed atakami środkowej man chronić zbiór podpisów.</span><span class="sxs-lookup"><span data-stu-id="124f5-306">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="124f5-307">2.7 układ nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="124f5-307">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="124f5-308">Każdy tryb uwierzytelniania opisano niektóre układ nagłówka zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="124f5-308">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="124f5-309">Elementy w nagłówku zabezpieczeń są uporządkowane częściowo.</span><span class="sxs-lookup"><span data-stu-id="124f5-309">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="124f5-310">Aby zdefiniować kolejność elementów podrzędnych nagłówka zabezpieczeń, polityki WS-Security definiuje następujące tryby układ nagłówka zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="124f5-310">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="124f5-311">Ograniczeniami</span><span class="sxs-lookup"><span data-stu-id="124f5-311">Strict</span></span>|<span data-ttu-id="124f5-312">Elementy są dodawane do następującego nagłówka zabezpieczeń się, że reguły numerowane układu opisanego w zasady zabezpieczeń sekcji 7.7.1 zgodnie z ogólną zasadą "deklaruje przed użyciem".</span><span class="sxs-lookup"><span data-stu-id="124f5-312">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="124f5-313">Swobodny</span><span class="sxs-lookup"><span data-stu-id="124f5-313">Lax</span></span>|<span data-ttu-id="124f5-314">Elementy są dodawane do nagłówka zabezpieczeń w dowolnej kolejności, która odpowiada programu WSS: zabezpieczenia wiadomości protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="124f5-314">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="124f5-315">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="124f5-315">LaxTimestampFirst</span></span>|<span data-ttu-id="124f5-316">Tym samym Lax z tą różnicą, że pierwszy element w nagłówku zabezpieczeń muszą być wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="124f5-316">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="124f5-317">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="124f5-317">LaxTimestampLast</span></span>|<span data-ttu-id="124f5-318">Identyczny swobodny z tą różnicą, że ostatni element w nagłówku zabezpieczeń muszą być wsse:Timestamp</span><span class="sxs-lookup"><span data-stu-id="124f5-318">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="124f5-319">obsługuje wszystkie cztery tryby układzie nagłówka zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="124f5-319"> supports all four modes for security header layout.</span></span> <span data-ttu-id="124f5-320">Zabezpieczenia nagłówka struktury i komunikat dla tryby uwierzytelniania poniżej przykładów trybu "Strict".</span><span class="sxs-lookup"><span data-stu-id="124f5-320">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="124f5-321">2. Wspólne parametry zabezpieczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="124f5-321">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="124f5-322">Ta sekcja zawiera przykładowe zasady dla każdego trybu uwierzytelniania wraz z przykładami przedstawiający Struktura nagłówka zabezpieczeń w wiadomości wymieniane przez klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="124f5-322">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="124f5-323">6.1 ochrony transportu</span><span class="sxs-lookup"><span data-stu-id="124f5-323">6.1 Transport Protection</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="124f5-324">zawiera pięć tryby uwierzytelniania, korzystających z bezpiecznego transportu do ochrony wiadomości. UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport i SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="124f5-324"> provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="124f5-325">Te tryby uwierzytelniania są konstruowane przy użyciu opisanego w SecurityPolicy powiązania transportu.</span><span class="sxs-lookup"><span data-stu-id="124f5-325">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="124f5-326">W przypadku UserNameOverTransport tryb uwierzytelniania UsernameToken jest podpisany token pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="124f5-326">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="124f5-327">W trybach uwierzytelniania tokenu jest wyświetlany jako podpisany token zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="124f5-327">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="124f5-328">Dodatek C.1.2 i C.1.3 SecurityPolicy opisują szczegółowo układ nagłówka zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="124f5-328">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="124f5-329">Następujące nagłówki zabezpieczeń przykład Pokaż Strict układu dla trybu danego uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="124f5-329">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="124f5-330">Wartość właściwości "Kluczy pochodnych" tokenów we wszystkich przypadkach jest "false".</span><span class="sxs-lookup"><span data-stu-id="124f5-330">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="124f5-331">Wartości różnych właściwości powiązania transportu są następujące:</span><span class="sxs-lookup"><span data-stu-id="124f5-331">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="124f5-332">Sygnatura czasowa: true</span><span class="sxs-lookup"><span data-stu-id="124f5-332">Timestamp: true</span></span>  
  
 <span data-ttu-id="124f5-333">Układ nagłówka zabezpieczeń: Strict</span><span class="sxs-lookup"><span data-stu-id="124f5-333">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="124f5-334">Pakiet algorytmów: Basic256</span><span class="sxs-lookup"><span data-stu-id="124f5-334">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="124f5-335">6.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="124f5-335">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="124f5-336">Z tego trybu uwierzytelniania klienta jest uwierzytelniany w usłudze Token nazwy użytkownika, który znajduje się na warstwie SOAP jako podpisanego tokenu pomocniczego zawsze wysyłany z inicjatora do adresata.</span><span class="sxs-lookup"><span data-stu-id="124f5-336">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="124f5-337">Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="124f5-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="124f5-338">Wiązanie używane jest powiązania transportu.</span><span class="sxs-lookup"><span data-stu-id="124f5-338">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="124f5-339">Zasady</span><span class="sxs-lookup"><span data-stu-id="124f5-339">Policy</span></span>  
  
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
  
 <span data-ttu-id="124f5-340">Układ nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="124f5-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="124f5-341">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-341">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-342">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="124f5-343">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="124f5-343">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="124f5-344">Z tego trybu uwierzytelniania, który uwierzytelnia klienta za pomocą X.509 certyfikatów, która jest wyświetlana w warstwie protokołu SOAP jako tokenu pomocniczego zawsze wysyłany z inicjatora do adresata.</span><span class="sxs-lookup"><span data-stu-id="124f5-344">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="124f5-345">Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="124f5-345">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="124f5-346">Wiązanie używane jest powiązania transportu.</span><span class="sxs-lookup"><span data-stu-id="124f5-346">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="124f5-347">Zasady</span><span class="sxs-lookup"><span data-stu-id="124f5-347">Policy</span></span>  
  
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
  
 <span data-ttu-id="124f5-348">Układ nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="124f5-348">Security Header Layout</span></span>  
  
 <span data-ttu-id="124f5-349">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-349">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-350">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-350">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="124f5-351">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="124f5-351">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="124f5-352">W ten tryb uwierzytelniania klienta nie uwierzytelniania w usłudze, w związku, ale raczej wyświetlany token wystawiony przez zabezpieczenia tokenu usługi (STS) oraz okaże się wiedzę na temat klucza wspólnego.</span><span class="sxs-lookup"><span data-stu-id="124f5-352">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="124f5-353">Wystawiony token jest wyświetlany w warstwie protokołu SOAP jako tokenu pomocniczego zawsze wysyłany z inicjatora do adresata.</span><span class="sxs-lookup"><span data-stu-id="124f5-353">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="124f5-354">Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="124f5-354">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="124f5-355">Powiązanie jest powiązania transportu.</span><span class="sxs-lookup"><span data-stu-id="124f5-355">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="124f5-356">Zasady</span><span class="sxs-lookup"><span data-stu-id="124f5-356">Policy</span></span>  
  
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
  
 <span data-ttu-id="124f5-357">Układ nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="124f5-357">Security Header Layout</span></span>  
  
 <span data-ttu-id="124f5-358">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-358">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-359">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-359">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="124f5-360">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="124f5-360">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="124f5-361">Z tego trybu uwierzytelniania klient przeprowadza uwierzytelnianie usługi przy użyciu biletu protokołu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="124f5-361">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="124f5-362">Token protokołu Kerberos jest wyświetlany w warstwie protokołu SOAP jako tokenu pomocniczego.</span><span class="sxs-lookup"><span data-stu-id="124f5-362">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="124f5-363">Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="124f5-363">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="124f5-364">Powiązanie jest powiązania transportu.</span><span class="sxs-lookup"><span data-stu-id="124f5-364">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="124f5-365">Zasady</span><span class="sxs-lookup"><span data-stu-id="124f5-365">Policy</span></span>  
  
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
  
 <span data-ttu-id="124f5-366">Układ nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="124f5-366">Security Header Layout</span></span>  
  
 <span data-ttu-id="124f5-367">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-367">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-368">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-368">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="124f5-369">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="124f5-369">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="124f5-370">W tym trybie protokół negocjacji służy do uwierzytelniania klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="124f5-370">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="124f5-371">Protokół Kerberos jest używany, jeśli to możliwe, w przeciwnym razie NTLM.</span><span class="sxs-lookup"><span data-stu-id="124f5-371">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="124f5-372">Wynikowa SCT pojawia się w warstwie protokołu SOAP jako tokenu pomocniczego zawsze wysyłany z inicjatora do adresata.</span><span class="sxs-lookup"><span data-stu-id="124f5-372">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="124f5-373">Usługa Ponadto jest uwierzytelniany w przypadku warstwy transportu za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="124f5-373">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="124f5-374">Wiązanie używane jest powiązania transportu.</span><span class="sxs-lookup"><span data-stu-id="124f5-374">The binding used is a transport binding.</span></span> <span data-ttu-id="124f5-375">W tym artykule opisano "SPNEGO" (negocjacji) jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wykorzystuje protokół negocjacji binarnej SSPI z protokołu WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="124f5-375">"SPNEGO" (negotiation) describes how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="124f5-376">Przykłady nagłówka zabezpieczeń w tej sekcji są po nawiązaniu SCT za pośrednictwem uzgadnianie SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="124f5-376">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="124f5-377">Zasady</span><span class="sxs-lookup"><span data-stu-id="124f5-377">Policy</span></span>  
  
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
  
### <a name="security-header-examples"></a><span data-ttu-id="124f5-378">Przykłady nagłówka zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="124f5-378">Security Header Examples</span></span>  
 <span data-ttu-id="124f5-379">Po Token kontekstu zabezpieczeń za pomocą uzgadniania SPNEGO przy użyciu protokołu WS-Trust negocjacji binarnej komunikatów aplikacji ma nagłówki zabezpieczeń o następującej strukturze.</span><span class="sxs-lookup"><span data-stu-id="124f5-379">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="124f5-380">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-380">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-381">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-381">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="124f5-382">6.2 za pomocą certyfikatów X.509 do usługi uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="124f5-382">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="124f5-383">W tej sekcji opisano następujące tryby uwierzytelniania: MutualCertificate WSS1.0, wzajemne CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate i IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="124f5-383">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="124f5-384">6.2.1 MutualCertificate WSS1.0</span><span class="sxs-lookup"><span data-stu-id="124f5-384">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="124f5-385">Z tego trybu uwierzytelniania, który uwierzytelnia klienta za pomocą X.509 certyfikatów, która jest wyświetlana w warstwie protokołu SOAP jako token inicjatora.</span><span class="sxs-lookup"><span data-stu-id="124f5-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="124f5-386">Usługa jest również uwierzytelniony za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="124f5-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="124f5-387">Wiązanie używane jest powiązanie asymetrycznego z następujących wartości właściwości:</span><span class="sxs-lookup"><span data-stu-id="124f5-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="124f5-388">Token inicjatora: certyfikat X.509 klienta, z ustawioną .../IncludeToken/AlwaysToRecipient tryb dołączania</span><span class="sxs-lookup"><span data-stu-id="124f5-388">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="124f5-389">Odbiorcy tokenu: Serwer do certyfikatu X.509, włączenia trybu ustawiono .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="124f5-389">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="124f5-390">Token ochrony: False</span><span class="sxs-lookup"><span data-stu-id="124f5-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="124f5-391">Cały nagłówek i podpisy treści: True</span><span class="sxs-lookup"><span data-stu-id="124f5-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="124f5-392">Kolejność Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="124f5-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="124f5-393">Szyfrowanie podpisów: True</span><span class="sxs-lookup"><span data-stu-id="124f5-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="124f5-394">Zasady</span><span class="sxs-lookup"><span data-stu-id="124f5-394">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="124f5-395">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="124f5-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="124f5-396">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-396">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-397">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-397">Response</span></span>  
  
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
  
 <span data-ttu-id="124f5-398">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="124f5-398">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="124f5-399">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-399">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-400">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-400">Response</span></span>  
  
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
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="124f5-401">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="124f5-401">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="124f5-402">Z tego trybu uwierzytelniania, który uwierzytelnia klienta za pomocą X.509 certyfikatów, która jest wyświetlana w warstwie protokołu SOAP jako token inicjatora.</span><span class="sxs-lookup"><span data-stu-id="124f5-402">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="124f5-403">Usługa jest również uwierzytelniony za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="124f5-403">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="124f5-404">Wiązanie używane jest powiązanie asymetrycznego z następujących wartości właściwości:</span><span class="sxs-lookup"><span data-stu-id="124f5-404">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="124f5-405">Token inicjatora: X509 klienta certyfikatu, tryb dołączania jest ustawiony na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="124f5-405">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="124f5-406">Odbiorcy tokenu: X509 serwera certyfikatów, tryb dołączania jest ustawiony na .../IncludeToken/AlwaysToInitiator</span><span class="sxs-lookup"><span data-stu-id="124f5-406">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="124f5-407">Token ochrony: False</span><span class="sxs-lookup"><span data-stu-id="124f5-407">Token Protection: False</span></span>  
  
 <span data-ttu-id="124f5-408">Cały nagłówek i podpisy treści: True</span><span class="sxs-lookup"><span data-stu-id="124f5-408">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="124f5-409">Kolejność Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="124f5-409">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="124f5-410">Szyfrowanie podpisów: True</span><span class="sxs-lookup"><span data-stu-id="124f5-410">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="124f5-411">Zasady</span><span class="sxs-lookup"><span data-stu-id="124f5-411">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="124f5-412">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="124f5-412">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="124f5-413">Żądanie i odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-413">Request and Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="124f5-414">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="124f5-414">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="124f5-415">Żądanie i odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-415">Request and Response</span></span>  
  
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
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="124f5-416">6.2.3 przy użyciu SymmetricBinding X.509 usługi uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="124f5-416">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="124f5-417">"WSS10" przewidzianych ograniczoną obsługę scenariuszy z X509 tokenów.</span><span class="sxs-lookup"><span data-stu-id="124f5-417">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="124f5-418">Na przykład nie było możliwości wykonania w celu zapewnienia ochrony podpis i szyfrowanie wiadomości za pomocą tylko usługi X509 tokenu.</span><span class="sxs-lookup"><span data-stu-id="124f5-418">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="124f5-419">"WSS11" wprowadzono użycie EncryptedKey jako tokenu symetrycznego.</span><span class="sxs-lookup"><span data-stu-id="124f5-419">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="124f5-420">Teraz tymczasowego klucza zaszyfrowanego dla certyfikatu X.509 usługi można użyć do ochrony wiadomości zarówno żądań i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="124f5-420">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="124f5-421">Tryby uwierzytelniania opisanego w sekcji 6.4 poniżej użycia tego wzorca.</span><span class="sxs-lookup"><span data-stu-id="124f5-421">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="124f5-422">WS-SecurityPolicy opisuje tego wzorca z usługą za pomocą SymmetricBinding X509 token jako token ochrony.</span><span class="sxs-lookup"><span data-stu-id="124f5-422">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="124f5-423">Tryby uwierzytelniania AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 i IssuedTokenForCertificate wszystkich za pomocą podobnego wystąpienia sp:SymmetricBinding wartości następujących właściwości:</span><span class="sxs-lookup"><span data-stu-id="124f5-423">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="124f5-424">Token ochrony: X509 serwera certyfikatów, tryb dołączania jest ustawiony na .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="124f5-424">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="124f5-425">Token ochrony: False</span><span class="sxs-lookup"><span data-stu-id="124f5-425">Token Protection: False</span></span>  
  
 <span data-ttu-id="124f5-426">Cały nagłówek i podpisy treści: True</span><span class="sxs-lookup"><span data-stu-id="124f5-426">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="124f5-427">Kolejność Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="124f5-427">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="124f5-428">Szyfrowanie podpisów: True</span><span class="sxs-lookup"><span data-stu-id="124f5-428">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="124f5-429">Powyżej tryby uwierzytelniania różnią się tylko przez pomocnicze tokeny, których używają.</span><span class="sxs-lookup"><span data-stu-id="124f5-429">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="124f5-430">AnonymousForCertificate nie ma żadnych tokenów pomocniczych, MutualCertificate WSS 1.1 ma klienta X509 certyfikatów jako wprowadzająca tokenami pomocniczymi, UserNameForCertificate ma Token nazwy użytkownika jako podpisanego tokenu pomocniczego i IssuedTokenForCertificate został wystawiony token jako tokenu pomocniczego.</span><span class="sxs-lookup"><span data-stu-id="124f5-430">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="124f5-431">Zasady</span><span class="sxs-lookup"><span data-stu-id="124f5-431">Policy</span></span>  
  
 <span data-ttu-id="124f5-432">Powiązanie symetryczne</span><span class="sxs-lookup"><span data-stu-id="124f5-432">Symmetric Binding</span></span>  
  
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
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="124f5-433">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="124f5-433">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="124f5-434">Z tego trybu uwierzytelniania anonimowego jest klient i Usługa uwierzytelniania za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="124f5-434">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="124f5-435">Wiązanie używane jest wystąpieniem symetrycznego powiązanie, zgodnie z opisem w 6.4.2.</span><span class="sxs-lookup"><span data-stu-id="124f5-435">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="124f5-436">Zasady</span><span class="sxs-lookup"><span data-stu-id="124f5-436">Policy</span></span>  
  
 <span data-ttu-id="124f5-437">Zobacz "Policy" w 6.2.3 powyżej dla powiązania szczegóły</span><span class="sxs-lookup"><span data-stu-id="124f5-437">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="124f5-438">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="124f5-438">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="124f5-439">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-439">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-440">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-440">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="124f5-441">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="124f5-441">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="124f5-442">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-442">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-443">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-443">Response</span></span>  
  
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
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="124f5-444">6.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="124f5-444">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="124f5-445">Z tego trybu uwierzytelniania klient przeprowadza uwierzytelnianie usługi przy użyciu Token nazwy użytkownika, który jest wyświetlany w warstwie protokołu SOAP jako podpisanego tokenu pomocniczego.</span><span class="sxs-lookup"><span data-stu-id="124f5-445">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="124f5-446">Usługa uwierzytelnia klienta, za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="124f5-446">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="124f5-447">Wiązanie używane jest symetrycznego powiązania z tokenem ochrony klucza wygenerowanych przez klienta, szyfrowany za pomocą klucza publicznego usługi trwa.</span><span class="sxs-lookup"><span data-stu-id="124f5-447">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="124f5-448">Zasady</span><span class="sxs-lookup"><span data-stu-id="124f5-448">Policy</span></span>  
  
 <span data-ttu-id="124f5-449">Zobacz "Policy" w 6.2.3 powyżej dla powiązania szczegóły</span><span class="sxs-lookup"><span data-stu-id="124f5-449">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="124f5-450">Podpisany Token pomocniczy</span><span class="sxs-lookup"><span data-stu-id="124f5-450">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="124f5-451">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="124f5-451">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="124f5-452">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-452">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-453">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-453">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="124f5-454">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="124f5-454">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="124f5-455">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-455">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-456">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-456">Response</span></span>  
  
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
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="124f5-457">6.2.6 MutualCertificate (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="124f5-457">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="124f5-458">Z tego trybu uwierzytelniania, który uwierzytelnia klienta za pomocą X.509 certyfikatów, która jest wyświetlana w warstwie protokołu SOAP jako tokenu pomocniczego.</span><span class="sxs-lookup"><span data-stu-id="124f5-458">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="124f5-459">Usługa jest również uwierzytelniony za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="124f5-459">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="124f5-460">Wiązanie używane jest symetrycznego powiązania z tokenem ochrony klucza wygenerowanych przez klienta, szyfrowany za pomocą klucza publicznego usługi trwa.</span><span class="sxs-lookup"><span data-stu-id="124f5-460">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="124f5-461">Zasady</span><span class="sxs-lookup"><span data-stu-id="124f5-461">Policy</span></span>  
  
 <span data-ttu-id="124f5-462">Zobacz zasady w 6.2.3 dla powiązania szczegóły</span><span class="sxs-lookup"><span data-stu-id="124f5-462">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="124f5-463">Wprowadzająca Obsługa tokenu</span><span class="sxs-lookup"><span data-stu-id="124f5-463">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="124f5-464">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="124f5-464">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="124f5-465">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-465">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-466">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-466">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="124f5-467">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="124f5-467">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="124f5-468">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-468">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-469">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-469">Response</span></span>  
  
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
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="124f5-470">6.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="124f5-470">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="124f5-471">To uwierzytelnianie trybu tak, ale zamiast tego klient nie uwierzytelniania w usłudze przedstawia token wystawiony przez usługę STS i okaże się wiedzę na temat klucza wspólnego.</span><span class="sxs-lookup"><span data-stu-id="124f5-471">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="124f5-472">Wystawiony token jest wyświetlany w warstwie protokołu SOAP jako tokenu pomocniczego.</span><span class="sxs-lookup"><span data-stu-id="124f5-472">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="124f5-473">Usługa uwierzytelnia klienta, za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="124f5-473">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="124f5-474">Wiązanie używane jest symetrycznego powiązania z tokenem ochrony klucza wygenerowanych przez klienta, szyfrowany za pomocą klucza publicznego usługi trwa.</span><span class="sxs-lookup"><span data-stu-id="124f5-474">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="124f5-475">Zasady</span><span class="sxs-lookup"><span data-stu-id="124f5-475">Policy</span></span>  
  
 <span data-ttu-id="124f5-476">Zobacz zasady w 6.2.3 powyżej szczegółowe powiązania</span><span class="sxs-lookup"><span data-stu-id="124f5-476">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="124f5-477">Wprowadzająca Obsługa tokenu</span><span class="sxs-lookup"><span data-stu-id="124f5-477">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="124f5-478">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="124f5-478">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="124f5-479">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-479">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-480">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-480">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="124f5-481">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="124f5-481">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="124f5-482">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-482">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-483">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-483">Response</span></span>  
  
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
  
## <a name="63-kerberos"></a><span data-ttu-id="124f5-484">6.3 protokołu Kerberos</span><span class="sxs-lookup"><span data-stu-id="124f5-484">6.3 Kerberos</span></span>  
 <span data-ttu-id="124f5-485">Z tego trybu uwierzytelniania klient przeprowadza uwierzytelnianie usługi przy użyciu biletu protokołu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="124f5-485">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="124f5-486">Korzystając z tego samego biletu także uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="124f5-486">That same ticket also provides server authentication.</span></span> <span data-ttu-id="124f5-487">Wiązanie używane jest symetrycznego powiązania z następującymi właściwościami;</span><span class="sxs-lookup"><span data-stu-id="124f5-487">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="124f5-488">Token ochrony: Biletu Kerberos, tryb dołączania ustawiono .../IncludeToken/Once</span><span class="sxs-lookup"><span data-stu-id="124f5-488">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="124f5-489">Token ochrony: False</span><span class="sxs-lookup"><span data-stu-id="124f5-489">Token Protection: False</span></span>  
  
 <span data-ttu-id="124f5-490">Cały nagłówek i podpisy treści: True</span><span class="sxs-lookup"><span data-stu-id="124f5-490">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="124f5-491">Kolejność Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="124f5-491">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="124f5-492">Szyfrowanie podpisów: True</span><span class="sxs-lookup"><span data-stu-id="124f5-492">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="124f5-493">Zasady</span><span class="sxs-lookup"><span data-stu-id="124f5-493">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="124f5-494">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="124f5-494">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="124f5-495">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-495">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-496">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-496">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="124f5-497">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="124f5-497">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="124f5-498">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-498">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="124f5-499">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-499">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="124f5-500">6.4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="124f5-500">6.4 IssuedToken</span></span>  
 <span data-ttu-id="124f5-501">W ten tryb uwierzytelniania, które klient nie uwierzytelniania w usłudze, zamiast klienta wyświetlany token wystawiony przez usługę STS oraz okaże się wiedzę na temat klucza wspólnego.</span><span class="sxs-lookup"><span data-stu-id="124f5-501">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="124f5-502">Usługa nie jest uwierzytelniony do klienta tak, zamiast niego usługi STS szyfruje klucz udostępniony jako część wystawionego tokenu tak, aby tylko usługa może odszyfrować klucza.</span><span class="sxs-lookup"><span data-stu-id="124f5-502">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="124f5-503">Wiązanie używane jest jako symetrycznego powiązania z następującymi właściwościami;</span><span class="sxs-lookup"><span data-stu-id="124f5-503">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="124f5-504">Token ochrony: Wystawiony Token, tryb dołączania jest ustawiony na .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="124f5-504">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="124f5-505">Token ochrony: False</span><span class="sxs-lookup"><span data-stu-id="124f5-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="124f5-506">Cały nagłówek i podpisy treści: True</span><span class="sxs-lookup"><span data-stu-id="124f5-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="124f5-507">Kolejność Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="124f5-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="124f5-508">Szyfrowanie podpisów: True</span><span class="sxs-lookup"><span data-stu-id="124f5-508">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="124f5-509">Zasady</span><span class="sxs-lookup"><span data-stu-id="124f5-509">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="124f5-510">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="124f5-510">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="124f5-511">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-511">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-512">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-512">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="124f5-513">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="124f5-513">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="124f5-514">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-514">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-515">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-515">Response</span></span>  
  
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
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="124f5-516">6.5 przy użyciu SslNegotiated dla usługi uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="124f5-516">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="124f5-517">W tej sekcji opisano grupę tryby uwierzytelniania, które symetrycznego powiązania za pomocą tokenu ochrony jest kontekst tokenu zabezpieczeń na WS-SecureConversation (WS-SC), wykonując protokół TLS za pośrednictwem protokołu WS-Trust (WS-T) RST negocjowane jest którego wartość klucza / Odpowiedź RSTR wiadomości.</span><span class="sxs-lookup"><span data-stu-id="124f5-517">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="124f5-518">Szczegóły implementacji uzgadniania TLS za pomocą protokołu WS-Trust są opisane w TLSNEGO.</span><span class="sxs-lookup"><span data-stu-id="124f5-518">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="124f5-519">W tym miejscu w przykładach komunikat możemy przyjmie założenie, że SCT z kontekstem zabezpieczeń skojarzony jest już ustalone przez uzgadniania.</span><span class="sxs-lookup"><span data-stu-id="124f5-519">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="124f5-520">Wiązanie używane jest symetrycznego powiązania z następującymi właściwościami;</span><span class="sxs-lookup"><span data-stu-id="124f5-520">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="124f5-521">Token ochrony: SslContextToken, tryb dołączania ustawiono .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="124f5-521">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="124f5-522">Token ochrony: False</span><span class="sxs-lookup"><span data-stu-id="124f5-522">Token Protection: False</span></span>  
  
 <span data-ttu-id="124f5-523">Cały nagłówek i podpisy treści: True</span><span class="sxs-lookup"><span data-stu-id="124f5-523">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="124f5-524">Kolejność Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="124f5-524">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="124f5-525">Szyfrowanie podpisów: True</span><span class="sxs-lookup"><span data-stu-id="124f5-525">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="124f5-526">6.5.1 zasady SslNegotiated usługi uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="124f5-526">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="124f5-527">Zasady dla wszystkich metod uwierzytelniania w tej sekcji są podobne i różnią się tylko przez określonych podpisanych obsługi lub potwierdzania tokenów używanych.</span><span class="sxs-lookup"><span data-stu-id="124f5-527">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
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
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="124f5-528">6.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="124f5-528">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="124f5-529">Z tego trybu uwierzytelniania anonimowego jest klient i Usługa uwierzytelniania za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="124f5-529">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="124f5-530">Wiązanie używane jest wystąpieniem symetrycznego powiązanie, zgodnie z opisem w powyższej 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="124f5-530">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="124f5-531">Zasady</span><span class="sxs-lookup"><span data-stu-id="124f5-531">Policy</span></span>  
  
 <span data-ttu-id="124f5-532">Zobacz zasady w 6.5.1 powyżej szczegółowe powiązania.</span><span class="sxs-lookup"><span data-stu-id="124f5-532">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="124f5-533">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="124f5-533">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="124f5-534">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-534">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-535">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-535">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="124f5-536">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="124f5-536">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="124f5-537">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-537">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-538">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-538">Response</span></span>  
  
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
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="124f5-539">6.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="124f5-539">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="124f5-540">Z tego uwierzytelnienia jest tryb, który klient jest uwierzytelniany przy użyciu Token nazwy użytkownika, który jest wyświetlany w warstwie protokołu SOAP jako podpisanego tokenu pomocniczego.</span><span class="sxs-lookup"><span data-stu-id="124f5-540">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="124f5-541">Usługa jest uwierzytelniany przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="124f5-541">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="124f5-542">Wiązanie używane jest wystąpieniem symetrycznego powiązanie, zgodnie z opisem w 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="124f5-542">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="124f5-543">Zasady</span><span class="sxs-lookup"><span data-stu-id="124f5-543">Policy</span></span>  
  
 <span data-ttu-id="124f5-544">W sekcji 6.5.1 powyżej powiązanie szczegóły</span><span class="sxs-lookup"><span data-stu-id="124f5-544">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="124f5-545">Podpisany Token pomocniczy</span><span class="sxs-lookup"><span data-stu-id="124f5-545">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="124f5-546">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="124f5-546">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="124f5-547">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-547">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-548">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-548">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="124f5-549">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="124f5-549">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="124f5-550">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-550">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-551">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-551">Response</span></span>  
  
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
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="124f5-552">6.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="124f5-552">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="124f5-553">To uwierzytelnianie trybu tak, ale zamiast tego klient nie uwierzytelniania w usłudze przedstawia token wystawiony przez usługę STS i okaże się wiedzę na temat klucza wspólnego.</span><span class="sxs-lookup"><span data-stu-id="124f5-553">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="124f5-554">Wystawiony token jest wyświetlany w warstwie protokołu SOAP jako tokenu pomocniczego.</span><span class="sxs-lookup"><span data-stu-id="124f5-554">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="124f5-555">Usługa jest uwierzytelniany przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="124f5-555">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="124f5-556">Wiązanie używane jest wystąpieniem symetrycznego powiązanie, zgodnie z opisem w powyższej 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="124f5-556">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="124f5-557">Zasady</span><span class="sxs-lookup"><span data-stu-id="124f5-557">Policy</span></span>  
  
 <span data-ttu-id="124f5-558">W sekcji 6.5.1 powyżej powiązanie szczegóły</span><span class="sxs-lookup"><span data-stu-id="124f5-558">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="124f5-559">Wprowadzająca Obsługa tokenu</span><span class="sxs-lookup"><span data-stu-id="124f5-559">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="124f5-560">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="124f5-560">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="124f5-561">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-561">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-562">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-562">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="124f5-563">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="124f5-563">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="124f5-564">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-564">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-565">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-565">Response</span></span>  
  
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
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="124f5-566">6.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="124f5-566">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="124f5-567">Z tego trybu uwierzytelniania klient i Usługa uwierzytelniania za pomocą certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="124f5-567">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="124f5-568">Wiązanie używane jest wystąpieniem symetrycznego powiązanie, zgodnie z opisem w powyższej 6.5.1.</span><span class="sxs-lookup"><span data-stu-id="124f5-568">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="124f5-569">Zasady</span><span class="sxs-lookup"><span data-stu-id="124f5-569">Policy</span></span>  
  
 <span data-ttu-id="124f5-570">W sekcji 6.5.1 powyżej powiązanie szczegóły</span><span class="sxs-lookup"><span data-stu-id="124f5-570">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="124f5-571">Wprowadzająca Obsługa tokenu</span><span class="sxs-lookup"><span data-stu-id="124f5-571">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="124f5-572">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="124f5-572">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="124f5-573">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-573">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-574">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-574">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="124f5-575">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="124f5-575">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="124f5-576">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-576">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-577">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-577">Response</span></span>  
  
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
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="124f5-578">6.6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="124f5-578">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="124f5-579">Z tego trybu uwierzytelniania protokół negocjacji służy do uwierzytelniania klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="124f5-579">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="124f5-580">Protokół Kerberos jest używany, jeśli to możliwe, w przeciwnym razie NTLM.</span><span class="sxs-lookup"><span data-stu-id="124f5-580">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="124f5-581">Wiązanie używane jest symetrycznego powiązania z następującymi właściwościami;</span><span class="sxs-lookup"><span data-stu-id="124f5-581">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="124f5-582">Token ochrony: SpnegoContextToken, tryb dołączania ustawiono .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="124f5-582">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="124f5-583">Token ochrony: False</span><span class="sxs-lookup"><span data-stu-id="124f5-583">Token Protection: False</span></span>  
  
 <span data-ttu-id="124f5-584">Cały nagłówek i podpisy treści: True</span><span class="sxs-lookup"><span data-stu-id="124f5-584">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="124f5-585">Kolejność Protection: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="124f5-585">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="124f5-586">Szyfrowanie podpisów: True</span><span class="sxs-lookup"><span data-stu-id="124f5-586">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="124f5-587">Zasady</span><span class="sxs-lookup"><span data-stu-id="124f5-587">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="124f5-588">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="124f5-588">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="124f5-589">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-589">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-590">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-590">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="124f5-591">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="124f5-591">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="124f5-592">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-592">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-593">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-593">Response</span></span>  
  
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
  
### <a name="67-secureconversation"></a><span data-ttu-id="124f5-594">6.7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="124f5-594">6.7 SecureConversation</span></span>  
 <span data-ttu-id="124f5-595">Wiązanie używane jest symetrycznego powiązania z tokenem ochrony trwa SCT na WS-SecureConversation (WS-SC).</span><span class="sxs-lookup"><span data-stu-id="124f5-595">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="124f5-596">SCT negocjowane jest za pomocą protokołu WS-Trust (WS-Trust) lub protokołu WS-SecureConversation (WS-SC) zgodnie z zagnieżdżonych powiązania, który sam jest powiązanie symetrycznego, które wykorzystuje protokół negocjacji.</span><span class="sxs-lookup"><span data-stu-id="124f5-596">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="124f5-597">Protokół negocjacji będzie korzystać z protokołu Kerberos do uwierzytelniania klienta i serwera, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="124f5-597">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="124f5-598">Jeśli nie można użyć protokołu Kerberos, jego powróci do uwierzytelniania NTLM.</span><span class="sxs-lookup"><span data-stu-id="124f5-598">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="124f5-599">Zasady</span><span class="sxs-lookup"><span data-stu-id="124f5-599">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="124f5-600">Przykłady nagłówka zabezpieczeń: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="124f5-600">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="124f5-601">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-601">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-602">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-602">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="124f5-603">Przykłady nagłówka zabezpieczeń: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="124f5-603">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="124f5-604">Żądanie</span><span class="sxs-lookup"><span data-stu-id="124f5-604">Request</span></span>  
  
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
  
 <span data-ttu-id="124f5-605">Odpowiedź</span><span class="sxs-lookup"><span data-stu-id="124f5-605">Response</span></span>  
  
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
