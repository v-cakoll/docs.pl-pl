---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: 5899c609b3cf52c4a275ba6fb10c5826fcf37f1e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153012"
---
# \<msmqTransportSecurity>
<span data-ttu-id="7bb02-101">Określa ustawienia zabezpieczeń transportu usługi MSMQ dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="7bb02-101">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegration>**](msmqintegration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqTransportSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="7bb02-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="7bb02-102">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bb02-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7bb02-103">Attributes and Elements</span></span>  
 <span data-ttu-id="7bb02-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7bb02-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bb02-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7bb02-105">Attributes</span></span>  
  
|<span data-ttu-id="7bb02-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7bb02-106">Attribute</span></span>|<span data-ttu-id="7bb02-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7bb02-107">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="7bb02-108">Określa, jak wiadomość musi zostać uwierzytelniona przez transport usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="7bb02-108">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="7bb02-109">Jeśli jest ustawiona na `None` , wartość `msmqProtectionLevel` atrybutu musi również być ustawiona na `None` .</span><span class="sxs-lookup"><span data-stu-id="7bb02-109">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="7bb02-110">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="7bb02-110">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7bb02-111">-Brak: brak uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7bb02-111">-   None: No authentication.</span></span><br /><span data-ttu-id="7bb02-112">-Windows: mechanizm uwierzytelniania używa Active Directory, aby uzyskać certyfikat X. 509 dla identyfikatora SID skojarzonego z wiadomością.</span><span class="sxs-lookup"><span data-stu-id="7bb02-112">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="7bb02-113">Ta wartość jest następnie używana do sprawdzenia listy ACL kolejki, aby upewnić się, że użytkownik ma uprawnienia do zapisu w kolejce.</span><span class="sxs-lookup"><span data-stu-id="7bb02-113">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="7bb02-114">-Certificate: kanał pobiera certyfikat z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="7bb02-114">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="7bb02-115">Wartość domyślna to Windows.</span><span class="sxs-lookup"><span data-stu-id="7bb02-115">The default value is Windows.</span></span> <span data-ttu-id="7bb02-116">Ten atrybut jest typu <xref:System.ServiceModel.MsmqAuthenticationMode> .</span><span class="sxs-lookup"><span data-stu-id="7bb02-116">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="7bb02-117">Określa algorytm używany do szyfrowania wiadomości w sieci podczas przesyłania komunikatów między menedżerami kolejki wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7bb02-117">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="7bb02-118">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="7bb02-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7bb02-119">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="7bb02-119">-   RC4Stream</span></span><br /><span data-ttu-id="7bb02-120">-AES</span><span class="sxs-lookup"><span data-stu-id="7bb02-120">-   AES</span></span><br /><br /> <span data-ttu-id="7bb02-121">Wartość domyślna to RC4Stream.</span><span class="sxs-lookup"><span data-stu-id="7bb02-121">The default value is RC4Stream.</span></span> <span data-ttu-id="7bb02-122">Ten atrybut jest typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="7bb02-122">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="7bb02-123">Określa, w jaki sposób wiadomość jest zabezpieczona na poziomie transportu usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="7bb02-123">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="7bb02-124">Szyfrowanie zapewnia integralność komunikatów, podczas gdy EncryptAndSign zapewnia integralność komunikatów i odrzucanie. oznacza to, że wiadomość rzeczywiście pochodzi od nadawcy, a nadawca to osoba, której mówią.</span><span class="sxs-lookup"><span data-stu-id="7bb02-124">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="7bb02-125">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="7bb02-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7bb02-126">-Brak: brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="7bb02-126">-   None: No protection.</span></span><br /><span data-ttu-id="7bb02-127">-Sign: komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="7bb02-127">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="7bb02-128">-EncryptAndSign: komunikaty są szyfrowane i podpisane.</span><span class="sxs-lookup"><span data-stu-id="7bb02-128">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="7bb02-129">Wartość domyślna to Sign.</span><span class="sxs-lookup"><span data-stu-id="7bb02-129">The default value is Sign.</span></span> <span data-ttu-id="7bb02-130">Ten atrybut jest typu <xref:System.Net.Security.ProtectionLevel> .</span><span class="sxs-lookup"><span data-stu-id="7bb02-130">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="7bb02-131">Określa algorytm, który ma być używany podczas obliczania skrótu jako części podpisów.</span><span class="sxs-lookup"><span data-stu-id="7bb02-131">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="7bb02-132">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="7bb02-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7bb02-133">-MD5</span><span class="sxs-lookup"><span data-stu-id="7bb02-133">-   MD5</span></span><br /><span data-ttu-id="7bb02-134">-SHA1</span><span class="sxs-lookup"><span data-stu-id="7bb02-134">-   SHA1</span></span><br /><span data-ttu-id="7bb02-135">-SHA256</span><span class="sxs-lookup"><span data-stu-id="7bb02-135">-   SHA256</span></span><br /><span data-ttu-id="7bb02-136">-SHA512</span><span class="sxs-lookup"><span data-stu-id="7bb02-136">-   SHA512</span></span><br /><br /> <span data-ttu-id="7bb02-137">Wartość domyślna to SHA1.</span><span class="sxs-lookup"><span data-stu-id="7bb02-137">The default value is SHA1.</span></span> <span data-ttu-id="7bb02-138">Ten atrybut jest typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="7bb02-138">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="7bb02-139">Ze względu na kolizje problemów z algorytmem MD5 i algorytmem SHA1 firma Microsoft zaleca SHA256ą lub lepszą.</span><span class="sxs-lookup"><span data-stu-id="7bb02-139">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7bb02-140">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7bb02-140">Child Elements</span></span>  
 <span data-ttu-id="7bb02-141">Brak.</span><span class="sxs-lookup"><span data-stu-id="7bb02-141">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7bb02-142">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7bb02-142">Parent Elements</span></span>  
  
|<span data-ttu-id="7bb02-143">Element</span><span class="sxs-lookup"><span data-stu-id="7bb02-143">Element</span></span>|<span data-ttu-id="7bb02-144">Opis</span><span class="sxs-lookup"><span data-stu-id="7bb02-144">Description</span></span>|  
|-------------|-----------------|  
|[\<msmqIntegration>](msmqintegration.md)|<span data-ttu-id="7bb02-145">Określa ustawienia wymagane do interakcji z nadawcą lub odbiornikiem usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="7bb02-145">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[\<msmqTransport>](msmqtransport.md)|<span data-ttu-id="7bb02-146">Określa właściwości komunikacji kolejkowania dla usługi Windows Communication Foundation (WCF), która używa natywnego protokołu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="7bb02-146">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bb02-147">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7bb02-147">Remarks</span></span>  
 <span data-ttu-id="7bb02-148">Aby uzyskać więcej informacji na temat zabezpieczeń transportu, zobacz [Transport Security](../../../wcf/feature-details/transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="7bb02-148">For more information on transport security, see [Transport Security](../../../wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bb02-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7bb02-149">See also</span></span>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7bb02-150">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="7bb02-150">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="7bb02-151">Transporty</span><span class="sxs-lookup"><span data-stu-id="7bb02-151">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="7bb02-152">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="7bb02-152">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="7bb02-153">Powiązania</span><span class="sxs-lookup"><span data-stu-id="7bb02-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7bb02-154">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="7bb02-154">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7bb02-155">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="7bb02-155">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="7bb02-156">Zabezpieczenia transportu</span><span class="sxs-lookup"><span data-stu-id="7bb02-156">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
