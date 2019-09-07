---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: f295fe48e194611c80b78c0c23ab3e66ea1c0b64
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400497"
---
# <a name="clientcredentials"></a><span data-ttu-id="ff033-101">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="ff033-101">\<clientCredentials></span></span>
<span data-ttu-id="ff033-102">Określa poświadczenia używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="ff033-102">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
<span data-ttu-id="ff033-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ff033-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ff033-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ff033-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ff033-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ff033-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="ff033-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ff033-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="ff033-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ff033-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="ff033-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Obiekt clientCredentials >**</span><span class="sxs-lookup"><span data-stu-id="ff033-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCredentials>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff033-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff033-109">Syntax</span></span>  
  
```xml  
<clientCredentials type="String"
                   supportInteractive="Boolean" >
  <clientCertificate>
  </clientCertificate>
  <digest>
  </digest>
  <isuedToken>
  </isuedToken>
  <peer>
  </peer>
  <serviceCertificate>
  </serviceCertificate>
  <windowsAuthentication>
  </windowsAuthentication>
</clientCredentials>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff033-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ff033-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ff033-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ff033-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff033-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ff033-112">Attributes</span></span>  
  
|<span data-ttu-id="ff033-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ff033-113">Attribute</span></span>|<span data-ttu-id="ff033-114">Opis</span><span class="sxs-lookup"><span data-stu-id="ff033-114">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="ff033-115">Wartość logiczna określająca, czy użytkownik interaktywny może uczestniczyć w wyborze poświadczenia klienta w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ff033-115">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="ff033-116">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="ff033-116">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="ff033-117">Ciąg określający typ tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ff033-117">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff033-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ff033-118">Child Elements</span></span>  
  
|<span data-ttu-id="ff033-119">Element</span><span class="sxs-lookup"><span data-stu-id="ff033-119">Element</span></span>|<span data-ttu-id="ff033-120">Opis</span><span class="sxs-lookup"><span data-stu-id="ff033-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff033-121">\<> clientCertificate</span><span class="sxs-lookup"><span data-stu-id="ff033-121">\<clientCertificate></span></span>](clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="ff033-122">Określa certyfikat używany do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="ff033-122">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="ff033-123">Ten element jest typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="ff033-123">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="ff033-124">\<httpDigest></span><span class="sxs-lookup"><span data-stu-id="ff033-124">\<httpDigest></span></span>](httpdigest-element.md)|<span data-ttu-id="ff033-125">Określa skrót używany do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="ff033-125">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="ff033-126">Ten element jest typu <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="ff033-126">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="ff033-127">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="ff033-127">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="ff033-128">Określa niestandardowy typ tokenu używany do uwierzytelniania klienta w usłudze bezpiecznego tokenu (STS).</span><span class="sxs-lookup"><span data-stu-id="ff033-128">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="ff033-129">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="ff033-129">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="ff033-130">\<> elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="ff033-130">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="ff033-131">Określa bieżące poświadczenie elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="ff033-131">Specifies a current peer credential.</span></span> <span data-ttu-id="ff033-132">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="ff033-132">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="ff033-133">\<> serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="ff033-133">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="ff033-134">Określa certyfikat używany do uwierzytelniania usługi na kliencie i udostępnia strukturę do ustawiania opcji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="ff033-134">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="ff033-135">Ten certyfikat musi być dostarczony z usługi do klienta jako poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="ff033-135">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="ff033-136">Ten element jest typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="ff033-136">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="ff033-137">\<windows></span><span class="sxs-lookup"><span data-stu-id="ff033-137">\<windows></span></span>](windows-of-clientcredentials-element.md)|<span data-ttu-id="ff033-138">Określa poświadczenie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ff033-138">Specifies a Windows credential.</span></span> <span data-ttu-id="ff033-139">Wartość domyślna to poświadczenie bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="ff033-139">The default is the credential of the current thread.</span></span> <span data-ttu-id="ff033-140">Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="ff033-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ff033-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ff033-141">Parent Elements</span></span>  
  
|<span data-ttu-id="ff033-142">Element</span><span class="sxs-lookup"><span data-stu-id="ff033-142">Element</span></span>|<span data-ttu-id="ff033-143">Opis</span><span class="sxs-lookup"><span data-stu-id="ff033-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff033-144">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="ff033-144">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ff033-145">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ff033-145">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff033-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff033-146">Remarks</span></span>  
 <span data-ttu-id="ff033-147">Poświadczenia klienta służą do uwierzytelniania klienta programu w przypadku, gdy wymagane jest uwierzytelnianie wzajemne.</span><span class="sxs-lookup"><span data-stu-id="ff033-147">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="ff033-148">Ta sekcja konfiguracji może również służyć do określania certyfikatów usługi dla scenariuszy, w których klient musi zabezpieczyć komunikaty do usługi za pomocą certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="ff033-148">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff033-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff033-149">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="ff033-150">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ff033-150">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="ff033-151">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="ff033-151">Securing Clients</span></span>](../../../wcf/securing-clients.md)
