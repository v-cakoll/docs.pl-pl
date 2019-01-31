---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 6c9c77f96ff6032de43d9b5a257bc0796a19b858
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269344"
---
# <a name="certificatereference"></a><span data-ttu-id="211ce-101">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="211ce-101">\<certificateReference></span></span>
<span data-ttu-id="211ce-102">Określa ustawienia, które są używane do znalezienia i sprawdź poprawność certyfikatu X.509 w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="211ce-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="211ce-103">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="211ce-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="211ce-104">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="211ce-104">\<federationConfiguration></span></span>  
<span data-ttu-id="211ce-105">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="211ce-105">\<serviceCertificate></span></span>  
<span data-ttu-id="211ce-106">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="211ce-106">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="211ce-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="211ce-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference   
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="211ce-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="211ce-108">Attributes and Elements</span></span>  
 <span data-ttu-id="211ce-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="211ce-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="211ce-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="211ce-110">Attributes</span></span>  
  
|<span data-ttu-id="211ce-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="211ce-111">Attribute</span></span>|<span data-ttu-id="211ce-112">Opis</span><span class="sxs-lookup"><span data-stu-id="211ce-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="211ce-113">storeName</span><span class="sxs-lookup"><span data-stu-id="211ce-113">storeName</span></span>|<span data-ttu-id="211ce-114">Nazwa magazynu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="211ce-114">The name of the X.509 certificate store.</span></span> <span data-ttu-id="211ce-115">Wartość domyślna to "Moje".</span><span class="sxs-lookup"><span data-stu-id="211ce-115">The default is "My".</span></span> <span data-ttu-id="211ce-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="211ce-116">Optional.</span></span>|  
|<span data-ttu-id="211ce-117">storeLocation</span><span class="sxs-lookup"><span data-stu-id="211ce-117">storeLocation</span></span>|<span data-ttu-id="211ce-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wartość, która określa lokalizację magazynu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="211ce-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="211ce-119">Wartość domyślna to "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="211ce-119">The default value is "LocalMachine".</span></span> <span data-ttu-id="211ce-120">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="211ce-120">Optional.</span></span>|  
|<span data-ttu-id="211ce-121">x509FindType</span><span class="sxs-lookup"><span data-stu-id="211ce-121">x509FindType</span></span>|<span data-ttu-id="211ce-122"><xref:System.Security.Cryptography.X509Certificates.X509FindType> Wartość, która określa typ wyszukiwania, który ma zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="211ce-122">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="211ce-123">Wartość domyślna to "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="211ce-123">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="211ce-124">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="211ce-124">Optional.</span></span>|  
|<span data-ttu-id="211ce-125">findValue</span><span class="sxs-lookup"><span data-stu-id="211ce-125">findValue</span></span>|<span data-ttu-id="211ce-126">Wartość do wyszukania w magazynie certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="211ce-126">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="211ce-127">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="211ce-127">Optional.</span></span>|  
|<span data-ttu-id="211ce-128">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="211ce-128">isChainIncluded</span></span>|<span data-ttu-id="211ce-129">Określa, czy powinna być sprawdzana za pomocą łańcucha certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="211ce-129">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="211ce-130">Wartość domyślna to "true"; Sprawdzanie poprawności jest wykonywane przy użyciu łańcucha certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="211ce-130">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="211ce-131">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="211ce-131">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="211ce-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="211ce-132">Child Elements</span></span>  
 <span data-ttu-id="211ce-133">Brak</span><span class="sxs-lookup"><span data-stu-id="211ce-133">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="211ce-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="211ce-134">Parent Elements</span></span>  
  
|<span data-ttu-id="211ce-135">Element</span><span class="sxs-lookup"><span data-stu-id="211ce-135">Element</span></span>|<span data-ttu-id="211ce-136">Opis</span><span class="sxs-lookup"><span data-stu-id="211ce-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="211ce-137">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="211ce-137">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="211ce-138">Umożliwia skonfigurowanie certyfikatu, który jest używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="211ce-138">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="211ce-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="211ce-139">Remarks</span></span>  
 <span data-ttu-id="211ce-140">`<certificateReference>` Element określa ustawienia, które są używane do znalezienia i sprawdź poprawność certyfikatu X.509 w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="211ce-140">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="211ce-141">Gdy jest określony jako element podrzędny elementu `<serviceCertficate>` elementu, określa lokalizację i weryfikacja ustawienia certyfikatu X.509, który jest używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="211ce-141">When it is specified as the child element of the `<serviceCertficate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="211ce-142">`<certificateReference>` Element jest reprezentowany przez <xref:System.ServiceModel.Configuration.CertificateReferenceElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="211ce-142">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
