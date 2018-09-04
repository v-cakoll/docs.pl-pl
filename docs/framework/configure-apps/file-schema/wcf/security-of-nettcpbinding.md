---
title: '&lt;security&gt; w &lt;netTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 13aeb3261fdb9689caa1dea1ec7382fdb9d9b1ce
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516976"
---
# <a name="ltsecuritygt-of-ltnettcpbindinggt"></a><span data-ttu-id="655b1-102">&lt;security&gt; w &lt;netTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="655b1-102">&lt;security&gt; of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="655b1-103">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="655b1-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="655b1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="655b1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="655b1-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="655b1-105">\<bindings></span></span>  
<span data-ttu-id="655b1-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="655b1-106">\<netTcpBinding></span></span>  
<span data-ttu-id="655b1-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="655b1-107">\<binding></span></span>  
<span data-ttu-id="655b1-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="655b1-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="655b1-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="655b1-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="655b1-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="655b1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="655b1-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="655b1-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="655b1-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="655b1-112">Attributes</span></span>  
  
|<span data-ttu-id="655b1-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="655b1-113">Attribute</span></span>|<span data-ttu-id="655b1-114">Opis</span><span class="sxs-lookup"><span data-stu-id="655b1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="655b1-115">tryb</span><span class="sxs-lookup"><span data-stu-id="655b1-115">mode</span></span>|<span data-ttu-id="655b1-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="655b1-116">Optional.</span></span> <span data-ttu-id="655b1-117">Określa typ zabezpieczeń, która jest stosowana.</span><span class="sxs-lookup"><span data-stu-id="655b1-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="655b1-118">Poniżej przedstawiono prawidłowe wartości.</span><span class="sxs-lookup"><span data-stu-id="655b1-118">Valid values are shown below.</span></span> <span data-ttu-id="655b1-119">Wartość domyślna to `Transport`.</span><span class="sxs-lookup"><span data-stu-id="655b1-119">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="655b1-120">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="655b1-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="655b1-121">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="655b1-121">mode Attribute</span></span>  
  
|<span data-ttu-id="655b1-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="655b1-122">Value</span></span>|<span data-ttu-id="655b1-123">Opis</span><span class="sxs-lookup"><span data-stu-id="655b1-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="655b1-124">Brak</span><span class="sxs-lookup"><span data-stu-id="655b1-124">None</span></span>|<span data-ttu-id="655b1-125">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="655b1-125">Security is disabled.</span></span>|  
|<span data-ttu-id="655b1-126">Transportu</span><span class="sxs-lookup"><span data-stu-id="655b1-126">Transport</span></span>|<span data-ttu-id="655b1-127">Zabezpieczenia transportu znajduje się za pośrednictwem protokołu TCP lub SPNego przy użyciu protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="655b1-127">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="655b1-128">Usługa może być konieczne można skonfigurować za pomocą certyfikatów SSL.</span><span class="sxs-lookup"><span data-stu-id="655b1-128">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="655b1-129">Istnieje możliwość kontrolować poziom ochrony w tym trybie.</span><span class="sxs-lookup"><span data-stu-id="655b1-129">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="655b1-130">Komunikat</span><span class="sxs-lookup"><span data-stu-id="655b1-130">Message</span></span>|<span data-ttu-id="655b1-131">Zabezpieczenia korzystanie z zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="655b1-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="655b1-132">Domyślnie treści protokołu SOAP jest zaszyfrowany i podpisany.</span><span class="sxs-lookup"><span data-stu-id="655b1-132">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="655b1-133">Ten tryb zapewnia szeroką gamę funkcji, takich jak tego, czy poświadczenia usługi są dostępne pod adresem klientem poza pasmem, pakiet algorytmów, używać oraz poziom ochrony w celu zastosowania do treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="655b1-133">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="655b1-134">Uwierzytelnianie klienta jest wykonywane raz na sesji i wyniki uwierzytelniania są buforowane na czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="655b1-134">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="655b1-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="655b1-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="655b1-136">Zabezpieczenia transportu jest sprzężona z zabezpieczeń komunikatów.</span><span class="sxs-lookup"><span data-stu-id="655b1-136">Transport security is coupled with message security.</span></span> <span data-ttu-id="655b1-137">Zabezpieczenia transportu znajduje się przez protokół TLS za pośrednictwem protokołu TCP lub SPNego i zapewnia integralność, poufności i uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="655b1-137">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="655b1-138">Zabezpieczenia komunikatów SOAP zapewnia uwierzytelnianie klienta.</span><span class="sxs-lookup"><span data-stu-id="655b1-138">SOAP message security provides client authentication.</span></span> <span data-ttu-id="655b1-139">Domyślnie uwierzytelnianie klienta jest wykonywane raz na sesję, a wyniki uwierzytelniania są buforowane na czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="655b1-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="655b1-140">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="655b1-140">Child Elements</span></span>  
  
