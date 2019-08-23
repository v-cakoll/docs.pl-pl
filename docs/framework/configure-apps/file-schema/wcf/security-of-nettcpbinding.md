---
title: <security> dla <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: 04e7e94f47be37dc9c4cbf404a269b9784281d7d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936606"
---
# <a name="security-of-nettcpbinding"></a><span data-ttu-id="98b60-102">\<zabezpieczenia > \<NetTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="98b60-102">\<security> of \<netTcpBinding></span></span>
<span data-ttu-id="98b60-103">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="98b60-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="98b60-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="98b60-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="98b60-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="98b60-105">\<bindings></span></span>  
<span data-ttu-id="98b60-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="98b60-106">\<netTcpBinding></span></span>  
<span data-ttu-id="98b60-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="98b60-107">\<binding></span></span>  
<span data-ttu-id="98b60-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="98b60-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98b60-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="98b60-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             protectionLevel="None/Sign/EncryptAndSign" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98b60-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="98b60-110">Attributes and Elements</span></span>  
 <span data-ttu-id="98b60-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="98b60-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98b60-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="98b60-112">Attributes</span></span>  
  
|<span data-ttu-id="98b60-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="98b60-113">Attribute</span></span>|<span data-ttu-id="98b60-114">Opis</span><span class="sxs-lookup"><span data-stu-id="98b60-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="98b60-115">tryb</span><span class="sxs-lookup"><span data-stu-id="98b60-115">mode</span></span>|<span data-ttu-id="98b60-116">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="98b60-116">Optional.</span></span> <span data-ttu-id="98b60-117">Określa typ stosowanego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="98b60-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="98b60-118">Poniżej przedstawiono prawidłowe wartości.</span><span class="sxs-lookup"><span data-stu-id="98b60-118">Valid values are shown below.</span></span> <span data-ttu-id="98b60-119">Wartość domyślna to `Transport`.</span><span class="sxs-lookup"><span data-stu-id="98b60-119">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="98b60-120">Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="98b60-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="98b60-121">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="98b60-121">mode Attribute</span></span>  
  
|<span data-ttu-id="98b60-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="98b60-122">Value</span></span>|<span data-ttu-id="98b60-123">Opis</span><span class="sxs-lookup"><span data-stu-id="98b60-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="98b60-124">Brak</span><span class="sxs-lookup"><span data-stu-id="98b60-124">None</span></span>|<span data-ttu-id="98b60-125">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="98b60-125">Security is disabled.</span></span>|  
|<span data-ttu-id="98b60-126">Transportu</span><span class="sxs-lookup"><span data-stu-id="98b60-126">Transport</span></span>|<span data-ttu-id="98b60-127">Zabezpieczenia transportu są udostępniane przy użyciu protokołu TLS przez TCP lub SPNego.</span><span class="sxs-lookup"><span data-stu-id="98b60-127">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="98b60-128">Może być konieczne skonfigurowanie usługi przy użyciu certyfikatów SSL.</span><span class="sxs-lookup"><span data-stu-id="98b60-128">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="98b60-129">Istnieje możliwość kontrolowania poziomu ochrony w tym trybie.</span><span class="sxs-lookup"><span data-stu-id="98b60-129">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="98b60-130">Message</span><span class="sxs-lookup"><span data-stu-id="98b60-130">Message</span></span>|<span data-ttu-id="98b60-131">Zabezpieczenia są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="98b60-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="98b60-132">Domyślnie treść protokołu SOAP jest zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="98b60-132">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="98b60-133">Ten tryb oferuje różne funkcje, takie jak to, czy poświadczenia usługi są dostępne na kliencie poza pasmem, pakiet algorytmów do użycia oraz jaki poziom ochrony ma być stosowany do treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="98b60-133">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="98b60-134">Uwierzytelnianie klienta jest wykonywane raz na sesję, a wyniki uwierzytelniania są buforowane na czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="98b60-134">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="98b60-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="98b60-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="98b60-136">Zabezpieczenia transportu są powiązane z zabezpieczeniami komunikatów.</span><span class="sxs-lookup"><span data-stu-id="98b60-136">Transport security is coupled with message security.</span></span> <span data-ttu-id="98b60-137">Zabezpieczenia transportu są udostępniane przez protokół TLS przez TCP lub SPNego oraz zapewniają integralność, poufność i uwierzytelnianie serwera.</span><span class="sxs-lookup"><span data-stu-id="98b60-137">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="98b60-138">Zabezpieczenia komunikatów protokołu SOAP zapewniają uwierzytelnianie klienta.</span><span class="sxs-lookup"><span data-stu-id="98b60-138">SOAP message security provides client authentication.</span></span> <span data-ttu-id="98b60-139">Domyślnie uwierzytelnianie klienta jest wykonywane raz na sesję, a wyniki uwierzytelniania są buforowane przez czas trwania sesji.</span><span class="sxs-lookup"><span data-stu-id="98b60-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98b60-140">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="98b60-140">Child Elements</span></span>  
  
