---
title: ICLRDataEnumMemoryRegionsCallback — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback
helpviewer_keywords:
- ICLRDataEnumMemoryRegionsCallback interface [.NET Framework debugging]
ms.assetid: 3f1af8b0-8478-48e0-a7ec-3e90e0b97649
topic_type:
- apiref
ms.openlocfilehash: cf46133095d1345ffbe0356d3ab486c11ae6dbd6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122913"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="9ec35-102">ICLRDataEnumMemoryRegionsCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9ec35-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="9ec35-103">Zapewnia metodę wywołania zwrotnego dla [ICLRDataEnumMemoryRegions:: EnumMemoryRegions —](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) , aby zgłosić do debugera wynik próby wyliczenia określonego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="9ec35-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ec35-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9ec35-104">Methods</span></span>  
  
|<span data-ttu-id="9ec35-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9ec35-105">Method</span></span>|<span data-ttu-id="9ec35-106">Opis</span><span class="sxs-lookup"><span data-stu-id="9ec35-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ec35-107">EnumMemoryRegion, metoda</span><span class="sxs-lookup"><span data-stu-id="9ec35-107">EnumMemoryRegion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="9ec35-108">Wywołane przez `ICLRDataEnumMemoryRegions::EnumMemoryRegions`, aby zgłosić debugerowi wynik próby wyliczenia określonego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="9ec35-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ec35-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9ec35-109">Requirements</span></span>  
 <span data-ttu-id="9ec35-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ec35-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ec35-111">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="9ec35-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="9ec35-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9ec35-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ec35-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ec35-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ec35-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ec35-114">See also</span></span>

- [<span data-ttu-id="9ec35-115">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9ec35-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
