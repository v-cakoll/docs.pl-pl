---
title: ServiceMetadataBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c05f6be9fc0507b7e2f1de4374e3b9bbe3e2a10e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="702e6-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="702e6-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="702e6-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="702e6-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="702e6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="702e6-104">Syntax</span></span>  
  
```  
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="702e6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="702e6-105">Methods</span></span>  
 <span data-ttu-id="702e6-106">Klasa ServiceMetadataBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="702e6-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="702e6-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="702e6-107">Properties</span></span>  
 <span data-ttu-id="702e6-108">Klasa ServiceMetadataBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="702e6-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="702e6-109">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="702e6-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="702e6-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="702e6-110">Data type: string</span></span>  
  
 <span data-ttu-id="702e6-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="702e6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="702e6-112">Ustawia lokalizację, do której przekierowywane są żądania metadanych.</span><span class="sxs-lookup"><span data-stu-id="702e6-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="702e6-113">httpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="702e6-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="702e6-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="702e6-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="702e6-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="702e6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="702e6-116">Określa, czy opis WSDL pod adresem określanym przez usługę `HttpGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="702e6-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="702e6-117">httpGetUrl</span><span class="sxs-lookup"><span data-stu-id="702e6-117">HttpGetUrl</span></span>  
 <span data-ttu-id="702e6-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="702e6-118">Data type: string</span></span>  
  
 <span data-ttu-id="702e6-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="702e6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="702e6-120">Określa położenie, w którym publikowany jest opis WSDL usługi, dla pobierania za pomocą protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="702e6-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="702e6-121">httpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="702e6-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="702e6-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="702e6-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="702e6-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="702e6-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="702e6-124">Określa, czy opis WSDL usługi za pośrednictwem protokołu HTTPS pod adresem określanym przez `HttpsGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="702e6-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="702e6-125">httpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="702e6-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="702e6-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="702e6-126">Data type: string</span></span>  
  
 <span data-ttu-id="702e6-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="702e6-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="702e6-128">Określa położenie, w którym publikowany jest opis WSDL usługi, dla pobierania za pomocą protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="702e6-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="702e6-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="702e6-129">Requirements</span></span>  
  
|<span data-ttu-id="702e6-130">MOF</span><span class="sxs-lookup"><span data-stu-id="702e6-130">MOF</span></span>|<span data-ttu-id="702e6-131">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="702e6-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="702e6-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="702e6-132">Namespace</span></span>|<span data-ttu-id="702e6-133">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="702e6-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="702e6-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="702e6-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
