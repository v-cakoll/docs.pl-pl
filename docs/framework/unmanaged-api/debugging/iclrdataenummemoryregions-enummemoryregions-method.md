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
ms.openlocfilehash: 886f78a0561ebbd5470b7932123f67975d650693
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197350"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="9a20b-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions — Metoda</span><span class="sxs-lookup"><span data-stu-id="9a20b-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="9a20b-103">Wylicza określone obszary pamięci.</span><span class="sxs-lookup"><span data-stu-id="9a20b-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a20b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a20b-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a20b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a20b-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="9a20b-106">[in] Wskaźnik do [iclrdataenummemoryregionscallback —](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) wystąpienia, która jest wywoływana przez tę metodę dla każdego regionu pamięci filtrująca wyliczany do debugera wyniku powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="9a20b-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="9a20b-107">Wyliczenie obszarów pamięci będzie kontynuowane, nawet jeśli wywołanie zwrotne oznacza błąd.</span><span class="sxs-lookup"><span data-stu-id="9a20b-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="9a20b-108">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="9a20b-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="9a20b-109">[in] Wartość [clrdataenummemoryflags —](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) wyliczenie, które określa regiony pamięci do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="9a20b-109">[in] A value of the [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a20b-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a20b-110">Remarks</span></span>  
 <span data-ttu-id="9a20b-111">Ta metoda używa określonego [iclrdataenummemoryregionscallback —](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) wystąpienia powiadomiono wywołującego wyników.</span><span class="sxs-lookup"><span data-stu-id="9a20b-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a20b-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a20b-112">Requirements</span></span>  
 <span data-ttu-id="9a20b-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a20b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a20b-114">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="9a20b-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="9a20b-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a20b-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9a20b-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9a20b-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9a20b-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a20b-117">See also</span></span>

- [<span data-ttu-id="9a20b-118">ICLRDataEnumMemoryRegions — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9a20b-118">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)
