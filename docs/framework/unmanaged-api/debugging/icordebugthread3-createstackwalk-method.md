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
ms.openlocfilehash: f2850e6c9cbb2250a08ab4a0e34c69e377d3a23d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83375853"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="57f11-102">ICorDebugThread3::CreateStackWalk — Metoda</span><span class="sxs-lookup"><span data-stu-id="57f11-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="57f11-103">Tworzy obiekt [ICorDebugStackWalk](icordebugstackwalk-interface.md) dla wątku, którego stos ma zostać rozwinięcia.</span><span class="sxs-lookup"><span data-stu-id="57f11-103">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57f11-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="57f11-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57f11-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57f11-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="57f11-106">określoną Wskaźnik do adresu obiektu [ICorDebugStackWalk](icordebugstackwalk-interface.md) dla wątku, którego stos ma zostać rozwinięcia.</span><span class="sxs-lookup"><span data-stu-id="57f11-106">[out] A pointer to address of the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57f11-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="57f11-107">Return Value</span></span>  
 <span data-ttu-id="57f11-108">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="57f11-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="57f11-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57f11-109">HRESULT</span></span>|<span data-ttu-id="57f11-110">Opis</span><span class="sxs-lookup"><span data-stu-id="57f11-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57f11-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="57f11-111">S_OK</span></span>|<span data-ttu-id="57f11-112">`ICorDebugStackWalk`Obiekt został pomyślnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="57f11-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="57f11-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57f11-113">E_FAIL</span></span>|<span data-ttu-id="57f11-114">`ICorDebugStackWalk`Obiekt nie został utworzony.</span><span class="sxs-lookup"><span data-stu-id="57f11-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="57f11-115">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="57f11-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57f11-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="57f11-116">Remarks</span></span>  
 <span data-ttu-id="57f11-117">Jeśli `CreateStackWalk` Metoda zakończy się pomyślnie, kontekst zwróconego `ICorDebugStackWalk` obiektu jest ustawiony na bieżący kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="57f11-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57f11-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="57f11-118">Requirements</span></span>  
 <span data-ttu-id="57f11-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57f11-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57f11-120">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="57f11-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57f11-121">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="57f11-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57f11-122">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57f11-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57f11-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57f11-123">See also</span></span>

- [<span data-ttu-id="57f11-124">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="57f11-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="57f11-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="57f11-125">Debugging</span></span>](index.md)
