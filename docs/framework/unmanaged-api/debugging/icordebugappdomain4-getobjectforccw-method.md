---
title: ICorDebugAppDomain4::GetObjectForCCW — metoda
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 8b046eb5926bb9aa4738e8fff8e61b0b7c23a3aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088828"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="2d30b-102">ICorDebugAppDomain4::GetObjectForCCW — metoda</span><span class="sxs-lookup"><span data-stu-id="2d30b-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="2d30b-103">Pobiera obiekt zarządzany z wskaźnika otoki (CCW) modelu COM.</span><span class="sxs-lookup"><span data-stu-id="2d30b-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d30b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2d30b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d30b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d30b-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="2d30b-106">podczas Wskaźnik wywoływanej otoki COM (CCW).</span><span class="sxs-lookup"><span data-stu-id="2d30b-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="2d30b-107">określoną Wskaźnik do adresu obiektu "ICorDebugValue", który reprezentuje zarządzany obiekt odpowiadający danemu wskaźnikowi CCW.</span><span class="sxs-lookup"><span data-stu-id="2d30b-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d30b-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2d30b-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d30b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2d30b-109">Requirements</span></span>  
 <span data-ttu-id="2d30b-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d30b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d30b-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2d30b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d30b-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2d30b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d30b-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d30b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d30b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2d30b-114">See also</span></span>

- [<span data-ttu-id="2d30b-115">ICorDebugAppDomain4, interfejs</span><span class="sxs-lookup"><span data-stu-id="2d30b-115">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)
- [<span data-ttu-id="2d30b-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2d30b-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
