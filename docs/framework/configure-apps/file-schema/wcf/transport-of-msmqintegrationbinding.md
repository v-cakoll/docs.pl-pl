---
title: '&lt;transport&gt; w &lt;msmqIntegrationBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03cd07681c111f51a4ea02ac46354fa9a19f42d3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="lttransportgt-of-ltmsmqintegrationbindinggt"></a><span data-ttu-id="1747b-102">&lt;transport&gt; w &lt;msmqIntegrationBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="1747b-102">&lt;transport&gt; of &lt;msmqIntegrationBinding&gt;</span></span>
<span data-ttu-id="1747b-103">Definiuje ustawienia zabezpieczeń transport integracji usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="1747b-103">Defines the security settings for the Message Queuing integration transport.</span></span>  
  
 <span data-ttu-id="1747b-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1747b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1747b-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="1747b-105">\<bindings></span></span>  
<span data-ttu-id="1747b-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="1747b-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="1747b-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="1747b-107">\<binding></span></span>  
<span data-ttu-id="1747b-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="1747b-108">\<security></span></span>  
<span data-ttu-id="1747b-109">\<transport ></span><span class="sxs-lookup"><span data-stu-id="1747b-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1747b-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="1747b-110">Syntax</span></span>  
  
```xml  
<security>  
    <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
        msmqEncryptionAlgorithm="RC4Stream/AES"  
        msmqProtectionLevel="None/Sign/EncryptAndSign"  
        msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1747b-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1747b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1747b-112">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1747b-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1747b-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1747b-113">Attributes</span></span>  
  
|<span data-ttu-id="1747b-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1747b-114">Attribute</span></span>|<span data-ttu-id="1747b-115">Opis</span><span class="sxs-lookup"><span data-stu-id="1747b-115">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="1747b-116">Określa jak wiadomość musi być uwierzytelniani przez usługę transportową MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1747b-116">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="1747b-117">Jeśli ta wartość jest równa `None`, wartość `msmqProtectionLevel` atrybutu również musi być ustawiona na `None`.</span><span class="sxs-lookup"><span data-stu-id="1747b-117">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="1747b-118">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="1747b-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1747b-119">-Brak: Bez uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="1747b-119">-   None: No authentication.</span></span><br /><span data-ttu-id="1747b-120">-WindowsDomain: Mechanizm uwierzytelniania używa usługi Active Directory, aby uzyskać certyfikat X.509, identyfikator SID skojarzone z wiadomością.</span><span class="sxs-lookup"><span data-stu-id="1747b-120">-   WindowsDomain: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="1747b-121">To jest następnie używany do sprawdzania listy ACL kolejki, aby upewnić się, użytkownik ma uprawnienia do zapisu w kolejce.</span><span class="sxs-lookup"><span data-stu-id="1747b-121">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="1747b-122">-Certyfikat: Kanał pobiera certyfikat z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="1747b-122">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="1747b-123">Wartość domyślna to WindowsDomain.</span><span class="sxs-lookup"><span data-stu-id="1747b-123">The default value is WindowsDomain.</span></span> <span data-ttu-id="1747b-124">Ten atrybut jest typu <xref:System.ServiceModel.MsmqAuthenticationMode>.</span><span class="sxs-lookup"><span data-stu-id="1747b-124">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="1747b-125">Określa algorytm używany do szyfrowania wiadomości w sieci podczas transferu wiadomości między menedżerami kolejki wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1747b-125">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="1747b-126">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="1747b-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1747b-127">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="1747b-127">-   RC4Stream</span></span><br /><span data-ttu-id="1747b-128">-AES</span><span class="sxs-lookup"><span data-stu-id="1747b-128">-   AES</span></span><br /><br /> <span data-ttu-id="1747b-129">Wartość domyślna to RC4Stream.</span><span class="sxs-lookup"><span data-stu-id="1747b-129">The default value is RC4Stream.</span></span> <span data-ttu-id="1747b-130">Ten atrybut jest typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="1747b-130">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="1747b-131">Określa, jak wiadomość jest zabezpieczona na poziomie transportu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1747b-131">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="1747b-132">Szyfrowanie zapewnia integralność wiadomości, gdy EncryptAndSign zapewnia zarówno integralność komunikatów i bez odrzucania; to, że w rzeczywistości pochodzą od nadawcy i jest nadawcy, który mówi się, że jest on.</span><span class="sxs-lookup"><span data-stu-id="1747b-132">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who he says he is.</span></span><br /><br /> <span data-ttu-id="1747b-133">-Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="1747b-133">-   Valid values include the following:</span></span><br /><span data-ttu-id="1747b-134">-Brak: Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="1747b-134">-   None: No protection.</span></span><br /><span data-ttu-id="1747b-135">-Znak: Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="1747b-135">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="1747b-136">-EncryptAndSign: Komunikaty są zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="1747b-136">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="1747b-137">Wartością domyślną jest znak.</span><span class="sxs-lookup"><span data-stu-id="1747b-137">The default value is Sign.</span></span> <span data-ttu-id="1747b-138">Ten atrybut jest typu ProtectionLevel.</span><span class="sxs-lookup"><span data-stu-id="1747b-138">This attribute is of type ProtectionLevel.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="1747b-139">— Określa algorytm używany w obliczeniu skrótu jako części podpisów.</span><span class="sxs-lookup"><span data-stu-id="1747b-139">-   Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="1747b-140">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="1747b-140">Valid values include the following:</span></span><br /><span data-ttu-id="1747b-141">-MD5</span><span class="sxs-lookup"><span data-stu-id="1747b-141">-   MD5</span></span><br /><span data-ttu-id="1747b-142">-SHA1.</span><span class="sxs-lookup"><span data-stu-id="1747b-142">-   SHA1</span></span><br /><span data-ttu-id="1747b-143">-SHA256</span><span class="sxs-lookup"><span data-stu-id="1747b-143">-   SHA256</span></span><br /><span data-ttu-id="1747b-144">-SHA512.</span><span class="sxs-lookup"><span data-stu-id="1747b-144">-   SHA512</span></span><br /><br /> <span data-ttu-id="1747b-145">Wartość domyślna to SHA1.</span><span class="sxs-lookup"><span data-stu-id="1747b-145">The default value is SHA1.</span></span> <span data-ttu-id="1747b-146">Ten atrybut jest typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="1747b-146">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1747b-147">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1747b-147">Child Elements</span></span>  
 <span data-ttu-id="1747b-148">Brak</span><span class="sxs-lookup"><span data-stu-id="1747b-148">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1747b-149">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1747b-149">Parent Elements</span></span>  
  
|<span data-ttu-id="1747b-150">Element</span><span class="sxs-lookup"><span data-stu-id="1747b-150">Element</span></span>|<span data-ttu-id="1747b-151">Opis</span><span class="sxs-lookup"><span data-stu-id="1747b-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1747b-152">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="1747b-152">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="1747b-153">Definiuje ustawienia zabezpieczeń dla powiązania usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1747b-153">Defines the security settings for a MSMQ binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1747b-154">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1747b-154">Remarks</span></span>  
 <span data-ttu-id="1747b-155">Ten element hermetyzuje ustawienia zabezpieczeń dla transport integracji usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="1747b-155">This element encapsulates the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="1747b-156">Ustawienia są takie same, Integracja usługi kolejkowania komunikatów i umieszczonych w kolejce transportów.</span><span class="sxs-lookup"><span data-stu-id="1747b-156">The settings are the same for both the Message Queuing integration and queued transports.</span></span> <span data-ttu-id="1747b-157">Umożliwia on ustawiony tryb uwierzytelniania, algorytmów szyfrowania, Secure Hash Algorithm i poziom ochrony.</span><span class="sxs-lookup"><span data-stu-id="1747b-157">It enables you to set the Authentication Mode, Encryption Algorithm, Secure Hash Algorithm, and Protection Level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1747b-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1747b-158">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [<span data-ttu-id="1747b-159">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="1747b-159">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="1747b-160">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="1747b-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="1747b-161">Powiązania</span><span class="sxs-lookup"><span data-stu-id="1747b-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="1747b-162">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="1747b-162">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="1747b-163">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="1747b-163">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="1747b-164">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="1747b-164">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
