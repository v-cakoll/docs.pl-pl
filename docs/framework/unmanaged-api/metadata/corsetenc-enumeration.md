---
title: CorSetENC — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
ms.openlocfilehash: 39f72e670ddc700c257f50f6bad6fab702ec21b6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432775"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="ce2bf-102">CorSetENC — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ce2bf-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="ce2bf-103">Contains values used to influence behavior during the generation of metadata.</span><span class="sxs-lookup"><span data-stu-id="ce2bf-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce2bf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce2bf-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a><span data-ttu-id="ce2bf-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ce2bf-105">Members</span></span>  
  
|<span data-ttu-id="ce2bf-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ce2bf-106">Member</span></span>|<span data-ttu-id="ce2bf-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ce2bf-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="ce2bf-108">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="ce2bf-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="ce2bf-109">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="ce2bf-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="ce2bf-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span><span class="sxs-lookup"><span data-stu-id="ce2bf-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="ce2bf-111">Indicates that tokens can be moved during updates.</span><span class="sxs-lookup"><span data-stu-id="ce2bf-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="ce2bf-112">Indicates that updates can consist only of additions.</span><span class="sxs-lookup"><span data-stu-id="ce2bf-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="ce2bf-113">Tokens cannot be moved.</span><span class="sxs-lookup"><span data-stu-id="ce2bf-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="ce2bf-114">Indicates that compilation is incremental.</span><span class="sxs-lookup"><span data-stu-id="ce2bf-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="ce2bf-115">Indicates that only changed metadata should be saved.</span><span class="sxs-lookup"><span data-stu-id="ce2bf-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="ce2bf-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span><span class="sxs-lookup"><span data-stu-id="ce2bf-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ce2bf-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ce2bf-117">Requirements</span></span>  
 <span data-ttu-id="ce2bf-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce2bf-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce2bf-119">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="ce2bf-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ce2bf-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce2bf-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce2bf-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce2bf-121">See also</span></span>

- [<span data-ttu-id="ce2bf-122">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="ce2bf-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
