---
title: ICorDebugProcess5::GetArrayLayout — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetArrayLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetArrayLayout
helpviewer_keywords:
- ICorDebugProcess5::GetArrayLayout method [.NET Framework debugging]
- GetArrayLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 9a7393b9-9735-43c6-8616-afb103c432fd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e96dccdd2836eebb08e88fe09dda531cd62baeee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420004"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="d943e-102">ICorDebugProcess5::GetArrayLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="d943e-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="d943e-103">Zawiera informacje o układzie typów tablicowych.</span><span class="sxs-lookup"><span data-stu-id="d943e-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d943e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d943e-104">Syntax</span></span>  
  
```  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d943e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d943e-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="d943e-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) tokenu, który określa tablicy, którego układ jest pożądane.</span><span class="sxs-lookup"><span data-stu-id="d943e-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="d943e-107">[out] Wskaźnik do [cor_array_layout —](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) struktury, który zawiera informacje o układzie tablicy w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d943e-107">[out] A pointer to a [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d943e-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d943e-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d943e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d943e-109">Requirements</span></span>  
 <span data-ttu-id="d943e-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d943e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d943e-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d943e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d943e-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d943e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d943e-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d943e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d943e-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d943e-114">See Also</span></span>  
 [<span data-ttu-id="d943e-115">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="d943e-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="d943e-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d943e-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
