---
title: ICorDebugProcess::ModifyLogSwitch — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ModifyLogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ModifyLogSwitch
helpviewer_keywords:
- ICorDebugProcess::ModifyLogSwitch method [.NET Framework debugging]
- ModifyLogSwitch method [.NET Framework debugging]
ms.assetid: 5fd30875-555e-4e96-877b-5dd266cde7c4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96db1ca115ffed47b5eb8eadd9c3d2f620060c4a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755448"
---
# <a name="icordebugprocessmodifylogswitch-method"></a><span data-ttu-id="e0bf3-102">ICorDebugProcess::ModifyLogSwitch — Metoda</span><span class="sxs-lookup"><span data-stu-id="e0bf3-102">ICorDebugProcess::ModifyLogSwitch Method</span></span>
<span data-ttu-id="e0bf3-103">Ustawia poziom ważności przełącznika określonego dziennika.</span><span class="sxs-lookup"><span data-stu-id="e0bf3-103">Sets the severity level of the specified log switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0bf3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0bf3-104">Syntax</span></span>  
  
```cpp  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0bf3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0bf3-105">Parameters</span></span>  
 `pLogSwitchName`  
 <span data-ttu-id="e0bf3-106">[in] Wskaźnik do ciągu, który określa nazwę przełącznika dziennika.</span><span class="sxs-lookup"><span data-stu-id="e0bf3-106">[in] A pointer to a string that specifies the name of the log switch.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="e0bf3-107">[in] Poziom ważności, należy ustawić dla przełącznika określonego dziennika.</span><span class="sxs-lookup"><span data-stu-id="e0bf3-107">[in] The severity level to be set for the specified log switch.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0bf3-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e0bf3-108">Remarks</span></span>  
 <span data-ttu-id="e0bf3-109">Ta metoda jest prawidłowa tylko po [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) wystąpiło wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="e0bf3-109">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0bf3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e0bf3-110">Requirements</span></span>  
 <span data-ttu-id="e0bf3-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0bf3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0bf3-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0bf3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0bf3-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0bf3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0bf3-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0bf3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
