---
title: ServiceDebugBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c829f68fe994b47fe880febb4d3ac2020fde2d1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="fbbb8-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="fbbb8-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="fbbb8-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="fbbb8-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbbb8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fbbb8-104">Syntax</span></span>  
  
```  
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="fbbb8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fbbb8-105">Methods</span></span>  
 <span data-ttu-id="fbbb8-106">Klasa ServiceDebugBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="fbbb8-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fbbb8-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="fbbb8-107">Properties</span></span>  
 <span data-ttu-id="fbbb8-108">Klasa ServiceDebugBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="fbbb8-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="fbbb8-109">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="fbbb8-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="fbbb8-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fbbb8-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="fbbb8-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fbbb8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fbbb8-112">Określa, czy opis WSDL pod adresem określanym przez usługę `HttpGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="fbbb8-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="fbbb8-113">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="fbbb8-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="fbbb8-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fbbb8-114">Data type: string</span></span>  
  
 <span data-ttu-id="fbbb8-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fbbb8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fbbb8-116">Określa położenie, w którym publikowany jest opis WSDL usługi, dla pobierania za pomocą protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="fbbb8-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="fbbb8-117">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="fbbb8-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="fbbb8-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fbbb8-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="fbbb8-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fbbb8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fbbb8-120">Określa, czy opis WSDL usługi za pośrednictwem protokołu HTTPS pod adresem określanym przez `HttpsGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="fbbb8-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="fbbb8-121">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="fbbb8-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="fbbb8-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fbbb8-122">Data type: string</span></span>  
  
 <span data-ttu-id="fbbb8-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fbbb8-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fbbb8-124">Określa położenie, w którym publikowany jest opis WSDL usługi, dla pobierania za pomocą protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="fbbb8-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="fbbb8-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="fbbb8-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="fbbb8-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fbbb8-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="fbbb8-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fbbb8-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fbbb8-128">Określa, czy dołączać informacje o zarządzanym wyjątku w informacjach szczegółowych o błędach SOAP zwracanych do klientów na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="fbbb8-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbbb8-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fbbb8-129">Requirements</span></span>  
  
|<span data-ttu-id="fbbb8-130">MOF</span><span class="sxs-lookup"><span data-stu-id="fbbb8-130">MOF</span></span>|<span data-ttu-id="fbbb8-131">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="fbbb8-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fbbb8-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="fbbb8-132">Namespace</span></span>|<span data-ttu-id="fbbb8-133">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fbbb8-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fbbb8-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fbbb8-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
