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
ms.openlocfilehash: ddcb8064dfb9be30c66404a8762a9ca73cd6afe4
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860663"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="14e77-102">ICLRDataEnumMemoryRegionsCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14e77-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="14e77-103">Zapewnia metodę wywołania zwrotnego dla [ICLRDataEnumMemoryRegions:: EnumMemoryRegions —](iclrdataenummemoryregions-enummemoryregions-method.md) , aby zgłosić do debugera wynik próby wyliczenia określonego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="14e77-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="14e77-104">Metody</span><span class="sxs-lookup"><span data-stu-id="14e77-104">Methods</span></span>  
  
|<span data-ttu-id="14e77-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="14e77-105">Method</span></span>|<span data-ttu-id="14e77-106">Opis</span><span class="sxs-lookup"><span data-stu-id="14e77-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="14e77-107">EnumMemoryRegion, metoda</span><span class="sxs-lookup"><span data-stu-id="14e77-107">EnumMemoryRegion Method</span></span>](iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="14e77-108">Wywołuje `ICLRDataEnumMemoryRegions::EnumMemoryRegions` się, by zgłosić debugerowi wynik próby wyliczenia określonego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="14e77-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="14e77-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="14e77-109">Requirements</span></span>  
 <span data-ttu-id="14e77-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14e77-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14e77-111">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="14e77-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="14e77-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="14e77-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14e77-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14e77-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14e77-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14e77-114">See also</span></span>

- [<span data-ttu-id="14e77-115">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="14e77-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
