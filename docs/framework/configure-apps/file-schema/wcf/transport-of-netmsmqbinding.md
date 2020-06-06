---
title: <transport> dla <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: cc47c01cccc931e81ba57ab37ad9e3accfaa693b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152934"
---
# <a name="transport-of-netmsmqbinding"></a><span data-ttu-id="dc3cb-102">\<transport> dla \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="dc3cb-102">\<transport> of \<netMsmqBinding></span></span>
<span data-ttu-id="dc3cb-103">Definiuje ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-103">Defines the transport security settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="dc3cb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc3cb-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc3cb-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dc3cb-105">Attributes and Elements</span></span>  
 <span data-ttu-id="dc3cb-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc3cb-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dc3cb-107">Attributes</span></span>  
  
|<span data-ttu-id="dc3cb-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="dc3cb-108">Attribute</span></span>|<span data-ttu-id="dc3cb-109">Opis</span><span class="sxs-lookup"><span data-stu-id="dc3cb-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dc3cb-110">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="dc3cb-110">msmqAuthenticationMode</span></span>|<span data-ttu-id="dc3cb-111">Określa, jak wiadomość musi zostać uwierzytelniona przez transport usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-111">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="dc3cb-112">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="dc3cb-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="dc3cb-113">-Brak: brak uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-113">-   None: No authentication.</span></span><br /><span data-ttu-id="dc3cb-114">-WindowsDomain: mechanizm uwierzytelniania używa Active Directory, aby pobrać certyfikat X. 509 dla identyfikatora zabezpieczeń skojarzonego z wiadomością.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-114">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="dc3cb-115">Ta wartość jest następnie używana do sprawdzenia listy ACL kolejki, aby upewnić się, że użytkownik ma uprawnienie do zapisu dla kolejki.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-115">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="dc3cb-116">-Certificate: kanał pobiera certyfikat z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-116">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="dc3cb-117">Wartość domyślna to `WindowsDomain`.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-117">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="dc3cb-118">Jeśli ten atrybut jest ustawiony na `None` , `msmqProtectionLevel` atrybut musi również być ustawiony na `None` .</span><span class="sxs-lookup"><span data-stu-id="dc3cb-118">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="dc3cb-119">Ten atrybut nie ma typu<xref:System.ServiceModel.MsmqAuthenticationMode></span><span class="sxs-lookup"><span data-stu-id="dc3cb-119">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="dc3cb-120">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="dc3cb-120">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="dc3cb-121">Określa algorytm używany do szyfrowania wiadomości w sieci podczas przesyłania komunikatów między menedżerami kolejki wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-121">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="dc3cb-122">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="dc3cb-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="dc3cb-123">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="dc3cb-123">-   RC4Stream</span></span><br /><span data-ttu-id="dc3cb-124">-AES</span><span class="sxs-lookup"><span data-stu-id="dc3cb-124">-   AES</span></span><br /><span data-ttu-id="dc3cb-125">— Wartość domyślna to `RC4Stream` .</span><span class="sxs-lookup"><span data-stu-id="dc3cb-125">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="dc3cb-126">Ten atrybut jest typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="dc3cb-126">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="dc3cb-127">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="dc3cb-127">msmqProtectionLevel</span></span>|<span data-ttu-id="dc3cb-128">Określa sposób, w jaki komunikaty są zabezpieczane na poziomie transportu usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-128">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="dc3cb-129">Szyfrowanie zapewnia integralność komunikatów, podczas gdy podpisywanie i szyfrowanie zapewnia integralność komunikatów i odrzucanie.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-129">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="dc3cb-130">Oznacza to, że komunikat rzeczywiście pochodzi od nadawcy, a nadawca wskazuje, że są.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-130">That is, the message indeed came from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="dc3cb-131">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="dc3cb-131">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="dc3cb-132">-Brak: brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-132">-   None: No protection.</span></span><br /><span data-ttu-id="dc3cb-133">-Sign: komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-133">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="dc3cb-134">-EncryptAndSign: komunikaty są szyfrowane i podpisane.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-134">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="dc3cb-135">-Wartość domyślna to `Sign` .</span><span class="sxs-lookup"><span data-stu-id="dc3cb-135">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="dc3cb-136">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="dc3cb-136">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="dc3cb-137">Określa algorytm wyznaczania wartości skrótu, który ma być używany do obliczania skrótu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-137">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="dc3cb-138">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="dc3cb-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="dc3cb-139">-MD5</span><span class="sxs-lookup"><span data-stu-id="dc3cb-139">-   MD5</span></span><br /><span data-ttu-id="dc3cb-140">-SHA1</span><span class="sxs-lookup"><span data-stu-id="dc3cb-140">-   SHA1</span></span><br /><span data-ttu-id="dc3cb-141">-SHA256</span><span class="sxs-lookup"><span data-stu-id="dc3cb-141">-   SHA256</span></span><br /><span data-ttu-id="dc3cb-142">-SHA512</span><span class="sxs-lookup"><span data-stu-id="dc3cb-142">-   SHA512</span></span><br /><br /> <span data-ttu-id="dc3cb-143">Wartość domyślna to `SHA1`.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-143">The default is `SHA1`.</span></span> <span data-ttu-id="dc3cb-144">Ten atrybut jest typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="dc3cb-144">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="dc3cb-145">Ze względu na kolizje problemów z algorytmem MD5 i algorytmem SHA1 firma Microsoft zaleca SHA256ą lub lepszą.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-145">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc3cb-146">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dc3cb-146">Child Elements</span></span>  
 <span data-ttu-id="dc3cb-147">Brak</span><span class="sxs-lookup"><span data-stu-id="dc3cb-147">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dc3cb-148">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dc3cb-148">Parent Elements</span></span>  
  
|<span data-ttu-id="dc3cb-149">Element</span><span class="sxs-lookup"><span data-stu-id="dc3cb-149">Element</span></span>|<span data-ttu-id="dc3cb-150">Opis</span><span class="sxs-lookup"><span data-stu-id="dc3cb-150">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netmsmqbinding.md)|<span data-ttu-id="dc3cb-151">Definiuje ustawienia zabezpieczeń transportu dla transportów umieszczonych w kolejce.</span><span class="sxs-lookup"><span data-stu-id="dc3cb-151">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc3cb-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc3cb-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="dc3cb-153">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="dc3cb-153">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="dc3cb-154">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="dc3cb-154">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="dc3cb-155">Powiązania</span><span class="sxs-lookup"><span data-stu-id="dc3cb-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="dc3cb-156">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="dc3cb-156">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="dc3cb-157">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="dc3cb-157">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
