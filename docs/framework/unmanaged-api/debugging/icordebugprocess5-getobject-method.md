---
title: ICorDebugProcess5::GetObject — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetObject method [.NET Framework debugging]
ms.assetid: c8111502-5a20-447f-9dc2-76e8acd7ed5a
topic_type:
- apiref
ms.openlocfilehash: 4b48132ee60bcaebb218d8f583de6558372f5055
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178607"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="c4c42-102">ICorDebugProcess5::GetObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="c4c42-102">ICorDebugProcess5::GetObject Method</span></span>
<span data-ttu-id="c4c42-103">Konwertuje adres obiektu na obiekt "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="c4c42-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4c42-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4c42-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4c42-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4c42-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="c4c42-106">[w] Adres obiektu.</span><span class="sxs-lookup"><span data-stu-id="c4c42-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="c4c42-107">[na zewnątrz] Wskaźnik do adresu obiektu "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="c4c42-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4c42-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c4c42-108">Remarks</span></span>  
 <span data-ttu-id="c4c42-109">Jeśli `addr` nie wskazuje prawidłowego obiektu `GetObject` zarządzanego, metoda zwraca `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="c4c42-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4c42-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c4c42-110">Requirements</span></span>  
 <span data-ttu-id="c4c42-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4c42-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4c42-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4c42-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4c42-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4c42-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4c42-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4c42-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4c42-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4c42-115">See also</span></span>

- [<span data-ttu-id="c4c42-116">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="c4c42-116">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="c4c42-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c4c42-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
