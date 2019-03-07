---
title: ICorDebugThread::CreateStepper — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89182739633984011aaab3d7900d376b6db5ef99
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476207"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="b794f-102">ICorDebugThread::CreateStepper — Metoda</span><span class="sxs-lookup"><span data-stu-id="b794f-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="b794f-103">Tworzy obiekt ICorDebugStepper —, który umożliwia krokowe wykonywanie aktywnej ramki tego ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="b794f-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b794f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b794f-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b794f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b794f-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="b794f-106">[out] Wskaźnik na adres `ICorDebugStepper` obiekt, który umożliwia krokowe wykonywanie aktywnej ramki tego wątku.</span><span class="sxs-lookup"><span data-stu-id="b794f-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b794f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b794f-107">Remarks</span></span>  
 <span data-ttu-id="b794f-108">Aktywnej ramki mogą być kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="b794f-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="b794f-109">`ICorDebugStepper` Interfejsu muszą być używane do wykonania rzeczywistego krokowego.</span><span class="sxs-lookup"><span data-stu-id="b794f-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b794f-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b794f-110">Requirements</span></span>  
 <span data-ttu-id="b794f-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b794f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b794f-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b794f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b794f-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b794f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b794f-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b794f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
