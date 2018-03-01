---
title: "ICLRDataEnumMemoryRegions::EnumMemoryRegions — Metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1685b1f739519485e5e68928b29a874587e6f9c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="ed135-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions — Metoda</span><span class="sxs-lookup"><span data-stu-id="ed135-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="ed135-103">Wylicza określone obszary pamięci.</span><span class="sxs-lookup"><span data-stu-id="ed135-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed135-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed135-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed135-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed135-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="ed135-106">[in] Wskaźnik do [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) wystąpienie, które jest wywoływana przez tę metodę w poszczególnych regionach pamięci wyliczany do debugera w wyniku powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="ed135-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="ed135-107">Wyliczanie regiony pamięci będzie kontynuowane, nawet wtedy, gdy wywołanie zwrotne oznacza błąd.</span><span class="sxs-lookup"><span data-stu-id="ed135-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="ed135-108">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="ed135-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="ed135-109">[in] Wartość [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) wyliczenia, który określa regiony pamięci, które mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="ed135-109">[in] A value of the [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed135-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed135-110">Remarks</span></span>  
 <span data-ttu-id="ed135-111">Ta metoda używa określonego [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) wystąpienia, aby powiadomić wywołującego wyników.</span><span class="sxs-lookup"><span data-stu-id="ed135-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed135-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ed135-112">Requirements</span></span>  
 <span data-ttu-id="ed135-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed135-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed135-114">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="ed135-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ed135-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed135-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed135-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed135-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed135-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed135-117">See Also</span></span>  
 [<span data-ttu-id="ed135-118">ICLRDataEnumMemoryRegions, interfejs</span><span class="sxs-lookup"><span data-stu-id="ed135-118">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)
