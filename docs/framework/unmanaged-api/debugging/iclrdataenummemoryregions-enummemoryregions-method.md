---
title: ICLRDataEnumMemoryRegions::EnumMemoryRegions — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16d91156427c2ef7bdabd5ab11b01894fbced64c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="5125f-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions — Metoda</span><span class="sxs-lookup"><span data-stu-id="5125f-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="5125f-103">Wylicza określone obszary pamięci.</span><span class="sxs-lookup"><span data-stu-id="5125f-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5125f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5125f-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5125f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5125f-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="5125f-106">[in] Wskaźnik do [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) wystąpienie, które jest wywoływana przez tę metodę w poszczególnych regionach pamięci wyliczany do debugera w wyniku powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="5125f-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="5125f-107">Wyliczanie regiony pamięci będzie kontynuowane, nawet wtedy, gdy wywołanie zwrotne oznacza błąd.</span><span class="sxs-lookup"><span data-stu-id="5125f-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="5125f-108">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="5125f-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="5125f-109">[in] Wartość [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) wyliczenia, który określa regiony pamięci, które mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="5125f-109">[in] A value of the [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5125f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5125f-110">Remarks</span></span>  
 <span data-ttu-id="5125f-111">Ta metoda używa określonego [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) wystąpienia, aby powiadomić wywołującego wyników.</span><span class="sxs-lookup"><span data-stu-id="5125f-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5125f-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5125f-112">Requirements</span></span>  
 <span data-ttu-id="5125f-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5125f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5125f-114">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="5125f-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5125f-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5125f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5125f-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5125f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5125f-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5125f-117">See Also</span></span>  
 [<span data-ttu-id="5125f-118">ICLRDataEnumMemoryRegions, interfejs</span><span class="sxs-lookup"><span data-stu-id="5125f-118">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)
