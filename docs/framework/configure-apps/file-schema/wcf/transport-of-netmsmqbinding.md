---
title: <transport> z <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: c82a786fe8e4a2b2e3243db007f4f705d9fbd79a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277150"
---
# <a name="transport-of-netmsmqbinding"></a><span data-ttu-id="979aa-102">\<transport > z \<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="979aa-102">\<transport> of \<netMsmqBinding></span></span>
<span data-ttu-id="979aa-103">Określa ustawienia zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="979aa-103">Defines the transport security settings.</span></span>  
  
 <span data-ttu-id="979aa-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="979aa-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="979aa-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="979aa-105">\<bindings></span></span>  
<span data-ttu-id="979aa-106">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="979aa-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="979aa-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="979aa-107">\<binding></span></span>  
<span data-ttu-id="979aa-108">\<security></span><span class="sxs-lookup"><span data-stu-id="979aa-108">\<security></span></span>  
<span data-ttu-id="979aa-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="979aa-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="979aa-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="979aa-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="979aa-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="979aa-111">Attributes and Elements</span></span>  
 <span data-ttu-id="979aa-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="979aa-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="979aa-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="979aa-113">Attributes</span></span>  
  
|<span data-ttu-id="979aa-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="979aa-114">Attribute</span></span>|<span data-ttu-id="979aa-115">Opis</span><span class="sxs-lookup"><span data-stu-id="979aa-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="979aa-116">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="979aa-116">msmqAuthenticationMode</span></span>|<span data-ttu-id="979aa-117">Określa, jak wiadomość musi zostać uwierzytelniony przez usługę transportową MSMQ.</span><span class="sxs-lookup"><span data-stu-id="979aa-117">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="979aa-118">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="979aa-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="979aa-119">-Brak: Bez uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="979aa-119">-   None: No authentication.</span></span><br /><span data-ttu-id="979aa-120">-WindowsDomain: Mechanizm uwierzytelniania używa usługi Active Directory można pobrać certyfikatu X.509 dla identyfikatora zabezpieczeń skojarzonych z wiadomością.</span><span class="sxs-lookup"><span data-stu-id="979aa-120">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="979aa-121">Następnie służy do Sprawdź, czy lista ACL kolejki, aby upewnić się, użytkownik ma uprawnienia do zapisu dla kolejki.</span><span class="sxs-lookup"><span data-stu-id="979aa-121">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="979aa-122">-Certyfikat: Kanał pobiera certyfikat z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="979aa-122">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="979aa-123">Wartość domyślna to `WindowsDomain`.</span><span class="sxs-lookup"><span data-stu-id="979aa-123">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="979aa-124">Jeśli ten atrybut jest ustawiony na `None`, `msmqProtectionLevel` atrybut również musi być ustawiona na `None`.</span><span class="sxs-lookup"><span data-stu-id="979aa-124">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="979aa-125">Ten atrybut nie ma typu<xref:System.ServiceModel.MsmqAuthenticationMode></span><span class="sxs-lookup"><span data-stu-id="979aa-125">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="979aa-126">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="979aa-126">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="979aa-127">Określa algorytm używany do szyfrowania wiadomości na łączu podczas transferu wiadomości między menedżerami kolejki wiadomości.</span><span class="sxs-lookup"><span data-stu-id="979aa-127">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="979aa-128">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="979aa-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="979aa-129">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="979aa-129">-   RC4Stream</span></span><br /><span data-ttu-id="979aa-130">-AES</span><span class="sxs-lookup"><span data-stu-id="979aa-130">-   AES</span></span><br /><span data-ttu-id="979aa-131">— Wartość domyślna to `RC4Stream`.</span><span class="sxs-lookup"><span data-stu-id="979aa-131">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="979aa-132">Ten atrybut jest typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="979aa-132">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="979aa-133">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="979aa-133">msmqProtectionLevel</span></span>|<span data-ttu-id="979aa-134">Określa, że sposób wiadomości są zabezpieczone na poziomie usługi transportu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="979aa-134">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="979aa-135">Szyfrowanie zapewnia, że komunikat integralności, podczas logowania i szyfrowania zapewnia integralność komunikatów i uznawania.</span><span class="sxs-lookup"><span data-stu-id="979aa-135">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="979aa-136">Oznacza to komunikat w rzeczywistości pochodzi od nadawcy i informacje o nadawcy mają który mówi, że jest on.</span><span class="sxs-lookup"><span data-stu-id="979aa-136">That is, the message indeed came from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="979aa-137">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="979aa-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="979aa-138">-Brak: Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="979aa-138">-   None: No protection.</span></span><br /><span data-ttu-id="979aa-139">— Logowanie: Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="979aa-139">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="979aa-140">-EncryptAndSign: Komunikaty są szyfrowane i podpisany.</span><span class="sxs-lookup"><span data-stu-id="979aa-140">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="979aa-141">— Wartość domyślna to `Sign`.</span><span class="sxs-lookup"><span data-stu-id="979aa-141">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="979aa-142">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="979aa-142">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="979aa-143">Określa algorytm wyznaczania wartości skrótu, który ma być używany do przetwarzania danych skrót wiadomości.</span><span class="sxs-lookup"><span data-stu-id="979aa-143">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="979aa-144">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="979aa-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="979aa-145">-   MD5</span><span class="sxs-lookup"><span data-stu-id="979aa-145">-   MD5</span></span><br /><span data-ttu-id="979aa-146">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="979aa-146">-   SHA1</span></span><br /><span data-ttu-id="979aa-147">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="979aa-147">-   SHA256</span></span><br /><span data-ttu-id="979aa-148">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="979aa-148">-   SHA512</span></span><br /><br /> <span data-ttu-id="979aa-149">Wartość domyślna to `SHA1`.</span><span class="sxs-lookup"><span data-stu-id="979aa-149">The default is `SHA1`.</span></span> <span data-ttu-id="979aa-150">Ten atrybut jest typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="979aa-150">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="979aa-151">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="979aa-151">Child Elements</span></span>  
 <span data-ttu-id="979aa-152">Brak</span><span class="sxs-lookup"><span data-stu-id="979aa-152">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="979aa-153">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="979aa-153">Parent Elements</span></span>  
  
|<span data-ttu-id="979aa-154">Element</span><span class="sxs-lookup"><span data-stu-id="979aa-154">Element</span></span>|<span data-ttu-id="979aa-155">Opis</span><span class="sxs-lookup"><span data-stu-id="979aa-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="979aa-156">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="979aa-156">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="979aa-157">Określa ustawienia zabezpieczenia transportu dla transportów umieszczonych w kolejce.</span><span class="sxs-lookup"><span data-stu-id="979aa-157">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="979aa-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="979aa-158">See also</span></span>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="979aa-159">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="979aa-159">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="979aa-160">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="979aa-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="979aa-161">Powiązania</span><span class="sxs-lookup"><span data-stu-id="979aa-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="979aa-162">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="979aa-162">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="979aa-163">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="979aa-163">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="979aa-164">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="979aa-164">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
