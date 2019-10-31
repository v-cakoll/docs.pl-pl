---
title: ICorDebugFrame::GetCode — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCode
helpviewer_keywords:
- GetCode method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCode method [.NET Framework debugging]
ms.assetid: fbaa0794-a031-4015-8beb-2749e47ac340
topic_type:
- apiref
ms.openlocfilehash: 9a4f533c0ab817d800c2d35b7d64c7aee78faaea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121164"
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="92295-102">ICorDebugFrame::GetCode — Metoda</span><span class="sxs-lookup"><span data-stu-id="92295-102">ICorDebugFrame::GetCode Method</span></span>
<span data-ttu-id="92295-103">Pobiera wskaźnik do kodu skojarzonego z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="92295-103">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92295-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92295-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92295-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92295-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="92295-106">określoną Wskaźnik do adresu obiektu ICorDebugCode, który reprezentuje kod skojarzony z tą ramką.</span><span class="sxs-lookup"><span data-stu-id="92295-106">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92295-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92295-107">Requirements</span></span>  
 <span data-ttu-id="92295-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92295-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92295-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="92295-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92295-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="92295-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92295-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92295-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
