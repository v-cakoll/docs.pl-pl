---
title: <scopedCertificates>, element
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: de85b3230461e876ec48e98887805d767e981e0f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270406"
---
# <a name="scopedcertificates-element"></a><span data-ttu-id="879b2-102">\<scopedCertificates> Element</span><span class="sxs-lookup"><span data-stu-id="879b2-102">\<scopedCertificates> Element</span></span>
<span data-ttu-id="879b2-103">Reprezentuje kolekcję certyfikatów X.509 dostarczonych przez określone usługi (w zakresie) do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="879b2-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="879b2-104">Ta kolekcja jest zazwyczaj pozwala ustalić certyfikaty usługi usługi tokenu zabezpieczeń w federacyjnym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="879b2-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
 <span data-ttu-id="879b2-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="879b2-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="879b2-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="879b2-106">\<behaviors></span></span>  
<span data-ttu-id="879b2-107">sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="879b2-107">endpointBehaviors section</span></span>  
<span data-ttu-id="879b2-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="879b2-108">\<behavior></span></span>  
<span data-ttu-id="879b2-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="879b2-109">\<clientCredentials></span></span>  
<span data-ttu-id="879b2-110">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="879b2-110">\<serviceCertificate></span></span>  
<span data-ttu-id="879b2-111">\<scopedCertificates> Element</span><span class="sxs-lookup"><span data-stu-id="879b2-111">\<scopedCertificates> Element</span></span>  
<span data-ttu-id="879b2-112">\<Dodaj >, element dla \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="879b2-112">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="879b2-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="879b2-113">Syntax</span></span>  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="879b2-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="879b2-114">Attributes and Elements</span></span>  
 <span data-ttu-id="879b2-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="879b2-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="879b2-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="879b2-116">Attributes</span></span>  
 <span data-ttu-id="879b2-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="879b2-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="879b2-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="879b2-118">Child Elements</span></span>  
  
|<span data-ttu-id="879b2-119">Element</span><span class="sxs-lookup"><span data-stu-id="879b2-119">Element</span></span>|<span data-ttu-id="879b2-120">Opis</span><span class="sxs-lookup"><span data-stu-id="879b2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="879b2-121">\<add></span><span class="sxs-lookup"><span data-stu-id="879b2-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)|<span data-ttu-id="879b2-122">Dodaje certyfikat X.509 do kolekcji certyfikatów będących w zakresie.</span><span class="sxs-lookup"><span data-stu-id="879b2-122">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="879b2-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="879b2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="879b2-124">Element</span><span class="sxs-lookup"><span data-stu-id="879b2-124">Element</span></span>|<span data-ttu-id="879b2-125">Opis</span><span class="sxs-lookup"><span data-stu-id="879b2-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="879b2-126">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="879b2-126">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="879b2-127">Określa certyfikat używany podczas uwierzytelniania usługi dla klienta.</span><span class="sxs-lookup"><span data-stu-id="879b2-127">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="879b2-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="879b2-128">Remarks</span></span>  
 <span data-ttu-id="879b2-129">Ta kolekcja umożliwia klienta skonfigurować certyfikaty usługi do użycia na podstawie adresu URL usługi, którym się komunikuje.</span><span class="sxs-lookup"><span data-stu-id="879b2-129">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="879b2-130">Jest to szczególnie przydatne w wystawionych tokenów scenariuszach, gdzie klienta może się komunikować z wielu usług (service zakończenia także usługach tokenów zabezpieczeń pośrednie).</span><span class="sxs-lookup"><span data-stu-id="879b2-130">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="879b2-131">Dla powiązań, które korzystają z zabezpieczeń komunikatów opartego na certyfikatach ten certyfikat jest używany do szyfrowania komunikatów do usługi, a powinien być używany przez usługę do podpisywania odpowiedzi do klienta.</span><span class="sxs-lookup"><span data-stu-id="879b2-131">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="879b2-132">Jeśli powiązanie wymaga certyfikatu dla usługi i nie określonego certyfikatu dla usługi, którą można odnaleźć adresu URL w ScopedCertificates, jest używany certyfikat domyślny.</span><span class="sxs-lookup"><span data-stu-id="879b2-132">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="879b2-133">Aby uzyskać więcej informacji, zobacz sekcję "O zakresie certyfikatów" [jak: Tworzenie klienta federacyjnego](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="879b2-133">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="879b2-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="879b2-134">Example</span></span>  
 <span data-ttu-id="879b2-135">W poniższym przykładzie określono certyfikatu usługi dla klientów do użycia podczas komunikowania się z punktami końcowymi, których nazwa domeny jest `http://www.contoso.com` za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="879b2-135">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="879b2-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="879b2-136">See also</span></span>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="879b2-137">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="879b2-137">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="879b2-138">Instrukcje: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="879b2-138">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="879b2-139">\<add></span><span class="sxs-lookup"><span data-stu-id="879b2-139">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)
- [<span data-ttu-id="879b2-140">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="879b2-140">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="879b2-141">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="879b2-141">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
