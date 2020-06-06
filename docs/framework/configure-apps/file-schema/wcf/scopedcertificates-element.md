---
title: <scopedCertificates> Element
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: 3c06159709df0afe2a475de1e186b0114af32bc2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399955"
---
# <a name="scopedcertificates-element"></a><span data-ttu-id="c89ae-102">\<scopedCertificates> Element</span><span class="sxs-lookup"><span data-stu-id="c89ae-102">\<scopedCertificates> Element</span></span>
<span data-ttu-id="c89ae-103">Reprezentuje kolekcję certyfikatów X. 509 dostarczonych przez określone usługi (w zakresie) do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c89ae-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="c89ae-104">Ta kolekcja jest zwykle używana do określania certyfikatów usługi dla usług tokenów zabezpieczających w scenariuszu federacyjnym.</span><span class="sxs-lookup"><span data-stu-id="c89ae-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopedCertificates>**  
  
## <a name="syntax"></a><span data-ttu-id="c89ae-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c89ae-105">Syntax</span></span>  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c89ae-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c89ae-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c89ae-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c89ae-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c89ae-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c89ae-108">Attributes</span></span>  
 <span data-ttu-id="c89ae-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="c89ae-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c89ae-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c89ae-110">Child Elements</span></span>  
  
|<span data-ttu-id="c89ae-111">Element</span><span class="sxs-lookup"><span data-stu-id="c89ae-111">Element</span></span>|<span data-ttu-id="c89ae-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c89ae-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-scopedcertificates-element.md)|<span data-ttu-id="c89ae-113">Dodaje certyfikat X. 509 do kolekcji certyfikatów z zakresem.</span><span class="sxs-lookup"><span data-stu-id="c89ae-113">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c89ae-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c89ae-114">Parent Elements</span></span>  
  
|<span data-ttu-id="c89ae-115">Element</span><span class="sxs-lookup"><span data-stu-id="c89ae-115">Element</span></span>|<span data-ttu-id="c89ae-116">Opis</span><span class="sxs-lookup"><span data-stu-id="c89ae-116">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="c89ae-117">Określa certyfikat, który ma być używany podczas uwierzytelniania usługi dla klienta.</span><span class="sxs-lookup"><span data-stu-id="c89ae-117">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c89ae-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c89ae-118">Remarks</span></span>  
 <span data-ttu-id="c89ae-119">Ta kolekcja umożliwia klientowi skonfigurowanie certyfikatów usługi do użycia na podstawie adresu URL usługi, z którą komunikuje się.</span><span class="sxs-lookup"><span data-stu-id="c89ae-119">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="c89ae-120">Jest to szczególnie przydatne w scenariuszach wystawionych tokenów, w których klient może komunikować się z wieloma usługami (usługą końcową oraz usługami tokenów zabezpieczających).</span><span class="sxs-lookup"><span data-stu-id="c89ae-120">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="c89ae-121">W przypadku powiązań korzystających z zabezpieczeń komunikatów opartych na certyfikatach ten certyfikat jest używany do szyfrowania komunikatów do usługi i powinien być używany przez usługę do podpisywania odpowiedzi do klienta.</span><span class="sxs-lookup"><span data-stu-id="c89ae-121">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="c89ae-122">Jeśli powiązanie wymaga certyfikatu dla usługi i nie zostanie znaleziony konkretny certyfikat dla adresu URL usługi w ScopedCertificates, zostanie użyty certyfikat domyślny.</span><span class="sxs-lookup"><span data-stu-id="c89ae-122">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="c89ae-123">Aby uzyskać więcej informacji, zobacz sekcję "certyfikaty w zakresie" w temacie [How to: Create a Federation Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="c89ae-123">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c89ae-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="c89ae-124">Example</span></span>  
 <span data-ttu-id="c89ae-125">W poniższym przykładzie określono certyfikat usługi używany przez klienta podczas komunikacji z punktami końcowymi, których nazwa domeny znajduje się `http://www.contoso.com` za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="c89ae-125">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c89ae-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c89ae-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="c89ae-127">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="c89ae-127">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="c89ae-128">Instrukcje: tworzenie klienta federacyjnego</span><span class="sxs-lookup"><span data-stu-id="c89ae-128">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [\<add>](add-of-scopedcertificates-element.md)
- [<span data-ttu-id="c89ae-129">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="c89ae-129">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="c89ae-130">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="c89ae-130">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