|<span data-ttu-id="655b1-141">Element</span><span class="sxs-lookup"><span data-stu-id="655b1-141">Element</span></span>|<span data-ttu-id="655b1-142">Opis</span><span class="sxs-lookup"><span data-stu-id="655b1-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="655b1-143">\<transport ></span><span class="sxs-lookup"><span data-stu-id="655b1-143">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|<span data-ttu-id="655b1-144">Definiuje ustawienia zabezpieczeń dla transportu.</span><span class="sxs-lookup"><span data-stu-id="655b1-144">Defines the security settings for the transport.</span></span> <span data-ttu-id="655b1-145">Ten element jest typu <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="655b1-145">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[<span data-ttu-id="655b1-146">\<message></span><span class="sxs-lookup"><span data-stu-id="655b1-146">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|<span data-ttu-id="655b1-147">Definiuje ustawienia zabezpieczeń dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="655b1-147">Defines the security settings for the message.</span></span> <span data-ttu-id="655b1-148">Ten element jest typu <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span><span class="sxs-lookup"><span data-stu-id="655b1-148">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="655b1-149">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="655b1-149">Parent Elements</span></span>  
  
|<span data-ttu-id="655b1-150">Element</span><span class="sxs-lookup"><span data-stu-id="655b1-150">Element</span></span>|<span data-ttu-id="655b1-151">Opis</span><span class="sxs-lookup"><span data-stu-id="655b1-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="655b1-152">powiązanie</span><span class="sxs-lookup"><span data-stu-id="655b1-152">binding</span></span>|<span data-ttu-id="655b1-153">Element powiązania [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="655b1-153">The binding element of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="655b1-154">Uwagi</span><span class="sxs-lookup"><span data-stu-id="655b1-154">Remarks</span></span>  
 <span data-ttu-id="655b1-155">Każda standardowa powiązania udostępnia parametry do kontrolowania wymagania w zakresie zabezpieczeń transferu.</span><span class="sxs-lookup"><span data-stu-id="655b1-155">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="655b1-156">Te parametry obejmują zazwyczaj tryb zabezpieczeń, który określono, czy zabezpieczeń na poziomie transportu lub poziomie wiadomości jest używany i wybór typu poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="655b1-156">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="655b1-157">Na podstawie wybranego opcji Parametry te obecny, stos kanał jest zbudowany z odpowiednie zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="655b1-157">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="655b1-158">Powiązania dostarczane przez system, dostarczonych przez Windows Communication Foundation (WCF) to zestaw zaprojektowanych do spełniania niektóre z najczęściej stawianych wymagań scenariusza.</span><span class="sxs-lookup"><span data-stu-id="655b1-158">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="655b1-159">Każda z tych powiązań umożliwia określenie wymagań dotyczących zabezpieczeń w niektórych określonych scenariuszach docelowych.</span><span class="sxs-lookup"><span data-stu-id="655b1-159">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="655b1-160">Ten element konfiguracji zawiera specyfikacje zabezpieczeń `netTcpBinding`.</span><span class="sxs-lookup"><span data-stu-id="655b1-160">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="655b1-161">Jest to bezpieczne, niezawodne i zoptymalizowane powiązanie odpowiednie dla komunikacji między komputerami.</span><span class="sxs-lookup"><span data-stu-id="655b1-161">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="655b1-162">Domyślnie generuje stosu komunikacji środowiska uruchomieniowego obsługi protokołu TCP dla dostarczania wiadomości i zabezpieczeń Windows dla zabezpieczenia wiadomości i każde uwierzytelnienie, WS-ReliableMessaging, niezawodność i kodowania komunikatu binarnego.</span><span class="sxs-lookup"><span data-stu-id="655b1-162">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="655b1-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="655b1-163">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpSecurity>  
 <xref:System.ServiceModel.NetTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [<span data-ttu-id="655b1-164">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="655b1-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="655b1-165">Powiązania</span><span class="sxs-lookup"><span data-stu-id="655b1-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="655b1-166">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="655b1-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="655b1-167">Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="655b1-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="655b1-168">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="655b1-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
