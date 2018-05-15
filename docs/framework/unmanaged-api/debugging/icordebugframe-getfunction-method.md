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
ms.openlocfilehash: 1b622d1bd82e53d5fa232e07b1f49e6fbba3ccba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugframegetfunction-method"></a><span data-ttu-id="34f78-102">ICorDebugFrame::GetFunction — Metoda</span><span class="sxs-lookup"><span data-stu-id="34f78-102">ICorDebugFrame::GetFunction Method</span></span>
<span data-ttu-id="34f78-103">Pobiera funkcję, która zawiera kod skojarzony z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="34f78-103">Gets the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34f78-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="34f78-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34f78-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="34f78-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="34f78-106">[out] Wskaźnik do adresu ICorDebugFunction obiekt, który reprezentuje funkcję kodem skojarzone z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="34f78-106">[out] A pointer to the address of an ICorDebugFunction object that represents the function containing the code associated with this stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34f78-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34f78-107">Remarks</span></span>  
 <span data-ttu-id="34f78-108">`GetFunction` Metody może zakończyć się niepowodzeniem, jeśli ramka nie jest skojarzony z dowolnej określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="34f78-108">The `GetFunction` method may fail if the frame is not associated with any particular function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34f78-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="34f78-109">Requirements</span></span>  
 <span data-ttu-id="34f78-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34f78-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34f78-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34f78-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34f78-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34f78-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34f78-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34f78-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
