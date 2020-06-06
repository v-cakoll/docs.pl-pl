---
title: <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: c6183a8d27d56c7199b815ccb31b06f983a51b33
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398400"
---
# \<messageSenderAuthentication>
<span data-ttu-id="de425-101">Określa ustawienia uwierzytelniania dla certyfikatu równorzędnego używanego przez nadawcę wiadomości.</span><span class="sxs-lookup"><span data-stu-id="de425-101">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="de425-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="de425-102">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de425-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="de425-103">Attributes and Elements</span></span>  
 <span data-ttu-id="de425-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="de425-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de425-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="de425-105">Attributes</span></span>  
  
|<span data-ttu-id="de425-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="de425-106">Attribute</span></span>|<span data-ttu-id="de425-107">Opis</span><span class="sxs-lookup"><span data-stu-id="de425-107">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="de425-108">Opcjonalne Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="de425-108">Optional enumeration.</span></span> <span data-ttu-id="de425-109">Określa jeden z pięciu trybów używanych do walidacji poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="de425-109">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="de425-110">Ten atrybut jest typu <xref:System.ServiceModel.Security.X509CertificateValidationMode> .</span><span class="sxs-lookup"><span data-stu-id="de425-110">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="de425-111">Jeśli jest ustawiona na `Custom` , `customCertificateValidator` należy również podać wartość.</span><span class="sxs-lookup"><span data-stu-id="de425-111">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="de425-112">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="de425-112">Optional string.</span></span> <span data-ttu-id="de425-113">Określa typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="de425-113">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="de425-114">Ten atrybut musi być ustawiony `certificateValidationMode` , gdy jest ustawiony na `Custom` .</span><span class="sxs-lookup"><span data-stu-id="de425-114">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="de425-115">Ten atrybut jest typu <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="de425-115">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="de425-116">Windows Communication Foundation (WCF) udostępnia domyślny moduł sprawdzania poprawności certyfikatu równorzędnego, który weryfikuje certyfikat równorzędny w magazynie zaufanych osób.</span><span class="sxs-lookup"><span data-stu-id="de425-116">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="de425-117">Sprawdza również, czy certyfikat jest łańcuchem do prawidłowego katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="de425-117">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="de425-118">Możesz zaimplementować niestandardowy moduł sprawdzania poprawności, aby określić inne zachowanie i użyć tego atrybutu, aby wskazać niestandardowy moduł sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="de425-118">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="de425-119">Opcjonalne Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="de425-119">Optional enumeration.</span></span> <span data-ttu-id="de425-120">Określa tryb odwoływania certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="de425-120">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="de425-121">Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> .</span><span class="sxs-lookup"><span data-stu-id="de425-121">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="de425-122">System sprawdza, czy certyfikat równorzędny nie został odwołany, sprawdzając go na liście odwołanych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="de425-122">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="de425-123">Ten test można przeprowadzić przez sprawdzenie w trybie online lub w odniesieniu do buforowanej listy odwołania.</span><span class="sxs-lookup"><span data-stu-id="de425-123">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="de425-124">Sprawdzanie odwołania można wyłączyć, ustawiając ten atrybut na NOCHECK.</span><span class="sxs-lookup"><span data-stu-id="de425-124">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="de425-125">Opcjonalne Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="de425-125">Optional enumeration.</span></span> <span data-ttu-id="de425-126">Określa lokalizację zaufanego magazynu, w której certyfikat równorzędny jest sprawdzany przez system zabezpieczeń WCF.</span><span class="sxs-lookup"><span data-stu-id="de425-126">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="de425-127">Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation> .</span><span class="sxs-lookup"><span data-stu-id="de425-127">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de425-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="de425-128">Child Elements</span></span>  
 <span data-ttu-id="de425-129">Brak.</span><span class="sxs-lookup"><span data-stu-id="de425-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de425-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="de425-130">Parent Elements</span></span>  
  
|<span data-ttu-id="de425-131">Element</span><span class="sxs-lookup"><span data-stu-id="de425-131">Element</span></span>|<span data-ttu-id="de425-132">Opis</span><span class="sxs-lookup"><span data-stu-id="de425-132">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="de425-133">Określa bieżące poświadczenia dla węzła równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="de425-133">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de425-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de425-134">Remarks</span></span>  
 <span data-ttu-id="de425-135">Ten element musi być skonfigurowany, jeśli wybrano opcję Uwierzytelnianie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="de425-135">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="de425-136">W przypadku kanałów wyjściowych każdy komunikat jest podpisywany przy użyciu certyfikatu dostarczonego przez [\<certificate>](certificate-element.md) .</span><span class="sxs-lookup"><span data-stu-id="de425-136">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="de425-137">Wszystkie komunikaty, przed dostarczeniem do aplikacji, są sprawdzane pod kątem poświadczeń komunikatów przy użyciu modułu walidacji określonego przez `customCertificateValidatorType` atrybut tego elementu.</span><span class="sxs-lookup"><span data-stu-id="de425-137">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="de425-138">Moduł sprawdzania poprawności może zaakceptować lub odrzucić poświadczenie.</span><span class="sxs-lookup"><span data-stu-id="de425-138">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de425-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de425-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- [<span data-ttu-id="de425-140">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="de425-140">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="de425-141">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="de425-141">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="de425-142">[Uwierzytelnianie komunikatów kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="de425-142">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="de425-143">[Uwierzytelnianie niestandardowe kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="de425-143">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="de425-144">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="de425-144">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
