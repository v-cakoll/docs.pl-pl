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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2d6b866c90e3e6c6e72dc75f230bcf7b4e03a6bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="1946f-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="1946f-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="1946f-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="1946f-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1946f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1946f-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="1946f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1946f-105">Methods</span></span>  
 <span data-ttu-id="1946f-106">Klasa ServiceDebugBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="1946f-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1946f-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1946f-107">Properties</span></span>  
 <span data-ttu-id="1946f-108">Klasa ServiceDebugBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="1946f-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="1946f-109">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="1946f-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="1946f-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="1946f-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="1946f-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1946f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1946f-112">Określa, czy opis WSDL pod adresem określanym przez usługę `HttpGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1946f-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="1946f-113">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="1946f-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="1946f-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="1946f-114">Data type: string</span></span>  
  
 <span data-ttu-id="1946f-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1946f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1946f-116">Określa położenie, w którym publikowany jest opis WSDL usługi, dla pobierania za pomocą protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="1946f-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="1946f-117">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="1946f-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="1946f-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="1946f-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="1946f-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1946f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1946f-120">Określa, czy opis WSDL usługi za pośrednictwem protokołu HTTPS pod adresem określanym przez `HttpsGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1946f-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="1946f-121">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="1946f-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="1946f-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="1946f-122">Data type: string</span></span>  
  
 <span data-ttu-id="1946f-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1946f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1946f-124">Określa położenie, w którym publikowany jest opis WSDL usługi, dla pobierania za pomocą protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1946f-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="1946f-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="1946f-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="1946f-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="1946f-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="1946f-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1946f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1946f-128">Określa, czy dołączać informacje o zarządzanym wyjątku w informacjach szczegółowych o błędach SOAP zwracanych do klientów na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="1946f-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1946f-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1946f-129">Requirements</span></span>  
  
|<span data-ttu-id="1946f-130">MOF</span><span class="sxs-lookup"><span data-stu-id="1946f-130">MOF</span></span>|<span data-ttu-id="1946f-131">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1946f-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1946f-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="1946f-132">Namespace</span></span>|<span data-ttu-id="1946f-133">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1946f-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1946f-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1946f-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
