---
title: ICorDebugThread2::GetActiveFunctions — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetActiveFunctions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetActiveFunctions
helpviewer_keywords:
- GetActiveFunctions method [.NET Framework debugging]
- ICorDebugThread2::GetActiveFunctions method [.NET Framework debugging]
ms.assetid: 27fae01a-ecec-423a-973e-24f8de55826c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed13f78d5a1f6d54b12c86613715f4878a521bfa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489933"
---
# <a name="icordebugthread2getactivefunctions-method"></a><span data-ttu-id="a793f-102">ICorDebugThread2::GetActiveFunctions — Metoda</span><span class="sxs-lookup"><span data-stu-id="a793f-102">ICorDebugThread2::GetActiveFunctions Method</span></span>
<span data-ttu-id="a793f-103">Pobiera informacje o funkcji aktywnych we wszystkich ramki dla wątku.</span><span class="sxs-lookup"><span data-stu-id="a793f-103">Gets information about the active function in each of this thread's frames.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a793f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a793f-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a793f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a793f-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="a793f-106">[in] Rozmiar `pFunctions` tablicy.</span><span class="sxs-lookup"><span data-stu-id="a793f-106">[in] The size of the `pFunctions` array.</span></span>  
  
 `pcFunctions`  
 <span data-ttu-id="a793f-107">[out] Wskaźnik do liczby obiektów zwróconych w `pFunctions` tablicy.</span><span class="sxs-lookup"><span data-stu-id="a793f-107">[out] A pointer to the number of objects returned in the `pFunctions` array.</span></span> <span data-ttu-id="a793f-108">Liczba obiektów zwróconych będzie równa liczbie zarządzanych ramek na stosie.</span><span class="sxs-lookup"><span data-stu-id="a793f-108">The number of objects returned will be equal to the number of managed frames on the stack.</span></span>  
  
 `pFunctions`  
 <span data-ttu-id="a793f-109">[out w] Tablica obiektów cor_active_function —, z których każdy zawiera informacje na temat funkcji active w ramkach tego wątku.</span><span class="sxs-lookup"><span data-stu-id="a793f-109">[in, out] An array of COR_ACTIVE_FUNCTION objects, each of which contains information about the active functions in this thread's frames.</span></span>  
  
 <span data-ttu-id="a793f-110">Pierwszy element stosowanych w odniesieniu do ramki liścia i itd wstecz do katalogu głównego stosu.</span><span class="sxs-lookup"><span data-stu-id="a793f-110">The first element will be used for the leaf frame, and so on back to the root of the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a793f-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a793f-111">Remarks</span></span>  
 <span data-ttu-id="a793f-112">Jeśli `pFunctions` ma wartość null w danych wejściowych, `GetActiveFunctions` zwraca liczbę funkcji, które znajdują się w stosie.</span><span class="sxs-lookup"><span data-stu-id="a793f-112">If `pFunctions` is null on input, `GetActiveFunctions` returns only the number of functions that are on the stack.</span></span> <span data-ttu-id="a793f-113">Oznacza to jeśli `pFunctions` ma wartość null w danych wejściowych, `GetActiveFunctions` zwraca wartość tylko w `pcFunctions`.</span><span class="sxs-lookup"><span data-stu-id="a793f-113">That is, If `pFunctions` is null on input, `GetActiveFunctions` returns a value only in `pcFunctions`.</span></span>  
  
 <span data-ttu-id="a793f-114">`GetActiveFunctions` Metoda jest przeznaczona do optymalizacji na pobieranie tych samych informacji z ramek w ślad stosu i zawiera tylko ramki, które będą miały obiektu ICorDebugILFrame ich w pełen ślad stosu.</span><span class="sxs-lookup"><span data-stu-id="a793f-114">The `GetActiveFunctions` method is intended as an optimization over getting the same information from frames in a stack trace, and includes only frames that would have had an ICorDebugILFrame object for them in the full stack trace.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a793f-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a793f-115">Requirements</span></span>  
 <span data-ttu-id="a793f-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a793f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a793f-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a793f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a793f-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a793f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a793f-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a793f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
