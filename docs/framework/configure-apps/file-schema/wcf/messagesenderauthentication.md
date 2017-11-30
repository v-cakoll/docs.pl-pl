---
title: '&lt;messageSenderAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 428dbdc65a4f66e5632e4ded7d7ded0d10b7c9d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltmessagesenderauthenticationgt"></a><span data-ttu-id="a147e-102">&lt;messageSenderAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="a147e-102">&lt;messageSenderAuthentication&gt;</span></span>
<span data-ttu-id="a147e-103">Określa ustawienia uwierzytelniania dla elementu równorzędnego certyfikat używany przez nadawcy wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a147e-103">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
 <span data-ttu-id="a147e-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a147e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a147e-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="a147e-105">\<behaviors></span></span>  
<span data-ttu-id="a147e-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a147e-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="a147e-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="a147e-107">\<behavior></span></span>  
<span data-ttu-id="a147e-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="a147e-108">\<serviceCredentials></span></span>  
<span data-ttu-id="a147e-109">\<peer ></span><span class="sxs-lookup"><span data-stu-id="a147e-109">\<peer></span></span>  
<span data-ttu-id="a147e-110">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="a147e-110">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a147e-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="a147e-111">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication  
   customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
   certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a147e-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a147e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a147e-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a147e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a147e-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a147e-114">Attributes</span></span>  
  
|<span data-ttu-id="a147e-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a147e-115">Attribute</span></span>|<span data-ttu-id="a147e-116">Opis</span><span class="sxs-lookup"><span data-stu-id="a147e-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="a147e-117">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="a147e-117">Optional enumeration.</span></span> <span data-ttu-id="a147e-118">Określa jeden z pięciu trybów używanych do walidacji poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="a147e-118">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="a147e-119">Ten atrybut jest typu <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="a147e-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="a147e-120">Jeśli ustawiono `Custom`, a następnie `customCertificateValidator` należy dostarczyć także.</span><span class="sxs-lookup"><span data-stu-id="a147e-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="a147e-121">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="a147e-121">Optional string.</span></span> <span data-ttu-id="a147e-122">Określa typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="a147e-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="a147e-123">Ten atrybut musi być ustawiane podczas `certificateValidationMode` ma ustawioną wartość `Custom`.</span><span class="sxs-lookup"><span data-stu-id="a147e-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="a147e-124">Ten atrybut jest typu <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="a147e-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="a147e-125">udostępnia element równorzędny domyślny moduł weryfikacji certyfikatów, która sprawdza równorzędnej certyfikatu w magazynie zaufanych osób.</span><span class="sxs-lookup"><span data-stu-id="a147e-125"> provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="a147e-126">Sprawdza także, że certyfikat powiązany prawidłowy katalog główny.</span><span class="sxs-lookup"><span data-stu-id="a147e-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="a147e-127">Można zaimplementować niestandardowego modułu weryfikacji, aby określić różne zachowania i wskaż niestandardowego modułu weryfikacji za pomocą tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a147e-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="a147e-128">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="a147e-128">Optional enumeration.</span></span> <span data-ttu-id="a147e-129">Określa tryb odwołania certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="a147e-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="a147e-130">Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="a147e-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="a147e-131">System sprawdza, czy certyfikatu elementu równorzędnego nie został odwołany przez wyszukiwanie z listy odwołania certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="a147e-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="a147e-132">Tego wyboru można przeprowadzić sprawdzania w trybie online lub z listą odwołania pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="a147e-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="a147e-133">Sprawdzanie odwołania można wyłączyć, ustawiając tego atrybutu na NoCheck.</span><span class="sxs-lookup"><span data-stu-id="a147e-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="a147e-134">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="a147e-134">Optional enumeration.</span></span> <span data-ttu-id="a147e-135">Określa lokalizację magazynu zaufanych, gdy certyfikat elementu równorzędnego jest zweryfikowany przez [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zabezpieczeń systemu.</span><span class="sxs-lookup"><span data-stu-id="a147e-135">Specifies the trusted store location where the peer certificate is validated by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] security system.</span></span> <span data-ttu-id="a147e-136">Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="a147e-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a147e-137">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a147e-137">Child Elements</span></span>  
 <span data-ttu-id="a147e-138">Brak.</span><span class="sxs-lookup"><span data-stu-id="a147e-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a147e-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a147e-139">Parent Elements</span></span>  
  
|<span data-ttu-id="a147e-140">Element</span><span class="sxs-lookup"><span data-stu-id="a147e-140">Element</span></span>|<span data-ttu-id="a147e-141">Opis</span><span class="sxs-lookup"><span data-stu-id="a147e-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a147e-142">\<peer ></span><span class="sxs-lookup"><span data-stu-id="a147e-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="a147e-143">Określa bieżące poświadczenia dla węzła równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="a147e-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a147e-144">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a147e-144">Remarks</span></span>  
 <span data-ttu-id="a147e-145">Ten element musi być skonfigurowany, jeśli wybrano opcję uwierzytelniania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a147e-145">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="a147e-146">Dane wyjściowe kanałów, każdy komunikat jest podpisany za pomocą certyfikatu dostarczonego przez [ \<certyfikatu >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="a147e-146">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="a147e-147">Wszystkie komunikaty przed dostarczeniem do aplikacji, są porównywane z poświadczeniami komunikatu za pomocą modułu sprawdzania poprawności określonego przez `customCertificateValidatorType` atrybutu tego elementu.</span><span class="sxs-lookup"><span data-stu-id="a147e-147">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="a147e-148">Moduł weryfikacji można zaakceptowanie lub odrzucenie poświadczenie.</span><span class="sxs-lookup"><span data-stu-id="a147e-148">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a147e-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a147e-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 [<span data-ttu-id="a147e-150">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="a147e-150">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="a147e-151">Sieci peer-to-Peer</span><span class="sxs-lookup"><span data-stu-id="a147e-151">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="a147e-152">Uwierzytelnianie wiadomości kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="a147e-152">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="a147e-153">Niestandardowe uwierzytelnianie kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="a147e-153">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="a147e-154">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="a147e-154">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
