---
title: ICorDebugProcess5::GetTypeLayout — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b05ff331520e0afc24b02fa7262045612c6344c1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162766"
---
# <a name="icordebugprocess5gettypelayout-method"></a><span data-ttu-id="e1c91-102">ICorDebugProcess5::GetTypeLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="e1c91-102">ICorDebugProcess5::GetTypeLayout Method</span></span>
<span data-ttu-id="e1c91-103">Pobiera informacje o układ obiektu w pamięci na podstawie jego identyfikatora typu.</span><span class="sxs-lookup"><span data-stu-id="e1c91-103">Gets information about the layout of an object in memory based on its type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1c91-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1c91-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1c91-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1c91-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="e1c91-106">[in] A [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token, który określa typ, którego układ jest pożądane.</span><span class="sxs-lookup"><span data-stu-id="e1c91-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the type whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="e1c91-107">[out] Wskaźnik do [cor_type_layout —](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) strukturę, która zawiera informacje na temat układu obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e1c91-107">[out] A pointer to a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that contains information about the layout of the object in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1c91-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1c91-108">Remarks</span></span>  
 <span data-ttu-id="e1c91-109">`ICorDebugProcess5::GetTypeLayout` Metoda zawiera informacje dotyczące obiektu, na podstawie jego [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), która jest zwracana przez szereg innych [icordebugprocess5 —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e1c91-109">The `ICorDebugProcess5::GetTypeLayout` method provides information about an object based on its [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which is returned by a number of other [ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) methods.</span></span> <span data-ttu-id="e1c91-110">Informacje są udostępniane przez [cor_type_layout —](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) strukturę, która jest wypełniana przez metodę.</span><span class="sxs-lookup"><span data-stu-id="e1c91-110">The information is provided by a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that is populated by the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1c91-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e1c91-111">Requirements</span></span>  
 <span data-ttu-id="e1c91-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1c91-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1c91-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1c91-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1c91-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1c91-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e1c91-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e1c91-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e1c91-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1c91-116">See also</span></span>

- [<span data-ttu-id="e1c91-117">COR_TYPE_LAYOUT — Struktura</span><span class="sxs-lookup"><span data-stu-id="e1c91-117">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)
- [<span data-ttu-id="e1c91-118">ICorDebugProcess5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e1c91-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="e1c91-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="e1c91-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
