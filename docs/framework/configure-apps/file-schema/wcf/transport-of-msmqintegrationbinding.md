---
title: <transport> dla <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: 1cb165fed9266307335482166116c4c1d62efe7e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152960"
---
# <a name="transport-of-msmqintegrationbinding"></a><span data-ttu-id="6d7c7-102">\<transport> dla \<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="6d7c7-102">\<transport> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="6d7c7-103">Definiuje ustawienia zabezpieczeń dla transportu integracji usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-103">Defines the security settings for the Message Queuing integration transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="6d7c7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d7c7-104">Syntax</span></span>  
  
```xml  
<security>
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d7c7-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6d7c7-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6d7c7-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d7c7-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6d7c7-107">Attributes</span></span>  
  
|<span data-ttu-id="6d7c7-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6d7c7-108">Attribute</span></span>|<span data-ttu-id="6d7c7-109">Opis</span><span class="sxs-lookup"><span data-stu-id="6d7c7-109">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="6d7c7-110">Określa, jak wiadomość musi zostać uwierzytelniona przez transport usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-110">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="6d7c7-111">Jeśli jest ustawiona na `None` , wartość `msmqProtectionLevel` atrybutu musi również być ustawiona na `None` .</span><span class="sxs-lookup"><span data-stu-id="6d7c7-111">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="6d7c7-112">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="6d7c7-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6d7c7-113">-Brak: brak uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-113">-   None: No authentication.</span></span><br /><span data-ttu-id="6d7c7-114">-WindowsDomain: mechanizm uwierzytelniania używa Active Directory, aby uzyskać certyfikat X. 509 dla identyfikatora SID skojarzonego z wiadomością.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-114">-   WindowsDomain: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="6d7c7-115">Ta wartość jest następnie używana do sprawdzenia listy ACL kolejki, aby upewnić się, że użytkownik ma uprawnienia do zapisu w kolejce.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-115">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="6d7c7-116">-Certificate: kanał pobiera certyfikat z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-116">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="6d7c7-117">Wartość domyślna to WindowsDomain.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-117">The default value is WindowsDomain.</span></span> <span data-ttu-id="6d7c7-118">Ten atrybut jest typu <xref:System.ServiceModel.MsmqAuthenticationMode> .</span><span class="sxs-lookup"><span data-stu-id="6d7c7-118">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="6d7c7-119">Określa algorytm używany do szyfrowania wiadomości w sieci podczas przesyłania komunikatów między menedżerami kolejki wiadomości.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-119">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="6d7c7-120">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="6d7c7-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6d7c7-121">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="6d7c7-121">-   RC4Stream</span></span><br /><span data-ttu-id="6d7c7-122">-AES</span><span class="sxs-lookup"><span data-stu-id="6d7c7-122">-   AES</span></span><br /><br /> <span data-ttu-id="6d7c7-123">Wartość domyślna to RC4Stream.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-123">The default value is RC4Stream.</span></span> <span data-ttu-id="6d7c7-124">Ten atrybut jest typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="6d7c7-124">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="6d7c7-125">Określa, w jaki sposób wiadomość jest zabezpieczona na poziomie transportu usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-125">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="6d7c7-126">Szyfrowanie zapewnia integralność komunikatów, podczas gdy EncryptAndSign zapewnia integralność komunikatów i odrzucanie. oznacza to, że wiadomość rzeczywiście pochodzi od nadawcy, a nadawca to osoba, której mówią.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-126">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span><br /><br /> <span data-ttu-id="6d7c7-127">-Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="6d7c7-127">-   Valid values include the following:</span></span><br /><span data-ttu-id="6d7c7-128">-Brak: brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-128">-   None: No protection.</span></span><br /><span data-ttu-id="6d7c7-129">-Sign: komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-129">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="6d7c7-130">-EncryptAndSign: komunikaty są szyfrowane i podpisane.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-130">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="6d7c7-131">Wartość domyślna to Sign.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-131">The default value is Sign.</span></span> <span data-ttu-id="6d7c7-132">Ten atrybut jest typu ProtectionLevel.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-132">This attribute is of type ProtectionLevel.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="6d7c7-133">-Określa algorytm, który ma być używany podczas obliczania skrótu jako części podpisów.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-133">-   Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="6d7c7-134">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="6d7c7-134">Valid values include the following:</span></span><br /><span data-ttu-id="6d7c7-135">-MD5</span><span class="sxs-lookup"><span data-stu-id="6d7c7-135">-   MD5</span></span><br /><span data-ttu-id="6d7c7-136">-SHA1</span><span class="sxs-lookup"><span data-stu-id="6d7c7-136">-   SHA1</span></span><br /><span data-ttu-id="6d7c7-137">-SHA256</span><span class="sxs-lookup"><span data-stu-id="6d7c7-137">-   SHA256</span></span><br /><span data-ttu-id="6d7c7-138">-SHA512</span><span class="sxs-lookup"><span data-stu-id="6d7c7-138">-   SHA512</span></span><br /><br /> <span data-ttu-id="6d7c7-139">Wartość domyślna to SHA1.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-139">The default value is SHA1.</span></span> <span data-ttu-id="6d7c7-140">Ten atrybut jest typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="6d7c7-140">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="6d7c7-141">Ze względu na kolizje problemów z algorytmem MD5 i algorytmem SHA1 firma Microsoft zaleca SHA256ą lub lepszą.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-141">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d7c7-142">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6d7c7-142">Child Elements</span></span>  
 <span data-ttu-id="6d7c7-143">Brak</span><span class="sxs-lookup"><span data-stu-id="6d7c7-143">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6d7c7-144">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6d7c7-144">Parent Elements</span></span>  
  
|<span data-ttu-id="6d7c7-145">Element</span><span class="sxs-lookup"><span data-stu-id="6d7c7-145">Element</span></span>|<span data-ttu-id="6d7c7-146">Opis</span><span class="sxs-lookup"><span data-stu-id="6d7c7-146">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="6d7c7-147">Definiuje ustawienia zabezpieczeń dla powiązania usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-147">Defines the security settings for a MSMQ binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d7c7-148">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d7c7-148">Remarks</span></span>  
 <span data-ttu-id="6d7c7-149">Ten element hermetyzuje ustawienia zabezpieczeń dla transportu integracji usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-149">This element encapsulates the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="6d7c7-150">Te ustawienia są takie same dla integracji usługi kolejkowania komunikatów i transportów znajdujących się w kolejce.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-150">The settings are the same for both the Message Queuing integration and queued transports.</span></span> <span data-ttu-id="6d7c7-151">Umożliwia ustawienie trybu uwierzytelniania, algorytmu szyfrowania, algorytmu bezpiecznego skrótu i poziomu ochrony.</span><span class="sxs-lookup"><span data-stu-id="6d7c7-151">It enables you to set the Authentication Mode, Encryption Algorithm, Secure Hash Algorithm, and Protection Level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d7c7-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d7c7-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="6d7c7-153">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="6d7c7-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6d7c7-154">Powiązania</span><span class="sxs-lookup"><span data-stu-id="6d7c7-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6d7c7-155">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="6d7c7-155">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6d7c7-156">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="6d7c7-156">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
