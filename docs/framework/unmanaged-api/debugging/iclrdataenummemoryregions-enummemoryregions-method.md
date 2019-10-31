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
ms.openlocfilehash: 693ec07176f80711709cd9b85c6886bea8be74b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122963"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="73368-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions — Metoda</span><span class="sxs-lookup"><span data-stu-id="73368-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="73368-103">Wylicza określone obszary pamięci.</span><span class="sxs-lookup"><span data-stu-id="73368-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73368-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73368-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73368-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73368-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="73368-106">podczas Wskaźnik do wystąpienia [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) , który jest wywoływany przez tę metodę dla każdego regionu pamięci, który jest wyliczany w celu powiadomienia debugera wyniku.</span><span class="sxs-lookup"><span data-stu-id="73368-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="73368-107">Wyliczenie regionów pamięci jest kontynuowane nawet wtedy, gdy wywołanie zwrotne wskazuje na błąd.</span><span class="sxs-lookup"><span data-stu-id="73368-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="73368-108">podczas Nieużywane.</span><span class="sxs-lookup"><span data-stu-id="73368-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="73368-109">podczas Wartość wyliczenia [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) , która określa regiony pamięci do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="73368-109">[in] A value of the [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73368-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73368-110">Remarks</span></span>  
 <span data-ttu-id="73368-111">Ta metoda używa określonego wystąpienia [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) do powiadomienia obiektu wywołującego wyniki.</span><span class="sxs-lookup"><span data-stu-id="73368-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73368-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73368-112">Requirements</span></span>  
 <span data-ttu-id="73368-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73368-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73368-114">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="73368-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="73368-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="73368-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73368-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73368-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73368-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73368-117">See also</span></span>

- [<span data-ttu-id="73368-118">ICLRDataEnumMemoryRegions, interfejs</span><span class="sxs-lookup"><span data-stu-id="73368-118">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)
