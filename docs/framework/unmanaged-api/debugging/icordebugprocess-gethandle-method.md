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
ms.openlocfilehash: c5d81564a34ed8e7ef75840e3a174661c36f5411
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498089"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="f519b-102">ICorDebugProcess::GetHandle — Metoda</span><span class="sxs-lookup"><span data-stu-id="f519b-102">ICorDebugProcess::GetHandle Method</span></span>
<span data-ttu-id="f519b-103">Pobiera uchwyt do procesu.</span><span class="sxs-lookup"><span data-stu-id="f519b-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f519b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f519b-104">Syntax</span></span>  
  
```  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f519b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f519b-105">Parameters</span></span>  
 `phProcessHandle`  
 <span data-ttu-id="f519b-106">[out] Wskaźnik do `HPROCESS` oznacza to dojście do procesu.</span><span class="sxs-lookup"><span data-stu-id="f519b-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f519b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f519b-107">Remarks</span></span>  
 <span data-ttu-id="f519b-108">Pobrane uchwyt jest własnością interfejsu debugowania programu.</span><span class="sxs-lookup"><span data-stu-id="f519b-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="f519b-109">Debuger powinien zduplikować dojście przed jego użyciem.</span><span class="sxs-lookup"><span data-stu-id="f519b-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f519b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f519b-110">Requirements</span></span>  
 <span data-ttu-id="f519b-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f519b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f519b-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f519b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f519b-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f519b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f519b-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f519b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
