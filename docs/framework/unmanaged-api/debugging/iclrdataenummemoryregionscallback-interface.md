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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dad66c8a55982762ede754a4b3cd747b7a91b87d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225433"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="0d4a5-102">ICLRDataEnumMemoryRegionsCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0d4a5-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="0d4a5-103">Zapewnia metodę wywołania zwrotnego dla [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) do zgłaszania do debugera wyniku próby wyliczenia określonego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="0d4a5-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0d4a5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0d4a5-104">Methods</span></span>  
  
|<span data-ttu-id="0d4a5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0d4a5-105">Method</span></span>|<span data-ttu-id="0d4a5-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0d4a5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0d4a5-107">EnumMemoryRegion, metoda</span><span class="sxs-lookup"><span data-stu-id="0d4a5-107">EnumMemoryRegion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="0d4a5-108">Wywoływane przez `ICLRDataEnumMemoryRegions::EnumMemoryRegions` do zgłaszania do debugera wyniku próby wyliczenia określonego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="0d4a5-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d4a5-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0d4a5-109">Requirements</span></span>  
 <span data-ttu-id="0d4a5-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d4a5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d4a5-111">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="0d4a5-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0d4a5-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d4a5-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0d4a5-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0d4a5-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0d4a5-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d4a5-114">See also</span></span>

- [<span data-ttu-id="0d4a5-115">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="0d4a5-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
