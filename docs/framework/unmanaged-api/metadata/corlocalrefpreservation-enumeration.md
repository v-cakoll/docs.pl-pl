---
title: CorLocalRefPreservation — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorLocalRefPreservation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLocalRefPreservation
helpviewer_keywords:
- CorLocalRefPreservation enumeration [.NET Framework metadata]
ms.assetid: 44757163-1228-4213-a4c4-d4de503cc75d
topic_type:
- apiref
ms.openlocfilehash: 706ea37101f9f961e92d8cef2cf508c1dd0d56c1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450245"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="e5710-102">CorLocalRefPreservation — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e5710-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="e5710-103">Zawiera wartości flag dla traktowania odwołań lokalnych.</span><span class="sxs-lookup"><span data-stu-id="e5710-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5710-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5710-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="e5710-105">Members</span><span class="sxs-lookup"><span data-stu-id="e5710-105">Members</span></span>  
  
|<span data-ttu-id="e5710-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e5710-106">Member</span></span>|<span data-ttu-id="e5710-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e5710-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="e5710-108">Nie zachowuj żadnych odwołań lokalnych.</span><span class="sxs-lookup"><span data-stu-id="e5710-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="e5710-109">Zachowaj odwołania do typu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="e5710-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="e5710-110">Zachowaj odwołania do lokalnych członków.</span><span class="sxs-lookup"><span data-stu-id="e5710-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e5710-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5710-111">Requirements</span></span>  
 <span data-ttu-id="e5710-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5710-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5710-113">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="e5710-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e5710-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5710-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5710-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5710-115">See also</span></span>

- [<span data-ttu-id="e5710-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="e5710-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
