---
title: '&lt;scopedCertificates&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5cb1d536d25186dd2d75cec962143b16cdd45260
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltscopedcertificatesgt-element"></a><span data-ttu-id="2c40d-102">&lt;scopedCertificates&gt;, element</span><span class="sxs-lookup"><span data-stu-id="2c40d-102">&lt;scopedCertificates&gt; Element</span></span>
<span data-ttu-id="2c40d-103">Reprezentuje kolekcję certyfikatów X.509 dostarczonych przez określone usługi (w zakresie) do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="2c40d-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="2c40d-104">Ta kolekcja jest zwykle można określić certyfikaty usługi dla usługi tokenu zabezpieczeń w federacyjnym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="2c40d-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
 <span data-ttu-id="2c40d-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2c40d-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="2c40d-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="2c40d-106">\<behaviors></span></span>  
<span data-ttu-id="2c40d-107">sekcja endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="2c40d-107">endpointBehaviors section</span></span>  
<span data-ttu-id="2c40d-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="2c40d-108">\<behavior></span></span>  
<span data-ttu-id="2c40d-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="2c40d-109">\<clientCredentials></span></span>  
<span data-ttu-id="2c40d-110">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="2c40d-110">\<serviceCertificate></span></span>  
<span data-ttu-id="2c40d-111">\<scopedCertificates > — Element</span><span class="sxs-lookup"><span data-stu-id="2c40d-111">\<scopedCertificates> Element</span></span>  
<span data-ttu-id="2c40d-112">\<Dodaj > elementu \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="2c40d-112">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c40d-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c40d-113">Syntax</span></span>  
  
```xml  
<scopedCertificates>  
      <add findValue="String"  
                storeLocation="CurrentUser/LocalMachine"  
                storeName=" CurrentUser/LocalMachine"  
                targetUri="string"  
            x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />   
</scopedCertificates>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c40d-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2c40d-114">Attributes and Elements</span></span>  
 <span data-ttu-id="2c40d-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2c40d-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c40d-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2c40d-116">Attributes</span></span>  
 <span data-ttu-id="2c40d-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="2c40d-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2c40d-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2c40d-118">Child Elements</span></span>  
  
|<span data-ttu-id="2c40d-119">Element</span><span class="sxs-lookup"><span data-stu-id="2c40d-119">Element</span></span>|<span data-ttu-id="2c40d-120">Opis</span><span class="sxs-lookup"><span data-stu-id="2c40d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c40d-121">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="2c40d-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)|<span data-ttu-id="2c40d-122">Dodaje certyfikat X.509 do kolekcji certyfikatów będących w zakresie.</span><span class="sxs-lookup"><span data-stu-id="2c40d-122">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2c40d-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2c40d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2c40d-124">Element</span><span class="sxs-lookup"><span data-stu-id="2c40d-124">Element</span></span>|<span data-ttu-id="2c40d-125">Opis</span><span class="sxs-lookup"><span data-stu-id="2c40d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c40d-126">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="2c40d-126">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="2c40d-127">Określa certyfikat używany podczas uwierzytelniania usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="2c40d-127">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c40d-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2c40d-128">Remarks</span></span>  
 <span data-ttu-id="2c40d-129">Ta kolekcja umożliwia klientowi skonfigurować certyfikaty usługi do użycia na podstawie adresu URL usługi, z którym się komunikuje.</span><span class="sxs-lookup"><span data-stu-id="2c40d-129">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="2c40d-130">Jest to szczególnie przydatne w wystawionego tokenu scenariuszach, gdzie klient może komunikować się wiele usług (usług a także usługi tokenu zabezpieczeń pośredniczące).</span><span class="sxs-lookup"><span data-stu-id="2c40d-130">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="2c40d-131">Dla powiązań, które korzystają z zabezpieczeń wiadomości opartego na certyfikatach ten certyfikat jest używany do szyfrowania wiadomości do usługi, a powinien być używany przez usługę do podpisywania odpowiedzi do klienta.</span><span class="sxs-lookup"><span data-stu-id="2c40d-131">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="2c40d-132">Jeśli powiązanie wymaga certyfikatu dla usługi i nie określonego certyfikatu dla usługi, którą można odnaleźć adresu URL w ScopedCertificates, jest używany certyfikat domyślny.</span><span class="sxs-lookup"><span data-stu-id="2c40d-132">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="2c40d-133">Aby uzyskać więcej informacji, zobacz sekcję "O zakresie certyfikatów" [porady: Tworzenie klienta federacyjnego](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="2c40d-133">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c40d-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c40d-134">Example</span></span>  
 <span data-ttu-id="2c40d-135">W poniższym przykładzie certyfikat usługi dla klienta do użycia przy komunikacji z punktami końcowymi, których nazwa domeny jest http://www.contoso.com za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="2c40d-135">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is http://www.contoso.com over the HTTP protocol.</span></span>  
  
```xml  
<serviceCertificate>  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
</serviceCertificate>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c40d-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c40d-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>  
 [<span data-ttu-id="2c40d-137">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="2c40d-137">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="2c40d-138">Porady: Tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="2c40d-138">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="2c40d-139">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="2c40d-139">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)  
 [<span data-ttu-id="2c40d-140">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="2c40d-140">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="2c40d-141">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="2c40d-141">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
