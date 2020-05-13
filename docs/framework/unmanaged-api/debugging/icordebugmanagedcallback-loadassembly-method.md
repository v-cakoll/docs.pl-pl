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
ms.openlocfilehash: 8cb8699c103f48b42694449a2bb2bbd25c42d3c6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212734"
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="fc353-102">ICorDebugManagedCallback::LoadAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="fc353-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>
<span data-ttu-id="fc353-103">Powiadamia debuger o pomyślnym załadowaniu zestawu środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="fc353-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc353-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc353-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc353-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc353-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="fc353-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, do której zestaw został załadowany.</span><span class="sxs-lookup"><span data-stu-id="fc353-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="fc353-107">podczas Wskaźnik do obiektu ICorDebugAssembly, który reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="fc353-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc353-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc353-108">Requirements</span></span>  
 <span data-ttu-id="fc353-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc353-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc353-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fc353-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc353-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fc353-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc353-112">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc353-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc353-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc353-113">See also</span></span>

- [<span data-ttu-id="fc353-114">UnloadAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="fc353-114">UnloadAssembly Method</span></span>](icordebugmanagedcallback-unloadassembly-method.md)
- [<span data-ttu-id="fc353-115">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fc353-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
