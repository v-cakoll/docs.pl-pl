---
title: ICorDebugDataTarget::GetThreadContext — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
ms.openlocfilehash: 79708aa5a2abcb8d7465f82a8beb918484c193b9
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976554"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="0d552-102">ICorDebugDataTarget::GetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="0d552-102">ICorDebugDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="0d552-103">Zwraca bieżący kontekst wątku dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="0d552-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d552-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d552-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d552-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d552-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="0d552-106">podczas Identyfikator wątku, którego kontekst ma zostać pobrany.</span><span class="sxs-lookup"><span data-stu-id="0d552-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="0d552-107">Identyfikator jest zdefiniowany przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="0d552-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="0d552-108">podczas Bitowa kombinacja flag zależnych od platformy wskazująca, które fragmenty kontekstu mają być odczytywane.</span><span class="sxs-lookup"><span data-stu-id="0d552-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="0d552-109">podczas Rozmiar `pContext`.</span><span class="sxs-lookup"><span data-stu-id="0d552-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="0d552-110">określoną Bufor, w którym będzie przechowywany kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="0d552-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d552-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0d552-111">Remarks</span></span>  
 <span data-ttu-id="0d552-112">Na platformach Windows `pContext` musi być `CONTEXT` strukturą (zdefiniowaną w Winnt. h), która jest odpowiednia dla typu maszyny określonego przez metodę [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0d552-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="0d552-113">`contextFlags`musi mieć te same wartości co `ContextFlags` pole `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="0d552-113">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="0d552-114">`CONTEXT` Struktura jest specyficzna dla procesora; Szczegóły można znaleźć w pliku WinNT. h.</span><span class="sxs-lookup"><span data-stu-id="0d552-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d552-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0d552-115">Requirements</span></span>  
 <span data-ttu-id="0d552-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d552-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d552-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0d552-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d552-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0d552-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d552-119">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d552-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d552-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d552-120">See also</span></span>

- [<span data-ttu-id="0d552-121">ICorDebugDataTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0d552-121">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="0d552-122">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="0d552-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0d552-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="0d552-123">Debugging</span></span>](index.md)
