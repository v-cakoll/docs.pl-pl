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
ms.openlocfilehash: 02ff60852a85d003deb68cae96a184ac8d61c65f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609402"
---
# <a name="corpubenumprocess-enumeration"></a><span data-ttu-id="7cc74-102">COR_PUB_ENUMPROCESS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="7cc74-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="7cc74-103">Identyfikuje typ procesu do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7cc74-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cc74-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7cc74-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="7cc74-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7cc74-105">Members</span></span>  
  
|<span data-ttu-id="7cc74-106">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="7cc74-106">Member name</span></span>|<span data-ttu-id="7cc74-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7cc74-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="7cc74-108">Proces zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="7cc74-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7cc74-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7cc74-109">Remarks</span></span>  
 <span data-ttu-id="7cc74-110">Bieżąca wersja interfejsu API debugowania niezarządzanego wylicza tylko zarządzanych procesów.</span><span class="sxs-lookup"><span data-stu-id="7cc74-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cc74-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7cc74-111">Requirements</span></span>  
 <span data-ttu-id="7cc74-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cc74-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cc74-113">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="7cc74-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="7cc74-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cc74-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cc74-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cc74-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cc74-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7cc74-116">See also</span></span>

- [<span data-ttu-id="7cc74-117">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="7cc74-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
