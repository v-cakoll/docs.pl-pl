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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82902e6a395fe62464065ccea4cca5b52c960f0d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988822"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="e04c9-102">ICorDebugFrame::GetCaller — Metoda</span><span class="sxs-lookup"><span data-stu-id="e04c9-102">ICorDebugFrame::GetCaller Method</span></span>
<span data-ttu-id="e04c9-103">Pobiera wskaźnik do obiektu ICorDebugFrame w łańcuchu bieżącym wywołaniu tej ramki.</span><span class="sxs-lookup"><span data-stu-id="e04c9-103">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e04c9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e04c9-104">Syntax</span></span>  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e04c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e04c9-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="e04c9-106">[out] Wskaźnik na adres `ICorDebugFrame` obiekt, który reprezentuje wywoływania ramki.</span><span class="sxs-lookup"><span data-stu-id="e04c9-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="e04c9-107">Ta wartość jest wartość null, jeśli ramka o nazwie jest najbardziej zewnętrznej ramki w łańcuchu bieżącego.</span><span class="sxs-lookup"><span data-stu-id="e04c9-107">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e04c9-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e04c9-108">Requirements</span></span>  
 <span data-ttu-id="e04c9-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e04c9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e04c9-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e04c9-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e04c9-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e04c9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e04c9-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e04c9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
