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
ms.openlocfilehash: 6c159780b9019127d166e8437ea4ed214284011f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121260"
---
# <a name="icordebugprocess5gettypeid-method"></a><span data-ttu-id="61078-102">ICorDebugProcess5::GetTypeID — Metoda</span><span class="sxs-lookup"><span data-stu-id="61078-102">ICorDebugProcess5::GetTypeID Method</span></span>
<span data-ttu-id="61078-103">Konwertuje adres obiektu na identyfikator [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="61078-103">Converts an object address to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61078-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="61078-104">Syntax</span></span>  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61078-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="61078-105">Parameters</span></span>  
 `obj`  
 <span data-ttu-id="61078-106">podczas Adres obiektu.</span><span class="sxs-lookup"><span data-stu-id="61078-106">[in] The object address.</span></span>  
  
 `pId`  
 <span data-ttu-id="61078-107">Wskaźnik do wartości [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) , która identyfikuje obiekt.</span><span class="sxs-lookup"><span data-stu-id="61078-107">A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61078-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="61078-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61078-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="61078-109">Requirements</span></span>  
 <span data-ttu-id="61078-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61078-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61078-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="61078-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61078-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="61078-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61078-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61078-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61078-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61078-114">See also</span></span>

- [<span data-ttu-id="61078-115">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="61078-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="61078-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="61078-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
