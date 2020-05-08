---
title: ICorDebugAppDomain::EnumerateBreakpoints — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateBreakpoints
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints method [.NET Framework debugging]
- EnumerateBreakpoints method [.NET Framework debugging]
ms.assetid: 206069c5-25cb-4794-9d69-67c5aa7ed0af
topic_type:
- apiref
ms.openlocfilehash: bb994ae32c9e0e61c06c60521361a5c6c78d12fa
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895279"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="a9509-102">ICorDebugAppDomain::EnumerateBreakpoints — Metoda</span><span class="sxs-lookup"><span data-stu-id="a9509-102">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>
<span data-ttu-id="a9509-103">Pobiera moduł wyliczający dla wszystkich aktywnych punktów przerwania w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9509-103">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9509-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9509-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9509-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9509-105">Parameters</span></span>  
 `ppBreakpoints`  
 <span data-ttu-id="a9509-106">określoną Wskaźnik do adresu obiektu ICorDebugBreakpointEnum, który jest modułem wyliczającym dla wszystkich aktywnych punktów przerwania w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9509-106">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9509-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9509-107">Remarks</span></span>  
 <span data-ttu-id="a9509-108">Moduł wyliczający zawiera wszystkie typy punktów przerwania, w tym punkty przerwania funkcji i punkty przerwania danych.</span><span class="sxs-lookup"><span data-stu-id="a9509-108">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9509-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a9509-109">Requirements</span></span>  
 <span data-ttu-id="a9509-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9509-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9509-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a9509-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9509-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a9509-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9509-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9509-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
