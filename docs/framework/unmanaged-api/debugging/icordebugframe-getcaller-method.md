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
ms.openlocfilehash: a637cebb9e1aef20c600353eb14fe900ad7513c7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754160"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="5c555-102">ICorDebugFrame::GetCaller — Metoda</span><span class="sxs-lookup"><span data-stu-id="5c555-102">ICorDebugFrame::GetCaller Method</span></span>
<span data-ttu-id="5c555-103">Pobiera wskaźnik do obiektu ICorDebugFrame w łańcuchu bieżącym wywołaniu tej ramki.</span><span class="sxs-lookup"><span data-stu-id="5c555-103">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c555-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c555-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c555-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c555-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="5c555-106">[out] Wskaźnik na adres `ICorDebugFrame` obiekt, który reprezentuje wywoływania ramki.</span><span class="sxs-lookup"><span data-stu-id="5c555-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="5c555-107">Ta wartość jest wartość null, jeśli ramka o nazwie jest najbardziej zewnętrznej ramki w łańcuchu bieżącego.</span><span class="sxs-lookup"><span data-stu-id="5c555-107">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c555-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5c555-108">Requirements</span></span>  
 <span data-ttu-id="5c555-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c555-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c555-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c555-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c555-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c555-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c555-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c555-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
