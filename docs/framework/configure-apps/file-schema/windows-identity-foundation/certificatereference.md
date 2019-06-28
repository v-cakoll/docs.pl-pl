---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: c7dc9cfff15e70eff0086cfd98a19f3360ab8bb0
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423026"
---
# <a name="certificatereference"></a><span data-ttu-id="d46e4-101">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="d46e4-101">\<certificateReference></span></span>
<span data-ttu-id="d46e4-102">Określa ustawienia, które są używane do znalezienia i sprawdź poprawność certyfikatu X.509 w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="d46e4-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="d46e4-103">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="d46e4-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="d46e4-104">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="d46e4-104">\<federationConfiguration></span></span>  
<span data-ttu-id="d46e4-105">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="d46e4-105">\<serviceCertificate></span></span>  
<span data-ttu-id="d46e4-106">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="d46e4-106">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d46e4-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="d46e4-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d46e4-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d46e4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d46e4-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d46e4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d46e4-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d46e4-110">Attributes</span></span>  
  
|<span data-ttu-id="d46e4-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d46e4-111">Attribute</span></span>|<span data-ttu-id="d46e4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d46e4-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d46e4-113">storeName</span><span class="sxs-lookup"><span data-stu-id="d46e4-113">storeName</span></span>|<span data-ttu-id="d46e4-114">Nazwa magazynu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="d46e4-114">The name of the X.509 certificate store.</span></span> <span data-ttu-id="d46e4-115">Wartość domyślna to "Moje".</span><span class="sxs-lookup"><span data-stu-id="d46e4-115">The default is "My".</span></span> <span data-ttu-id="d46e4-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d46e4-116">Optional.</span></span>|  
|<span data-ttu-id="d46e4-117">storeLocation</span><span class="sxs-lookup"><span data-stu-id="d46e4-117">storeLocation</span></span>|<span data-ttu-id="d46e4-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wartość, która określa lokalizację magazynu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="d46e4-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="d46e4-119">Wartość domyślna to "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="d46e4-119">The default value is "LocalMachine".</span></span> <span data-ttu-id="d46e4-120">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d46e4-120">Optional.</span></span>|  
|<span data-ttu-id="d46e4-121">x509FindType</span><span class="sxs-lookup"><span data-stu-id="d46e4-121">x509FindType</span></span>|<span data-ttu-id="d46e4-122"><xref:System.Security.Cryptography.X509Certificates.X509FindType> Wartość, która określa typ wyszukiwania, który ma zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="d46e4-122">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="d46e4-123">Wartość domyślna to "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="d46e4-123">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="d46e4-124">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d46e4-124">Optional.</span></span>|  
|<span data-ttu-id="d46e4-125">findValue</span><span class="sxs-lookup"><span data-stu-id="d46e4-125">findValue</span></span>|<span data-ttu-id="d46e4-126">Wartość do wyszukania w magazynie certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="d46e4-126">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="d46e4-127">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d46e4-127">Optional.</span></span>|  
|<span data-ttu-id="d46e4-128">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="d46e4-128">isChainIncluded</span></span>|<span data-ttu-id="d46e4-129">Określa, czy powinna być sprawdzana za pomocą łańcucha certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="d46e4-129">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="d46e4-130">Wartość domyślna to "true"; Sprawdzanie poprawności jest wykonywane przy użyciu łańcucha certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="d46e4-130">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="d46e4-131">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d46e4-131">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d46e4-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d46e4-132">Child Elements</span></span>  
 <span data-ttu-id="d46e4-133">Brak</span><span class="sxs-lookup"><span data-stu-id="d46e4-133">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d46e4-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d46e4-134">Parent Elements</span></span>  
  
|<span data-ttu-id="d46e4-135">Element</span><span class="sxs-lookup"><span data-stu-id="d46e4-135">Element</span></span>|<span data-ttu-id="d46e4-136">Opis</span><span class="sxs-lookup"><span data-stu-id="d46e4-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d46e4-137">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="d46e4-137">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="d46e4-138">Umożliwia skonfigurowanie certyfikatu, który jest używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="d46e4-138">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d46e4-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d46e4-139">Remarks</span></span>  
 <span data-ttu-id="d46e4-140">`<certificateReference>` Element określa ustawienia, które są używane do znalezienia i sprawdź poprawność certyfikatu X.509 w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="d46e4-140">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="d46e4-141">Gdy jest określony jako element podrzędny elementu `<serviceCertificate>` elementu, określa lokalizację i weryfikacja ustawienia certyfikatu X.509, który jest używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="d46e4-141">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="d46e4-142">`<certificateReference>` Element jest reprezentowany przez <xref:System.ServiceModel.Configuration.CertificateReferenceElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="d46e4-142">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
