---
title: <transport> dla <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: ede4103f9c8f2f73ac34036fe7a58242e32350e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934689"
---
# <a name="transport-of-netmsmqbinding"></a><span data-ttu-id="ccf4a-102">\<Transport > \<usługi msmqbinding ></span><span class="sxs-lookup"><span data-stu-id="ccf4a-102">\<transport> of \<netMsmqBinding></span></span>
<span data-ttu-id="ccf4a-103">Definiuje ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-103">Defines the transport security settings.</span></span>  
  
 <span data-ttu-id="ccf4a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ccf4a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ccf4a-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="ccf4a-105">\<bindings></span></span>  
<span data-ttu-id="ccf4a-106">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="ccf4a-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="ccf4a-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="ccf4a-107">\<binding></span></span>  
<span data-ttu-id="ccf4a-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ccf4a-108">\<security></span></span>  
<span data-ttu-id="ccf4a-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="ccf4a-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccf4a-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="ccf4a-110">Syntax</span></span>  
  
```xml  
<netMsmqBinding>
  <binding>
    <security>
      <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    </security>
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ccf4a-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ccf4a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ccf4a-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ccf4a-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ccf4a-113">Attributes</span></span>  
  
|<span data-ttu-id="ccf4a-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ccf4a-114">Attribute</span></span>|<span data-ttu-id="ccf4a-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ccf4a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ccf4a-116">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="ccf4a-116">msmqAuthenticationMode</span></span>|<span data-ttu-id="ccf4a-117">Określa, jak wiadomość musi zostać uwierzytelniona przez transport usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-117">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="ccf4a-118">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="ccf4a-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ccf4a-119">Dawaj Brak uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-119">-   None: No authentication.</span></span><br /><span data-ttu-id="ccf4a-120">- WindowsDomain: Mechanizm uwierzytelniania używa Active Directory do pobierania certyfikatu X. 509 dla identyfikatora zabezpieczeń skojarzonego z wiadomością.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-120">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="ccf4a-121">Ta wartość jest następnie używana do sprawdzenia listy ACL kolejki, aby upewnić się, że użytkownik ma uprawnienie do zapisu dla kolejki.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-121">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="ccf4a-122">Certyfikatu Kanał pobiera certyfikat z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-122">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="ccf4a-123">Wartość domyślna to `WindowsDomain`.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-123">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="ccf4a-124">Jeśli ten atrybut jest ustawiony na `None` `msmqProtectionLevel` , atrybut musi również być ustawiony na `None`.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-124">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="ccf4a-125">Ten atrybut nie ma typu<xref:System.ServiceModel.MsmqAuthenticationMode></span><span class="sxs-lookup"><span data-stu-id="ccf4a-125">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="ccf4a-126">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="ccf4a-126">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="ccf4a-127">Określa algorytm używany do szyfrowania wiadomości w sieci podczas przesyłania komunikatów między menedżerami kolejki wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-127">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="ccf4a-128">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="ccf4a-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ccf4a-129">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="ccf4a-129">-   RC4Stream</span></span><br /><span data-ttu-id="ccf4a-130">-AES</span><span class="sxs-lookup"><span data-stu-id="ccf4a-130">-   AES</span></span><br /><span data-ttu-id="ccf4a-131">— Wartość domyślna to `RC4Stream`.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-131">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="ccf4a-132">Ten atrybut jest typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-132">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="ccf4a-133">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="ccf4a-133">msmqProtectionLevel</span></span>|<span data-ttu-id="ccf4a-134">Określa sposób, w jaki komunikaty są zabezpieczane na poziomie transportu usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-134">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="ccf4a-135">Szyfrowanie zapewnia integralność komunikatów, podczas gdy podpisywanie i szyfrowanie zapewnia integralność komunikatów i odrzucanie.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-135">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="ccf4a-136">Oznacza to, że wiadomość rzeczywiście pochodzi od nadawcy, a nadawca jest jego informacją.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-136">That is, the message indeed came from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="ccf4a-137">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="ccf4a-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ccf4a-138">Dawaj Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-138">-   None: No protection.</span></span><br /><span data-ttu-id="ccf4a-139">Zapis Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-139">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="ccf4a-140">EncryptAndSign Komunikaty są szyfrowane i podpisane.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-140">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="ccf4a-141">-Wartość domyślna to `Sign`.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-141">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="ccf4a-142">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="ccf4a-142">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="ccf4a-143">Określa algorytm wyznaczania wartości skrótu, który ma być używany do obliczania skrótu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-143">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="ccf4a-144">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="ccf4a-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ccf4a-145">-   MD5</span><span class="sxs-lookup"><span data-stu-id="ccf4a-145">-   MD5</span></span><br /><span data-ttu-id="ccf4a-146">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="ccf4a-146">-   SHA1</span></span><br /><span data-ttu-id="ccf4a-147">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="ccf4a-147">-   SHA256</span></span><br /><span data-ttu-id="ccf4a-148">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="ccf4a-148">-   SHA512</span></span><br /><br /> <span data-ttu-id="ccf4a-149">Wartość domyślna to `SHA1`.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-149">The default is `SHA1`.</span></span> <span data-ttu-id="ccf4a-150">Ten atrybut jest typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-150">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="ccf4a-151">Ze względu na kolizje problemów z algorytmem MD5 i algorytmem SHA1 firma Microsoft zaleca SHA256ą lub lepszą.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-151">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ccf4a-152">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ccf4a-152">Child Elements</span></span>  
 <span data-ttu-id="ccf4a-153">Brak</span><span class="sxs-lookup"><span data-stu-id="ccf4a-153">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ccf4a-154">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ccf4a-154">Parent Elements</span></span>  
  
|<span data-ttu-id="ccf4a-155">Element</span><span class="sxs-lookup"><span data-stu-id="ccf4a-155">Element</span></span>|<span data-ttu-id="ccf4a-156">Opis</span><span class="sxs-lookup"><span data-stu-id="ccf4a-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ccf4a-157">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ccf4a-157">\<security></span></span>](security-of-netmsmqbinding.md)|<span data-ttu-id="ccf4a-158">Definiuje ustawienia zabezpieczeń transportu dla transportów umieszczonych w kolejce.</span><span class="sxs-lookup"><span data-stu-id="ccf4a-158">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ccf4a-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ccf4a-159">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="ccf4a-160">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="ccf4a-160">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="ccf4a-161">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="ccf4a-161">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ccf4a-162">Powiązania</span><span class="sxs-lookup"><span data-stu-id="ccf4a-162">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ccf4a-163">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="ccf4a-163">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ccf4a-164">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="ccf4a-164">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ccf4a-165">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="ccf4a-165">\<binding></span></span>](../../../misc/binding.md)
