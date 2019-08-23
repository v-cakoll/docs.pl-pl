---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: a3aba5618855f7225dc8a427516eaa72b45f6e8b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942413"
---
# <a name="servicecertificate"></a><span data-ttu-id="954f1-101">\<> serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="954f1-101">\<serviceCertificate></span></span>
<span data-ttu-id="954f1-102">Konfiguruje certyfikat X. 509, który jest używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="954f1-102">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="954f1-103">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="954f1-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="954f1-104">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="954f1-104">\<federationConfiguration></span></span>  
<span data-ttu-id="954f1-105">\<> serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="954f1-105">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="954f1-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="954f1-106">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="954f1-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="954f1-107">Attributes and Elements</span></span>  
 <span data-ttu-id="954f1-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="954f1-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="954f1-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="954f1-109">Attributes</span></span>  
 <span data-ttu-id="954f1-110">Brak</span><span class="sxs-lookup"><span data-stu-id="954f1-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="954f1-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="954f1-111">Child Elements</span></span>  
  
|<span data-ttu-id="954f1-112">Element</span><span class="sxs-lookup"><span data-stu-id="954f1-112">Element</span></span>|<span data-ttu-id="954f1-113">Opis</span><span class="sxs-lookup"><span data-stu-id="954f1-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="954f1-114">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="954f1-114">\<certificateReference></span></span>](certificatereference.md)|<span data-ttu-id="954f1-115">Określa ustawienia, które są używane do znajdowania i weryfikowania certyfikatu X. 509 w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="954f1-115">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="954f1-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="954f1-116">Parent Elements</span></span>  
  
|<span data-ttu-id="954f1-117">Element</span><span class="sxs-lookup"><span data-stu-id="954f1-117">Element</span></span>|<span data-ttu-id="954f1-118">Opis</span><span class="sxs-lookup"><span data-stu-id="954f1-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="954f1-119">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="954f1-119">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="954f1-120">Zawiera ustawienia, które konfigurują <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule> i (sam).</span><span class="sxs-lookup"><span data-stu-id="954f1-120">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="954f1-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="954f1-121">Example</span></span>  
 <span data-ttu-id="954f1-122">Poniższy kod XML przedstawia użycie \<elementu serviceCertificate >.</span><span class="sxs-lookup"><span data-stu-id="954f1-122">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="954f1-123">Kod XML jest pobierany z `CustomToken` przykładu.</span><span class="sxs-lookup"><span data-stu-id="954f1-123">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
