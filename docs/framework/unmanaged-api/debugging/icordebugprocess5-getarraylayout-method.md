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
ms.openlocfilehash: c1afb87e063a18bd05bedf856f8b7ebdf0e47e91
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767418"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="b43c6-102">ICorDebugProcess5::GetArrayLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="b43c6-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="b43c6-103">Informacje dotyczące układu typów tablicowych.</span><span class="sxs-lookup"><span data-stu-id="b43c6-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b43c6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b43c6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b43c6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b43c6-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="b43c6-106">[in] A [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) tokenu, który określa tablicę, którego układ jest pożądane.</span><span class="sxs-lookup"><span data-stu-id="b43c6-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="b43c6-107">[out] Wskaźnik do [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) strukturę, która zawiera informacje na temat układ tablicy w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b43c6-107">[out] A pointer to a [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b43c6-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b43c6-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b43c6-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b43c6-109">Requirements</span></span>  
 <span data-ttu-id="b43c6-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b43c6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b43c6-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b43c6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b43c6-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b43c6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b43c6-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b43c6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b43c6-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b43c6-114">See also</span></span>

- [<span data-ttu-id="b43c6-115">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="b43c6-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="b43c6-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b43c6-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
