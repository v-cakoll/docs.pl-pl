---
title: ICorDebugManagedCallback::LoadModule — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
ms.openlocfilehash: 21a97f140a41f8f380c1334652bc2417e19659c6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777138"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="e4857-102">ICorDebugManagedCallback::LoadModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="e4857-102">ICorDebugManagedCallback::LoadModule Method</span></span>
<span data-ttu-id="e4857-103">Powiadamia debuger o pomyślnym załadowaniu modułu środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="e4857-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4857-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4857-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4857-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4857-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="e4857-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, do której moduł został załadowany.</span><span class="sxs-lookup"><span data-stu-id="e4857-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="e4857-107">podczas Wskaźnik do obiektu ICorDebugModule, który reprezentuje moduł CLR.</span><span class="sxs-lookup"><span data-stu-id="e4857-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4857-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e4857-108">Remarks</span></span>  
 <span data-ttu-id="e4857-109">Wywołanie zwrotne `LoadModule` zapewnia odpowiedni czas na przeanalizowanie metadanych dla modułu, ustawienie flag kompilatora just-in-Time (JIT) lub włączenie lub wyłączenie wywołania zwrotnego ładowania klasy dla modułu.</span><span class="sxs-lookup"><span data-stu-id="e4857-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4857-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4857-110">Requirements</span></span>  
 <span data-ttu-id="e4857-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4857-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4857-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e4857-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4857-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e4857-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4857-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4857-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4857-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4857-115">See also</span></span>

- [<span data-ttu-id="e4857-116">UnloadModule, metoda</span><span class="sxs-lookup"><span data-stu-id="e4857-116">UnloadModule Method</span></span>](icordebugmanagedcallback-unloadmodule-method.md)
- [<span data-ttu-id="e4857-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4857-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
