---
title: "ICorDebugProcess5::GetTypeLayout — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4317fd374646dd5187a94f3e91cc88df939ed762
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5gettypelayout-method"></a><span data-ttu-id="39051-102">ICorDebugProcess5::GetTypeLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="39051-102">ICorDebugProcess5::GetTypeLayout Method</span></span>
<span data-ttu-id="39051-103">Pobiera informacje o układzie obiektu w pamięci na podstawie jego identyfikatora typu.</span><span class="sxs-lookup"><span data-stu-id="39051-103">Gets information about the layout of an object in memory based on its type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39051-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="39051-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="39051-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="39051-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="39051-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token, który określa typ, którego układ jest pożądane.</span><span class="sxs-lookup"><span data-stu-id="39051-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the type whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="39051-107">[out] Wskaźnik do [cor_type_layout —](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) struktury, który zawiera informacje o układzie obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="39051-107">[out] A pointer to a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that contains information about the layout of the object in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39051-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39051-108">Remarks</span></span>  
 <span data-ttu-id="39051-109">`ICorDebugProcess5::GetTypeLayout` Metoda zapewnia informacje o obiektach na podstawie jego [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), który jest zwracany przez wiele innych [ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) metody.</span><span class="sxs-lookup"><span data-stu-id="39051-109">The `ICorDebugProcess5::GetTypeLayout` method provides information about an object based on its [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which is returned by a number of other [ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) methods.</span></span> <span data-ttu-id="39051-110">Informacje są udostępniane przez [cor_type_layout —](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) struktury, która jest wypełniana przez metodę.</span><span class="sxs-lookup"><span data-stu-id="39051-110">The information is provided by a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that is populated by the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39051-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="39051-111">Requirements</span></span>  
 <span data-ttu-id="39051-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39051-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39051-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39051-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39051-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39051-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39051-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39051-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39051-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="39051-116">See Also</span></span>  
 [<span data-ttu-id="39051-117">COR_TYPE_LAYOUT, struktura</span><span class="sxs-lookup"><span data-stu-id="39051-117">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 [<span data-ttu-id="39051-118">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="39051-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="39051-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="39051-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
