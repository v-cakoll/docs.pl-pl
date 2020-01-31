---
title: ICorDebugManagedCallback::LoadAssembly — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadAssembly
helpviewer_keywords:
- LoadAssembly method [.NET Framework debugging]
- ICorDebugManagedCallback::LoadAssembly method [.NET Framework debugging]
ms.assetid: 55cb673a-e240-43a6-a406-6912e7c0fe66
topic_type:
- apiref
ms.openlocfilehash: 80836cbbf82a97ccd6dc7251e5cbe934e0cbe66f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777276"
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="e31c0-102">ICorDebugManagedCallback::LoadAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="e31c0-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>
<span data-ttu-id="e31c0-103">Powiadamia debuger o pomyślnym załadowaniu zestawu środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="e31c0-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e31c0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e31c0-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e31c0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e31c0-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="e31c0-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, do której zestaw został załadowany.</span><span class="sxs-lookup"><span data-stu-id="e31c0-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="e31c0-107">podczas Wskaźnik do obiektu ICorDebugAssembly, który reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="e31c0-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e31c0-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e31c0-108">Requirements</span></span>  
 <span data-ttu-id="e31c0-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e31c0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e31c0-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e31c0-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e31c0-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e31c0-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e31c0-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e31c0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e31c0-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e31c0-113">See also</span></span>

- [<span data-ttu-id="e31c0-114">UnloadAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="e31c0-114">UnloadAssembly Method</span></span>](icordebugmanagedcallback-unloadassembly-method.md)
- [<span data-ttu-id="e31c0-115">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="e31c0-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
