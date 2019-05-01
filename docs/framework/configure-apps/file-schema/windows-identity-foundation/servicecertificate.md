---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 328d074f9edc5ddf871308a7e3d694bf94adea78
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793825"
---
# <a name="servicecertificate"></a><span data-ttu-id="ac15f-101">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="ac15f-101">\<serviceCertificate></span></span>
<span data-ttu-id="ac15f-102">Określa certyfikat X.509, który jest używany do szyfrowania i odszyfrowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="ac15f-102">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="ac15f-103">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="ac15f-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="ac15f-104">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="ac15f-104">\<federationConfiguration></span></span>  
<span data-ttu-id="ac15f-105">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="ac15f-105">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac15f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac15f-106">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac15f-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ac15f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="ac15f-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ac15f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac15f-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ac15f-109">Attributes</span></span>  
 <span data-ttu-id="ac15f-110">Brak</span><span class="sxs-lookup"><span data-stu-id="ac15f-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ac15f-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ac15f-111">Child Elements</span></span>  
  
|<span data-ttu-id="ac15f-112">Element</span><span class="sxs-lookup"><span data-stu-id="ac15f-112">Element</span></span>|<span data-ttu-id="ac15f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ac15f-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac15f-114">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="ac15f-114">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="ac15f-115">Określa ustawienia, które są używane do znalezienia i sprawdź poprawność certyfikatu X.509 w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="ac15f-115">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ac15f-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ac15f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ac15f-117">Element</span><span class="sxs-lookup"><span data-stu-id="ac15f-117">Element</span></span>|<span data-ttu-id="ac15f-118">Opis</span><span class="sxs-lookup"><span data-stu-id="ac15f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac15f-119">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="ac15f-119">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="ac15f-120">Zawiera ustawienia, które skonfigurować <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="ac15f-120">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ac15f-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="ac15f-121">Example</span></span>  
 <span data-ttu-id="ac15f-122">Następujący kody XML pokazuje użycie \<serviceCertificate > element.</span><span class="sxs-lookup"><span data-stu-id="ac15f-122">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="ac15f-123">Kod XML jest pobierana z `CustomToken` próbki.</span><span class="sxs-lookup"><span data-stu-id="ac15f-123">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
