---
title: '&lt;transport&gt; w &lt;netMsmqBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2df5bf18605fcf20b253212cb0f9a62b4719b0ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="775f9-102">&lt;transport&gt; w &lt;netMsmqBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="775f9-102">&lt;transport&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="775f9-103">Określa ustawienia zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="775f9-103">Defines the transport security settings.</span></span>  
  
 <span data-ttu-id="775f9-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="775f9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="775f9-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="775f9-105">\<bindings></span></span>  
<span data-ttu-id="775f9-106">\<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="775f9-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="775f9-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="775f9-107">\<binding></span></span>  
<span data-ttu-id="775f9-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="775f9-108">\<security></span></span>  
<span data-ttu-id="775f9-109">\<transport ></span><span class="sxs-lookup"><span data-stu-id="775f9-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="775f9-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="775f9-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="775f9-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="775f9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="775f9-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="775f9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="775f9-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="775f9-113">Attributes</span></span>  
  
|<span data-ttu-id="775f9-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="775f9-114">Attribute</span></span>|<span data-ttu-id="775f9-115">Opis</span><span class="sxs-lookup"><span data-stu-id="775f9-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="775f9-116">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="775f9-116">msmqAuthenticationMode</span></span>|<span data-ttu-id="775f9-117">Określa jak wiadomość musi być uwierzytelniani przez usługę transportową MSMQ.</span><span class="sxs-lookup"><span data-stu-id="775f9-117">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="775f9-118">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="775f9-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="775f9-119">-Brak: Bez uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="775f9-119">-   None: No authentication.</span></span><br /><span data-ttu-id="775f9-120">-WindowsDomain: Mechanizm uwierzytelniania używa usługi Active Directory można pobrać certyfikatu X.509 identyfikator zabezpieczeń skojarzony z komunikatem.</span><span class="sxs-lookup"><span data-stu-id="775f9-120">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="775f9-121">Służy to następnie sprawdź, czy listy ACL kolejki, aby upewnić się, użytkownik ma uprawnienia do zapisu dla kolejki.</span><span class="sxs-lookup"><span data-stu-id="775f9-121">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="775f9-122">-Certyfikat: Kanał pobiera certyfikat z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="775f9-122">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="775f9-123">Wartość domyślna to `WindowsDomain`.</span><span class="sxs-lookup"><span data-stu-id="775f9-123">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="775f9-124">Jeśli ten atrybut ma ustawioną `None`, `msmqProtectionLevel` atrybutu również musi być ustawiona na `None`.</span><span class="sxs-lookup"><span data-stu-id="775f9-124">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="775f9-125">Ten atrybut nie ma typu<xref:System.ServiceModel.MsmqAuthenticationMode></span><span class="sxs-lookup"><span data-stu-id="775f9-125">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="775f9-126">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="775f9-126">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="775f9-127">Określa algorytm używany do szyfrowania wiadomości w sieci podczas transferu wiadomości między menedżerami kolejki wiadomości.</span><span class="sxs-lookup"><span data-stu-id="775f9-127">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="775f9-128">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="775f9-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="775f9-129">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="775f9-129">-   RC4Stream</span></span><br /><span data-ttu-id="775f9-130">-AES</span><span class="sxs-lookup"><span data-stu-id="775f9-130">-   AES</span></span><br /><span data-ttu-id="775f9-131">— Wartość domyślna to `RC4Stream`.</span><span class="sxs-lookup"><span data-stu-id="775f9-131">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="775f9-132">Ten atrybut jest typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="775f9-132">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="775f9-133">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="775f9-133">msmqProtectionLevel</span></span>|<span data-ttu-id="775f9-134">Określa sposób wiadomości są zabezpieczone na poziomie usługi transportu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="775f9-134">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="775f9-135">Szyfrowanie gwarantuje, że komunikat integralności, podczas logowania i szyfrowania zapewnia zarówno integralność komunikatów i wyłączność podpisu.</span><span class="sxs-lookup"><span data-stu-id="775f9-135">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="775f9-136">To, że wiadomość rzeczywiście pochodzi od nadawcy i jest nadawcy, który mówi się, że jest on.</span><span class="sxs-lookup"><span data-stu-id="775f9-136">That is, the message indeed came from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="775f9-137">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="775f9-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="775f9-138">-Brak: Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="775f9-138">-   None: No protection.</span></span><br /><span data-ttu-id="775f9-139">-Znak: Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="775f9-139">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="775f9-140">-EncryptAndSign: Komunikaty są zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="775f9-140">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="775f9-141">— Wartość domyślna to `Sign`.</span><span class="sxs-lookup"><span data-stu-id="775f9-141">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="775f9-142">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="775f9-142">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="775f9-143">Określa algorytm wyznaczania wartości skrótu używanego do obliczania skrót wiadomości.</span><span class="sxs-lookup"><span data-stu-id="775f9-143">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="775f9-144">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="775f9-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="775f9-145">-MD5</span><span class="sxs-lookup"><span data-stu-id="775f9-145">-   MD5</span></span><br /><span data-ttu-id="775f9-146">-SHA1.</span><span class="sxs-lookup"><span data-stu-id="775f9-146">-   SHA1</span></span><br /><span data-ttu-id="775f9-147">-SHA256</span><span class="sxs-lookup"><span data-stu-id="775f9-147">-   SHA256</span></span><br /><span data-ttu-id="775f9-148">-SHA512.</span><span class="sxs-lookup"><span data-stu-id="775f9-148">-   SHA512</span></span><br /><br /> <span data-ttu-id="775f9-149">Wartość domyślna to `SHA1`.</span><span class="sxs-lookup"><span data-stu-id="775f9-149">The default is `SHA1`.</span></span> <span data-ttu-id="775f9-150">Ten atrybut jest typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="775f9-150">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="775f9-151">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="775f9-151">Child Elements</span></span>  
 <span data-ttu-id="775f9-152">Brak</span><span class="sxs-lookup"><span data-stu-id="775f9-152">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="775f9-153">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="775f9-153">Parent Elements</span></span>  
  
|<span data-ttu-id="775f9-154">Element</span><span class="sxs-lookup"><span data-stu-id="775f9-154">Element</span></span>|<span data-ttu-id="775f9-155">Opis</span><span class="sxs-lookup"><span data-stu-id="775f9-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="775f9-156">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="775f9-156">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="775f9-157">Definiuje ustawienia zabezpieczeń transportu dla transportów umieszczonych w kolejce.</span><span class="sxs-lookup"><span data-stu-id="775f9-157">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="775f9-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="775f9-158">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [<span data-ttu-id="775f9-159">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="775f9-159">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="775f9-160">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="775f9-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="775f9-161">Powiązania</span><span class="sxs-lookup"><span data-stu-id="775f9-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="775f9-162">Konfigurowanie powiązań dostarczanych przez System</span><span class="sxs-lookup"><span data-stu-id="775f9-162">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="775f9-163">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="775f9-163">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="775f9-164">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="775f9-164">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
