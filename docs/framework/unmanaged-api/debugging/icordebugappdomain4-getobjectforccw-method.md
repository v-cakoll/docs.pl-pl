---
title: ICorDebugAppDomain4::GetObjectForCCW — metoda
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 50f46394c809321f0bd256e4c8d75b76fc7c2c70
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784853"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="73497-102">ICorDebugAppDomain4::GetObjectForCCW — metoda</span><span class="sxs-lookup"><span data-stu-id="73497-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="73497-103">Pobiera obiekt zarządzany z wskaźnika otoki (CCW) modelu COM.</span><span class="sxs-lookup"><span data-stu-id="73497-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73497-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73497-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73497-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73497-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="73497-106">podczas Wskaźnik wywoływanej otoki COM (CCW).</span><span class="sxs-lookup"><span data-stu-id="73497-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="73497-107">określoną Wskaźnik do adresu obiektu "ICorDebugValue", który reprezentuje zarządzany obiekt odpowiadający danemu wskaźnikowi CCW.</span><span class="sxs-lookup"><span data-stu-id="73497-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73497-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73497-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73497-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73497-109">Requirements</span></span>  
 <span data-ttu-id="73497-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73497-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73497-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="73497-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73497-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="73497-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73497-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73497-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73497-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73497-114">See also</span></span>

- [<span data-ttu-id="73497-115">ICorDebugAppDomain4, interfejs</span><span class="sxs-lookup"><span data-stu-id="73497-115">ICorDebugAppDomain4 Interface</span></span>](icordebugappdomain4-interface.md)
- [<span data-ttu-id="73497-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="73497-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
