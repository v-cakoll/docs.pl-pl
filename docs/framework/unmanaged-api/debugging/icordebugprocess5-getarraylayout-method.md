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
ms.openlocfilehash: 332de11790e78b712a429365bd89cc9e41539edc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105524"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="7f7c1-102">ICorDebugProcess5::GetArrayLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="7f7c1-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="7f7c1-103">Informacje dotyczące układu typów tablicowych.</span><span class="sxs-lookup"><span data-stu-id="7f7c1-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f7c1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f7c1-104">Syntax</span></span>  
  
```  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f7c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f7c1-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="7f7c1-106">[in] A [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) tokenu, który określa tablicę, którego układ jest pożądane.</span><span class="sxs-lookup"><span data-stu-id="7f7c1-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="7f7c1-107">[out] Wskaźnik do [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) strukturę, która zawiera informacje na temat układ tablicy w pamięci.</span><span class="sxs-lookup"><span data-stu-id="7f7c1-107">[out] A pointer to a [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f7c1-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7f7c1-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f7c1-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7f7c1-109">Requirements</span></span>  
 <span data-ttu-id="7f7c1-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f7c1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f7c1-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f7c1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f7c1-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f7c1-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7f7c1-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7f7c1-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7f7c1-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f7c1-114">See also</span></span>

- [<span data-ttu-id="7f7c1-115">ICorDebugProcess5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7f7c1-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="7f7c1-116">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="7f7c1-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
