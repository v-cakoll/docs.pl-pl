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
ms.openlocfilehash: 9153503fc114b0e4052265fca7c9399510d687ef
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792317"
---
# <a name="icordebugprocess5gettypeid-method"></a><span data-ttu-id="2e3d1-102">ICorDebugProcess5::GetTypeID — Metoda</span><span class="sxs-lookup"><span data-stu-id="2e3d1-102">ICorDebugProcess5::GetTypeID Method</span></span>
<span data-ttu-id="2e3d1-103">Konwertuje adres obiektu na identyfikator [COR_TYPEID](cor-typeid-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="2e3d1-103">Converts an object address to a [COR_TYPEID](cor-typeid-structure.md) identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e3d1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e3d1-104">Syntax</span></span>  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e3d1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e3d1-105">Parameters</span></span>  
 `obj`  
 <span data-ttu-id="2e3d1-106">podczas Adres obiektu.</span><span class="sxs-lookup"><span data-stu-id="2e3d1-106">[in] The object address.</span></span>  
  
 `pId`  
 <span data-ttu-id="2e3d1-107">Wskaźnik do wartości [COR_TYPEID](cor-typeid-structure.md) , która identyfikuje obiekt.</span><span class="sxs-lookup"><span data-stu-id="2e3d1-107">A pointer to the [COR_TYPEID](cor-typeid-structure.md) value that identifies the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e3d1-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2e3d1-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e3d1-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2e3d1-109">Requirements</span></span>  
 <span data-ttu-id="2e3d1-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e3d1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e3d1-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2e3d1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e3d1-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2e3d1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e3d1-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e3d1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e3d1-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e3d1-114">See also</span></span>

- [<span data-ttu-id="2e3d1-115">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="2e3d1-115">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="2e3d1-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2e3d1-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
