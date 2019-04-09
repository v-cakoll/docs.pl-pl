---
title: <transport> z <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: ec726c4b39fedbf63a7ecc9e685a86367609fa43
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085015"
---
# <a name="transport-of-netmsmqbinding"></a><span data-ttu-id="fd400-102">\<transport > z \<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="fd400-102">\<transport> of \<netMsmqBinding></span></span>
<span data-ttu-id="fd400-103">Określa ustawienia zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="fd400-103">Defines the transport security settings.</span></span>  
  
 <span data-ttu-id="fd400-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fd400-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fd400-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="fd400-105">\<bindings></span></span>  
<span data-ttu-id="fd400-106">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="fd400-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="fd400-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="fd400-107">\<binding></span></span>  
<span data-ttu-id="fd400-108">\<security></span><span class="sxs-lookup"><span data-stu-id="fd400-108">\<security></span></span>  
<span data-ttu-id="fd400-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="fd400-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd400-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd400-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd400-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fd400-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fd400-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fd400-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd400-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fd400-113">Attributes</span></span>  
  
|<span data-ttu-id="fd400-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fd400-114">Attribute</span></span>|<span data-ttu-id="fd400-115">Opis</span><span class="sxs-lookup"><span data-stu-id="fd400-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd400-116">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="fd400-116">msmqAuthenticationMode</span></span>|<span data-ttu-id="fd400-117">Określa, jak wiadomość musi zostać uwierzytelniony przez usługę transportową MSMQ.</span><span class="sxs-lookup"><span data-stu-id="fd400-117">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="fd400-118">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="fd400-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fd400-119">-Brak: Bez uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fd400-119">-   None: No authentication.</span></span><br /><span data-ttu-id="fd400-120">-WindowsDomain: Mechanizm uwierzytelniania używa usługi Active Directory można pobrać certyfikatu X.509 dla identyfikatora zabezpieczeń skojarzonych z wiadomością.</span><span class="sxs-lookup"><span data-stu-id="fd400-120">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="fd400-121">Następnie służy do Sprawdź, czy lista ACL kolejki, aby upewnić się, użytkownik ma uprawnienia do zapisu dla kolejki.</span><span class="sxs-lookup"><span data-stu-id="fd400-121">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="fd400-122">-Certyfikat: Kanał pobiera certyfikat z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="fd400-122">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="fd400-123">Wartość domyślna to `WindowsDomain`.</span><span class="sxs-lookup"><span data-stu-id="fd400-123">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="fd400-124">Jeśli ten atrybut jest ustawiony na `None`, `msmqProtectionLevel` atrybut również musi być ustawiona na `None`.</span><span class="sxs-lookup"><span data-stu-id="fd400-124">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="fd400-125">Ten atrybut jest typu</span><span class="sxs-lookup"><span data-stu-id="fd400-125">This attribute is of type</span></span> <xref:System.ServiceModel.MsmqAuthenticationMode>|  
|<span data-ttu-id="fd400-126">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="fd400-126">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="fd400-127">Określa algorytm używany do szyfrowania wiadomości na łączu podczas transferu wiadomości między menedżerami kolejki wiadomości.</span><span class="sxs-lookup"><span data-stu-id="fd400-127">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="fd400-128">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="fd400-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fd400-129">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="fd400-129">-   RC4Stream</span></span><br /><span data-ttu-id="fd400-130">-AES</span><span class="sxs-lookup"><span data-stu-id="fd400-130">-   AES</span></span><br /><span data-ttu-id="fd400-131">— Wartość domyślna to `RC4Stream`.</span><span class="sxs-lookup"><span data-stu-id="fd400-131">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="fd400-132">Ten atrybut jest typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="fd400-132">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="fd400-133">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="fd400-133">msmqProtectionLevel</span></span>|<span data-ttu-id="fd400-134">Określa, że sposób wiadomości są zabezpieczone na poziomie usługi transportu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="fd400-134">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="fd400-135">Szyfrowanie zapewnia, że komunikat integralności, podczas logowania i szyfrowania zapewnia integralność komunikatów i uznawania.</span><span class="sxs-lookup"><span data-stu-id="fd400-135">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="fd400-136">Oznacza to komunikat w rzeczywistości pochodzi od nadawcy i informacje o nadawcy mają który mówi, że jest on.</span><span class="sxs-lookup"><span data-stu-id="fd400-136">That is, the message indeed came from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="fd400-137">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="fd400-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fd400-138">-Brak: Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="fd400-138">-   None: No protection.</span></span><br /><span data-ttu-id="fd400-139">— Logowanie: Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="fd400-139">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="fd400-140">-EncryptAndSign: Komunikaty są szyfrowane i podpisany.</span><span class="sxs-lookup"><span data-stu-id="fd400-140">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="fd400-141">— Wartość domyślna to `Sign`.</span><span class="sxs-lookup"><span data-stu-id="fd400-141">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="fd400-142">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="fd400-142">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="fd400-143">Określa algorytm wyznaczania wartości skrótu, który ma być używany do przetwarzania danych skrót wiadomości.</span><span class="sxs-lookup"><span data-stu-id="fd400-143">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="fd400-144">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="fd400-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fd400-145">-   MD5</span><span class="sxs-lookup"><span data-stu-id="fd400-145">-   MD5</span></span><br /><span data-ttu-id="fd400-146">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="fd400-146">-   SHA1</span></span><br /><span data-ttu-id="fd400-147">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="fd400-147">-   SHA256</span></span><br /><span data-ttu-id="fd400-148">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="fd400-148">-   SHA512</span></span><br /><br /> <span data-ttu-id="fd400-149">Wartość domyślna to `SHA1`.</span><span class="sxs-lookup"><span data-stu-id="fd400-149">The default is `SHA1`.</span></span> <span data-ttu-id="fd400-150">Ten atrybut jest typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="fd400-150">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="fd400-151">Z powodu problemów kolizji z MD5 lub SHA1 firma Microsoft zaleca SHA256 lub lepszej.</span><span class="sxs-lookup"><span data-stu-id="fd400-151">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd400-152">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fd400-152">Child Elements</span></span>  
 <span data-ttu-id="fd400-153">Brak</span><span class="sxs-lookup"><span data-stu-id="fd400-153">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd400-154">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fd400-154">Parent Elements</span></span>  
  
|<span data-ttu-id="fd400-155">Element</span><span class="sxs-lookup"><span data-stu-id="fd400-155">Element</span></span>|<span data-ttu-id="fd400-156">Opis</span><span class="sxs-lookup"><span data-stu-id="fd400-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd400-157">\<security></span><span class="sxs-lookup"><span data-stu-id="fd400-157">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="fd400-158">Określa ustawienia zabezpieczenia transportu dla transportów umieszczonych w kolejce.</span><span class="sxs-lookup"><span data-stu-id="fd400-158">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd400-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd400-159">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="fd400-160">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="fd400-160">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="fd400-161">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="fd400-161">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="fd400-162">Powiązania</span><span class="sxs-lookup"><span data-stu-id="fd400-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="fd400-163">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="fd400-163">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="fd400-164">Konfigurowanie usług i klientów za pomocą wiązań</span><span class="sxs-lookup"><span data-stu-id="fd400-164">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="fd400-165">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="fd400-165">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
