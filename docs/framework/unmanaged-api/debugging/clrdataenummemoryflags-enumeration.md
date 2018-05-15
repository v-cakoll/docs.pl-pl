---
title: CLRDataEnumMemoryFlags — Wyliczenie
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a19c6f22ee9fbe7eb1019a0b799d63e4ee650e98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="eb68b-102">CLRDataEnumMemoryFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="eb68b-102">CLRDataEnumMemoryFlags Enumeration</span></span>
<span data-ttu-id="eb68b-103">Wskazuje, które regiony pamięci wywołanie [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) metoda powinna zawierać.</span><span class="sxs-lookup"><span data-stu-id="eb68b-103">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb68b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb68b-104">Syntax</span></span>  
  
```  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="eb68b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="eb68b-105">Members</span></span>  
  
|<span data-ttu-id="eb68b-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="eb68b-106">Member</span></span>|<span data-ttu-id="eb68b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="eb68b-107">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="eb68b-108">Minizrzutu, czyli zrzutu pamięci rozrzedzone.</span><span class="sxs-lookup"><span data-stu-id="eb68b-108">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="eb68b-109">Zrzut pełnego stosu.</span><span class="sxs-lookup"><span data-stu-id="eb68b-109">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eb68b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb68b-110">Requirements</span></span>  
 <span data-ttu-id="eb68b-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb68b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb68b-112">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="eb68b-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="eb68b-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb68b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb68b-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb68b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb68b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb68b-115">See Also</span></span>  
 [<span data-ttu-id="eb68b-116">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="eb68b-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
