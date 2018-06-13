---
title: '&lt;security&gt; w &lt;netTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f58dd0ee1b00785e82628e5442c736866ffe7db5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751236"
---
# <a name="ltsecuritygt-of-ltnettcpbindinggt"></a><span data-ttu-id="642cb-102">&lt;security&gt; w &lt;netTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="642cb-102">&lt;security&gt; of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="642cb-103">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="642cb-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="642cb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="642cb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="642cb-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="642cb-105">\<bindings></span></span>  
<span data-ttu-id="642cb-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="642cb-106">\<netTcpBinding></span></span>  
<span data-ttu-id="642cb-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="642cb-107">\<binding></span></span>  
<span data-ttu-id="642cb-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="642cb-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="642cb-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="642cb-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="642cb-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="642cb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="642cb-111">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="642cb-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="642cb-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="642cb-112">Attributes</span></span>  
  
|<span data-ttu-id="642cb-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="642cb-113">Attribute</span></span>|<span data-ttu-id="642cb-114">Opis</span><span class="sxs-lookup"><span data-stu-id="642cb-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="642cb-115">tryb</span><span class="sxs-lookup"><span data-stu-id="642cb-115">mode</span></span>|<span data-ttu-id="642cb-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="642cb-116">Optional.</span></span> <span data-ttu-id="642cb-117">Określa typ zabezpieczeń, która została zastosowana.</span><span class="sxs-lookup"><span data-stu-id="642cb-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="642cb-118">Poniżej przedstawiono prawidłowe wartości.</span><span class="sxs-lookup"><span data-stu-id="642cb-118">Valid values are shown below.</span></span> <span data-ttu-id="642cb-119">Wartość domyślna to `Transport`.</span><span class="sxs-lookup"><span data-stu-id="642cb-119">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="642cb-120">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="642cb-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="642cb-121">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="642cb-121">mode Attribute</span></span>  
  
|<span data-ttu-id="642cb-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="642cb-122">Value</span></span>|<span data-ttu-id="642cb-123">Opis</span><span class="sxs-lookup"><span data-stu-id="642cb-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="642cb-124">Brak</span><span class="sxs-lookup"><span data-stu-id="642cb-124">None</span></span>|<span data-ttu-id="642cb-125">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="642cb-125">Security is disabled.</span></span>|  
|<span data-ttu-id="642cb-126">Transportu</span><span class="sxs-lookup"><span data-stu-id="642cb-126">Transport</span></span>|<span data-ttu-id="642cb-127">Zabezpieczenia transportu są udostępniane za pośrednictwem protokołu TCP lub SPNego przy użyciu protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="642cb-127">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="642cb-128">Usługa może być konieczne można skonfigurować za pomocą certyfikatów SSL.</span><span class="sxs-lookup"><span data-stu-id="642cb-128">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="642cb-129">Jest możliwe kontrolowanie poziomu ochrony, w tym trybie.</span><span class="sxs-lookup"><span data-stu-id="642cb-129">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="642cb-130">Komunikat</span><span class="sxs-lookup"><span data-stu-id="642cb-130">Message</span></span>|<span data-ttu-id="642cb-131">Zabezpieczenia korzystanie z zabezpieczeń komunikatów SOAP.</span><span class="sxs-lookup"><span data-stu-id="642cb-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="642cb-132">Domyślnie treści protokołu SOAP zostaje zaszyfrowany i podpisany.</span><span class="sxs-lookup"><span data-stu-id="642cb-132">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="642cb-133">W tym trybie oferuje wiele funkcji, takich jak określa, czy poświadczenia usługi są dostępne pod adresem klientem poza pasmem, pakiet algorytmów do użycia, a poziom ochrony do zastosowania do treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="642cb-133">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="642cb-134">Uwierzytelnianie klienta jest wykonywane raz na sesji i wyniki uwierzytelniania są buforowane na czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="642cb-134">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="642cb-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="642cb-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="642cb-136">Zabezpieczenia transportu jest sprzężona z zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="642cb-136">Transport security is coupled with message security.</span></span> <span data-ttu-id="642cb-137">Zabezpieczenia transportu są dostarczane przez TLS za pośrednictwem protokołu TCP lub SPNego i zapewnia integralność, poufności i uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="642cb-137">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="642cb-138">Zabezpieczenia komunikatów SOAP zapewnia uwierzytelnianie klienta.</span><span class="sxs-lookup"><span data-stu-id="642cb-138">SOAP message security provides client authentication.</span></span> <span data-ttu-id="642cb-139">Domyślnie uwierzytelnianie klienta jest wykonywane raz na sesji i wyniki uwierzytelniania są buforowane na czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="642cb-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="642cb-140">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="642cb-140">Child Elements</span></span>  
  
