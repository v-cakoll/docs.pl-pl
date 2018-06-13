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
ms.openlocfilehash: 0a0af0c86bc44a4968119e1afd2a84e17e941601
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405502"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="6856c-102">ICLRDataEnumMemoryRegionsCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6856c-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="6856c-103">Zapewnia metodę wywołania zwrotnego [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) zgłoszenia do debugera wynik próby wyliczenia określonego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="6856c-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6856c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6856c-104">Methods</span></span>  
  
|<span data-ttu-id="6856c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6856c-105">Method</span></span>|<span data-ttu-id="6856c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6856c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6856c-107">EnumMemoryRegion, metoda</span><span class="sxs-lookup"><span data-stu-id="6856c-107">EnumMemoryRegion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="6856c-108">Wywoływane przez `ICLRDataEnumMemoryRegions::EnumMemoryRegions` zgłoszenia do debugera wynik próby wyliczenia określonego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="6856c-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6856c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6856c-109">Requirements</span></span>  
 <span data-ttu-id="6856c-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6856c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6856c-111">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="6856c-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="6856c-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6856c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6856c-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6856c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6856c-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6856c-114">See Also</span></span>  
 [<span data-ttu-id="6856c-115">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6856c-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
