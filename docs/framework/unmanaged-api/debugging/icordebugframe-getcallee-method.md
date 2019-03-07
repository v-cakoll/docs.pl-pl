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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a179b68e2196eeadc712ae8f7d023b2943533335
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471072"
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="81083-102">ICorDebugFrame::GetCallee — Metoda</span><span class="sxs-lookup"><span data-stu-id="81083-102">ICorDebugFrame::GetCallee Method</span></span>
<span data-ttu-id="81083-103">Pobiera wskaźnik do obiektu ICorDebugFrame w łańcuchu bieżącym wywołaniu tej ramki.</span><span class="sxs-lookup"><span data-stu-id="81083-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81083-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="81083-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81083-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81083-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="81083-106">[out] Wskaźnik na adres `ICorDebugFrame` obiekt, który reprezentuje o nazwie ramki.</span><span class="sxs-lookup"><span data-stu-id="81083-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="81083-107">Ta wartość jest wartość null, jeśli ramka wywołującego jest najbardziej ramki w łańcuchu bieżącego.</span><span class="sxs-lookup"><span data-stu-id="81083-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81083-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81083-108">Requirements</span></span>  
 <span data-ttu-id="81083-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81083-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81083-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81083-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81083-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81083-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81083-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81083-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
