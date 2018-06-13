---
title: '&lt;certificateReference&gt;'
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e0f9a826a4c8d292346d9efee7970a82b88fb612
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756842"
---
# <a name="ltcertificatereferencegt"></a><span data-ttu-id="391e3-102">&lt;certificateReference&gt;</span><span class="sxs-lookup"><span data-stu-id="391e3-102">&lt;certificateReference&gt;</span></span>
<span data-ttu-id="391e3-103">Określa ustawienia, które są używane do znajdowania i zweryfikować certyfikatu w magazynie certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="391e3-103">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="391e3-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="391e3-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="391e3-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="391e3-105">\<federationConfiguration></span></span>  
<span data-ttu-id="391e3-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="391e3-106">\<serviceCertificate></span></span>  
<span data-ttu-id="391e3-107">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="391e3-107">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="391e3-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="391e3-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="391e3-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="391e3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="391e3-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="391e3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="391e3-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="391e3-111">Attributes</span></span>  
  
|<span data-ttu-id="391e3-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="391e3-112">Attribute</span></span>|<span data-ttu-id="391e3-113">Opis</span><span class="sxs-lookup"><span data-stu-id="391e3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="391e3-114">storeName</span><span class="sxs-lookup"><span data-stu-id="391e3-114">storeName</span></span>|<span data-ttu-id="391e3-115">Nazwa magazynu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="391e3-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="391e3-116">Wartość domyślna to "Moje".</span><span class="sxs-lookup"><span data-stu-id="391e3-116">The default is "My".</span></span> <span data-ttu-id="391e3-117">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="391e3-117">Optional.</span></span>|  
|<span data-ttu-id="391e3-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="391e3-118">storeLocation</span></span>|<span data-ttu-id="391e3-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wartość, która określa lokalizację magazynu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="391e3-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="391e3-120">Wartością domyślną jest "Komputer lokalny".</span><span class="sxs-lookup"><span data-stu-id="391e3-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="391e3-121">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="391e3-121">Optional.</span></span>|  
|<span data-ttu-id="391e3-122">X509FindType</span><span class="sxs-lookup"><span data-stu-id="391e3-122">x509FindType</span></span>|<span data-ttu-id="391e3-123"><xref:System.Security.Cryptography.X509Certificates.X509FindType> Wartość, która określa typ wyszukiwania, która ma zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="391e3-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="391e3-124">Wartość domyślna to "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="391e3-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="391e3-125">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="391e3-125">Optional.</span></span>|  
|<span data-ttu-id="391e3-126">findValue</span><span class="sxs-lookup"><span data-stu-id="391e3-126">findValue</span></span>|<span data-ttu-id="391e3-127">Wartość do wyszukania w magazynie certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="391e3-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="391e3-128">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="391e3-128">Optional.</span></span>|  
|<span data-ttu-id="391e3-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="391e3-129">isChainIncluded</span></span>|<span data-ttu-id="391e3-130">Określa, czy Weryfikacja ma zostać wykonane przy użyciu łańcucha certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="391e3-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="391e3-131">Wartość domyślna to "true"; Sprawdzanie poprawności jest wykonywane przy użyciu łańcucha certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="391e3-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="391e3-132">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="391e3-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="391e3-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="391e3-133">Child Elements</span></span>  
 <span data-ttu-id="391e3-134">Brak</span><span class="sxs-lookup"><span data-stu-id="391e3-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="391e3-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="391e3-135">Parent Elements</span></span>  
  
|<span data-ttu-id="391e3-136">Element</span><span class="sxs-lookup"><span data-stu-id="391e3-136">Element</span></span>|<span data-ttu-id="391e3-137">Opis</span><span class="sxs-lookup"><span data-stu-id="391e3-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="391e3-138">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="391e3-138">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="391e3-139">Określa certyfikat, który jest używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="391e3-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="391e3-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="391e3-140">Remarks</span></span>  
 <span data-ttu-id="391e3-141">`<certificateReference>` Element określa ustawienia, które są używane do znajdowania i zweryfikować certyfikatu w magazynie certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="391e3-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="391e3-142">Jeśli jest określony jako element podrzędny elementu `<serviceCertficate>` elementu, określa ustawienia lokalizacji i weryfikacja certyfikatu X.509, który jest używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="391e3-142">When it is specified as the child element of the `<serviceCertficate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="391e3-143">`<certificateReference>` Reprezentowany przez element <xref:System.ServiceModel.Configuration.CertificateReferenceElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="391e3-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
