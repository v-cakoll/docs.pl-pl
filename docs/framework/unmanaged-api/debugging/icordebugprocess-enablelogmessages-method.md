---
title: ICorDebugProcess::EnableLogMessages — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnableLogMessages
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnableLogMessages
helpviewer_keywords:
- ICorDebugProcess::EnableLogMessages method [.NET Framework debugging]
- EnableLogMessages method [.NET Framework debugging]
ms.assetid: 14a4e5a3-3eaf-4f53-9dd1-762726963a23
topic_type:
- apiref
ms.openlocfilehash: 4134062be93a2fc5e76949d465a7b5822556b408
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128903"
---
# <a name="icordebugprocessenablelogmessages-method"></a><span data-ttu-id="99886-102">ICorDebugProcess::EnableLogMessages — Metoda</span><span class="sxs-lookup"><span data-stu-id="99886-102">ICorDebugProcess::EnableLogMessages Method</span></span>
<span data-ttu-id="99886-103">Włącza i wyłącza przekazywanie komunikatów dziennika do debugera.</span><span class="sxs-lookup"><span data-stu-id="99886-103">Enables and disables the transmission of log messages to the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99886-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="99886-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99886-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99886-105">Parameters</span></span>  
 `fOnOff`  
 <span data-ttu-id="99886-106">[in] `true` włącza przekazywanie komunikatów dziennika; `false` wyłącza transmisję.</span><span class="sxs-lookup"><span data-stu-id="99886-106">[in] `true` enables the transmission of log messages; `false` disables the transmission.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99886-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99886-107">Remarks</span></span>  
 <span data-ttu-id="99886-108">Ta metoda jest prawidłowa tylko po wywołaniu wywołania zwrotnego [ICorDebugManagedCallback:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="99886-108">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback occurs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99886-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99886-109">Requirements</span></span>  
 <span data-ttu-id="99886-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99886-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99886-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="99886-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99886-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="99886-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99886-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99886-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
