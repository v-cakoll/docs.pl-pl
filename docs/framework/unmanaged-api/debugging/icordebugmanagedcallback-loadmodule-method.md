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
ms.openlocfilehash: cd4a16bc8b48f147ed03555b51eee5f42a445bc6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212704"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="877e0-102">ICorDebugManagedCallback::LoadModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="877e0-102">ICorDebugManagedCallback::LoadModule Method</span></span>
<span data-ttu-id="877e0-103">Powiadamia debuger o pomyślnym załadowaniu modułu środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="877e0-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="877e0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="877e0-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="877e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="877e0-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="877e0-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, do której moduł został załadowany.</span><span class="sxs-lookup"><span data-stu-id="877e0-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="877e0-107">podczas Wskaźnik do obiektu ICorDebugModule, który reprezentuje moduł CLR.</span><span class="sxs-lookup"><span data-stu-id="877e0-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="877e0-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="877e0-108">Remarks</span></span>  
 <span data-ttu-id="877e0-109">`LoadModule`Wywołanie zwrotne zapewnia odpowiedni czas na sprawdzenie metadanych modułu, ustawienie flag kompilatora just-in-Time (JIT) lub włączenie lub wyłączenie wywołania zwrotnego ładowania klasy dla modułu.</span><span class="sxs-lookup"><span data-stu-id="877e0-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="877e0-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="877e0-110">Requirements</span></span>  
 <span data-ttu-id="877e0-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="877e0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="877e0-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="877e0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="877e0-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="877e0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="877e0-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="877e0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="877e0-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="877e0-115">See also</span></span>

- [<span data-ttu-id="877e0-116">UnloadModule, metoda</span><span class="sxs-lookup"><span data-stu-id="877e0-116">UnloadModule Method</span></span>](icordebugmanagedcallback-unloadmodule-method.md)
- [<span data-ttu-id="877e0-117">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="877e0-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
