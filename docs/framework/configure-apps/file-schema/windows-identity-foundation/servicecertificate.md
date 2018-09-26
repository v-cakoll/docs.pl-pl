---
title: '&lt;serviceCertificate&gt;'
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 008d2269a72759117658e27ec130cc8cf62cfdfa
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084309"
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="034bd-102">&lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="034bd-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="034bd-103">Określa certyfikat X.509, który jest używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="034bd-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="034bd-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="034bd-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="034bd-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="034bd-105">\<federationConfiguration></span></span>  
<span data-ttu-id="034bd-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="034bd-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="034bd-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="034bd-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="034bd-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="034bd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="034bd-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="034bd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="034bd-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="034bd-110">Attributes</span></span>  
 <span data-ttu-id="034bd-111">Brak</span><span class="sxs-lookup"><span data-stu-id="034bd-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="034bd-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="034bd-112">Child Elements</span></span>  
  
|<span data-ttu-id="034bd-113">Element</span><span class="sxs-lookup"><span data-stu-id="034bd-113">Element</span></span>|<span data-ttu-id="034bd-114">Opis</span><span class="sxs-lookup"><span data-stu-id="034bd-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="034bd-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="034bd-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="034bd-116">Określa ustawienia, które są używane do znalezienia i sprawdź poprawność certyfikatu X.509 w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="034bd-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="034bd-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="034bd-117">Parent Elements</span></span>  
  
|<span data-ttu-id="034bd-118">Element</span><span class="sxs-lookup"><span data-stu-id="034bd-118">Element</span></span>|<span data-ttu-id="034bd-119">Opis</span><span class="sxs-lookup"><span data-stu-id="034bd-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="034bd-120">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="034bd-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="034bd-121">Zawiera ustawienia, które skonfigurować <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="034bd-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="034bd-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="034bd-122">Example</span></span>  
 <span data-ttu-id="034bd-123">Następujący kody XML pokazuje użycie \<serviceCertificate > element.</span><span class="sxs-lookup"><span data-stu-id="034bd-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="034bd-124">Kod XML jest pobierana z `CustomToken` próbki.</span><span class="sxs-lookup"><span data-stu-id="034bd-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
