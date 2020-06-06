---
title: <security> dla <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 97c52fa4f062ed0c65d5b1a8ca47a1439ab04cf5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736481"
---
# <a name="security-of-nethttpbinding"></a><span data-ttu-id="61454-102">\<security> dla \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="61454-102">\<security> of \<netHttpBinding></span></span>

<span data-ttu-id="61454-103">Definiuje możliwości zabezpieczeń programu [\<netHttpBinding>](nethttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="61454-103">Defines the security capabilities of the [\<netHttpBinding>](nethttpbinding.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  

## <a name="syntax"></a><span data-ttu-id="61454-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="61454-104">Syntax</span></span>

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="61454-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="61454-105">Attributes and elements</span></span>

<span data-ttu-id="61454-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="61454-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="61454-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="61454-107">Attributes</span></span>

|<span data-ttu-id="61454-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="61454-108">Attribute</span></span>|<span data-ttu-id="61454-109">Opis</span><span class="sxs-lookup"><span data-stu-id="61454-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="61454-110">tryb</span><span class="sxs-lookup"><span data-stu-id="61454-110">mode</span></span>|<span data-ttu-id="61454-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="61454-111">Optional.</span></span> <span data-ttu-id="61454-112">Określa typ używanego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="61454-112">Specifies the type of security that is used.</span></span> <span data-ttu-id="61454-113">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="61454-113">The default is `None`.</span></span> <span data-ttu-id="61454-114">Ten atrybut jest typu <xref:System.ServiceModel.BasicHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="61454-114">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|

## <a name="mode-attribute"></a><span data-ttu-id="61454-115">atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="61454-115">mode attribute</span></span>

|<span data-ttu-id="61454-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="61454-116">Value</span></span>|<span data-ttu-id="61454-117">Opis</span><span class="sxs-lookup"><span data-stu-id="61454-117">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="61454-118">Brak</span><span class="sxs-lookup"><span data-stu-id="61454-118">None</span></span>|<span data-ttu-id="61454-119">-Komunikaty nie są zabezpieczane podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="61454-119">-   Messages are not secured during transfer.</span></span>|
|<span data-ttu-id="61454-120">Transport</span><span class="sxs-lookup"><span data-stu-id="61454-120">Transport</span></span>|<span data-ttu-id="61454-121">Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="61454-121">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="61454-122">Komunikaty protokołu SOAP są zabezpieczone przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="61454-122">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="61454-123">Usługa jest uwierzytelniana na kliencie przy użyciu certyfikatu X. 509 usługi.</span><span class="sxs-lookup"><span data-stu-id="61454-123">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="61454-124">Klient jest uwierzytelniany przy użyciu dostarczonego obiekt ClientCredentialtype.</span><span class="sxs-lookup"><span data-stu-id="61454-124">The client is authenticated using the ClientCredentialType supplied.</span></span>|
|<span data-ttu-id="61454-125">Komunikat</span><span class="sxs-lookup"><span data-stu-id="61454-125">Message</span></span>|<span data-ttu-id="61454-126">Zabezpieczenia są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="61454-126">Security is provided using SOAP message security.</span></span> <span data-ttu-id="61454-127">Domyślnie treść jest zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="61454-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="61454-128">W przypadku tego powiązania system wymaga, aby certyfikat serwera został dostarczony do klienta poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="61454-128">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="61454-129">Jedyna prawidłowa `ClientCredentialType` dla tego powiązania to `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="61454-129">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|
|<span data-ttu-id="61454-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="61454-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="61454-131">Integralność, poufność i uwierzytelnianie serwera są udostępniane przez zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="61454-131">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="61454-132">Uwierzytelnianie klienta jest zapewniane przez zabezpieczenia komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="61454-132">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="61454-133">Ten tryb jest istotny, gdy użytkownik jest uwierzytelniany przy użyciu nazwy użytkownika/hasła i istnieje wdrożenie HTTP na potrzeby zabezpieczania transferu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="61454-133">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|
|<span data-ttu-id="61454-134">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="61454-134">TransportCredentialOnly</span></span>|<span data-ttu-id="61454-135">Ten tryb nie zapewnia integralności i poufności komunikatów.</span><span class="sxs-lookup"><span data-stu-id="61454-135">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="61454-136">Zapewnia uwierzytelnianie klienta oparte na protokole HTTP.</span><span class="sxs-lookup"><span data-stu-id="61454-136">It provides http-based client authentication.</span></span> <span data-ttu-id="61454-137">Ten tryb powinien być używany z zachowaniem ostrożności.</span><span class="sxs-lookup"><span data-stu-id="61454-137">This mode should be used with caution.</span></span> <span data-ttu-id="61454-138">Powinna być używana w środowiskach, w których zabezpieczenia transportu są dostarczane przy użyciu innych metod (takich jak IPSec) i tylko uwierzytelnianie klienta jest udostępniane przez infrastrukturę WCF.</span><span class="sxs-lookup"><span data-stu-id="61454-138">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="61454-139">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="61454-139">Child elements</span></span>

|<span data-ttu-id="61454-140">Element</span><span class="sxs-lookup"><span data-stu-id="61454-140">Element</span></span>|<span data-ttu-id="61454-141">Opis</span><span class="sxs-lookup"><span data-stu-id="61454-141">Description</span></span>|
|-------------|-----------------|
|[\<transport>](transport-of-nethttpbinding.md)|<span data-ttu-id="61454-142">Definiuje ustawienia zabezpieczeń transportu dla podstawowej usługi HTTP.</span><span class="sxs-lookup"><span data-stu-id="61454-142">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="61454-143">Ten element odnosi się do <xref:System.ServiceModel.HttpTransportSecurity> .</span><span class="sxs-lookup"><span data-stu-id="61454-143">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|
|[\<message>](message-of-nethttpbinding.md)|<span data-ttu-id="61454-144">Definiuje ustawienia zabezpieczeń wiadomości dla podstawowej usługi HTTP.</span><span class="sxs-lookup"><span data-stu-id="61454-144">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="61454-145">Ten element odnosi się do <xref:System.ServiceModel.BasicHttpMessageSecurity> .</span><span class="sxs-lookup"><span data-stu-id="61454-145">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="61454-146">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="61454-146">Parent elements</span></span>

|<span data-ttu-id="61454-147">Element</span><span class="sxs-lookup"><span data-stu-id="61454-147">Element</span></span>|<span data-ttu-id="61454-148">Opis</span><span class="sxs-lookup"><span data-stu-id="61454-148">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="61454-149">powiązanie</span><span class="sxs-lookup"><span data-stu-id="61454-149">binding</span></span>|<span data-ttu-id="61454-150">Element Binding elementu [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="61454-150">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|

## <a name="remarks"></a><span data-ttu-id="61454-151">Uwagi</span><span class="sxs-lookup"><span data-stu-id="61454-151">Remarks</span></span>

 <span data-ttu-id="61454-152">Domyślnie komunikat protokołu SOAP nie jest zabezpieczony i klient nie jest uwierzytelniany.</span><span class="sxs-lookup"><span data-stu-id="61454-152">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="61454-153">Ten element umożliwia skonfigurowanie dodatkowych ustawień zabezpieczeń dla `netHttpBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="61454-153">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="61454-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61454-154">See also</span></span>

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [<span data-ttu-id="61454-155">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="61454-155">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="61454-156">Wybieranie typu poświadczeń</span><span class="sxs-lookup"><span data-stu-id="61454-156">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="61454-157">Powiązania</span><span class="sxs-lookup"><span data-stu-id="61454-157">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="61454-158">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="61454-158">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="61454-159">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="61454-159">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
