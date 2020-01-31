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
ms.openlocfilehash: 4e3891996af5945ed95c8c37dddfee5c446db248
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789106"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="49222-102">ICLRDataEnumMemoryRegionsCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="49222-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="49222-103">Zapewnia metodę wywołania zwrotnego dla [ICLRDataEnumMemoryRegions:: EnumMemoryRegions —](iclrdataenummemoryregions-enummemoryregions-method.md) , aby zgłosić do debugera wynik próby wyliczenia określonego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="49222-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="49222-104">Metody</span><span class="sxs-lookup"><span data-stu-id="49222-104">Methods</span></span>  
  
|<span data-ttu-id="49222-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="49222-105">Method</span></span>|<span data-ttu-id="49222-106">Opis</span><span class="sxs-lookup"><span data-stu-id="49222-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="49222-107">EnumMemoryRegion, metoda</span><span class="sxs-lookup"><span data-stu-id="49222-107">EnumMemoryRegion Method</span></span>](iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="49222-108">Wywołane przez `ICLRDataEnumMemoryRegions::EnumMemoryRegions`, aby zgłosić debugerowi wynik próby wyliczenia określonego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="49222-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="49222-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="49222-109">Requirements</span></span>  
 <span data-ttu-id="49222-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49222-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49222-111">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="49222-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="49222-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="49222-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49222-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49222-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49222-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49222-114">See also</span></span>

- [<span data-ttu-id="49222-115">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="49222-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
