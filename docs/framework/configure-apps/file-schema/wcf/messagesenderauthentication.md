---
title: '&lt;messageSenderAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: 8a3beb42d1064e6c6629014369628248b4cd5c8d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43553800"
---
# <a name="ltmessagesenderauthenticationgt"></a><span data-ttu-id="bc72b-102">&lt;messageSenderAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="bc72b-102">&lt;messageSenderAuthentication&gt;</span></span>
<span data-ttu-id="bc72b-103">Określa ustawienia uwierzytelniania dla elementów równorzędnych certyfikat używany przez nadawcy wiadomości.</span><span class="sxs-lookup"><span data-stu-id="bc72b-103">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
 <span data-ttu-id="bc72b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bc72b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bc72b-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="bc72b-105">\<behaviors></span></span>  
<span data-ttu-id="bc72b-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="bc72b-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="bc72b-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="bc72b-107">\<behavior></span></span>  
<span data-ttu-id="bc72b-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="bc72b-108">\<serviceCredentials></span></span>  
<span data-ttu-id="bc72b-109">\<elementu równorzędnego ></span><span class="sxs-lookup"><span data-stu-id="bc72b-109">\<peer></span></span>  
<span data-ttu-id="bc72b-110">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="bc72b-110">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc72b-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc72b-111">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication  
   customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
   certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc72b-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bc72b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="bc72b-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bc72b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc72b-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bc72b-114">Attributes</span></span>  
  
|<span data-ttu-id="bc72b-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bc72b-115">Attribute</span></span>|<span data-ttu-id="bc72b-116">Opis</span><span class="sxs-lookup"><span data-stu-id="bc72b-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="bc72b-117">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="bc72b-117">Optional enumeration.</span></span> <span data-ttu-id="bc72b-118">Określa jedno z pięciu trybów używanych do walidacji poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="bc72b-118">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="bc72b-119">Ten atrybut jest typu <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="bc72b-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="bc72b-120">Jeśli ustawiono `Custom`, a następnie `customCertificateValidator` musi również zostać dostarczony.</span><span class="sxs-lookup"><span data-stu-id="bc72b-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="bc72b-121">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="bc72b-121">Optional string.</span></span> <span data-ttu-id="bc72b-122">Określa typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="bc72b-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="bc72b-123">Ten atrybut musi być ustawiane podczas `certificateValidationMode` ustawiono `Custom`.</span><span class="sxs-lookup"><span data-stu-id="bc72b-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="bc72b-124">Ten atrybut jest typu <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="bc72b-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="bc72b-125">Windows Communication Foundation (WCF) zapewnia elementu równorzędnego domyślny moduł weryfikacji certyfikatów samodzielną sprawdzającą równorzędnej certyfikatu w magazynie zaufanych osób.</span><span class="sxs-lookup"><span data-stu-id="bc72b-125">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="bc72b-126">Sprawdza także, że łączy się łańcuchem Certyfikat prawidłowy główny.</span><span class="sxs-lookup"><span data-stu-id="bc72b-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="bc72b-127">Możesz zaimplementować niestandardowego modułu weryfikacji, aby określić różne zachowania i użyj tego atrybutu, aby wskazywał niestandardowego modułu weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="bc72b-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="bc72b-128">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="bc72b-128">Optional enumeration.</span></span> <span data-ttu-id="bc72b-129">Określa tryb odwołania certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="bc72b-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="bc72b-130">Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="bc72b-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="bc72b-131">System sprawdza certyfikat elementu równorzędnego nie został odwołany wyszukiwanie w listę odwołanych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="bc72b-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="bc72b-132">Można wykonać ten test, sprawdzając w trybie online lub względem listę odwołanych pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="bc72b-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="bc72b-133">Sprawdzanie odwołań może być wyłączona przez ustawienie tego atrybutu na NoCheck.</span><span class="sxs-lookup"><span data-stu-id="bc72b-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="bc72b-134">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="bc72b-134">Optional enumeration.</span></span> <span data-ttu-id="bc72b-135">Określa lokalizację magazynu zaufanych, gdzie certyfikat równorzędnej zostanie zweryfikowany przez system zabezpieczeń programu WCF.</span><span class="sxs-lookup"><span data-stu-id="bc72b-135">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="bc72b-136">Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="bc72b-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc72b-137">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bc72b-137">Child Elements</span></span>  
 <span data-ttu-id="bc72b-138">Brak.</span><span class="sxs-lookup"><span data-stu-id="bc72b-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc72b-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bc72b-139">Parent Elements</span></span>  
  
|<span data-ttu-id="bc72b-140">Element</span><span class="sxs-lookup"><span data-stu-id="bc72b-140">Element</span></span>|<span data-ttu-id="bc72b-141">Opis</span><span class="sxs-lookup"><span data-stu-id="bc72b-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc72b-142">\<elementu równorzędnego ></span><span class="sxs-lookup"><span data-stu-id="bc72b-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="bc72b-143">Określa bieżące poświadczenia dla węzła równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="bc72b-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc72b-144">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc72b-144">Remarks</span></span>  
 <span data-ttu-id="bc72b-145">Ten element musi być skonfigurowany, jeśli wybrano opcję uwierzytelniania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="bc72b-145">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="bc72b-146">Dla kanałów danych wyjściowych, każdy komunikat jest podpisany przy użyciu certyfikatu dostarczonego przez [ \<certyfikatu >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="bc72b-146">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="bc72b-147">Wszystkie komunikaty zanim dostarczane do aplikacji, są porównywane z poświadczeniami komunikatu przy użyciu modułu sprawdzania poprawności określonego przez `customCertificateValidatorType` atrybutu tego elementu.</span><span class="sxs-lookup"><span data-stu-id="bc72b-147">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="bc72b-148">Moduł weryfikacji można zaakceptować lub odrzucić poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="bc72b-148">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc72b-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc72b-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 [<span data-ttu-id="bc72b-150">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="bc72b-150">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="bc72b-151">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="bc72b-151">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="bc72b-152">Uwierzytelnianie wiadomości z kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="bc72b-152">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="bc72b-153">Kanał elementu równorzędnego uwierzytelniania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="bc72b-153">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="bc72b-154">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="bc72b-154">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