|<span data-ttu-id="642cb-141">Element</span><span class="sxs-lookup"><span data-stu-id="642cb-141">Element</span></span>|<span data-ttu-id="642cb-142">Opis</span><span class="sxs-lookup"><span data-stu-id="642cb-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="642cb-143">\<transport ></span><span class="sxs-lookup"><span data-stu-id="642cb-143">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|<span data-ttu-id="642cb-144">Definiuje ustawienia zabezpieczeń dla transportu.</span><span class="sxs-lookup"><span data-stu-id="642cb-144">Defines the security settings for the transport.</span></span> <span data-ttu-id="642cb-145">Ten element jest typu <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="642cb-145">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[<span data-ttu-id="642cb-146">\<message></span><span class="sxs-lookup"><span data-stu-id="642cb-146">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|<span data-ttu-id="642cb-147">Definiuje ustawienia zabezpieczeń dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="642cb-147">Defines the security settings for the message.</span></span> <span data-ttu-id="642cb-148">Ten element jest typu <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span><span class="sxs-lookup"><span data-stu-id="642cb-148">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="642cb-149">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="642cb-149">Parent Elements</span></span>  
  
|<span data-ttu-id="642cb-150">Element</span><span class="sxs-lookup"><span data-stu-id="642cb-150">Element</span></span>|<span data-ttu-id="642cb-151">Opis</span><span class="sxs-lookup"><span data-stu-id="642cb-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="642cb-152">powiązanie</span><span class="sxs-lookup"><span data-stu-id="642cb-152">binding</span></span>|<span data-ttu-id="642cb-153">Element powiązania [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="642cb-153">The binding element of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="642cb-154">Uwagi</span><span class="sxs-lookup"><span data-stu-id="642cb-154">Remarks</span></span>  
 <span data-ttu-id="642cb-155">Każdy powiązań standardowych zawiera parametry kontrolowanie wymagania dotyczące zabezpieczeń transferu.</span><span class="sxs-lookup"><span data-stu-id="642cb-155">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="642cb-156">Te parametry obejmują zazwyczaj tryb zabezpieczeń, które określone, czy używany jest zabezpieczeń na poziomie transportu lub poziom wiadomości i wybór typu poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="642cb-156">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="642cb-157">Na podstawie wyboru opcji parametrów nie istnieje stosu kanał jest tworzony z odpowiednich ustawień zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="642cb-157">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="642cb-158">Powiązania dostarczane przez system dostarczane przez Windows Communication Foundation (WCF) są zestawem zaprojektowane pod kątem niektórych wymagań najbardziej typowych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="642cb-158">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="642cb-159">Każdy z tych powiązań umożliwia określenie wymagań dotyczących zabezpieczeń dla niektórych konkretnych scenariuszy docelowych.</span><span class="sxs-lookup"><span data-stu-id="642cb-159">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="642cb-160">Ten element konfiguracji zawiera specyfikacji zabezpieczenia dla `netTcpBinding`.</span><span class="sxs-lookup"><span data-stu-id="642cb-160">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="642cb-161">Jest to bezpieczne, niezawodne i zoptymalizowane powiązanie odpowiednie dla komunikacji między komputerami.</span><span class="sxs-lookup"><span data-stu-id="642cb-161">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="642cb-162">Domyślnie generuje stosu komunikacji środowiska uruchomieniowego obsługi protokołu TCP dla dostarczanie komunikatów i zabezpieczenia systemu Windows dla komunikatów zabezpieczeń i uwierzytelniania, WS-ReliableMessaging, niezawodności i kodowanie komunikatu binarnego.</span><span class="sxs-lookup"><span data-stu-id="642cb-162">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="642cb-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="642cb-163">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpSecurity>  
 <xref:System.ServiceModel.NetTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [<span data-ttu-id="642cb-164">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="642cb-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="642cb-165">Powiązania</span><span class="sxs-lookup"><span data-stu-id="642cb-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="642cb-166">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="642cb-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="642cb-167">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="642cb-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="642cb-168">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="642cb-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
