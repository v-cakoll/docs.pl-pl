---
title: '&lt;msmqTransportSecurity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 0ece4395c574a4d6bc9399788ad3fb513cb86379
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltmsmqtransportsecuritygt"></a><span data-ttu-id="720eb-102">&lt;msmqTransportSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="720eb-102">&lt;msmqTransportSecurity&gt;</span></span>
<span data-ttu-id="720eb-103">Określa ustawienia zabezpieczenia transportu MSMQ dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="720eb-103">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
 <span data-ttu-id="720eb-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="720eb-104">\<system.serviceModel></span></span>  
<span data-ttu-id="720eb-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="720eb-105">\<bindings></span></span>  
<span data-ttu-id="720eb-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="720eb-106">\<customBinding></span></span>  
<span data-ttu-id="720eb-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="720eb-107">\<binding></span></span>  
<span data-ttu-id="720eb-108">\<msmqIntegration ></span><span class="sxs-lookup"><span data-stu-id="720eb-108">\<msmqIntegration></span></span>  
<span data-ttu-id="720eb-109">\<msmqTransportSecurity ></span><span class="sxs-lookup"><span data-stu-id="720eb-109">\<msmqTransportSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="720eb-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="720eb-110">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity>  
   msmqAuthenticationMode="None/Windows/Certificate"  
   msmqEncryptionAlgorithm="RC4Stream/AES"  
   msmqProtectionLevel="None/Sign/EncryptAndSign"  
   msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
</msmqTransportSecurity>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="720eb-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="720eb-111">Attributes and Elements</span></span>  
 <span data-ttu-id="720eb-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="720eb-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="720eb-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="720eb-113">Attributes</span></span>  
  
|<span data-ttu-id="720eb-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="720eb-114">Attribute</span></span>|<span data-ttu-id="720eb-115">Opis</span><span class="sxs-lookup"><span data-stu-id="720eb-115">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="720eb-116">Określa jak wiadomość musi być uwierzytelniani przez usługę transportową MSMQ.</span><span class="sxs-lookup"><span data-stu-id="720eb-116">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="720eb-117">Jeśli ta wartość jest równa `None`, wartość `msmqProtectionLevel` atrybutu również musi być ustawiona na `None`.</span><span class="sxs-lookup"><span data-stu-id="720eb-117">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="720eb-118">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="720eb-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="720eb-119">-Brak: Bez uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="720eb-119">-   None: No authentication.</span></span><br /><span data-ttu-id="720eb-120">-Windows: Mechanizm uwierzytelniania używa usługi Active Directory, aby uzyskać certyfikat X.509, identyfikator SID skojarzone z wiadomością.</span><span class="sxs-lookup"><span data-stu-id="720eb-120">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="720eb-121">To jest następnie używany do sprawdzania listy ACL kolejki, aby upewnić się, użytkownik ma uprawnienia do zapisu w kolejce.</span><span class="sxs-lookup"><span data-stu-id="720eb-121">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="720eb-122">-Certyfikat: Kanał pobiera certyfikat z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="720eb-122">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="720eb-123">Wartość domyślna to Windows.</span><span class="sxs-lookup"><span data-stu-id="720eb-123">The default value is Windows.</span></span> <span data-ttu-id="720eb-124">Ten atrybut jest typu <xref:System.ServiceModel.MsmqAuthenticationMode>.</span><span class="sxs-lookup"><span data-stu-id="720eb-124">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="720eb-125">Określa algorytm używany do szyfrowania wiadomości w sieci podczas transferu wiadomości między menedżerami kolejki wiadomości.</span><span class="sxs-lookup"><span data-stu-id="720eb-125">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="720eb-126">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="720eb-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="720eb-127">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="720eb-127">-   RC4Stream</span></span><br /><span data-ttu-id="720eb-128">-AES</span><span class="sxs-lookup"><span data-stu-id="720eb-128">-   AES</span></span><br /><br /> <span data-ttu-id="720eb-129">Wartość domyślna to RC4Stream.</span><span class="sxs-lookup"><span data-stu-id="720eb-129">The default value is RC4Stream.</span></span> <span data-ttu-id="720eb-130">Ten atrybut jest typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="720eb-130">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="720eb-131">Określa, jak wiadomość jest zabezpieczona na poziomie transportu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="720eb-131">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="720eb-132">Szyfrowanie zapewnia integralność wiadomości, gdy EncryptAndSign zapewnia zarówno integralność komunikatów i bez odrzucania; to, że w rzeczywistości pochodzą od nadawcy i jest nadawcy, który mówi się, że jest on.</span><span class="sxs-lookup"><span data-stu-id="720eb-132">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="720eb-133">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="720eb-133">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="720eb-134">-Brak: Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="720eb-134">-   None: No protection.</span></span><br /><span data-ttu-id="720eb-135">-Znak: Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="720eb-135">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="720eb-136">-EncryptAndSign: Komunikaty są zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="720eb-136">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="720eb-137">Wartością domyślną jest znak.</span><span class="sxs-lookup"><span data-stu-id="720eb-137">The default value is Sign.</span></span> <span data-ttu-id="720eb-138">Ten atrybut jest typu <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="720eb-138">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="720eb-139">Określa algorytm używany w obliczeniu skrótu jako części podpisów.</span><span class="sxs-lookup"><span data-stu-id="720eb-139">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="720eb-140">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="720eb-140">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="720eb-141">-MD5</span><span class="sxs-lookup"><span data-stu-id="720eb-141">-   MD5</span></span><br /><span data-ttu-id="720eb-142">-SHA1.</span><span class="sxs-lookup"><span data-stu-id="720eb-142">-   SHA1</span></span><br /><span data-ttu-id="720eb-143">-SHA256</span><span class="sxs-lookup"><span data-stu-id="720eb-143">-   SHA256</span></span><br /><span data-ttu-id="720eb-144">-SHA512.</span><span class="sxs-lookup"><span data-stu-id="720eb-144">-   SHA512</span></span><br /><br /> <span data-ttu-id="720eb-145">Wartość domyślna to SHA1.</span><span class="sxs-lookup"><span data-stu-id="720eb-145">The default value is SHA1.</span></span> <span data-ttu-id="720eb-146">Ten atrybut jest typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="720eb-146">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="720eb-147">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="720eb-147">Child Elements</span></span>  
 <span data-ttu-id="720eb-148">Brak.</span><span class="sxs-lookup"><span data-stu-id="720eb-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="720eb-149">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="720eb-149">Parent Elements</span></span>  
  
