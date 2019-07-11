---
title: ICorDebugFunction::CreateBreakpoint — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::CreateBreakpoint
helpviewer_keywords:
- ICorDebugFunction::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: ffd0f708-0d21-4fae-a395-63b6c45828fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6eb93b84baf9dcd82d89bb1a4711a91d97c52779
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754789"
---
# <a name="icordebugfunctioncreatebreakpoint-method"></a><span data-ttu-id="1b8a2-102">ICorDebugFunction::CreateBreakpoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="1b8a2-102">ICorDebugFunction::CreateBreakpoint Method</span></span>
<span data-ttu-id="1b8a2-103">Tworzy punkt przerwania na początku tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="1b8a2-103">Creates a breakpoint at the beginning of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b8a2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b8a2-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateBreakpoint (  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b8a2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1b8a2-105">Parameters</span></span>  
 `ppBreakpoint`  
 <span data-ttu-id="1b8a2-106">[out] Wskaźnik na adres icordebugfunctionbreakpoint — obiekt, który reprezentuje nowy punkt przerwania funkcji.</span><span class="sxs-lookup"><span data-stu-id="1b8a2-106">[out] A pointer to the address of an ICorDebugFunctionBreakpoint object that represents the new breakpoint for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b8a2-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1b8a2-107">Requirements</span></span>  
 <span data-ttu-id="1b8a2-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b8a2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b8a2-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b8a2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b8a2-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b8a2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b8a2-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b8a2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
