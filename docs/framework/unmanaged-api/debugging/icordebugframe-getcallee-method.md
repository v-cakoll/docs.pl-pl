---
title: ICorDebugFrame::GetCallee — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type:
- apiref
ms.openlocfilehash: b83dec65e1dd4fc610be3190e8126e6d9d38a6e8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121220"
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="b109b-102">ICorDebugFrame::GetCallee — Metoda</span><span class="sxs-lookup"><span data-stu-id="b109b-102">ICorDebugFrame::GetCallee Method</span></span>
<span data-ttu-id="b109b-103">Pobiera wskaźnik do obiektu ICorDebugFrame w bieżącym łańcuchu, dla którego ta ramka została wywołana.</span><span class="sxs-lookup"><span data-stu-id="b109b-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b109b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b109b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b109b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b109b-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="b109b-106">określoną Wskaźnik do adresu obiektu `ICorDebugFrame`, który reprezentuje wywoływaną ramkę.</span><span class="sxs-lookup"><span data-stu-id="b109b-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="b109b-107">Ta wartość jest równa null, jeśli wywoływana ramka jest wewnętrzna ramką w bieżącym łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="b109b-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b109b-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b109b-108">Requirements</span></span>  
 <span data-ttu-id="b109b-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b109b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b109b-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b109b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b109b-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b109b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b109b-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b109b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
