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
ms.openlocfilehash: bd29f6a0b0dfc0b7ab5b57bb61a3540d5caf66d0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639656"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="495e3-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions — Metoda</span><span class="sxs-lookup"><span data-stu-id="495e3-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="495e3-103">Wylicza określone obszary pamięci.</span><span class="sxs-lookup"><span data-stu-id="495e3-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="495e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="495e3-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="495e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="495e3-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="495e3-106">[in] Wskaźnik do [iclrdataenummemoryregionscallback —](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) wystąpienia, która jest wywoływana przez tę metodę dla każdego regionu pamięci filtrująca wyliczany do debugera wyniku powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="495e3-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="495e3-107">Wyliczenie obszarów pamięci będzie kontynuowane, nawet jeśli wywołanie zwrotne oznacza błąd.</span><span class="sxs-lookup"><span data-stu-id="495e3-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="495e3-108">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="495e3-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="495e3-109">[in] Wartość [clrdataenummemoryflags —](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) wyliczenie, które określa regiony pamięci do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="495e3-109">[in] A value of the [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="495e3-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="495e3-110">Remarks</span></span>  
 <span data-ttu-id="495e3-111">Ta metoda używa określonego [iclrdataenummemoryregionscallback —](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) wystąpienia powiadomiono wywołującego wyników.</span><span class="sxs-lookup"><span data-stu-id="495e3-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="495e3-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="495e3-112">Requirements</span></span>  
 <span data-ttu-id="495e3-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="495e3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="495e3-114">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="495e3-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="495e3-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="495e3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="495e3-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="495e3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="495e3-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="495e3-117">See also</span></span>
- [<span data-ttu-id="495e3-118">ICLRDataEnumMemoryRegions, interfejs</span><span class="sxs-lookup"><span data-stu-id="495e3-118">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)
