---
title: ICorDebugProcess::GetHandle — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60bd7567f541a0bbaa3591d2f2905d13064dec3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423445"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="4ee8a-102">ICorDebugProcess::GetHandle — Metoda</span><span class="sxs-lookup"><span data-stu-id="4ee8a-102">ICorDebugProcess::GetHandle Method</span></span>
<span data-ttu-id="4ee8a-103">Pobiera dojścia do procesu.</span><span class="sxs-lookup"><span data-stu-id="4ee8a-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ee8a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ee8a-104">Syntax</span></span>  
  
```  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ee8a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ee8a-105">Parameters</span></span>  
 `phProcessHandle`  
 <span data-ttu-id="4ee8a-106">[out] Wskaźnik do `HPROCESS` oznacza to dojścia do procesu.</span><span class="sxs-lookup"><span data-stu-id="4ee8a-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ee8a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ee8a-107">Remarks</span></span>  
 <span data-ttu-id="4ee8a-108">Pobrane dojścia jest należących do interfejsu debugowania.</span><span class="sxs-lookup"><span data-stu-id="4ee8a-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="4ee8a-109">Debuger powinien zduplikowane dojście przed jego użyciem.</span><span class="sxs-lookup"><span data-stu-id="4ee8a-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ee8a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4ee8a-110">Requirements</span></span>  
 <span data-ttu-id="4ee8a-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ee8a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ee8a-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4ee8a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ee8a-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ee8a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ee8a-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ee8a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
