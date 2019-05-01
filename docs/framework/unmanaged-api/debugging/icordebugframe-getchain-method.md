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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 032c1e3dcfe50cd30953ca581ff9f0d83b78518d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995868"
---
# <a name="icordebugframegetchain-method"></a><span data-ttu-id="7bf25-102">ICorDebugFrame::GetChain — Metoda</span><span class="sxs-lookup"><span data-stu-id="7bf25-102">ICorDebugFrame::GetChain Method</span></span>
<span data-ttu-id="7bf25-103">Pobiera wskaźnik do łańcucha, do którego należy ta ramka.</span><span class="sxs-lookup"><span data-stu-id="7bf25-103">Gets a pointer to the chain this frame is a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bf25-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7bf25-104">Syntax</span></span>  
  
```  
HRESULT GetChain (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bf25-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7bf25-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="7bf25-106">[out] Wskaźnik na adres icordebugchain — obiekt, który reprezentuje łańcuch zawierający tej ramki.</span><span class="sxs-lookup"><span data-stu-id="7bf25-106">[out] A pointer to the address of an ICorDebugChain object that represents the chain containing this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bf25-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7bf25-107">Requirements</span></span>  
 <span data-ttu-id="7bf25-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bf25-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bf25-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7bf25-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7bf25-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bf25-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bf25-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bf25-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