|<span data-ttu-id="720eb-150">Element</span><span class="sxs-lookup"><span data-stu-id="720eb-150">Element</span></span>|<span data-ttu-id="720eb-151">Opis</span><span class="sxs-lookup"><span data-stu-id="720eb-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="720eb-152">\<msmqIntegration ></span><span class="sxs-lookup"><span data-stu-id="720eb-152">\<msmqIntegration></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegration.md)|<span data-ttu-id="720eb-153">Określa ustawienia wymagane do interakcji z usługi kolejkowania komunikatów (MSMQ) nadawcy i adresata.</span><span class="sxs-lookup"><span data-stu-id="720eb-153">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[<span data-ttu-id="720eb-154">\<msmqTransport ></span><span class="sxs-lookup"><span data-stu-id="720eb-154">\<msmqTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqtransport.md)|<span data-ttu-id="720eb-155">Określa właściwości kolejkowania komunikacji usługi Windows Communication Foundation (WCF), który korzysta z natywnego protokołu usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="720eb-155">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="720eb-156">Uwagi</span><span class="sxs-lookup"><span data-stu-id="720eb-156">Remarks</span></span>  
 <span data-ttu-id="720eb-157">Aby uzyskać więcej informacji dotyczących zabezpieczeń transportu, zobacz [zabezpieczeń transportu](../../../../../docs/framework/wcf/feature-details/transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="720eb-157">For more information on transport security, see [Transport Security](../../../../../docs/framework/wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="720eb-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="720eb-158">See Also</span></span>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="720eb-159">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="720eb-159">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="720eb-160">Transporty</span><span class="sxs-lookup"><span data-stu-id="720eb-160">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="720eb-161">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="720eb-161">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="720eb-162">Powiązania</span><span class="sxs-lookup"><span data-stu-id="720eb-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="720eb-163">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="720eb-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="720eb-164">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="720eb-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="720eb-165">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="720eb-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="720eb-166">Zabezpieczenia transportu</span><span class="sxs-lookup"><span data-stu-id="720eb-166">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)
