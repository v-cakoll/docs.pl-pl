---
title: <scopedCertificates>, element
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: ed53a42575a8d57c365f7a329a1a9c1df075d6d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935219"
---
# <a name="scopedcertificates-element"></a><span data-ttu-id="a9117-102">\<scopedCertificates> Element</span><span class="sxs-lookup"><span data-stu-id="a9117-102">\<scopedCertificates> Element</span></span>
<span data-ttu-id="a9117-103">Reprezentuje kolekcję certyfikatów X. 509 dostarczonych przez określone usługi (w zakresie) do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a9117-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="a9117-104">Ta kolekcja jest zwykle używana do określania certyfikatów usługi dla usług tokenów zabezpieczających w scenariuszu federacyjnym.</span><span class="sxs-lookup"><span data-stu-id="a9117-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
 <span data-ttu-id="a9117-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a9117-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a9117-106">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="a9117-106">\<behaviors></span></span>  
<span data-ttu-id="a9117-107">Sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="a9117-107">endpointBehaviors section</span></span>  
<span data-ttu-id="a9117-108">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="a9117-108">\<behavior></span></span>  
<span data-ttu-id="a9117-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="a9117-109">\<clientCredentials></span></span>  
<span data-ttu-id="a9117-110">\<> serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="a9117-110">\<serviceCertificate></span></span>  
<span data-ttu-id="a9117-111">\<scopedCertificates> Element</span><span class="sxs-lookup"><span data-stu-id="a9117-111">\<scopedCertificates> Element</span></span>  
<span data-ttu-id="a9117-112">\<Dodaj element > dla \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="a9117-112">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9117-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9117-113">Syntax</span></span>  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9117-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a9117-114">Attributes and Elements</span></span>  
 <span data-ttu-id="a9117-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a9117-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9117-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a9117-116">Attributes</span></span>  
 <span data-ttu-id="a9117-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="a9117-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a9117-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a9117-118">Child Elements</span></span>  
  
|<span data-ttu-id="a9117-119">Element</span><span class="sxs-lookup"><span data-stu-id="a9117-119">Element</span></span>|<span data-ttu-id="a9117-120">Opis</span><span class="sxs-lookup"><span data-stu-id="a9117-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9117-121">\<add></span><span class="sxs-lookup"><span data-stu-id="a9117-121">\<add></span></span>](add-of-scopedcertificates-element.md)|<span data-ttu-id="a9117-122">Dodaje certyfikat X. 509 do kolekcji certyfikatów z zakresem.</span><span class="sxs-lookup"><span data-stu-id="a9117-122">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a9117-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a9117-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a9117-124">Element</span><span class="sxs-lookup"><span data-stu-id="a9117-124">Element</span></span>|<span data-ttu-id="a9117-125">Opis</span><span class="sxs-lookup"><span data-stu-id="a9117-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9117-126">\<> serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="a9117-126">\<serviceCertificate></span></span>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="a9117-127">Określa certyfikat, który ma być używany podczas uwierzytelniania usługi dla klienta.</span><span class="sxs-lookup"><span data-stu-id="a9117-127">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9117-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9117-128">Remarks</span></span>  
 <span data-ttu-id="a9117-129">Ta kolekcja umożliwia klientowi skonfigurowanie certyfikatów usługi do użycia na podstawie adresu URL usługi, z którą komunikuje się.</span><span class="sxs-lookup"><span data-stu-id="a9117-129">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="a9117-130">Jest to szczególnie przydatne w scenariuszach wystawionych tokenów, w których klient może komunikować się z wieloma usługami (usługą końcową oraz usługami tokenów zabezpieczających).</span><span class="sxs-lookup"><span data-stu-id="a9117-130">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="a9117-131">W przypadku powiązań korzystających z zabezpieczeń komunikatów opartych na certyfikatach ten certyfikat jest używany do szyfrowania komunikatów do usługi i powinien być używany przez usługę do podpisywania odpowiedzi do klienta.</span><span class="sxs-lookup"><span data-stu-id="a9117-131">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="a9117-132">Jeśli powiązanie wymaga certyfikatu dla usługi i nie zostanie znaleziony konkretny certyfikat dla adresu URL usługi w ScopedCertificates, zostanie użyty certyfikat domyślny.</span><span class="sxs-lookup"><span data-stu-id="a9117-132">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="a9117-133">Aby uzyskać więcej informacji, zobacz sekcję ["certyfikaty w zakresie", w jaki sposób: Utwórz klienta](../../../wcf/feature-details/how-to-create-a-federated-client.md)federacyjnego.</span><span class="sxs-lookup"><span data-stu-id="a9117-133">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9117-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9117-134">Example</span></span>  
 <span data-ttu-id="a9117-135">W poniższym przykładzie określono certyfikat usługi używany przez klienta podczas komunikacji z punktami końcowymi, których nazwa domeny `http://www.contoso.com` znajduje się za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="a9117-135">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
```xml  
<serviceCertificate>
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="a9117-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9117-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="a9117-137">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="a9117-137">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="a9117-138">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="a9117-138">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="a9117-139">\<add></span><span class="sxs-lookup"><span data-stu-id="a9117-139">\<add></span></span>](add-of-scopedcertificates-element.md)
- [<span data-ttu-id="a9117-140">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="a9117-140">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="a9117-141">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="a9117-141">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
