---
title: ICorDebugFrame::GetChain — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetChain
helpviewer_keywords:
- ICorDebugFrame::GetChain method [.NET Framework debugging]
- GetChain method [.NET Framework debugging]
ms.assetid: e28e51d3-8f73-494f-bcd4-48bac239fbe1
topic_type:
- apiref
ms.openlocfilehash: 9677fd14f50cf93eac7eeaef784082d45e8884c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137684"
---
# <a name="icordebugframegetchain-method"></a><span data-ttu-id="a1b1b-102">ICorDebugFrame::GetChain — Metoda</span><span class="sxs-lookup"><span data-stu-id="a1b1b-102">ICorDebugFrame::GetChain Method</span></span>
<span data-ttu-id="a1b1b-103">Pobiera wskaźnik do łańcucha, do którego należy ta ramka.</span><span class="sxs-lookup"><span data-stu-id="a1b1b-103">Gets a pointer to the chain this frame is a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1b1b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1b1b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChain (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1b1b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1b1b-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="a1b1b-106">określoną Wskaźnik do adresu obiektu ICorDebugChain, który reprezentuje łańcuch zawierający tę ramkę.</span><span class="sxs-lookup"><span data-stu-id="a1b1b-106">[out] A pointer to the address of an ICorDebugChain object that represents the chain containing this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1b1b-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1b1b-107">Requirements</span></span>  
 <span data-ttu-id="a1b1b-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1b1b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1b1b-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a1b1b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1b1b-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a1b1b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1b1b-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1b1b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
