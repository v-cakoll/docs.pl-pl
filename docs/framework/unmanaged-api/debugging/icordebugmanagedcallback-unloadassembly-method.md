---
title: ICorDebugManagedCallback::UnloadAssembly — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type:
- apiref
ms.openlocfilehash: 06c08499298656c8314d72667d9dac88c8d11e6a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788342"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="6a7c7-102">ICorDebugManagedCallback::UnloadAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="6a7c7-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="6a7c7-103">Powiadamia debuger, że zestaw środowiska uruchomieniowego języka wspólnego został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="6a7c7-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a7c7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a7c7-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a7c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a7c7-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="6a7c7-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, która zawiera zestaw.</span><span class="sxs-lookup"><span data-stu-id="6a7c7-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="6a7c7-107">podczas Wskaźnik do obiektu ICorDebugAssembly, który reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="6a7c7-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a7c7-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a7c7-108">Remarks</span></span>  
 <span data-ttu-id="6a7c7-109">Zestawu nie należy używać po tym wywołaniu zwrotnym.</span><span class="sxs-lookup"><span data-stu-id="6a7c7-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a7c7-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6a7c7-110">Requirements</span></span>  
 <span data-ttu-id="6a7c7-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a7c7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a7c7-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6a7c7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a7c7-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6a7c7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a7c7-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a7c7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a7c7-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a7c7-115">See also</span></span>

- [<span data-ttu-id="6a7c7-116">LoadAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="6a7c7-116">LoadAssembly Method</span></span>](icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="6a7c7-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="6a7c7-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
