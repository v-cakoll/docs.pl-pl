---
title: '&lt;clientCertificate&gt; w &lt;serviceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: c33c6d6a80625028b9d97ab486cf50e4970b8941
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748922"
---
# <a name="ltclientcertificategt-of-ltservicecredentialsgt"></a><span data-ttu-id="e8ab8-102">&lt;clientCertificate&gt; w &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="e8ab8-102">&lt;clientCertificate&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="e8ab8-103">Definiuje certyfikat X.509 używany do podpisywania i szyfrowania wiadomości dla formularza klienta usługi we wzorcu komunikację dupleksową.</span><span class="sxs-lookup"><span data-stu-id="e8ab8-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
 <span data-ttu-id="e8ab8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e8ab8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e8ab8-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="e8ab8-105">\<behaviors></span></span>  
<span data-ttu-id="e8ab8-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="e8ab8-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e8ab8-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="e8ab8-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="e8ab8-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="e8ab8-108">\<behavior></span></span>  
<span data-ttu-id="e8ab8-109">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="e8ab8-109">\<serviceCredentials></span></span>  
<span data-ttu-id="e8ab8-110">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="e8ab8-110">\<clientCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8ab8-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8ab8-111">Syntax</span></span>  
  
```xml  
<clientCertificate>  
 <certificate/>  
 <authentication/>  
</clientCertificate>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8ab8-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e8ab8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e8ab8-113">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e8ab8-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8ab8-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e8ab8-114">Attributes</span></span>  
 <span data-ttu-id="e8ab8-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="e8ab8-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e8ab8-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e8ab8-116">Child Elements</span></span>  
  
|<span data-ttu-id="e8ab8-117">Element</span><span class="sxs-lookup"><span data-stu-id="e8ab8-117">Element</span></span>|<span data-ttu-id="e8ab8-118">Opis</span><span class="sxs-lookup"><span data-stu-id="e8ab8-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8ab8-119">\<Uwierzytelnianie ></span><span class="sxs-lookup"><span data-stu-id="e8ab8-119">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)|<span data-ttu-id="e8ab8-120">Określa opcje uwierzytelniania certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="e8ab8-120">Specifies authentication options for the client certificate.</span></span>|  
|[<span data-ttu-id="e8ab8-121">\<certyfikat ></span><span class="sxs-lookup"><span data-stu-id="e8ab8-121">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)|<span data-ttu-id="e8ab8-122">Określa certyfikat do użycia.</span><span class="sxs-lookup"><span data-stu-id="e8ab8-122">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e8ab8-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e8ab8-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e8ab8-124">Element</span><span class="sxs-lookup"><span data-stu-id="e8ab8-124">Element</span></span>|<span data-ttu-id="e8ab8-125">Opis</span><span class="sxs-lookup"><span data-stu-id="e8ab8-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8ab8-126">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="e8ab8-126">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="e8ab8-127">Określa poświadczenia, które mają być użyte w uwierzytelnianiu usługi, i sprawdzanie poprawności poświadczeń klienta powiązane ustawienia.</span><span class="sxs-lookup"><span data-stu-id="e8ab8-127">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8ab8-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e8ab8-128">Remarks</span></span>  
 <span data-ttu-id="e8ab8-129">Ten element jest używany, gdy usługa musi mieć certyfikat klienta z wyprzedzeniem do bezpiecznego komunikowania się z klientem.</span><span class="sxs-lookup"><span data-stu-id="e8ab8-129">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="e8ab8-130">Dzieje się tak podczas używania wzorca komunikację dupleksową.</span><span class="sxs-lookup"><span data-stu-id="e8ab8-130">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="e8ab8-131">We wzorcu bardziej typowego żądania/odpowiedzi klienta obejmuje jego certyfikat w żądaniu, usługa używa do szyfrowania i podpisywania odpowiedzi do klienta.</span><span class="sxs-lookup"><span data-stu-id="e8ab8-131">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="e8ab8-132">We wzorcu komunikację dupleksową jednak usługa ma żądania z klienta i dlatego wymaga certyfikatu klienta z wyprzedzeniem, aby zabezpieczyć wiadomość do klienta.</span><span class="sxs-lookup"><span data-stu-id="e8ab8-132">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="e8ab8-133">W związku z tym należy uzyskać certyfikat klienta w negocjacji poza pasmem oraz określić certyfikat przy użyciu tego elementu.</span><span class="sxs-lookup"><span data-stu-id="e8ab8-133">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="e8ab8-134">Aby uzyskać więcej informacji na temat usługi dwukierunkowe, zobacz [porady: tworzenie kontraktu dwukierunkowego](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="e8ab8-134">For more information about duplex services, see [How to: Create a Duplex Contract](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="e8ab8-135">Certyfikat w tym elemencie jest używany do szyfrowania wiadomości do klienta tylko dla powiązania, które są skonfigurowane przy użyciu `MutualCertificateDuplex` trybu uwierzytelniania zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e8ab8-135">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ab8-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8ab8-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>  
 [<span data-ttu-id="e8ab8-137">Instrukcje: tworzenie kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="e8ab8-137">How to: Create a Duplex Contract</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="e8ab8-138">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="e8ab8-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="e8ab8-139">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="e8ab8-139">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
