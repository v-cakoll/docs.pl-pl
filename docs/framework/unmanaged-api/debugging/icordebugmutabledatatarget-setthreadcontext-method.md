---
title: 'ICorDebugMutableDataTarget:: SetThreadContext —, Metoda'
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
ms.openlocfilehash: 2c9e508c7a4059fee4e1cce6eb28e6de7b2fff6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132709"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="5e999-102">ICorDebugMutableDataTarget:: SetThreadContext —, Metoda</span><span class="sxs-lookup"><span data-stu-id="5e999-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="5e999-103">Ustawia kontekst (wartości rejestru) dla wątku.</span><span class="sxs-lookup"><span data-stu-id="5e999-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e999-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e999-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e999-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e999-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="5e999-106">podczas Identyfikator wątku zdefiniowanego przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="5e999-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="5e999-107">podczas Rozmiar bufora `pContext`, który ma zostać zapisany.</span><span class="sxs-lookup"><span data-stu-id="5e999-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="5e999-108">podczas Wskaźnik do bajtów do zapisania.</span><span class="sxs-lookup"><span data-stu-id="5e999-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e999-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e999-109">Remarks</span></span>  
 <span data-ttu-id="5e999-110">Metoda `SetThreadContext` aktualizuje bieżący kontekst dla wątku określonego przez argument `dwThreadID` zdefiniowanego przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="5e999-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="5e999-111">Format rekordu kontekstu jest określany przez platformę wskazywaną przez metodę [ICorDebugDataTarget:: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5e999-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="5e999-112">W systemie Windows jest to struktura [kontekstu](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) .</span><span class="sxs-lookup"><span data-stu-id="5e999-112">On Windows, this is a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e999-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e999-113">Requirements</span></span>  
 <span data-ttu-id="5e999-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e999-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e999-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5e999-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e999-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5e999-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e999-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e999-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e999-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e999-118">See also</span></span>

- [<span data-ttu-id="5e999-119">ICorDebugMutableDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e999-119">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="5e999-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5e999-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
