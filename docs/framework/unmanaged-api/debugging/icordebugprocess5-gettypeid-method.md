---
title: ICorDebugProcess5::GetTypeID — Metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess5.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeID
helpviewer_keywords:
- ICorDebugProcess5::GetTypeID method [.NET Framework debugging]
- GetTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 47dbaea4-8857-462e-93ba-fff880fc9e50
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07c23a32037e83a878bb3136c48176f19249b207
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948697"
---
# <a name="icordebugprocess5gettypeid-method"></a><span data-ttu-id="5bfff-102">ICorDebugProcess5::GetTypeID — Metoda</span><span class="sxs-lookup"><span data-stu-id="5bfff-102">ICorDebugProcess5::GetTypeID Method</span></span>
<span data-ttu-id="5bfff-103">Konwertuje adres obiektu, który pozwoli [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="5bfff-103">Converts an object address to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bfff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5bfff-104">Syntax</span></span>  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bfff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5bfff-105">Parameters</span></span>  
 `obj`  
 <span data-ttu-id="5bfff-106">[in] Adres obiektu.</span><span class="sxs-lookup"><span data-stu-id="5bfff-106">[in] The object address.</span></span>  
  
 `pId`  
 <span data-ttu-id="5bfff-107">Wskaźnik do [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) wartość, która identyfikuje obiekt.</span><span class="sxs-lookup"><span data-stu-id="5bfff-107">A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bfff-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5bfff-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bfff-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5bfff-109">Requirements</span></span>  
 <span data-ttu-id="5bfff-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bfff-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bfff-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5bfff-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5bfff-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bfff-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bfff-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bfff-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bfff-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5bfff-114">See also</span></span>

- [<span data-ttu-id="5bfff-115">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="5bfff-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="5bfff-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5bfff-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
