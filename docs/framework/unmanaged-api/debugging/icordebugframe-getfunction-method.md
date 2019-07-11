---
title: ICorDebugFrame::GetFunction — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetFunction method [.NET Framework debugging]
ms.assetid: 879d2311-0ff1-4616-a8b3-959ea5868b2e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f801dae69f16f2848b4ffa30f458c084fe9750a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754901"
---
# <a name="icordebugframegetfunction-method"></a><span data-ttu-id="7410b-102">ICorDebugFrame::GetFunction — Metoda</span><span class="sxs-lookup"><span data-stu-id="7410b-102">ICorDebugFrame::GetFunction Method</span></span>
<span data-ttu-id="7410b-103">Pobiera funkcję, która zawiera kod skojarzony z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="7410b-103">Gets the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7410b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7410b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7410b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7410b-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="7410b-106">[out] Wskaźnik na adres obiektu ICorDebugFunction, który reprezentuje funkcję zawierające kod skojarzony z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="7410b-106">[out] A pointer to the address of an ICorDebugFunction object that represents the function containing the code associated with this stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7410b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7410b-107">Remarks</span></span>  
 <span data-ttu-id="7410b-108">`GetFunction` Metoda może zakończyć się niepowodzeniem, jeśli ramka nie jest skojarzona z dowolną określoną funkcję.</span><span class="sxs-lookup"><span data-stu-id="7410b-108">The `GetFunction` method may fail if the frame is not associated with any particular function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7410b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7410b-109">Requirements</span></span>  
 <span data-ttu-id="7410b-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7410b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7410b-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7410b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7410b-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7410b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7410b-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7410b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
