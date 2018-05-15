---
title: COR_PUB_ENUMPROCESS — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PUB_ENUMPROCESS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_PUB_ENUMPROCESS
helpviewer_keywords:
- COR_PUB_ENUMPROCESS enumeration [.NET Framework debugging]
ms.assetid: 5d3ada6e-feea-47da-a7ed-b664107c137f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fcdb5883e109d7e0c73c8fb76ee61b52cf23091f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="corpubenumprocess-enumeration"></a><span data-ttu-id="ae2a7-102">COR_PUB_ENUMPROCESS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ae2a7-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="ae2a7-103">Określa typ procesu, które mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="ae2a7-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae2a7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae2a7-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="ae2a7-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ae2a7-105">Members</span></span>  
  
|<span data-ttu-id="ae2a7-106">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="ae2a7-106">Member name</span></span>|<span data-ttu-id="ae2a7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ae2a7-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="ae2a7-108">Proces zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="ae2a7-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae2a7-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae2a7-109">Remarks</span></span>  
 <span data-ttu-id="ae2a7-110">Bieżąca wersja niezarządzanego API debugowania wylicza tylko zarządzanych procesów.</span><span class="sxs-lookup"><span data-stu-id="ae2a7-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae2a7-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ae2a7-111">Requirements</span></span>  
 <span data-ttu-id="ae2a7-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae2a7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae2a7-113">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="ae2a7-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ae2a7-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae2a7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae2a7-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae2a7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae2a7-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae2a7-116">See Also</span></span>  
 [<span data-ttu-id="ae2a7-117">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ae2a7-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
