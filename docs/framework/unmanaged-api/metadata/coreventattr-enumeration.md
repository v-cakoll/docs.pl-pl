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
ms.openlocfilehash: ec2972605c40f4ba292f5a5f58d6d3efed53f966
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443558"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="6c0d3-102">CorEventAttr — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="6c0d3-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="6c0d3-103">Contains values that describe the metadata of an event.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c0d3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c0d3-104">Syntax</span></span>  
  
```cpp  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="6c0d3-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="6c0d3-105">Members</span></span>  
  
|<span data-ttu-id="6c0d3-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="6c0d3-106">Member</span></span>|<span data-ttu-id="6c0d3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6c0d3-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="6c0d3-108">Specifies that the event is special, and that its name describes how.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="6c0d3-109">Reserved for internal use by the common language runtime.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="6c0d3-110">Specifies that the common language runtime should check the encoding of the event name.</span><span class="sxs-lookup"><span data-stu-id="6c0d3-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6c0d3-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c0d3-111">Requirements</span></span>  
 <span data-ttu-id="6c0d3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c0d3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c0d3-113">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="6c0d3-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="6c0d3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c0d3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c0d3-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c0d3-115">See also</span></span>

- [<span data-ttu-id="6c0d3-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="6c0d3-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
