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
ms.openlocfilehash: 6cd385c1176bea41b41a981e743c6104227d8acd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708197"
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="63aca-102">CLRDataEnumMemoryFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="63aca-102">CLRDataEnumMemoryFlags Enumeration</span></span>
<span data-ttu-id="63aca-103">Wskazuje, które regiony pamięci wywołanie [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) powinna zawierać metodę.</span><span class="sxs-lookup"><span data-stu-id="63aca-103">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63aca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="63aca-104">Syntax</span></span>  
  
```  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="63aca-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="63aca-105">Members</span></span>  
  
|<span data-ttu-id="63aca-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="63aca-106">Member</span></span>|<span data-ttu-id="63aca-107">Opis</span><span class="sxs-lookup"><span data-stu-id="63aca-107">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="63aca-108">Minizrzutu, czyli zrzutu pamięci rozrzedzone.</span><span class="sxs-lookup"><span data-stu-id="63aca-108">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="63aca-109">Zrzut pełnego stosu.</span><span class="sxs-lookup"><span data-stu-id="63aca-109">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63aca-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="63aca-110">Requirements</span></span>  
 <span data-ttu-id="63aca-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63aca-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63aca-112">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="63aca-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="63aca-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63aca-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63aca-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63aca-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63aca-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63aca-115">See also</span></span>
- [<span data-ttu-id="63aca-116">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="63aca-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
