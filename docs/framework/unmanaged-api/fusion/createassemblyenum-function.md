---
title: CreateAssemblyEnum — Funkcja
ms.date: 03/30/2017
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d809bbfa17ed9e9ae16505852740e874ca11248c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621789"
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="1ea81-102">CreateAssemblyEnum — Funkcja</span><span class="sxs-lookup"><span data-stu-id="1ea81-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="1ea81-103">Pobiera wskaźnik do [iassemblyenum —](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) wystąpienie, które można wyliczyć obiektów w zestawie z określonym [iassemblyname —](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span><span class="sxs-lookup"><span data-stu-id="1ea81-103">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ea81-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ea81-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ea81-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ea81-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="1ea81-106">[out] Wskaźnik do lokalizacji pamięci, która zawiera żądanie `IAssemblyEnum` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="1ea81-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="1ea81-107">[in] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="1ea81-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="1ea81-108">`pUnkReserved` musi być odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="1ea81-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="1ea81-109">[in] `IAssemblyName` Żądanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="1ea81-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="1ea81-110">Ta nazwa jest używana do filtrowania wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1ea81-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="1ea81-111">Może być null można wyliczyć wszystkie zestawy w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="1ea81-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="1ea81-112">[in] Flagi do modyfikowania zachowania modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="1ea81-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="1ea81-113">Ten parametr zawiera dokładnie jeden bit z [asm_cache_flags —](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1ea81-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="1ea81-114">[in] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="1ea81-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="1ea81-115">`pvReserved` musi być odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="1ea81-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ea81-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ea81-116">Remarks</span></span>  
 <span data-ttu-id="1ea81-117">`dwFlags` Parametr zawiera dokładnie jeden bit z `ASM_CACHE_FLAGS` wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1ea81-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ea81-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ea81-118">Requirements</span></span>  
 <span data-ttu-id="1ea81-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ea81-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ea81-120">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="1ea81-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1ea81-121">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1ea81-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1ea81-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ea81-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ea81-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ea81-123">See also</span></span>
- [<span data-ttu-id="1ea81-124">IAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="1ea81-124">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
- [<span data-ttu-id="1ea81-125">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="1ea81-125">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="1ea81-126">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="1ea81-126">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
