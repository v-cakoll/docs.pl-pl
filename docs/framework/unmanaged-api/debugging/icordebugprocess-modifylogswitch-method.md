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
ms.openlocfilehash: 86b8737577bdb5f61f1061cb217620fae03ebd0c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139372"
---
# <a name="icordebugprocessmodifylogswitch-method"></a><span data-ttu-id="e8a39-102">ICorDebugProcess::ModifyLogSwitch — Metoda</span><span class="sxs-lookup"><span data-stu-id="e8a39-102">ICorDebugProcess::ModifyLogSwitch Method</span></span>
<span data-ttu-id="e8a39-103">Ustawia poziom ważności określonego przełącznika dziennika.</span><span class="sxs-lookup"><span data-stu-id="e8a39-103">Sets the severity level of the specified log switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8a39-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8a39-104">Syntax</span></span>  
  
```cpp  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8a39-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8a39-105">Parameters</span></span>  
 `pLogSwitchName`  
 <span data-ttu-id="e8a39-106">podczas Wskaźnik do ciągu, który określa nazwę przełącznika dziennika.</span><span class="sxs-lookup"><span data-stu-id="e8a39-106">[in] A pointer to a string that specifies the name of the log switch.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="e8a39-107">podczas Poziom ważności, który ma zostać ustawiony dla określonego przełączenia dziennika.</span><span class="sxs-lookup"><span data-stu-id="e8a39-107">[in] The severity level to be set for the specified log switch.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8a39-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e8a39-108">Remarks</span></span>  
 <span data-ttu-id="e8a39-109">Ta metoda jest prawidłowa tylko po wystąpieniu wywołania zwrotnego [ICorDebugManagedCallback:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e8a39-109">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8a39-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8a39-110">Requirements</span></span>  
 <span data-ttu-id="e8a39-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8a39-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8a39-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e8a39-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8a39-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e8a39-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8a39-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8a39-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
