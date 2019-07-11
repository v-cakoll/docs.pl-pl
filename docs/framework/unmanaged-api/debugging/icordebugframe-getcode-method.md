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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca64e392b930ed57691f05ae771bbaf305df8eb3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754074"
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="0c35d-102">ICorDebugFrame::GetCode — Metoda</span><span class="sxs-lookup"><span data-stu-id="0c35d-102">ICorDebugFrame::GetCode Method</span></span>
<span data-ttu-id="0c35d-103">Pobiera wskaźnik do kodu skojarzonego z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="0c35d-103">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c35d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c35d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c35d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c35d-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="0c35d-106">[out] Wskaźnik na adres obiektu ICorDebugCode, która przedstawia kod skojarzony z tej ramki.</span><span class="sxs-lookup"><span data-stu-id="0c35d-106">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c35d-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c35d-107">Requirements</span></span>  
 <span data-ttu-id="0c35d-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c35d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c35d-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c35d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c35d-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c35d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c35d-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c35d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
