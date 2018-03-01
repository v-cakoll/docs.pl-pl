---
title: "CLRDataEnumMemoryFlags — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CLRDataEnumMemoryFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLRDataEnumMemoryFlags
helpviewer_keywords:
- CLRDataEnumMemoryFlags enumeration [.NET Framework debugging]
ms.assetid: e249f9fc-e24a-4506-903c-92781f6eab7c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 88e8ca340c8512156606f10236c779daf96c3156
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="b5b7b-102">CLRDataEnumMemoryFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b5b7b-102">CLRDataEnumMemoryFlags Enumeration</span></span>
<span data-ttu-id="b5b7b-103">Wskazuje, które regiony pamięci wywołanie [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) metoda powinna zawierać.</span><span class="sxs-lookup"><span data-stu-id="b5b7b-103">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5b7b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5b7b-104">Syntax</span></span>  
  
```  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="b5b7b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b5b7b-105">Members</span></span>  
  
|<span data-ttu-id="b5b7b-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="b5b7b-106">Member</span></span>|<span data-ttu-id="b5b7b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b5b7b-107">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="b5b7b-108">Minizrzutu, czyli zrzutu pamięci rozrzedzone.</span><span class="sxs-lookup"><span data-stu-id="b5b7b-108">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="b5b7b-109">Zrzut pełnego stosu.</span><span class="sxs-lookup"><span data-stu-id="b5b7b-109">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b5b7b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b5b7b-110">Requirements</span></span>  
 <span data-ttu-id="b5b7b-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5b7b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5b7b-112">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="b5b7b-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b5b7b-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5b7b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5b7b-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5b7b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5b7b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b5b7b-115">See Also</span></span>  
 [<span data-ttu-id="b5b7b-116">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b5b7b-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
