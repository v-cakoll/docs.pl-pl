---
title: "ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1b1897b18a8dcbb261a5041ca8b530b7877b910
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="58e68-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion — Metoda</span><span class="sxs-lookup"><span data-stu-id="58e68-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>
<span data-ttu-id="58e68-103">Wywoływane przez [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) zgłoszenia do debugera wynik próby wyliczenia określonego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="58e68-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58e68-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="58e68-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58e68-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="58e68-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="58e68-106">[in] Adres początkowy obszaru pamięci, który miał zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="58e68-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="58e68-107">[in] Rozmiar w bajtach obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="58e68-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58e68-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="58e68-108">Remarks</span></span>  
 <span data-ttu-id="58e68-109">`ICLRDataEnumMemoryRegions::EnumMemoryRegions` — Metoda będzie wywoływać tej metody wywołania zwrotnego po każdej próbie wyliczyć regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="58e68-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="58e68-110">Wyliczenie będzie kontynuowane, nawet wtedy, gdy ta metoda zwraca wartość HRESULT informujący o niepowodzeniu.</span><span class="sxs-lookup"><span data-stu-id="58e68-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="58e68-111">Regiony zgłoszone przez tego wywołania zwrotnego może być duplikatów lub nakładające się regionów.</span><span class="sxs-lookup"><span data-stu-id="58e68-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58e68-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="58e68-112">Requirements</span></span>  
 <span data-ttu-id="58e68-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58e68-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58e68-114">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="58e68-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="58e68-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58e68-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58e68-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58e68-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58e68-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58e68-117">See Also</span></span>  
 [<span data-ttu-id="58e68-118">ICLRDataEnumMemoryRegionsCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="58e68-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)
