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
ms.openlocfilehash: f5cff3f3f577a0c7ef04a226ec70a2722c89b5c8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496888"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="b6261-102">ICorDebugProcess5::GetArrayLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="b6261-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="b6261-103">Informacje dotyczące układu typów tablicowych.</span><span class="sxs-lookup"><span data-stu-id="b6261-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6261-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6261-104">Syntax</span></span>  
  
```  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6261-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6261-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="b6261-106">[in] A [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) tokenu, który określa tablicę, którego układ jest pożądane.</span><span class="sxs-lookup"><span data-stu-id="b6261-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="b6261-107">[out] Wskaźnik do [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) strukturę, która zawiera informacje na temat układ tablicy w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b6261-107">[out] A pointer to a [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6261-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6261-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6261-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6261-109">Requirements</span></span>  
 <span data-ttu-id="b6261-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6261-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6261-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6261-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6261-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6261-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6261-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6261-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6261-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6261-114">See also</span></span>
- [<span data-ttu-id="b6261-115">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6261-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="b6261-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b6261-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
