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
ms.openlocfilehash: a74d32478bc88ee634fa5ff9b61ac2059bc8e302
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379718"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="fe2c0-102">ICorDebugThread::CreateStepper — Metoda</span><span class="sxs-lookup"><span data-stu-id="fe2c0-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="fe2c0-103">Tworzy obiekt ICorDebugStepper, który umożliwia przechodzenie przez aktywną ramkę tego ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="fe2c0-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe2c0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe2c0-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe2c0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe2c0-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="fe2c0-106">określoną Wskaźnik do adresu `ICorDebugStepper` obiektu, który umożliwia przechodzenie przez aktywną ramkę tego wątku.</span><span class="sxs-lookup"><span data-stu-id="fe2c0-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe2c0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fe2c0-107">Remarks</span></span>  
 <span data-ttu-id="fe2c0-108">Aktywna ramka może być kodem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="fe2c0-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="fe2c0-109">`ICorDebugStepper`Interfejs musi być używany do wykonywania rzeczywistego kroku.</span><span class="sxs-lookup"><span data-stu-id="fe2c0-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe2c0-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fe2c0-110">Requirements</span></span>  
 <span data-ttu-id="fe2c0-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe2c0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe2c0-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fe2c0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe2c0-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fe2c0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe2c0-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe2c0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
