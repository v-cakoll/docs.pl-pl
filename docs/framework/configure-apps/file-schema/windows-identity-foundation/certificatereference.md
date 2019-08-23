---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: da8ea128466457409334cd0b4ee3246a923f969a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941930"
---
# <a name="certificatereference"></a><span data-ttu-id="57403-101">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="57403-101">\<certificateReference></span></span>
<span data-ttu-id="57403-102">Określa ustawienia, które są używane do znajdowania i weryfikowania certyfikatu X. 509 w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="57403-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="57403-103">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="57403-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="57403-104">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="57403-104">\<federationConfiguration></span></span>  
<span data-ttu-id="57403-105">\<> serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="57403-105">\<serviceCertificate></span></span>  
<span data-ttu-id="57403-106">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="57403-106">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57403-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="57403-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57403-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="57403-108">Attributes and Elements</span></span>  
 <span data-ttu-id="57403-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="57403-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57403-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="57403-110">Attributes</span></span>  
  
|<span data-ttu-id="57403-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="57403-111">Attribute</span></span>|<span data-ttu-id="57403-112">Opis</span><span class="sxs-lookup"><span data-stu-id="57403-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="57403-113">storeName</span><span class="sxs-lookup"><span data-stu-id="57403-113">storeName</span></span>|<span data-ttu-id="57403-114">Nazwa magazynu certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="57403-114">The name of the X.509 certificate store.</span></span> <span data-ttu-id="57403-115">Wartość domyślna to "my".</span><span class="sxs-lookup"><span data-stu-id="57403-115">The default is "My".</span></span> <span data-ttu-id="57403-116">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="57403-116">Optional.</span></span>|  
|<span data-ttu-id="57403-117">storeLocation</span><span class="sxs-lookup"><span data-stu-id="57403-117">storeLocation</span></span>|<span data-ttu-id="57403-118"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Wartość, która określa lokalizację magazynu certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="57403-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="57403-119">Wartość domyślna to "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="57403-119">The default value is "LocalMachine".</span></span> <span data-ttu-id="57403-120">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="57403-120">Optional.</span></span>|  
|<span data-ttu-id="57403-121">x509FindType</span><span class="sxs-lookup"><span data-stu-id="57403-121">x509FindType</span></span>|<span data-ttu-id="57403-122"><xref:System.Security.Cryptography.X509Certificates.X509FindType> Wartość określająca typ wyszukiwania, które ma zostać wykonane.</span><span class="sxs-lookup"><span data-stu-id="57403-122">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="57403-123">Wartość domyślna to "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="57403-123">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="57403-124">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="57403-124">Optional.</span></span>|  
|<span data-ttu-id="57403-125">findValue</span><span class="sxs-lookup"><span data-stu-id="57403-125">findValue</span></span>|<span data-ttu-id="57403-126">Wartość do wyszukania w magazynie certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="57403-126">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="57403-127">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="57403-127">Optional.</span></span>|  
|<span data-ttu-id="57403-128">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="57403-128">isChainIncluded</span></span>|<span data-ttu-id="57403-129">Określa, czy należy przeprowadzić walidację przy użyciu łańcucha certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="57403-129">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="57403-130">Wartość domyślna to "true"; Walidacja jest przeprowadzana przy użyciu łańcucha certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="57403-130">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="57403-131">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="57403-131">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57403-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="57403-132">Child Elements</span></span>  
 <span data-ttu-id="57403-133">Brak</span><span class="sxs-lookup"><span data-stu-id="57403-133">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="57403-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="57403-134">Parent Elements</span></span>  
  
|<span data-ttu-id="57403-135">Element</span><span class="sxs-lookup"><span data-stu-id="57403-135">Element</span></span>|<span data-ttu-id="57403-136">Opis</span><span class="sxs-lookup"><span data-stu-id="57403-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57403-137">\<> serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="57403-137">\<serviceCertificate></span></span>](servicecertificate.md)|<span data-ttu-id="57403-138">Konfiguruje certyfikat używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="57403-138">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57403-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="57403-139">Remarks</span></span>  
 <span data-ttu-id="57403-140">`<certificateReference>` Element określa ustawienia, które są używane do znajdowania i weryfikowania certyfikatu X. 509 w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="57403-140">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="57403-141">Gdy jest określony jako element `<serviceCertificate>` podrzędny elementu, określa lokalizację i ustawienia weryfikacji certyfikatu X. 509, który jest używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="57403-141">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="57403-142">Element jest reprezentowany <xref:System.ServiceModel.Configuration.CertificateReferenceElement> przez klasę. `<certificateReference>`</span><span class="sxs-lookup"><span data-stu-id="57403-142">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
