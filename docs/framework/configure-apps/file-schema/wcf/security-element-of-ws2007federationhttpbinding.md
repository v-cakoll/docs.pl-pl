---
title: <security>elementu<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: 61b56ca1fae5c328cda0bbebef4026f0784095a3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936819"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="66197-102">\<> zabezpieczeń elementu \<WS2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="66197-102">\<security> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="66197-103">Definiuje ustawienia [ \<zabezpieczeń elementu > WS2007FederationHttpBinding](ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="66197-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="66197-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="66197-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="66197-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="66197-105">\<bindings></span></span>  
<span data-ttu-id="66197-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="66197-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="66197-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="66197-107">\<binding></span></span>  
<span data-ttu-id="66197-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="66197-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66197-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="66197-109">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/  Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               defaultProtectionLevel="none/sign/EncryptAndSign"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
  </binding>
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66197-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="66197-110">Attributes and Elements</span></span>  
 <span data-ttu-id="66197-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="66197-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66197-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="66197-112">Attributes</span></span>  
  
|<span data-ttu-id="66197-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="66197-113">Attribute</span></span>|<span data-ttu-id="66197-114">Opis</span><span class="sxs-lookup"><span data-stu-id="66197-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="66197-115">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="66197-115">Optional.</span></span> <span data-ttu-id="66197-116">Określa typ stosowanego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="66197-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="66197-117">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="66197-117">The default value is `Message`.</span></span> <span data-ttu-id="66197-118">Ten atrybut jest typu <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="66197-118">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="66197-119">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="66197-119">mode Attribute</span></span>  
  
|<span data-ttu-id="66197-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="66197-120">Value</span></span>|<span data-ttu-id="66197-121">Opis</span><span class="sxs-lookup"><span data-stu-id="66197-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="66197-122">Brak</span><span class="sxs-lookup"><span data-stu-id="66197-122">None</span></span>|<span data-ttu-id="66197-123">Komunikat protokołu SOAP nie jest zabezpieczony podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="66197-123">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="66197-124">Message</span><span class="sxs-lookup"><span data-stu-id="66197-124">Message</span></span>|<span data-ttu-id="66197-125">Integralność, poufność, uwierzytelnianie serwera i uwierzytelnianie klienta są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="66197-125">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="66197-126">Domyślnie treść jest zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="66197-126">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="66197-127">Usługa musi być skonfigurowana przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="66197-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="66197-128">Uwierzytelnianie klienta opiera się na tokenie wystawionym dla klienta przez usługę tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="66197-128">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="66197-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="66197-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="66197-130">Uwierzytelnianie za pomocą protokołu HTTPS zapewnia integralność, poufność i serwer.</span><span class="sxs-lookup"><span data-stu-id="66197-130">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="66197-131">Usługa musi być skonfigurowana przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="66197-131">The service must be configured with a certificate.</span></span> <span data-ttu-id="66197-132">Uwierzytelnianie klienta jest zapewniane przez zabezpieczenia komunikatów protokołu SOAP i opiera się na tokenie wystawionym dla klienta przez usługę tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="66197-132">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="66197-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="66197-133">Child Elements</span></span>  
  
|<span data-ttu-id="66197-134">Element</span><span class="sxs-lookup"><span data-stu-id="66197-134">Element</span></span>|<span data-ttu-id="66197-135">Opis</span><span class="sxs-lookup"><span data-stu-id="66197-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66197-136">\<message></span><span class="sxs-lookup"><span data-stu-id="66197-136">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="66197-137">Definiuje ustawienia zabezpieczeń na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="66197-137">Defines the settings for the message-level security.</span></span> <span data-ttu-id="66197-138">Ten element jest typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="66197-138">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="66197-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="66197-139">Parent Elements</span></span>  
  
|<span data-ttu-id="66197-140">Element</span><span class="sxs-lookup"><span data-stu-id="66197-140">Element</span></span>|<span data-ttu-id="66197-141">Opis</span><span class="sxs-lookup"><span data-stu-id="66197-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66197-142">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="66197-142">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="66197-143">Definiuje wszystkie możliwości [ \<powiązań WSDualHttpBinding >](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="66197-143">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66197-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66197-144">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="66197-145">Instrukcje: Utwórz WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="66197-145">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="66197-146">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="66197-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="66197-147">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="66197-147">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="66197-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="66197-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="66197-149">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="66197-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="66197-150">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="66197-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="66197-151">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="66197-151">\<binding></span></span>](../../../misc/binding.md)
