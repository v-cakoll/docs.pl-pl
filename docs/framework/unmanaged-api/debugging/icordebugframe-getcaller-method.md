---
title: ICorDebugFrame::GetCaller — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCaller
helpviewer_keywords:
- GetCaller method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCaller method [.NET Framework debugging]
ms.assetid: bfdc946b-8238-4eb9-8a85-884049fb0fd4
topic_type:
- apiref
ms.openlocfilehash: b29de0b70daa783197e78fe985d379d4124bc140
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205144"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="d0cf9-102">ICorDebugFrame::GetCaller — Metoda</span><span class="sxs-lookup"><span data-stu-id="d0cf9-102">ICorDebugFrame::GetCaller Method</span></span>
<span data-ttu-id="d0cf9-103">Pobiera wskaźnik do obiektu ICorDebugFrame w bieżącym łańcuchu, który wywołał tę ramkę.</span><span class="sxs-lookup"><span data-stu-id="d0cf9-103">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0cf9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0cf9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0cf9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0cf9-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="d0cf9-106">określoną Wskaźnik do adresu `ICorDebugFrame` obiektu, który reprezentuje ramkę wywołującą.</span><span class="sxs-lookup"><span data-stu-id="d0cf9-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="d0cf9-107">Ta wartość jest równa null, jeśli wywoływana ramka jest skrajną zewnętrzną ramką w bieżącym łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="d0cf9-107">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0cf9-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d0cf9-108">Requirements</span></span>  
 <span data-ttu-id="d0cf9-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0cf9-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0cf9-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d0cf9-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0cf9-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d0cf9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0cf9-112">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0cf9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
