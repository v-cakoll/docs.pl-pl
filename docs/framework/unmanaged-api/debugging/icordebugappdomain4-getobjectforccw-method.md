---
title: ICorDebugAppDomain4::GetObjectForCCW — metoda
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: a175a6b6c91c284348580e1d9dc9ef0c5f5fc5df
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895116"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="deb4e-102">ICorDebugAppDomain4::GetObjectForCCW — metoda</span><span class="sxs-lookup"><span data-stu-id="deb4e-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="deb4e-103">Pobiera obiekt zarządzany z wskaźnika otoki (CCW) modelu COM.</span><span class="sxs-lookup"><span data-stu-id="deb4e-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deb4e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="deb4e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="deb4e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="deb4e-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="deb4e-106">podczas Wskaźnik wywoływanej otoki COM (CCW).</span><span class="sxs-lookup"><span data-stu-id="deb4e-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="deb4e-107">określoną Wskaźnik do adresu obiektu "ICorDebugValue", który reprezentuje zarządzany obiekt odpowiadający danemu wskaźnikowi CCW.</span><span class="sxs-lookup"><span data-stu-id="deb4e-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="deb4e-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="deb4e-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="deb4e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="deb4e-109">Requirements</span></span>  
 <span data-ttu-id="deb4e-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="deb4e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="deb4e-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="deb4e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="deb4e-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="deb4e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="deb4e-113">**.NET Framework wersje:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="deb4e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deb4e-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="deb4e-114">See also</span></span>

- [<span data-ttu-id="deb4e-115">ICorDebugAppDomain4 — interfejs</span><span class="sxs-lookup"><span data-stu-id="deb4e-115">ICorDebugAppDomain4 Interface</span></span>](icordebugappdomain4-interface.md)
- [<span data-ttu-id="deb4e-116">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="deb4e-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
