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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 611d6730695c2e353782d11cb74d391107c02c35
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="lttransportgt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="3e0a8-102">&lt;transport&gt; w &lt;netMsmqBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="3e0a8-102">&lt;transport&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="3e0a8-103">Określa ustawienia zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-103">Defines the transport security settings.</span></span>  
  
 <span data-ttu-id="3e0a8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3e0a8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3e0a8-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="3e0a8-105">\<bindings></span></span>  
<span data-ttu-id="3e0a8-106">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="3e0a8-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="3e0a8-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="3e0a8-107">\<binding></span></span>  
<span data-ttu-id="3e0a8-108">\<security></span><span class="sxs-lookup"><span data-stu-id="3e0a8-108">\<security></span></span>  
<span data-ttu-id="3e0a8-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="3e0a8-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e0a8-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e0a8-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e0a8-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3e0a8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3e0a8-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e0a8-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3e0a8-113">Attributes</span></span>  
  
|<span data-ttu-id="3e0a8-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3e0a8-114">Attribute</span></span>|<span data-ttu-id="3e0a8-115">Opis</span><span class="sxs-lookup"><span data-stu-id="3e0a8-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3e0a8-116">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="3e0a8-116">msmqAuthenticationMode</span></span>|<span data-ttu-id="3e0a8-117">Określa jak wiadomość musi być uwierzytelniani przez usługę transportową MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-117">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="3e0a8-118">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="3e0a8-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3e0a8-119">-Brak: Bez uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-119">-   None: No authentication.</span></span><br /><span data-ttu-id="3e0a8-120">-WindowsDomain: Mechanizm uwierzytelniania używa usługi Active Directory można pobrać certyfikatu X.509 identyfikator zabezpieczeń skojarzony z komunikatem.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-120">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="3e0a8-121">Służy to następnie sprawdź, czy listy ACL kolejki, aby upewnić się, użytkownik ma uprawnienia do zapisu dla kolejki.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-121">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="3e0a8-122">-Certyfikat: Kanał pobiera certyfikat z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-122">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="3e0a8-123">Wartość domyślna to `WindowsDomain`.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-123">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="3e0a8-124">Jeśli ten atrybut ma ustawioną `None`, `msmqProtectionLevel` atrybutu również musi być ustawiona na `None`.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-124">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="3e0a8-125">Ten atrybut nie ma typu<xref:System.ServiceModel.MsmqAuthenticationMode></span><span class="sxs-lookup"><span data-stu-id="3e0a8-125">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="3e0a8-126">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="3e0a8-126">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="3e0a8-127">Określa algorytm używany do szyfrowania wiadomości w sieci podczas transferu wiadomości między menedżerami kolejki wiadomości.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-127">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="3e0a8-128">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="3e0a8-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3e0a8-129">-   RC4Stream</span><span class="sxs-lookup"><span data-stu-id="3e0a8-129">-   RC4Stream</span></span><br /><span data-ttu-id="3e0a8-130">-AES</span><span class="sxs-lookup"><span data-stu-id="3e0a8-130">-   AES</span></span><br /><span data-ttu-id="3e0a8-131">— Wartość domyślna to `RC4Stream`.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-131">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="3e0a8-132">Ten atrybut jest typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-132">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="3e0a8-133">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="3e0a8-133">msmqProtectionLevel</span></span>|<span data-ttu-id="3e0a8-134">Określa sposób wiadomości są zabezpieczone na poziomie usługi transportu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-134">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="3e0a8-135">Szyfrowanie gwarantuje, że komunikat integralności, podczas logowania i szyfrowania zapewnia zarówno integralność komunikatów i wyłączność podpisu.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-135">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="3e0a8-136">To, że wiadomość rzeczywiście pochodzi od nadawcy i jest nadawcy, który mówi się, że jest on.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-136">That is, the message indeed came from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="3e0a8-137">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="3e0a8-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3e0a8-138">-Brak: Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-138">-   None: No protection.</span></span><br /><span data-ttu-id="3e0a8-139">-Znak: Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-139">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="3e0a8-140">-EncryptAndSign: Komunikaty są zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-140">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="3e0a8-141">— Wartość domyślna to `Sign`.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-141">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="3e0a8-142">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="3e0a8-142">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="3e0a8-143">Określa algorytm wyznaczania wartości skrótu używanego do obliczania skrót wiadomości.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-143">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="3e0a8-144">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="3e0a8-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3e0a8-145">-   MD5</span><span class="sxs-lookup"><span data-stu-id="3e0a8-145">-   MD5</span></span><br /><span data-ttu-id="3e0a8-146">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="3e0a8-146">-   SHA1</span></span><br /><span data-ttu-id="3e0a8-147">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="3e0a8-147">-   SHA256</span></span><br /><span data-ttu-id="3e0a8-148">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="3e0a8-148">-   SHA512</span></span><br /><br /> <span data-ttu-id="3e0a8-149">Wartość domyślna to `SHA1`.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-149">The default is `SHA1`.</span></span> <span data-ttu-id="3e0a8-150">Ten atrybut jest typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-150">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e0a8-151">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3e0a8-151">Child Elements</span></span>  
 <span data-ttu-id="3e0a8-152">Brak</span><span class="sxs-lookup"><span data-stu-id="3e0a8-152">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e0a8-153">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3e0a8-153">Parent Elements</span></span>  
  
|<span data-ttu-id="3e0a8-154">Element</span><span class="sxs-lookup"><span data-stu-id="3e0a8-154">Element</span></span>|<span data-ttu-id="3e0a8-155">Opis</span><span class="sxs-lookup"><span data-stu-id="3e0a8-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e0a8-156">\<security></span><span class="sxs-lookup"><span data-stu-id="3e0a8-156">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="3e0a8-157">Definiuje ustawienia zabezpieczeń transportu dla transportów umieszczonych w kolejce.</span><span class="sxs-lookup"><span data-stu-id="3e0a8-157">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3e0a8-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e0a8-158">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [<span data-ttu-id="3e0a8-159">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="3e0a8-159">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="3e0a8-160">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="3e0a8-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="3e0a8-161">Powiązania</span><span class="sxs-lookup"><span data-stu-id="3e0a8-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="3e0a8-162">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="3e0a8-162">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="3e0a8-163">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="3e0a8-163">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="3e0a8-164">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="3e0a8-164">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
