---
title: "ICorDebugProcess5::GetArrayLayout — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetArrayLayout
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetArrayLayout
helpviewer_keywords:
- ICorDebugProcess5::GetArrayLayout method [.NET Framework debugging]
- GetArrayLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 9a7393b9-9735-43c6-8616-afb103c432fd
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b4c5d07e1645bc3736de2f8a298ad5b80e2cb26d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="d1857-102">ICorDebugProcess5::GetArrayLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="d1857-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="d1857-103">Zawiera informacje o układzie typów tablicowych.</span><span class="sxs-lookup"><span data-stu-id="d1857-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1857-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1857-104">Syntax</span></span>  
  
```  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1857-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1857-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="d1857-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) tokenu, który określa tablicy, którego układ jest pożądane.</span><span class="sxs-lookup"><span data-stu-id="d1857-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="d1857-107">[out] Wskaźnik do [cor_array_layout —](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) struktury, który zawiera informacje o układzie tablicy w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d1857-107">[out] A pointer to a [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1857-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1857-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1857-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1857-109">Requirements</span></span>  
 <span data-ttu-id="d1857-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1857-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1857-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1857-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1857-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1857-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1857-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1857-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1857-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1857-114">See Also</span></span>  
 [<span data-ttu-id="d1857-115">ICorDebugProcess5 — interfejs</span><span class="sxs-lookup"><span data-stu-id="d1857-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="d1857-116">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="d1857-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
