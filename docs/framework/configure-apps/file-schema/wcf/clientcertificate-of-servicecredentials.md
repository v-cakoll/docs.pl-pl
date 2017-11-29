---
title: '&lt;clientCertificate&gt; w &lt;serviceCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bc4b3251a85a6926c93f418c154b4eabbd44092f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltclientcertificategt-of-ltservicecredentialsgt"></a><span data-ttu-id="c0fa4-102">&lt;clientCertificate&gt; w &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="c0fa4-102">&lt;clientCertificate&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="c0fa4-103">Definiuje certyfikat X.509 używany do podpisywania i szyfrowania wiadomości dla formularza klienta usługi we wzorcu komunikację dupleksową.</span><span class="sxs-lookup"><span data-stu-id="c0fa4-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
 <span data-ttu-id="c0fa4-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c0fa4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c0fa4-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="c0fa4-105">\<behaviors></span></span>  
<span data-ttu-id="c0fa4-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c0fa4-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="c0fa4-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c0fa4-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="c0fa4-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="c0fa4-108">\<behavior></span></span>  
<span data-ttu-id="c0fa4-109">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="c0fa4-109">\<serviceCredentials></span></span>  
<span data-ttu-id="c0fa4-110">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="c0fa4-110">\<clientCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0fa4-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="c0fa4-111">Syntax</span></span>  
  
```xml  
<clientCertificate>  
 <certificate/>  
 <authentication/>  
</clientCertificate>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0fa4-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c0fa4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c0fa4-113">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c0fa4-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0fa4-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c0fa4-114">Attributes</span></span>  
 <span data-ttu-id="c0fa4-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="c0fa4-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c0fa4-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c0fa4-116">Child Elements</span></span>  
  
|<span data-ttu-id="c0fa4-117">Element</span><span class="sxs-lookup"><span data-stu-id="c0fa4-117">Element</span></span>|<span data-ttu-id="c0fa4-118">Opis</span><span class="sxs-lookup"><span data-stu-id="c0fa4-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0fa4-119">\<Uwierzytelnianie ></span><span class="sxs-lookup"><span data-stu-id="c0fa4-119">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)|<span data-ttu-id="c0fa4-120">Określa opcje uwierzytelniania certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="c0fa4-120">Specifies authentication options for the client certificate.</span></span>|  
|[<span data-ttu-id="c0fa4-121">\<certyfikat ></span><span class="sxs-lookup"><span data-stu-id="c0fa4-121">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)|<span data-ttu-id="c0fa4-122">Określa certyfikat do użycia.</span><span class="sxs-lookup"><span data-stu-id="c0fa4-122">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c0fa4-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c0fa4-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c0fa4-124">Element</span><span class="sxs-lookup"><span data-stu-id="c0fa4-124">Element</span></span>|<span data-ttu-id="c0fa4-125">Opis</span><span class="sxs-lookup"><span data-stu-id="c0fa4-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0fa4-126">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="c0fa4-126">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="c0fa4-127">Określa poświadczenia, które mają być użyte w uwierzytelnianiu usługi, i sprawdzanie poprawności poświadczeń klienta powiązane ustawienia.</span><span class="sxs-lookup"><span data-stu-id="c0fa4-127">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0fa4-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c0fa4-128">Remarks</span></span>  
 <span data-ttu-id="c0fa4-129">Ten element jest używany, gdy usługa musi mieć certyfikat klienta z wyprzedzeniem do bezpiecznego komunikowania się z klientem.</span><span class="sxs-lookup"><span data-stu-id="c0fa4-129">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="c0fa4-130">Dzieje się tak podczas używania wzorca komunikację dupleksową.</span><span class="sxs-lookup"><span data-stu-id="c0fa4-130">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="c0fa4-131">We wzorcu bardziej typowego żądania/odpowiedzi klienta obejmuje jego certyfikat w żądaniu, usługa używa do szyfrowania i podpisywania odpowiedzi do klienta.</span><span class="sxs-lookup"><span data-stu-id="c0fa4-131">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="c0fa4-132">We wzorcu komunikację dupleksową jednak usługa ma żądania z klienta i dlatego wymaga certyfikatu klienta z wyprzedzeniem, aby zabezpieczyć wiadomość do klienta.</span><span class="sxs-lookup"><span data-stu-id="c0fa4-132">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="c0fa4-133">W związku z tym należy uzyskać certyfikat klienta w negocjacji poza pasmem oraz określić certyfikat przy użyciu tego elementu.</span><span class="sxs-lookup"><span data-stu-id="c0fa4-133">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="c0fa4-134">Aby uzyskać więcej informacji na temat usługi dwukierunkowe, zobacz [porady: tworzenie kontraktu dwukierunkowego](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="c0fa4-134">For more information about duplex services, see [How to: Create a Duplex Contract](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="c0fa4-135">Certyfikat w tym elemencie jest używany do szyfrowania wiadomości do klienta tylko dla powiązania, które są skonfigurowane przy użyciu `MutualCertificateDuplex` trybu uwierzytelniania zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c0fa4-135">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0fa4-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0fa4-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>  
 [<span data-ttu-id="c0fa4-137">Porady: tworzenie kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="c0fa4-137">How to: Create a Duplex Contract</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="c0fa4-138">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="c0fa4-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="c0fa4-139">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="c0fa4-139">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
