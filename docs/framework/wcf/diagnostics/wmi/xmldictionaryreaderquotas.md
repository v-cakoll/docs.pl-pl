---
title: XmlDictionaryReaderQuotas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 980a7eacd095dc1b601d63f5a807f2e287c09885
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="7c7bf-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="7c7bf-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="7c7bf-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="7c7bf-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c7bf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c7bf-104">Syntax</span></span>  
  
```  
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7c7bf-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7c7bf-105">Methods</span></span>  
 <span data-ttu-id="7c7bf-106">Klasa obiektu XmlDictionaryReaderQuotas nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="7c7bf-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7c7bf-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7c7bf-107">Properties</span></span>  
 <span data-ttu-id="7c7bf-108">Klasa obiektu XmlDictionaryReaderQuotas ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="7c7bf-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="7c7bf-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="7c7bf-109">MaxArrayLength</span></span>  
 <span data-ttu-id="7c7bf-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="7c7bf-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="7c7bf-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7c7bf-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7c7bf-112">Maksymalna dozwolona długość tablicy.</span><span class="sxs-lookup"><span data-stu-id="7c7bf-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="7c7bf-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="7c7bf-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="7c7bf-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="7c7bf-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="7c7bf-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7c7bf-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7c7bf-116">Maksymalna dozwolona liczba bajtów zwracana przy każdym odczycie.</span><span class="sxs-lookup"><span data-stu-id="7c7bf-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="7c7bf-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="7c7bf-117">MaxDepth</span></span>  
 <span data-ttu-id="7c7bf-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="7c7bf-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="7c7bf-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7c7bf-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7c7bf-120">Maksymalna głębokość zagnieżdżenia węzłów przy każdym odczycie.</span><span class="sxs-lookup"><span data-stu-id="7c7bf-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="7c7bf-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="7c7bf-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="7c7bf-122">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="7c7bf-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="7c7bf-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7c7bf-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7c7bf-124">Maksymalna dozwolona liczba znaków w nazwie tabeli.</span><span class="sxs-lookup"><span data-stu-id="7c7bf-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="7c7bf-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="7c7bf-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="7c7bf-126">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="7c7bf-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="7c7bf-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7c7bf-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7c7bf-128">Maksymalna liczba znaków dozwolona w zawartości elementu XML.</span><span class="sxs-lookup"><span data-stu-id="7c7bf-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c7bf-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c7bf-129">Requirements</span></span>  
  
|<span data-ttu-id="7c7bf-130">MOF</span><span class="sxs-lookup"><span data-stu-id="7c7bf-130">MOF</span></span>|<span data-ttu-id="7c7bf-131">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7c7bf-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7c7bf-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="7c7bf-132">Namespace</span></span>|<span data-ttu-id="7c7bf-133">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7c7bf-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c7bf-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c7bf-134">See Also</span></span>  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
