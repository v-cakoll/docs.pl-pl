---
title: ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85b1c5455cb2008a352461d6b506e43fcef48d17
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130926"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="37ed2-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion — Metoda</span><span class="sxs-lookup"><span data-stu-id="37ed2-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>
<span data-ttu-id="37ed2-103">Wywoływane przez [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) do zgłaszania do debugera wyniku próby wyliczenia określonego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="37ed2-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37ed2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="37ed2-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37ed2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37ed2-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="37ed2-106">[in] Adres początkowy region pamięci, który był do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="37ed2-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="37ed2-107">[in] Rozmiar w bajtach regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="37ed2-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37ed2-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37ed2-108">Remarks</span></span>  
 <span data-ttu-id="37ed2-109">`ICLRDataEnumMemoryRegions::EnumMemoryRegions` Metoda będzie wywołać tę metodę wywołania zwrotnego po każdej próby wyliczenia regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="37ed2-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="37ed2-110">Wyliczenia będą nadal, nawet jeśli ta metoda zwraca wartość HRESULT wskazujący awarię.</span><span class="sxs-lookup"><span data-stu-id="37ed2-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="37ed2-111">Zgłoszone przez to wywołanie zwrotne regionów może być duplikaty lub regionów nakładających się.</span><span class="sxs-lookup"><span data-stu-id="37ed2-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37ed2-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="37ed2-112">Requirements</span></span>  
 <span data-ttu-id="37ed2-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37ed2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37ed2-114">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="37ed2-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="37ed2-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37ed2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37ed2-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37ed2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37ed2-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37ed2-117">See also</span></span>

- [<span data-ttu-id="37ed2-118">ICLRDataEnumMemoryRegionsCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="37ed2-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)
