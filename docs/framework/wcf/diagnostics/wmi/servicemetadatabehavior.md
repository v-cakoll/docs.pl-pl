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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9d10fdd9e33b078fa392e0ef359372913f9ba133
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="dfc60-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="dfc60-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="dfc60-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="dfc60-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfc60-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dfc60-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="dfc60-105">Metody</span><span class="sxs-lookup"><span data-stu-id="dfc60-105">Methods</span></span>  
 <span data-ttu-id="dfc60-106">Klasa ServiceMetadataBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="dfc60-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="dfc60-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="dfc60-107">Properties</span></span>  
 <span data-ttu-id="dfc60-108">Klasa ServiceMetadataBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="dfc60-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="dfc60-109">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="dfc60-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="dfc60-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="dfc60-110">Data type: string</span></span>  
  
 <span data-ttu-id="dfc60-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dfc60-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dfc60-112">Ustawia lokalizację, do której przekierowywane są żądania metadanych.</span><span class="sxs-lookup"><span data-stu-id="dfc60-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="dfc60-113">httpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="dfc60-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="dfc60-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="dfc60-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="dfc60-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dfc60-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dfc60-116">Określa, czy opis WSDL pod adresem określanym przez usługę `HttpGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="dfc60-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="dfc60-117">httpGetUrl</span><span class="sxs-lookup"><span data-stu-id="dfc60-117">HttpGetUrl</span></span>  
 <span data-ttu-id="dfc60-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="dfc60-118">Data type: string</span></span>  
  
 <span data-ttu-id="dfc60-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dfc60-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dfc60-120">Określa położenie, w którym publikowany jest opis WSDL usługi, dla pobierania za pomocą protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc60-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="dfc60-121">httpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="dfc60-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="dfc60-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="dfc60-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="dfc60-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dfc60-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dfc60-124">Określa, czy opis WSDL usługi za pośrednictwem protokołu HTTPS pod adresem określanym przez `HttpsGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="dfc60-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="dfc60-125">httpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="dfc60-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="dfc60-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="dfc60-126">Data type: string</span></span>  
  
 <span data-ttu-id="dfc60-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dfc60-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dfc60-128">Określa położenie, w którym publikowany jest opis WSDL usługi, dla pobierania za pomocą protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="dfc60-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfc60-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dfc60-129">Requirements</span></span>  
  
|<span data-ttu-id="dfc60-130">MOF</span><span class="sxs-lookup"><span data-stu-id="dfc60-130">MOF</span></span>|<span data-ttu-id="dfc60-131">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="dfc60-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="dfc60-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="dfc60-132">Namespace</span></span>|<span data-ttu-id="dfc60-133">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="dfc60-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dfc60-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dfc60-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
