---
title: CorEventAttr — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorEventAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorEventAttr
helpviewer_keywords:
- CorEventAttr enumeration [.NET Framework metadata]
ms.assetid: dc2b3281-3820-487e-930d-350b66dc6417
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d34aa954126cc26519aaea963f99299e5557d2c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743058"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="a2ce8-102">CorEventAttr — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a2ce8-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="a2ce8-103">Zawiera wartości, które opisują metadane zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a2ce8-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2ce8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2ce8-104">Syntax</span></span>  
  
```  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="a2ce8-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a2ce8-105">Members</span></span>  
  
|<span data-ttu-id="a2ce8-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a2ce8-106">Member</span></span>|<span data-ttu-id="a2ce8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a2ce8-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="a2ce8-108">Określa, czy zdarzenie jest specjalne i że jego nazwę w tym artykule opisano sposób.</span><span class="sxs-lookup"><span data-stu-id="a2ce8-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="a2ce8-109">Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="a2ce8-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="a2ce8-110">Określa, że środowisko uruchomieniowe języka wspólnego powinien sprawdzać, kodowanie Nazwa zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a2ce8-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a2ce8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2ce8-111">Requirements</span></span>  
 <span data-ttu-id="a2ce8-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2ce8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2ce8-113">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="a2ce8-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a2ce8-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2ce8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2ce8-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2ce8-115">See also</span></span>
- [<span data-ttu-id="a2ce8-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="a2ce8-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
