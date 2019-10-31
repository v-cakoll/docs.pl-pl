---
title: ICorDebugManagedCallback::UnloadClass — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
ms.openlocfilehash: e2550320494b9ba43947c3176788042f5c2e6ad5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130631"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="76ca6-102">ICorDebugManagedCallback::UnloadClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="76ca6-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="76ca6-103">Powiadamia debuger, że Klasa jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="76ca6-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76ca6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="76ca6-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76ca6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="76ca6-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="76ca6-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji zawierającą klasę.</span><span class="sxs-lookup"><span data-stu-id="76ca6-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="76ca6-107">podczas Wskaźnik do obiektu ICorDebugClass, który reprezentuje klasę.</span><span class="sxs-lookup"><span data-stu-id="76ca6-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76ca6-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76ca6-108">Remarks</span></span>  
 <span data-ttu-id="76ca6-109">Nie należy odwoływać się do klasy po tym wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="76ca6-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76ca6-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="76ca6-110">Requirements</span></span>  
 <span data-ttu-id="76ca6-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76ca6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76ca6-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="76ca6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76ca6-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="76ca6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76ca6-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76ca6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76ca6-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76ca6-115">See also</span></span>

- [<span data-ttu-id="76ca6-116">LoadClass, metoda</span><span class="sxs-lookup"><span data-stu-id="76ca6-116">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="76ca6-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="76ca6-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
