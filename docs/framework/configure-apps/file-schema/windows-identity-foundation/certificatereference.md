---
title: '&lt;certificateReference&gt;'
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: e04dc90134aadfb8af7b0800c7144963d267f513
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075086"
---
# <a name="ltcertificatereferencegt"></a><span data-ttu-id="70c8d-102">&lt;certificateReference&gt;</span><span class="sxs-lookup"><span data-stu-id="70c8d-102">&lt;certificateReference&gt;</span></span>
<span data-ttu-id="70c8d-103">Określa ustawienia, które są używane do znalezienia i sprawdź poprawność certyfikatu X.509 w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="70c8d-103">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="70c8d-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="70c8d-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="70c8d-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="70c8d-105">\<federationConfiguration></span></span>  
<span data-ttu-id="70c8d-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="70c8d-106">\<serviceCertificate></span></span>  
<span data-ttu-id="70c8d-107">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="70c8d-107">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70c8d-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="70c8d-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70c8d-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="70c8d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="70c8d-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="70c8d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70c8d-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="70c8d-111">Attributes</span></span>  
  
|<span data-ttu-id="70c8d-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="70c8d-112">Attribute</span></span>|<span data-ttu-id="70c8d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="70c8d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="70c8d-114">storeName</span><span class="sxs-lookup"><span data-stu-id="70c8d-114">storeName</span></span>|<span data-ttu-id="70c8d-115">Nazwa magazynu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="70c8d-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="70c8d-116">Wartość domyślna to "Moje".</span><span class="sxs-lookup"><span data-stu-id="70c8d-116">The default is "My".</span></span> <span data-ttu-id="70c8d-117">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="70c8d-117">Optional.</span></span>|  
|<span data-ttu-id="70c8d-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="70c8d-118">storeLocation</span></span>|<span data-ttu-id="70c8d-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wartość, która określa lokalizację magazynu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="70c8d-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="70c8d-120">Wartość domyślna to "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="70c8d-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="70c8d-121">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="70c8d-121">Optional.</span></span>|  
|<span data-ttu-id="70c8d-122">X509FindType</span><span class="sxs-lookup"><span data-stu-id="70c8d-122">x509FindType</span></span>|<span data-ttu-id="70c8d-123"><xref:System.Security.Cryptography.X509Certificates.X509FindType> Wartość, która określa typ wyszukiwania, który ma zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="70c8d-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="70c8d-124">Wartość domyślna to "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="70c8d-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="70c8d-125">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="70c8d-125">Optional.</span></span>|  
|<span data-ttu-id="70c8d-126">findValue</span><span class="sxs-lookup"><span data-stu-id="70c8d-126">findValue</span></span>|<span data-ttu-id="70c8d-127">Wartość do wyszukania w magazynie certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="70c8d-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="70c8d-128">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="70c8d-128">Optional.</span></span>|  
|<span data-ttu-id="70c8d-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="70c8d-129">isChainIncluded</span></span>|<span data-ttu-id="70c8d-130">Określa, czy powinna być sprawdzana za pomocą łańcucha certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="70c8d-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="70c8d-131">Wartość domyślna to "true"; Sprawdzanie poprawności jest wykonywane przy użyciu łańcucha certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="70c8d-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="70c8d-132">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="70c8d-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70c8d-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="70c8d-133">Child Elements</span></span>  
 <span data-ttu-id="70c8d-134">Brak</span><span class="sxs-lookup"><span data-stu-id="70c8d-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="70c8d-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="70c8d-135">Parent Elements</span></span>  
  
|<span data-ttu-id="70c8d-136">Element</span><span class="sxs-lookup"><span data-stu-id="70c8d-136">Element</span></span>|<span data-ttu-id="70c8d-137">Opis</span><span class="sxs-lookup"><span data-stu-id="70c8d-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70c8d-138">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="70c8d-138">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="70c8d-139">Umożliwia skonfigurowanie certyfikatu, który jest używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="70c8d-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70c8d-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70c8d-140">Remarks</span></span>  
 <span data-ttu-id="70c8d-141">`<certificateReference>` Element określa ustawienia, które są używane do znalezienia i sprawdź poprawność certyfikatu X.509 w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="70c8d-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="70c8d-142">Gdy jest określony jako element podrzędny elementu `<serviceCertficate>` elementu, określa lokalizację i weryfikacja ustawienia certyfikatu X.509, który jest używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="70c8d-142">When it is specified as the child element of the `<serviceCertficate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="70c8d-143">`<certificateReference>` Element jest reprezentowany przez <xref:System.ServiceModel.Configuration.CertificateReferenceElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="70c8d-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
