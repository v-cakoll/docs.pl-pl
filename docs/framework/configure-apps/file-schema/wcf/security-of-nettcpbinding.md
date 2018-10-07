---
title: '&lt;security&gt; w &lt;netTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
author: BrucePerlerMS
ms.openlocfilehash: 8db4fd0a123ac798cae803240b0db98a7057fa97
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48840123"
---
# <a name="ltsecuritygt-of-ltnettcpbindinggt"></a><span data-ttu-id="db9bc-102">&lt;security&gt; w &lt;netTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="db9bc-102">&lt;security&gt; of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="db9bc-103">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="db9bc-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="db9bc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="db9bc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="db9bc-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="db9bc-105">\<bindings></span></span>  
<span data-ttu-id="db9bc-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="db9bc-106">\<netTcpBinding></span></span>  
<span data-ttu-id="db9bc-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="db9bc-107">\<binding></span></span>  
<span data-ttu-id="db9bc-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="db9bc-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db9bc-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="db9bc-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
           protectionLevel="None/Sign/EncryptAndSign" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db9bc-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="db9bc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="db9bc-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="db9bc-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db9bc-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="db9bc-112">Attributes</span></span>  
  
|<span data-ttu-id="db9bc-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="db9bc-113">Attribute</span></span>|<span data-ttu-id="db9bc-114">Opis</span><span class="sxs-lookup"><span data-stu-id="db9bc-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db9bc-115">tryb</span><span class="sxs-lookup"><span data-stu-id="db9bc-115">mode</span></span>|<span data-ttu-id="db9bc-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="db9bc-116">Optional.</span></span> <span data-ttu-id="db9bc-117">Określa typ zabezpieczeń, która jest stosowana.</span><span class="sxs-lookup"><span data-stu-id="db9bc-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="db9bc-118">Poniżej przedstawiono prawidłowe wartości.</span><span class="sxs-lookup"><span data-stu-id="db9bc-118">Valid values are shown below.</span></span> <span data-ttu-id="db9bc-119">Wartość domyślna to `Transport`.</span><span class="sxs-lookup"><span data-stu-id="db9bc-119">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="db9bc-120">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="db9bc-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="db9bc-121">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="db9bc-121">mode Attribute</span></span>  
  
|<span data-ttu-id="db9bc-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="db9bc-122">Value</span></span>|<span data-ttu-id="db9bc-123">Opis</span><span class="sxs-lookup"><span data-stu-id="db9bc-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="db9bc-124">Brak</span><span class="sxs-lookup"><span data-stu-id="db9bc-124">None</span></span>|<span data-ttu-id="db9bc-125">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="db9bc-125">Security is disabled.</span></span>|  
|<span data-ttu-id="db9bc-126">Transportu</span><span class="sxs-lookup"><span data-stu-id="db9bc-126">Transport</span></span>|<span data-ttu-id="db9bc-127">Zabezpieczenia transportu znajduje się za pośrednictwem protokołu TCP lub SPNego przy użyciu protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="db9bc-127">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="db9bc-128">Usługa może być konieczne można skonfigurować za pomocą certyfikatów SSL.</span><span class="sxs-lookup"><span data-stu-id="db9bc-128">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="db9bc-129">Istnieje możliwość kontrolować poziom ochrony w tym trybie.</span><span class="sxs-lookup"><span data-stu-id="db9bc-129">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="db9bc-130">Komunikat</span><span class="sxs-lookup"><span data-stu-id="db9bc-130">Message</span></span>|<span data-ttu-id="db9bc-131">Zabezpieczenia korzystanie z zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="db9bc-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="db9bc-132">Domyślnie treści protokołu SOAP jest zaszyfrowany i podpisany.</span><span class="sxs-lookup"><span data-stu-id="db9bc-132">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="db9bc-133">Ten tryb zapewnia szeroką gamę funkcji, takich jak tego, czy poświadczenia usługi są dostępne pod adresem klientem poza pasmem, pakiet algorytmów, używać oraz poziom ochrony w celu zastosowania do treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="db9bc-133">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="db9bc-134">Uwierzytelnianie klienta jest wykonywane raz na sesji i wyniki uwierzytelniania są buforowane na czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="db9bc-134">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="db9bc-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="db9bc-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="db9bc-136">Zabezpieczenia transportu jest sprzężona z zabezpieczeń komunikatów.</span><span class="sxs-lookup"><span data-stu-id="db9bc-136">Transport security is coupled with message security.</span></span> <span data-ttu-id="db9bc-137">Zabezpieczenia transportu znajduje się przez protokół TLS za pośrednictwem protokołu TCP lub SPNego i zapewnia integralność, poufności i uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="db9bc-137">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="db9bc-138">Zabezpieczenia komunikatów SOAP zapewnia uwierzytelnianie klienta.</span><span class="sxs-lookup"><span data-stu-id="db9bc-138">SOAP message security provides client authentication.</span></span> <span data-ttu-id="db9bc-139">Domyślnie uwierzytelnianie klienta jest wykonywane raz na sesję, a wyniki uwierzytelniania są buforowane na czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="db9bc-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db9bc-140">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="db9bc-140">Child Elements</span></span>  
  
