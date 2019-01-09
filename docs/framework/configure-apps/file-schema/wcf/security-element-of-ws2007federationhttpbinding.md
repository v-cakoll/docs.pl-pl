---
title: '&lt;security&gt; w &lt;ws2007FederationHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: 4ddf963db10656c905220ca22606772625dd7f3c
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145721"
---
# <a name="ltsecuritygt-element-of-ltws2007federationhttpbindinggt"></a><span data-ttu-id="e1bd0-102">&lt;security&gt; w &lt;ws2007FederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="e1bd0-102">&lt;security&gt; element of &lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="e1bd0-103">Definiuje ustawienia zabezpieczeń [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="e1bd0-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="e1bd0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e1bd0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e1bd0-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="e1bd0-105">\<bindings></span></span>  
<span data-ttu-id="e1bd0-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e1bd0-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="e1bd0-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="e1bd0-107">\<binding></span></span>  
<span data-ttu-id="e1bd0-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="e1bd0-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1bd0-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1bd0-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1bd0-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e1bd0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e1bd0-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e1bd0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1bd0-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e1bd0-112">Attributes</span></span>  
  
|<span data-ttu-id="e1bd0-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e1bd0-113">Attribute</span></span>|<span data-ttu-id="e1bd0-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e1bd0-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="e1bd0-115">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="e1bd0-115">Optional.</span></span> <span data-ttu-id="e1bd0-116">Określa typ zabezpieczeń, która jest stosowana.</span><span class="sxs-lookup"><span data-stu-id="e1bd0-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="e1bd0-117">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="e1bd0-117">The default value is `Message`.</span></span> <span data-ttu-id="e1bd0-118">Ten atrybut jest typu <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="e1bd0-118">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="e1bd0-119">Tryb atrybutu</span><span class="sxs-lookup"><span data-stu-id="e1bd0-119">mode Attribute</span></span>  
  
|<span data-ttu-id="e1bd0-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="e1bd0-120">Value</span></span>|<span data-ttu-id="e1bd0-121">Opis</span><span class="sxs-lookup"><span data-stu-id="e1bd0-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e1bd0-122">Brak</span><span class="sxs-lookup"><span data-stu-id="e1bd0-122">None</span></span>|<span data-ttu-id="e1bd0-123">Komunikat protokołu SOAP nie jest bezpieczne podczas przesyłania.</span><span class="sxs-lookup"><span data-stu-id="e1bd0-123">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="e1bd0-124">Komunikat</span><span class="sxs-lookup"><span data-stu-id="e1bd0-124">Message</span></span>|<span data-ttu-id="e1bd0-125">Integralność, poufności, uwierzytelnianie serwera i uwierzytelnianie klienta znajdują się korzystanie z zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="e1bd0-125">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="e1bd0-126">Domyślnie treść jest zaszyfrowany i podpisany.</span><span class="sxs-lookup"><span data-stu-id="e1bd0-126">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="e1bd0-127">Usługa musi być skonfigurowany przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e1bd0-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="e1bd0-128">Uwierzytelnianie klienta jest oparty na token wystawiony do klienta przez usługę tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="e1bd0-128">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="e1bd0-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="e1bd0-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="e1bd0-130">Integralność, poufności i serwerem uwierzytelniania są dostarczane przez protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e1bd0-130">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="e1bd0-131">Usługa musi być skonfigurowany przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e1bd0-131">The service must be configured with a certificate.</span></span> <span data-ttu-id="e1bd0-132">Uwierzytelnianie klienta znajduje się za pomocą zabezpieczeń wiadomości protokołu SOAP i opiera się na token wystawiony do klienta przez usługę tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="e1bd0-132">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1bd0-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e1bd0-133">Child Elements</span></span>  
  
|<span data-ttu-id="e1bd0-134">Element</span><span class="sxs-lookup"><span data-stu-id="e1bd0-134">Element</span></span>|<span data-ttu-id="e1bd0-135">Opis</span><span class="sxs-lookup"><span data-stu-id="e1bd0-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1bd0-136">\<message></span><span class="sxs-lookup"><span data-stu-id="e1bd0-136">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="e1bd0-137">Definiuje ustawienia zabezpieczeń na poziomie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="e1bd0-137">Defines the settings for the message-level security.</span></span> <span data-ttu-id="e1bd0-138">Ten element jest typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="e1bd0-138">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e1bd0-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e1bd0-139">Parent Elements</span></span>  
  
|<span data-ttu-id="e1bd0-140">Element</span><span class="sxs-lookup"><span data-stu-id="e1bd0-140">Element</span></span>|<span data-ttu-id="e1bd0-141">Opis</span><span class="sxs-lookup"><span data-stu-id="e1bd0-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1bd0-142">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="e1bd0-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="e1bd0-143">Definiuje wszystkie możliwości wiązania [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e1bd0-143">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e1bd0-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1bd0-144">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpSecurity>  
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>  
 [<span data-ttu-id="e1bd0-145">Instrukcje: Tworzenie elementu WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="e1bd0-145">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="e1bd0-146">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="e1bd0-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="e1bd0-147">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="e1bd0-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="e1bd0-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="e1bd0-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e1bd0-149">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="e1bd0-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="e1bd0-150">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="e1bd0-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="e1bd0-151">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="e1bd0-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
