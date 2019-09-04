---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 653dd9cfadbfd33f5371b77172199b946321bc8c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251857"
---
# <a name="servicecertificate"></a><span data-ttu-id="a5ff3-101">\<> serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="a5ff3-101">\<serviceCertificate></span></span>
<span data-ttu-id="a5ff3-102">Konfiguruje certyfikat X. 509, który jest używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="a5ff3-102">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
<span data-ttu-id="a5ff3-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a5ff3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a5ff3-104">&nbsp;&nbsp;[ **\<> System. identityModel. Services**](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="a5ff3-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="a5ff3-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="a5ff3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="a5ff3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> serviceCertificate**</span><span class="sxs-lookup"><span data-stu-id="a5ff3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5ff3-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5ff3-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5ff3-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a5ff3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a5ff3-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a5ff3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5ff3-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a5ff3-110">Attributes</span></span>  
 <span data-ttu-id="a5ff3-111">Brak</span><span class="sxs-lookup"><span data-stu-id="a5ff3-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a5ff3-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a5ff3-112">Child Elements</span></span>  
  
|<span data-ttu-id="a5ff3-113">Element</span><span class="sxs-lookup"><span data-stu-id="a5ff3-113">Element</span></span>|<span data-ttu-id="a5ff3-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a5ff3-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5ff3-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="a5ff3-115">\<certificateReference></span></span>](certificatereference.md)|<span data-ttu-id="a5ff3-116">Określa ustawienia, które są używane do znajdowania i weryfikowania certyfikatu X. 509 w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="a5ff3-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a5ff3-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a5ff3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a5ff3-118">Element</span><span class="sxs-lookup"><span data-stu-id="a5ff3-118">Element</span></span>|<span data-ttu-id="a5ff3-119">Opis</span><span class="sxs-lookup"><span data-stu-id="a5ff3-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5ff3-120">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="a5ff3-120">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="a5ff3-121">Zawiera ustawienia, które konfigurują <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule> i (sam).</span><span class="sxs-lookup"><span data-stu-id="a5ff3-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a5ff3-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5ff3-122">Example</span></span>  
 <span data-ttu-id="a5ff3-123">Poniższy kod XML przedstawia użycie \<elementu serviceCertificate >.</span><span class="sxs-lookup"><span data-stu-id="a5ff3-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="a5ff3-124">Kod XML jest pobierany z `CustomToken` przykładu.</span><span class="sxs-lookup"><span data-stu-id="a5ff3-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
