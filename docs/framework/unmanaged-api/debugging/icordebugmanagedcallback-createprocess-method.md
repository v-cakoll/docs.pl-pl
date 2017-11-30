---
title: "ICorDebugManagedCallback::CreateProcess — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.CreateProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::CreateProcess
helpviewer_keywords:
- ICorDebugManagedCallback::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: 8e89d5ee-e4e3-4738-8302-0b7d1cf4846e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bef3140717ff977fbfae813d0de89011b89ed062
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="383f1-102">ICorDebugManagedCallback::CreateProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="383f1-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="383f1-103">Powiadamia debuger został dołączony proces lub uruchomiony po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="383f1-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="383f1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="383f1-104">Syntax</span></span>  
  
```  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="383f1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="383f1-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="383f1-106">[in] Wskaźnik do obiektu ICorDebugProcess, który reprezentuje proces, który jest dołączony lub został rozpoczęty.</span><span class="sxs-lookup"><span data-stu-id="383f1-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="383f1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="383f1-107">Remarks</span></span>  
 <span data-ttu-id="383f1-108">Ta metoda nie jest wywoływany, dopóki nie została zainicjowana przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="383f1-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="383f1-109">Większość [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) metody zwróci CORDBG_E_NOTREADY przed `CreateProcess` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="383f1-109">Most of the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="383f1-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="383f1-110">Requirements</span></span>  
 <span data-ttu-id="383f1-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="383f1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="383f1-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="383f1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="383f1-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="383f1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="383f1-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="383f1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="383f1-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="383f1-115">See Also</span></span>  
 [<span data-ttu-id="383f1-116">ICorDebugManagedCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="383f1-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
