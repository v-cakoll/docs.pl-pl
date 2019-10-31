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
ms.openlocfilehash: e4061580d59b0cf2a6e6e481d5242005e9452caf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128872"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="17195-102">ICorDebugProcess::GetHandle — Metoda</span><span class="sxs-lookup"><span data-stu-id="17195-102">ICorDebugProcess::GetHandle Method</span></span>
<span data-ttu-id="17195-103">Pobiera dojście do procesu.</span><span class="sxs-lookup"><span data-stu-id="17195-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17195-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="17195-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17195-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="17195-105">Parameters</span></span>  
 `phProcessHandle`  
 <span data-ttu-id="17195-106">określoną Wskaźnik do `HPROCESS`, który jest dojściem do procesu.</span><span class="sxs-lookup"><span data-stu-id="17195-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17195-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="17195-107">Remarks</span></span>  
 <span data-ttu-id="17195-108">Pobrany uchwyt jest własnością interfejsu debugowania.</span><span class="sxs-lookup"><span data-stu-id="17195-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="17195-109">Debuger powinien zduplikować dojście przed jego użyciem.</span><span class="sxs-lookup"><span data-stu-id="17195-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17195-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="17195-110">Requirements</span></span>  
 <span data-ttu-id="17195-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17195-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17195-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="17195-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17195-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="17195-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17195-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17195-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
