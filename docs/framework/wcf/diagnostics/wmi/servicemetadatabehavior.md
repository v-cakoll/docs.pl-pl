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
ms.openlocfilehash: f17b31e1dfe9ba60b2042a85a6d673d986fe0a33
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="00378-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="00378-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="00378-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="00378-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00378-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="00378-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="00378-105">Metody</span><span class="sxs-lookup"><span data-stu-id="00378-105">Methods</span></span>  
 <span data-ttu-id="00378-106">Klasa ServiceMetadataBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="00378-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="00378-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="00378-107">Properties</span></span>  
 <span data-ttu-id="00378-108">Klasa ServiceMetadataBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="00378-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="00378-109">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="00378-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="00378-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="00378-110">Data type: string</span></span>  
  
 <span data-ttu-id="00378-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="00378-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="00378-112">Ustawia lokalizację, do której przekierowywane są żądania metadanych.</span><span class="sxs-lookup"><span data-stu-id="00378-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="00378-113">httpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="00378-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="00378-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="00378-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="00378-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="00378-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="00378-116">Określa, czy opis WSDL pod adresem określanym przez usługę `HttpGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="00378-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="00378-117">httpGetUrl</span><span class="sxs-lookup"><span data-stu-id="00378-117">HttpGetUrl</span></span>  
 <span data-ttu-id="00378-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="00378-118">Data type: string</span></span>  
  
 <span data-ttu-id="00378-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="00378-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="00378-120">Określa położenie, w którym publikowany jest opis WSDL usługi, dla pobierania za pomocą protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="00378-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="00378-121">httpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="00378-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="00378-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="00378-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="00378-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="00378-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="00378-124">Określa, czy opis WSDL usługi za pośrednictwem protokołu HTTPS pod adresem określanym przez `HttpsGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="00378-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="00378-125">httpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="00378-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="00378-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="00378-126">Data type: string</span></span>  
  
 <span data-ttu-id="00378-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="00378-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="00378-128">Określa położenie, w którym publikowany jest opis WSDL usługi, dla pobierania za pomocą protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="00378-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00378-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="00378-129">Requirements</span></span>  
  
|<span data-ttu-id="00378-130">MOF</span><span class="sxs-lookup"><span data-stu-id="00378-130">MOF</span></span>|<span data-ttu-id="00378-131">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="00378-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="00378-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="00378-132">Namespace</span></span>|<span data-ttu-id="00378-133">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="00378-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="00378-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00378-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
