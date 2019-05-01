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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948710"
---
# <a name="icordebugprocess5gettypelayout-method"></a><span data-ttu-id="6bd69-102">ICorDebugProcess5::GetTypeLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="6bd69-102">ICorDebugProcess5::GetTypeLayout Method</span></span>
<span data-ttu-id="6bd69-103">Pobiera informacje o układ obiektu w pamięci na podstawie jego identyfikatora typu.</span><span class="sxs-lookup"><span data-stu-id="6bd69-103">Gets information about the layout of an object in memory based on its type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bd69-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6bd69-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bd69-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6bd69-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="6bd69-106">[in] A [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token, który określa typ, którego układ jest pożądane.</span><span class="sxs-lookup"><span data-stu-id="6bd69-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the type whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="6bd69-107">[out] Wskaźnik do [cor_type_layout —](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) strukturę, która zawiera informacje na temat układu obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="6bd69-107">[out] A pointer to a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that contains information about the layout of the object in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bd69-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6bd69-108">Remarks</span></span>  
 <span data-ttu-id="6bd69-109">`ICorDebugProcess5::GetTypeLayout` Metoda zawiera informacje dotyczące obiektu, na podstawie jego [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), która jest zwracana przez szereg innych [icordebugprocess5 —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6bd69-109">The `ICorDebugProcess5::GetTypeLayout` method provides information about an object based on its [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which is returned by a number of other [ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) methods.</span></span> <span data-ttu-id="6bd69-110">Informacje są udostępniane przez [cor_type_layout —](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) strukturę, która jest wypełniana przez metodę.</span><span class="sxs-lookup"><span data-stu-id="6bd69-110">The information is provided by a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that is populated by the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bd69-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6bd69-111">Requirements</span></span>  
 <span data-ttu-id="6bd69-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bd69-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bd69-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6bd69-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bd69-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bd69-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bd69-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bd69-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bd69-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6bd69-116">See also</span></span>

- [<span data-ttu-id="6bd69-117">COR_TYPE_LAYOUT, struktura</span><span class="sxs-lookup"><span data-stu-id="6bd69-117">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)
- [<span data-ttu-id="6bd69-118">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="6bd69-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="6bd69-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6bd69-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
