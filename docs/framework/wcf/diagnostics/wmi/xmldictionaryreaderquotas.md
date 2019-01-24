---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: f24865fb0affa7b4516a14fc05b905995826e82e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597674"
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="4a325-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="4a325-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="4a325-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="4a325-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a325-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a325-104">Syntax</span></span>  
  
```csharp
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4a325-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4a325-105">Methods</span></span>  
 <span data-ttu-id="4a325-106">Klasa obiektu XmlDictionaryReaderQuotas nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="4a325-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4a325-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4a325-107">Properties</span></span>  
 <span data-ttu-id="4a325-108">Klasa obiektu XmlDictionaryReaderQuotas ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="4a325-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="4a325-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="4a325-109">MaxArrayLength</span></span>  
 <span data-ttu-id="4a325-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="4a325-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="4a325-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4a325-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4a325-112">Maksymalna dozwolona długość tablicy.</span><span class="sxs-lookup"><span data-stu-id="4a325-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="4a325-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="4a325-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="4a325-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="4a325-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="4a325-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4a325-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4a325-116">Maksymalna dozwolona liczba bajtów zwróconych do każdego odczytu.</span><span class="sxs-lookup"><span data-stu-id="4a325-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="4a325-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="4a325-117">MaxDepth</span></span>  
 <span data-ttu-id="4a325-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="4a325-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="4a325-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4a325-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4a325-120">Maksymalna głębokość zagnieżdżonego węzła dla każdego do odczytu.</span><span class="sxs-lookup"><span data-stu-id="4a325-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="4a325-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="4a325-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="4a325-122">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="4a325-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="4a325-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4a325-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4a325-124">Maksymalna dozwolona liczba znaków w nazwie tabeli.</span><span class="sxs-lookup"><span data-stu-id="4a325-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="4a325-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="4a325-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="4a325-126">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="4a325-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="4a325-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4a325-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4a325-128">Maksymalna dozwolona liczba znaków w elemencie zawartości XML.</span><span class="sxs-lookup"><span data-stu-id="4a325-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a325-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4a325-129">Requirements</span></span>  
  
|<span data-ttu-id="4a325-130">MOF</span><span class="sxs-lookup"><span data-stu-id="4a325-130">MOF</span></span>|<span data-ttu-id="4a325-131">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4a325-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4a325-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="4a325-132">Namespace</span></span>|<span data-ttu-id="4a325-133">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4a325-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a325-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a325-134">See also</span></span>
- <xref:System.Xml.XmlDictionaryReaderQuotas>
- <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
