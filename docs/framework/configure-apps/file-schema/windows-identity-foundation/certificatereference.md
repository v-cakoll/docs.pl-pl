---
title: '&lt;certificateReference&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: fd0d4742a162000d438851cef9c00e21368b7ba1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltcertificatereferencegt"></a><span data-ttu-id="2ee24-102">&lt;certificateReference&gt;</span><span class="sxs-lookup"><span data-stu-id="2ee24-102">&lt;certificateReference&gt;</span></span>
<span data-ttu-id="2ee24-103">Określa ustawienia, które są używane do znajdowania i zweryfikować certyfikatu w magazynie certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="2ee24-103">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="2ee24-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="2ee24-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="2ee24-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="2ee24-105">\<federationConfiguration></span></span>  
<span data-ttu-id="2ee24-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="2ee24-106">\<serviceCertificate></span></span>  
<span data-ttu-id="2ee24-107">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="2ee24-107">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ee24-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ee24-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ee24-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2ee24-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2ee24-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2ee24-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ee24-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2ee24-111">Attributes</span></span>  
  
|<span data-ttu-id="2ee24-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2ee24-112">Attribute</span></span>|<span data-ttu-id="2ee24-113">Opis</span><span class="sxs-lookup"><span data-stu-id="2ee24-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2ee24-114">storeName</span><span class="sxs-lookup"><span data-stu-id="2ee24-114">storeName</span></span>|<span data-ttu-id="2ee24-115">Nazwa magazynu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="2ee24-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="2ee24-116">Wartość domyślna to "Moje".</span><span class="sxs-lookup"><span data-stu-id="2ee24-116">The default is "My".</span></span> <span data-ttu-id="2ee24-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2ee24-117">Optional.</span></span>|  
|<span data-ttu-id="2ee24-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="2ee24-118">storeLocation</span></span>|<span data-ttu-id="2ee24-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wartość, która określa lokalizację magazynu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="2ee24-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="2ee24-120">Wartością domyślną jest "Komputer lokalny".</span><span class="sxs-lookup"><span data-stu-id="2ee24-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="2ee24-121">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2ee24-121">Optional.</span></span>|  
|<span data-ttu-id="2ee24-122">X509FindType</span><span class="sxs-lookup"><span data-stu-id="2ee24-122">x509FindType</span></span>|<span data-ttu-id="2ee24-123"><xref:System.Security.Cryptography.X509Certificates.X509FindType> Wartość, która określa typ wyszukiwania, która ma zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="2ee24-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="2ee24-124">Wartość domyślna to "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="2ee24-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="2ee24-125">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2ee24-125">Optional.</span></span>|  
|<span data-ttu-id="2ee24-126">findValue</span><span class="sxs-lookup"><span data-stu-id="2ee24-126">findValue</span></span>|<span data-ttu-id="2ee24-127">Wartość do wyszukania w magazynie certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="2ee24-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="2ee24-128">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2ee24-128">Optional.</span></span>|  
|<span data-ttu-id="2ee24-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="2ee24-129">isChainIncluded</span></span>|<span data-ttu-id="2ee24-130">Określa, czy Weryfikacja ma zostać wykonane przy użyciu łańcucha certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="2ee24-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="2ee24-131">Wartość domyślna to "true"; Sprawdzanie poprawności jest wykonywane przy użyciu łańcucha certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="2ee24-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="2ee24-132">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2ee24-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ee24-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2ee24-133">Child Elements</span></span>  
 <span data-ttu-id="2ee24-134">Brak</span><span class="sxs-lookup"><span data-stu-id="2ee24-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ee24-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2ee24-135">Parent Elements</span></span>  
  
|<span data-ttu-id="2ee24-136">Element</span><span class="sxs-lookup"><span data-stu-id="2ee24-136">Element</span></span>|<span data-ttu-id="2ee24-137">Opis</span><span class="sxs-lookup"><span data-stu-id="2ee24-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ee24-138">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="2ee24-138">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="2ee24-139">Określa certyfikat, który jest używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="2ee24-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ee24-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ee24-140">Remarks</span></span>  
 <span data-ttu-id="2ee24-141">`<certificateReference>` Element określa ustawienia, które są używane do znajdowania i zweryfikować certyfikatu w magazynie certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="2ee24-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="2ee24-142">Jeśli jest określony jako element podrzędny elementu `<serviceCertficate>` elementu, określa ustawienia lokalizacji i weryfikacja certyfikatu X.509, który jest używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="2ee24-142">When it is specified as the child element of the `<serviceCertficate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="2ee24-143">`<certificateReference>` Reprezentowany przez element <xref:System.ServiceModel.Configuration.CertificateReferenceElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="2ee24-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
