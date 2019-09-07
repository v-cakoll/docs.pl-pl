---
title: <security>elementu<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: 450b2403b8cd4ec43a41fd27bccb3b77202820bb
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399903"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="aef03-102">\<> zabezpieczeń elementu \<WS2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="aef03-102">\<security> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="aef03-103">Definiuje ustawienia [ \<zabezpieczeń elementu > WS2007FederationHttpBinding](ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="aef03-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
<span data-ttu-id="aef03-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="aef03-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="aef03-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="aef03-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="aef03-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="aef03-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="aef03-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007FederationHttpBinding >** ](ws2007federationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="aef03-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="aef03-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="aef03-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="aef03-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zabezpieczeń**</span><span class="sxs-lookup"><span data-stu-id="aef03-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aef03-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="aef03-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aef03-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="aef03-111">Attributes and Elements</span></span>  
 <span data-ttu-id="aef03-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="aef03-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aef03-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="aef03-113">Attributes</span></span>  
  
|<span data-ttu-id="aef03-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="aef03-114">Attribute</span></span>|<span data-ttu-id="aef03-115">Opis</span><span class="sxs-lookup"><span data-stu-id="aef03-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="aef03-116">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="aef03-116">Optional.</span></span> <span data-ttu-id="aef03-117">Określa typ stosowanego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="aef03-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="aef03-118">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="aef03-118">The default value is `Message`.</span></span> <span data-ttu-id="aef03-119">Ten atrybut jest typu <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="aef03-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="aef03-120">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="aef03-120">mode Attribute</span></span>  
  
|<span data-ttu-id="aef03-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="aef03-121">Value</span></span>|<span data-ttu-id="aef03-122">Opis</span><span class="sxs-lookup"><span data-stu-id="aef03-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aef03-123">Brak</span><span class="sxs-lookup"><span data-stu-id="aef03-123">None</span></span>|<span data-ttu-id="aef03-124">Komunikat protokołu SOAP nie jest zabezpieczony podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="aef03-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="aef03-125">Message</span><span class="sxs-lookup"><span data-stu-id="aef03-125">Message</span></span>|<span data-ttu-id="aef03-126">Integralność, poufność, uwierzytelnianie serwera i uwierzytelnianie klienta są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="aef03-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="aef03-127">Domyślnie treść jest zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="aef03-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="aef03-128">Usługa musi być skonfigurowana przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="aef03-128">The service must be configured with a certificate.</span></span> <span data-ttu-id="aef03-129">Uwierzytelnianie klienta opiera się na tokenie wystawionym dla klienta przez usługę tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="aef03-129">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="aef03-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="aef03-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="aef03-131">Uwierzytelnianie za pomocą protokołu HTTPS zapewnia integralność, poufność i serwer.</span><span class="sxs-lookup"><span data-stu-id="aef03-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="aef03-132">Usługa musi być skonfigurowana przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="aef03-132">The service must be configured with a certificate.</span></span> <span data-ttu-id="aef03-133">Uwierzytelnianie klienta jest zapewniane przez zabezpieczenia komunikatów protokołu SOAP i opiera się na tokenie wystawionym dla klienta przez usługę tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="aef03-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aef03-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="aef03-134">Child Elements</span></span>  
  
|<span data-ttu-id="aef03-135">Element</span><span class="sxs-lookup"><span data-stu-id="aef03-135">Element</span></span>|<span data-ttu-id="aef03-136">Opis</span><span class="sxs-lookup"><span data-stu-id="aef03-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aef03-137">\<message></span><span class="sxs-lookup"><span data-stu-id="aef03-137">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="aef03-138">Definiuje ustawienia zabezpieczeń na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="aef03-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="aef03-139">Ten element jest typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="aef03-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aef03-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="aef03-140">Parent Elements</span></span>  
  
|<span data-ttu-id="aef03-141">Element</span><span class="sxs-lookup"><span data-stu-id="aef03-141">Element</span></span>|<span data-ttu-id="aef03-142">Opis</span><span class="sxs-lookup"><span data-stu-id="aef03-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aef03-143">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="aef03-143">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="aef03-144">Definiuje wszystkie możliwości [ \<powiązań WSDualHttpBinding >](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="aef03-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aef03-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aef03-145">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="aef03-146">Instrukcje: Utwórz WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="aef03-146">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="aef03-147">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="aef03-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="aef03-148">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="aef03-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="aef03-149">Powiązania</span><span class="sxs-lookup"><span data-stu-id="aef03-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="aef03-150">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="aef03-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="aef03-151">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="aef03-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="aef03-152">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="aef03-152">\<binding></span></span>](../../../misc/binding.md)
