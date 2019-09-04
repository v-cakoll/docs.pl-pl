---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 782ca3344774b8412a18e3cf13bff5f969751ea3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252143"
---
# <a name="certificatereference"></a><span data-ttu-id="8982e-101">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="8982e-101">\<certificateReference></span></span>
<span data-ttu-id="8982e-102">Określa ustawienia, które są używane do znajdowania i weryfikowania certyfikatu X. 509 w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="8982e-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
<span data-ttu-id="8982e-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8982e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8982e-104">&nbsp;&nbsp;[ **\<> System. identityModel. Services**](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="8982e-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="8982e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="8982e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="8982e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceCertificate**](servicecertificate.md)</span><span class="sxs-lookup"><span data-stu-id="8982e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)</span></span>\
<span data-ttu-id="8982e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<certificateReference >**</span><span class="sxs-lookup"><span data-stu-id="8982e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8982e-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="8982e-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8982e-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8982e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8982e-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8982e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8982e-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8982e-111">Attributes</span></span>  
  
|<span data-ttu-id="8982e-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8982e-112">Attribute</span></span>|<span data-ttu-id="8982e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="8982e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8982e-114">storeName</span><span class="sxs-lookup"><span data-stu-id="8982e-114">storeName</span></span>|<span data-ttu-id="8982e-115">Nazwa magazynu certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="8982e-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="8982e-116">Wartość domyślna to "my".</span><span class="sxs-lookup"><span data-stu-id="8982e-116">The default is "My".</span></span> <span data-ttu-id="8982e-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8982e-117">Optional.</span></span>|  
|<span data-ttu-id="8982e-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="8982e-118">storeLocation</span></span>|<span data-ttu-id="8982e-119"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Wartość, która określa lokalizację magazynu certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="8982e-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="8982e-120">Wartość domyślna to "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="8982e-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="8982e-121">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="8982e-121">Optional.</span></span>|  
|<span data-ttu-id="8982e-122">x509FindType</span><span class="sxs-lookup"><span data-stu-id="8982e-122">x509FindType</span></span>|<span data-ttu-id="8982e-123"><xref:System.Security.Cryptography.X509Certificates.X509FindType> Wartość określająca typ wyszukiwania, które ma zostać wykonane.</span><span class="sxs-lookup"><span data-stu-id="8982e-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="8982e-124">Wartość domyślna to "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="8982e-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="8982e-125">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8982e-125">Optional.</span></span>|  
|<span data-ttu-id="8982e-126">findValue</span><span class="sxs-lookup"><span data-stu-id="8982e-126">findValue</span></span>|<span data-ttu-id="8982e-127">Wartość do wyszukania w magazynie certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="8982e-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="8982e-128">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="8982e-128">Optional.</span></span>|  
|<span data-ttu-id="8982e-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="8982e-129">isChainIncluded</span></span>|<span data-ttu-id="8982e-130">Określa, czy należy przeprowadzić walidację przy użyciu łańcucha certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="8982e-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="8982e-131">Wartość domyślna to "true"; Walidacja jest przeprowadzana przy użyciu łańcucha certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="8982e-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="8982e-132">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8982e-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8982e-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8982e-133">Child Elements</span></span>  
 <span data-ttu-id="8982e-134">Brak</span><span class="sxs-lookup"><span data-stu-id="8982e-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8982e-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8982e-135">Parent Elements</span></span>  
  
|<span data-ttu-id="8982e-136">Element</span><span class="sxs-lookup"><span data-stu-id="8982e-136">Element</span></span>|<span data-ttu-id="8982e-137">Opis</span><span class="sxs-lookup"><span data-stu-id="8982e-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8982e-138">\<> serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="8982e-138">\<serviceCertificate></span></span>](servicecertificate.md)|<span data-ttu-id="8982e-139">Konfiguruje certyfikat używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="8982e-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8982e-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8982e-140">Remarks</span></span>  
 <span data-ttu-id="8982e-141">`<certificateReference>` Element określa ustawienia, które są używane do znajdowania i weryfikowania certyfikatu X. 509 w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="8982e-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="8982e-142">Gdy jest określony jako element `<serviceCertificate>` podrzędny elementu, określa lokalizację i ustawienia weryfikacji certyfikatu X. 509, który jest używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="8982e-142">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="8982e-143">Element jest reprezentowany <xref:System.ServiceModel.Configuration.CertificateReferenceElement> przez klasę. `<certificateReference>`</span><span class="sxs-lookup"><span data-stu-id="8982e-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
