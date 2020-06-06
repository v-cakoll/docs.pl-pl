---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 90a34a4a52b4c7a2e67d733fecba132818cac4fc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399645"
---
# \<serviceCredentials>
<span data-ttu-id="155cd-101">Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi i ustawień związanych z walidacją poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="155cd-101">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="155cd-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="155cd-102">Syntax</span></span>  
  
```xml  
<serviceCredentials type="String">
  <clientCertificate>
  </clientCertificate>
  <issuedTokenAuthentication>
  </issuedTokenAuthentication>
  <peer>
  </peer>
  <secureConversationAuthentication>
  </secureConversationAuthentication>
  <serviceCertificate>
  </serviceCertificate>
  <userNameAuthentication>
  </userNameAuthentication>
  <windowsAuthentication>
  </windowsAuthentication>
</serviceCredentials>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="155cd-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="155cd-103">Attributes and Elements</span></span>  
 <span data-ttu-id="155cd-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="155cd-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="155cd-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="155cd-105">Attributes</span></span>  
  
|<span data-ttu-id="155cd-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="155cd-106">Attribute</span></span>|<span data-ttu-id="155cd-107">Opis</span><span class="sxs-lookup"><span data-stu-id="155cd-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="155cd-108">Ciąg określający typ tego elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="155cd-108">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="155cd-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="155cd-109">Child Elements</span></span>  
  
|<span data-ttu-id="155cd-110">Element</span><span class="sxs-lookup"><span data-stu-id="155cd-110">Element</span></span>|<span data-ttu-id="155cd-111">Opis</span><span class="sxs-lookup"><span data-stu-id="155cd-111">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="155cd-112">Określa certyfikat, który ma być używany, gdy certyfikat klienta jest dostępny poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="155cd-112">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="155cd-113">Ten element określa również ustawienia weryfikacji certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="155cd-113">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="155cd-114">Ten element jest typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="155cd-114">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="155cd-115">Określa bieżący token wystawiony dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="155cd-115">Specifies the current issued token for this service.</span></span> <span data-ttu-id="155cd-116">Ten element jest typu <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="155cd-116">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="155cd-117">Określa bieżące poświadczenia dla węzła równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="155cd-117">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="155cd-118">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerCredentialElement> .</span><span class="sxs-lookup"><span data-stu-id="155cd-118">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<secureConversationAuthentication>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="155cd-119">Określa bieżące poświadczenia dla bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="155cd-119">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="155cd-120">Ten element jest typu <xref:System.ServiceModel.Configuration.SecureConversationServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="155cd-120">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="155cd-121">Określa certyfikat używany przez usługę do zidentyfikowania siebie.</span><span class="sxs-lookup"><span data-stu-id="155cd-121">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="155cd-122">Ten element jest typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="155cd-122">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[\<userNameAuthentication>](usernameauthentication.md)|<span data-ttu-id="155cd-123">Określa ustawienia dla walidacji hasła użytkownika.</span><span class="sxs-lookup"><span data-stu-id="155cd-123">Specifies the settings for username password validation.</span></span> <span data-ttu-id="155cd-124">Ten element jest typu <xref:System.ServiceModel.Configuration.UserNameServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="155cd-124">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[\<windowsAuthentication>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="155cd-125">Określa ustawienia weryfikacji poświadczeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="155cd-125">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="155cd-126">Ten element jest typu <xref:System.ServiceModel.Configuration.WindowsServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="155cd-126">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="155cd-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="155cd-127">Parent Elements</span></span>  
  
|<span data-ttu-id="155cd-128">Element</span><span class="sxs-lookup"><span data-stu-id="155cd-128">Element</span></span>|<span data-ttu-id="155cd-129">Opis</span><span class="sxs-lookup"><span data-stu-id="155cd-129">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="155cd-130">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="155cd-130">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="155cd-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="155cd-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="155cd-132">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="155cd-132">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
