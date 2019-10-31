---
title: ICorDebugThread::GetCurrentException — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type:
- apiref
ms.openlocfilehash: 8082b2a3654f1605f18f3b68f54464dc83c8e60a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133489"
---
# <a name="icordebugthreadgetcurrentexception-method"></a><span data-ttu-id="7f843-102">ICorDebugThread::GetCurrentException — Metoda</span><span class="sxs-lookup"><span data-stu-id="7f843-102">ICorDebugThread::GetCurrentException Method</span></span>
<span data-ttu-id="7f843-103">Pobiera wskaźnik interfejsu do obiektu ICorDebugValue, który reprezentuje wyjątek, który jest aktualnie generowany przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="7f843-103">Gets an interface pointer to an ICorDebugValue object that represents an exception that is currently being thrown by managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f843-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f843-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f843-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f843-105">Parameters</span></span>  
 `ppExceptionObject`  
 <span data-ttu-id="7f843-106">określoną Wskaźnik do adresu obiektu `ICorDebugValue`, który reprezentuje wyjątek, który jest aktualnie generowany przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="7f843-106">[out] A pointer to the address of an `ICorDebugValue` object that represents the exception that is currently being thrown by managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f843-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7f843-107">Remarks</span></span>  
 <span data-ttu-id="7f843-108">Obiekt wyjątku będzie istniał od momentu zgłoszenia wyjątku do końca bloku `catch`.</span><span class="sxs-lookup"><span data-stu-id="7f843-108">The exception object will exist from the time the exception is thrown until the end of the `catch` block.</span></span> <span data-ttu-id="7f843-109">Ocena funkcji, która jest wykonywana przez metody ICorDebugEval, spowoduje wyczyszczenie obiektu wyjątku podczas instalacji i przywrócenie go po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="7f843-109">A function evaluation, which is performed by the ICorDebugEval methods, will clear out the exception object on setup and restore it on completion.</span></span>  
  
 <span data-ttu-id="7f843-110">Wyjątki mogą być zagnieżdżane (na przykład, jeśli wyjątek jest zgłaszany w filtr lub w ocenie funkcji), więc może istnieć wiele oczekujących wyjątków w pojedynczym wątku.</span><span class="sxs-lookup"><span data-stu-id="7f843-110">Exceptions can be nested (for example, if an exception is thrown in a filter or in a function evaluation), so there may be multiple outstanding exceptions on a single thread.</span></span> <span data-ttu-id="7f843-111">`GetCurrentException` zwraca najbardziej aktualny wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7f843-111">`GetCurrentException` returns the most current exception.</span></span>  
  
 <span data-ttu-id="7f843-112">Obiekt i typ wyjątku mogą ulec zmianie w całym okresie istnienia wyjątku.</span><span class="sxs-lookup"><span data-stu-id="7f843-112">The exception object and type may change throughout the life of the exception.</span></span> <span data-ttu-id="7f843-113">Na przykład po wystąpieniu wyjątku typu x, środowisko uruchomieniowe języka wspólnego (CLR) może za mało pamięci i podnieść go do wyjątku braku pamięci.</span><span class="sxs-lookup"><span data-stu-id="7f843-113">For example, after an exception of type x is thrown, the common language runtime (CLR) may run out of memory and promote it to an out-of-memory exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f843-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7f843-114">Requirements</span></span>  
 <span data-ttu-id="7f843-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f843-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f843-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7f843-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f843-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7f843-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f843-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f843-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
