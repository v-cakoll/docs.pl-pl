---
title: <clientCertificate> dla <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: 277e5e33bcc7f9d417da7ce24caa4c6200c23e23
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919537"
---
# <a name="clientcertificate-of-servicecredentials"></a><span data-ttu-id="654a7-102">\<> \<ClientCertificate ></span><span class="sxs-lookup"><span data-stu-id="654a7-102">\<clientCertificate> of \<serviceCredentials></span></span>
<span data-ttu-id="654a7-103">Definiuje certyfikat X. 509 używany do podpisywania i szyfrowania komunikatów na kliencie, który tworzy usługę we wzorcu komunikacji dwukierunkowej.</span><span class="sxs-lookup"><span data-stu-id="654a7-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
 <span data-ttu-id="654a7-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="654a7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="654a7-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="654a7-105">\<behaviors></span></span>  
<span data-ttu-id="654a7-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="654a7-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="654a7-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="654a7-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="654a7-108">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="654a7-108">\<behavior></span></span>  
<span data-ttu-id="654a7-109">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="654a7-109">\<serviceCredentials></span></span>  
<span data-ttu-id="654a7-110">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="654a7-110">\<clientCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="654a7-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="654a7-111">Syntax</span></span>  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="654a7-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="654a7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="654a7-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="654a7-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="654a7-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="654a7-114">Attributes</span></span>  
 <span data-ttu-id="654a7-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="654a7-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="654a7-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="654a7-116">Child Elements</span></span>  
  
|<span data-ttu-id="654a7-117">Element</span><span class="sxs-lookup"><span data-stu-id="654a7-117">Element</span></span>|<span data-ttu-id="654a7-118">Opis</span><span class="sxs-lookup"><span data-stu-id="654a7-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="654a7-119">\<> uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="654a7-119">\<authentication></span></span>](authentication-of-clientcertificate-element.md)|<span data-ttu-id="654a7-120">Określa opcje uwierzytelniania dla certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="654a7-120">Specifies authentication options for the client certificate.</span></span>|  
|[<span data-ttu-id="654a7-121">\<> certyfikatów</span><span class="sxs-lookup"><span data-stu-id="654a7-121">\<certificate></span></span>](certificate-of-clientcertificate-element.md)|<span data-ttu-id="654a7-122">Określa certyfikat, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="654a7-122">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="654a7-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="654a7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="654a7-124">Element</span><span class="sxs-lookup"><span data-stu-id="654a7-124">Element</span></span>|<span data-ttu-id="654a7-125">Opis</span><span class="sxs-lookup"><span data-stu-id="654a7-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="654a7-126">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="654a7-126">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="654a7-127">Określa poświadczenia, które mają być używane w uwierzytelnianiu usługi oraz ustawienia powiązane z walidacją poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="654a7-127">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="654a7-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="654a7-128">Remarks</span></span>  
 <span data-ttu-id="654a7-129">Ten element jest używany, gdy usługa musi uzyskać certyfikat klienta z wyprzedzeniem w celu bezpiecznego komunikowania się z klientem.</span><span class="sxs-lookup"><span data-stu-id="654a7-129">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="654a7-130">Dzieje się tak w przypadku używania wzorca komunikacji dupleksowej.</span><span class="sxs-lookup"><span data-stu-id="654a7-130">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="654a7-131">W przypadku bardziej typowego wzorca żądania/odpowiedzi klient zawiera swój certyfikat w żądaniu, którego usługa używa do szyfrowania i podpisywania odpowiedzi z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="654a7-131">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="654a7-132">W przypadku wzorca komunikacji dupleksowej usługa nie ma jednak żądania od klienta i w związku z tym potrzebuje certyfikatu klienta z wyprzedzeniem, aby zabezpieczyć komunikat do klienta.</span><span class="sxs-lookup"><span data-stu-id="654a7-132">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="654a7-133">W związku z tym należy uzyskać certyfikat klienta w negocjacji poza pasmem i określić certyfikat przy użyciu tego elementu.</span><span class="sxs-lookup"><span data-stu-id="654a7-133">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="654a7-134">Aby uzyskać więcej informacji na temat usług dupleksowych, zobacz [How to: Utwórz kontrakt](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)dupleksowy.</span><span class="sxs-lookup"><span data-stu-id="654a7-134">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="654a7-135">Certyfikat ustawiony w tym elemencie jest używany do szyfrowania komunikatów na kliencie tylko dla powiązań skonfigurowanych przy użyciu `MutualCertificateDuplex` trybu uwierzytelniania zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="654a7-135">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="654a7-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="654a7-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [<span data-ttu-id="654a7-137">Instrukcje: Tworzenie kontraktu dupleksowego</span><span class="sxs-lookup"><span data-stu-id="654a7-137">How to: Create a Duplex Contract</span></span>](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="654a7-138">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="654a7-138">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="654a7-139">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="654a7-139">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
