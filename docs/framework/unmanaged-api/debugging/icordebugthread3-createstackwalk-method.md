---
title: ICorDebugThread3::CreateStackWalk — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.CreateStackWalk Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::CreateStackWalk
helpviewer_keywords:
- CreateStackWalk method [.NET Framework debugging]
- ICorDebugThread3::CreateStackWalk method [.NET Framework debugging]
ms.assetid: c55e35d9-f9aa-4268-94b5-dce44c61acf2
topic_type:
- apiref
ms.openlocfilehash: ca5db8c8570cedd9b0412b71058d453112a1831c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140128"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="b5634-102">ICorDebugThread3::CreateStackWalk — Metoda</span><span class="sxs-lookup"><span data-stu-id="b5634-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="b5634-103">Tworzy obiekt [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) dla wątku, którego stos ma zostać rozwinięcia.</span><span class="sxs-lookup"><span data-stu-id="b5634-103">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5634-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5634-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5634-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5634-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="b5634-106">określoną Wskaźnik do adresu obiektu [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) dla wątku, którego stos ma zostać rozwinięcia.</span><span class="sxs-lookup"><span data-stu-id="b5634-106">[out] A pointer to address of the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5634-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b5634-107">Return Value</span></span>  
 <span data-ttu-id="b5634-108">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="b5634-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b5634-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b5634-109">HRESULT</span></span>|<span data-ttu-id="b5634-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b5634-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b5634-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b5634-111">S_OK</span></span>|<span data-ttu-id="b5634-112">Obiekt `ICorDebugStackWalk` został pomyślnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="b5634-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="b5634-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b5634-113">E_FAIL</span></span>|<span data-ttu-id="b5634-114">Obiekt `ICorDebugStackWalk` nie został utworzony.</span><span class="sxs-lookup"><span data-stu-id="b5634-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="b5634-115">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="b5634-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5634-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b5634-116">Remarks</span></span>  
 <span data-ttu-id="b5634-117">Jeśli metoda `CreateStackWalk` powiedzie się, zostanie ustawiony kontekst zwróconego obiektu `ICorDebugStackWalk` dla bieżącego kontekstu wątku.</span><span class="sxs-lookup"><span data-stu-id="b5634-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5634-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b5634-118">Requirements</span></span>  
 <span data-ttu-id="b5634-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5634-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5634-120">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b5634-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5634-121">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b5634-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5634-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5634-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5634-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5634-123">See also</span></span>

- [<span data-ttu-id="b5634-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b5634-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b5634-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b5634-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
