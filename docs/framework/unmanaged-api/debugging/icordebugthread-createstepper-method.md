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
ms.openlocfilehash: d1b058aef66ed32c2cadcc3cfd72320dd8eb7729
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133591"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="5b1ae-102">ICorDebugThread::CreateStepper — Metoda</span><span class="sxs-lookup"><span data-stu-id="5b1ae-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="5b1ae-103">Tworzy obiekt ICorDebugStepper, który umożliwia przechodzenie przez aktywną ramkę tego ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="5b1ae-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b1ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b1ae-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b1ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b1ae-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="5b1ae-106">określoną Wskaźnik do adresu obiektu `ICorDebugStepper`, który umożliwia przechodzenie przez aktywną ramkę tego wątku.</span><span class="sxs-lookup"><span data-stu-id="5b1ae-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b1ae-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5b1ae-107">Remarks</span></span>  
 <span data-ttu-id="5b1ae-108">Aktywna ramka może być kodem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="5b1ae-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="5b1ae-109">Aby wykonać rzeczywiste przechodzenie, należy użyć interfejsu `ICorDebugStepper`.</span><span class="sxs-lookup"><span data-stu-id="5b1ae-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b1ae-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5b1ae-110">Requirements</span></span>  
 <span data-ttu-id="5b1ae-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b1ae-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b1ae-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5b1ae-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b1ae-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5b1ae-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b1ae-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b1ae-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
