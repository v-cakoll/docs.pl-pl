---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: b1e5b87b053e947432cba9f6e716f7d1ea8f013f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484332"
---
# <a name="servicetoendpointassociation"></a><span data-ttu-id="59ae5-102">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="59ae5-102">ServiceToEndpointAssociation</span></span>
<span data-ttu-id="59ae5-103">Mapuje usługi do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="59ae5-103">Maps a service to an endpoint.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59ae5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="59ae5-104">Syntax</span></span>  
  
```  
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="59ae5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="59ae5-105">Methods</span></span>  
 <span data-ttu-id="59ae5-106">Klasa ServiceToEndpointAssociation nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="59ae5-106">The ServiceToEndpointAssociation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="59ae5-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="59ae5-107">Properties</span></span>  
 <span data-ttu-id="59ae5-108">Klasa ServiceToEndpointAssociation ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="59ae5-108">The ServiceToEndpointAssociation class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="59ae5-109">ref</span><span class="sxs-lookup"><span data-stu-id="59ae5-109">ref</span></span>  
 <span data-ttu-id="59ae5-110">Typ danych: usługi</span><span class="sxs-lookup"><span data-stu-id="59ae5-110">Data type: Service</span></span>  
  
 <span data-ttu-id="59ae5-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="59ae5-111">Access type: Read-only</span></span>  
<span data-ttu-id="59ae5-112">Kwalifikatory: klucz</span><span class="sxs-lookup"><span data-stu-id="59ae5-112">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="59ae5-113">Usługa skojarzona z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="59ae5-113">The service associated with the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="59ae5-114">ref</span><span class="sxs-lookup"><span data-stu-id="59ae5-114">ref</span></span>  
 <span data-ttu-id="59ae5-115">Typ danych: punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="59ae5-115">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="59ae5-116">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="59ae5-116">Access type: Read-only</span></span>  
<span data-ttu-id="59ae5-117">Kwalifikatory: klucz</span><span class="sxs-lookup"><span data-stu-id="59ae5-117">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="59ae5-118">Punkt końcowym skojarzony z usługą.</span><span class="sxs-lookup"><span data-stu-id="59ae5-118">The endpoint associated with the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59ae5-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="59ae5-119">Requirements</span></span>  
  
|<span data-ttu-id="59ae5-120">MOF</span><span class="sxs-lookup"><span data-stu-id="59ae5-120">MOF</span></span>|<span data-ttu-id="59ae5-121">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="59ae5-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="59ae5-122">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="59ae5-122">Namespace</span></span>|<span data-ttu-id="59ae5-123">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="59ae5-123">Defined in root\ServiceModel</span></span>|