|<span data-ttu-id="db9bc-141">Element</span><span class="sxs-lookup"><span data-stu-id="db9bc-141">Element</span></span>|<span data-ttu-id="db9bc-142">Opis</span><span class="sxs-lookup"><span data-stu-id="db9bc-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db9bc-143">\<transport ></span><span class="sxs-lookup"><span data-stu-id="db9bc-143">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|<span data-ttu-id="db9bc-144">Definiuje ustawienia zabezpieczeń dla transportu.</span><span class="sxs-lookup"><span data-stu-id="db9bc-144">Defines the security settings for the transport.</span></span> <span data-ttu-id="db9bc-145">Ten element jest typu <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="db9bc-145">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[<span data-ttu-id="db9bc-146">\<message></span><span class="sxs-lookup"><span data-stu-id="db9bc-146">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|<span data-ttu-id="db9bc-147">Definiuje ustawienia zabezpieczeń dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="db9bc-147">Defines the security settings for the message.</span></span> <span data-ttu-id="db9bc-148">Ten element jest typu <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span><span class="sxs-lookup"><span data-stu-id="db9bc-148">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="db9bc-149">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="db9bc-149">Parent Elements</span></span>  
  
|<span data-ttu-id="db9bc-150">Element</span><span class="sxs-lookup"><span data-stu-id="db9bc-150">Element</span></span>|<span data-ttu-id="db9bc-151">Opis</span><span class="sxs-lookup"><span data-stu-id="db9bc-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db9bc-152">powiązanie</span><span class="sxs-lookup"><span data-stu-id="db9bc-152">binding</span></span>|<span data-ttu-id="db9bc-153">Element powiązania [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="db9bc-153">The binding element of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db9bc-154">Uwagi</span><span class="sxs-lookup"><span data-stu-id="db9bc-154">Remarks</span></span>  
 <span data-ttu-id="db9bc-155">Każda standardowa powiązania udostępnia parametry do kontrolowania wymagania w zakresie zabezpieczeń transferu.</span><span class="sxs-lookup"><span data-stu-id="db9bc-155">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="db9bc-156">Te parametry obejmują zazwyczaj tryb zabezpieczeń, który określono, czy zabezpieczeń na poziomie transportu lub poziomie wiadomości jest używany i wybór typu poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="db9bc-156">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="db9bc-157">Na podstawie wybranego opcji Parametry te obecny, stos kanał jest zbudowany z odpowiednie zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="db9bc-157">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="db9bc-158">Powiązania dostarczane przez system, dostarczonych przez Windows Communication Foundation (WCF) to zestaw zaprojektowanych do spełniania niektóre z najczęściej stawianych wymagań scenariusza.</span><span class="sxs-lookup"><span data-stu-id="db9bc-158">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="db9bc-159">Każda z tych powiązań umożliwia określenie wymagań dotyczących zabezpieczeń w niektórych określonych scenariuszach docelowych.</span><span class="sxs-lookup"><span data-stu-id="db9bc-159">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="db9bc-160">Ten element konfiguracji zawiera specyfikacje zabezpieczeń `netTcpBinding`.</span><span class="sxs-lookup"><span data-stu-id="db9bc-160">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="db9bc-161">Jest to bezpieczne, niezawodne i zoptymalizowane powiązanie odpowiednie dla komunikacji między komputerami.</span><span class="sxs-lookup"><span data-stu-id="db9bc-161">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="db9bc-162">Domyślnie generuje stosu komunikacji środowiska uruchomieniowego obsługi protokołu TCP dla dostarczania wiadomości i zabezpieczeń Windows dla zabezpieczenia wiadomości i każde uwierzytelnienie, WS-ReliableMessaging, niezawodność i kodowania komunikatu binarnego.</span><span class="sxs-lookup"><span data-stu-id="db9bc-162">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db9bc-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db9bc-163">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpSecurity>  
 <xref:System.ServiceModel.NetTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [<span data-ttu-id="db9bc-164">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="db9bc-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="db9bc-165">Powiązania</span><span class="sxs-lookup"><span data-stu-id="db9bc-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="db9bc-166">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="db9bc-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="db9bc-167">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="db9bc-167">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="db9bc-168">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="db9bc-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