|<span data-ttu-id="98b60-141">Element</span><span class="sxs-lookup"><span data-stu-id="98b60-141">Element</span></span>|<span data-ttu-id="98b60-142">Opis</span><span class="sxs-lookup"><span data-stu-id="98b60-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98b60-143">\<> transportu</span><span class="sxs-lookup"><span data-stu-id="98b60-143">\<transport></span></span>](transport-of-nettcpbinding.md)|<span data-ttu-id="98b60-144">Definiuje ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="98b60-144">Defines the security settings for the transport.</span></span> <span data-ttu-id="98b60-145">Ten element jest typu <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="98b60-145">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[<span data-ttu-id="98b60-146">\<message></span><span class="sxs-lookup"><span data-stu-id="98b60-146">\<message></span></span>](message-element-of-nettcpbinding.md)|<span data-ttu-id="98b60-147">Definiuje ustawienia zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="98b60-147">Defines the security settings for the message.</span></span> <span data-ttu-id="98b60-148">Ten element jest typu <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span><span class="sxs-lookup"><span data-stu-id="98b60-148">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="98b60-149">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="98b60-149">Parent Elements</span></span>  
  
|<span data-ttu-id="98b60-150">Element</span><span class="sxs-lookup"><span data-stu-id="98b60-150">Element</span></span>|<span data-ttu-id="98b60-151">Opis</span><span class="sxs-lookup"><span data-stu-id="98b60-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="98b60-152">powiązanie</span><span class="sxs-lookup"><span data-stu-id="98b60-152">binding</span></span>|<span data-ttu-id="98b60-153">Element Binding elementu [ \<NetTcpBinding >](nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="98b60-153">The binding element of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98b60-154">Uwagi</span><span class="sxs-lookup"><span data-stu-id="98b60-154">Remarks</span></span>  
 <span data-ttu-id="98b60-155">Wszystkie powiązania standardowe zawierają parametry służące do kontrolowania wymagań dotyczących zabezpieczeń transferu.</span><span class="sxs-lookup"><span data-stu-id="98b60-155">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="98b60-156">Parametry te zazwyczaj obejmują tryb zabezpieczeń, który określa, czy używane są zabezpieczenia na poziomie wiadomości lub transportu oraz wybór typu poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="98b60-156">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="98b60-157">Na podstawie wyboru opcji tych parametrów istnieje stos kanału z odpowiednimi zabezpieczeniami.</span><span class="sxs-lookup"><span data-stu-id="98b60-157">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="98b60-158">Powiązania dostarczone przez system Windows Communication Foundation (WCF) są zestawem zaprojektowanym pod kątem spełnienia niektórych typowych wymagań scenariusza.</span><span class="sxs-lookup"><span data-stu-id="98b60-158">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="98b60-159">Każde z tych powiązań umożliwia określenie wymagań dotyczących zabezpieczeń dla niektórych konkretnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="98b60-159">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="98b60-160">Ten element konfiguracji zawiera specyfikacje zabezpieczeń dla programu `netTcpBinding`.</span><span class="sxs-lookup"><span data-stu-id="98b60-160">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="98b60-161">Jest to bezpieczne, niezawodne i zoptymalizowane powiązanie odpowiednie dla komunikacji między komputerami.</span><span class="sxs-lookup"><span data-stu-id="98b60-161">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="98b60-162">Domyślnie generuje stos komunikacji środowiska uruchomieniowego obsługujący protokół TCP na potrzeby dostarczania komunikatów i zabezpieczenia systemu Windows w celu zapewnienia bezpieczeństwa i uwierzytelniania komunikatów oraz szyfrowania wiadomości binarnych.</span><span class="sxs-lookup"><span data-stu-id="98b60-162">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98b60-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98b60-163">See also</span></span>

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="98b60-164">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="98b60-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="98b60-165">Powiązania</span><span class="sxs-lookup"><span data-stu-id="98b60-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="98b60-166">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="98b60-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="98b60-167">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="98b60-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="98b60-168">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="98b60-168">\<binding></span></span>](../../../misc/binding.md)
