---
title: ICorDebugThread::GetActiveFrame — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveFrame
helpviewer_keywords:
- ICorDebugThread::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 8d6d3a1a-fef6-4f2f-a22c-3bdd30d70e07
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 390a2c64508bf407296d318a47bfd2972b7ef9d9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762564"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="9f954-102">ICorDebugThread::GetActiveFrame — Metoda</span><span class="sxs-lookup"><span data-stu-id="9f954-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="9f954-103">Pobiera wskaźnik interfejsu do aktywnej ramki (najnowsze) dla tego obiektu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="9f954-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f954-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9f954-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f954-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f954-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="9f954-106">[out] Wskaźnik na adres obiektu interfejsu ICorDebugFrame, który reprezentuje ramkę.</span><span class="sxs-lookup"><span data-stu-id="9f954-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f954-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9f954-107">Remarks</span></span>  
 <span data-ttu-id="9f954-108">`ppFrame` Parametr ma wartość null, jeśli ramka nie jest obecnie aktywna.</span><span class="sxs-lookup"><span data-stu-id="9f954-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f954-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9f954-109">Requirements</span></span>  
 <span data-ttu-id="9f954-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f954-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f954-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f954-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f954-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f954-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f954-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f954-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
