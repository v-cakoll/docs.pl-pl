---
title: "CreateAssemblyEnum — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: CreateAssemblyEnum
helpviewer_keywords: CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c229496a79b146b5dcac3d06fa3efd9237e39d3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="114f4-102">CreateAssemblyEnum — Funkcja</span><span class="sxs-lookup"><span data-stu-id="114f4-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="114f4-103">Pobiera wskaźnik do [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) wystąpienie, które można wyliczyć obiektów w zestawie z określonym [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span><span class="sxs-lookup"><span data-stu-id="114f4-103">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="114f4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="114f4-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="114f4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="114f4-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="114f4-106">[out] Wskaźnik do lokalizacji w pamięci, który zawiera żądanie `IAssemblyEnum` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="114f4-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="114f4-107">[in] Zarezerwowane dla przyszłego rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="114f4-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="114f4-108">`pUnkReserved`musi być odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="114f4-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="114f4-109">[in] `IAssemblyName` Żądanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="114f4-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="114f4-110">Ta nazwa jest używana do filtrowania wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="114f4-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="114f4-111">Może być null wyliczyć wszystkich zestawów w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="114f4-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="114f4-112">[in] Flagi do modyfikowania zachowania modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="114f4-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="114f4-113">Ten parametr zawiera dokładnie jeden bit z [asm_cache_flags —](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="114f4-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="114f4-114">[in] Zarezerwowane dla przyszłego rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="114f4-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="114f4-115">`pvReserved`musi być odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="114f4-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="114f4-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="114f4-116">Remarks</span></span>  
 <span data-ttu-id="114f4-117">`dwFlags` Parametr zawiera dokładnie jeden bit z `ASM_CACHE_FLAGS` wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="114f4-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="114f4-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="114f4-118">Requirements</span></span>  
 <span data-ttu-id="114f4-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="114f4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="114f4-120">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="114f4-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="114f4-121">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="114f4-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="114f4-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="114f4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="114f4-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="114f4-123">See Also</span></span>  
 [<span data-ttu-id="114f4-124">IAssemblyEnum — interfejs</span><span class="sxs-lookup"><span data-stu-id="114f4-124">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 [<span data-ttu-id="114f4-125">IAssemblyName — interfejs</span><span class="sxs-lookup"><span data-stu-id="114f4-125">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="114f4-126">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="114f4-126">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
