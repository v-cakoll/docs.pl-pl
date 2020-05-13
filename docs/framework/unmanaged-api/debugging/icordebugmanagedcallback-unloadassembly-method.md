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
ms.openlocfilehash: 07996a78d7f559de587c8a3eb2babfc06675169d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212649"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="a785f-102">ICorDebugManagedCallback::UnloadAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="a785f-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="a785f-103">Powiadamia debuger, że zestaw środowiska uruchomieniowego języka wspólnego został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="a785f-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a785f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a785f-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a785f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a785f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="a785f-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, która zawiera zestaw.</span><span class="sxs-lookup"><span data-stu-id="a785f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="a785f-107">podczas Wskaźnik do obiektu ICorDebugAssembly, który reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="a785f-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a785f-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a785f-108">Remarks</span></span>  
 <span data-ttu-id="a785f-109">Zestawu nie należy używać po tym wywołaniu zwrotnym.</span><span class="sxs-lookup"><span data-stu-id="a785f-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a785f-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a785f-110">Requirements</span></span>  
 <span data-ttu-id="a785f-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a785f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a785f-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a785f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a785f-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a785f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a785f-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a785f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a785f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a785f-115">See also</span></span>

- [<span data-ttu-id="a785f-116">LoadAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="a785f-116">LoadAssembly Method</span></span>](icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="a785f-117">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a785f-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
