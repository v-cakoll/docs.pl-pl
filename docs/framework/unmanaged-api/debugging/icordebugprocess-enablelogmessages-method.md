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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b199d3226ec391fadc356b5efacdbf10a3e25adf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766158"
---
# <a name="icordebugprocessenablelogmessages-method"></a><span data-ttu-id="9b0d0-102">ICorDebugProcess::EnableLogMessages — Metoda</span><span class="sxs-lookup"><span data-stu-id="9b0d0-102">ICorDebugProcess::EnableLogMessages Method</span></span>
<span data-ttu-id="9b0d0-103">Włącza i wyłącza transmisji komunikatów dziennika do debugera.</span><span class="sxs-lookup"><span data-stu-id="9b0d0-103">Enables and disables the transmission of log messages to the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b0d0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9b0d0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b0d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b0d0-105">Parameters</span></span>  
 `fOnOff`  
 <span data-ttu-id="9b0d0-106">[in] `true` umożliwia przekazywanie komunikaty w Dzienniku; `false` wyłącza transmisji.</span><span class="sxs-lookup"><span data-stu-id="9b0d0-106">[in] `true` enables the transmission of log messages; `false` disables the transmission.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b0d0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9b0d0-107">Remarks</span></span>  
 <span data-ttu-id="9b0d0-108">Ta metoda jest prawidłowa tylko po [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) występuje wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="9b0d0-108">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback occurs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b0d0-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9b0d0-109">Requirements</span></span>  
 <span data-ttu-id="9b0d0-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b0d0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b0d0-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b0d0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b0d0-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b0d0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b0d0-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b0d0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
