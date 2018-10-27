---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: 9bc519509b00383be333ac605688950d2709117c
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50044232"
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="332c3-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="332c3-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="332c3-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="332c3-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="332c3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="332c3-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="332c3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="332c3-105">Methods</span></span>  
 <span data-ttu-id="332c3-106">Klasa obiektu XmlDictionaryReaderQuotas nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="332c3-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="332c3-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="332c3-107">Properties</span></span>  
 <span data-ttu-id="332c3-108">Klasa obiektu XmlDictionaryReaderQuotas ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="332c3-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="332c3-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="332c3-109">MaxArrayLength</span></span>  
 <span data-ttu-id="332c3-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="332c3-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="332c3-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="332c3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="332c3-112">Maksymalna dozwolona długość tablicy.</span><span class="sxs-lookup"><span data-stu-id="332c3-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="332c3-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="332c3-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="332c3-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="332c3-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="332c3-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="332c3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="332c3-116">Maksymalna dozwolona liczba bajtów zwróconych do każdego odczytu.</span><span class="sxs-lookup"><span data-stu-id="332c3-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="332c3-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="332c3-117">MaxDepth</span></span>  
 <span data-ttu-id="332c3-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="332c3-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="332c3-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="332c3-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="332c3-120">Maksymalna głębokość zagnieżdżonego węzła dla każdego do odczytu.</span><span class="sxs-lookup"><span data-stu-id="332c3-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="332c3-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="332c3-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="332c3-122">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="332c3-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="332c3-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="332c3-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="332c3-124">Maksymalna dozwolona liczba znaków w nazwie tabeli.</span><span class="sxs-lookup"><span data-stu-id="332c3-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="332c3-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="332c3-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="332c3-126">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="332c3-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="332c3-127">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="332c3-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="332c3-128">Maksymalna dozwolona liczba znaków w elemencie zawartości XML.</span><span class="sxs-lookup"><span data-stu-id="332c3-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="332c3-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="332c3-129">Requirements</span></span>  
  
|<span data-ttu-id="332c3-130">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="332c3-130">MOF</span></span>|<span data-ttu-id="332c3-131">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="332c3-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="332c3-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="332c3-132">Namespace</span></span>|<span data-ttu-id="332c3-133">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="332c3-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="332c3-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="332c3-134">See Also</span></span>  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
