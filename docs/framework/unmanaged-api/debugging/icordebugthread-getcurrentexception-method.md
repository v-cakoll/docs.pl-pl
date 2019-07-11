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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a6d53ebfebb8c883065ce119c2338a2225f0472
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762479"
---
# <a name="icordebugthreadgetcurrentexception-method"></a><span data-ttu-id="c56b3-102">ICorDebugThread::GetCurrentException — Metoda</span><span class="sxs-lookup"><span data-stu-id="c56b3-102">ICorDebugThread::GetCurrentException Method</span></span>
<span data-ttu-id="c56b3-103">Pobiera wskaźnik interfejsu do obiektu ICorDebugValue, który przedstawia wyjątek, który obecnie został zgłoszony przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="c56b3-103">Gets an interface pointer to an ICorDebugValue object that represents an exception that is currently being thrown by managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c56b3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c56b3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c56b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c56b3-105">Parameters</span></span>  
 `ppExceptionObject`  
 <span data-ttu-id="c56b3-106">[out] Wskaźnik na adres `ICorDebugValue` obiekt, który reprezentuje wyjątek, który obecnie został zgłoszony przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="c56b3-106">[out] A pointer to the address of an `ICorDebugValue` object that represents the exception that is currently being thrown by managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c56b3-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c56b3-107">Remarks</span></span>  
 <span data-ttu-id="c56b3-108">Obiekt wyjątku będzie istnieć od momentu wyjątek aż do końca `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="c56b3-108">The exception object will exist from the time the exception is thrown until the end of the `catch` block.</span></span> <span data-ttu-id="c56b3-109">Obliczanie funkcji, które jest wykonywane za pomocą metod ICorDebugEval, należy usunąć obiekt wyjątku na temat instalacji, a następnie przywróć ją po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="c56b3-109">A function evaluation, which is performed by the ICorDebugEval methods, will clear out the exception object on setup and restore it on completion.</span></span>  
  
 <span data-ttu-id="c56b3-110">Wyjątki mogą być zagnieżdżane (na przykład, jeśli wyjątek jest zgłaszany w filtrze lub obliczanie funkcji), dlatego może być wiele wyjątków oczekujących w jednym wątku.</span><span class="sxs-lookup"><span data-stu-id="c56b3-110">Exceptions can be nested (for example, if an exception is thrown in a filter or in a function evaluation), so there may be multiple outstanding exceptions on a single thread.</span></span> <span data-ttu-id="c56b3-111">`GetCurrentException` Zwraca najbardziej bieżącego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c56b3-111">`GetCurrentException` returns the most current exception.</span></span>  
  
 <span data-ttu-id="c56b3-112">Obiekt wyjątku i typu mogą ulec zmianie w całym cyklu życia wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c56b3-112">The exception object and type may change throughout the life of the exception.</span></span> <span data-ttu-id="c56b3-113">Na przykład po typu x jest zwracany wyjątek, środowisko uruchomieniowe języka wspólnego (CLR) może przekroczyć dostępną ilość pamięci i podwyższyć jego poziom do wyjątku braku pamięci.</span><span class="sxs-lookup"><span data-stu-id="c56b3-113">For example, after an exception of type x is thrown, the common language runtime (CLR) may run out of memory and promote it to an out-of-memory exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c56b3-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c56b3-114">Requirements</span></span>  
 <span data-ttu-id="c56b3-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c56b3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c56b3-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c56b3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c56b3-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c56b3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c56b3-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c56b3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
